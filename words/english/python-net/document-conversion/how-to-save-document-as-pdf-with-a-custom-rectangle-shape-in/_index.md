---
category: general
date: 2026-10-07
description: Learn how to save document as PDF while adding a rectangle shape and
  custom shadow using Aspose.Words for Python. Step‑by‑step code included.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: en
lastmod: 2026-10-07
og_description: Save document as PDF with a custom rectangle shape using Aspose.Words
  for Python. Follow the full example to draw, style, and export Word to PDF.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Save document as PDF with a rectangle shape – complete Python guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: How to save document as PDF with a custom rectangle shape in Python
url: /python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to save document as PDF with a custom rectangle shape in Python

If you need to **save document as PDF** while adding custom graphics, this guide shows you how. We’ll walk through creating a blank Word file, **drawing a rectangle shape**, setting its size, applying a visible shadow, and finally **export Word to PDF** using the Aspose.Words for Python library.

You’ll finish with a PDF that contains a perfectly positioned rectangle, ready for reports, invoices, or any document‑automation scenario. No external tools are required—just Python and the Aspose.Words package.

## What you’ll need

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | The Aspose.Words for Python API targets modern interpreters. |
| `aspose-words` package (`pip install aspose-words`) | Provides the `aw` namespace used in the code examples. |
| Basic familiarity with Python and object‑oriented programming | The tutorial manipulates objects like `Document` and `Shape`. |
| Write permission to a folder where the PDF will be saved | The `save document as pdf` step writes a file to disk. |

> **Pro tip:** Use a virtual environment (`python -m venv venv`) to keep dependencies isolated.

## How to save document as PDF with a rectangle shape

Below is a complete, runnable example. Each step is explained so you understand **why** we perform the action, not just **what** the code does.

### Step 1: Initialize a new blank document

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Creating a fresh `Document` object gives you a clean page collection. You could also load an existing *.docx* if you wanted to **export Word to PDF** later, but starting blank keeps the example focused.

### Step 2: Add rectangle shape to the document

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

The `add rectangle shape` step uses `ShapeType.RECTANGLE`. By appending the shape to a paragraph, Aspose.Words knows where to render it in the final PDF.

### Step 3: Set rectangle dimensions

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Setting explicit **rectangle dimensions** ensures the shape looks consistent across platforms. You can also use `convert_to_inches` helpers if you prefer imperial units.

### Step 4: (Optional) Apply a visible custom shadow

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

A shadow makes the rectangle stand out in the PDF. The `shadow.visible` flag is required; without it the other properties have no effect.

### Step 5: Save document as PDF

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Calling `document.save` with a **.pdf** extension automatically **save document as pdf** using Aspose.Words’ built‑in PDF renderer. No additional conversion steps are needed, which is why this method is the recommended way to **export Word to PDF**.

> **Why this works:** Aspose.Words writes the document’s layout, including the rectangle and its shadow, directly into the PDF stream. The process is lossless and retains vector quality.

## Full source code (single script)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Running this script produces `shadow_rectangle.pdf` that looks like this:

![Diagram of the generated PDF showing the rectangle shape after save document as pdf](placeholder-image.png)

*The PDF contains a single page with a black‑shadowed rectangle centered in the document.*

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Can I place the rectangle at a specific location?** | Yes. Set `rectangle.left` and `rectangle.top` (in points) before saving. |
| **What if I need multiple shapes?** | Create additional `Shape` objects, configure each, and append them to the same or different paragraphs. |
| **Does the shadow affect PDF size?** | Only marginally; the shadow is stored as vector metadata, not a raster image. |
| **Can I use this to convert existing *.docx* files?** | Absolutely. Replace `aw.Document()` with `aw.Document("input.docx")` and the rest of the steps remain unchanged. |
| **Is there a way to change the rectangle’s fill color?** | Set `rectangle.fill_color = aw.drawing.Color.light_blue` (or any `Color` you prefer). |

## Next steps

Now that you know how to **save document as PDF** with a custom rectangle, you might explore:

* **Export Word to PDF** with headers, footers, and page numbers.  
* **Add other drawing objects** (`Ellipse`, `Polygon`) using the same `Shape` class.  
* **Batch process** a folder of Word files, applying the same rectangle overlay to each.  

These extensions follow the same pattern: create a shape, configure its properties, and **save document as pdf**.

---

**Summary:** This tutorial showed you how to **save document as PDF** while **add rectangle shape**, **set rectangle dimensions**, and apply a custom shadow using Aspose.Words for Python. The complete script is ready to copy, run, and adapt to your own document‑automation pipelines. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Add rectangle to PDF with Aspose.Words – Step‑by‑Step Guide](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Save Document as PDF with Aspose.Words – Complete C# Guide](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}