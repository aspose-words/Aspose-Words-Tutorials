---
category: general
date: 2026-05-30
description: Save Word as PDF with shape tagging in Python. Convert docx to pdf, make
  pdf accessible, and learn how to tag floating shapes for better accessibility.
draft: false
keywords:
- save word as pdf
- convert docx to pdf
- convert word document pdf
- make pdf accessible
- how to tag shapes
language: en
og_description: Save Word as PDF using Python and tag floating shapes for accessibility.
  Learn to convert docx to pdf and make pdf accessible in minutes.
og_title: Save Word as PDF with Shape Tagging – Full Python Guide
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Save Word as PDF with shape tagging in Python. Convert docx to pdf,
    make pdf accessible, and learn how to tag floating shapes for better accessibility.
  headline: Save Word as PDF with Shape Tagging – Full Python Guide
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for Python via .NET runs on .NET Core, which is cross‑platform.
      Just install the appropriate runtime (`dotnet-sdk-6.0` or later) and the `aspose-words`
      package.
    question: Does this work on Linux?
  - answer: Absolutely. Wrap the `convert_word_to_accessible_pdf` call in a `for`
      loop that iterates over `os.listdir()` and filters for `*.docx`.
    question: Can I batch‑process a folder of .docx files?
  - answer: Iterate over `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and set `shape.title`
      or `shape.alternative_text` before saving.
    question: What if I need to add custom alt text to each shape?
  - answer: 'The inline tagging respects the original layout; however, if you enable
      PDF/A compliance, some visual tweaks (like color profiles) might be applied
      automatically. ## Wrapping Up We’ve just covered how to **save Word as PDF**
      while ensuring that floating shapes are tagged correctly for accessibility.'
    question: Is there a way to keep the original layout exactly the same?
  type: FAQPage
tags:
- Aspose.Words
- PDF conversion
- Python
- Document automation
title: Save Word as PDF with Shape Tagging – Full Python Guide
url: /python/document-conversion/save-word-as-pdf-with-shape-tagging-full-python-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save Word as PDF with Shape Tagging – Full Python Guide

Ever wondered how to **save Word as PDF** while keeping those floating shapes accessible? You're not the only one. In many compliance‑heavy environments, a plain PDF isn’t enough—screen readers need proper tags, especially for shapes that hover over text.  

In this tutorial we’ll walk through a complete, runnable example that shows you how to **convert docx to pdf**, configure the PDF options so the output is both visually correct *and* accessible, and finally tag the shapes the right way. By the end you’ll have a one‑file solution you can drop into any Python project.

## What You’ll Learn

- Load a Word document that contains floating shapes (pictures, text boxes, diagrams).  
- Use Aspose.Words for Python via .NET to **convert Word document pdf** with custom tagging.  
- Enable the *inline* tagging mode so the PDF meets accessibility standards.  
- Verify the result and handle common pitfalls like missing fonts or oversized images.  

No external services, no obscure command‑line tricks—just plain Python code and a few explanatory notes.

## Prerequisites

Before we dive in, make sure you have:

| Requirement | Reason |
|-------------|--------|
| Python 3.9+ | Required by the Aspose .Words for Python via .NET package. |
| `aspose-words` NuGet package installed (via `pip install aspose-words`) | Provides the `aw` namespace used in the sample. |
| A `.docx` file with at least one floating shape (e.g., a text box) | Demonstrates the tagging feature. |
| Optional: PDF/A‑1a validator (e.g., veraPDF) if you need to certify accessibility. | Helps you confirm the PDF is truly accessible. |

If you’ve never used Aspose.Words before, think of it as the “Swiss army knife” for document manipulation—much more powerful than the built‑in `python-docx` library, especially when you need PDF output with fine‑grained control.

## Step 1: Install and Import Aspose.Words

First things first—install the library and import the necessary classes. This step is short, but skipping it will leave you staring at an `ImportError` later on.

```bash
pip install aspose-words
```

```python
# Step 1: Import the Aspose.Words namespace
import aspose.words as aw
```

> **Pro tip:** If you’re working in a virtual environment, activate it before running the `pip` command. That way you keep your project dependencies tidy.

## Step 2: Load the Word Document That Contains Floating Shapes

Now we actually open the source file. The `Document` constructor accepts a path or a stream, so you can feed it anything from a local file to an S3 object.

```python
# Step 2: Load the source .docx
input_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(input_path)
```

> **Why this matters:** Loading the document gives us access to its internal node tree, where floating shapes are represented as `Shape` objects. If the file doesn’t exist, Aspose will raise a `FileNotFoundError`, which you can catch and handle gracefully.

## Step 3: Configure PDF Save Options for Accessible Shape Tagging

Here’s the heart of the tutorial. By default Aspose.Words saves floating shapes as *block‑level* tags, which many assistive technologies treat as separate, non‑reading order elements. Setting `export_floating_shapes_as_inline_tag` to `True` forces the shapes to be tagged *inline*, preserving reading order and improving screen‑reader experience.

```python
# Step 3: Create PDF save options and enable inline shape tagging
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True   # True → inline (accessible) tagging
```

> **How it works:** When `export_floating_shapes_as_inline_tag` is `True`, Aspose injects `<Figure>` tags around each shape and places them in the document flow. This is the recommended approach for **make pdf accessible** compliance, especially under WCAG 2.1 Guideline 1.3.1.

### Optional Tweaks

| Option | Description | Typical Value |
|--------|-------------|---------------|
| `pdf_opts.compliance` | Sets PDF/A compliance level (e.g., PDF/A‑1a). | `aw.saving.PdfCompliance.PDF_A_1A` |
| `pdf_opts.embed_full_fonts` | Embeds all used fonts to avoid substitution. | `True` |
| `pdf_opts.save_format` | Forces the output format (useful if you later switch to XPS). | `aw.SaveFormat.PDF` |

You can chain these settings if your project has stricter requirements.

## Step 4: Save the Document as PDF Using the Configured Options

Finally, we write the output file. The `save` method takes the destination path and the options object we just configured.

```python
# Step 4: Save the document as a PDF with the accessible tagging options
output_path = "YOUR_DIRECTORY/output.pdf"
doc.save(output_path, pdf_opts)
print(f"✅ PDF saved to {output_path}")
```

That’s it—your **convert word document pdf** operation is complete. The resulting PDF will have floating shapes tagged inline, making it much friendlier for assistive technologies.

## Verifying the Accessible PDF

If you want to be extra sure that the PDF truly meets accessibility standards, open it in Adobe Acrobat Pro and check the **Tags** panel. You should see entries like:

```
/Figure
  /Alt (optional alt text you may have set)
  /Para
