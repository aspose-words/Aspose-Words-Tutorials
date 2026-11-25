---
category: general
date: 2026-11-25
description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
  and export floating shapes as inline tags in a single step.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx as pdf
- convert docx to pdf
- how to export shapes
- convert word to pdf
- aspose docx to pdf
language: en
lastmod: 2026-11-25
og_description: Save docx as pdf using Aspose.Words, convert docx to pdf, and learn
  how to export shapes as inline tags for perfect PDF output.
og_image_alt: Screenshot showing a DOCX file being saved as PDF with shapes preserved
og_title: Save docx as pdf with Aspose.Words – export shapes correctly
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  headline: How to save docx as pdf with Aspose.Words while exporting shapes
  type: TechArticle
- description: Learn how to save docx as pdf using Aspose.Words, convert docx to pdf,
    and export floating shapes as inline tags in a single step.
  name: How to save docx as pdf with Aspose.Words while exporting shapes
  steps:
  - name: Converting multiple DOCX files in a batch
    text: 'When you need to **convert docx to pdf** for many files, wrap the three
      steps in a loop:'
  - name: Dealing with very large documents
    text: For large Word files, consider enabling `pdf_opts.save_format = aw.SaveFormat.PDF`
      (the default) and adjusting `pdf_opts.compliance` if you need PDF/A compliance.
      These options do not affect shape export but improve compatibility with archival
      systems.
  - name: When shapes should remain floating
    text: If a specific document requires floating shapes to stay floating (e.g.,
      a design‑heavy brochure), set the flag to `False`. The PDF will then render
      shapes as separate drawing objects, which may be preferable for precise graphic
      positioning.
  type: HowTo
tags:
- Aspose.Words
- PDF conversion
- Word automation
title: How to save docx as pdf with Aspose.Words while exporting shapes
url: /python/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-while-exporting-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to save docx as pdf with Aspose.Words while exporting shapes

If you need to **save docx as pdf** and keep every floating shape exactly where it belongs, this guide shows you the complete process. By the end of the tutorial you will be able to convert a Word document to a PDF file, export shapes correctly, and understand why each setting matters.

Converting Word files to PDF is a common requirement for invoice generation, report publishing, and document archiving. This tutorial covers the **convert docx to pdf** workflow, explains **how to export shapes** so they appear inline, and demonstrates the **convert word to pdf** operation using the Aspose.Words library. No external tools are required beyond the Aspose.Words for Python via .NET package.

## Prerequisites

Before you start, make sure you have:

* Python 3.9+ installed on your development machine.  
* The `aspose-words` package (installable via `pip install aspose-words`).  
* A DOCX file that contains floating shapes (e.g., text boxes, pictures, or SmartArt).  
* Write permission to the output directory.

All of these prerequisites are free‑form; the tutorial works on Windows, macOS, and Linux.

## Step 1: Load the source document

The first operation is to load the DOCX file into an `aw.Document` object. This object represents the entire Word document in memory, giving you access to its sections, paragraphs, and drawing objects.

```python
import aspose.words as aw

# Step 1: Load the source document
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

**Why this step matters:**  
Loading the file creates a structured object model that Aspose.Words can manipulate. Without this model the subsequent PDF conversion would have no source to read from.

## Step 2: Configure PDF save options and enable inline export for floating shapes

Aspose.Words provides a `PdfSaveOptions` class that lets you fine‑tune the output PDF. The property `export_floating_shapes_as_inline_tag` controls whether floating shapes are rendered as inline `<w:wrap>` tags (which the PDF renderer treats as part of the text flow) or as separate drawing objects.

```python
# Step 2: Create PDF save options and enable inline export for floating shapes
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
```

**Why this setting is important:**  
When you **how to export shapes** correctly, you avoid the common issue where a shape disappears or moves to an unexpected location in the PDF. Setting the flag to `True` tells the renderer to treat each floating shape as if it were anchored inline, preserving layout fidelity. This is the recommended approach for most business documents.

## Step 3: Save the document as a PDF using the configured options

With the document loaded and the save options prepared, you can now write the PDF file to disk.

```python
# Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

