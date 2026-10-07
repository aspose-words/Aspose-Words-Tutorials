---
category: general
date: 2026-02-18
description: Crea opciones de carga en Java para detectar fuentes faltantes y aprende
  cómo cargar archivos DOCX con una devolución de llamada de advertencia.
draft: false
keywords:
- create load options
- detect missing fonts
- how to load docx
- Aspose.Words warning callback
- Java document processing
language: es
og_description: Crea opciones de carga en Java para detectar fuentes faltantes y aprende
  a cargar archivos DOCX con una devolución de llamada de advertencia.
og_title: Crear opciones de carga en Java – Detectar fuentes faltantes y cómo cargar
  DOCX
tags:
- java
- aspose-words
- document-processing
title: Crear opciones de carga en Java – Detectar fuentes faltantes y cómo cargar
  DOCX
url: /es/java/document-loading-and-saving/create-load-options-in-java-detect-missing-fonts-how-to-load/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear opciones de carga en Java – Detectar fuentes faltantes y cómo cargar DOCX

¿Alguna vez te has preguntado cómo **crear opciones de carga** que no solo lean un DOCX sino que también te avisen cuando falta una fuente? No eres el único. Las fuentes faltantes pueden convertir un documento perfectamente formateado en un desastre ilegible, y detectarlas temprano ahorra horas de depuración. En este tutorial recorreremos paso a paso cómo **detectar fuentes faltantes** mientras te mostramos **cómo cargar archivos DOCX** con una devolución de llamada de advertencia personalizada.

## Lo que aprenderás

- Cómo instanciar `LoadOptions` y configurar un manejador de advertencias.  
- Por qué la devolución de llamada de advertencia es esencial para capturar problemas de sustitución de fuentes.  
- El código exacto necesario para **cargar un DOCX** de forma segura, más algunos consejos prácticos para proyectos del mundo real.  
- Manejo de casos límite, como tratar otros tipos de advertencias o cargar PDFs con el mismo enfoque.

No se necesita documentación externa—todo lo que necesitas está aquí.

## Requisitos previos

- Java 17 o superior (la API funciona en versiones anteriores, pero 17 es el punto óptimo).  
- Biblioteca Aspose.Words for Java añadida a tu proyecto (`aspose-words-x.x.jar`).  
- Un conocimiento básico del manejo de excepciones en Java.  

Si ya tienes eso, vamos a sumergirnos.

![Diagrama de flujo de creación de opciones de carga](/images/create-load-options-diagram.png){: .center-image alt="Diagrama de flujo de creación de opciones de carga"}

## Paso 1: Crear opciones de carga (Cómo cargar DOCX)

Lo primero que debes hacer es **crear opciones de carga**. Este objeto le indica a Aspose.Words cómo comportarse al abrir un archivo. Piensa en él como un conjunto de instrucciones que entregas a la biblioteca antes de que vea el DOCX.

```java
// Step 1: Instantiate LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

¿Por qué no simplemente llamar a `new Document("file.docx")`? Porque sin `LoadOptions` pierdes la capacidad de reaccionar a advertencias—como fuentes faltantes—hasta después de que el documento ya está cargado, lo que puede ser demasiado tarde para ciertos flujos de trabajo.

## Paso 2: Configurar una devolución de llamada de advertencia para detectar fuentes faltantes

Ahora adjuntamos una devolución de llamada que se invocará cada vez que Aspose.Words encuentre una situación que quiera advertirte. En nuestro caso, nos interesa `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // React only to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Missing font detected: " + info.getDescription());
        }
    }
});
```

Algunas cosas a tener en cuenta:

- **¿Por qué una devolución de llamada?** Se ejecuta *durante* el proceso de carga, dándote la oportunidad de registrar o incluso abortar la operación antes de que el documento se materialice por completo.  
- **¿Por qué comprobar `WarningType.FONT_SUBSTITUTION`?** Ese es el valor exacto del enum que Aspose.Words usa para escenarios de fuentes faltantes. Otros tipos de advertencia (p. ej., `TABLE_STRUCTURE`) pueden filtrarse de forma similar si los necesitas.  
- **Consejo de rendimiento:** La devolución de llamada es ligera; evita operaciones de I/O intensivas dentro de ella. Si necesitas escribir a un archivo, encola los mensajes y vacíalos después de la carga.

## Paso 3: Cargar el archivo DOCX con las opciones configuradas

Con las opciones y la devolución de llamada listas, finalmente puedes cargar el DOCX. Esta es la parte que responde **cómo cargar docx** respetando las advertencias que configuraste.

```java
// Step 3: Load the document using the configured LoadOptions
try {
    Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    System.out.println("Document loaded successfully.");
} catch (Exception e) {
    System.err.println("Failed to load document: " + e.getMessage());
}
```

**¿Qué ocurre internamente?** A medida que el archivo se transmite, Aspose.Words verifica cada referencia de fuente. Si una fuente referenciada no está instalada, dispara la devolución de llamada de advertencia que definimos antes. Verás una salida como:

```
Missing font detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Document loaded successfully.
```

Ese feedback inmediato es invaluable cuando procesas lotes de archivos en un servidor.

## Ejemplo completo funcionando

Juntando todo, aquí tienes un programa autocontenido que puedes copiar‑pegar en tu IDE.

```java
import com.aspose.words.*;

