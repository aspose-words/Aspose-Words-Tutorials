---
category: general
date: 2026-07-03
description: Create rectangle shape in Java and learn how to add shadow to shape,
  apply shadow effect, set shape transparency, and create blank document quickly.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: en
og_description: Create rectangle shape in Java with shadow, transparency and a blank
  document. Follow this guide to master shape handling.
og_title: Create rectangle shape in Java – Full Programming Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Create rectangle shape in Java – Complete Step‑by‑Step Guide
url: /java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Java – Complete Step‑by‑Step Guide

Ever wondered how to **create rectangle shape** in a Word document using Java? You're not the only one—developers often need a quick way to add geometric graphics, then give them a subtle shadow so the layout feels more polished. In this tutorial we’ll walk through the whole process: from spinning up a **create blank document** to **add shadow to shape**, **apply shadow effect**, and even **set shape transparency** for that professional look.

The code snippet below is a fully functional example that you can copy‑paste into your project. No external documentation required—just follow the steps, understand the “why,” and you’ll be generating shadowed rectangles in seconds.

## What You’ll Learn

- How to **create rectangle shape** programmatically with Aspose.Words for Java.
- The exact calls needed to **add shadow to shape** and configure its visual properties.
- Ways to **apply shadow effect** and tweak parameters like offset, blur radius, and color.
- Techniques to **set shape transparency** for a more subtle appearance.
- How to **create blank document**, insert the shape, and save the result.

> **Pro tip:** All of these actions are performed on a single `Document` instance, which means you can chain them together without worrying about intermediate file I/O.

## Prerequisites

Before we dive in, make sure you have:

- Java 17 (or any recent JDK) installed.
- Aspose.Words for Java library added to your project (Maven coordinates: `com.aspose:aspose-words:23.12`).
- A Java IDE or simple text editor—nothing fancy, just a place to compile and run.

If you’re missing any of these, grab the JDK from Oracle and pull the Aspose dependency via Maven or Gradle. Once that’s set, you’re ready to roll.

## Step 1: **Create blank document** – the canvas for everything

The very first thing you need is an empty `Document` object. Think of it as a fresh sheet of paper; without it, there’s nowhere to put your rectangle.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Why start with a blank document? Because every shape lives inside a `Section`, and a newly‑instantiated `Document` already contains a default section with a body ready to receive nodes. Skipping this step would force you to manually create sections later, which adds unnecessary complexity.

## Step 2: **Create rectangle shape** and define its size

Now that we have a canvas, let’s **create rectangle shape**. The `Shape` class takes the document reference and a `ShapeType`. Here we pick `RECTANGLE` and set width/height in points (1 pt ≈ 1/72 inch).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Why set `WrapType.INLINE`? Inline wrapping makes the shape behave like a character in the paragraph, ensuring it moves with surrounding text. If you need floating behavior, switch to `WrapType.SQUARE` or `WrapType.TOP_BOTTOM`.

## Step 3: **Apply shadow effect** – give the rectangle depth

A flat rectangle looks… well, flat. Adding a shadow makes it pop. We’ll **apply shadow effect** by creating a `ShadowEffect` instance, then tweaking its visual properties.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Let’s unpack this a bit:

- **Color** – `Color.getGray(0.5)` yields a 50 % gray, which is neutral and works on most backgrounds.
- **OffsetX/Y** – Positive values push the shadow to the right and down; negative values would move it left/up.
- **BlurRadius** – Larger values create a softer, more diffused shadow.
- **Transparency** – Ranges from `0` (opaque) to `1` (fully transparent). Here we chose `0.3` for a subtle effect.

## Step 4: **Add shadow to shape** – bind the effect

Creating the effect isn’t enough; we must **add shadow to shape** by assigning the `ShadowEffect` object to the rectangle.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Behind the scenes, this call updates the underlying OpenXML markup (`<w:shdw>`) that Word uses to render shadows. If you inspect the saved `.docx`, you’ll see a `<w:effect>` element populated with the parameters we set.

## Step 5: **Set shape transparency** – optional but often useful

Sometimes you want the rectangle itself to be semi‑transparent, letting background text show through. The `Shape` class exposes `setFillColor` and `setFillTransparency`. Here’s a quick example that makes the rectangle 40 % transparent:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Why might you do this? Imagine a watermark or a highlighted call‑out where the underlying content must remain readable. Adjust the transparency value to suit your design language.

## Step 6: Insert the shape into the document

We’ve built the rectangle, added a shadow, and (optionally) set its transparency. The final step is to **add the shape to the first section of the document**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Appending the shape to the body places it at the end of the first paragraph. If you need a specific insertion point, retrieve the target `Paragraph` and use `insertBefore` or `insertAfter`.

## Step 7: Save the document – see the result

All that work culminates in a single `save` call. Choose a path that makes sense for your environment.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Open the resulting `ShadowShape.docx` in Microsoft Word or LibreOffice, and you’ll see a crisp rectangle with a gentle gray shadow, slightly transparent if you kept the optional step. The visual matches the parameters we defined programmatically.

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*Image alt text:* **create rectangle shape with shadow** – visual representation of the final output.

## Common Questions & Edge Cases

### What if I want a different shadow color?

Simply change the `setColor` call:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Remember that overly vivid shadows can look unprofessional; subtle tones usually work best.

### Can I apply the same shadow to multiple shapes?

Yes. Create one `ShadowEffect` instance, configure it, then reuse it:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Just avoid mutating the `ShadowEffect` after you’ve attached it to other shapes, unless you intend to update them all.

### How do I change the shadow blur dynamically?

Expose a UI slider that maps to `setBlurRadius`. Values between `2` and `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.

### What if I need the shape to float rather than be inline?

Swap the wrap type:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Floating shapes give you more layout freedom but require extra positioning logic.

## Full Working Example

Below is the complete, copy‑paste‑ready program that incorporates all the steps we discussed. Run it as a regular Java application.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Expected output:** When you open `ShadowShape.docx`, you’ll see a white rectangle, 200 × 100 pt, centered in the first paragraph, with a medium‑gray shadow offset by 5 pt, blurred with radius 8, and 30 % transparent. The rectangle itself is 40 % transparent, allowing any underlying text to peek through.

## Wrapping Up

We’ve just **create rectangle shape** from scratch, **add shadow to shape**, **apply shadow effect**, and even **set shape transparency**—all while **create blank document** as the foundation. The approach is straightforward, relies on Aspose.Words’ fluent API, and can be extended to circles, stars, or custom polygons.

What’s next on your roadmap? Try swapping `ShapeType.RECTANGLE` for `ShapeType.OVAL` to generate shadowed circles, or experiment with gradient fills for


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}