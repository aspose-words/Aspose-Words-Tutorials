---
category: general
date: 2026-10-16
description: Learn how to group shapes in Word using Java. This tutorial shows how
  to add rectangle shape, set shape size and dimensions, and save the document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: en
lastmod: 2026-10-16
og_description: Group shapes in Word using Java. Add rectangle shape, set shape size
  and dimensions, and create professional documents programmatically.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Group shapes in Word with Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: How to group shapes in Word with Java – complete guide
url: /java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word with Java – complete guide

If you need to **group shapes in Word** programmatically, this tutorial gives you a ready‑to‑run solution. You’ll see how to **add rectangle shape**, adjust its size, set shape dimensions, and finally save a DOCX file that contains a grouped rectangle and an ellipse.

Grouping shapes in Word is useful for building complex diagrams, creating reusable graphic components, or simply keeping related objects together when the document is edited later. The code uses the Aspose.Words for Java library, which works with any recent JDK and does not require Microsoft Word to be installed.

## Prerequisites

Before you start, make sure you have:

| Requirement | Reason |
|-------------|--------|
| Java 17 (or later) | The library targets modern Java runtimes. |
| Aspose.Words for Java (latest version) | Provides the `Document`, `DocumentBuilder`, `GroupShape`, and `Shape` classes used in the example. |
| An IDE or build tool (Maven/Gradle) | To compile and run the sample. |
| Basic knowledge of Java syntax | Needed to understand the code flow. |

Add the Aspose.Words dependency to your project. For Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Or for Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Overview of the solution

The tutorial follows a clear **problem → solution → explanation** pattern:

1. **Create a new Word document** and obtain a `DocumentBuilder`.  
2. **Insert a `GroupShape` container** that will hold multiple shapes.  
3. **Add a rectangle**, set its width/height (the **set shape size** step), and attach it to the group.  
4. **Add an ellipse**, position it inside the same group, and also set its dimensions.  
5. **Save** the document to disk.

Each step includes the **why** behind the code, so you understand what the API does and how you can adapt it to other scenarios.

## Step 1: Create the document and a DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` represents the entire DOCX file, while `DocumentBuilder` is a helper that lets you insert content without dealing with low‑level node management. Creating them first gives you a clean canvas for all subsequent shape operations.

## Step 2: Insert a GroupShape container

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

A `GroupShape` works like a **folder** for drawing objects. When you move, rotate, or delete the group, all child shapes follow automatically. This is the core of **group shapes in word**.

## Step 3: Add a rectangle shape – the rectangle shape code

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – The `Shape` constructor receives `ShapeType.RECTANGLE`, which tells Aspose.Words to render a rectangular outline.  
- **set shape size** – `setWidth` and `setHeight` define the **shape dimensions** in points (1 pt = 1/72 in). This is the most common way to control visual size.  
- **Why we use `appendChild`** – It attaches the rectangle to the `GroupShape` so it moves together with the group.

## Step 4: Add an ellipse and position it inside the group

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

The ellipse demonstrates **set shape dimensions** beyond a simple rectangle. By calling `setLeft`, we control the horizontal offset inside the group, which is useful when arranging multiple objects.

## Step 5: Save the document

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

When you open *GroupShapeDemo.docx* in Microsoft Word, you’ll see a rectangle and an ellipse locked together inside a single group. Selecting either shape will select the entire group—exactly what you expect when **group shapes in word**.

## Full, runnable example

Putting all pieces together, here is the complete source file you can copy into your IDE:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Expected output

- A file named **GroupShapeDemo.docx** appears in the project folder.  
- Opening the file in Word shows two shapes (a rectangle and an ellipse) that are grouped together.  
- Dragging either shape moves the whole group, confirming that **group shapes in word** works as intended.

## Common variations and edge cases

| Scenario | What to change | Why |
|----------|----------------|-----|
| **Different shape types** (e.g., triangle) | Use `ShapeType.TRIANGLE` or any other enum value when constructing `Shape`. | Allows you to build more complex diagrams. |
| **Setting fill color** | Call `shape.getFillColor().setColor(Color.BLUE);` after creating the shape. | Improves visual appearance without affecting grouping. |
| **Rotating the group** | `groupShape.setRotationAngle(45);` | Rotates all child shapes together, useful for icons. |
| **Adding text inside a shape** | `shape.appendChild(new Paragraph(document));` then add a `Run` with text. | Makes the shape act like a label or callout. |
| **Saving to a stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Useful for web services that return the document directly. |

### Pro tip

When you need to **set shape dimensions** based on dynamic data (e.g., a barcode length), calculate the width/height in points first:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

This avoids hard‑coding values and keeps your code adaptable.

## Conclusion

You now know how to **group shapes in Word** using Java, how to **add rectangle shape**, and how to **set shape size** and **set shape dimensions** with concise, production‑ready code. By following the steps above, you can create reusable graphic groups, embed them in automated reports, or build custom diagramming tools without ever opening Word manually.

### What’s next?

- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE` with `setCornerRadius`).  
- Combine **group shapes in word** with tables or charts for richer documents.  
- Look into the Aspose.Words API for **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) to control how surrounding text interacts with your grouped graphics.

Feel free to experiment, adapt the **rectangle shape code**, and share your results


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}