---
category: general
date: 2026-08-14
description: Group shapes in Word with Java using Aspose.Words. Learn how to create
  rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
  document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: en
lastmod: 2026-08-14
og_description: Group shapes in Word using Aspose.Words for Java. Build a blank Word
  document, create rectangle shape, set shape dimensions, and group multiple shapes
  in minutes.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Group shapes in Word – Java example for developers
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Group shapes in Word – complete programming guide
url: /java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Group shapes in Word – complete programming guide

If you need to **group shapes in Word**, this tutorial walks you through the entire process with Java and Aspose.Words. You’ll learn how to **build blank Word document**, **create rectangle shape**, **set shape dimensions**, and finally **group multiple shapes** so they behave as a single object.

Working with shapes in a Word file often feels like drawing on a canvas without a paintbrush. By the end of this guide you will have a reusable code snippet that you can drop into any Java project, whether you are generating reports, invoices, or custom templates.

## What you’ll need

- Java 8 or newer
- Aspose.Words for Java (the latest version, e.g., 24.9)
- An IDE such as IntelliJ IDEA or Eclipse
- Basic familiarity with object‑oriented programming

All of these prerequisites are free to install, and the code below compiles with a single Maven dependency:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Step 1: Build blank Word document and initialize the builder

The first thing you must do is **build a blank Word document**. This gives you a clean canvas on which you can later insert shapes.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` represents the whole *.docx* file, while `DocumentBuilder` is the helper that inserts paragraphs, tables, and shapes. Initializing both objects is the foundation for any Word automation task.

## Step 2: Insert a group shape container

A **group shape** acts like a folder that can hold other shapes. First we create the container with a fixed size of 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

The `insertGroupShape` method returns a `GroupShape` object. All subsequent shapes that you want to treat as a single unit must be appended to this object.

## Step 3: Create rectangle shapes and set shape dimensions

Now we **create rectangle shape** objects, configure their size, and position them inside the group. This step also demonstrates how to **set shape dimensions** precisely.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Both rectangles share the same dimensions, but their `left` properties differ, so they appear side‑by‑side. You can change `setTop` and `setLeft` to arrange any layout you need.

## Step 4: Save the document containing the grouped rectangles

After the shapes are inside the group, you simply save the `Document`. The resulting file will show two rectangles that move together when selected.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Running the program creates `GroupShape.docx` in the working directory. Open it in Microsoft Word, select one rectangle, and you’ll notice that the whole group moves as a unit—exactly what **group shapes in Word** are meant to do.

![Group shapes in Word example](group-shapes.png){alt="Group shapes in Word example"}

*Figure: Two rectangle shapes grouped together in a Word document.*

## Pro tip: Re‑using the same group shape

If you need to add more shapes later (e.g., circles, text boxes), keep a reference to `groupShape` and continue calling `appendChild`. This avoids recreating the container and ensures all members stay synchronized.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Edge cases and common questions

- **What if the shapes overlap?** Overlap is allowed; Word will render them in the order they were added. Use `setZOrder` if you need explicit stacking.
- **Can I group shapes across different pages?** No. A `GroupShape` is confined to a single page because its coordinate system is page‑relative.
- **Do grouped shapes inherit formatting?** Each child keeps its own formatting (fill color, line style). To apply a uniform style, iterate over `groupShape.getChildNodes()` and set properties programmatically.

## Full source code for reference

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Running the program produces a DOCX file where the two rectangles are **grouped**. Selecting any rectangle moves both, confirming that you have successfully **grouped multiple shapes**.

## Conclusion

You now know how to **group shapes in Word** using Java, from **building a blank Word document** to **creating rectangle shape**, **setting shape dimensions**, and finally **grouping multiple shapes** into a single, movable object. This pattern scales to any number of shapes and can be combined with text, images, or charts to build rich, programmatic documents.

### What’s next?

- Explore **group multiple shapes** with different types (ellipses, arrows, text boxes).
- Apply fill colors or borders by calling `shape.getFillColor()` and `shape.getLine().setColor()`.
- Insert the grouped shape into a table cell for structured reports.
- Combine this approach with mail‑merge to generate personalized contracts that include branded graphics.

Feel free to experiment, adapt the dimensions, or embed additional content. When you master grouping, your Word automation scripts become far more flexible and maintainable. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}