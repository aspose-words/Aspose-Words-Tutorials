---
title: Cómo guardar documentos como Markdown en Aspose.Words para Java
linktitle: Guardar documentos como Markdown
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a convertir documentos de Word a Markdown con Aspose.Words para Java. Esta guía paso a paso cubre la alineación de tablas, el manejo de imágenes y más.
weight: 18
url: /es/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo guardar documentos como Markdown en Aspose.Words para Java


## Introducción a cómo guardar documentos como Markdown en Aspose.Words para Java

En esta guía paso a paso, demostraremos cómo guardar documentos como Markdown usando Aspose.Words para Java. Markdown es un lenguaje de marcado liviano que se usa comúnmente para formatear documentos de texto. Con Aspose.Words para Java, puede convertir fácilmente sus documentos de Word al formato Markdown. Cubriremos diferentes aspectos del almacenamiento de archivos Markdown, incluida la alineación del contenido de la tabla y el manejo de imágenes.

## Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

- Java Development Kit (JDK) instalado en su sistema.
-  Biblioteca Aspose.Words para Java. Puedes descargarla desde[aquí](https://releases.aspose.com/words/java/).

## Paso 1: Crear un documento de Word

Comencemos creando un documento de Word que luego convertiremos al formato Markdown. Puede personalizar este documento según sus necesidades.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar una tabla con dos celdas
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Guardar el documento como Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 En este ejemplo, creamos una tabla simple con dos celdas y establecemos la alineación de los párrafos dentro de estas celdas. Luego, guardamos el documento como Markdown usando el`MarkdownSaveOptions`.

## Paso 2: Personalizar la alineación del contenido de la tabla

Aspose.Words para Java le permite personalizar la alineación del contenido de la tabla al guardarla como Markdown. Puede alinear el contenido de la tabla a la izquierda, a la derecha, al centro o dejar que se determine automáticamente en función del primer párrafo de cada columna de la tabla.

A continuación se explica cómo personalizar la alineación del contenido de la tabla:

```java
// Establecer la alineación del contenido de la tabla a la izquierda
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Establecer la alineación del contenido de la tabla a la derecha
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Establecer la alineación del contenido de la tabla al centro
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Establezca la alineación del contenido de la tabla en automática (determinada por el primer párrafo)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Al cambiar el`TableContentAlignment` propiedad, puede controlar cómo se alinea el contenido dentro de las tablas al convertir a Markdown.

## Paso 3: Manejo de imágenes

 Para incluir imágenes en su documento Markdown, debe especificar la carpeta donde se encuentran las imágenes. Aspose.Words para Java le permite configurar la carpeta de imágenes en el`MarkdownSaveOptions`.

A continuación se explica cómo configurar la carpeta de imágenes y guardar el documento con imágenes:

```java
// Cargar un documento que contenga imágenes
Document doc = new Document("document_with_images.docx");

// Establecer la ruta de la carpeta de imágenes
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Guardar el documento con imágenes
doc.save("document_with_images.md", saveOptions);
```

 Asegúrese de reemplazar`"document_with_images.docx"` con la ruta a su documento de Word que contiene imágenes y`"images_folder/"` con la ruta real a la carpeta donde se almacenan sus imágenes.

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
	// Hace que todos los párrafos dentro de la tabla estén alineados.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// La alineación en este caso se tomará del primer párrafo de la columna de la tabla correspondiente.
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

## Conclusión

En esta guía, hemos explorado cómo guardar documentos como Markdown usando Aspose.Words para Java. Cubrimos la creación de un documento de Word, la personalización de la alineación del contenido de la tabla y el manejo de imágenes en archivos Markdown. Ahora puede convertir de manera eficiente sus documentos de Word al formato Markdown, lo que los hace adecuados para varias plataformas de publicación y necesidades de documentación.

## Preguntas frecuentes

### ¿Cómo instalo Aspose.Words para Java?

 Aspose.Words para Java se puede instalar incluyendo la biblioteca en su proyecto Java. Puede descargar la biblioteca desde[aquí](https://releases.aspose.com/words/java/) y siga las instrucciones de instalación proporcionadas en la documentación.

### ¿Puedo convertir documentos complejos de Word con tablas e imágenes a Markdown?

Sí, Aspose.Words para Java admite la conversión de documentos Word complejos con tablas, imágenes y diversos elementos de formato a Markdown. Puede personalizar la salida de Markdown según la complejidad de su documento.

### ¿Cómo puedo manejar imágenes en archivos Markdown?

 Para incluir imágenes en archivos Markdown, configure la ruta de la carpeta de imágenes utilizando el`setImagesFolder`método en`MarkdownSaveOptions`Asegúrese de que los archivos de imagen estén almacenados en la carpeta especificada y Aspose.Words para Java manejará las referencias de imagen en consecuencia.

### ¿Hay una versión de prueba de Aspose.Words para Java disponible?

Sí, puede obtener una versión de prueba de Aspose.Words para Java desde el sitio web de Aspose. La versión de prueba le permite evaluar las capacidades de la biblioteca antes de comprar una licencia.

### ¿Dónde puedo encontrar más ejemplos y documentación?

 Para obtener más ejemplos, documentación e información detallada sobre Aspose.Words para Java, visite el sitio[documentación](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
