---
category: general
date: 2026-10-16
description: Create a blank Word document, insert shape in Word, add outer shadow,
  and save as PDF using Python.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: en
lastmod: 2026-10-16
og_description: Create a blank Word document with an outer shadow shape using Aspose.Words
  for Python. This guide shows how to insert the shape, apply the shadow, and save
  the file as a PDF.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Create blank Word document with shape shadow – Python guide
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Create blank Word document with shadowed shape in Python
url: /python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank Word document with shadowed shape in Python

If you need to **create blank Word document** and add a custom graphic, this guide has you covered. We'll walk through how to **insert shape in Word**, apply an **outer shadow shape**, and finally **save as PDF using Python**.

You’ll learn how to set up Aspose.Words for Python, build a rectangle, style its shadow, and generate a PDF that preserves the visual effect. No prior experience with the Aspose API is required, but you should have basic Python knowledge and a working installation of Python 3.10 or later.

## Prerequisites

Before you start, make sure you have:

* Python 3.10 or newer installed.
* An active Aspose.Words for Python license (a free trial works for evaluation).
* `pip` access to install the `aspose-words` package.
* Write permission to the directory where the PDF will be saved.

You can install the library with a single command:

```bash
pip install aspose-words
```

## Create blank Word document – environment setup

The first step is to create an empty Word file that will serve as the canvas for the shape.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` represents a completely blank Word file. By using `DocumentBuilder` you gain access to methods like `insert_shape`, which we’ll use in the next step.

## Insert shape in Word and set dimensions

Now we add a rectangle that will later receive an outer shadow. The size is expressed in points (1 pt ≈ 1/72 inch).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

The `insert_shape` call returns a `Shape` object that you can further customize. At this point the document already contains a visible rectangle when opened in Microsoft Word.

## Add outer shadow shape – customizing the effect

Aspose.Words provides a `ShadowEffect` class to define shadow properties such as style, blur, distance, and color.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Setting `style` to `OUTER` ensures the shadow appears outside the rectangle’s border, giving a subtle 3‑D look. You can experiment with `blur` and `distance` to achieve a tighter or more diffused shadow.

## Save as PDF python – finalizing the document

After styling the shape, the document can be saved directly as a PDF. Aspose.Words handles the conversion internally, preserving the shadow effect.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

When you open `shape_with_shadow.pdf` in any PDF viewer, you’ll see the rectangle with the outer shadow exactly as it appeared in Word.

## Full working example

Below is the complete script that combines all steps. Copy it into a file named `create_word_with_shadow.py` and run it.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Expected output**

Running the script prints a confirmation line, e.g.:

```
PDF generated at: output/shape_with_shadow.pdf
```

Opening the resulting PDF shows a single page containing a 200 pt × 100 pt rectangle with a soft black outer shadow.

## Common variations and edge cases

* **Changing shadow color** – Replace `aw.Color.black` with any other `aw.Color` value, such as `aw.Color.red` or `aw.Color.from_argb(255, 0, 120, 215)`.
* **Using a different shape** – Change `aw.drawing.ShapeType.RECTANGLE` to `OVAL`, `DIAMOND`, or any supported enum value.
* **Saving as DOCX instead of PDF** – Call `doc.save("output/shape.docx")` to keep the Word format.
* **Multiple shapes** – Create additional shapes by calling `builder.insert_shape` again; each shape can have its own `ShadowEffect`.

**Pro tip:** If you need to place the shape at a specific location, set `rectangle.left` and `rectangle.top` after insertion. This gives you pixel‑perfect control over placement.

## Conclusion

You now know how to **create blank Word document**, **insert shape in Word**, **add outer shadow shape**, and **save as PDF using Python**. The complete code sample demonstrates the end‑to‑end workflow, and the explanations clarify why each API call is necessary.

From here you can explore more advanced styling options, add text inside the shape, or combine multiple shapes to build complex diagrams. Experiment with different shadow parameters to match your brand’s visual language, and integrate this approach into larger document‑generation pipelines.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create PDF from Word – Complete Python Guide with Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}