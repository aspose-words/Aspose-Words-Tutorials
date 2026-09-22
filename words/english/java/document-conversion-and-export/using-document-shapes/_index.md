---
title: Using Document Shapes in Aspose.Words for Java
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
description: Learn how to **insert image shape** with Aspose.Words for Java. This guide shows you how to add shapes, create text box shapes, place shapes in tables, set shape aspect ratio, and add callout shapes.
weight: 14
url: /java/document-conversion-and-export/using-document-shapes/
date: 2025-12-14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to **insert image shape** with Aspose.Words for Java

In this comprehensive tutorial you’ll discover how to **insert image shape** objects into Word documents using Aspose.Words for Java. Whether you’re building reports, marketing collateral, or interactive forms, shapes let you add callouts, buttons, text boxes, watermarks, and even SmartArt. We’ll walk through each step, explain why you’d use a particular shape, and provide ready‑to‑run code snippets.

## Quick Answers
- **What is the primary way to add a shape?** Use `DocumentBuilder.insertShape` or create a `Shape` instance and add it to the document tree.  
- **Can I insert an image as a shape?** Yes – call `builder.insertImage` and then treat the returned `Shape` like any other.  
- **How do I keep a shape’s aspect ratio?** Set `shape.setAspectRatioLocked(true)` or `false` depending on your needs.  
- **Is it possible to group shapes?** Absolutely – wrap them in a `GroupShape` and insert the group as a single node.  
- **Do SmartArt diagrams work with Aspose.Words?** Yes, you can detect and update SmartArt shapes programmatically.

## What is **insert image shape**?
An *image shape* is a visual element that holds raster or vector graphics inside a Word document. In Aspose.Words, an image is represented by a `Shape` object, giving you full control over size, position, rotation, and wrapping.

## Why use shapes in your documents?
- **Visual impact:** Shapes draw attention to key information.  
- **Interactivity:** Buttons and callouts can be linked to URLs or bookmarks.  
- **Layout flexibility:** Position graphics precisely with absolute or relative coordinates.  
- **Automation:** Generate complex layouts without manual editing.

## Prerequisites
- Java Development Kit (JDK 8 or higher)  
- Aspose.Words for Java library (download from the official site)  
- Basic knowledge of Java and object‑oriented programming  

You can download the library here: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

## How to **add shape** – Inserting a GroupShape
A `GroupShape` lets you treat several shapes as a single unit. This is useful for moving or formatting multiple elements together.

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

## Create **text box shape**
A text box is a container that can hold formatted text. You can also rotate it for a dynamic look.

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

## Set **shape aspect ratio**
Sometimes you need a shape to stretch freely, other times you want to keep its original proportions. Controlling the aspect ratio is straightforward.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Place **shape in table**
Embedding a shape inside a table cell can be handy for report layouts. The example below creates a table and then inserts a watermark‑style shape that spans the whole page.

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

## Add **callout shape**
A callout shape is perfect for highlighting notes or warnings. While the code above already demonstrates an `ACCENT_BORDER_CALLOUT_1`, you can swap the `ShapeType` to any callout variant to suit your design.

## Working with SmartArt Shapes

### Detect SmartArt Shapes
SmartArt diagrams can be identified programmatically, allowing you to process or replace them as needed.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Update SmartArt Drawings
Once detected, you can refresh the SmartArt graphics to reflect any data changes.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Common Issues & Tips
- **Shape not appearing:** Ensure the shape is inserted after the target node using `builder.insertNode`.  
- **Unexpected rotation:** Remember that rotation is applied around the shape’s center; adjust `setLeft`/`setTop` if needed.  
- **Aspect ratio locked:** By default, many shapes lock their aspect ratio; call `setAspectRatioLocked(false)` to stretch freely.  
- **SmartArt detection fails:** Verify you are using Aspose.Words version that supports SmartArt (v24+).

## Frequently Asked Questions

**Q: What is Aspose.Words for Java?**  
A: Aspose.Words for Java is a Java library that allows developers to create, modify, and convert Word documents programmatically. It provides a wide range of features and tools for working with documents in various formats.

**Q: How can I download Aspose.Words for Java?**  
A: You can download Aspose.Words for Java from the Aspose website by following this link: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

**Q: What are the benefits of using document shapes?**  
A: Document shapes add visual elements and interactivity to your documents, making them more engaging and informative. With shapes, you can create callouts, buttons, images, watermarks, and more, enhancing the overall user experience.

**Q: Can I customize the appearance of shapes?**  
A: Yes, you can customize the appearance of shapes by adjusting their properties such as size, position, rotation, and fill color. Aspose.Words for Java provides extensive options for shape customization.

**Q: Is Aspose.Words for Java compatible with SmartArt?**  
A: Yes, Aspose.Words for Java supports SmartArt shapes, allowing you to work with complex diagrams and graphics in your documents.

---

**Last Updated:** 2025-12-14  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}