---
category: general
date: 2026-08-04
description: Cargar subrayado de Markdown en Java y preservar el formato Markdown
  al cargar Markdown en el documento. Sigue este tutorial paso a paso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: es
lastmod: 2026-08-04
og_description: Cargar subrayado de Markdown en Java y preservar el formato Markdown.
  Aprende a cargar Markdown en un documento con soporte completo de subrayado.
og_image_alt: Diagram showing load markdown underline process
og_title: Cargar subrayado de Markdown en Java – guía paso a paso
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Cargar subrayado de Markdown en Java – guía completa de programación
url: /es/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cargar subrayado de markdown en Java – guía completa de programación

Si necesitas **cargar subrayado de markdown** al convertir un archivo Markdown a un objeto `Document`, esta guía te muestra exactamente cómo hacerlo. También aprenderás cómo **cargar markdown en documento** sin perder ningún estilo de subrayado, garantizando que el formato original de Markdown se preserve completamente.

El tutorial cubre todo lo que necesitas saber: bibliotecas requeridas, cada paso de configuración y cómo verificar que el formato de subrayado sobrevivió a la importación. Al final tendrás un fragmento de código reutilizable que podrás insertar en cualquier proyecto Java.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- Java 17 o posterior instalado (el ejemplo usa el sistema de módulos moderno)
- La última versión de **GroupDocs.Viewer** (o una biblioteca compatible que proporcione `LoadOptions` y `Document`)
- Un archivo Markdown (`sample.md`) que contenga texto subrayado, por ejemplo, `<u>underlined</u>` o la sintaxis al estilo GitHub `__underlined__`
- Un IDE como IntelliJ IDEA o VS Code, aunque cualquier editor de texto funciona

Estos requisitos garantizan que el código se ejecute sin configuración adicional.

## Cargar subrayado de markdown – guía paso a paso

El proceso consta de tres acciones principales: crear una instancia de `LoadOptions`, habilitar la detección de subrayado y, finalmente, cargar el archivo Markdown con esas opciones. Cada paso se explica a continuación.

### Paso 1: Crear `LoadOptions` para el documento

`LoadOptions` te permite personalizar cómo la biblioteca analiza el archivo fuente. Crear una nueva instancia te brinda una base limpia para configuraciones posteriores.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

El objeto `LoadOptions` es el punto de entrada para todos los ajustes relacionados con la importación. Lo usarás en el siguiente paso para activar la detección de subrayado.

### Paso 2: Habilitar la detección del formato de subrayado al cargar

Por defecto, el visor puede ignorar las etiquetas de subrayado porque son menos comunes en Markdown. Habilitar esta bandera indica al analizador que mantenga los fragmentos de subrayado intactos.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

Configurar `setImportUnderlineFormatting(true)` asegura que cualquier etiqueta HTML `<u>` o la sintaxis de subrayado al estilo GitHub se traduzca al modelo `Document` como un estilo de subrayado. Esta es la acción clave que hace que **cargar subrayado de markdown** funcione como se espera.

### Paso 3: Cargar el archivo Markdown usando las opciones configuradas

Ahora puedes cargar el archivo. Pasa el objeto `loadOptions` al constructor de `Document` para que el analizador respete la bandera de subrayado.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Cuando el constructor termina, `markdownDoc` contiene una representación completa en memoria del origen Markdown, con los fragmentos de subrayado incluidos.

### Paso 4: Verificar que el formato de subrayado se preserve

Una rápida verificación ayuda a confirmar que **preservar el formato de markdown** funcionó. El siguiente fragmento imprime el texto de cada párrafo y marca los fragmentos subrayados con una tilde (`~`) para mayor visibilidad.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Salida esperada** (suponiendo que `sample.md` contenga `This is __underlined__ text`):

```
This is ~underlined~ text
```

Las tildes indican que el estilo de subrayado sobrevivió a la importación, confirmando que la operación **cargar markdown en documento** preservó el formato original.

## Problemas comunes y cómo evitarlos

| Síntoma | Causa | Solución |
|---|---|---|
| El subrayado desaparece después de cargar | `setImportUnderlineFormatting` dejado en su valor predeterminado `false` | Asegúrate de llamar a `loadOptions.setImportUnderlineFormatting(true)` antes de crear el `Document`. |
| Solo una parte del texto está subrayada | Sintaxis Markdown mixta (p. ej., HTML `<u>` mezclado con `__underline__`) | La biblioteca soporta ambos; verifica que el archivo fuente use un marcador de subrayado consistente. |
| El documento no se carga | Ruta de archivo incorrecta o dependencias de biblioteca faltantes | Usa una ruta absoluta o coloca `sample.md` relativo al directorio de trabajo; incluye los JARs del visor en el classpath. |

**Consejo profesional:** Si también necesitas mantener estilos en negrita o cursiva, habilítalos con `setImportBoldFormatting(true)` y `setImportItalicFormatting(true)` respectivamente. Combinar estas banderas te brinda una importación totalmente fiel de los estilos Markdown más comunes.

## Ejemplo completo ejecutable

A continuación hay un programa Java autónomo que reúne todo. Copia el código en un archivo llamado `LoadMarkdownUnderlineDemo.java`, ajusta la ruta del archivo y ejecútalo con `java LoadMarkdownUnderlineDemo`.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

Ejecutar el programa imprime el contenido del documento con marcadores de subrayado, demostrando que la función **cargar subrayado de markdown** funciona y que puedes **preservar el formato de markdown** a lo largo de la canalización de importación.

## Conclusión

Ahora sabes cómo **cargar subrayado de markdown** en Java, cómo **cargar markdown en documento** manteniendo el estilo original, y cómo verificar que el formato de subrayado está intacto. Este enfoque funciona con las últimas versiones de GroupDocs.Viewer y puede ampliarse para soportar características adicionales de Markdown como negrita, cursiva y tablas.

A continuación, explora temas relacionados como **preservar el formato de markdown para tablas**, **renderizar Markdown a PDF**, o **estilizado personalizado de elementos Markdown importados**. Ajusta las banderas de `LoadOptions` para que coincidan con los requisitos exactos de formato de tu aplicación, y tendrás un control granular sobre cada paso de importación. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Domina las opciones de carga de Markdown con Aspose.Words para Java](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Domina las opciones de carga de Markdown Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}