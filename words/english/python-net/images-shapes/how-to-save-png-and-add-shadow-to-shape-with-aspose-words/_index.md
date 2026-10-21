---
category: general
date: 2026-08-17
description: How to save PNG using Aspose.Words for Python. Learn to add shadow to
  shape, save document as PDF and export Word to PNG in one guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: en
lastmod: 2026-08-17
og_description: How to save PNG with Aspose.Words. This tutorial shows adding a shadow
  to a shape, saving the document as PDF, and exporting Word to PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: How to save PNG and add shadow to shape with Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: How to save PNG and add shadow to shape with Aspose.Words
url: /python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to save PNG and add shadow to shape with Aspose.Words

If you need to **how to save PNG** from a Word file, this guide gives you a complete, runnable solution. You will also see how to **add shadow to shape**, **save document as PDF**, and **export Word to PNG** without leaving the Aspose.Words environment.

The tutorial covers everything required to turn a blank Word document into a PDF and a PNG image, while applying a simple shadow effect to a rectangle shape. No external tools are required, and the code works with Aspose.Words for Python via .NET 7 or later.

## What you will accomplish

By the end of this article you will be able to:

* Create a new Word document programmatically.  
* Insert a rectangle shape and configure a shadow effect.  
* Save the same document as a PDF file.  
* Export the document as a PNG image.  

These steps answer the common query **how to save PNG** while also handling **add shadow to shape** and **save document as PDF** in a single workflow.

## Prerequisites

* Python 3.9 or newer.  
* Aspose.Words for Python via .NET installed (`pip install aspose-words`).  
* Write permission to the output directory you specify.  

If you have not installed Aspose.Words yet, run:

```bash
pip install aspose-words
```

## How to save PNG with Aspose.Words

The first major step is to create a document and a `DocumentBuilder`. The builder gives you a fluent API for inserting content such as shapes, tables, or text.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` represents the entire Word file in memory. `aw.DocumentBuilder` points to the current insertion location, which initially is the start of the first (and only) section.

## Add shadow to shape before exporting

A shape can be any drawing object—rectangle, ellipse, or custom polygon. Here we create a 100 × 100 point rectangle and apply a soft shadow.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Why configure the shadow before saving? Aspose.Words renders the shadow during the PDF and PNG export phases, so the visual effect is preserved in both output formats.

### Pro tip
If you need a sharper shadow, reduce `blur`. For a more pronounced offset, increase `distance`. The `Shadow` class also exposes `angle` and `transparency` for fine‑tuned control.

## Save document as PDF

Saving a Word document as PDF is a one‑liner once the content is ready. The `SaveFormat.PDF` constant tells Aspose.Words to perform the conversion.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

The resulting PDF contains the rectangle with the exact shadow you defined. Aspose.Words handles vector graphics, so the PDF size remains modest.

## Export Word to PNG

Exporting to PNG creates a raster image of each page. By default Aspose.Words uses 96 DPI; you can increase this value for higher‑resolution output by providing a `PngSaveOptions` object.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

When you **export Word to PNG**, each page is saved as a separate PNG file. Because our example document has only one page, only a single PNG file appears.

### Optional: higher‑resolution PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Higher DPI is useful when the PNG will be used in print or when you need a crisp thumbnail.

## Full script – copy, paste, and run

Below is the complete, self‑contained script that implements every step described above. Save it as `generate_assets.py` and run it from the command line.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Expected output

Running the script creates three files:

* `output/output.pdf` – a PDF with a rectangle that casts a black shadow.  
* `output/output.png` – a 96 DPI PNG rendering of the same page.  
* `output/high_res_output.png` – a 300 DPI PNG for higher quality.

Open any of the files in your favorite viewer to verify that the shadow appears exactly as defined.

## Common questions and edge cases

**What if the output directory does not exist?**  
The script calls `os.makedirs(output_dir, exist_ok=True)`, which creates the folder automatically. This prevents a `FileNotFoundError` during the save operations.

**Can I add multiple shapes with different shadows?**  
Yes. Create additional `Shape` objects, configure each `shadow` property independently, and insert them with `builder.insert_node(shape)` before saving.

**Will the shadow be preserved when converting to other raster formats (e.g., JPEG)?**  
Aspose.Words renders the shadow for all raster formats supported by `SaveFormat`. You can replace `aw.SaveFormat.PNG` with `aw.SaveFormat.JPEG` and the shadow will still appear.

**How does this differ from “convert word to pdf”?**  
`convert word to pdf` is essentially the same operation performed in step 4. The same `doc.save` call with `SaveFormat.PDF` handles the conversion internally, preserving layout, fonts, and graphics such as shadows.

**Is there a limit on shape size?**  
Shapes are measured in points (1 pt ≈ 1/72 inch). Very large dimensions may increase the resulting file size, but Aspose.Words imposes no hard limit. Adjust `width` and `height` arguments when constructing `aw.Shape` to suit your layout.

## Conclusion

You now know **how to save PNG** from a Word document while also learning to **add shadow to shape**, **save document as PDF**, and **export Word to PNG** using Aspose.Words for Python. The complete script demonstrates a clean, repeatable pattern that you can adapt for larger documents, multiple pages, or more complex graphic effects.

Next steps could include:

* Experimenting with other `ShapeType` values (ellipse, cloud, etc.).  
* Using `


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}