---
category: general
date: 2026-11-22
description: Learn how to add shape to Word using Aspose.Words for Java – insert a
  rectangle and hide it programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: en
lastmod: 2026-11-22
og_description: Add shape to Word using Aspose.Words for Java. This tutorial shows
  how to insert a rectangle, hide the shape, and save the document.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Add shape to Word with Aspose.Words – Java guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: How to add shape to Word documents with Aspose.Words for Java
url: /java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to add shape to Word documents with Aspose.Words for Java

If you need to **add shape to Word** documents programmatically, Aspose.Words for Java makes it straightforward. In this guide you’ll learn **how to insert shape**, control its visibility, and **how to hide shape** so the final file looks exactly as you expect.

You’ll walk through a complete, runnable example that loads an existing `.docx`, inserts a rectangle, hides it, and saves the result. No external scripts or manual steps are required, and the tutorial covers common variations such as creating a new document from scratch or hiding a shape only when printing.

## Prerequisites

Before you start, make sure you have:

* Java 17 (or later) installed – earlier versions work but the latest LTS provides better performance.  
* Maven 3.8+ for dependency management.  
* A valid Aspose.Words for Java license (the free evaluation works for learning).  
* An IDE or text editor of your choice (e.g., IntelliJ IDEA, VS Code).

## Step 1: Add Aspose.Words to your Maven project

Add the following dependency to your `pom.xml`. This pulls the latest stable version (as of November 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Pro tip:** Use a `<scope>provided</scope>` clause if you plan to ship the JAR with your own licensing logic.

## Add shape to Word – initializing the document

The first functional step is to obtain a `Document` object. You can either load an existing file or create a fresh one.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Why this matters*: The `Document` class is the entry point for all Word manipulations. Loading an existing file preserves styles, headers, and footers, while a new document gives you a clean slate.

## How to insert shape in a Word document

Next, create a `DocumentBuilder` to modify the document’s content. The builder gives you methods for inserting text, tables, and **shapes**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

The `insertShape` call returns a `Shape` object that you can further configure (color, border, text, etc.). The dimensions are expressed in points (1 pt = 1/72 in).

*Why you might use a rectangle*: Rectangles are the most common container for annotations, watermarks, or placeholders. You can replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., to meet different visual needs.

## How to hide shape in Word

Sometimes you need a shape to exist for layout calculations but not appear in the final rendering. Aspose.Words provides the `setHidden(true)` method to achieve this.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

The hidden flag works like the **Hidden** formatting option in Microsoft Word: the shape is omitted from the visual layout but still participates in the document’s object model. This is useful for:

* Storing metadata or markers that your application reads later.  
* Creating placeholders that are removed just before publishing.  
* Controlling visibility for different output formats (e.g., hide in HTML but keep in PDF).

> **Note:** Hidden shapes are still exported to PDF by default. If you need them omitted from PDF as well, set `rectangle.getWrapType( ) = WrapType.NONE` and adjust the `Hidden` property accordingly.

## Step 4: Save the modified document

Finally, persist the changes to a new file.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

When you open `output.docx` in Microsoft Word, the rectangle will not be visible, but it remains part of the document tree. You can verify its presence programmatically by re‑loading the file and checking `Shape.isHidden()`.

### Expected output

* The file `output.docx` opens without any visible shapes.  
* If you inspect the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`), the shape count will be **1**, confirming that the shape exists but is hidden.

## Advanced variations and edge cases

### 1. Creating a shape in a fresh document

If you start from scratch, replace the load line with:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Positioning the shape precisely

By default, `insertShape` places the shape at the current cursor location. To position it absolutely:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Controlling visibility per output format

If you need the shape visible in the Word UI but hidden when exporting to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Adding text inside the shape

A rectangle can contain a text frame:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

You can then hide the text box with the same `setHidden(true)` call.

## Common pitfalls and how to avoid them

| Symptom | Cause | Fix |
|---------|-------|-----|
| Shape appears even after `setHidden(true)` | The document was saved before the hidden flag was set. | Ensure you call `setHidden(true)` **before** `doc.save()`. |
| Shape size looks distorted | Points vs. pixels confusion on high‑DPI screens. | Use points (72 pt = 1 in) for consistent sizing across platforms. |
| Hidden shape still prints | Some printers ignore the hidden flag. | Set `Shape.setWrapType(WrapType.NONE)` and also clear the `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Conclusion

You now know how to **add shape to Word** documents using Aspose.Words for Java, **how to insert shape**, and **how to hide shape** so it remains invisible to end users while still being part of the document structure. The complete example above loads a file, inserts a rectangle, hides it, and saves the result, covering both typical use‑cases and several edge cases.

From here you can explore related topics such as **how to insert shape** with custom fill colors, **how to hide shape in Word** for conditional printing, or automating bulk document processing with Aspose.Words. Experiment with different `ShapeType` values, positioning options, and visibility flags to fit your specific workflow.

Happy coding, and enjoy the flexibility that programmatic Word manipulation brings to your Java applications!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}