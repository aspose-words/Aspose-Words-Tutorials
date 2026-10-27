---
category: general
date: 2026-09-24
description: Learn how to create a blank Word document in Java and group shapes like
  rectangles and lines using Aspose.Words. Includes step‑by‑step code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: en
lastmod: 2026-09-24
og_description: Create a blank Word document in Java and learn how to group shapes,
  add a rectangle shape, and set shape size with Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Create a blank Word document and group shapes in Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: How to create a blank Word document and group shapes in Java
url: /java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create a blank Word document and group shapes in Java

If you need to **create a blank Word document** and then organize multiple drawing objects, this guide shows you exactly how. Using Aspose.Words for Java you can insert a group shape, add a rectangle shape, draw a line, and control each shape’s size and position—all in a single, runnable program.

You’ll walk through every step, from initializing the document to saving the final `.docx`. By the end you’ll understand **how to group shapes**, **add rectangle shape**, and **set shape size** so your Word files look exactly as intended.

## Prerequisites

- Java 17 or later (the code compiles with any recent JDK)
- Aspose.Words for Java library (download from the [Aspose website](https://products.aspose.com/words/java))
- An IDE or build tool (Maven/Gradle) that can add the Aspose.Words JAR to the classpath
- Basic knowledge of Java syntax

> **Pro tip:** Use Maven for dependency management; add `com.aspose:aspose-words:23.12` (or the latest version) to your `pom.xml`.

## Step 1: Create a blank Word document

The first task is to **create a blank Word document**. This gives you a clean canvas on which you can later insert shapes.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* A `Document` object represents the entire `.docx` file. Starting with a blank document ensures no hidden formatting interferes with the shapes you will add.

## Step 2: Insert a group shape – the container for multiple objects

A **group shape** acts like a container that lets you move, resize, or rotate several shapes together. This is the core of **how to group shapes** in Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Explanation:* The `insertGroupShape` method creates a `GroupShape` object and places it at the current cursor location. All subsequent shapes that you `appendChild` to this group will be treated as a single unit.

## Step 3: Add a rectangle shape and set its size

Now we **add rectangle shape** to the group and **set shape size** precisely.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Why you need to set shape size:* Width and height control how the rectangle appears on the page. The `setLeft` and `setTop` methods position the rectangle relative to the group's origin, giving you pixel‑perfect layout control.

## Step 4: Add a line shape and configure its dimensions

A line is another common drawing object. We’ll **add rectangle shape**‑like logic to a line, showing that the same sizing principles apply.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Key point:* Even though a line has no height, you still use `setWidth` to define its length. Positioning (`setLeft`, `setTop`) follows the same coordinate system as other shapes.

## Step 5: Save the document with grouped shapes

Finally, persist the changes by saving the document. This produces a `.docx` file that you can open in Microsoft Word to verify the result.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Expected output:** Opening `GroupShapeDemo.docx` shows a blank page containing a grouped rectangle and line. Selecting either shape selects the whole group, allowing you to move them together.

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| *Can I add more than two shapes to the group?* | Yes. Call `group.appendChild(yourShape)` for each additional shape. |
| *What if I need a different unit (e.g., centimeters) for size?* | Aspose.Words uses points (1 point = 1/72 inch). Convert using `Points = centimeters * 28.3465`. |
| *Will the group retain its layout when the document is opened on another machine?* | Absolutely. All size and position data are stored in the `.docx` file, making the layout portable. |
| *How do I ungroup shapes later?* | Retrieve the `GroupShape` object, then iterate over `group.getChildNodes(NodeType.SHAPE, true)` and move each child out of the group. |
| *What if I need to rotate the whole group?* | Use `group.setRotationAngle(double angleInDegrees)` before saving. |

## Full, runnable example

Below is the complete program you can copy‑paste into your IDE. It includes all necessary imports and comments.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Run the program, open `GroupShapeDemo.docx` in Microsoft Word, and you’ll see the grouped shapes exactly as described.

## Conclusion

You now know how to **create a blank Word document**, **group shapes in Word**, **add rectangle shape**, and **set shape size** using Aspose.Words for Java. By placing shapes inside a `GroupShape`, you gain full control over collective positioning, scaling, and rotation—perfect for diagrams, flowcharts, or custom graphics embedded in automated reports.

**Next steps:**  
- Explore **how to group shapes** with more complex objects like pictures or text boxes.  
- Experiment with `setRotationAngle` to rotate the entire group.  
- Combine this technique with mail‑merge to generate personalized documents that include branded graphics.

Feel free to adapt the code for your own projects, and share your results in the comments!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}