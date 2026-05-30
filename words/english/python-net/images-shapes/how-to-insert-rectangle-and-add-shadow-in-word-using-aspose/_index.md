---
category: general
date: 2026-05-30
description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
  Python guide to create a Word document with shape shadow effect.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: en
og_description: How to insert rectangle and add shadow in Word using Aspose – learn
  to create a Word document with shape shadow effect in Python.
og_title: How to insert rectangle and add shadow in Word using Aspose
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: How to insert rectangle and add shadow in Word using Aspose
url: /python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to insert rectangle and add shadow in Word using Aspose

Ever wondered **how to insert rectangle** into a Word file without opening the UI? You’re not alone. Many developers need to generate reports, invoices, or certificates on the fly, and drawing a simple rectangle with a nice shadow can make the output look polished. In this tutorial we’ll walk through the exact steps to create a Word document, drop a rectangle shape, and apply a realistic shadow using Aspose.Words for Python.

We’ll cover everything from setting up the Aspose package to tweaking the shadow’s distance, blur, and opacity. By the end you’ll have a reusable snippet that you can drop into any automation pipeline. No magic, just clear code and a few practical tips.

## Prerequisites

Before we dive in, make sure you have:

- Python 3.8+ installed (the code works on 3.9, 3.10, and newer)
- An active Aspose.Words for Python license or a free evaluation key
- `aspose-words` package installed via `pip install aspose-words`
- A writable folder where the generated **create word document aspose** will be saved

That’s it—no extra DLLs, no COM interop, just pure Python.

## Step 1: Initialize the Document (How to create word document aspose)

First things first: you need a fresh `Document` object. Think of it as a blank canvas. The following code creates the document and a `DocumentBuilder` that will let us insert shapes.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Why this matters:* The `DocumentBuilder` gives you a high‑level API to add paragraphs, tables, and—yes—shapes without dealing with low‑level node trees. If you skip the builder and manipulate nodes directly, you’ll end up with verbose code that’s harder to maintain.

## Step 2: Insert the Rectangle (how to insert rectangle)

Now we actually **how to insert rectangle**. Aspose.Words treats a rectangle as a generic shape type. You specify the width and height in points (1 point ≈ 1/72 inch). Feel free to adjust the numbers to suit your layout.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Pro tip:** If you need the rectangle to be positioned at a specific location on the page, set `shape.left` and `shape.top` after insertion. This gives you pixel‑perfect control.

## Step 3: Access the Shape’s Shadow Format (add shadow to shape)

A shape’s visual flair lives in its `ShadowFormat`. By retrieving it, we gain access to every property that defines the shadow’s look.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

At this point the shadow is invisible—think of it as a hidden layer waiting for your instructions.

## Step 4: Configure the Shadow (how to add shape shadow, apply shadow effect word)

Here’s where the magic happens. We’ll turn the shadow on and tweak its appearance. The values below produce a soft, diagonal shadow that works well for most documents, but you can experiment.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### What each property does

| Property | Effect | Typical Range |
|----------|--------|---------------|
| `visible` | Turns the shadow on/off | `True` / `False` |
| `distance` | How far the shadow sits from the shape | 2 – 10 pts |
| `blur` | Softness of the shadow edges | 4 – 12 pts |
| `color` | Shadow hue; dark gray is a safe default | Any `aw.Color` |
| `opacity` | Transparency; 0 = invisible, 1 = solid | 0.3 – 0.8 for subtle look |
| `angle` | Direction the light comes from | 0 – 360° |

**Why adjust these?** A well‑tuned shadow can make a flat rectangle appear lifted off the page, adding depth without any images. If you set `opacity` too high, the shadow looks harsh; too low and it disappears.

## Step 5: Save the Document (create word document aspose)

Finally, write the file to disk. You can use any extension supported by Aspose.Words (`.docx`, `.pdf`, `.html`). For this tutorial we’ll stick with `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Open the resulting file in Microsoft Word, and you’ll see a crisp rectangle with a subtle shadow—exactly what you’d expect from a professionally designed template.

![how to insert rectangle shape with shadow using Aspose.Words](/images/rectangle-shadow.png){alt="how to insert rectangle shape with shadow using Aspose.Words"}

*The screenshot (above) shows the rectangle with the shadow applied. Notice the gentle blur and the 45° angle, which gives a natural look.*

## Common Variations and Edge Cases

### Adding Multiple Shapes

If you need more than one rectangle, simply repeat the `insert_shape` call. Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top` to avoid overlap.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Changing the Shape Type

While this guide focuses on rectangles, the same pattern works for ovals, stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.CLOUD`, etc., and the shadow settings remain identical.

### Saving to Other Formats

Aspose.Words can export to PDF, PNG, or even XPS with a single line:

```python
doc.save("output/ShapeWithShadow.pdf")
```

The shadow rendering is preserved across formats, so your PDF will look just like the Word file.

### Handling Large Documents

When generating massive reports, consider calling `doc.update_page_layout()` after inserting all shapes. This forces a layout pass and can improve performance when you later convert to PDF.

## Full Working Example (All Steps Combined)

Below is the complete script you can copy‑paste into a file named `rectangle_shadow.py`. Run it with `python rectangle_shadow.py` and check the `output` folder.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Running this script produces the exact same document we discussed earlier. Feel free to tweak the numbers; the code is deliberately simple so you can experiment without fear.

## Frequently Asked Questions

**Q: Does this work on Linux?**


## What Should You Learn Next?

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}