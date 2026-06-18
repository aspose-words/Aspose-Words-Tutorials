---
category: general
date: 2026-06-17
description: 'Registre advertencias de sustitución de fuentes en Java con Aspose.Words:
  capture fuentes faltantes al cargar el documento y mantenga la salida consistente.'
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: es
og_description: Registra advertencias de sustitución de fuentes en Java con Aspose.Words.
  Aprende a capturar alertas de fuentes faltantes durante la carga del documento y
  mantener tus PDFs impecables.
og_title: Registro de advertencias de sustitución de fuentes en Java – Guía completa
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Registrar advertencias de sustitución de fuentes en Java con Aspose.Words
url: /es/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar advertencias de sustitución de fuentes en Java – Guía completa

¿Alguna vez te has preguntado cómo **registrar advertencias de sustitución de fuentes** cuando un documento de Word incorpora una fuente que no tienes en el servidor? No eres el único que se rasca la cabeza por fuentes faltantes que se sustituyen silenciosamente. ¿La buena noticia? Aspose.Words for Java te ofrece una forma sencilla de capturar esas sustituciones en el momento en que se carga un documento.

En este tutorial recorreremos un ejemplo práctico que muestra exactamente cómo registrar una devolución de llamada de advertencia, filtrar las alertas de sustitución de fuentes y escribirlas en la consola (o en cualquier registrador que prefieras). Al final tendrás un fragmento reutilizable que podrás insertar en cualquier proyecto Java que use **Aspose.Words Java**.

## Lo que aprenderás

- Cómo configurar **LoadOptions** para capturar advertencias.
- Cómo implementar un **IWarningCallback** que solo reaccione a eventos de **font substitution**.
- Cómo cargar un documento de forma segura manteniendo un registro claro de fuentes faltantes.
- Consejos para ampliar la solución a registros basados en archivos o sistemas de monitoreo.

### Requisitos previos

- Java 8 o superior (el código también funciona con Java 11+).
- Biblioteca Aspose.Words for Java (se recomienda la versión 23.10 o posterior).
- Un archivo de ejemplo `.docx` que haga referencia a una fuente no instalada en tu máquina (p. ej., `MissingFont.docx`).

No se requieren frameworks adicionales—solo Java puro y los Aspose.JARs.

---

## Paso 1: Configurar LoadOptions para Aspose.Words Java

Antes de poder interceptar cualquier advertencia, necesitas una instancia de **LoadOptions**. Este objeto indica a Aspose.Words cómo debe comportarse al analizar el archivo entrante.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

¿Por qué es crucial este paso? Sin un objeto `LoadOptions`, la biblioteca sustituye silenciosamente las fuentes faltantes y nunca ves rastro. Al crear uno explícitamente, abres la puerta a una **warning callback** personalizada que puede registrar exactamente lo que te importa.

> **Consejo profesional:** Si estás cargando muchos documentos en lote, reutiliza una única instancia de `LoadOptions` para evitar la creación innecesaria de objetos.

---

## Paso 2: Implementar una Warning Callback para la sustitución de fuentes

Aspose.Words incluye la interfaz `IWarningCallback`. Implementarla te permite decidir qué hacer cuando el motor genera un `WarningInfo`. En nuestro caso, solo queremos reaccionar a `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Algunas cosas a tener en cuenta:

1. **Filtrado** – La sentencia `if` garantiza que ignoramos advertencias no relacionadas (como problemas de diseño) y mantenemos el registro ordenado.
2. **Seguridad de subprocesos** – La devolución de llamada se ejecuta en el mismo subproceso que carga el documento, por lo que no necesitas sincronización adicional para una salida simple a la consola. Si escribes en un registrador compartido, asegúrate de que sea thread‑safe.
3. **Extensibilidad** – ¿Quieres escribir en un archivo? Sustituye `System.out.println` por `java.util.logging.Logger` o un framework de registro de terceros.

---

## Paso 3: Cargar el documento usando las opciones configuradas

Ahora que la devolución de llamada está configurada, carga tu archivo Word. En el momento en que Aspose.Words analiza el documento, cualquier fuente faltante activará la devolución de llamada definida arriba.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Si el archivo fuente hace referencia a una fuente que no está instalada, verás una salida similar a:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Esa línea es la **log font substitution warnings** que estabas buscando. Ahora puedes actuar sobre ella—quizás alertar a un usuario, cambiar a una hoja de estilo de respaldo, o simplemente mantener un registro para cumplimiento.

---

## Paso 4: Continuar con el procesamiento normal

Después de cargar, el documento se comporta como cualquier otro objeto `Document`. Siéntete libre de inspeccionar secciones, extraer texto o convertir a PDF. El registro de advertencias ocurre automáticamente durante el paso de carga, por lo que no necesitas código adicional.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

La consola mostrará ahora tanto la advertencia de sustitución de fuentes (si la hay) **como** el recuento de secciones, confirmando que el documento está completamente funcional.

---

## Consejos avanzados y casos límite

### Registrar en un archivo en lugar de la consola

Si prefieres un registro persistente, reemplaza la llamada `System.out.println` por un `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Recuerda manejar `IOException` adecuadamente en código de producción.

### Capturar varios documentos en un bucle

Al procesar una carpeta de documentos, puedes reutilizar la misma devolución de llamada:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Dado que la devolución de llamada está adjunta a `loadOptions`, cada iteración registra automáticamente cualquier evento de sustitución de fuentes.

### Manejar fuentes incrustadas

Aspose.Words puede incrustar fuentes faltantes si lo habilitas:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Incluso con la incrustación activada, la devolución de llamada de advertencia sigue disparándose, dándote visibilidad de lo que se sustituyó.

---

## Ejemplo completo y funcional

A continuación se muestra el programa completo, listo para ejecutarse. Cópialo en una clase llamada `FontSubstitutionDiagnostics.java`, ajusta la ruta del archivo y ejecútalo.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Salida esperada** (suponiendo que el documento fuente haga referencia a una fuente faltante):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Tanto la consola como `font_substitution_log.txt` contendrán la advertencia, proporcionándote un registro de auditoría fiable.

---

## Conclusión

Acabamos de mostrarte cómo **registrar advertencias de sustitución de fuentes** en Java usando Aspose.Words. Configurando `LoadOptions`, conectando un `IWarningCallback` y cargando el documento, obtienes total visibilidad de cualquier evento de fuente faltante que de otro modo pasaría desapercibido. A partir de aquí puedes:

- Redirigir advertencias a un servicio de registro central.
- Activar alertas para pipelines de control de calidad.
- Combinar esta técnica con otras estrategias de **document loading**, como conversión a PDF o combinación de correspondencia.

Siéntete libre de experimentar—cambia el registrador de consola por SLF4J, agrega marcas de tiempo, o incluso envía alertas a un panel de monitoreo. El patrón central sigue siendo el mismo, y ahora tienes una base sólida para un manejo robusto de fuentes en cualquier flujo de trabajo de documentos basado en Java.

¿Tienes una variante que te gustaría compartir? Tal vez la hayas integrado con Spring Boot o una función en la nube. Deja un comentario abajo, y mantengamos la conversación. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Capturar advertencias de sustitución de fuentes en Java con Aspose.Words – Guía completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Uso de opciones y configuraciones de documento en Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Habilitar advertencias de sustitución de fuentes en Aspose.Words – Guía completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}