```

Alternatively, run a command‑line validator:

```bash
verapdf --format text output.pdf
```

If the validator returns “No errors,” you’ve successfully **make pdf accessible**.

## Common Edge Cases & How to Handle Them

| Situation | What Might Go Wrong | Suggested Fix |
|-----------|---------------------|---------------|
| **Document contains many high‑resolution images** | PDF size balloons, performance degrades. | Set `pdf_opts.jpeg_quality = 80` or downscale images with `doc.get_child_nodes(aw.NodeType.SHAPE, True)` before saving. |
| **Missing fonts on the server** | Text appears with fallback fonts, breaking layout. | Enable `pdf_opts.embed_full_fonts = True` and ensure the required fonts are installed on the host OS. |
| **Shapes have no alt text** | Accessibility tools read “Figure” with no description. | Iterate over shapes and assign `shape.title = "Description"` before saving. |
| **Large documents (>100 MB)** | Out‑of‑memory errors on 32‑bit runtimes. | Use `PdfSaveOptions.memory_usage_setting = aw.saving.MemoryUsageSetting.LOW` to stream content. |
| **You need PDF/A‑2b instead of PDF/A‑1a** | Compliance mismatch. | Set `pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_2B`. |

Handling these scenarios early saves you from re‑working the conversion later on.

## Full Working Example

Below is the complete script you can copy‑paste into a file named `convert_to_accessible_pdf.py`. Just replace `YOUR_DIRECTORY` with the actual folder paths.

```python
import aspose.words as aw

def convert_word_to_accessible_pdf(input_docx: str, output_pdf: str) -> None:
    """
    Loads a Word document, configures PDF save options to tag floating shapes inline,
    and saves the result as an accessible PDF.
    """
    # Load the .docx file
    doc = aw.Document(input_docx)

    # Configure PDF options for accessible shape tagging
    pdf_opts = aw.saving.PdfSaveOptions()
    pdf_opts.export_floating_shapes_as_inline_tag = True   # Inline tagging for accessibility
    pdf_opts.compliance = aw.saving.PdfCompliance.PDF_A_1A  # Optional: enforce PDF/A‑1a
    pdf_opts.embed_full_fonts = True                       # Ensure fonts are embedded

    # Save the PDF
    doc.save(output_pdf, pdf_opts)
    print(f"✅ Successfully saved accessible PDF to: {output_pdf}")

if __name__ == "__main__":
    # Adjust these paths as needed
    INPUT_PATH = "YOUR_DIRECTORY/input.docx"
    OUTPUT_PATH = "YOUR_DIRECTORY/output.pdf"

    convert_word_to_accessible_pdf(INPUT_PATH, OUTPUT_PATH)
```

Running the script:

```bash
python convert_to_accessible_pdf.py
```

You should see the confirmation message, and the `output.pdf` will contain inline‑tagged shapes ready for screen readers.

## Frequently Asked Questions

**Q: Does this work on Linux?**  
A: Yes. Aspose.Words for Python via .NET runs on .NET Core, which is cross‑platform. Just install the appropriate runtime (`dotnet-sdk-6.0` or later) and the `aspose-words` package.

**Q: Can I batch‑process a folder of .docx files?**  
A: Absolutely. Wrap the `convert_word_to_accessible_pdf` call in a `for` loop that iterates over `os.listdir()` and filters for `*.docx`.

**Q: What if I need to add custom alt text to each shape?**  
A: Iterate over `doc.get_child_nodes(aw.NodeType.SHAPE, True)` and set `shape.title` or `shape.alternative_text` before saving.

**Q: Is there a way to keep the original layout exactly the same?**  
A: The inline tagging respects the original layout; however, if you enable PDF/A compliance, some visual tweaks (like color profiles) might be applied automatically.

## Wrapping Up

We’ve just covered how to **save Word as PDF** while ensuring that floating shapes are tagged correctly for accessibility. The steps—load, configure, save—


## What Should You Learn Next?

- [Create Accessible PDF from Word – Convert to PDF/UA](/words/english/java/document-conversion-and-export/create-accessible-pdf-from-word-convert-to-pdf-ua/)
- [Save Word as PDF with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}