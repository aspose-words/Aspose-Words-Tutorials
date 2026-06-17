---
category: general
date: 2026-06-02
description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
  tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
draft: false
keywords:
- create pdf/ua-2 compliant document
- Aspose.Words PDF/UA
- C# document conversion
- PDF accessibility
- PdfSaveOptions
language: en
og_description: Learn how to create pdf/ua-2 compliant document using Aspose.Words
  for .NET. Full code, compliance tips, and PDF accessibility explained.
og_title: Create pdf/ua-2 compliant document – Complete C# Guide
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  headline: Create pdf/ua-2 compliant document – Complete C# Guide
  type: TechArticle
- description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  name: Create pdf/ua-2 compliant document – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Core, .NET Framework 4.7+,
      and .NET 5+). - A licensed copy of **Aspose.Words for .NET** (the free trial
      works for testing). - Basic familiarity with C# and Visual Studio (or your favourite
      IDE).'
  - name: Why These Settings Matter
    text: '- **Compliance = PdfUa2** – This flag adds the *PDF/UA* metadata and logical
      structure tree. - **EmbedFullFonts** – PDF/UA requires that all glyphs used
      in the document are embedded, otherwise a screen reader might miss characters.
      - **ExportDocumentStructure** – Tags the PDF so assistive technologi'
  - name: Quick Validation with the PDF/UA Validator
    text: 1. Download the free **PDF/UA‑2 validator** from the PDF Association (search
      “PDF/UA validator”). 2. Drag `Doc_UA.pdf` onto the validator window. 3. The
      tool will report “No errors” if the document meets the standard.
  - name: Custom Fonts
    text: If your source uses a font that isn’t installed on the server, enable `FontEmbeddingMode
      = FontEmbeddingMode.Always` to force embedding.
  - name: Complex Tables
    text: PDF/UA‑2 requires that tables have proper structure. Ensure every table
      in the Word file has header rows defined (`Table Tools → Layout → Repeat Header
      Rows`). Aspose.Words respects this setting automatically.
  - name: Images Without Alt Text
    text: 'Screen readers rely on alternative text. If an image lacks alt text, Aspose.Words
      will insert an empty description, which may cause a compliance warning. Add
      alt text in Word (`Picture Tools → Alt Text`) or programmatically:'
  type: HowTo
tags:
- PDF
- C#
- Aspose.Words
- Accessibility
title: Create pdf/ua-2 compliant document – Complete C# Guide
url: /net/programming-with-pdfsaveoptions/create-pdf-ua-2-compliant-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create pdf/ua-2 compliant document – Complete C# Guide

Need to **create pdf/ua-2 compliant document** but aren’t sure where to start? In this tutorial we’ll walk you through how to create pdf/ua-2 compliant document with Aspose.Words for .NET, guaranteeing PDF accessibility and full PDF/UA‑2 compliance.  

If you’ve ever wrestled with accessibility requirements for PDFs, you’ll appreciate the simplicity of the approach we’ll cover. By the end, you’ll have a ready‑to‑use C# snippet, understand why each setting matters, and know how to verify that the output truly meets the PDF/UA‑2 standard.

## What You’ll Learn

- How to set up **Aspose.Words PDF/UA** support in a C# project.  
- The exact role of **PdfSaveOptions** when targeting PDF/UA‑2.  
- Tips for handling edge cases like custom fonts and complex tables.  
- A quick way to validate the generated file with free PDF/UA validators.  

### Prerequisites

- .NET 6.0 or later (the code works with .NET Core, .NET Framework 4.7+, and .NET 5+).  
- A licensed copy of **Aspose.Words for .NET** (the free trial works for testing).  
- Basic familiarity with C# and Visual Studio (or your favourite IDE).  

If you tick those boxes, let’s dive in—no extra tools required.

![create pdf/ua-2 compliant document example](images/pdf-ua2-example.png "create pdf/ua-2 compliant document example")

## Step 1: Install Aspose.Words and Add References  

First things first, you need the Aspose.Words library. Open a terminal in your project folder and run:

```bash
dotnet add package Aspose.Words
```

Alternatively, use the NuGet Package Manager in Visual Studio. This brings in the **Aspose.Words PDF/UA** capabilities, including the `PdfSaveOptions` class we’ll rely on later.  

> **Pro tip:** If you plan to ship the PDF generation feature to a client, add the license file (`Aspose.Words.lic`) to your project and call `License license = new License(); license.SetLicense("Aspose.Words.lic");` early in `Main()`—this removes the evaluation watermark.

## Step 2: Load the Source Document  

