---
title: How to create text box and use Document Shapes in Aspose.Words for Java
linktitle: Using Document Shapes
second_title: Aspose.Words Java Document Processing API
description: Learn how to create text box, add watermark word, group multiple shapes, set shape aspect ratio, and place shape in a table cell using Aspose.Words for Java.
weight: 14
url: /java/document-conversion-and-export/using-document-shapes/
date: 2026-02-16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using Document Shapes in Aspose.Words for Java

## Introduction to Using Document Shapes in Aspose.Words for Java

In this comprehensive guide, **you’ll learn how to create text box** objects and other powerful shapes with Aspose.Words for Java. Shapes let you enrich Word documents with callouts, buttons, watermarks, SmartArt, and more—making them visually engaging and interactive. We’ll walk through real‑world examples, from inserting a simple text box to grouping multiple shapes, setting aspect ratios, and placing shapes inside table cells.

## Quick Answers
- **What is the primary way to add a text box?** Use `DocumentBuilder.insertShape(ShapeType.TEXT_BOX, …)`.
- **Can I group shapes together?** Yes – create a `GroupShape` and append child shapes.
- **How do I lock or unlock a shape’s aspect ratio?** Call `shape.setAspectRatioLocked(true/false)`.
- **Is it possible to add a watermark with a shape?** Absolutely – insert a `Shape` with `TEXT_PLAIN_TEXT` and set its fill/stroke.
- **Do SmartArt diagrams work with Aspose.Words?** Yes – detect with `shape.hasSmartArt()` and update via `shape.updateSmartArtDrawing()`.

## What is a text box and why create text box shapes?

A text box is a container that can hold formatted text, images, or other shapes. Using **create text box** in your automation lets you place floating content anywhere on a page, perfect for annotations, callouts, or decorative elements without altering the main document flow.

## How to add shape

Before we dive into code, ensure Aspose.Words for Java is referenced in your project. If you haven’t added it yet, download the library from the official site:

[Download Aspose.Words for Java](https://releases.aspose.com/words/java/)

### Adding Shapes to Documents

## How to group multiple shapes

A `GroupShape` lets you treat several individual shapes as a single unit—useful for moving or rotating them together.

### Inserting a GroupShape

Below is a complete example that creates a group, adds two different shapes, and inserts the group into the document.

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

## How to create a text box (create text box)

### Inserting a Text Box Shape

The `insertShape` method makes it straightforward to add a text box. The example below shows two ways to position and rotate a text box.

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

## How to set shape aspect ratio

### Managing Aspect Ratio

Sometimes you need a shape to stretch without preserving its original proportions. The following snippet demonstrates unlocking the aspect ratio of an image shape.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Shape shape = builder.insertImage(getImagesDir() + "Transparent background logo.png");
shape.setAspectRatioLocked(false);

doc.save("Your Directory Path" + "WorkingWithShapes.AspectRatioLocked.docx");
```

## How to place shape in a table cell

### Placing a Shape Inside a Table Cell

Below is a step‑by‑step example that builds a table, then inserts a watermark shape that is positioned relative to the page but can also be placed inside a cell.

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

You can programmatically find SmartArt objects in a document using the `hasSmartArt()` method.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
List<Shape> shapes = IterableUtils.toList(doc.getChildNodes(NodeType.SHAPE, true));
int count = (int) shapes.stream().filter(s -> s.hasSmartArt()).count();
System.out.println("The document has " + count + " shapes with SmartArt.");
```

### Updating SmartArt Drawings

Once you’ve located SmartArt shapes, you can refresh their internal drawing data with `updateSmartArtDrawing()`.

```java
Document doc = new Document("Your Directory Path" + "SmartArt.docx");
for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true)) {
    if (shape.hasSmartArt())
        shape.updateSmartArtDrawing();
}
```

## Conclusion

In this guide, we’ve covered how to **create text box** objects, group multiple shapes, adjust aspect ratios, embed shapes inside table cells, add watermarks, and work with SmartArt diagrams using Aspose.Words for Java. These techniques empower you to build richly formatted, interactive Word documents programmatically.

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

## Frequently Asked Questions

**Q: Can I combine a text box with an image inside the same shape?**  
A: Yes. Insert an image into the text box shape using `builder.insertImage()` after creating the shape, then adjust its layout as needed.

**Q: How do I ensure a watermark appears behind all document content?**  
A: Set the shape’s `WrapType` to `NONE` and adjust its `RelativeHorizontalPosition` and `RelativeVerticalPosition` to `PAGE`. This positions the watermark behind the main flow.

**Q: Is it possible to animate a grouped shape in Word?**  
A: While Aspose.Words can create and group shapes, animation features are not supported because they rely on Word’s UI capabilities.

**Q: What version of Aspose.Words is required for SmartArt support?**  
A: SmartArt detection and updating are available starting from Aspose.Words 20.9 for Java and later.

**Q: Does the library handle large documents with many shapes efficiently?**  
A: Yes. Use `doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2010)` or higher to improve performance on documents with many shapes.

---

**Last Updated:** 2026-02-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}