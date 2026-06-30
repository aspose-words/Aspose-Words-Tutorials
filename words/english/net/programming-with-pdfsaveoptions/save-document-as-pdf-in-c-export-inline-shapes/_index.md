---
category: general
date: 2026-06-30
description: Save document as PDF in C# while converting docx to PDF and handling
  inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
draft: false
keywords:
- save document as pdf
- convert docx to pdf
- convert word to pdf
- save word as pdf
- how to export inline
language: en
og_description: Save document as PDF in C# with Aspose.Words. Learn how to convert
  docx to PDF and export floating shapes as inline elements.
og_title: Save Document as PDF in C# – Export Inline Shapes
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  headline: Save Document as PDF in C# – Export Inline Shapes
  type: TechArticle
- description: Save document as PDF in C# while converting docx to PDF and handling
    inline shapes. Follow this step‑by‑step guide to export Word to PDF correctly.
  name: Save Document as PDF in C# – Export Inline Shapes
  steps:
  - name: '**.NET 6+** (or .NET Framework 4.6+).'
    text: '**.NET 6+** (or .NET Framework 4.6+).'
  - name: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
    text: The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).
  - name: A sample `input.docx` that contains at least one floating picture or text
      box.
    text: A sample `input.docx` that contains at least one floating picture or text
      box.
  type: HowTo
tags:
- C#
- PDF
- Aspose.Words
title: Save Document as PDF in C# – Export Inline Shapes
url: /net/programming-with-pdfsaveoptions/save-document-as-pdf-in-c-export-inline-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save Document as PDF in C# – Export Inline Shapes

Ever wondered how to **save document as PDF** directly from C# without losing the layout of floating images? You're not the only one. Many developers hit a snag when a Word file contains pictures or text boxes that float above the text—those elements often disappear or shift when you simply call `doc.Save("output.pdf")`.  

In this tutorial we’ll walk through the exact steps to **convert docx to pdf** while preserving those floating objects as inline elements, effectively answering *how to export inline* shapes. By the end you’ll have a ready‑to‑run snippet that **save word as pdf** the way you expect.

## What You’ll Learn

- Load a `.docx` file with Aspose.Words (or any compatible library).  
- Configure `PdfSaveOptions` so that floating shapes become inline.  
- Execute the save operation to **convert word to pdf**.  
- Handle common pitfalls such as missing fonts or large images.  

No external tools, no manual fiddling with Word‑automation COM objects—just clean, pure C# code.

---

## Prerequisites

Before we dive in, make sure you have:

1. **.NET 6+** (or .NET Framework 4.6+).  
2. The **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`).  
3. A sample `input.docx` that contains at least one floating picture or text box.  

If you’re using a different PDF library, the concepts stay the same—look for a property similar to `ExportFloatingShapesAsInlineTag`.

---

## Step 1: Load the Source Document – Save Document as PDF Basics  

The very first thing is to bring the Word file into memory. This is where the **save document as pdf** process actually begins.

```csharp
using Aspose.Words;

// Step 1: Load the source DOCX file
string inputPath = @"C:\MyDocs\input.docx";
Document doc = new Document(inputPath);
```

*Why this matters*: Loading the document validates that the file exists and parses all its parts (styles, images, headers). If the load fails, the later PDF conversion will never run, so catching errors here saves you a lot of debugging time.

---

## Step 2: Configure PDF Save Options – How to Export Inline Shapes  

Now we tell the library how to treat floating shapes. The key flag is `ExportFloatingShapesAsInlineTag`. Setting it to `true` forces every floating picture or text box to be rendered **inline**, just like a regular paragraph run.

```csharp
// Step 2: Prepare PDF save options
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    // true → inline (text‑flow); false → keep as block‑level floating objects
    ExportFloatingShapesAsInlineTag = true,

    // Optional: improve compatibility with older PDF viewers
    Compliance = PdfCompliance.PdfA1b
};
```

*Why this matters*: By default, Aspose.Words keeps floating shapes at their original position, which can cause them to be clipped or dropped in the resulting PDF. Enabling the inline export ensures the shapes become part of the text flow, preserving visual fidelity across all PDF readers.

---

## Step 3: Save the Document as PDF – Convert Word to PDF  

With the document loaded and options set, the final step is a one‑liner that actually **save document as pdf**.

```csharp
// Step 3: Save the document as a PDF file
string outputPath = @"C:\MyDocs\FloatingShapes.pdf";
doc.Save(outputPath, pdfOptions);
```

That’s it! The `doc.Save` call writes a PDF that mirrors the original Word layout, with floating images now sitting neatly within the text.

---

## Full Working Example  

Putting everything together, here’s a self‑contained console app you can copy‑paste, compile, and run:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToPdfInlineExport
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\MyDocs\input.docx";
            string outputPath = @"C:\MyDocs\FloatingShapes.pdf";

            // Load the DOCX file
            Document doc = new Document(inputPath);

            // Configure PDF options to export floating shapes as inline
            PdfSaveOptions pdfOptions = new PdfSaveOptions
            {
                ExportFloatingShapesAsInlineTag = true,
                Compliance = PdfCompliance.PdfA1b // optional, ensures PDF/A‑1b compliance
            };

            // Save as PDF
            doc.Save(outputPath, pdfOptions);

            Console.WriteLine($"Document successfully saved as PDF: {outputPath}");
        }
    }
}
```