Our goal is to turn a Word file (`.docx`) into a PDF/UA‑2 compliant document. The source can be any Word document, but for a clean accessibility audit, start with a simple file that includes headings, alt‑text for images, and proper table structures.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class PdfUaGenerator
{
    static void Main()
    {
        // Load the source .docx file
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        
        // Proceed to configure PDF/UA‑2 options
        SaveAsPdfUa2(doc);
    }
}
```

Why load the document first? Aspose.Words parses the Word file into an object model, letting us inspect or modify content before conversion—useful if you need to inject accessibility tags later.

## Step 3: Configure PdfSaveOptions for PDF/UA‑2  

The **PdfSaveOptions** class is where the magic happens. Setting `Compliance = PdfCompliance.PdfUa2` tells Aspose.Words to embed the necessary tags, logical structure elements, and set the correct PDF version.

```csharp
static void SaveAsPdfUa2(Document doc)
{
    // Create a new PdfSaveOptions instance
    PdfSaveOptions pdfOptions = new PdfSaveOptions
    {
        // Enforce PDF/UA‑2 compliance
        Compliance = PdfCompliance.PdfUa2,

        // Optional but recommended: embed all fonts to avoid substitution issues
        EmbedFullFonts = true,

        // Ensure the document is tagged (required for PDF/UA)
        ExportDocumentStructure = true,

        // Preserve hyperlinks and bookmarks for better navigation
        ExportHyperlinks = true,
        ExportBookmarks = true
    };

    // Save the PDF/UA‑2 file
    doc.Save(@"YOUR_DIRECTORY\Doc_UA.pdf", pdfOptions);
}
```

### Why These Settings Matter  

- **Compliance = PdfUa2** – This flag adds the *PDF/UA* metadata and logical structure tree.  
- **EmbedFullFonts** – PDF/UA requires that all glyphs used in the document are embedded, otherwise a screen reader might miss characters.  
- **ExportDocumentStructure** – Tags the PDF so assistive technologies can interpret headings, paragraphs, and tables correctly.  
- **ExportHyperlinks / ExportBookmarks** – Improves navigation for users relying on keyboard shortcuts or screen‑reader shortcuts.

## Step 4: Run the Code and Verify the Output  

Build and run the project. If everything is wired correctly, you’ll find `Doc_UA.pdf` in the target folder. Open it in Adobe Acrobat Reader and check **File → Properties → Description** – you should see *PDF/UA‑2* listed under the “PDF/A” field.

### Quick Validation with the PDF/UA Validator  

1. Download the free **PDF/UA‑2 validator** from the PDF Association (search “PDF/UA validator”).  
2. Drag `Doc_UA.pdf` onto the validator window.  
3. The tool will report “No errors” if the document meets the standard.  

If you encounter warnings about missing language tags, add a language attribute to the Word document (`Review → Language → Set Proofing Language`) before conversion.

## Step 5: Handle Common Edge Cases  

### Custom Fonts  

If your source uses a font that isn’t installed on the server, enable `FontEmbeddingMode = FontEmbeddingMode.Always` to force embedding.  

```csharp
pdfOptions.FontEmbeddingMode = FontEmbeddingMode.Always;
```

### Complex Tables  

PDF/UA‑2 requires that tables have proper structure. Ensure every table in the Word file has header rows defined (`Table Tools → Layout → Repeat Header Rows`). Aspose.Words respects this setting automatically.

### Images Without Alt Text  

Screen readers rely on alternative text. If an image lacks alt text, Aspose.Words will insert an empty description, which may cause a compliance warning. Add alt text in Word (`Picture Tools → Alt Text`) or programmatically:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage && string.IsNullOrEmpty(shape.AlternativeText))
    {
        shape.AlternativeText = "Descriptive text for accessibility";
    }
}
```

## Step 6: Best Practices for Ongoing PDF/UA‑2 Projects  

- **Automate validation**: Integrate the PDF/UA validator into your CI pipeline so every generated PDF is checked before release.  
- **Keep libraries current**: Aspose.Words releases frequent updates that improve PDF/UA support—upgrade at least once a year.  
- **Document your workflow**: Store a checklist (font embedding, alt text, table headers) to ensure non‑technical team members can maintain compliance.  

---

## Conclusion  

You now know exactly how to **create pdf/ua-2 compliant document** using C# and Aspose.Words. By configuring `PdfSaveOptions` with the right flags, embedding fonts, and ensuring your source Word file follows accessibility best practices, you can generate PDFs that pass official PDF/UA‑2 validation without a hitch.  

Ready for the next challenge? Try adding **PDF accessibility** features like logical reading order for multi‑column layouts, or explore **C# document conversion** to other formats such as EPUB while preserving the same accessibility metadata.  

If you hit a snag, drop a comment below—happy coding, and enjoy building inclusive PDFs!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Accessible PDF – Step‑by‑Step Guide for PDF/UA Compliance](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-step-by-step-guide-for-pdf-ua-complian/)
- [Create Accessible PDF in C# – PDF Accessibility Tutorial](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-in-c-pdf-accessibility-tutorial/)
- [convert word to pdf in C# using Aspose.Words – Guide](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}