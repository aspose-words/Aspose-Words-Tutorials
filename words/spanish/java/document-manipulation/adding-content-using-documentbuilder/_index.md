---
date: 2026-01-01
description: Aprenda a crear campos de formulario y agregar texto, tablas, imágenes,
  hipervínculos y más usando Aspose.Words para Java DocumentBuilder. Una guía paso
  a paso para desarrolladores.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Cómo crear campos de formulario y agregar contenido usando DocumentBuilder
  en Aspose.Words para Java
url: /es/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Añadir contenido usando DocumentBuilder en Aspose.Words para Java

## Introducción a añadir contenido usando DocumentBuilder en Aspose.Words para Java

En esta guía paso a paso, **creará campos de formulario** y añadirá una variedad de contenido—texto, tablas, reglas horizontales, HTML, hipervínculos, imágenes y más—en un documento Word con Aspose.Words para Java. Ya sea que esté creando un informe, una plantilla de contrato o un formulario interactivo, la clase `DocumentBuilder` le brinda un control detallado sobre cada elemento. ¡Vamos allá!

## Respuestas rápidas
- **¿Cómo creo campos de formulario?** Use `insertTextInput`, `insertCheckBox` o `insertComboBox` en un `DocumentBuilder`.
- **¿Qué método agrega texto plano?** Llame a `builder.write("Your text")` o `builder.writeln("Your text")`.
- **¿Puedo insertar una regla horizontal?** Sí—`builder.insertHorizontalRule()` agrega una línea separadora.
- **¿Cómo incrustar HTML?** Use `builder.insertHtml("<p>HTML content</p>")`.
- **¿Cómo añadir una imagen en línea?** `builder.insertImage("path/to/image.png")` coloca la imagen dentro del flujo de texto.

## ¿Qué es DocumentBuilder y por qué usarlo para crear campos de formulario?

`DocumentBuilder` es la API fluida de Aspose.Words para construir y editar documentos Word de forma programática. Abstracta la estructura OpenXML de bajo nivel, permitiéndole centrarse en *qué* quiere añadir—como **campos de formulario**—en lugar de *cómo* se ve el XML. Esto lo hace ideal para generar formularios dinámicos, contratos o cualquier documento que requiera interacción del usuario.

## Requisitos previos

Antes de comenzar, asegúrese de tener la biblioteca Aspose.Words para Java instalada en su proyecto. Puede descargarla [aquí](https://releases.aspose.com/words/java/).

## Añadir texto (cómo añadir texto)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir tablas

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir una regla horizontal (añadir regla horizontal)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir campos de formulario (crear campos de formulario)

### Campo de formulario de entrada de texto

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Campo de formulario de casilla de verificación

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Campo de formulario de lista desplegable

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir HTML (insertar html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir hipervínculos (cómo añadir hipervínculo)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir una tabla de contenido

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir imágenes

### Imagen en línea (insertar imagen en línea)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Imagen flotante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Añadir párrafos

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Mover el cursor (Paso 10)

Puede controlar la posición del cursor dentro del documento usando métodos como `moveToParagraph`, `moveToCell`, etc.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Estas son algunas operaciones comunes que puede realizar usando `DocumentBuilder` de Aspose.Words para Java. Explore la documentación de la biblioteca para obtener funciones avanzadas y opciones de personalización. ¡Feliz creación de documentos!

## Conclusión

En esta guía completa, hemos mostrado cómo **crear campos de formulario** y añadir varios tipos de contenido—texto, tablas, reglas horizontales, HTML, hipervínculos, una tabla de contenido, imágenes, párrafos con formato y navegación del cursor—usando `DocumentBuilder` de Aspose.Words para Java. Ahora tiene una base sólida para generar documentos Word dinámicos e interactivos de forma programática.

## Preguntas frecuentes

### P: ¿Qué es Aspose.Words para Java?

R: Aspose.Words para Java es una biblioteca Java que permite a los desarrolladores crear, modificar y manipular documentos Microsoft Word de forma programática. Proporciona una amplia gama de funciones para generación de documentos, formato e inserción de contenido.

### P: ¿Cómo puedo añadir una tabla de contenido a mi documento?

R: Para añadir una tabla de contenido, use `DocumentBuilder` para insertar un campo TOC y luego llame a `doc.updateFields()` después de agregar su contenido.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### P: ¿Cómo inserto imágenes en un documento usando Aspose.Words para Java?

R: Puede insertar imágenes, tanto en línea como flotantes, usando `DocumentBuilder`.

#### Imagen en línea:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Imagen flotante:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### P: ¿Puedo dar formato al texto y a los párrafos al añadir contenido?

R: Sí, puede dar formato al texto y a los párrafos usando `DocumentBuilder`. Establezca propiedades de fuente, alineación de párrafo, sangría y más antes de escribir el contenido.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### P: ¿Cómo puedo mover el cursor a una ubicación específica dentro del documento?

R: Use métodos como `moveToParagraph`, `moveToCell`, etc., para posicionar el cursor antes de insertar nuevo contenido.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Estas respuestas cubren los escenarios más comunes al trabajar con `DocumentBuilder` de Aspose.Words para Java. Para más detalles, consulte la [documentación de la biblioteca](https://reference.aspose.com/words/java/) o únase a la comunidad de Aspose.Words para obtener soporte.

---

**Última actualización:** 2026-01-01  
**Probado con:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}