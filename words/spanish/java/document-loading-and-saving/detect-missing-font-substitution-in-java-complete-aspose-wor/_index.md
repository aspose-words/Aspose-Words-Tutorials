---
category: general
date: 2026-06-05
description: Detecta la sustitución de fuentes faltantes en Java con Aspose.Words.
  Aprende a configurar LoadOptions, FontSettings y callbacks de advertencia para un
  procesamiento de documentos fiable.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: es
og_description: Detecta la sustitución de fuentes faltantes en Java con Aspose.Words.
  Esta guía muestra paso a paso cómo configurar LoadOptions, FontSettings y una devolución
  de llamada de advertencia para capturar fuentes faltantes.
og_title: Detectar sustitución de fuentes faltantes en Java – Tutorial completo de
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: detectar sustitución de fuentes faltantes en Java – Guía completa de Aspose.Words
url: /es/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# detectar sustitución de fuentes faltantes en Java – Guía completa de Aspose.Words

¿Alguna vez te has preguntado cómo **detect missing font substitution** al cargar un documento Word en Java? No eres el único. Las fuentes faltantes pueden arruinar silenciosamente tus PDFs o páginas renderizadas, y detectarlas temprano ahorra horas de depuración. En este tutorial recorreremos una solución práctica que no solo carga un documento, sino que también te indica exactamente cuándo ocurre una sustitución de fuente.

Cubriremos todo, desde crear `LoadOptions` hasta conectar un `WarningCallback` que imprime un mensaje claro cada vez que Aspose.Words intercambia una fuente faltante. Al final, tendrás un fragmento reutilizable que funciona con cualquier archivo `.docx`, y comprenderás *por qué* cada pieza es importante. Sin bibliotecas extra, solo Java puro y Aspose.Words.

## Lo que aprenderás

- Cómo configurar **LoadOptions** para usar **FontSettings** personalizados.  
- Cómo implementar un **IWarningCallback** que capture advertencias `FONT_SUBSTITUTION`.  
- Cómo cargar un documento mientras se monitoriza de forma segura la ausencia de fuentes.  
- Salida esperada en la consola y cómo adaptar el código para frameworks de registro.  

**Requisitos previos**: Java 8+ instalado, Aspose.Words for Java (v23.12 o superior) en tu classpath, y un archivo `.docx` de ejemplo que haga referencia a una fuente que no tengas instalada. Eso es todo—no se requieren herramientas de compilación adicionales.

---

## Paso 1: Configura el proyecto y agrega Aspose.Words

Antes de sumergirnos en el código, asegúrate de que Aspose.Words esté disponible. Si usas Maven, agrega la siguiente dependencia a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Si prefieres Gradle, el equivalente es:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

Una vez que la biblioteca esté en el classpath, estás listo para **detect missing font substitution** con una única llamada de método.

---

## Paso 2: Crea LoadOptions y adjunta FontSettings

El corazón de la solución está en preparar una instancia de `LoadOptions` que sepa cómo vigilar los problemas de fuentes. Aquí tienes el código desglosado línea por línea.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Por qué es importante**: `LoadOptions` le indica a Aspose.Words *cómo* interpretar el archivo entrante. Al conectar un `FontSettings` personalizado, le damos al cargador un gancho (`IWarningCallback`) que se dispara **exactamente cuando se sustituye una fuente faltante**. Sin este callback, Aspose.Words reemplazaría la fuente silenciosamente y nunca lo sabrías.

---

## Paso 3: Carga el documento con las opciones configuradas

Ahora que el sistema de advertencias está listo, cargar el documento es sencillo.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

Cuando se ejecuta la llamada `new Document(...)`, Aspose.Words lee el archivo, verifica cada referencia de fuente y, si no puede encontrar una fuente coincidente en el sistema, activa el método `warning` que definimos antes. La consola mostrará inmediatamente una línea como:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Esa línea es la salida de **detect missing font substitution** que estabas buscando.

---

## Paso 4: Verifica el resultado y ajusta el callback (Avanzado)

### 4.1 Verificación rápida

Ejecuta el programa desde tu IDE o mediante `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Si el documento hace referencia a una fuente que no tienes, verás el mensaje de advertencia impreso. Si la consola permanece silenciosa, la fuente existe en tu máquina o el documento no solicita fuentes faltantes.

### 4.2 Registro en lugar de `System.out`

En código de producción probablemente querrás un logger:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Ese pequeño cambio hace que el mecanismo de **detect missing font substitution** funcione bien con los pipelines de registro existentes.

### 4.3 Manejo de otros tipos de advertencia

El callback recibe *todas* las advertencias, no solo los problemas de fuentes. Si deseas vigilar otros problemas (p. ej., `UNKNOWN_STYLE`), agrega ramas `if` adicionales. Aquí tienes un ejemplo rápido:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## Paso 5: Errores comunes y consejos profesionales

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **No aparece ninguna advertencia** | La fuente realmente existe en el SO, o el documento usa un fallback que Aspose.Words considera “encontrado”. | Elimina temporalmente la fuente del sistema o usa un nombre de fuente verdaderamente inexistente en el documento fuente. |
| **Callback nunca llamado** | `setWarningCallback` se llamó en una instancia *diferente* de `FontSettings` a la que está adjunta a `LoadOptions`. | Asegúrate de llamar `loadOptions.setFontSettings(fontSettings)` **después** de configurar el callback. |
| **Ralentización del rendimiento** | Cargar muchos documentos grandes con callbacks puede añadir sobrecarga. | Cachea una única instancia de `FontSettings` y reutilízala en varias cargas si procesas lotes. |
| **Múltiples hilos** | `FontSettings` no es thread‑safe por defecto. | Crea una instancia separada de `FontSettings` por hilo o sincroniza el acceso. |

**Consejo profesional**: Si generas PDFs para un servicio web, podrías recopilar todas las advertencias de sustitución en una lista y devolverlas en la respuesta de la API, en lugar de imprimirlas en la consola.

## Ejemplo completo listo para copiar y pegar

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Salida esperada en la consola** (asumiendo que el archivo hace referencia a una fuente faltante):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Si no hay fuentes faltantes, solo verás la línea final “Document loaded successfully.”.

## Conclusión

Acabamos de demostrar cómo **detect missing font substitution** en Java usando Aspose.Words. Configurando `LoadOptions`, creando una instancia de `FontSettings` y conectando un `IWarningCallback`, obtienes visibilidad total de cada fuente que la biblioteca intercambia tras bambalinas. Este enfoque no solo evita fallos silenciosos de renderizado, sino que también te brinda un punto de enganche para registro, alertas o incluso la inserción automática de fuentes de respaldo.

A partir de aquí puedes:

- Extender el callback para recopilar advertencias en una lista para respuestas de API.  
- Combinar esta técnica con la **configuración de LoadOptions** para otros escenarios (p. ej., carga de recursos personalizada).  
- Explorar el ecosistema más amplio de **Java Aspose.Words**: conversión a PDF, extracción de texto o fusiones de correo.

Pruébalo, ajusta el logger y permite que tus aplicaciones avisen cuando una fuente desaparece. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Capturar advertencias de sustitución de fuentes en Java con Aspose.Words – Guía completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Uso de opciones y configuraciones de documento en Aspose.Words para Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}