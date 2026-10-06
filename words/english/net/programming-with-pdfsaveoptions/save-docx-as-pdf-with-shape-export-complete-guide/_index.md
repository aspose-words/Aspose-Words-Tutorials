---
category: general
date: 2026-02-13
description: Save docx as pdf while preserving floating shapes. Learn how to convert
  word to pdf, export shapes, and handle edge cases in C#.
draft: false
keywords:
- save docx as pdf
- convert word to pdf
- how to export shapes
- convert word document pdf
- how to convert docx pdf
language: en
og_description: Save docx as pdf while preserving floating shapes. This guide shows
  how to convert word to pdf, export shapes, and handle common pitfalls.
og_title: Save docx as pdf with Shape Export – Complete Guide
tags:
- Aspose.Words
- C#
- PDF conversion
title: Save docx as pdf with Shape Export – Complete Guide
url: /net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-shape-export-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save docx as pdf – Full‑stack Tutorial (C#)

Ever needed to **save docx as pdf** and keep those floating diagrams looking exactly the same? You’re not alone. Many developers hit a wall when Word’s shapes disappear or get mangled after conversion. The good news? With a few lines of C# you can tell the library to treat every shape as a block‑level element, and the result is a faithful PDF replica.

In this guide we’ll walk through the whole process: loading a `.docx` file, configuring the **convert word to pdf** options so that shapes are exported correctly, and finally writing the PDF to disk. By the end you’ll know **how to export shapes**, understand the trade‑offs of different export modes, and have a ready‑to‑run code sample you can drop into any .NET project.

> **What you’ll get:** a complete, runnable example, explanations of *why* each setting matters, tips for edge cases, and ideas for extending the solution (e.g., handling images, custom fonts, or password‑protected PDFs).

---

## Prerequisites

- .NET 6+ (or .NET Framework 4.7+). The API we use works on both.
- Aspose.Words for .NET (free trial or licensed version). Install via NuGet: `Install-Package Aspose.Words`.
- A Word document (`input.docx`) that contains floating shapes (text boxes, auto‑shapes, SmartArt, etc.).
- Visual Studio 2022 or any IDE you prefer.

No other third‑party libraries are required.

---

## Step‑by‑Step Implementation

Below each step you’ll see a short code snippet, a plain‑English explanation, and a note on **how to export shapes** correctly.

### ## Step 1 – Load the source document (save docx as pdf)

```csharp
// Step 1: Load the source document
// This is the starting point for any conversion – you must have a Document object.
Document doc = new Document(@"C:\MyFolder\input.docx");
```

*Why this matters:* The `Document` class represents the entire Word file in memory. If you skip this step, there’s nothing to convert, and the subsequent PDF options have nothing to act upon.

### ## Step 2 – Configure PDF save options (how to export shapes)

```csharp
// Step 2: Configure PDF save options to export floating shapes as block‑level tags
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // ExportFloatingShapesAsInlineTag determines how shapes are rendered in PDF.
    // Setting it to Block ensures each shape gets its own block, preserving layout.
    ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block
};
```

**Explanation**

- `PdfSaveOptions` is a “bag of settings” that tells Aspose.Words how to translate Word constructs into PDF.
- The **ExportFloatingShapesAsInlineTag** property has three possible values:
  1. **Inline** – shapes become inline elements (often squashed into surrounding text).
  2. **Block** – each shape is placed on its own block, which is the safest way to keep the original appearance.
  3. **Auto** – the library decides automatically (may not always pick the best option).

Choosing **Block** is the recommended approach when you *need to export shapes* exactly as they appear in the original document. It prevents the “shape disappears” problem that many encounter when simply calling `doc.Save("out.pdf")`.

### ## Step 3 – Save the document as PDF (convert word to pdf)

```csharp
// Step 3: Save the document as PDF using the configured options
doc.Save(@"C:\MyFolder\FloatingShapes.pdf", pdfSaveOptions);
```

*What you’ll see:* After this line runs, `FloatingShapes.pdf` sits in `C:\MyFolder`. Open it, and you should see every text box, callout, and SmartArt positioned just like in the source `.docx`.

---

## Full Working Example

Below is the **complete program** you can compile and run as a console app. It includes all necessary `using` statements and comments for clarity.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the DOCX file you want to convert.
        // Replace the path with your own file location.
        Document doc = new Document(@"C:\MyFolder\input.docx");

        // 2️⃣ Set up PDF options – this is where we tell Aspose.Words
        //    how to handle floating shapes.
        PdfSaveOptions pdfOptions = new PdfSaveOptions
        {
            // ExportFloatingShapesAsInlineTag = Block makes each shape a separate block.
            ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Block,

            // Optional: preserve the original page size.
            PageMode = PdfPageMode.UseOutlines,

            // Optional: embed fonts to avoid missing‑glyph issues.
            EmbedFullFonts = true
        };

        // 3️⃣ Write the PDF to disk.
        string outPath = @"C:\MyFolder\FloatingShapes.pdf";
        doc.Save(outPath, pdfOptions);

        Console.WriteLine($"Successfully saved DOCX as PDF: {outPath}");
    }
}
```

**Expected output**

```
Successfully saved DOCX as PDF: C:\MyFolder\FloatingShapes.pdf
```

Open the resulting PDF and verify that all shapes retain their original positions. If any shape still looks off, double‑check that it truly is a *floating* shape (versus an inline picture) in Word.

---

## Frequently Asked Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **Can I export shapes as inline instead of block?** | Yes – set `ExportFloatingShapesAsInlineTag = ExportFloatingShapesAsInlineTag.Inline`. This may be useful for simple layouts, but expect tighter text flow and possible overlap. |
| **What if my document contains images inside shapes?** | The same option works; Aspose.Words rasterizes the shape together with its image. For highest fidelity, also enable `PdfSaveOptions.JpegQuality` if you need better image compression. |
| **Does this work with password‑protected DOCX files?** | Load the document with a `LoadOptions` object that supplies the password, then proceed as normal. |
| **Can I convert multiple DOCX files in a batch?** | Wrap the three‑step logic in a `foreach` loop over a file list. Remember to reuse `PdfSaveOptions` for performance. |
| **Is the PDF compatible with older readers (Acrobat 7)?** | By default Aspose.Words creates PDF 1.7 files. Set `pdfOptions.Compliance = PdfCompliance.PdfA1b` for archival‑grade PDFs that work on legacy readers. |

---

## Pro Tips & Common Pitfalls

- **Pro tip:** If you notice slight vertical shifts after conversion, try setting `pdfOptions.UsePdfDocumentStructure = true`. This forces the PDF engine to respect the Word layout hierarchy.
- **Watch out for:** Documents that mix floating shapes with anchored tables. In some cases, the block export may push a table onto a new page; you can mitigate this by adjusting `pdfOptions.PageSetup` before saving.
- **Performance note:** Reusing a single `PdfSaveOptions` instance for many files reduces GC pressure and speeds up batch conversions.

---

## Visual Reference

Below is a schematic screenshot (placeholder) showing the before/after of a document with a floating text box.

![save docx as pdf example with floating shapes](image-placeholder.png "save docx as pdf example with floating shapes")

*The image illustrates how the shape stays exactly where it was in the original Word file after conversion.*

---

## Wrap‑Up

We’ve covered **how to save docx as pdf** while keeping every floating shape intact, explored the **convert word to pdf** settings that matter, and answered the most common “**how to export shapes**” questions. The complete code sample is ready to drop into any C# project, and the optional tweaks give you flexibility for real‑world scenarios like batch processing or PDF/A compliance.

### Next Steps

- Try **convert word document pdf** with different compliance levels (`PdfCompliance.PdfA2b`, `PdfCompliance.PdfUa`) to meet regulatory requirements.
- Experiment with **how to convert docx pdf** for password‑protected files—add `LoadOptions` with a password and `PdfSaveOptions` with `EncryptionDetails`.
- Explore other output formats (e.g., XPS, HTML) using the same `Document` object; the only change is the `Save` method’s format argument.

Got more questions? Drop a comment, and happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}