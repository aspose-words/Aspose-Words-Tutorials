---
category: general
date: 2026-02-10
description: Create rectangle shape in a Word document using Aspose.Words for Java.
  Learn how to set shadow color, how to add shadow, and create word document programmatically.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: en
og_description: Create rectangle shape in a Word document using Aspose.Words for Java.
  Follow this step‑by‑step tutorial to set shadow color, add shadow, and create word
  document.
og_title: Create rectangle shape in Word with Java – Full Guide
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

Ever needed to **create rectangle shape** in a Word document but weren't sure where to start? You're not alone—many developers hit that wall when they first try to programmatically draw graphics in Word. The good news? With Aspose.Words for Java you can drop a rectangle onto a page, give it a nice shadow, and save the file in seconds. In this tutorial we’ll walk through exactly **how to add shadow**, **set shadow color**, and **create word document** from scratch.  

We'll cover everything you need: the required libraries, each line of code, why certain settings matter, and a few tricks you might not find in the official docs. By the end you’ll have a ready‑to‑run example that creates a rectangle shape with a soft gray shadow, saved as *Shadow.docx*.

## Prerequisites – What You Need Before You Start

Before we dive into the code, make sure you have the following:

| Requirement | Reason |
|-------------|--------|
| Java Development Kit (JDK) 8 or newer | Aspose.Words runs on any modern JDK. |
| Maven or Gradle (optional) | Simplifies adding the Aspose.Words dependency. |
| Aspose.Words for Java license (or a free trial) | The library is commercial; a trial works for testing. |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Helps you run and debug the example quickly. |

If you already have a Java project, just add the Maven coordinate:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

No fancy setup beyond that—just a plain `public static void main` method will do.

![create rectangle shape example](https://example.com/rectangle-shadow.png "create rectangle shape with shadow in Word")

*Image alt text: create rectangle shape example showing a cyan rectangle with a gray shadow.*

## Step 1 – Create a New Word Document

The first thing we have to do is spin up a blank document. Think of it as opening a fresh Word file that you’ll later paint on.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Why start with a blank `Document`? Because Aspose.Words treats the `Document` class as the canvas for all subsequent operations—adding paragraphs, tables, or shapes. If you skip this step you’ll get a `NullPointerException` the moment you try to insert anything.

## Step 2 – Set Up a DocumentBuilder

A `DocumentBuilder` is your friendly pen that writes into the `Document`. It’s the recommended way to add content because it automatically manages the cursor position.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

You might wonder, “Why not manipulate the document directly?” The answer: the builder abstracts away low‑level details like section handling, making the code cleaner and less error‑prone.

## Step 3 – Insert the Rectangle Shape

Now comes the fun part—**how to create shape**. We’ll insert a rectangle that’s 100 × 50 points and give it a cyan fill so you can actually see it.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

A couple of notes:

* `ShapeType.RECTANGLE` tells Aspose we want a rectangle; you could swap it for `OVAL`, `LINE`, etc.
* The dimensions are expressed in points (1 pt ≈ 1/72 in). Adjust them to fit your layout.
* Without a fill color the shape would be invisible against a white page—hence the cyan.

## Step 4 – Add a Shadow and **Set Shadow Color**

Here’s where we answer the **how to add shadow** part of the puzzle. The `ShadowFormat` object controls every visual aspect of the shadow, from color to blur radius.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Why these particular values?

* **Visibility** – Without `setVisible(true)` the rest of the settings are ignored.
* **Color** – Gray is a neutral choice that works on both light and dark backgrounds. Feel free to replace `java.awt.Color.GRAY` with any `java.awt.Color` you like.
* **Blur radius** – A value of `5.0` gives a gentle feather; larger numbers make the shadow look more diffuse.
* **OffsetX/Y** – Offsets shift the shadow right and down, mimicking a light source from the top‑left.
* **Transparency** – A semi‑transparent shadow blends better with the page, especially when printing.

If you need a sharper look, drop the blur radius to `0` and increase the offset. Experimentation is encouraged—shadows are highly visual, and the right settings depend on your document’s design.

## Step 5 – Save the Document

Finally, we persist everything to a `.docx` file. You can choose any path you like; just make sure the directory exists.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

When you open *Shadow.docx* in Microsoft Word, you’ll see a cyan rectangle with a subtle gray shadow hovering 4 pts to the right and bottom. That’s the complete **create word document** workflow.

### Expected Result

| Element | Appearance |
|---------|------------|
| Rectangle | Cyan fill, 100 × 50 pt size |
| Shadow | Gray, 30 % transparent, 5 pt blur, offset (4, 4) |
| File | `Shadow.docx` stored at the path you provided |

If the shape doesn’t appear, double‑check that the fill color isn’t the same as the page background and that the shadow is set to visible.

## Pro Tips & Common Pitfalls

* **Pro tip:** Use `rectangle.setStrokeColor(java.awt.Color.BLACK);` if you want a border around the shape. It makes the rectangle stand out more on a printed page.
* **Watch out for:** Saving to a read‑only folder will throw an `IOException`. Choose a writable location or adjust file permissions.
* **Edge case:** If you need a transparent fill (no color), call `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. The shape will still cast a shadow, which can be useful for watermark‑style graphics.
* **Performance note:** Adding hundreds of shapes in a loop can increase memory usage. Call `document.save` only once after all shapes are added.

## Full Working Example

Below is the entire program you can copy‑paste into a Java class called `ShadowDemo`. It compiles and runs as‑is (provided you have the Aspose.Words JAR on the classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Run the program, open the resulting *Shadow.docx*, and you’ll see the rectangle with its shadow exactly as described.

## What If You Need More Shapes?

You might wonder, “Can I **create rectangle shape** multiple times or use other shapes?” Absolutely. Just loop over the insertion code and adjust coordinates using `builder.moveTo` or `builder.insertParagraph`. The same shadow settings can be reused by extracting them into a helper method:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Call `applyStandardShadow(rectangle);` after each shape insertion to keep your code DRY (Don’t Repeat Yourself).

## Next Steps – Going Beyond the Basics

Now that you know **how to add shadow**, consider exploring these related topics:

* **How to set shadow color** for text runs – gives titles a subtle lift.
* **Create word document** with tables and images – combine shapes with other content.
* **How to create shape** animations using Word’s built‑in

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}