---
title: Uso de formas de documentos en Aspose.Words para Java
linktitle: Uso de formas de documentos
second_title: API de procesamiento de documentos Java Aspose.Words
description: Descubra el poder de las formas de documentos en Aspose.Words para Java. Aprenda a crear documentos visualmente atractivos con ejemplos paso a paso.
weight: 14
url: /es/java/document-conversion-and-export/using-document-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uso de formas de documentos en Aspose.Words para Java


## Introducción al uso de formas de documentos en Aspose.Words para Java

En esta guía completa, profundizaremos en el mundo de las formas de documentos en Aspose.Words para Java. Las formas son elementos esenciales a la hora de crear documentos visualmente atractivos e interactivos. Ya sea que necesite agregar llamadas, botones, imágenes o marcas de agua, Aspose.Words para Java proporciona las herramientas para hacerlo de manera eficiente. Exploremos cómo usar estas formas paso a paso con ejemplos de código fuente.

## Introducción a las formas de documentos

 Antes de comenzar con el código, configuremos nuestro entorno. Asegúrese de tener Aspose.Words para Java integrado en su proyecto. Si aún no lo ha hecho, puede descargarlo desde el sitio web de Aspose.[Descargar Aspose.Words para Java](https://releases.aspose.com/words/java/)

## Cómo agregar formas a los documentos

### Insertar una GroupShape

 A`GroupShape` le permite agrupar varias formas. Aquí se explica cómo crear e insertar una`GroupShape`:

```java
Document doc = new Document();
doc.ensureMinimum();

GroupShape groupShape = new GroupShape(doc);
Shape accentBorderShape = new Shape(doc, ShapeType.ACCENT_BORDER_CALLOUT_1);
accentBorderShape.setWidth(100.0);
accentBorderShape.setHeight(100.0);

groupShape.appendChild(accentBorderShape);

Shape actionButtonShape = new Shape(doc, ShapeType.ACTION_BUTTON_BEGINNING);
actionButtonShape.setLeft(100.0);
actionButtonShape.setWidth(100.0);
actionButtonShape.setHeight(200.0);

groupShape.appendChild(actionButtonShape);

groupShape.setWidth(200.0);
groupShape.setHeight(200.0);
groupShape.setCoordSize(new Dimension(200, 200));

DocumentBuilder builder = new DocumentBuilder(doc);
builder.insertNode(groupShape);

doc.save("Your Directory Path" + "WorkingWithShapes.AddGroupShape.docx");
```

### Insertar una forma de cuadro de texto

 Para insertar una forma de cuadro de texto, puede utilizar el`insertShape` método como se muestra en el ejemplo siguiente:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertShape(ShapeType.TEXT_BOX, RelativeHorizontalPosition.PAGE, 100.0,
    RelativeVerticalPosition.PAGE, 100.0, 50.0, 50.0, WrapType.NONE);

shape.setRotation(30.0);
builder.writeln();

shape = builder.insertShape(ShapeType.TEXT_BOX, 50.0, 50.0);
shape.setRotation(30.0);

OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);

doc.save("Your Directory Path" + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Manipulación de propiedades de formas

### Administrar la relación de aspecto

Puedes controlar si la relación de aspecto de una forma está bloqueada o no. A continuación, te indicamos cómo desbloquear la relación de aspecto de una forma:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Colocar una forma en una celda de una tabla

Si necesita colocar una forma dentro de una celda de una tabla, puede lograrlo con el siguiente código:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

builder.startTable();
builder.getRowFormat().setHeight(100.0);
builder.getRowFormat().setHeightRule(HeightRule.EXACTLY);

for (int i = 0; i < 31; i++) {
    if (i != 0 && i % 7 == 0)
        builder.endRow();

    builder.insertCell();
    builder.write("Cell contents");
}

builder.endTable();

Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.isLayoutInCell(true); // Muestra la forma fuera de la celda de la tabla si se colocará dentro de una celda.
watermark.setWidth(300.0);
watermark.setHeight(70.0);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setRotation(-40);
watermark.setFillColor(Color.GRAY);
watermark.setStrokeColor(Color.GRAY);
watermark.getTextPath().setText("watermarkText");
watermark.getTextPath().setFontFamily("Arial");
watermark.setName("WaterMark_{Guid.NewGuid()}");
watermark.setWrapType(WrapType.NONE);

Run run = (Run) doc.getChildNodes(NodeType.RUN, true).get(doc.getChildNodes(NodeType.RUN, true).getCount() - 1);
builder.moveTo(run);
builder.insertNode(watermark);

doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010);
doc.save("Your Directory Path" + "WorkingWithShapes.LayoutInCell.docx");
```

## Trabajar con formas SmartArt

### Detección de formas SmartArt

Puede detectar formas SmartArt en un documento utilizando el siguiente código:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Actualización de dibujos SmartArt

Para actualizar dibujos SmartArt dentro de un documento, utilice el siguiente código:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusión

En esta guía, hemos explorado el mundo de las formas de documentos en Aspose.Words para Java. Aprendió a agregar varias formas a sus documentos, manipular sus propiedades y trabajar con formas SmartArt. Con este conocimiento, puede crear documentos visualmente atractivos e interactivos con facilidad.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para Java?

Aspose.Words para Java es una biblioteca Java que permite a los desarrolladores crear, modificar y convertir documentos de Word mediante programación. Ofrece una amplia gama de funciones y herramientas para trabajar con documentos en varios formatos.

### ¿Cómo puedo descargar Aspose.Words para Java?

 Puede descargar Aspose.Words para Java desde el sitio web de Aspose siguiendo este enlace:[Descargar Aspose.Words para Java](https://releases.aspose.com/words/java/)

### ¿Cuáles son los beneficios de utilizar formas de documentos?

Las formas de los documentos añaden elementos visuales e interactividad a los mismos, lo que los hace más atractivos e informativos. Con las formas, puede crear llamadas, botones, imágenes, marcas de agua y más, mejorando la experiencia general del usuario.

### ¿Puedo personalizar la apariencia de las formas?

Sí, puedes personalizar la apariencia de las formas ajustando sus propiedades, como el tamaño, la posición, la rotación y el color de relleno. Aspose.Words para Java ofrece amplias opciones para la personalización de formas.

### ¿Aspose.Words para Java es compatible con SmartArt?

Sí, Aspose.Words para Java admite formas SmartArt, lo que le permite trabajar con diagramas y gráficos complejos en sus documentos.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
