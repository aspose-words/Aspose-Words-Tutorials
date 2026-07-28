---
category: general
date: 2026-01-11
description: Enable font substitution warnings to detect missing fonts in your .NET
  documents. Learn how to get missing font name and list missing fonts with Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: en
og_description: Enable font substitution warnings in Aspose.Words to detect missing
  fonts, get missing font name, and list missing fonts in your documents.
og_title: Enable Font Substitution Warnings – Step‑by‑Step C# Tutorial
tags:
- Aspose.Words
- C#
- Document Processing
title: Enable Font Substitution Warnings in Aspose.Words – Complete Guide
url: /net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enable Font Substitution Warnings – Complete Guide

Ever wondered why a Word document looks slightly off after you load it on a server? Chances are a font the original author used isn’t available on your machine, and Aspose.Words silently swapped it for the closest match. **Enable font substitution warnings** and you’ll instantly know which fonts are missing, what they were replaced with, and how to act on that information.

In this tutorial we’ll walk through a practical, end‑to‑end example that shows you how to **detect missing fonts**, retrieve the **get missing font name**, and even **list missing fonts** for reporting. No fluff, just a clear solution you can drop into any .NET project today.

---

## What You’ll Learn

- How to configure `LoadOptions` so that Aspose.Words emits detailed warnings.
- The exact code needed to load a document and enumerate font‑related warnings.
- Ways to extract the missing font name and its substitution, then output a tidy report.
- Tips for handling edge cases, such as documents with dozens of missing fonts or custom font folders.

### Prerequisites

- .NET 6+ (the code also works with .NET Framework 4.7+)
- Aspose.Words for .NET 23.10 or newer (you can grab it from NuGet)
- A sample DOCX that references a font you don’t have installed (we’ll call it `MissingFont.docx`)

If you’ve got those basics, let’s dive in.

---

## Step 1: Set Up LoadOptions to Enable Font Substitution Warnings  

The first thing you need to do is tell Aspose.Words that you care about missing fonts. By default the library only logs warnings internally. Setting the `SubstitutionWarningLevel` to `Typical` (or `All` for the most verbose output) flips the switch.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Why this matters:**  
When `SubstitutionWarningLevel` is set, every time Aspose.Words can’t find a referenced font it adds a `FontSubstitutionWarning` to the document’s `Warnings` collection. That collection is the only reliable way to **detect missing fonts** without parsing the document manually.

> **Pro tip:** If you’re dealing with a batch of documents and want to be absolutely certain you catch every substitution, use `FontSubstitutionWarningLevel.All`. It’s a little noisier but guarantees no warning slips through.

---

## Step 2: Load the Document Using the Configured Options  

Now that the warning system is primed, load your DOCX with the `LoadOptions` we just prepared. The path can be absolute or relative; just make sure the file exists.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**What’s happening under the hood?**  
Aspose.Words parses the document’s XML, resolves each `<w:font>` element, and checks the system’s font catalog (plus any custom folders you may have added to `FontSettings`). When it can’t locate a font, it records a warning—exactly what we need to **list missing fonts** later.

---

## Step 3: Iterate Over Warnings and Extract Missing Font Details  

With the document in memory, the `Warnings` collection holds every `FontSubstitutionWarning`. We’ll loop through it, filter for the right type, and print a friendly report.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Expected output** (assuming the source document references `MyCustomFont` which isn’t installed):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Notice how each entry gives you both the **get missing font name** (`MyCustomFont`) and the fallback (`Arial`). That’s exactly the information you need to decide whether to embed the original font, ask the author for a replacement, or simply accept the substitution.

---

## Step 4: Optional – Collect the Data into a List for Further Processing  

If you need to export the report to CSV, send it over an API, or just keep it in memory for later, you can stash the warnings in a strongly‑typed list.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Now you’ve **list missing fonts** in a format that any downstream system can consume. Whether you’re feeding a dashboard or generating an audit log, the data is ready.

---

## Step 5: Handling Edge Cases and Common Pitfalls  

### Multiple Missing Fonts in a Single Run  

Large corporate templates often reference dozens of custom fonts. The warning collection can become sizable, but the iteration pattern shown above scales linearly, so performance isn’t a concern. Just remember to keep the output readable—grouping by page or style can be helpful if you need deeper analysis.

### Custom Font Folders  

If you store fonts in a non‑standard directory (e.g., a shared network share), tell Aspose.Words where to look:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Setting this *before* loading the document gives the library a chance to find the fonts, which may eliminate some warnings altogether.

### Suppressing Specific Warnings  

Sometimes you know a particular substitution is acceptable (e.g., a decorative font that you never mind replacing). You can filter those out after the fact:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Version Compatibility  

The `FontSubstitutionWarningLevel` enum has been stable since Aspose.Words 20.12. If you’re on an older version, you may need to upgrade to access the warning‑level feature.

---

## Full Working Example  

Below is the complete, ready‑to‑run program that incorporates all the steps above. Paste it into a new console project, add the Aspose.Words NuGet package, and point `docPath` at a document that references a missing font.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Running this program will **enable font substitution warnings**, **detect missing fonts**, **get missing font name**, and **list missing fonts** in both the console and a CSV file.

---

## Conclusion  

We’ve just covered everything you need to **enable font substitution warnings** in Aspose.Words, from the initial configuration to extracting a clean list of missing fonts. By following the steps above you’ll be able to audit your documents, ensure visual fidelity, and avoid nasty surprises when rendering on a server.

Next, you might want to explore:

- **Embedding missing fonts** directly into the output PDF or DOCX (use `FontSettings.EmbeddedFonts`).
- **Automating font installation** on build agents based on the generated report.
- **Integrating with CI pipelines** to fail builds when critical fonts are absent.

Give those a try, and you’ll turn a simple warning system into a full‑blown font‑management workflow.

Happy coding, and may all your fonts be found!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}