---
category: general
date: 2026-09-18
description: Create blank document and insert shapes to Word with Aspose.Words – learn
  how to add a triangle shape and more.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: en
lastmod: 2026-09-18
og_description: Create blank document in Word using Aspose.Words and learn how to
  insert a triangle shape, group shapes, and other graphics. Follow this complete
  guide.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Create blank document and add shapes to Word – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: How to create blank document and add shapes to Word
url: /java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create blank document and add shapes to Word

If you need to **create blank document** and then enrich it with graphics, this guide shows you exactly how. We'll walk through creating a Word file from scratch and **add shapes to Word**, including **how to insert triangle** shape, using Aspose.Words for Java.

You’ll finish the tutorial with a ready‑to‑use *.docx* file that contains a grouped shape holding a triangle. The steps cover everything from project setup to saving the final **create word document**. No external tools are required beyond Aspose.Words.

## Prerequisites

Before you start, make sure you have:

* Java 17 or later installed  
* Maven or Gradle for dependency management  
* An Aspose.Words for Java license (the free evaluation works for this demo)  

If you prefer a different build system, adjust the dependency syntax accordingly. The code works on any platform that supports Java.

## Create blank document with Aspose.Words

The first operation is to **create blank document** in memory. Aspose.Words provides a `Document` class that represents a Word file without any content.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

The `new Document()` constructor builds an empty *.docx* structure, which you can later populate with paragraphs, tables, or graphics. Because the document is blank, you have full control over every element you add.

## Add shapes to Word – inserting a group shape

A group shape lets you treat several graphics as a single unit. This is useful when you want to move or resize multiple shapes together.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` is the primary API for adding content. The `insertGroupShape` call creates a container that is 300 × 300 points (approximately 4 × 4 inches). After this call the cursor is positioned *inside* the group, ready for additional shapes.

### Why use a group shape?

Grouping keeps related graphics aligned and makes it easier to apply uniform formatting. If you later decide to move the triangle, the whole group moves together, preserving layout.

## How to insert triangle shape inside the group

Now we address **how to insert triangle** shape. The triangle is one of the built‑in `ShapeType` values.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

The `moveTo` call ensures the builder’s insertion point is the first paragraph of the group. `insertShape` then adds a triangle that is 60 × 60 points. Because the cursor is inside the group, the triangle becomes a child of the group shape.

**Add triangle shape** tips:

* The size is measured in points; 72 points equal one inch. Adjust the dimensions to suit your layout.  
* If you need a different orientation, use `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` to align the shape within the group.  
* The triangle inherits the group’s fill and line styles unless you override them with `shape.getFillColor()` or `shape.getStrokeColor()`.

## Save the document – create word document

After constructing the graphics, you save the file. This step finalizes the **create word document** operation.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` writes the in‑memory representation to disk as a standard Word document. You can open `ExtendedGroup.docx` in Microsoft Word, LibreOffice, or any viewer that supports the OOXML format. The file will display a grouped shape containing a triangle, exactly as built by the code.

## Full runnable example

Putting all pieces together, here is the complete program you can copy, compile, and run:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Expected result

When you open `ExtendedGroup.docx`, you will see a single group shape occupying the center of the page. Inside that group, a small triangle appears at the default position. The triangle can be selected and moved as part of the group, confirming that **add shapes to word** worked as intended.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| *Can I add more than one shape inside the group?* | Yes. After inserting the triangle, keep the cursor inside the group and call `builder.insertShape` again with a different `ShapeType`. |
| *What if I need the triangle to be red?* | Retrieve the `Shape` returned by `insertShape` and call `shape.getFillColor().setColor(Color.RED)`. |
| *Does this work with older .doc files?* | Aspose.Words saves in the format you specify. Use `doc.save("file.doc", SaveFormat.DOC)` to create a legacy Word document. |
| *How do I change the group’s border?* | Use `group.getStrokeColor().setColor(Color.BLUE)` and `group.setLineWeight(2.0)` to customize the outline. |
| *Is there a way to rotate the triangle?* | Call `shape.getRotation()` to set an angle in degrees. |

## Pro tips

* **Reuse the builder** – creating a new `DocumentBuilder` for each shape adds overhead. Keep a single builder per document.  
* **Unit conversion** – if you work with millimeters, convert them to points (`points = mm * 2.83465`).  
* **Performance** – for large documents, call `doc.updatePageLayout()` only once after all shapes are added.

## Conclusion

You now know how to **create blank document**, **add shapes to Word**, and specifically **how to insert triangle** shape using Aspose.Words for Java. The complete example demonstrates the full workflow from an empty file to a saved **create word document** that contains a grouped triangle.

From here you can explore additional `ShapeType` values, apply custom styling, or combine multiple groups to build complex diagrams. Experiment with different sizes, colors, and positions to master Word automation in Java.

--- 

*Ready to automate your next report? Clone the example, tweak the dimensions, and integrate the code into your own application today.*


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}