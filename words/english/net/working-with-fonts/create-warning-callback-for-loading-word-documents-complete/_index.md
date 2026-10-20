---
category: general
date: 2026-03-25
description: Create warning callback to load Word document and detect missing fonts.
  Learn how to configure font settings in Aspose.Words for .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: en
og_description: Create warning callback to load Word document while detecting missing
  fonts. This guide shows how to configure font settings in Aspose.Words.
og_title: Create warning callback – Load Word document & detect missing fonts
tags:
- Aspose.Words
- C#
- Font handling
title: Create warning callback for loading Word documents – Complete Guide
url: /net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create warning callback – Load Word document & detect missing fonts

Ever needed to **create warning callback** when loading a Word document and wondered why some fonts just disappear? You're not the only one. In many enterprise apps, missing fonts cause layout disasters, and without a proper callback you might never even notice the problem.  

The good news? With Aspose.Words for .NET you can **load Word document**, **detect missing fonts**, and **configure font settings** all in a few tidy lines of code. In this tutorial we’ll walk through a complete, runnable example, explain why each piece matters, and show you how to verify that the warning callback is doing its job.

> **What you’ll walk away with**  
> * A full C# program that loads a DOCX, reports any font substitutions, and lets you customise font search paths.  
> * Understanding of the `FontSettings`, `LoadOptions`, and `IWarningCallback` classes.  
> * Tips for handling edge‑cases like embedded fonts or system‑wide font folders.

---

## Prerequisites

- .NET 6+ (or .NET Framework 4.7.2+) with a C# compiler.  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`).  
- A sample Word file (`input.docx`) that uses at least one font not installed on the machine (e.g., *Calibri Light* on a minimal Windows container).  
- Basic familiarity with C# console apps.

No additional libraries are required; everything lives inside Aspose.Words.

---

## Step 1: Create warning callback to detect missing fonts

The **primary** piece of this puzzle is a class that implements `IWarningCallback`. Aspose.Words will invoke this callback whenever it encounters a situation that warrants a warning – font substitution being the most common.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Why this matters** – Without a callback you’d have to sift through logs after the fact. By handling warnings in real time you can decide whether to abort the load, replace the missing font with a fallback, or simply log the issue for later review.

---

## Step 2: Configure FontSettings for custom font handling

Before we actually load the document, we may want to tell Aspose.Words where to look for fonts that aren’t present on the system. That’s where `FontSettings` comes in.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Why this matters** – By pointing Aspose.Words at a folder that contains the missing fonts, you often avoid substitution altogether. When that isn’t possible, a sensible default (like *Arial*) keeps the document readable.

---

## Step 3: Load Word document with the configured warning callback

Now we tie everything together: we create `LoadOptions`, plug in our `FontSettings` and `FontWarningHandler`, and finally load the document.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Why this matters** – `LoadOptions` is the single place where you configure *how* a document is read. By supplying both the font configuration and the warning callback we ensure that any missing font is both looked for in the right places **and** reported immediately.

---

## Step 4: Verify the output – what should you see?

Run the program from a console. If `input.docx` uses a font that isn’t installed and also isn’t in `C:\SharedFonts`, you’ll see something like:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

If all fonts are available, the warning line simply never appears. This immediate feedback loop is invaluable during automated document processing pipelines where silent font swaps could break branding guidelines.

---

## Step 5: Common pitfalls and best‑practice tips

| Pitfall | How to avoid it |
|---------|-----------------|
| **Forgot to reference `Aspose.Words.Fonts`** | Ensure you have `using Aspose.Words.Fonts;` at the top; otherwise the compiler will complain about missing types. |
| **Font folder path is wrong** | Double‑check the path and set `recursive: true` if you have sub‑folders. Use `Path.GetFullPath` to debug. |
| **Multiple warning callbacks** | Aspose.Words only honors the last `WarningCallback` you assign. Keep a single handler that delegates if you need more complex logic. |
| **Running on a server without UI** | Console writes are fine, but for web apps you might want to log to a file or monitoring system instead of `Console.WriteLine`. |
| **Large documents cause performance hit** | Re‑use a single `FontSettings` instance across multiple loads; creating it repeatedly can be costly. |

**Pro tip:** If you need to *collect* warnings for later analysis, store them in a `List<string>` inside the handler instead of printing directly.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

You can then inspect `handler.Messages` after the document load.

---

## Step 6: Extending the solution – what if I need to embed a fallback font?

Sometimes you want the missing font to be *embedded* in the output PDF so that downstream viewers see the exact appearance. After loading the document, you can force embedding:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

This snippet shows how the same **configure font settings** approach can be extended beyond just loading.

---

## Full runnable example

Below is the complete program you can copy‑paste into a new Console App project. It includes all the pieces discussed above.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Expected output** (when a missing font is present):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

If no substitution occurs, only the success messages appear.

---

## Conclusion

We’ve just **created a warning callback** that reliably **detects missing fonts** while **loading a Word document** with Aspose.Words, and we showed how to **configure font settings** to control where the library looks for fonts and which fallback to use. By wiring `FontSettings` and `LoadOptions` together, you gain full visibility into font‑related issues—no more silent layout glitches.

Next steps? Try swapping out the `FontWarningHandler` for a logger that writes to a database, or experiment with **font substitution rules** to map specific missing fonts to brand‑approved alternatives. You might also explore **dynamic font loading** from cloud storage if your app runs in a containerized environment.

Got questions about a particular edge case—like handling OpenType features or dealing with encrypted DOCX files? Drop a comment below, and happy coding!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}