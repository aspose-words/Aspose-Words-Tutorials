---
category: general
date: 2026-11-22
description: Aprende cómo cargar markdown con formato en Java. Esta guía te muestra
  cómo leer markdown con formato usando LoadOptions y Document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to load markdown
- read markdown with formatting
- Java markdown parsing
- LoadOptions import underline
- Document processing Java
language: es
lastmod: 2026-11-22
og_description: Cómo cargar markdown con formato en Java. Sigue este tutorial completo
  para leer markdown con formato, preservar los estilos de subrayado y trabajar con
  objetos Document.
og_image_alt: Java code snippet showing markdown loading with formatting enabled
og_title: Cómo cargar markdown con formato en Java – guía paso a paso
schemas:
- author: GroupDocs
  dateModified: '2026-11-22'
  description: Learn how to load markdown with formatting in Java. This guide shows
    you how to read markdown with formatting using LoadOptions and Document.
  headline: How to load markdown with formatting in Java
  type: TechArticle
tags:
- markdown
- java
- document-processing
title: Cómo cargar markdown con formato en Java
url: /es/java/document-loading-and-saving/how-to-load-markdown-with-formatting-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo cargar markdown con formato en Java

Si necesitas **cargar markdown** manteniendo sus estilos visuales, este tutorial te brinda una solución lista para ejecutar. Verás exactamente cómo **leer markdown con formato** como texto subrayado, de modo que el documento renderizado coincida con el origen.

La guía cubre cada paso, desde la configuración del cargador hasta la verificación de que el formato sobrevivió a la importación. No se requieren herramientas externas más allá de la biblioteca estándar GroupDocs.Viewer (o cualquier API compatible que proporcione `LoadOptions` y `Document`). Al final podrás integrar la carga de markdown en cualquier backend Java, servicio web o aplicación de escritorio.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o superior instalado.  
* Maven o Gradle para la gestión de dependencias.  
* Acceso al JAR de GroupDocs.Viewer (o equivalente) que contiene `LoadOptions` y `Document`.  
* Un archivo markdown de ejemplo (`sample.md`) que incluya marcado de subrayado (p. ej., `<u>texto subrayado</u>` o `_subrayado_` según el analizador).

## Paso 1: Añadir la dependencia requerida

Si usas Maven, agrega lo siguiente a tu `pom.xml`. Ajusta la versión a la última publicación estable.

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>23.12</version>
</dependency>
```

Los usuarios de Gradle pueden añadir:

```groovy
implementation 'com.groupdocs:groupdocs-viewer:23.12'
```

Incluir la biblioteca hace que las clases `LoadOptions` y `Document` estén disponibles en tiempo de compilación.

## Paso 2: Configurar LoadOptions para importar el formato de subrayado

El objeto `LoadOptions` indica al analizador qué características de markdown preservar. Habilitar el formato de subrayado asegura que el estilo visual aparezca en el `Document` resultante.

```java
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Creates a LoadOptions instance with underline import enabled.
 *
 * @return configured LoadOptions
 */
private static LoadOptions createLoadOptions() {
    LoadOptions loadOptions = new LoadOptions();
    // Preserve underline markup when the markdown is parsed.
    loadOptions.setImportUnderlineFormatting(true);
    return loadOptions;
}
```

**Por qué es importante:**  
Sin `setImportUnderlineFormatting(true)`, el analizador elimina las etiquetas de subrayado, dejando texto plano. Activar la bandera mantiene el estilo intacto, lo cual es esencial cuando el consumidor posterior (p. ej., un generador de PDF) depende de esas pistas visuales.

## Paso 3: Cargar el documento markdown usando las opciones configuradas

Ahora puedes leer el archivo markdown. El constructor de `Document` acepta la ruta del archivo y el `LoadOptions` que acabas de preparar.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Loads a markdown file while preserving formatting.
 *
 * @param markdownPath absolute or relative path to the .md file
 * @param options      LoadOptions with formatting flags
 * @return Document representing the parsed markdown
 */
private static Document loadMarkdown(String markdownPath, LoadOptions options) {
    return new Document(markdownPath, options);
}
```

**Por qué es importante:**  
Pasar el `LoadOptions` al constructor de `Document` garantiza que el analizador respete la bandera de subrayado durante todo el proceso de importación. El objeto `Document` resultante puede renderizarse, convertirse o inspeccionarse con el formato completo.

## Paso 4: Verificar que el formato de subrayado se conservó

Una forma rápida de confirmar que el subrayado está presente es renderizar el documento a HTML e imprimir la salida. El HTML contendrá etiquetas `<u>` si la importación tuvo éxito.

