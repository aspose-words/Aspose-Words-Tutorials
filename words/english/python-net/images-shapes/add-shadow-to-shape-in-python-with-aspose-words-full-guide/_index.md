---
category: general
date: 2026-06-30
description: Add shadow to shape using Aspose.Words for Python. Learn how to set shadow
  distance, customize blur, and save a PDF with shape shadow quickly.
draft: false
keywords:
- add shadow to shape
- how to set shadow distance
- how to add shape shadow
- Aspose.Words Python shadow
- shape formatting Python
language: en
og_description: Add shadow to shape in a Word document with Aspose.Words for Python.
  This tutorial shows how to set shadow distance, blur, and color, then save as PDF.
og_title: Add Shadow to Shape in Python – Complete Aspose.Words Guide
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  headline: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to set
    shadow distance, customize blur, and save a PDF with shape shadow quickly.
  name: Add Shadow to Shape in Python with Aspose.Words – Full Guide
  steps:
  - name: What if I need a different shape?
    text: Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g.,
      `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code
      needed.
  - name: Can I apply a shadow to multiple shapes at once?
    text: 'Yes. Loop over the shapes you create and configure each `shadow_format`
      individually. Here’s a quick snippet:'
  - name: How do I change the shadow’s opacity?
    text: 'Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Add Shadow to Shape in Python with Aspose.Words – Full Guide
url: /python/images-shapes/add-shadow-to-shape-in-python-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add Shadow to Shape in Python with Aspose.Words – Full Guide

Add shadow to shape in a Word document using Aspose.Words for Python is easier than you think. If you've ever wondered **how to set shadow distance** or **how to add shape shadow** for a polished look, this guide has you covered.

In the next few minutes we’ll walk through everything you need: from creating a fresh document, inserting a rectangle, tweaking its shadow properties, to finally saving a PDF that showcases the effect. By the end you’ll be able to drop a shadow on any shape—rectangle, ellipse, or custom drawing—without digging through the API docs.

> **Prerequisites** – You should have Python 3.7+ installed, an Aspose.Words for Python license (or a free evaluation), and a basic familiarity with Python scripting. No other external libraries are required.

---

## Add Shadow to Shape – Step-by-Step Overview

Below is a quick roadmap of what we’ll accomplish:

1. **Create a new document** and a `DocumentBuilder` to edit it.  
2. **Insert a rectangle shape** of the size you need.  
3. **Enable and customize the shadow** – this is where the primary keyword shines.  
4. **Save the document** as a PDF that retains the shape’s shadow.

Each step is broken out into its own section, so you can copy‑paste the code snippets directly into your IDE.

---

## Step 1: Initialize the Document and Builder

First things first—without a `Document` you have nothing to work on. The `DocumentBuilder` is your paintbrush.

```python
import aspose.words as aw

# Create a new, empty Word document
document = aw.Document()

# Attach a builder to the document for easy editing
builder = aw.DocumentBuilder(document)
```

*Why this matters*: The `Document` object represents the whole file, while the `DocumentBuilder` simplifies inserting text, tables, and shapes. Think of the builder as a cursor you can move around the page.

---

## Step 2: Insert a Rectangle Shape

Now we’ll add a rectangle—our canvas for the shadow effect. You can replace `RECTANGLE` with `ELLIPSE`, `STAR`, or any other `ShapeType` if you need a different geometry.

```python
# Insert a rectangle with width=200pt and height=100pt
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

*Pro tip*: The dimensions are in points (1 pt ≈ 1/72 inch). Adjust them to fit your layout; the shadow will scale automatically.

---

## How to Set Shadow Distance

The shadow’s **distance** determines how far it appears from the shape. A larger distance mimics a light source farther away, while a smaller value gives a subtle lift.

```python
# Access the shadow format of the shape
shadow = rectangle_shape.shadow_format

# Make the shadow visible
shadow.visible = True

# Set the distance (in points) from the shape
shadow.distance = 4.0          # <-- this is the "how to set shadow distance" part
```

