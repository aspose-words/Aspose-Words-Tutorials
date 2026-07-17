---
category: general
date: 2026-07-16
description: how to insert group shape in Java using Aspose.Words – add rectangle
  shape, set shape dimensions, and create colored rectangle and circle.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: en
lastmod: 2026-07-16
og_description: 'how to insert group shape in Java: a hands‑on guide to add rectangle
  shape, set shape dimensions, and create colored rectangle and circle with Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Insert Group Shape in Java – Full Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: how to insert group shape in Java – Complete Guide
url: /java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# how to insert group shape in Java – Complete Guide

Ever wondered **how to insert group shape** in a Word document using Java? You're not the only one. Whether you're building a report generator or a dynamic flyer creator, grouping shapes keeps your layout tidy and your code manageable.

In this tutorial we’ll walk through the exact steps to **add rectangle shape**, **set shape dimensions**, and **create colored rectangle** and **create colored circle** using the Aspose.Words library. By the end you’ll have a runnable program that produces a .docx file with a blue rectangle and a red circle neatly wrapped inside a group.

## Prerequisites

Before we dive in, make sure you have:

- Java 17 (or any recent JDK) installed and configured.
- Maven or Gradle to manage dependencies.
- Aspose.Words for Java 23.9 or newer – you can grab it from Maven Central.
- A basic understanding of Java syntax – nothing fancy required.

If you’re missing any of these, grab the JDK from Oracle’s site and add the Aspose.Words dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Now that the groundwork is set, let’s get our hands dirty.

## how to insert group shape – Overview

The core idea is simple: create a `Document`, open a `DocumentBuilder`, insert a **group shape**, then drop individual shapes (a rectangle and a circle) into that group. The group acts like a container, so moving it later will shift everything inside – ideal for complex layouts.

Below is the full, ready‑to‑run code. Feel free to copy‑paste it into a new Java class called `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro tip:** The `setLeft` and `setTop` values are relative to the group’s origin, not the page. This makes repositioning the whole group a breeze later on.

### What just happened?

1. **Document & Builder** – We spin up an empty Word file and a `DocumentBuilder` that lets us insert content.
2. **Group Shape** – `builder.insertGroupShape()` creates a container. Think of it as a folder for drawing objects.
3. **Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size it, position it, and fill it with blue – that’s the **create colored rectangle** step.
4. **Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle, then filling it red – that’s the **create colored circle** part.
5. **Saving** – Finally we persist everything to `GroupShapeDemo.docx`.

Run the program (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) and open the resulting file. You should see a blue rectangle on the left and a red circle on the right, both locked inside a single group box.

## Adding a Rectangle Shape

If you only need a rectangle without grouping, you can skip the `insertGroupShape()` call and append the rectangle directly to the document’s body. However, grouping gives you the flexibility to move, rotate, or delete multiple shapes in one go.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Notice how we used **add rectangle shape** logic here. The rectangle appears on the page as an independent object. In most real‑world scenarios you’ll want the group, though, because it preserves relative positioning.

## Setting Shape Dimensions

When you see methods like `setWidth` and `setHeight`, remember they accept **points** (1/72 inch). If you prefer millimeters, convert first:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

This snippet demonstrates **set shape dimensions** with a unit conversion – handy when your design specs come from a UI mockup that uses metric units.

## Creating a Colored Rectangle

Coloring a shape is as simple as calling `getFill().setForeColor()`. You can pass any `java.awt.Color`. Want a gradient? Use `setForeColor` for the start color and `setBackColor` for the end.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

That’s a quick way to **create colored rectangle** with a gradient fill instead of a solid hue.

## Creating a Colored Circle

Circles are just ellipses with equal width and height. The same color logic applies:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

If you need a transparent fill, set the alpha channel:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Now you’ve mastered the **create colored circle** technique.

## Saving the Document

Aspose.Words lets you output to many formats: DOCX, PDF, HTML, PNG, you name it. For this demo we stick with DOCX because it preserves the vector shapes perfectly.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Switching the `SaveFormat` is all it takes to generate a PDF version of the same grouped artwork.

## Common Pitfalls & How to Avoid Them

- **Forgot to add the shape to the group?** The shape will appear on the page but won’t move with the group. Always call `group.appendChild(yourShape)`.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}