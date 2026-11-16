---
category: general
date: 2026-11-15
description: Save Word as PDF in Python using Aspose.Words, learn how to export shapes
  and tag floating shapes as inline for accurate docx to PDF conversion.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to pdf
- how to export shapes
- how to convert docx
- how to tag shapes
language: en
lastmod: 2026-11-15
og_description: Save Word as PDF in Python using Aspose.Words. This guide shows how
  to export shapes, tag floating shapes as inline, and reliably convert docx to PDF.
og_image_alt: Screenshot of Python code that saves a Word document as PDF with shape
  tagging
og_title: Save Word as PDF with shape tagging in Python – complete guide
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Save Word as PDF in Python using Aspose.Words, learn how to export
    shapes and tag floating shapes as inline for accurate docx to PDF conversion.
  headline: How to save Word as PDF with shape tagging in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
title: How to save Word as PDF with shape tagging in Python
url: /python/document-conversion/how-to-save-word-as-pdf-with-shape-tagging-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to save Word as PDF with shape tagging in Python

If you need to **save Word as PDF** and keep every drawing exactly where it belongs, this guide shows you a reliable way to do it with Aspose.Words for Python. You’ll also learn **how to export shapes** and **how to tag shapes** so that floating objects become inline elements during the conversion.

In this tutorial we cover:

* Converting a DOCX file to PDF (`convert docx to pdf`)  
* Exporting floating shapes as inline tags (`how to export shapes`)  
* Tagging shapes during the PDF save operation (`how to tag shapes`)  

No external tools are required—just a few lines of Python code.

## Prerequisites

Before you start, make sure you have:

* Python 3.8+ installed  
* An active Aspose.Words for Python license (or a free trial)  
* The `aspose-words` package installed (`pip install aspose-words`)  
* A DOCX file (`input.docx`) that contains floating shapes (pictures, text boxes, etc.)

## Step 1: Install and import Aspose.Words

First, add the library to your environment and import it in your script.

```python
# Install the package (run once):
# pip install aspose-words

import aspose.words as aw
```

*Why?* The `aspose.words` module provides the `Document` class and `PdfSaveOptions` we need to control shape handling.

## Step 2: Load the Word document

Use the `Document` constructor to read the source file.

```python
# Load the Word document you want to convert
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

If the file does not exist, Aspose.Words raises a `FileNotFoundError`. Wrap the call in a `try/except` block for production code.

## Step 3: Configure PDF save options – export and tag shapes

The key to a clean conversion is the `PdfSaveOptions` object. Setting `export_floating_shapes_as_inline_tag` to `True` tells the engine to treat floating drawings as inline elements, which eliminates layout shifts in the resulting PDF.

```python
# Create PDF save options and enable inline tagging for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes
```

*Why?* When `export_floating_shapes_as_inline_tag` is `False` (the default), floating shapes keep their original position metadata, which can cause them to appear misplaced in the PDF. Enabling the inline tag forces Aspose.Words to embed a small XML tag that the PDF renderer interprets as an inline object, preserving visual fidelity.

## Step 4: Save the document as PDF

Now write the PDF file using the configured options.

```python
# Save the document as a PDF, applying the shape‑tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)

print(f"PDF saved to {output_path}")
```

After execution, `output.pdf` contains the original Word layout with all floating shapes correctly rendered as inline elements.

## Step 5: Verify the conversion (optional)

You can programmatically verify that the PDF was created and contains at least one page:

```python
import os
from aspose.pdf import Document as PdfDocument

if os.path.exists(output_path):
    pdf_doc = PdfDocument(output_path)
    print(f"PDF has {pdf_doc.pages.count} page(s).")
else:
    raise FileNotFoundError("PDF was not created.")
```

*Tip:* Use a PDF viewer to double‑check that pictures, text boxes, and callouts appear exactly where they were in the DOCX file.

## Common variations and edge cases

| Situation | What to change |
|-----------|----------------|
| **You need to keep floating shapes floating** | Set `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **Convert many files in a batch** | Loop over a list of file paths and reuse a single `PdfSaveOptions` instance. |
| **You want to embed a password** | Use `pdf_opts.encrypt_options.password = "your‑password"` before calling `save`. |
| **Large documents cause memory pressure** | Enable `pdf_opts.memory_optimization = True` to reduce RAM usage. |

## Pro tip: handle missing fonts

If the source DOCX uses fonts that aren’t installed on the server, PDF rendering may fall back to a default font. Register the missing fonts with `FontSettings`:

```python
font_settings = aw.FontSettings()
font_settings.set_fonts_folder("YOUR_DIRECTORY/fonts", recursive=True)
doc.font_settings = font_settings
```

This ensures the PDF looks identical to the original Word file.

## Full runnable example

```python
import aspose.words as aw
import os

def convert_docx_to_pdf(input_path: str, output_path: str) -> None:
    """
    Saves a Word document as PDF while tagging floating shapes as inline.
    """
    # Load the DOCX
    doc = aw.Document(input_path)

    # Optional: register custom fonts
    # font_settings = aw.FontSettings()
    # font_settings.set_fonts_folder("fonts", recursive=True)
    # doc.font_settings = font_settings

    # Configure PDF options to export shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True  # how to tag shapes

    # Save as PDF
    doc.save(output_path, pdf_opts)
    print(f"PDF saved to {output_path}")

if __name__ == "__main__":
    INPUT = "YOUR_DIRECTORY/input.docx"
    OUTPUT = "YOUR_DIRECTORY/output.pdf"

    if not os.path.isfile(INPUT):
        raise FileNotFoundError(f"Input file not found: {INPUT}")

    convert_docx_to_pdf(INPUT, OUTPUT)

    # Verify creation
    if os.path.isfile(OUTPUT):
        from aspose.pdf import Document as PdfDocument
        pdf = PdfDocument(OUTPUT)
        print(f"Conversion successful – PDF has {pdf.pages.count} page(s).")
    else:
        raise RuntimeError("PDF conversion failed.")
```

Running the script produces `output.pdf` with all floating shapes correctly tagged, giving you a clean **save word as pdf** result.

## Conclusion

You now know how to **save Word as PDF** in Python while controlling shape handling. By configuring `PdfSaveOptions.export_floating_shapes_as_inline_tag`, you can reliably **convert docx to pdf**, **export shapes** as inline tags, and answer **how to tag shapes** during conversion.  

From here you might explore:

* Adding watermarks (`pdf_opts.add_watermark`) – a natural extension of PDF customization.  
* Converting other formats (HTML, EPUB) using the same `save` pattern.  
* Automating batch conversions for large document repositories.

Give the script a spin, experiment with the optional settings, and integrate it into your document‑processing pipeline today. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Save Word as PDF – Convert Shapes to Inline with Aspose.Words](/words/english/python-net/document-conversion/save-word-as-pdf-convert-shapes-to-inline-with-aspose-words/)
- [How to save Word as PDF with Aspose.Words for Python](/words/english/python-net/document-conversion/how-to-save-word-as-pdf-with-aspose-words-for-python/)
- [How to convert DOCX to PDF in Python using Aspose.Words](/words/english/python-net/document-conversion/how-to-convert-docx-to-pdf-in-python-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}