```java
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.Viewer;

/**
 * Renders the loaded Document to HTML and prints the first page.
 *
 * @param doc Document loaded from markdown
 */
private static void renderAndPrint(Document doc) {
    // Create a Viewer instance for rendering.
    Viewer viewer = new Viewer(doc);
    // Render the first page as HTML.
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
    viewer.view(viewOptions, 1);
    String html = viewOptions.getHtmlContent();

    System.out.println("Rendered HTML snippet:");
    System.out.println(html.substring(0, Math.min(html.length(), 500)));
}
```

Ejecutar el programa completo debería mostrar un fragmento HTML que incluye `<u>texto subrayado</u>`. Si la etiqueta falta, verifica que `setImportUnderlineFormatting(true)` se haya llamado antes de cargar el archivo.

## Ejemplo completo ejecutable

Juntando todo, aquí tienes una clase Java autónoma que puedes compilar y ejecutar:

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.Viewer;
import com.groupdocs.viewer.options.HtmlViewOptions;
import com.groupdocs.viewer.options.LoadOptions;

/**
 * Demonstrates how to load markdown with formatting in Java.
 * The program reads a markdown file, preserves underline markup,
 * renders the first page to HTML, and prints a snippet.
 */
public class MarkdownLoader {

    public static void main(String[] args) {
        // Path to the markdown file – adjust as needed.
        String markdownPath = "sample.md";

        // Step 1: create LoadOptions with underline support.
        LoadOptions options = createLoadOptions();

        // Step 2: load the markdown document.
        Document doc = loadMarkdown(markdownPath, options);

        // Step 3: render the document to HTML and verify formatting.
        renderAndPrint(doc);
    }

    private static LoadOptions createLoadOptions() {
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setImportUnderlineFormatting(true);
        return loadOptions;
    }

    private static Document loadMarkdown(String path, LoadOptions options) {
        return new Document(path, options);
    }

    private static void renderAndPrint(Document doc) {
        Viewer viewer = new Viewer(doc);
        HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
        viewer.view(viewOptions, 1); // render first page
        String html = viewOptions.getHtmlContent();

        System.out.println("Rendered HTML snippet:");
        System.out.println(html.substring(0, Math.min(html.length(), 500)));
    }
}
```

**Salida esperada (truncada por brevedad):**

```
Rendered HTML snippet:
<div class="page">
  <p>This is a <u>underlined text</u> example from the markdown file.</p>
  …
```

Si aparece la etiqueta `<u>`, el markdown se cargó con el formato intacto.

## Variaciones comunes y casos límite

| Situación                              | Qué cambiar                                                |
|----------------------------------------|------------------------------------------------------------|
| **Diferentes extensiones de markdown** | Usa `loadOptions.setImportBoldFormatting(true)` para **negrita**. |
| **Archivos grandes (> 10 MB)**         | Transmite el archivo con `FileInputStream` y pasa el stream a `Document`. |
| **Necesidad de salida PDF**            | Después de cargar, usa `PdfViewOptions` con `Viewer` para generar un PDF que conserve los estilos de subrayado. |
| **Ejecutándose en un contenedor servlet** | Almacena el `Document` en el ámbito de la solicitud y renderízalo a HTML sobre la marcha. |

**Consejo:** Siempre crea una nueva instancia de `LoadOptions` para cada operación de carga. Reutilizar el mismo objeto entre hilos puede provocar fugas de estado inesperadas.

## Conclusión

Ahora sabes **cómo cargar markdown con formato en Java** y cómo **leer markdown con formato** usando `LoadOptions`. El ejemplo completo muestra la configuración, carga y verificación, para que puedas incorporar este patrón en cualquier proyecto Java que procese archivos markdown.  

A continuación, explora temas relacionados como **leer markdown con imágenes**, **convertir markdown a PDF** o **personalizar otras importaciones de estilo** (negrita, cursiva, tachado). Cada una de esas extensiones sigue el mismo patrón: ajustar las banderas de `LoadOptions`, cargar el `Document` y renderizar en el formato deseado.

¡Feliz programación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo cargar documento markdown en Java con opciones de importación personalizadas](/words/english/java/document-loading-and-saving/how-to-load-markdown-document-in-java-with-custom-import-opt/)
- [Cómo leer y cargar un archivo Markdown en Java con Aspose.Words](/words/english/java/document-loading-and-saving/how-to-read-markdown-file-java-with-aspose-words/)
- [Cómo cargar Markdown en Java – Guía completa](/words/english/java/document-loading-and-saving/how-to-load-markdown-in-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}