---
category: general
date: 2026-08-07
description: Create blank Word document with grouped shapes in Java using Aspose.Words.
  Learn how to group shape, set shape size, and add shapes to Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: en
lastmod: 2026-08-07
og_description: Create blank Word document with grouped shapes in Java. Follow this
  guide to set shape size, add shapes to Word, and master how to group shape.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Create blank Word document with grouped shapes – Java tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Create blank Word document with grouped shapes in Java
url: /java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank Word document with grouped shapes in Java

If you need to **create blank Word document** that contains several shapes arranged as a single unit, this tutorial shows you exactly how. You’ll see a complete, runnable example that demonstrates **how to group shape** objects, adjust their dimensions, and **add shapes to Word** using Aspose.Words for Java.

The guide walks through every step—from project setup to saving the final .docx file—so you can copy the code directly into your own application. No external references are required, and the solution works with Aspose.Words 23.9 or later.

## Prerequisites

Before you start, make sure you have:

* Java 17 (or any supported JDK)
* Maven or Gradle for dependency management
* An Aspose.Words for Java license (or a temporary evaluation key)
* A sample image file (e.g., `sample.jpg`) placed in a known directory

If any of these items are missing, install them first; the rest of the tutorial assumes the environment is ready.

## Step 1: Add Aspose.Words to your project

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). This library provides the `Document`, `DocumentBuilder`, `GroupShape`, and `Shape` classes used later.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Why this matters:** Without the library, none of the Word‑processing APIs are available, and you cannot **create blank Word document** programmatically.

## Step 2: Create a blank Word document

The first concrete action is to instantiate a `Document` object, which represents a **blank Word document** in memory.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* creates a **blank Word document** with default settings (A4 page, default margins). The accompanying `DocumentBuilder` lets you insert content at the current cursor position.

## Step 3: Insert a group shape (how to group shape)

A *group shape* acts as a container for other shapes. In this step you learn **how to group shape** objects so they move together.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

The `insertGroupShape` method places the container at the builder’s cursor location. Grouping is essential when you want to treat multiple drawings as a single entity—this is the core of **group shapes word** functionality.

## Step 4: Create a rectangle and set its size

Now add a rectangle to the group. This demonstrates **set shape size**, which is necessary for precise layout.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Why set dimensions?* Explicitly calling `setWidth` and `setHeight` guarantees that the rectangle appears exactly as intended, regardless of the document’s default shape styles.

## Step 5: Insert an image and add it to the group

Adding a picture shows another common use case for **add shapes to word**. The image becomes part of the same group, moving together with the rectangle.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

If the image file is missing, Aspose.Words throws an exception. A practical tip is to verify the path beforehand:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Step 6: Save the document containing the grouped shapes

Finally, persist the **blank Word document** (now populated with a grouped shape) to disk.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

When you open `GroupShapeDemo.docx` in Microsoft Word, you’ll see a single grouped object that contains a rectangle and an image. Selecting any part of the group moves the entire container, confirming that the shapes were correctly **grouped**.

### Expected output

* A file named `GroupShapeDemo.docx` in the specified directory.
* Opening the file shows a 300 × 200‑point container with:
  * A 100 × 50‑point rectangle positioned at (20, 20).
  * An image positioned at (150, 30) inside the same container.

## Edge cases and variations

| Situation | How to handle it |
|-----------|-----------------|
| **Different page size** | Call `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` before inserting the group. |
| **Multiple groups** | Repeat steps 3‑5 with a new `GroupShape` instance; each group can be positioned independently. |
| **Rotating shapes** | Use `shape.setRotationAngle(45.0);` to rotate a rectangle or picture before appending it to the group. |
| **Non‑image shapes** | Create `Shape` objects of type `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., and append them just like the rectangle. |
| **Large images** | Scale the picture with `picture.setWidth(80.0); picture.setHeight(60.0);` to keep the group within its original bounds. |

These variations let you adapt the core pattern to a wide range of document‑generation scenarios.

## Practical tips from experience

* **Pro tip:** Set the group’s `RelativeHorizontalPosition` and `RelativeVerticalPosition` to `RelativeHorizontalPosition.PAGE` and `RelativeVerticalPosition.PAGE` if you want the group to stay anchored to the page rather than the cursor.
* **Watch out for:** Adding a shape that exceeds the group’s dimensions; the shape will be clipped in Word. Adjust the group size with `group.setWidth()` and `group.setHeight()` accordingly.
* **Performance note:** If you generate many documents in a loop, reuse a single `DocumentBuilder` instance and call `doc.clone()` to reduce object‑creation overhead.

## Conclusion

You now know how to **create blank Word document** that contains a grouped collection of shapes using Aspose.Words for Java. The tutorial covered the complete workflow: setting up the library, creating the document, inserting a group, **set shape size**, **add shapes to word**, and saving the result. 

From here you can explore more advanced features such as grouping charts, applying styles to individual shapes, or exporting the document to PDF. Each of these topics builds on the same principles demonstrated in this guide.

---


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}