---
date: 2025-12-22
description: Aprende a exportar markdown convirtiendo documentos de Word a Markdown
  con Aspose.Words para Java. Esta guía paso a paso cubre la alineación de tablas,
  el manejo de imágenes y más.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Cómo exportar Markdown con Aspose.Words para Java
url: /es/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo exportar Markdown con Aspose.Words para Java

## Introducción a la exportación de Markdown en Aspose.Words para Java

En este tutorial paso a paso, **aprenderás cómo exportar markdown** desde documentos Word usando Aspose.Words para Java. Markdown es un lenguaje de marcado ligero que es perfecto para documentación, generadores de sitios estáticos y muchas plataformas de publicación. Al final de esta guía podrás **convertir Word a markdown**, personalizar la alineación de tablas y **manejar imágenes en markdown** sin esfuerzo.

## Respuestas rápidas
- **¿Cuál es la clase principal para guardar como Markdown?** `MarkdownSaveOptions`
- **¿Pueden las imágenes incrustarse automáticamente?** Sí – establece la carpeta de imágenes mediante `setImagesFolder`.
- **¿Cómo controlo la alineación de la tabla?** Usa `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **¿Cuáles son los requisitos mínimos?** JDK 8+ y la biblioteca Aspose.Words para Java.
- **¿Hay una versión de prueba disponible?** Sí, descárgala desde el sitio web de Aspose.

## ¿Qué es “cómo exportar markdown”?

Exportar markdown significa tomar un documento Word de texto enriquecido (`.docx`) y producir un archivo de texto plano `.md` que conserva encabezados, tablas e imágenes en la sintaxis Markdown.

## ¿Por qué usar Aspose.Words para Java para convertir docx con imágenes?

Aspose.Words maneja diseños complejos, imágenes incrustadas y estructuras de tablas sin perder fidelidad. También te brinda un control granular sobre la salida Markdown, como la alineación de tablas y la gestión de la carpeta de imágenes.

## Requisitos previos

- Java Development Kit (JDK) instalado en tu sistema.
- Biblioteca Aspose.Words para Java. Puedes descargarla desde [aquí](https://releases.aspose.com/words/java/).

## Paso 1: Crear un documento Word sencillo

Primero, crearemos un documento pequeño que contiene una tabla. Esto nos permitirá demostrar **personalizar la alineación de la tabla** más adelante.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

En el fragmento anterior nosotros:

1. Crear un nuevo `Document`.
2. Usar `DocumentBuilder` para insertar una tabla de dos celdas.
3. Aplicar alineación de párrafo **derecha** y **centrada** dentro de cada celda.
4. Guardar el archivo como Markdown usando `MarkdownSaveOptions`.

## Paso 2: Personalizar la alineación del contenido de la tabla

Aspose.Words te permite dictar cómo se renderizan las celdas de la tabla en el Markdown final. Puedes forzar la alineación izquierda, derecha, centrada, o dejar que la biblioteca decida automáticamente basándose en el primer párrafo de cada columna.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Al cambiar la propiedad `TableContentAlignment` controlas **personalizar la alineación de la tabla** para la salida Markdown.

## Paso 3: Manejar imágenes al exportar a markdown

Cuando un documento contiene imágenes, querrás que esas imágenes aparezcan correctamente en el archivo `.md` generado. Establece la carpeta donde Aspose.Words debe volcar las imágenes extraídas.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Reemplaza `"document_with_images.docx"` con la ruta a tu archivo fuente y `"images_folder/"` con la ubicación donde deseas que se almacenen las imágenes. El Markdown resultante contendrá enlaces de imagen que apuntan a esta carpeta, permitiéndote **manejar imágenes en markdown** sin problemas.

## Código fuente completo para guardar documentos como Markdown en Aspose.Words para Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Problemas comunes y soluciones

| Problema | Solución |
|----------|----------|
| Las imágenes no aparecen en el archivo `.md` | Verifica que `setImagesFolder` apunte a un directorio con permisos de escritura y que la carpeta esté referenciada correctamente en el Markdown generado. |
| La alineación de la tabla se ve incorrecta | Usa `TableContentAlignment.AUTO` para que Aspose.Words infiera la mejor alineación basándose en el primer párrafo de cada columna. |
| El archivo de salida está vacío | Asegúrate de que el objeto `Document` realmente contenga contenido antes de llamar a `save`. |

## Preguntas frecuentes

**Q: ¿Cómo instalo Aspose.Words para Java?**  
A: Aspose.Words para Java se puede instalar incluyendo la biblioteca en tu proyecto Java. Puedes descargar la biblioteca desde [aquí](https://releases.aspose.com/words/java/) y seguir las instrucciones de instalación proporcionadas en la documentación.

**Q: ¿Puedo convertir documentos Word complejos con tablas e imágenes a Markdown?**  
A: Sí, Aspose.Words para Java soporta la conversión de documentos Word complejos con tablas, imágenes y varios elementos de formato a Markdown. Puedes personalizar la salida Markdown según la complejidad de tu documento.

**Q: ¿Cómo puedo manejar imágenes en archivos Markdown?**  
A: Establece la ruta de la carpeta de imágenes usando el método `setImagesFolder` en `MarkdownSaveOptions`. Asegúrate de que los archivos de imagen se almacenen en la carpeta especificada; Aspose.Words generará los enlaces de imagen Markdown apropiados.

**Q: ¿Hay una versión de prueba de Aspose.Words para Java disponible?**  
A: Sí, puedes obtener una versión de prueba de Aspose.Words para Java desde el sitio web de Aspose. La versión de prueba te permite evaluar las capacidades de la biblioteca antes de comprar una licencia.

**Q: ¿Dónde puedo encontrar más ejemplos y documentación?**  
A: Para más ejemplos, documentación e información detallada sobre Aspose.Words para Java, por favor visita la [documentación](https://reference.aspose.com/words/java/).

---

**Última actualización:** 2025-12-22  
**Probado con:** Aspose.Words para Java 24.12 (última versión al momento de escribir)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}