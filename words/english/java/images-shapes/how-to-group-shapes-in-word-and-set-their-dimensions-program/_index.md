---
category: general
date: 2026-11-25
description: How to group shapes in Word using Java and how to set shape dimensions
  in a DOCX file with Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: en
lastmod: 2026-11-25
og_description: How to group shapes in Word with Aspose.Words Java API and set shape
  size word quickly. Follow the complete step‑by‑step solution.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: How to group shapes in Word and set their dimensions – Java guide
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: How to group shapes in Word and set their dimensions programmatically
url: /java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word and set their dimensions programmatically

If you need to **how to group shapes in Word** and control their exact size, this guide shows you a complete, runnable solution. Using Aspose.Words for Java you can create a rectangle, an ellipse, add them to a `GroupShape`, and then **how to set shape dimensions** such as width and height in a single DOCX file.

You’ll learn how to:

* Create a new Word document from scratch.  
* Insert a `GroupShape` (new API in version 24.9).  
* Add a rectangle and an ellipse to the group.  
* **Set shape size Word** precisely with `setWidth` and `setHeight`.  
* Save the document to disk.

No external tooling is required—just Java 17+, Maven, and the Aspose.Words for Java library.

## Prerequisites

* Java Development Kit 17 or newer.  
* Maven (or Gradle) for dependency management.  
* Aspose.Words for Java 24.9 or later (the `GroupShape` API was introduced in 24.9).  
* Basic familiarity with Java syntax and object‑oriented concepts.

If you haven’t added Aspose.Words to your project yet, include the following Maven dependency:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Step 1: Create a new document and a DocumentBuilder

The `Document` class represents the entire Word file, while `DocumentBuilder` provides a convenient way to add content.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this step?*  
Creating a fresh `Document` gives you a clean canvas. `DocumentBuilder` is the high‑level helper that lets you insert paragraphs, tables, and, in this case, shapes.

## Step 2: Insert a GroupShape (new API in version 24.9)

A `GroupShape` acts like a container; any shape you add becomes part of the same visual group.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use `GroupShape`?*  
Grouping shapes simplifies moving, rotating, or applying formatting to multiple objects at once. The API was added in 24.9, so older versions won’t compile this line.

## Step 3: Create a rectangle, set its size, and add it to the group

Here we demonstrate **how to set shape dimensions** for a rectangle.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Why set width and height explicitly?*  
Word stores shape size in points. By calling `setWidth` and `setHeight` you control the exact visual footprint, which is essential when you need precise layout or when exporting to PDF.

## Step 4: Create an ellipse, set its size, and add it to the same group

The same **set shape size word** technique works for any shape type.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Why add the ellipse to the same `GroupShape`?*  
Both shapes will move together as a unit. This is useful for creating icons, logos, or complex diagrams that must stay aligned.

## Step 5: Save the document with the grouped shapes

Finally, persist the DOCX file to disk.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Running this program produces a file named **GroupShape.docx** that contains a rectangle and an ellipse grouped together. When you open the file in Microsoft Word, you’ll see the two shapes behave as a single object—you can drag, resize, or rotate them together.

### Expected output

* A Word document (`GroupShape.docx`) with one page.  
* A `GroupShape` containing a 100 × 50 pt rectangle and an 80 × 80 pt ellipse.  
* Selecting either shape selects the whole group.

## Common questions and edge cases

### How to change the position of the grouped shapes?

After creating the `GroupShape`, you can set its `left` and `top` properties:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

These coordinates are also measured in points.

### What if I need to add more than two shapes?

`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)` for each additional shape. The API does not limit the number of children.

### Can I apply style (fill color, line weight) to individual shapes?

Yes. Each `Shape` object exposes formatting properties:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Does the code work with older Aspose.Words versions?

The `insertGroupShape` method was introduced in version 24.9. If you are on an earlier version, you’ll need to create a `GroupShape` manually via the node tree, which is more involved. Upgrading is the recommended path.

## Pro tips

* **Use points for consistency** – Word’s internal unit is the point (1/72 inch). Converting from pixels or centimeters can lead to unexpected sizes.  
* **Group before positioning** – Position the `GroupShape` after you’ve added all its children; otherwise you may need to recalculate offsets.  
* **Reuse the DocumentBuilder** – You can insert multiple groups in the same document by moving the builder’s cursor (`builder.moveTo`) before each `insertGroupShape` call.

## Conclusion

You now have a complete, end‑to‑end example of **how to group shapes in Word** and **how to set shape dimensions** using Aspose.Words for Java. The tutorial covered creating a document, inserting a `GroupShape`, adding a rectangle and an ellipse, setting their exact size, and saving the result.  

From here you can explore:

* Adding text boxes or pictures to the same group.  
* Animating grouped shapes with Word’s smart art features (via the API).  
* Exporting the grouped shapes to PDF or SVG for web use.

Feel free to experiment with different shape types, sizes, and positions—grouping gives you powerful control over complex layouts in Word documents.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}