> **Note**: The distance works together with `angle`. Changing the angle rotates the shadow around the shape, while `distance` pushes it outward.

---

## How to Add Shape Shadow – Customizing Blur, Color, and Angle

Adding a shadow isn’t just about turning it on; you often want to tweak blur, color, and direction for a realistic effect.

```python
# Define how blurry the shadow should be (larger = softer)
shadow.blur_radius = 5.0       # Soft edge for a natural look

# Choose the direction (in degrees). 45° points down‑right.
shadow.angle = 45

# Set the shadow color – black works for most cases
shadow.color = aw.drawing.Color.black
```

*Why these settings?*  
- **Blur radius** softens the edge, preventing a harsh silhouette.  
- **Angle** simulates the light source; 45° is a common default that looks balanced.  
- **Color** can be any `Color` object; try `Color.gray` for a gentler effect.

---

## Step 4: Save the Document as PDF

Once the shape and its shadow are ready, persisting the result is a breeze. Aspose.Words handles the conversion to PDF automatically, preserving the visual fidelity.

```python
# Save the document to a PDF file (adjust the path as needed)
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"Document saved to {output_path}")
```

*Expected output*: Open the generated `ShadowShape.pdf`. You’ll see a single page with a 200 × 100 pt rectangle, its shadow cast 4 pt away at a 45° angle, blurred by 5 pt. The shadow should appear as a subtle gray‑black halo hugging the shape.

---

## Common Questions & Edge Cases

### What if I need a different shape?

Replace `aw.drawing.ShapeType.RECTANGLE` with any other enum value, e.g., `aw.drawing.ShapeType.ELLIPSE`. The same shadow properties apply—no extra code needed.

### Can I apply a shadow to multiple shapes at once?

Yes. Loop over the shapes you create and configure each `shadow_format` individually. Here’s a quick snippet:

```python
for shape_type in [aw.drawing.ShapeType.RECTANGLE, aw.drawing.ShapeType.ELLIPSE]:
    shp = builder.insert_shape(shape_type, 150, 80)
    shp.shadow_format.visible = True
    shp.shadow_format.distance = 3.0
    shp.shadow_format.blur_radius = 4.0
```

### How do I change the shadow’s opacity?

Use the `shadow.transparency` property (0 = opaque, 1 = fully transparent):

```python
shadow.transparency = 0.3   # 30 % transparent
```

---

## Full Working Example

Below is the complete script—copy it, adjust the output folder, and run it. No pieces are missing.

```python
import aspose.words as aw

# 1️⃣ Create a new document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert a rectangle shape (200 × 100 pt)
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Enable and configure the shadow (add shadow to shape)
shadow = rectangle_shape.shadow_format
shadow.visible = True                # Show the shadow
shadow.blur_radius = 5.0             # Soft edges
shadow.distance = 4.0                # How far the shadow lies from the shape
shadow.angle = 45                    # Direction of the light source
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.0            # Fully opaque (optional)

# 4️⃣ Save as PDF
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
document.save(output_path)
print(f"PDF with shape shadow saved at: {output_path}")
```

Run the script, then open the resulting PDF. You should see the rectangle with a crisp, offset shadow—exactly what **add shadow to shape** promises.

---

## Conclusion

We’ve just demonstrated how to **add shadow to shape** in a Word document using Aspose.Words for Python, covering the essential steps to **set shadow distance**, customize blur, angle, and color, and finally export a PDF that retains the effect. This technique works for any shape type, and you can extend it with loops, opacity tweaks, or even gradient shadows.

Ready for the next challenge? Try combining multiple shadows, layering shapes, or generating a report where each chart gets its own stylized shadow. Experimenting will cement the concepts and reveal new possibilities for document automation.

If you found this guide helpful, feel free to share it, star the Aspose.Words repository, or drop a comment with your own shadow‑tweaking tips. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}