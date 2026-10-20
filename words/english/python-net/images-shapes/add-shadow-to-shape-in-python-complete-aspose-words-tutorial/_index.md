---
category: general
date: 2026-06-08
description: Add shadow to shape using Aspose.Words for Python and set shape fill
  color in just a few steps. Learn the full workflow with runnable code.
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: en
og_description: Add shadow to shape with Aspose.Words for Python and set shape fill
  color instantly. Follow this step‑by‑step tutorial to create PDF output.
og_title: Add Shadow to Shape in Python – Full Aspose.Words Guide
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
url: /python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add Shadow to Shape in Python – Complete Aspose.Words Tutorial

Ever wondered how to **add shadow to shape** when generating a document with Aspose.Words for Python? You're not the only one. Whether you're building a report template, a marketing flyer, or a technical diagram, a subtle shadow can make a rectangle pop and look more professional.  

In this guide we’ll also show you **how to set shape fill color**, so you get a fully styled rectangle ready for PDF export. The solution is straightforward, the code is ready‑to‑run, and the reasoning behind each line is explained in plain English.

## What This Tutorial Covers

- Initializing an Aspose.Words document and builder.  
- Inserting a rectangle shape and **setting its fill color**.  
- Defining and applying a **shadow effect** to that shape.  
- Saving the result as a PDF.  
- Full, runnable example plus tips for common pitfalls.

By the end of the article you’ll be able to drop a styled rectangle into any Word or PDF file with just a few lines of Python. No external tools, no guesswork.

> **Prerequisites** – You need Python 3.7+ and the `aspose-words` package (`pip install aspose-words`). An IDE or text editor of your choice will do; Visual Studio Code works great.

---

## Add Shadow to Shape – Step‑by‑Step

Below we break the process into logical chunks. Each step includes the exact code you need, a short explanation of *why* it matters, and a quick tip to keep you from hitting a wall later on.

### Step 1: Create the Document and Builder

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**Why this matters:** `Document` is the container for everything—pages, styles, images, and shapes. The `DocumentBuilder` is the high‑level API that lets us place objects without worrying about low‑level node trees.

### Step 2: Insert a Rectangle Shape and Set Its Fill Color

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**Why this matters:** The shape acts like a canvas for our shadow. By **setting the shape fill color** we make sure the rectangle isn’t just a transparent box; it becomes a visible element that the shadow can accentuate. You can replace `Color.BLUE` with any RGB value or even a gradient if you need more flair.

> **Pro tip:** If you plan to reuse the same color across many shapes, store it in a variable (`my_fill = Color.from_argb(0, 120, 200, 255)`) and reuse that reference.

### Step 3: Define the Shadow Effect

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**Why this matters:** A shadow isn’t just a visual gimmick; it conveys depth and hierarchy. The `blur_radius` controls softness, `distance` determines the offset, and `direction` lets you simulate a light source. Adjust these values to match your design language.

### Step 4: Apply the Shadow to the Shape

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**Why this matters:** Until this line runs, the shape remains flat. Assigning the `shadow_effect` tells Aspose.Words to render the rectangle with the defined shadow when the document is saved.

### Step 5: Save the Document as PDF

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**Why this matters:** Saving as PDF locks in the visual styling, making the shadow appear exactly as you designed it. You can also save as `.docx` if you need further editing later—Aspose.Words handles both formats seamlessly.

---

## Set Shape Fill Color – Customizing Appearance

If you need a different hue, replace the `Color.BLUE` assignment with any of the following examples:

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **Why you might want this:** A semi‑transparent fill combined with a shadow can create a “glass” effect popular in modern UI mock‑ups.

---

## Full Working Example

Here’s the entire script in one block. Copy‑paste it into a file named `shadow_shape.py` and run it—assuming you’ve installed `aspose-words`.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**Expected output:** Open `ShadowShape.pdf` and you’ll see a blue rectangle with a soft, diagonal black shadow offset to the bottom‑right. The shadow should look slightly blurred, giving the shape a lifted appearance.

---

## Common Pitfalls & Pro Tips

| Issue | Why it Happens | Fix |
|------|----------------|-----|
| **Shadow not visible** | The shape’s fill is fully transparent or the PDF viewer disables shadows. | Ensure `fill_color` is opaque (`alpha = 255`) or adjust the shadow’s `color` opacity. |
| **File path error** | `YOUR_DIRECTORY` doesn’t exist or you lack write permission. | Use `os.makedirs("YOUR_DIRECTORY", exist_ok=True)` before `doc.save`. |
| **Incorrect import** | Trying to import `ShadowEffect` from the wrong sub‑module. | Import exactly as shown: `from aspose.words.drawing import ShadowEffect, ShadowType, Color`. |
| **Unexpected color** | Using `Color.from_argb` with wrong order (alpha, red, green, blue). | Remember the order: **alpha**, **red**, **green**, **blue**. |

---

## Next Steps – Expand Your Shape Toolkit

Now that you know how to **add shadow to shape** and **set shape fill color**, you can explore:

- **Gradient fills** (`LinearGradientBrush`) for richer backgrounds.  
- **Multiple shadows** (inner + outer) by chaining `ShadowEffect` objects.  
- **Other shape types** (`Ellipse`, `Polygon`) to create icons or flow‑chart elements.  
- **Embedding the PDF** into a web response or email attachment using Flask or Django.

Each of these topics builds on the same core concepts covered here, so you’ll feel right at home.

---

## Conclusion

We’ve walked through the complete process of **adding shadow to shape** in Aspose.Words for Python while also **setting the shape fill color**. From document creation to PDF export, the code is self‑contained and ready for production use.  

Feel free to tweak the blur radius, distance, or color to match your brand guidelines. If you run into an edge case or have a feature request, drop a comment below—happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Set Up Aspose.Words License in Python](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}