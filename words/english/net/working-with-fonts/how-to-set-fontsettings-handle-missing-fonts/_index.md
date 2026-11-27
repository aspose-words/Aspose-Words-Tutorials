---
category: general
date: 2026-05-29
description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
  gracefully. Step-by-step guide with complete code and best practices.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: en
og_description: How to set FontSettings in Aspose.Words and handle missing fonts quickly.
  Follow this guide for a complete, runnable solution.
og_title: How to Set FontSettings – Handle Missing Fonts
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: How to Set FontSettings – Handle Missing Fonts
url: /net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Set FontSettings – Handle Missing Fonts

Ever wondered **how to set FontSettings** when working with Aspose.Words and suddenly run into a document that references a font you don’t have installed? It’s a common snag, especially when processing client‑supplied files on a server that only has a minimal font set. The good news? You can catch those gaps and **handle missing fonts** without your app crashing or producing ugly PDFs.

In this tutorial we’ll walk through a real‑world scenario: loading a DOCX that asks for “Calibri” while your Linux container only ships “DejaVu Sans”. You’ll see exactly how to configure FontSettings, collect substitution warnings, and supply fallback fonts so the document renders just as the author intended. No fluff—just the code you can drop into your project today.

## Prerequisites

- .NET 6.0 or later (the API works the same on .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 or newer (the NuGet package name is `Aspose.Words`)
- A basic C# development environment (Visual Studio, Rider, or VS Code)

If you’ve got those, let’s dive in.

## Step 1: Create FontSettings and Prepare a Warning Collector

The heart of the solution is the `FontSettings` object. To get a report every time Aspose.Words substitutes a missing typeface, use a `WarningInfoCollection` and assign it to `LoadOptions.WarningCallback`. The collection will receive `WarningInfo` objects whose `WarningType` is `WarningType.FontSubstitution`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Prepare a warning collector
WarningInfoCollection warnings = new WarningInfoCollection();
```

**Why this matters:**  
When the engine can’t locate *Calibri*, it will generate a warning of type `FontSubstitution`. By examining the collected warnings after loading, you keep a transparent audit trail—perfect for debugging or compliance reporting.

> **Pro tip:** If you run this on a CI server, pipe the output to a log file so you can review which fonts were missing after a batch run.

## Step 2: Attach FontSettings to LoadOptions

`LoadOptions` is the gateway for controlling how a document is parsed. By assigning the `FontSettings` we just configured and the warning collector, every subsequent `Document` load will respect our substitution logic and capture warnings.

```csharp
// Step 2 – wire FontSettings and warnings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warnings
};
```

**What’s happening under the hood?**  
During the `Document` constructor Aspose.Words reads the XML of the DOCX, resolves font references, and—if a font isn’t found—adds a `WarningInfo` with `WarningType.FontSubstitution` to the collection we provided. Without this hook, you’d never know a substitution took place.

## Step 3: Load the Document and (Optionally) Define Fallback Fonts

Now we finally bring the file into memory. If you already have a fallback font folder (e.g., a directory of OpenType fonts shipped with your app), tell `FontSettings` where to look. This step is optional but often the cleanest way to *handle missing fonts*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Edge case alert:**  
If the document contains a custom font embedded as a binary stream, Aspose.Words will use it automatically—no substitution needed. The warning only fires for *missing* system fonts.

### Verifying the Result

After loading, you can inspect the collected warnings and then save the document to PDF or Word to confirm everything looks right.

```csharp
// Output any font substitution warnings
foreach (WarningInfo info in warnings)
{
    if (info.WarningType == WarningType.FontSubstitution)
        Console.WriteLine(info.Description);
}

// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

When you run the program, the console will output lines like:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

If you see these messages, you’ve successfully **handled missing fonts** and know exactly which substitutions occurred.

## Step 4: Advanced – Custom Font Substitution Rules (Optional)

Sometimes you need deterministic mapping, e.g., always replace *Times New Roman* with *Liberation Serif*. You can achieve this with the table substitution rule available via `FontSettings.SubstitutionSettings.TableSubstitution`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionSettings.TableSubstitution.AddSubstitutes(
    "Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionSettings.TableSubstitution.AddSubstitutes(
    "Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Why bother?**  
Explicit rules give you control over typography, ensuring brand consistency across generated PDFs, especially when you’re producing marketing collateral.

## Common Pitfalls & How to Avoid Them

| Pitfall | Symptom | Fix |
|---------|---------|-----|
| **No warning output** | You think fonts are fine but the document looks wrong. | Ensure the `WarningCallback` is assigned **before** loading the document and that you inspect the `WarningInfoCollection` after loading. |
| **Fallback folder not scanned** | Substitutions still fall back to system defaults. | Call `SetFontsFolder(path, true)` with the second argument `true` to recurse sub‑folders. |
| **Embedded fonts ignored** | You expected a custom embedded font to be used, but a substitution occurs. | Verify the source DOCX actually embeds the font (check with Word → File → Info → Fonts). |

## Full Working Example

Below is the complete, copy‑paste‑ready program. It demonstrates everything from warning collection to saving the final PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings
        FontSettings fontSettings = new FontSettings();

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // Prepare a warning collector
        WarningInfoCollection warnings = new WarningInfoCollection();

        // 2️⃣ Attach FontSettings and warnings to LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = fontSettings,
            WarningCallback = warnings
        };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionSettings.TableSubstitution.AddSubstitutes(
            "Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionSettings.TableSubstitution.AddSubstitutes(
            "Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Output any font substitution warnings
        foreach (WarningInfo info in warnings)
        {
            if (info.WarningType == WarningType.FontSubstitution)
                Console.WriteLine(info.Description);
        }

        // 6️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Expected console output** (example):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Run the program, open `Output.pdf`, and you’ll see the text rendered with the fallback fonts—no missing‑glyph squares, no crashes.

## Conclusion

You now have a solid, production‑ready pattern for **how to set FontSettings** in Aspose.Words and **handle missing fonts** elegantly. By using a `WarningInfoCollection` to capture `FontSubstitution` warnings, pointing to a fallback font directory, and (if needed) defining explicit substitution rules, you gain full visibility and control over typography in automated document pipelines.

What’s next? Try adding a custom font collection for brand‑specific typefaces, or explore the `FontSourceBase` API to load fonts from a database or cloud storage. The same principles apply—just plug a different source into `FontSettings`.

Got questions about edge cases, such as handling right‑to‑left scripts or emoji fonts? Drop a comment below, and happy coding!


## What Should You Learn Next?

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}