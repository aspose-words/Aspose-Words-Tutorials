---
category: general
date: 2026-08-04
description: Recover corrupted docx files using Aspose.Words recovery mode and convert
  docx to markdown, exporting equations as LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: en
lastmod: 2026-08-04
og_description: Recover corrupted docx files with Aspose.Words recovery mode, then
  convert docx to markdown while exporting equations as LaTeX. Follow this step‑by‑step
  guide to also create PDF and TXT outputs.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: Recover corrupted docx and convert to markdown – Aspose guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: Recover corrupted docx and convert to markdown with Aspose
url: /python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recover corrupted docx and convert to markdown with Aspose

If you need to **recover corrupted docx** files, Aspose.Words provides a built‑in recovery mode that can automatically repair damaged Word documents. Once the file is restored you can **convert docx to markdown**, and even **export equations latex** for seamless use in scientific documents. This tutorial shows you exactly how to do that in Python, plus a few extra options for PDF and plain‑text output.

You’ll learn how to:

* Load a potentially broken DOCX using the recovery mode.  
* Save the recovered document as Markdown with LaTeX‑formatted equations.  
* Generate a plain‑text (TXT) version that also contains LaTeX equations.  
* Export to PDF while tagging floating shapes as inline elements.  
* Adjust a shape’s shadow and produce a final PDF.

No external tools are required—just the free Aspose.Words for Python library.

## Prerequisites

| Requirement | Why it matters |
|-------------|----------------|
| Python 3.8+ | Required by Aspose.Words for Python |
| `aspose-words` package (`pip install aspose-words`) | Provides the `aw` namespace used in the code |
| A DOCX file that may be damaged (e.g., `corrupted.docx`) | Demonstrates the recovery workflow |
| Write permission to the output directory | The script writes several files (`.md`, `.txt`, `.pdf`) |

Make sure the Aspose.Words license (free trial or purchased) is correctly configured if you exceed the evaluation limits.

## Recover corrupted docx using Aspose.Words

The first step is to tell Aspose.Words to treat the input file as potentially broken. This is done with `LoadOptions.recovery_mode`.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Why this works:**  
`RecoveryMode.RECOVER` forces the loader to ignore structural errors and attempt to rebuild the document tree. If the file is only partially damaged, most content—including text, images, and equations—will be restored.

**Tip:** If you only want to validate a document without repairing it, use `RecoveryMode.NO_RECOVERY`. For full recovery, keep the setting as shown.

## Convert docx to markdown with LaTeX equations

Once the document is in memory, you can save it as Markdown. Setting `office_math_export_mode` to `LATEX` tells Aspose.Words to render each Word equation as a LaTeX string.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

The resulting `output.md` will look like a regular Markdown file, but every equation appears as `$...$` (inline) or `$$...$$` (display) LaTeX code. This is essential for downstream tools like Pandoc or Jupyter notebooks that understand LaTeX syntax.

## How to use recovery mode for damaged files

The recovery mode can be reused for any loading operation. Below is a compact pattern you can copy into other scripts:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

Calling `load_with_recovery("myfile.docx")` returns a `Document` object that Aspose.Words has already attempted to fix. This function embodies **how to use recovery mode** safely across projects.

## Export equations latex when saving to markdown and txt

If you also need a plain‑text version, the same `office_math_export_mode` flag works with `TxtSaveOptions`.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

The `.txt` file contains the raw text of the Word document, and every equation is represented as LaTeX code. This format is handy for indexing or feeding the content into search engines that understand LaTeX.

## Additional options: PDF with inline shapes and shape shadow

### Export floating shapes as inline tags

Floating images or text boxes can cause layout issues when converting to PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat those shapes as regular inline elements, preserving the visual flow.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### Adjust the shadow of the first shape

You might want to enhance the appearance of a specific shape before saving the final PDF. The code below accesses the first `Shape` node, enables its shadow, and tweaks visual parameters.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**Result:** `shadowed.pdf` looks identical to `output.pdf` but the first shape now casts a subtle black shadow, which can improve readability in presentations.

## Complete runnable script

Below is the full script that combines all of the steps. Copy it into a file called `recover_and_convert.py`, replace `YOUR_DIRECTORY` with an actual path, and run `python recover_and_convert.py`.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### Expected output

| File | Description |
|------|-------------|
| `output.md` | Markdown version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`). |
| `output.txt` | Plain‑text dump


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to Use Markdown: Convert DOCX to Markdown with LaTeX Equations](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [how to recover docx with Aspose.Words – step by step](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Recover Corrupted DOCX & Convert Word to Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}