**Why this final step completes the workflow:**  
Calling `doc.save` with the `PdfSaveOptions` instance triggers the conversion pipeline. Aspose.Words reads the DOCX structure, applies the inline‑shape rule, and writes a PDF that mirrors the original layout. After this call, `output.pdf` contains the same text, images, and shapes as the source DOCX.

## Expected output

* `output.pdf` appears in the target folder.  
* All paragraphs, tables, and floating shapes (text boxes, pictures, SmartArt) are positioned exactly as they were in `input.docx`.  
* The file size is comparable to a standard PDF generated from a Word document without shape export tweaks.

If you open the PDF in Adobe Acrobat or any modern viewer, you should see no missing graphics and no shifted elements.

## Common variations and edge cases

### Converting multiple DOCX files in a batch

When you need to **convert docx to pdf** for many files, wrap the three steps in a loop:

```python
import pathlib

source_dir = pathlib.Path("YOUR_DIRECTORY")
for docx_path in source_dir.glob("*.docx"):
    doc = aw.Document(str(docx_path))
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True
    pdf_path = docx_path.with_suffix(".pdf")
    doc.save(str(pdf_path), pdf_opts)
```

### Dealing with very large documents

For large Word files, consider enabling `pdf_opts.save_format = aw.SaveFormat.PDF` (the default) and adjusting `pdf_opts.compliance` if you need PDF/A compliance. These options do not affect shape export but improve compatibility with archival systems.

### When shapes should remain floating

If a specific document requires floating shapes to stay floating (e.g., a design‑heavy brochure), set the flag to `False`. The PDF will then render shapes as separate drawing objects, which may be preferable for precise graphic positioning.

## Pro tips

* **Pro tip:** Always test the PDF on the target viewer (e.g., Chrome, Edge, Acrobat) because some viewers interpret inline tags slightly differently.  
* **Watch out for:** Documents that use legacy VML drawing formats; Aspose.Words automatically converts VML to modern drawing objects, but complex VML may need additional cleanup.  
* **Performance tip:** Reuse a single `PdfSaveOptions` instance when processing many files to reduce object allocation overhead.

## Full, runnable example

Below is the complete script you can copy‑paste into a file named `docx_to_pdf.py`. Replace `YOUR_DIRECTORY` with the actual path on your machine.

```python
import aspose.words as aw
import pathlib

def convert_docx_to_pdf(input_path: pathlib.Path, output_path: pathlib.Path):
    """
    Loads a DOCX file, configures PDF save options to export floating shapes as inline tags,
    and writes the result to a PDF file.
    """
    # Load the DOCX document
    doc = aw.Document(str(input_path))

    # Configure PDF options – export floating shapes as inline tags
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True

    # Save the PDF
    doc.save(str(output_path), pdf_opts)

if __name__ == "__main__":
    base_dir = pathlib.Path("YOUR_DIRECTORY")
    input_file = base_dir / "input.docx"
    output_file = base_dir / "output.pdf"

    convert_docx_to_pdf(input_file, output_file)
    print(f"Conversion complete: {output_file}")
```

Running `python docx_to_pdf.py` produces `output.pdf` with all shapes preserved. The script demonstrates the **aspose docx to pdf** capability in a clean, reusable function.

## Conclusion

You now know how to **save docx as pdf** using Aspose.Words, how to **convert docx to pdf** while controlling shape export, and why the `export_floating_shapes_as_inline_tag` flag is the key to reliable layout preservation. This approach works for the **convert word to pdf** scenario, supports batch processing, and gives you the flexibility to adjust shape handling per document.

Next, explore related topics such as **adding watermarks to PDFs**, **compressing PDF output**, or **converting DOCX to other formats** like HTML or EPUB. Each of those features builds on the same `aw.Document` object model you used here, so you can extend your automation pipeline with confidence.

Happy coding, and enjoy the seamless PDF results!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to save docx as pdf with Aspose.Words in Python](/words/english/python-net/document-conversion/how-to-save-docx-as-pdf-with-aspose-words-in-python/)
- [Save Word as PDF in C# – Full Guide to Convert DOCX to PDF with Shape Export](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [Save docx as pdf & detect missing fonts using Aspose.Words](/words/english/net/working-with-fonts/save-docx-as-pdf-detect-missing-fonts-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}