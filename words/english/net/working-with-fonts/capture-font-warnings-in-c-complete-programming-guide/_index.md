---
category: general
date: 2026-02-18
description: Learn how to capture font warnings and detect missing fonts in C# using
  Aspose.Words. Follow this step‑by‑step guide to handle missing fonts efficiently.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: en
og_description: Capture font warnings in C# and learn to detect missing fonts, handle
  missing fonts, and list missing fonts with a full code example.
og_title: Capture Font Warnings in C# – Complete Guide
tags:
- Aspose.Words
- C#
- Font Management
title: Capture Font Warnings in C# – Complete Programming Guide
url: /net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capture Font Warnings in C# – Complete Programming Guide

Ever wondered how to **capture font warnings** when a document references a font that isn’t installed on the server? You’re not the only one. In many enterprise apps, missing fonts cause layout glitches, and the only reliable way to spot them is by listening for the warnings the library throws.  

In this tutorial we’ll show you a ready‑to‑run solution that not only **capture font warnings** but also **detect missing fonts**, **handle missing fonts**, and even **list missing fonts** so you can decide whether to substitute, embed, or alert the user. No external documentation needed—just copy, paste, and run.

## What You’ll Learn

- How to configure `LoadOptions` to turn on font‑substitution warnings.  
- The exact code you need to load a DOCX and pull out every warning.  
- Why each step matters, including performance considerations.  
- Edge‑case handling such as documents with mixed‑script fonts or custom font folders.  

**Prerequisites**: .NET 6+ (or .NET Framework 4.6+), a reference to the **Aspose.Words** NuGet package, and a basic understanding of C#. If you’ve never used Aspose.Words before, don’t worry—this guide walks you through every nuance.

![Diagram showing capture font warnings flow](image.png){alt="capture font warnings diagram"}

## Capture Font Warnings – Why It Matters

When Aspose.Words loads a document, it silently swaps any unavailable font with a fallback. That fallback keeps the load operation alive, but the visual result can be completely off‑center. By turning on the **SubstitutionWarningLevel.All** flag, the library adds a `WarningInfo` entry for each missing font, allowing you to **detect missing fonts** before the document is rendered or saved.

> **Pro tip:** If you’re processing hundreds of files in a batch job, logging these warnings to a central store can save you hours of manual QA later.

## Step 1: Set Up Your Project

1. Open your favourite IDE (Visual Studio, Rider, VS Code).  
2. Create a new console project:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Add the Aspose.Words package:

```bash
dotnet add package Aspose.Words
```

That’s it—no extra DLLs, no COM interop. The library ships everything you need to **handle missing fonts**.

## Step 2: Prepare Load Options to Capture All Font Substitution Warnings

To make the engine **capture font warnings**, you must tell it to record every substitution. The following snippet creates a `LoadOptions` instance, enables the warning level, and (optionally) points the engine at a folder that contains custom fonts you might want to use.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Why this matters:**  
- `SubstitutionWarningLevel.All` ensures **every** missing‑font event is recorded, not just the first one.  
- Without this flag, Aspose.Words silently replaces the font and you never know a problem exists.

## Step 3: Load the Document Using the Configured Options

Now we actually open the file. Replace `DocumentWithMissingFonts.docx` with the path to your test document.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

If the file contains any references to fonts that aren’t on the machine (or in the optional folder you added), the `document.WarningInfoCollection` will be populated.

## Step 4: Find and Display Any Font Substitution Warnings

Here’s the heart of the tutorial: iterating over the `WarningInfoCollection` to **list missing fonts**. We’ll filter by `WarningType.FontSubstitution` and print a friendly message.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Expected Output

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

If the document uses only installed fonts, you’ll see the “✅ No missing fonts detected” line.

## Step 5: Advanced – How to **Handle Missing Fonts** Programmatically

Simply printing a list may be enough for a diagnostic tool, but many production systems need to **handle missing fonts** automatically. Below are two common strategies:

### 5.1 Substitute with a Known Fallback

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Embed a Custom Font on the Fly

If you have a corporate font file (`MyBrand.ttf`), you can embed it when a missing font is detected:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Note:** Embedding fonts may increase the output file size, so weigh the trade‑off between fidelity and bandwidth.

## Common Pitfalls and How to Avoid Them

| Symptom | Likely Cause | Fix |
|---------|--------------|-----|
| No warnings appear even though the document looks wrong | `SubstitutionWarningLevel` not set to `All` | Ensure step 2 sets the flag exactly as shown |
| Warnings list the same font multiple times | Document contains the font in several styles | De‑duplicate if you only need a unique list: `fontWarnings.Select(w => w.Description).Distinct()` |
| Application crashes on large DOCX files | Loading with default memory settings | Use `LoadOptions.LoadFormat` or stream the file to reduce memory pressure |

## Full Working Example (Copy‑Paste Ready)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Run the program with `dotnet run`. You should see the list of missing fonts printed to the console, confirming that you have successfully **captured font warnings**.

## Conclusion

You now have a complete, production‑ready pattern to **capture font warnings**, **detect missing fonts**, **handle missing fonts**, and **list missing fonts** using Aspose.Words in C#. The approach is lightweight, requires only a few lines of code, and can be dropped into any existing pipeline—whether you

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}