---
category: general
date: 2026-02-15
description: Create rectangle shape in a Word document using Java. Learn how to add
  shape shadow, save Word document, and add rectangle shape with Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: en
og_description: Create rectangle shape in a Word file with Java. This guide shows
  how to add shape shadow, save Word document, and add rectangle shape step‑by‑step.
og_title: Create rectangle shape – Java Aspose.Words Tutorial
tags:
- Aspose.Words
- Java
- Document Automation
title: Create rectangle shape in Word with Java – Full Guide
url: /java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Word with Java – Full Guide

Ever needed to **create rectangle shape** in a Word file but weren’t sure where to start? You're not the only one—many developers hit that wall when automating reports or invoices. The good news? With Aspose.Words for Java you can spin up a rectangle, give it a nice shadow, and save the Word document in a handful of lines.

In this tutorial we’ll walk through everything you need: from initializing a blank document, to configuring a shadow, to finally saving the file. By the end you’ll know **how to shadow shape** objects, how to **add shape shadow**, and how to **add rectangle shape** to any Word document you generate. No external docs required—just pure, runnable code.

## Prerequisites

- Java 8 or newer (the API works with Java 11+ as well).  
- Aspose.Words for Java library (version 23.9 or later).  
- An IDE like IntelliJ IDEA or Eclipse—any will do.  
- Basic familiarity with Java syntax.

> **Pro tip:** If you’re using Maven, add the Aspose.Words dependency to your `pom.xml` and let the IDE handle the rest.

---

## Step 1: Initialize a New Document – How to **create rectangle shape**  

First things first: you need a clean canvas. In Aspose.Words that canvas is a `Document` object.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

The `Document` class represents the whole .docx file. Think of it as the notebook where you’ll later **add rectangle shape** and its shadow.

## Step 2: Build the Rectangle – **Add rectangle shape**  

Now we actually construct the rectangle. We’ll set its size, layout, and fill color.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Why `INLINE` wrap? Because we want the shape to behave like a paragraph—perfect for simple reports. You can change it to `TOPBOTTOM` if you need text to flow around the shape later.

## Step 3: Apply a Shadow – **How to shadow shape**  

A flat rectangle looks a bit bland. Adding a shadow gives it depth and makes the document feel more polished. This is where we answer “**how to shadow shape**” in practice.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Each property does something specific:

- `setVisible(true)` turns the shadow on.  
- `setColor` picks a dark gray for a subtle effect.  
- `setBlurRadius` controls how soft the edges appear.  
- `setOffsetX/Y` moves the shadow right and down, mimicking a light source.  
- `setTransparency` makes it slightly see‑through, so the shape stays the star.

> **Note:** If you ever need a colored shadow, just pass a different `java.awt.Color` to `setColor`.

## Step 4: Insert the Shape into the Document  

With the rectangle and its shadow ready, we drop it into the first section of the document.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Appending to the body places the shape where a new paragraph would go. If you want the rectangle at a specific location, you could use `insertBefore` or manipulate the `Paragraph` collection.

## Step 5: **Save Word document** – Persist Your Work  

The final step is to write the file to disk. This is the moment you actually **save Word document**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Replace `YOUR_DIRECTORY` with an absolute or relative path on your machine. After running the program, open `ShadowShape.docx` in Microsoft Word—you should see a light‑gray rectangle with a soft dark shadow.

![Diagram showing a rectangle shape with shadow created using Aspose.Words](https://example.com/rectangle-shadow.png "create rectangle shape with shadow")

---

## Common Questions & Edge Cases  

### What if I need multiple rectangles?  

Just repeat **Step 2** and **Step 3** in a loop, adjusting `setWidth`, `setHeight`, or `setFillColor` each iteration. Remember to give each shape a unique variable name or store them in a list.

### Can I export to PDF instead of DOCX?  

Absolutely. After the shape is added, call `document.save("output.pdf")`. Aspose.Words will handle the conversion, preserving the shadow.

### What about older Word versions?  

Use the overload `document.save("file.doc", SaveFormat.DOC)`. The API automatically downgrades features, but note that some shadow styles may look slightly different in legacy formats.

### How do I change the shadow direction?  

Manipulate `setOffsetX` and `setOffsetY`. Positive X moves the shadow right, negative moves left. Positive Y moves down, negative moves up. Play with those numbers to simulate a light source from any angle.

---

## Tips for Working with Shapes  

- **Group shapes**: If you need a label next to the rectangle, create a `GroupShape` and add both the rectangle and a `TextBox`.  
- **Z‑order matters**: Use `shape.moveToFront()` or `shape.moveToBack()` to control which shape appears on top.  
- **Performance**: Adding hundreds of shapes can be slow. Batch them in a single section, then call `document.updatePageLayout()` once at the end.

---

## Recap  

We’ve covered how to **create rectangle shape** in a Word document using Java, how to **add shape shadow**, and how to **save Word document** with the result. The complete, runnable code lives in the snippets above, and you now understand the “why” behind each property—so you can tweak colors, blur, and offsets to suit any design.

Ready for the next challenge? Try combining the rectangle with a chart, or export the file as PDF and see how the shadow renders. You might also explore **add rectangle shape** inside tables for fancy report layouts.

Happy coding, and may your documents always look as sharp as your code!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}