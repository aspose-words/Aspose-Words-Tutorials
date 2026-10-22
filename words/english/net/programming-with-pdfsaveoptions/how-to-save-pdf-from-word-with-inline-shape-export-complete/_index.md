---
category: general
date: 2026-06-02
description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
  span tags, and convert Word to PDF in just a few steps.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: en
og_description: How to save PDF from a Word document using Aspose.Words, exporting
  floating shapes as inline span tags for a clean convert Word to PDF result.
og_title: How to Save PDF from Word – Inline Shape Export Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: How to Save PDF from Word with Inline Shape Export – Complete Guide
url: /net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Save PDF from Word with Inline Shape Export – Complete Guide

Ever wondered **how to save PDF** from a Word file while keeping every floating shape tucked neatly into the flow? You're not the only one. In many enterprise apps we need to *convert Word to PDF* without ending up with misplaced images or stray drawing objects. The good news? Aspose.Words makes it painless, and you can even tell the library to **export shapes as inline `<span>` tags** so the PDF looks just like the original DOCX.

In this tutorial we’ll walk through the entire process—loading a DOCX, tweaking the `PdfSaveOptions`, and finally saving a clean PDF. By the end you’ll know **how to save PDF**, **save docx as pdf**, and even **how to export shapes** using *inline span tags*.

## What You’ll Need

- **Aspose.Words for .NET** (latest version, 24.x at the time of writing).  
- **.NET 6.0** or later – the code works on .NET Framework 4.7.2 as well, but .NET 6 is the sweet spot.  
- A simple Word document that contains at least one floating shape (image, text box, or drawing).  
- Any IDE you like (Visual Studio, Rider, VS Code + C# extension).  

That’s it—no extra NuGet packages, no fiddly COM interop. Ready? Let’s dive in.

## Step 1: Set Up the Project and Add Aspose.Words

First, create a console app (or integrate the code into your existing service).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Pro tip:** If you’re using Visual Studio, you can add the package via the NuGet Package Manager UI—just search for *Aspose.Words*.

## Step 2: Load the Source Document

Now that the library is referenced, we can load the DOCX. This is the **how to save pdf** part’s first concrete action—getting the source into memory.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Why this matters:** Loading the file validates that the path is correct and that Aspose can parse the Word structure. If the file contains floating shapes, they’ll be part of the `Document` object’s node tree.

## Step 3: Configure PDF Save Options – Export Shapes as Inline Tags

Here’s the heart of **how to export shapes**. By default Aspose.Words renders floating shapes as separate objects in the PDF, which can shift layout. Setting `ExportFloatingShapesAsInlineTag` to `true` tells the engine to wrap each shape in an inline `<span>` element, preserving the flow.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Why enable this flag?** Imagine a contract with a signature box that floats over text. When you convert it to PDF without this setting, the box may appear on a different page. Inline `<span>` tags keep the shape anchored to its surrounding paragraph, producing a faithful visual replica.

## Step 4: Save the Document as PDF

Finally, we call `doc.Save` with the options we just built. This is the moment you actually **save docx as pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Run the program (`dotnet run`) and check the `output.pdf`. You should see your floating shapes rendered inline, just as they appeared in Word.

## Step 5: Verify the Result – Quick Checklist

1. **All text is present** – no missing paragraphs.  
2. **Floating shapes appear where they should** – they’re now part of the text flow.  
3. **PDF size is reasonable** – exporting as inline tags usually reduces file bloat compared to separate image streams.  

If anything looks off, double‑check that the source DOCX really uses *floating* shapes (right‑click → Layout → “In line with text” vs “Square/Behind text”). Switching a shape to “In line” before conversion also works, but the inline‑tag option gives you control without editing the original file.

## Edge Cases & Common Questions

### What if my document contains **SmartArt** or **Charts**?

SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag` flag will still wrap them in `<span>` tags, but complex graphics may lose some fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`) and then inserting it inline.

### Can I **preserve hyperlinks** and **bookmarks**?

Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag` setting. Aspose.Words retains all hyperlink and bookmark information automatically.

### How do I **change PDF compression** or **embed fonts**?

`PdfSaveOptions` offers many additional properties:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

Feel free to tweak those settings based on your downstream requirements (e.g., PDF/A compliance).

## Full Working Example (Copy‑Paste Ready)

Below is the complete program you can copy into `Program.cs`. Replace `YOUR_DIRECTORY` with an actual folder path.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Expected output in the console:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Open `output.pdf`—you’ll see the original layout, with every floating shape snugly placed inside the text flow.

## Conclusion

We’ve covered **how to save PDF** from a Word document while ensuring that floating shapes become inline `<span>` tags. By loading the DOCX, configuring `PdfSaveOptions`, and invoking `doc.Save`, you can reliably **save docx as pdf** and **convert word to pdf** without layout surprises.  

Next steps? Try combining this approach with **PDF/A** compliance for archival, or batch‑process a folder of DOCX files with a simple `foreach` loop. You might also explore **custom rendering** (e.g., adding watermarks) by tapping into Aspose.Words’ `DocumentVisitor` API.

Got more questions about shape handling, font embedding, or performance tuning? Drop a comment below, and happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Convert DOCX to PDF in Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}