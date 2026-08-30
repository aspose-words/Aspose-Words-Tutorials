---
category: general
date: 2026-06-27
description: Learn how to insert rectangle shape in Python using Aspose.Words, change
  shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: en
og_description: Master how to insert rectangle shape in Python, change its shadow
  color, add an outer shadow, and apply a shadow effect to shape with Aspose.Words.
og_title: How to Insert Rectangle Shape in Python – Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
url: /python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide

Ever wondered **how to insert rectangle shape** into a Word document using Python? You're not the only one—many developers hit this snag when automating reports or creating templates. The good news is that Aspose.Words makes it a piece of cake, and in this tutorial we’ll walk through the whole process, from drawing the rectangle to giving it a slick outer shadow.

We'll also cover **how to change shadow color**, **how to add outer shadow**, and the final step of **apply shadow effect to shape**. By the end, you’ll have a fully‑styled rectangle that you can drop into any .docx file programmatically.

## Prerequisites

- Python 3.8+ installed on your machine  
- Aspose.Words for Python via `pip install aspose-words`  
- Basic familiarity with Python scripting (no deep Word‑API knowledge required)  

If you already have these, great—let’s dive in. If not, grab the library first; the rest of the guide assumes the import works without a hitch.

## How to Insert Rectangle Shape with Aspose.Words for Python

The first step is exactly what the primary keyword promises: **how to insert rectangle shape**. We’ll create a new document, spin up a `DocumentBuilder`, and drop a rectangle onto the page.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Why this matters:** The `insert_shape` call is the core of *how to insert rectangle shape*. It returns a `Shape` object that you can later manipulate—size, position, fill, borders, you name it. Notice we also set a `fill_color`; without it the shadow might blend into a white page, making it hard to see.

### Pro tip
If you need the rectangle positioned at a specific location, use `builder.move_to` before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.

## Changing the Shadow Color of a Shape

Now that the rectangle lives in the document, let’s answer **how to change shadow color**. Aspose.Words exposes a `ShadowEffect` object where you can set the `color` property to any RGB value.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Why you’d want this:** A dark black shadow can be too harsh, especially on light‑colored documents. Tweaking the color lets you match corporate branding or simply achieve a softer visual effect.

### Edge case
If you forget to set `shadow.opacity`, the default is fully opaque, which can make the shadow look like a solid shape. Always pair a color change with an appropriate opacity level.

## Adding an Outer Shadow Effect

The next question many ask is **how to add outer shadow**. The `ShadowStyle.OUTER` flag tells Aspose.Words to render the shadow outside the shape’s outline rather than inside it.

The code snippet above already uses `ShadowStyle.OUTER`, but let’s isolate this setting for clarity:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

If you switch to `ShadowStyle.INNER`, the shadow will appear *inside* the rectangle, which is useful for embossing effects. For most document‑design scenarios, the outer style gives a natural drop‑shadow look.

## Applying the Shadow Effect to Your Shape

We’ve already **apply shadow effect to shape** by assigning `rectangle.shadow = shadow`. Let’s wrap everything together and save the document, confirming that the effect persists.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

When you open `RectangleWithShadow.docx` in Microsoft Word, you should see a light‑blue rectangle with a subtle gray outer shadow cast at a 45° angle. The shadow will be slightly blurred and offset, exactly as we configured.

### Common pitfalls
- **Missing directory:** `doc.save` will raise an error if the folder doesn’t exist. Create it first or use `os.makedirs`.
- **Version mismatch:** The shadow API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.

## Full Working Example

Below is the complete, ready‑to‑run script that combines all the steps. Copy‑paste it into a file named `rectangle_shadow.py` and execute with `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Expected output:** A Word document (`RectangleWithShadow.docx`) containing a single rectangle with a gray outer shadow. Open it in Word to verify the visual effect.

## Frequently Asked Questions

| Question | Answer |
|----------|--------|
| *Can I use a different shape type?* | Absolutely—replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.TRIANGLE`, etc., and the same shadow logic applies. |
| *What if I need a thicker border?* | Set `rectangle.line_width = 2.0` (points) before applying the shadow. |
| *Is it possible to animate the shadow?* | Not directly with Aspose.Words; you’d need to export to HTML/CSS for animation. |
| *Does this work on macOS?* | Yes—Aspose.Words is platform‑agnostic as long as Python runs. |

## Conclusion

We’ve walked through **how to insert rectangle shape**, demonstrated **how to change shadow color**, explained **how to add outer shadow**, and finally showed you how to **apply shadow effect to shape** using Aspose.Words for Python. The full script is ready to drop into any automation pipeline, giving you a professional‑looking rectangle with a polished shadow in seconds.

Ready for the next step? Try swapping the fill color, experimenting with different `direction` angles, or adding multiple shapes to the same page. You can also explore Aspose.Words’ rich text‑formatting API to combine shadows with styled text—perfect for eye‑catching reports.

If you found this tutorial helpful, give it a thumbs‑up, share it with teammates, or leave a comment with your own variations. Happy coding!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}