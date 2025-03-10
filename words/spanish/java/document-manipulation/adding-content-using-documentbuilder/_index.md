---
title: Cómo agregar contenido mediante DocumentBuilder en Aspose.Words para Java
linktitle: Cómo agregar contenido mediante DocumentBuilder
second_title: API de procesamiento de documentos Java Aspose.Words
description: Domine la creación de documentos con Aspose.Words para Java. Una guía paso a paso para agregar texto, tablas, imágenes y más. Cree documentos de Word impresionantes sin esfuerzo.
weight: 26
url: /es/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar contenido mediante DocumentBuilder en Aspose.Words para Java


## Introducción a la adición de contenido mediante DocumentBuilder en Aspose.Words para Java

En esta guía paso a paso, exploraremos cómo usar DocumentBuilder de Aspose.Words para Java para agregar varios tipos de contenido a un documento de Word. Cubriremos la inserción de texto, tablas, reglas horizontales, campos de formulario, HTML, hipervínculos, tabla de contenido, imágenes en línea y flotantes, párrafos y más. ¡Comencemos!

## Prerrequisitos

 Antes de comenzar, asegúrese de tener la biblioteca Aspose.Words para Java configurada en su proyecto. Puede descargarla desde[aquí](https://releases.aspose.com/words/java/).

## Agregar texto

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar un párrafo de texto simple
builder.write("This is a simple text paragraph.");

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Agregar tablas

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Iniciar una mesa
Table table = builder.startTable();

// Insertar celdas y contenido
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Terminar la mesa
builder.endTable();

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Agregar regla horizontal

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar una regla horizontal
builder.insertHorizontalRule();

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Agregar campos de formulario

### Campo de formulario de entrada de texto

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar un campo de formulario de entrada de texto
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Guardar el documento
doc.save("path/to/your/document.docx");
```

### Campo de formulario de casilla de verificación

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar un campo de formulario de casilla de verificación
builder.insertCheckBox("CheckBox", true, true, 0);

// Guardar el documento
doc.save("path/to/your/document.docx");
```

### Campo de formulario de cuadro combinado

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Definir elementos para el cuadro combinado
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insertar un campo de formulario de cuadro combinado
builder.insertComboBox("DropDown", items, 0);

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Añadiendo HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar contenido HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Agregar hipervínculos

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar un hipervínculo
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", falso);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Cómo agregar una tabla de contenido

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar una tabla de contenidos
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Agregar contenido al documento
// ...

// Actualizar la tabla de contenidos
doc.updateFields();

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Agregar imágenes

### Imagen en línea

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar una imagen en línea
builder.insertImage("path/to/your/image.png");

// Guardar el documento
doc.save("path/to/your/document.docx");
```

### Imagen flotante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar una imagen flotante
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Agregar párrafos

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Establecer el formato del párrafo
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

// Insertar un párrafo
builder.writeln("This is a formatted paragraph.");

// Guardar el documento
doc.save("path/to/your/document.docx");
```

## Paso 10: mover el cursor

 Puede controlar la posición del cursor dentro del documento utilizando varios métodos como`moveToParagraph`, `moveToCell`y más. Aquí tienes un ejemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mueva el cursor a un párrafo específico
builder.moveToParagraph(2, 0);

// Agregar contenido en la nueva posición del cursor
builder.writeln("This is the 3rd paragraph.");
```

Estas son algunas operaciones comunes que puede realizar utilizando Aspose.Words para DocumentBuilder de Java. Explore la documentación de la biblioteca para obtener funciones más avanzadas y opciones de personalización. ¡Feliz creación de documentos!


## Conclusión

En esta guía completa, hemos explorado las capacidades de DocumentBuilder de Aspose.Words para Java para agregar varios tipos de contenido a documentos de Word. Hemos cubierto texto, tablas, reglas horizontales, campos de formulario, HTML, hipervínculos, tabla de contenido, imágenes, párrafos y movimiento del cursor.

## Preguntas frecuentes

### P: ¿Qué es Aspose.Words para Java?

A: Aspose.Words para Java es una biblioteca Java que permite a los desarrolladores crear, modificar y manipular documentos de Microsoft Word mediante programación. Ofrece una amplia gama de funciones para la generación, el formato y la inserción de contenido de documentos.

### P: ¿Cómo puedo agregar una tabla de contenido a mi documento?

A: Para agregar una tabla de contenido, utilice el`DocumentBuilder` para insertar un campo de tabla de contenido en su documento. Asegúrese de actualizar los campos del documento después de agregar contenido para completar la tabla de contenido. A continuación, se muestra un ejemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar un campo de tabla de contenido
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Agregar contenido al documento
// ...

// Actualizar la tabla de contenidos
doc.updateFields();
```

### P: ¿Cómo puedo insertar imágenes en un documento usando Aspose.Words para Java?

 A: Puede insertar imágenes, tanto en línea como flotantes, utilizando el`DocumentBuilder`A continuación se muestran ejemplos de ambos:

#### Imagen en línea:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar una imagen en línea
builder.insertImage("path/to/your/image.png");
```

#### Imagen flotante:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar una imagen flotante
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### P: ¿Puedo formatear texto y párrafos al agregar contenido?

 R: Sí, puedes formatear texto y párrafos usando el`DocumentBuilder`Puede configurar las propiedades de fuente, la alineación de párrafos, la sangría y más. A continuación, se muestra un ejemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Establecer el formato de fuente y párrafo
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

// Insertar un párrafo formateado
builder.writeln("This is a formatted paragraph.");
```

### P: ¿Cómo puedo mover el cursor a una ubicación específica dentro del documento?

 A: Puede controlar la posición del cursor utilizando métodos como`moveToParagraph`, `moveToCell`y más. Aquí tienes un ejemplo:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Mueva el cursor a un párrafo específico
builder.moveToParagraph(2, 0);

// Agregar contenido en la nueva posición del cursor
builder.writeln("This is the 3rd paragraph.");
```

Estas son algunas preguntas y respuestas comunes que lo ayudarán a comenzar a usar Aspose.Words para DocumentBuilder de Java. Si tiene más preguntas o necesita más ayuda, consulte la[documentación de la biblioteca](https://reference.aspose.com/words/java/) o busque ayuda de la comunidad Aspose.Words y recursos de soporte.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
