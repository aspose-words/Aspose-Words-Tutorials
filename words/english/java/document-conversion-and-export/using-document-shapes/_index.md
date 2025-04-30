---
title: Using Document Shapes in Aspose.Words for Java
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
description: Unlock the Power of Document Shapes in Aspose.Words for Java. Learn to Create Visually Engaging Documents with Step-by-Step Examples.
weight: 14
url: /java/document-conversion-and-export/using-document-shapes/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using Document Shapes in Aspose.Words for Java


## Introduction to Using Document Shapes in Aspose.Words for Java

In this comprehensive guide, we'll delve into the world of document shapes in Aspose.Words for Java. Shapes are essential elements when it comes to creating visually appealing and interactive documents. Whether you need to add callouts, buttons, images, or watermarks, Aspose.Words for Java provides the tools to do it efficiently. Let's explore how to use these shapes step by step with source code examples.

## Getting Started with Document Shapes

Before we jump into the code, let's set up our environment. Make sure you have Aspose.Words for Java integrated into your project. If you haven't already, you can download it from the Aspose website [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## Adding Shapes to Documents

### Inserting a GroupShape

A `GroupShape` allows you to group multiple shapes together. Here's how you can create and insert a `GroupShape`:

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

### Inserting a Text Box Shape

To insert a text box shape, you can use the `insertShape` method as shown in the example below:

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

## Manipulating Shape Properties

### Managing Aspect Ratio

You can control whether the aspect ratio of a shape is locked or not. Here's how to unlock the aspect ratio of a shape:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

### Placing a Shape in a Table Cell

If you need to place a shape inside a table cell, you can achieve this with the following code:

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

## Working with SmartArt Shapes

### Detecting SmartArt Shapes

You can detect SmartArt shapes in a document using the following code:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Updating SmartArt Drawings

To update SmartArt drawings within a document, use the following code:

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusion

In this guide, we've explored the world of document shapes in Aspose.Words for Java. You've learned how to add various shapes to your documents, manipulate their properties, and work with SmartArt shapes. With this knowledge, you can create visually appealing and interactive documents with ease.

## FAQ's

### What is Aspose.Words for Java?

Aspose.Words for Java is a Java library that allows developers to create, modify, and convert Word documents programmatically. It provides a wide range of features and tools for working with documents in various formats.

### How can I download Aspose.Words for Java?

You can download Aspose.Words for Java from the Aspose website by following this link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### What are the benefits of using document shapes?

Document shapes add visual elements and interactivity to your documents, making them more engaging and informative. With shapes, you can create callouts, buttons, images, watermarks, and more, enhancing the overall user experience.

### Can I customize the appearance of shapes?

Yes, you can customize the appearance of shapes by adjusting their properties such as size, position, rotation, and fill color. Aspose.Words for Java provides extensive options for shape customization.

### Is Aspose.Words for Java compatible with SmartArt?

Yes, Aspose.Words for Java supports SmartArt shapes, allowing you to work with complex diagrams and graphics in your documents.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
