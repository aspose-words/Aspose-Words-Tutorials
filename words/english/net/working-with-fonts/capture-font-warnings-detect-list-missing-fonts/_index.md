---
category: general
date: 2025-12-31
description: Capture font warnings in Aspose.Words to detect missing fonts and list
  missing fonts in your .NET app. Learn a step‑by‑step C# solution.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: en
og_description: Capture font warnings in Aspose.Words to detect missing fonts and
  list missing fonts. Complete C# guide with code and tips.
og_title: Capture Font Warnings – Detect & List Missing Fonts
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Capture Font Warnings – Detect & List Missing Fonts
url: /net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Warnings – Detect & List Missing Fonts

Ever needed to **capture font warnings** when loading a Word document but weren’t sure how to surface the missing‑font details? You’re not alone. In many real‑world projects, missing fonts cause layout glitches, and without proper warnings you end up chasing phantom bugs.  

In this tutorial we’ll show you how to **detect missing fonts** and **list missing fonts** using Aspose.Words for .NET. By the end you’ll have a ready‑to‑run C# snippet that prints every substitution warning, so you can log, alert, or even replace fonts automatically.

---

## Why Capture Font Warnings Matters

When Aspose.Words opens a DOCX that references a font not installed on the server, it silently substitutes a fallback. The document looks fine, but the visual fidelity is compromised—think of a corporate brand logo rendered in the wrong typeface.  

Capturing those warnings lets you:

* **Maintain brand consistency** – you know exactly which fonts are missing.
* **Automate remediation** – replace missing fonts programmatically.
* **Audit compliance** – generate reports for legal or design reviews.

In short, **capture font warnings** is the first line of defense against silent font substitution.

---

## Set Up LoadOptions to Detect Missing Fonts

The key to surfacing warnings is the `LoadOptions.FontSubstitutionWarning` property. By default it’s set to `None`, which means Aspose.Words swallows the messages. Switching it to `All` tells the library to record every substitution event.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Pro tip:** If you already have a custom font folder, assign it to `FontSettings.SetFontsFolder("path")` before loading the document. That way you can **detect missing fonts** that aren’t in the system directory.

---

## Load the Document and List Missing Fonts

Now that the `LoadOptions` are ready, the next step is to load the Word file. The constructor accepts the options object, and any substitution will be recorded in the document’s `WarningInfoCollection`.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

If the file references fonts that aren’t available, each missing font generates a `WarningInfo` entry. You can **list missing fonts** by iterating over that collection.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Typical output looks like:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Each line tells you exactly which font was missing, satisfying the **list missing fonts** requirement.

---

## Read and Interpret the WarningInfoCollection

The `WarningInfoCollection` can contain different warning types (e.g., `DocumentStructure`, `ImageLoading`). To focus solely on font issues, filter by `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Why filter? Because a large document may also generate warnings about corrupted images or unsupported features. By narrowing the collection you avoid noise and keep the **capture font warnings** output clean.

---

## Full Working Example – Capture Font Warnings in Action

Below is the complete, self‑contained program you can drop into any .NET console project. It demonstrates every step from configuring `LoadOptions` to printing a tidy list of missing fonts.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Expected console output**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

If the document contains no missing fonts you’ll see:

```
All referenced fonts are available – no warnings captured.
```

---

## Common Edge Cases & How to Handle Them

| Situation | Why It Happens | Recommended Fix |
|-----------|----------------|-----------------|
| **Document uses an embedded OpenType font** | Aspose.Words can read embedded fonts, but only if the file isn’t corrupted. | Verify the DOCX in Word first; re‑embed the font if necessary. |
| **Large number of warnings** (e.g., 200+ missing fonts) | Bulk imports from legacy systems often reference a wide font palette. | Batch‑process the warnings: store them in a database, then run a font‑installation script. |
| **WarningInfoCollection is empty** | Either the document has all fonts, or `FontSubstitutionWarning` was left at `None`. | Double‑check your `LoadOptions` configuration and ensure you’re loading the correct file path. |
| **Custom fonts located on a network share** | Network latency can cause timeouts during font lookup. | Pre‑load the fonts into `FontSettings` using `SetFontsFolder` and set `CacheFontData = true`. |

These tips help you **detect missing fonts** reliably, even in complex environments.

---

## Image Illustration

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*The screenshot shows a console run where two missing fonts are reported.*

---

## Next Steps – Going Beyond Simple Reporting

Now that you can **capture font warnings**, consider automating remediation:

1. **Automatic Font Substitution** – Replace missing fonts with a company‑approved fallback by modifying `FontSettings.SubstitutionSettings`.
2. **Logging to a Monitoring System** – Pipe the warning messages into Serilog, ELK, or Azure Application Insights.
3. **User‑Facing Reports** – Generate an HTML or PDF summary for designers to review which fonts need to be installed.

All of these extensions build on the same foundation we covered: configuring `LoadOptions`, loading the document, and reading `WarningInfoCollection`.

---

## Conclusion

You’ve just learned how to **capture font warnings** in Aspose.Words, **detect missing fonts**, and **list missing fonts** with a clean, console‑friendly output. The approach is straightforward, requires only a few lines of C#, and works with any .NET version that supports Aspose.Words 23.x or later.  

Give it a try on a sample DOCX that references a font you deliberately uninstall – you’ll see the warnings appear instantly. From there, you can decide whether to install the missing typefaces, substitute them programmatically, or simply log the issue for later review.

Happy coding, and may your documents always render with the right fonts!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}