---
category: general
date: 2026-11-15
description: Create rectangle shape in Word with Java and learn how to add shapes
  to Word, set shape dimensions, and save Word document efficiently.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: en
lastmod: 2026-11-15
og_description: Create rectangle shape in a Word document using Java. Learn to add
  shapes to Word, set shape dimensions, and save the Word document in minutes.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Create rectangle shape in Word with Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Create rectangle shape in a Word document using Java
url: /java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in a Word document using Java

If you need to **create rectangle shape** inside a Word file, this guide shows you exactly how to do it with Java. You’ll see how to **add shapes to Word**, control the **set shape dimensions**, and finally **save Word document** without leaving your IDE.

In the sections that follow you’ll get a complete, runnable example, an explanation of every line, and tips for common pitfalls such as sizing issues and document compatibility. No external references are required—just the Aspose.Words for Java library.

## What you’ll learn

* How to initialise a `Document` and a `DocumentBuilder`.
* How to insert a **group shape** and place a rectangle inside it.
* How to **define shape size** using `setWidth` and `setHeight`.
* How to **save Word document** in `.docx` format.
* Edge‑case handling for different page sizes and DPI settings.

### Prerequisites

* Java 17 or later (the code compiles with Java 8 as well).
* Aspose.Words for Java 23.10 or newer – you can obtain it from Maven Central.
* A basic understanding of Java syntax and object‑oriented concepts.

> **Pro tip:** If you plan to add more shapes later (e.g., circles or text boxes), keep them inside the same `GroupShape`. This makes moving, rotating, or formatting the whole collection much easier.

## Step 1: Initialise the document and builder

The first step is to create a blank Word file and a `DocumentBuilder` that lets you write content.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* A `Document` represents the entire file, while `DocumentBuilder` provides high‑level methods for inserting text, tables, and **shapes**. Without the builder you would have to manipulate low‑level nodes manually.

## Step 2: Insert a group shape to hold multiple shapes

A **group shape** acts like a container; you can add several shapes and treat them as a single object later (e.g., move or rotate together).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use a group shape?* If you later decide to add arrows, circles, or labels around the rectangle, the group keeps everything aligned. It also simplifies the **add shapes to Word** workflow because you only need one call to `appendChild` for each new shape.

## Step 3: Create the rectangle shape

Now we create the actual rectangle that will live inside the group. The `Shape` constructor needs the owning `Document` and the type of shape you want.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Why a rectangle?* `ShapeType.RECTANGLE` is the most common primitive for highlighting sections, creating placeholders, or drawing simple UI mock‑ups directly inside Word.

## Step 4: Define the rectangle’s size

Setting the dimensions is where **set shape dimensions** becomes important. You can use any measurement unit supported by Aspose.Words; the default is points (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Note:** If you prefer millimeters, call `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` where `1.39 in ≈ 35 mm`. This demonstrates the **define shape size** flexibility.

## Step 5: Add the rectangle to the group shape

Appending the rectangle to the previously created group makes it appear in the document.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

At this point the rectangle is positioned at the top‑left corner of the group. You can move it later with `rectangle.setLeft(...)` and `rectangle.setTop(...)` if you need precise placement.

## Step 6: (Optional) Save the document to see the result

Finally, write the document to disk. This is the **save Word document** step that produces a `.docx` file you can open in Microsoft Word, LibreOffice, or Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Running the program creates `RectangleShapeDemo.docx` containing a single rectangle inside a group shape. Opening the file shows a plain white rectangle—exactly the size you defined.

### Expected output

* A Word file named `RectangleShapeDemo.docx`.
* Inside the first paragraph, a group shape containing a 100 pt × 50 pt rectangle.
* No text is added, so the rectangle appears on a blank page.

## Common variations and edge cases

| Situation | How to adapt the code |
|-----------|-----------------------|
| **Different page size** (e.g., A4) | Call `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` before inserting the shape. |
| **Higher DPI for printing** | Multiply width/height by the desired DPI factor, e.g., `rectangle.setWidth(200 * 2);` for double resolution. |
| **Adding a text label inside the rectangle** | Create a `Shape` of type `TEXT_BOX`, set its `setWidth`/`setHeight` to match the rectangle, then add it to the same `GroupShape`. |
| **Rotating the rectangle** | Use `rectangle.setRotationAngle(45);` to rotate 45 degrees clockwise. |
| **Saving as PDF instead of DOCX** | Replace `document.save("output.docx");` with `document.save("output.pdf");` – the same API works for PDF, preserving the rectangle. |

## Pro tips for a robust implementation

1. **Reuse the builder** – after inserting the group shape, you can continue adding paragraphs or tables without creating a new builder instance.
2. **Dispose resources** – although Java’s garbage collector handles most objects, explicitly calling `document.close();` (if using streams) prevents file‑handle leaks.
3. **Validate dimensions** – before calling `setWidth`/`setHeight`, ensure the values are positive; negative values throw `IllegalArgumentException`.
4. **Version compatibility** – the code works with Aspose.Words 23.x and later. Earlier versions may require `Shape.setSize(width, height)` instead of separate setters.

## Full, runnable example

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Result verification:** Open `output/RectangleShapeDemo.docx` in Microsoft Word. You should see a rectangle of the specified size centered at the top of the first page. If the rectangle appears too small, adjust the values passed to `setWidth` and `setHeight`.

## Conclusion

You now know how to **create rectangle shape** in a Word file using Java, how to **add shapes to Word** via a `GroupShape`, how to **set shape dimensions** and **define shape size**, and finally how to **save Word document** for further distribution. The same pattern works for other shape types, allowing you to build complex diagrams programmatically.

### What’s next?

* Explore **add shapes to Word** by inserting circles, arrows, or text boxes.
* Combine multiple shapes into a single `GroupShape` and apply transformations (rotate, flip).
* Generate reports that embed charts as shapes, then **save Word document** as PDF for sharing.

Feel free to experiment with the dimensions, colors, and positioning to fit your specific scenario. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}