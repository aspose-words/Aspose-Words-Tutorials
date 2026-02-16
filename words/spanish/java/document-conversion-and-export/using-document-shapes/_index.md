---
date: 2026-02-16
description: Aprenda cómo crear un cuadro de texto, agregar una marca de agua de palabra,
  agrupar varias formas, establecer la relación de aspecto de la forma y colocar la
  forma en una celda de tabla usando Aspose.Words para Java.
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
title: Cómo crear un cuadro de texto y usar formas de documento en Aspose.Words para
  Java
url: /es/java/document-conversion-and-export/using-document-shapes/
weight: 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uso de Formas de Documento en Aspose.Words para Java

## Introducción al Uso de Formas de Documento en Aspose.Words para Java

En esta guía completa, **aprenderá cómo crear objetos de cuadro de texto** y otras formas poderosas con Aspose.Words para Java. Las formas le permiten enriquecer los documentos de Word con llamadas, botones, marcas de agua, SmartArt y más, haciéndolos visualmente atractivos e interactivos. Recorreremos ejemplos del mundo real, desde insertar un cuadro de texto simple hasta agrupar múltiples formas, establecer relaciones de aspecto y colocar formas dentro de celdas de tabla.

## Respuestas rápidas
- **¿Cuál es la forma principal de agregar un cuadro de texto?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **¿Puedo agrupar formas juntas?** Sí – cree un `GroupShape` y añada formas hijas.
- **¿Cómo bloqueo o desbloqueo la relación de aspecto de una forma?** Llame a `shape.setAspectRatioLocked(true/false)`.
- **¿Es posible agregar una marca de agua con una forma?** Absolutamente – inserte un `Shape` con `TEXT_PLAIN_TEXT` y configure su relleno/trazo.
- **¿Los diagramas SmartArt funcionan con Aspose.Words?** Sí – detecte con `shape.hasSmartArt()` y actualice mediante `shape.updateSmartArtDrawing()`.

## ¿Qué es un cuadro de texto y por qué crear formas de cuadro de texto?

Un cuadro de texto es un contenedor que puede contener texto con formato, imágenes u otras formas. Usar **crear cuadro de texto** en su automatización le permite colocar contenido flotante en cualquier parte de una página, perfecto para anotaciones, llamadas o elementos decorativos sin alterar el flujo principal del documento.

## Cómo agregar una forma

Antes de sumergirnos en el código, asegúrese de que Aspose.Words para Java esté referenciado en su proyecto. Si aún no lo ha añadido, descargue la biblioteca desde el sitio oficial:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Agregar formas a documentos

## Cómo agrupar múltiples formas

Un `GroupShape` le permite tratar varias formas individuales como una sola unidad—útil para moverlas o rotarlas juntas.

### Insertar un GroupShape

A continuación se muestra un ejemplo completo que crea un grupo, añade dos formas diferentes y inserta el grupo en el documento.

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

## Cómo crear un cuadro de texto (crear cuadro de texto)

### Insertar una forma de cuadro de texto

El método `insertShape` facilita la inserción de un cuadro de texto. El ejemplo a continuación muestra dos formas de posicionar y rotar un cuadro de texto.

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

## Cómo establecer la relación de aspecto de una forma

### Gestión de la relación de aspecto

A veces necesita que una forma se estire sin conservar sus proporciones originales. El fragmento siguiente demuestra cómo desbloquear la relación de aspecto de una forma de imagen.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Cómo colocar una forma en una celda de tabla

### Colocar una forma dentro de una celda de tabla

A continuación se muestra un ejemplo paso a paso que crea una tabla y luego inserta una forma de marca de agua que se posiciona respecto a la página pero también puede colocarse dentro de una celda.

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
watermark.isLayoutInCell(true); // Display the shape outside of the table cell if it will be placed into a cell.
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

## Trabajo con formas SmartArt

### Detección de formas SmartArt

Puede encontrar programáticamente objetos SmartArt en un documento usando el método `hasSmartArt()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Actualización de dibujos SmartArt

Una vez que haya localizado las formas SmartArt, puede actualizar sus datos internos de dibujo con `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusión

En esta guía, hemos cubierto cómo **crear cuadros de texto**, agrupar múltiples formas, ajustar relaciones de aspecto, incrustar formas dentro de celdas de tabla, agregar marcas de agua y trabajar con diagramas SmartArt usando Aspose.Words para Java. Estas técnicas le permiten crear documentos de Word con formato rico e interactivo de forma programática.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para Java?

Aspose.Words para Java es una biblioteca Java que permite a los desarrolladores crear, modificar y convertir documentos de Word programáticamente. Proporciona una amplia gama de funciones y herramientas para trabajar con documentos en varios formatos.

### ¿Cómo puedo descargar Aspose.Words para Java?

Puede descargar Aspose.Words para Java desde el sitio web de Aspose siguiendo este enlace: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### ¿Cuáles son los beneficios de usar formas de documento?

Las formas de documento añaden elementos visuales e interactividad a sus documentos, haciéndolos más atractivos e informativos. Con las formas, puede crear llamadas, botones, imágenes, marcas de agua y más, mejorando la experiencia del usuario.

### ¿Puedo personalizar la apariencia de las formas?

Sí, puede personalizar la apariencia de las formas ajustando sus propiedades como tamaño, posición, rotación y color de relleno. Aspose.Words para Java ofrece amplias opciones para la personalización de formas.

### ¿Aspose.Words para Java es compatible con SmartArt?

Sí, Aspose.Words para Java admite formas SmartArt, lo que le permite trabajar con diagramas y gráficos complejos en sus documentos.

## Preguntas frecuentes (FAQ)

**P: ¿Puedo combinar un cuadro de texto con una imagen dentro de la misma forma?**  
R: Sí. Inserte una imagen en la forma de cuadro de texto usando `builder.insertImage()` después de crear la forma, luego ajuste su diseño según sea necesario.

**P: ¿Cómo garantizo que una marca de agua aparezca detrás de todo el contenido del documento?**  
R: Establezca el `WrapType` de la forma a `NONE` y ajuste su `RelativeHorizontalPosition` y `RelativeVerticalPosition` a `PAGE`. Esto posiciona la marca de agua detrás del flujo principal.

**P: ¿Es posible animar una forma agrupada en Word?**  
R: Aunque Aspose.Words puede crear y agrupar formas, las funciones de animación no son compatibles porque dependen de las capacidades de la interfaz de Word.

**P: ¿Qué versión de Aspose.Words se requiere para el soporte de SmartArt?**  
R: La detección y actualización de SmartArt están disponibles a partir de Aspose.Words 20.9 para Java y versiones posteriores.

**P: ¿La biblioteca maneja documentos grandes con muchas formas de manera eficiente?**  
R: Sí. Use `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` o una versión superior para mejorar el rendimiento en documentos con muchas formas.

---

**Última actualización:** 2026-02-16  
**Probado con:** Aspose.Words para Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}