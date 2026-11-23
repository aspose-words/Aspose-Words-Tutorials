---
category: general
date: 2026-11-22
description: Add rectangle shape in a Word document with Java, set shape size, group
  multiple shapes, and append shape to group efficiently.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: en
lastmod: 2026-11-22
og_description: Add rectangle shape in a Word document using Java, then set shape
  size, group multiple shapes, and append shape to group in a single workflow.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Add rectangle shape and group shapes in Java – full guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Add rectangle shape and group shapes in Java
url: /java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add rectangle shape and group shapes in Java

If you need to **add rectangle shape** to a Word document with Java, this guide walks you through the exact steps. You’ll also learn how to **set shape size**, **group multiple shapes**, and **append shape to group** without leaving the IDE.

Working with vector graphics inside a DOCX file often feels like juggling separate APIs. By the end of this tutorial you will have a single, self‑contained program that creates a rectangle, an ellipse, and any additional shapes you may need, then groups them so they move as one object. No external tools are required beyond Aspose.Words for Java.

## Prerequisites

Before you start, ensure you have:

* Java 17 or later installed.
* Maven 3.8+ (or Gradle) to manage dependencies.
* A valid Aspose.Words for Java license (evaluation works for testing).
* An IDE such as IntelliJ IDEA or VS Code, though any text editor will do.

These requirements let the code compile and run on any modern development environment.

## Step 1: Set up the Maven project

Create a new Maven project or add the Aspose.Words dependency to an existing `pom.xml`:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

The dependency pulls in all classes needed for document manipulation, including `Document`, `DocumentBuilder`, `Shape`, and `GroupShape`. Maven will download the JARs automatically when you run `mvn compile`.

## Step 2: Load the document and create a DocumentBuilder

A `DocumentBuilder` provides the fluent API for inserting content. Load an existing DOCX or start from a blank document:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Creating the builder early gives you a cursor positioned at the start of the document, ready for shape insertion.

## Add rectangle shape to a Word document

### Step 3: Insert the rectangle shape

The rectangle is the first visual element we want to place inside the document. By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully editable object.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Adding the rectangle at this point does not affect layout until its size is defined and it is appended to a container.

### Set shape size and dimensions

#### Step 4: Define width and height

Setting the shape’s dimensions determines how it appears on the page. Width and height values are measured in points (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

You can adjust these numbers to match your design requirements. The same methods apply to any `Shape` instance, so you can reuse them for circles, arrows, or custom drawings.

#### Step 5: Insert the rectangle into the document

Now that the rectangle has a size, place it on the page. The `insertShape` method of `DocumentBuilder` adds the shape at the current cursor position.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

At this stage the rectangle appears alone on the page. The next steps show how to combine it with other shapes.

## Group multiple shapes together

Grouping shapes lets you move, rotate, or resize them as a single unit. This is especially useful for creating complex diagrams.

### Step 6: Create a group shape container

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

The `insertGroupShape` call adds an empty container to the document. Any shapes appended to this container become part of the group.

### Append shape to group

#### Step 7: Add the rectangle to the group

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Appending moves the rectangle from the document body into the group’s internal collection. The rectangle now respects the group’s transformations.

#### Step 8: Add an ellipse for demonstration

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

The ellipse shares the same coordinate space as the rectangle, so you can align them visually by adjusting their `setLeft` and `setTop` properties if needed.

### Step 9: Save the document

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Running the program generates `output.docx`. Open the file in Microsoft Word or LibreOffice; you’ll see a rectangle and an ellipse grouped together. Selecting either shape highlights the entire group, confirming that **append shape to group** succeeded.

![Add rectangle shape example in Java](image.png){alt="Add rectangle shape example in Java"}

*The screenshot shows the rectangle and ellipse inside a single group, ready for joint manipulation.*

## Why this approach matters

* **Single source of truth** – All shape properties are set before the group is created, preventing layout glitches.
* **Reusability** – The same `setWidth`/`setHeight` methods work for any shape, so you can extend the example to arrows, stars, or custom SVGs.
* **Performance** – Grouping reduces the number of drawing objects the Word renderer must handle, which improves opening speed for large documents.
* **Maintainability** – By keeping shape creation and grouping logic together, future developers can modify dimensions or add new shapes without searching through unrelated code.

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different units** | Use `PointsToPixels` conversion or set `Shape.setWrapType(WrapType.INLINE)` for inline placement. |
| **Rotating the group** | Call `groupShape.setRotation(45);` to rotate all child shapes by 45°. |
| **Adding text to a shape** | Use `Shape.setText("Label");` after setting size. |
| **Dynamic sizing** | Retrieve page dimensions via `doc.getFirstSection().getPageSetup().getPageWidth()` and calculate shape sizes proportionally. |

These variations illustrate how the core pattern—**add rectangle shape**, **set shape size**, **group multiple shapes**, **append shape to group**—adapts to many real‑world requirements.

## Conclusion

You now know how to **add rectangle shape** to a Word document using Java, **set shape size**, **group multiple shapes**, and **append shape to group** in a clean, maintainable way. The complete example compiles into a single runnable class, and the resulting DOCX file demonstrates the expected output.

From here you can explore:

* Adding text labels or hyperlinks to each shape.
* Nesting groups to build hierarchical diagrams.
* Exporting the document to PDF while preserving shape groups.

Feel free to experiment with different dimensions, colors, and additional shape types. Mastering shape manipulation opens the door to automated report generation, dynamic diagrams, and rich document experiences—all directly from Java code.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}