public class DetectMissingFonts {
    public static void main(String[] args) {
        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register warning callback to detect missing fonts
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Missing font: " + info.getDescription());
                }
            }
        });

        // 3️⃣ Load the DOCX using the configured options
        try {
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            System.out.println("DOCX loaded – you can now work with it.");
        } catch (Exception ex) {
            System.err.println("Error loading DOCX: " + ex.getMessage());
        }
    }
}
```

**Salida esperada**

```
Missing font: Font 'Times New Roman' is not installed. Substituted with 'Arial'.
DOCX loaded – you can now work with it.
```

Si el archivo no contiene fuentes faltantes, la devolución de llamada simplemente permanece silenciosa y aparece la línea “DOCX loaded”.

## Consejos profesionales y casos límite

| Situación | Qué hacer |
|-----------|-----------|
| **Múltiples fuentes faltantes** | La devolución de llamada se dispara por cada una, por lo que obtendrás una línea por fuente. Agrúpalas en una `List<String>` si necesitas un resumen más adelante. |
| **También quieres capturar otras advertencias** | Añade ramas `else if` para `WarningType.TABLE_STRUCTURE`, `WarningType.UNKNOWN_FILE_FORMAT`, etc. |
| **Cargar archivos DOCX grandes** | Usa `LoadOptions.setLoadFormat(LoadFormat.DOCX)` para indicar el formato y acelerar la detección. |
| **Ejecutar en un servicio web** | Evita `System.out.println`; en su lugar, inyecta un logger (`SLF4J`, `Log4j`) dentro de la devolución de llamada. |
| **Las fuentes se instalan en tiempo de ejecución** | Después de detectar una fuente faltante, podrías cargarla programáticamente mediante `GraphicsEnvironment.registerFont(...)` y volver a cargar el documento. |

## Por qué este enfoque supera al método “solo try‑catch”

Muchos desarrolladores simplemente envuelven `new Document(...)` en un bloque try‑catch, esperando que una excepción les indique fuentes faltantes. Desafortunadamente, Aspose.Words trata la sustitución de fuentes como una *advertencia*, no como un error, por lo que no se lanza excepción. Al **crear opciones de carga** y adjuntar una devolución de llamada de advertencia, obtienes información determinista sobre problemas de fuentes sin sacrificar rendimiento.

## Próximos pasos

- **Detectar fuentes faltantes en PDFs** – el mismo patrón de `LoadOptions` funciona para PDFs, solo cambia la ruta del archivo y el formato de carga.  
- **Automatizar la instalación de fuentes** – combina la devolución de llamada con un script que obtenga fuentes faltantes de un repositorio compartido.  
- **Explorar otros tipos de advertencia** – Aspose.Words puede alertarte sobre etiquetas obsoletas, tablas complejas y más.  

Siéntete libre de experimentar: cambia el constructor `Document` por un stream (`new Document(InputStream, loadOptions)`) si trabajas con datos en memoria, o encadena múltiples devoluciones de llamada usando un patrón compuesto para pipelines de procesamiento a gran escala.

---

### TL;DR

Te mostramos cómo **crear opciones de carga** en Java, configurar una devolución de llamada que **detecta fuentes faltantes**, y finalmente **cargar un DOCX** de forma segura. Con solo tres pasos concisos ahora tienes un patrón reutilizable que puedes insertar en cualquier proyecto Aspose.Words.

¿Tienes preguntas sobre otros formatos de archivo o necesitas ayuda para ajustar la devolución de llamada a tu entorno específico? ¡Deja un comentario abajo y feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}