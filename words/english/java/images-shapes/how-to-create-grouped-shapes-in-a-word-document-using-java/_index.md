---
category: general
date: 2026-10-13
description: Learn how to create grouped shapes in Word with Java. This guide shows
  you how to insert group shape, add line to group, and group multiple shapes word‑wide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: en
lastmod: 2026-10-13
og_description: Create grouped shapes in Word with Java. Follow this complete tutorial
  to insert group shape, add line to group, and group multiple shapes word documents.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Create grouped shapes in Word with Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: How to create grouped shapes in a Word document using Java
url: /java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create grouped shapes in a Word document using Java

If you need to **create grouped shapes** in a Microsoft Word file from Java, this tutorial walks you through the entire process. You’ll see how to **insert group shape**, place a rectangle and a line inside the same container, and finally save the document with the grouped graphics.

Grouping shapes makes it easy to move, resize, or style several drawing objects as a single unit—perfect for diagrams, flowcharts, or custom page decorations. By the end of this guide you’ll be able to **add line to group**, **group multiple shapes word** documents, and reuse the same technique for any number of shapes.

## Prerequisites

- Java 17 or later installed on your development machine.  
- An Aspose.Words for Java license (or a free evaluation).  
- A Maven or Gradle project where you can add the Aspose.Words dependency:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

No additional libraries are required.

## Step 1: Insert the group shape container

The first step is to **insert group shape** into the document. This container will hold every subsequent shape.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` creates an empty `Shape` object of type `GROUPSHAPE`. Think of it as a transparent canvas that can contain other drawing objects.

## Step 2: Add a rectangle to the group

A rectangle often serves as the visual background for a group of shapes.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Setting `Left` and `Top` to `0` positions the rectangle at the top‑left corner of the group. You can change these values to offset the shape within the group.

## Step 3: **Add line to group** – create a line shape

Now we **add line to group**. The line will appear beneath the rectangle.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

The `Top` property moves the line 60 points below the rectangle, creating a simple stacked layout. You could also set `Left` if you need horizontal offset.

## Step 4: Save the document with the grouped shapes

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

When you open `GroupShapeDemo.docx` in Microsoft Word, you’ll see a single group that contains both the rectangle and the line. Selecting the group lets you move both shapes together, which demonstrates that you have successfully **group multiple shapes word**.

## Full, runnable example

Below is the complete program with all imports and error handling. Copy it into your IDE, replace `YOUR_DIRECTORY` with an existing folder path, and run.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Expected output

- A file named `GroupShapeDemo.docx` appears in the target folder.  
- Opening the file in Word shows a single grouped object containing a rectangle on top and a line below it.  
- Dragging the group moves both shapes together, confirming that you have **created grouped shapes** successfully.

## Tips and common pitfalls

- **Pro tip:** If you need to rotate or style individual shapes inside the group, call the respective setters (`setRotation`, `getFill().setForeColor`, etc.) before appending them to the group. The group will preserve those visual properties.
- **Watch out for:** Forgetting to set the `Top` property for the line can cause it to overlap the rectangle, making the group look cluttered.
- **Edge case:** When you add more than two shapes, remember that each child’s coordinates are relative to the group’s origin (0,0). Plan the layout accordingly.
- **Performance note:** Grouping a large number of shapes (hundreds) may increase the file size slightly, but it simplifies later editing in Word.

## How to **group multiple shapes word** documents programmatically

The pattern shown above—create a group container, configure each child shape, and append—works for any number of shapes: circles, pictures, text boxes, etc. Simply repeat the “create shape → set properties → append” steps before calling `doc.save()`.

If you need to **add line to group** after the group already contains other shapes, you can retrieve the existing group with:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

This demonstrates that you can modify a group at any point in the document lifecycle.

## Conclusion

You now know how to **create grouped shapes** in a Word document using Java and Aspose.Words. By **inserting group shape**, **adding line to group**, and **group multiple shapes word**, you can build complex drawings that behave as a single object—ideal for diagrams, templates, and automated report generation.

Next, explore these related topics:

- **Applying styles to grouped shapes** – learn how to set fill colors, borders, and effects for all children at once.  
- **Exporting grouped shapes to PDF** – see how the same group persists when you convert the document.  
- **Animating shapes with VBA** – combine Java‑generated groups with Word macros for interactive documents.

Feel free to experiment with different shape types, sizes, and positions. Grouping gives you the flexibility to treat many objects as one, simplifying both code and user interaction. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}