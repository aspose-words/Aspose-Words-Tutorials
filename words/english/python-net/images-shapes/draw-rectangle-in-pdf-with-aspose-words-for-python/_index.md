---
category: general
date: 2026-08-07
description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
  add shadow to shape, configure shape shadow, and save document as PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: en
lastmod: 2026-08-07
og_description: Draw rectangle in PDF with Aspose.Words for Python. This tutorial
  shows how to add shadow to shape, configure shape shadow, and save document as PDF
  for professional document generation.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Draw rectangle in PDF with Aspose.Words for Python – guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Draw rectangle in PDF with Aspose.Words for Python
url: /python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Draw rectangle in PDF with Aspose.Words for Python

If you need to **draw rectangle in PDF** while working in Python, this guide gives you a complete, ready‑to‑run solution. You’ll see exactly how to **add shadow to shape**, configure that shadow, and finally **save document as PDF** for distribution or archiving.

Creating a shaded rectangle is a common requirement for reports, invoices, or visual annotations. By the end of this tutorial you’ll have a single script that produces a PDF containing a rectangle with a realistic shadow, and you’ll understand how to tweak size, color, and offset to fit any design.

## Prerequisites

Before you start, make sure you have:

* Python 3.8+ installed.
* The Aspose.Words for Python via .NET package (`aspose-words`) – install with:

```bash
pip install aspose-words
```

* Write permission to the folder where you intend to save the PDF.

No additional libraries are required; Aspose.Words handles shape creation, shadow configuration, and PDF export internally.

## Step 1: Create a new blank document (draw rectangle in PDF – initialize)

The first step is to instantiate a `Document` object. This object represents the entire PDF file and provides a container for sections, paragraphs, and shapes.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Why this matters:** Aspose.Words treats PDF generation as a conversion from a Word document model, so we start with a `Document` even though the final output is a PDF.

## Step 2: Insert a rectangle shape into the document body

A rectangle is a specific `ShapeType`. We add it to the first section’s body, which automatically creates a new page when saved as PDF.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Explanation:** The `width` and `height` properties control the visual size of the shape in the PDF. Adding text makes the rectangle easier to verify during testing.

## Step 3: Add shadow to shape – enable and customize

Now we turn on the shadow effect and fine‑tune its appearance. This is where the **add shadow to shape** keyword comes into play.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Why configure shape shadow?** Adjusting `blur`, `distance`, and `angle` lets you simulate realistic lighting, which improves readability and visual hierarchy in generated PDFs.

## Step 4: Save document as PDF – final output

With the rectangle and its shadow defined, the last step is to export the Word document to PDF. This satisfies the **save document as pdf** requirement.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

When you open `shadow_rectangle.pdf`, you’ll see a single page containing a gray‑bordered rectangle titled “Shadow demo” with a crisp, diagonal shadow.

### Expected output

* A PDF file named `shadow_rectangle.pdf`.
* One page with a 200 pt × 100 pt rectangle.
* A visible shadow offset 5 pt at a 45° angle, blurred by 8 pt.

## Step 5: Explore variations and edge cases (optional)

Below are common tweaks you might need in real‑world projects:

| Variation | Code snippet | When to use |
|-----------|--------------|-------------|
| **Different shape type** (e.g., ellipse) | `aw.drawing.ShapeType.OVAL` instead of `RECTANGLE` | For rounded graphics or badges |
| **Custom shadow color** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | When a gray or brand‑specific shadow is required |
| **Multiple shapes** | Repeat the shape‑creation block and adjust `left`/`top` properties | To build complex diagrams |
| **No text inside shape** | Omit `rectangle.text = "..."` | When the shape is purely decorative |
| **Higher DPI output** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` with `PdfSaveOptions` set for image quality | For print‑ready PDFs |

**Pro tip:** Always set `shadow.visible = True` before adjusting other properties; otherwise the changes are ignored silently.

## Full script – copy, paste, and run

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Run the script from your terminal or IDE. Replace `YOUR_DIRECTORY` with a real folder path, such as `"/tmp"` or `"C:\\Users\\Me\\Documents"`.

## Conclusion

You now know how to **draw rectangle in PDF** using Aspose.Words for Python, **add shadow to shape**, **configure shape shadow**, and **save document as PDF**. The complete example demonstrates every step from document creation to final export, and the optional variations show how to adapt the code for more complex scenarios.

Next, you might explore:

* Adding other shape types (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Applying gradient fills or borders to enhance visual appeal.
* Using `PdfSaveOptions` to embed fonts or control image compression.

Feel free to experiment with the parameters to match your branding or design guidelines. Happy PDF scripting!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Optimize PDF Bookmarks Using Aspose.Words for Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [Optimize Pdf Loading Python Aspose Words Skip Images](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python Pdf Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}