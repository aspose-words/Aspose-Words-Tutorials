---
category: general
date: 2026-04-02
description: How to detect fonts in C# documents using Aspose.Words. Learn to configure
  font settings and handle missing fonts efficiently.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: en
og_description: How to detect fonts in C# documents using Aspose.Words. This guide
  shows you how to configure font settings and handle missing fonts.
og_title: How to Detect Fonts in C# – Complete Guide
tags:
- C#
- Aspose.Words
- Document Processing
title: How to Detect Fonts in C# – Complete Guide
url: /net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Detect Fonts in C# – Complete Guide

Ever wondered **how to detect fonts** that are missing or substituted when you load a Word document in .NET? You're not the only one—developers constantly hit the wall when a document references a font that isn’t installed on the server. The good news is that Aspose.Words gives you a clean, programmatic way to spot those gaps.

In this tutorial we’ll walk through a hands‑on example that not only shows **how to detect fonts**, but also demonstrates how to **configure font settings** and **handle missing fonts** gracefully. By the end you’ll have a ready‑to‑run snippet that prints every font substitution warning, so you can log, alert, or replace fonts as needed.

---

## What You’ll Need

- **Aspose.Words for .NET** (latest version works best; the code below targets .NET 6+)
- A .NET development environment (Visual Studio, Rider, or VS Code)
- A sample `.docx` that references a font you don’t have installed (great for testing)

No extra NuGet packages beyond Aspose.Words are required, and the solution works on Windows, Linux, and macOS.

---

## Step 1: Install and Reference Aspose.Words

First, add the library to your project. The NuGet command is straightforward:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** If you’re on a CI server, pin the package version to avoid unexpected breaking changes.

---

## Step 2: Configure Font Settings (and Prepare Load Options)

Before you open a document, you can tell Aspose.Words where to look for fallback fonts. This is the **configure font settings** part that prevents the engine from silently swapping fonts you might not want.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Why bother? If the document references *Comic Sans* but your server only has *Calibri*, Aspose.Words will substitute *Calibri* and raise a warning. By configuring the search path, you reduce unwanted surprises.

---

## Step 3: Load the Document with the Prepared Options

Now we actually open the file. The `LoadOptions` we built in the previous step are passed directly to the `Document` constructor.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

If the file can’t be found or is corrupted, an exception is thrown—so you might want to wrap this in a try/catch in production code.

---

## Step 4: Scan the Document Warnings for Font Substitutions

Aspose.Words collects a list of warnings while parsing. Among them, `FontSubstitutionWarning` tells you exactly which font was swapped.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

The `Warnings` collection may also contain other items (e.g., `DocumentStructureWarning`). Filtering for `FontSubstitutionWarning` ensures we only report the **handle missing fonts** scenario we care about.

---

## Step 5: Put It All Together – A Complete, Runnable Example

Below is the full program. Copy‑paste it into a new console app and run; you’ll see each missing font printed to the console.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Expected output** (example):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

If the document uses only fonts that exist on the machine, you’ll see the “No font substitutions detected” line instead.

---

## Edge Cases & Common Questions

### What if the document contains **no warnings** at all?

That simply means every referenced font was located in the search folders you configured. The `anySubstitutions` flag in the example covers this case.

### Can I **log** warnings to a file instead of the console?

Absolutely. Replace the `Console.WriteLine` calls with a logger of your choice (Serilog, NLog, etc.). The `WarningInfo` object also exposes `WarningType` and `WarningMessage` if you need more detail.

### How do I **ignore** certain fonts, like a corporate brand font that should never be swapped?

You can add a custom substitution rule:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Now Aspose.Words will only replace *MyBrandFont* with the listed alternatives, and you’ll still receive a warning you can act on.

### Does this work on **Linux** containers?

Yes—just make sure you mount a folder with the required `.ttf`/`.otf` files and point `SetFontsFolder` to it. Aspose.Words doesn’t rely on OS‑installed fonts.

---

## Visual Overview

![how to detect fonts flowchart](detect-fonts.png "Diagram showing the steps to detect fonts in a document")

*Image alt text:* **how to detect fonts** flowchart illustrating configuration, loading, and warning inspection.

---

## Recap – What We’ve Learned

- **How to detect fonts** that are missing or substituted using Aspose.Words warnings.  
- How to **configure font settings** to point at custom font folders and set a default fallback.  
- Strategies to **handle missing fonts**, from logging to custom substitution rules.

All of this fits into a compact, self‑contained console app that you can drop into any .NET solution.

---

## Next Steps & Related Topics

- **Embedding fonts** directly into the output document to avoid future substitutions (`SaveOptions` with `EmbedFullFonts`).  
- **Programmatic font replacement** – replace missing fonts with a specific alternative before saving.  
- **Performance tuning** – cache `FontSettings` when processing many documents in a batch.  

If you’re interested in those topics, search for *configure font settings* and *handle missing fonts*—they’ll lead you to deeper dives on font management with Aspose.Words.

---

Happy coding! Got a weird font edge case? Drop a comment, and we’ll troubleshoot together.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}