---
category: general
date: 2026-10-26
description: Learn how to create Word document programmatically, add a shape, and
  hide object in Word using Aspose.Words for Java – step‑by‑step guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: en
lastmod: 2026-10-26
og_description: Create Word document programmatically, learn how to add shape and
  hide object in Word with Aspose.Words for Java. Complete, runnable example.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Create Word document programmatically – add and hide shapes in Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Create a Word document programmatically, add and hide a shape in Java using Aspose.Words
url: /java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word document programmatically and add a shape in Java

If you need to **create Word document programmatically**, this tutorial shows you exactly how to do it, add a shape, and then hide the object in Word. Whether you are building a report generator or an automated contract system, you’ll get a complete, ready‑to‑run solution in just a few minutes.

You’ll learn how to:

* Initialize a Word document with Aspose.Words for Java.  
* Insert an ellipse (or any other shape) using the **how to add shape** technique.  
* Hide that shape so it never appears when the file is opened, answering the **how to hide shape** question.  

No external tools are required beyond the Aspose.Words library, and the code works with Java 17 and later.

## Prerequisites

Before you start, make sure you have:

* Java Development Kit (JDK) 17 or newer installed.  
* Maven or Gradle to manage dependencies (the example uses Maven).  
* A valid Aspose.Words for Java license (the free evaluation works for testing).  

If you are new to Aspose.Words, refer to the official Getting Started guide, but you won’t need to read it to follow this tutorial.

## Maven dependency

Add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Keep the version number up to date; newer releases contain bug fixes for shape handling.

## Step 1: Create Word document programmatically – initializing the document

The first thing you do when you **create Word document programmatically** is instantiate a `Document` object. This object represents the entire .docx file in memory.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step matters*: The `Document` class is the entry point for all Word‑processing operations. Without it you cannot add pages, paragraphs, or shapes.

## Step 2: How to add shape – inserting an ellipse

Now we address the **how to add shape** part of the tutorial. Aspose.Words supports many shape types (Ellipse, Rectangle, TextBox, etc.). Below we insert an ellipse with a width and height of 50 points.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

The `insertShape` method returns a `Shape` object that you can further customize—color, line style, rotation, and more. The coordinates are measured in points (1/72 inch).

*Why you might want to add a shape*: Shapes are useful for watermarks, decorative elements, or placeholders that you later hide or replace.

## Step 3: How to hide shape – making the object invisible in Word

To answer the **how to hide shape** question, simply set the shape’s `Hidden` property to `true`. This tells Word to treat the shape as a hidden object, so it never renders in the document view or printout.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

If you need to **hide object in Word** for a specific user or condition, you can toggle this property at runtime based on your business logic.

> **Note:** Hidden shapes are still part of the document’s XML structure. They can be revealed later by setting `setHidden(false)`.

## Step 4: Save the document

After adding and hiding the shape, write the document to disk.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

When you open `HiddenShapeDemo.docx` in Microsoft Word, you will see a blank page because the ellipse is hidden. The document otherwise behaves like any normal Word file.

## Full working example

Putting all the pieces together, here is the complete, runnable program:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Expected output**

```
Document created successfully.
```

Opening `HiddenShapeDemo.docx` shows an empty page; the hidden ellipse does not render, confirming that the **hide object in Word** operation succeeded.

## Edge cases and variations

| Situation | What to change | Why |
|-----------|----------------|-----|
| Hide a rectangle instead of an ellipse | Use `ShapeType.RECTANGLE` in `insertShape` | Different visual placeholder |
| Hide multiple shapes at once | Loop through `doc.getChildNodes(NodeType.SHAPE, true)` and set `setHidden(true)` | Useful for bulk processing |
| Show the shape only in print view | Set `shape.setVisible(false)` and `shape.setPrint(true)` | Word distinguishes between screen and print visibility |
| Use a different measurement unit | Call `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Aligns with your layout requirements |

## Common pitfalls

* **Forgetting to call `setHidden(true)`** – the shape will appear as normal.  
* **Saving the document before hiding the shape** – order matters; hide first, then save.  
* **Using an outdated Aspose.Words version** – older releases may lack the `setHidden` API.  

Always test the generated file in the target version of Microsoft Word to ensure the hidden state behaves as expected.

## Conclusion

In this guide you learned how to **create Word document programmatically**, **add shape**, and **hide object in Word** using Aspose.Words for Java. The complete example demonstrates the exact steps, from initializing the document to saving a file where the shape never appears.  

From here you can:

* Experiment with other shape types (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Combine hidden shapes with bookmarks to create dynamic templates.  
* Explore the `setVisible` and `setPrint` properties for more granular control over object visibility.

Happy coding, and enjoy automating your Word documents!


## What should you learn next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create blank word document with Aspose.Words for Java]({{< relref "java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/_index.md" >}})
- [How to hide shape in a Word document using Java]({{< relref "java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/_index.md" >}})
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect]({{< relref "java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/_index.md" >}})

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}