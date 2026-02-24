---
date: 2026-02-24
description: Aprende cómo convertir Word a Markdown usando Aspose.Words para Java.
  Esta guía cubre la alineación de tablas, el manejo de imágenes y cómo guardar el
  documento como Markdown.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Convertir Word a Markdown con Aspose.Words para Java
url: /es/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

 produce final content.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Convertir Word a Markdown con Aspose.Words para Java

## Introducción a Convertir Word a Markdown con Aspose.Words para Java

En este tutorial paso a paso aprenderás **cómo convertir Word a Markdown** usando la potente API de Aspose.Words para Java. Markdown es un lenguaje de marcado ligero que muchos desarrolladores y plataformas de contenido utilizan para documentación limpia y legible. Al final de esta guía podrás tomar cualquier archivo `.docx`, conservar tablas, imágenes y formato, y exportarlo como un archivo `.md` listo para generadores de sitios estáticos, READMEs de GitHub o cualquier flujo de trabajo compatible con markdown.

## Respuestas rápidas
- **¿Qué biblioteca necesito?** Aspose.Words para Java (`aspose-words.jar`).
- **¿Puedo personalizar la alineación de la tabla?** Sí – usa `TableContentAlignment` en `MarkdownSaveOptions`.
- **¿Cómo se manejan las imágenes?** Establece una carpeta de imágenes con `setImagesFolder()`; la biblioteca crea enlaces relativos.
- **¿Necesito una licencia para producción?** Se requiere una licencia comercial para uso no de prueba.
- **¿Es compatible con Java 17?** Sí, la biblioteca soporta Java 8 y superiores.

## ¿Qué es convertir Word a Markdown?

Convertir Word a Markdown significa tomar el formato enriquecido de un documento Microsoft Word y traducirlo a la sintaxis de markdown en texto plano. Este proceso conserva encabezados, listas, tablas y referencias de imágenes mientras elimina el formato binario, haciendo el contenido portátil y amigable para el control de versiones.

## ¿Por qué usar Aspose.Words para Java para guardar el documento como markdown?

* **Fidelidad total** – tablas, imágenes y diseños complejos se conservan.
* **Control granular** – puedes personalizar la alineación de tablas, rutas de imágenes y más.
* **Sin dependencias externas** – la biblioteca funciona inmediatamente sin necesidad de Office instalado.
* **Multiplataforma** – funciona en Windows, Linux y macOS con cualquier runtime de Java.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- Java Development Kit (JDK) instalado en tu sistema.
- Biblioteca Aspose.Words para Java. Puedes descargarla desde [here](https://releases.aspose.com/words/java/).

## Guía paso a paso

### Paso 1: Crear un documento Word que será convertido

Primero, creamos un documento Word sencillo que contiene una tabla de dos celdas. Este ejemplo muestra cómo se respeta la alineación de los párrafos dentro de las celdas de la tabla cuando más adelante **guardamos el documento como markdown**.

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

### Paso 2: Personalizar la alineación del contenido de la tabla

Aspose.Words para Java le permite controlar cómo se alinean las celdas de la tabla en el markdown generado. Usa la propiedad `TableContentAlignment` para **personalizar la alineación de la tabla** a izquierda, derecha, centro, o dejar que la biblioteca decida automáticamente según el primer párrafo de cada columna.

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

Al alternar esta configuración puedes **exportar tablas de Word a markdown** con la alineación exacta que necesites para los motores de renderizado posteriores.

### Paso 3: Manejar imágenes durante la conversión

Cuando su documento Word de origen contiene imágenes, debe indicar a Aspose.Words dónde colocar los archivos de imagen exportados. El método `setImagesFolder` en `MarkdownSaveOptions` define la carpeta que contendrá los recursos de imagen, y el markdown incluirá enlaces relativos a esos archivos.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Reemplace `"document_with_images.docx"` con la ruta a su archivo fuente y `"images_folder/"` con la carpeta de salida deseada para las imágenes.

### Código fuente completo para todos los escenarios

A continuación se muestra un ejemplo consolidado que muestra cómo **alinear automáticamente la tabla**, **personalizar la alineación** y **establecer una carpeta de imágenes** en un solo método. Este fragmento refleja el código original del tutorial y funciona sin cambios.

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

| Problema | Razón | Solución |
|----------|-------|----------|
| Las imágenes aparecen como enlaces rotos | `setImagesFolder` no está configurado o la ruta de la carpeta es incorrecta | Verifique que la ruta de la carpeta sea correcta y que la carpeta sea escribible |
| La alineación de la tabla se ve incorrecta | Valor incorrecto de `TableContentAlignment` | Use `TableContentAlignment.AUTO` para que el primer párrafo decida, o establezca explícitamente LEFT/RIGHT/CENTER |
| El archivo de salida está vacío | Opciones de guardado no pasadas a `doc.save()` | Asegúrese de pasar la instancia de `MarkdownSaveOptions` al método `save` |
| Características de Word no compatibles (p. ej., SmartArt) | Markdown no puede representar algunos objetos complejos | Convierta esos elementos a imágenes antes de guardar, o simplifique el documento de origen |

## Preguntas frecuentes

**P: ¿Cómo instalo Aspose.Words para Java?**  
R: Aspose.Words para Java se puede instalar incluyendo la biblioteca en su proyecto Java. Puede descargar la biblioteca desde [here](https://releases.aspose.com/words/java/) y seguir las instrucciones de instalación proporcionadas en la documentación.

**P: ¿Puedo convertir documentos Word complejos con tablas e imágenes a Markdown?**  
R: Sí, Aspose.Words para Java soporta la conversión de documentos Word complejos con tablas, imágenes y varios elementos de formato a Markdown. Puede personalizar la salida Markdown según la complejidad de su documento.

**P: ¿Cómo puedo manejar imágenes en archivos Markdown?**  
R: Para incluir imágenes en archivos Markdown, establezca la ruta de la carpeta de imágenes usando el método `setImagesFolder` en `MarkdownSaveOptions`. Asegúrese de que los archivos de imagen se almacenen en la carpeta especificada, y Aspose.Words para Java gestionará las referencias a las imágenes adecuadamente.

**P: ¿Existe una versión de prueba de Aspose.Words para Java disponible?**  
R: Sí, puede obtener una versión de prueba de Aspose.Words para Java desde el sitio web de Aspose. La versión de prueba le permite evaluar las capacidades de la biblioteca antes de comprar una licencia.

**P: ¿Dónde puedo encontrar más ejemplos y documentación?**  
R: Para más ejemplos, documentación e información detallada sobre Aspose.Words para Java, visite la [documentation](https://reference.aspose.com/words/java/).

## Conclusión

En esta guía cubrimos todo lo que necesita para **convertir Word a markdown** usando Aspose.Words para Java: crear un documento fuente, **personalizar la alineación de la tabla**, y manejar imágenes con la configuración adecuada de carpeta. Con estas técnicas podrá exportar de forma fiable contenido Word a markdown para blogs, sitios de documentación o cualquier plataforma que consuma markdown.

---

**Última actualización:** 2026-02-24  
**Probado con:** Aspose.Words para Java 24.12 (última versión al momento de escribir)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}