---
category: general
date: 2026-08-01
description: Group shapes in Word with Java using Aspose.Words. Learn how to group
  shapes and insert rectangle shape quickly with a full code example.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: en
lastmod: 2026-08-01
og_description: Group shapes in Word using Java. This guide shows how to group shapes,
  insert rectangle shape, and save a DOCX with Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Group Shapes in Word with Java – Full Programming Walkthrough
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Group Shapes in Word with Java – Complete Step-by-Step Guide
url: /java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Group Shapes in Word with Java – Complete Step-by-Step Guide

If you need to **group shapes in Word** using Java, this guide has you covered. Whether you’re building a report generator or a dynamic template engine, grouping shapes makes your documents look polished and keeps related graphics together.

In the next few minutes you’ll see exactly **how to group shapes** and **insert rectangle shape** objects with Aspose.Words, plus a handful of practical tips that save you from common pitfalls. Ready to turn those loose rectangles and ellipses into a tidy group? Let’s dive in.

## What This Tutorial Covers

* The minimal prerequisites (Java 17+, Aspose.Words 24.10 or later).  
* A complete, runnable Java program that creates a Word document, inserts a rectangle and an ellipse, groups them, hides the group if you wish, and saves the file.  
* Why each API call matters, not just what it does.  
* Edge‑case handling for older Aspose.Words versions and for grouping more than two shapes.  
* Expected output and a quick way to verify the result.

By the end you’ll be able to drop this snippet into any Java project and start grouping shapes in Word without hunting through scattered docs.

---

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** | Modern language features and better performance. |
| **Aspose.Words for Java 24.10+** | The `setHidden` method used later only exists from this version onward. |
| **A Maven or Gradle build** | Makes dependency management painless. |
| **An IDE (IntelliJ, Eclipse, VS Code)** | Helpful for quick testing, but any text editor works. |

Add the Aspose.Words Maven dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

If you prefer Gradle, the equivalent is:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Step 1: Create a New Document and Builder

First we spin up an empty `Document` and a `DocumentBuilder`. The builder is the workhorse that lets us insert shapes, text, and more.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Why this step?*  
`Document` represents the whole DOCX file, while `DocumentBuilder` provides a convenient cursor‑based API. Without a builder you’d have to manipulate low‑level node collections manually—something that’s easy to get wrong.

---

## Step 2: Insert a Rectangle Shape (and an Ellipse)

Now we add the two basic shapes we want to group. Notice the **insert rectangle shape** call—this is exactly the secondary keyword you’re looking for.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

A few things to keep in mind:

* The width (`100`) and height (`50`) are measured in points (1 pt ≈ 1/72 in). Adjust them to fit your layout.  
* The rectangle is drawn first, so it sits behind the ellipse by default. If you need the opposite order, insert the ellipse first.  
* Both shapes inherit the builder’s current formatting (color, line style). You can customize them before grouping if you wish.

---

## Step 3: How to Group Shapes with Aspose.Words

Here’s the core of the tutorial—**how to group shapes**. The `insertGroupShape` API takes an array of existing shapes and returns a new `Shape` that represents the group.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Why use a group?  

* A group moves as a single unit, preserving relative positioning.  
* You can apply transformations (rotation, scaling) to the whole set with one call.  
* Grouping simplifies later editing—un‑group later if you need to tweak individual elements.

---

## Step 4 (Optional): Hide the Group from the Document View

If you don’t want the group to appear when the user opens the document in Word, you can hide it. This step is optional but handy for background graphics or watermarks.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**What if you’re on an older Aspose.Words version?**  
The `setHidden` method won’t compile. In that case you can achieve a similar effect by setting the shape’s `WrapType` to `NONE` and moving it behind the text layer:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

It’s a bit more verbose, but it still keeps the group out of the reader’s way.

---

## Step 5: Save the Document

Finally, write the document to disk. Change the path to wherever you’d like the file to land.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

When you open `GroupShapeResult.docx` in Microsoft Word, you’ll see a rectangle and an ellipse neatly bundled together. If you set `setHidden(true)`, the group will be invisible in the editor but still present in the file (useful for programmatic processing later).

---

## Full Working Example

Putting it all together, here’s the complete, self‑contained Java class you can copy‑paste into your project:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Expected output:** A file named `GroupShapeResult.docx` containing a single group that holds a blue‑filled rectangle and a red‑outlined ellipse (default colors). If you open the document, select the group, and right‑click → **Group → Ungroup**, you’ll see the two original shapes reappear.

---

## Common Questions & Edge Cases

### 1. Can I group more than two shapes?

Absolutely. Just pass a larger array to `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

The API scales linearly; the only limitation is memory for extremely large groups.

### 2. What if I need to change the group’s position after creation?

Use the group’s `setLeft` and `setTop` methods, just like any other shape:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Because the group behaves like a single shape, all child shapes move together.

### 3. How do I apply a border or fill to the whole group?

The group itself can have formatting, but it doesn’t affect the children directly. If you want a common border, wrap the shapes in a rectangle shape first, then group everything. Alternatively, iterate over each child shape and set the same `fillColor` or `strokeWeight`.

### 4. Does `setHidden(true)` affect printing?

Hidden shapes are **not** printed by default in Word, which can be useful for watermarks or template markers. If you need the shape to print but stay invisible on screen, you’ll have to use a different approach (e.g., set its opacity to 0%).

---

## Pro Tips From the Trenches

* **Name your shapes** – `groupShape.setName("HeaderGraphics");` makes debugging easier when you later retrieve shapes by name.  
* **Reuse the builder** – After inserting a group, the builder’s cursor stays where the group was placed, so you can continue adding paragraphs right after the group without resetting the position.  
* **Version guard** – If you ship a library that might run on older Aspose.Words versions, wrap the `setHidden` call in a try‑catch for `NoSuchMethodError` and fall back to the `WrapType.NONE` trick shown earlier.  
* **Performance tip** – When generating thousands


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rendering Shapes in Aspose.Words for Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}