**Expected output** (in the console):

```
Document successfully saved as PDF: C:\MyDocs\FloatingShapes.pdf
```

Open `FloatingShapes.pdf` in any viewer; you’ll see the previously floating picture now snugly embedded within the paragraph, just as intended.

---

## Why Export Floating Shapes as Inline?  

Floating shapes are great in Word because they let you position images anywhere on the page. However, PDF is a *page‑oriented* format—there’s no concept of “float” the same way Word has. When the conversion engine leaves them as block‑level objects, they can:

- Overlap other content.  
- Get cut off at page margins.  
- Disappear entirely in older PDF readers.

By converting them to **inline** elements, you guarantee that the PDF respects the reading order and that screen readers can interpret the document correctly—important for accessibility compliance.

---

## Common Pitfalls When Converting Docx to PDF  

| Issue | Symptom | Fix |
|-------|---------|-----|
| Missing fonts | Text appears as “□” or defaults to Arial | Embed fonts via `PdfSaveOptions.FontEmbeddingMode = FontEmbeddingMode.Always`. |
| Large images cause memory spikes | Out‑of‑memory exception on big DOCX | Downscale images before conversion or set `PdfSaveOptions.ImageCompression = PdfImageCompression.Jpeg;` |
| Inline export not applied | Floating shapes still float in PDF | Verify you’re using the latest Aspose.Words version; the property name changed in older releases. |
| Path errors | `FileNotFoundException` | Use `Path.Combine` and ensure the directory exists (`Directory.CreateDirectory`). |

---

## Advanced: Exporting Only Specific Shapes Inline  

Sometimes you want *selective* inline conversion—only certain pictures, not all. You can achieve this by iterating the document nodes before saving:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.WrapType == WrapType.Inline)
        continue; // already inline

    // Example condition: only convert pictures larger than 300px
    if (shape.HasImage && shape.Width > 300)
        shape.WrapType = WrapType.Inline;
}
```

After adjusting the `WrapType`, run the same `doc.Save` call. This gives you fine‑grained control over the **how to export inline** behavior.

---

## Pro Tips & Best Practices  

- **Pro tip:** Set `pdfOptions.Compliance = PdfCompliance.PdfA1b` if your organization requires PDF/A for archiving.  
- **Watch out for:** Hidden sections (`SectionBreakContinuous`) that might hide floating shapes; run `doc.UpdatePageLayout()` before saving.  
- **Performance tip:** Reuse a single `PdfSaveOptions` instance if you’re converting many files in a batch; it reduces allocation overhead.  
- **Testing:** Always open the resulting PDF in at least two viewers (Adobe Reader, Edge) to verify layout consistency.

---

## Visual Overview  

![Save document as PDF flowchart showing load → configure → save steps](https://example.com/flowchart.png "Save document as PDF flowchart")

*Alt text:* **Save document as PDF flowchart** – illustrates the three‑step process of loading a DOCX, configuring inline export, and saving as PDF.

---

## Conclusion  

You now have a solid, production‑ready method to **save document as PDF** in C# while handling floating objects the right way. By configuring `ExportFloatingShapesAsInlineTag`, you ensure that every picture, chart, or text box becomes part of the text flow, eliminating the typical glitches that plague a naïve **convert word to pdf** approach.  

Give it a spin: try converting a complex report with multiple floating images, then experiment with the selective inline logic to keep some shapes floating where they belong. The next time you need to **convert docx to pdf**, you’ll know exactly how to preserve every visual element.

Feel free to drop a comment if you hit any snags or discover a clever shortcut. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [save docx as pdf with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)
- [Save Word as PDF with Aspose.Words – Complete C# Guide](/words/english/net/basic-conversions/save-word-as-pdf-with-aspose-words-complete-c-guide/)
- [convert word to pdf in C# using Aspose.Words – Guide](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}