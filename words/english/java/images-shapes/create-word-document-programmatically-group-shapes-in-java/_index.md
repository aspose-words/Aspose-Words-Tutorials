---
category: general
date: 2026-09-21
description: Create word document programmatically using Java. Learn how to group
  shapes in Word, insert a rectangle shape, set shape size, and add shapes to a Word
  document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: en
lastmod: 2026-09-21
og_description: 'Create word document programmatically with Java: this guide shows
  how to group shapes in Word, insert rectangle shapes, set shape size, and add shapes
  to a Word document.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Create word document programmatically, group shapes in Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Create word document programmatically, group shapes in Java
url: /java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create word document programmatically, group shapes in Java

If you need to **create word document programmatically**, this guide walks you through a complete solution. You will see how to **group shapes in Word**, insert a rectangle, set its size, and add other shapes—all using Java and the Aspose.Words for Java library.

The tutorial covers every step from project setup to saving the final .docx file. By the end you will be able to generate a Word document that contains a rectangle and an image wrapped inside a single group, making it easy to move or resize them together. No prior experience with the Aspose.Words API is required, but you should have a basic Java development environment.

## Prerequisites

* Java Development Kit (JDK) 8 or newer  
* Maven or Gradle for dependency management  
* Aspose.Words for Java 23.9 (or the latest version) – the library is free for evaluation  
* An image file (e.g., `sample.jpg`) placed in a known directory  

Having these items ready ensures the code runs without additional configuration.

## Step 1: Set up the project and import Aspose.Words

Create a Maven project (or add the dependency to your existing `pom.xml`):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

If you prefer Gradle, add the following to `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

After the dependency is resolved, import the required classes in your Java source file:

```java
import com.aspose.words.*;
import java.io.File;
```

## Step 2: Create the Word document programmatically

The first operation in any automation scenario is to instantiate a `Document` object and a `DocumentBuilder`. The builder simplifies insertion of text, images, and shapes.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

At this point the document exists only in memory. You can now start adding shapes.

## Step 3: Insert a rectangle shape – how to insert rectangle shape

A rectangle is a basic `Shape` with `ShapeType.RECTANGLE`. You control its dimensions with `setWidth`, `setHeight`, and position it with `setTop` and `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Why this matters:** Setting the size and position explicitly (`set shape size word`) guarantees that the rectangle appears exactly where you expect, regardless of the default layout of the document.

## Step 4: Insert an image – add shapes to word document

The `DocumentBuilder` can insert an image directly from a file path. After insertion, you can reposition the picture just like any other shape.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Both the rectangle and the picture are now independent shapes inside the document.

## Step 5: Group the shapes – how to group shapes in word

Grouping shapes is useful when you want to move or resize them as a single unit. Aspose.Words provides a `GroupShape` container for this purpose.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

When the group is saved, Word treats the two children as one logical object. You can later select the group and drag it, and both the rectangle and the image will follow.

## Step 6: Save the document

Finally, write the document to disk. The path must be writable by the Java process.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Running the `main` method produces a file named **GroupShapeExample.docx**. Open it in Microsoft Word to see a rectangle and an image locked together inside a group. Selecting the group lets you move both objects simultaneously, confirming that the grouping succeeded.

## Expected output

* A Word file (`GroupShapeExample.docx`) located in the directory you specified.  
* Inside the file, a rectangle (light‑gray fill) appears at the top‑left corner, and the image sits directly below it.  
* Both objects are part of a single group, so dragging one moves the other.

## Common variations and edge cases

| Situation | Recommendation |
|-----------|----------------|
| **Different image formats** | Aspose.Words supports PNG, BMP, GIF, and TIFF. Use the appropriate file extension in `insertImage`. |
| **Negative dimensions** | The API throws `ArgumentException`. Always validate width and height before calling `setWidth` / `setHeight`. |
| **Large documents** | Grouping many shapes can increase file size. Consider merging shapes into a single picture when performance matters. |
| **Word version compatibility** | GroupShape works with Word 2007 (`.docx`) and later. For older `.doc` files, the group will be flattened. |
| **Dynamic positioning** | Use calculations based on page size (`doc.getFirstSection().getPageSetup().getPageWidth()`) if you need adaptive placement. |

**Pro tip:** After creating the group, you can change


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}