---
category: general
date: 2026-02-10
description: Set warning callback to monitor font changes while you configure default
  font and set default import font in Aspose.Words. Learn the full step‑by‑step solution.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: en
og_description: Set warning callback to monitor font changes while configuring default
  font and setting default import font. Follow the full tutorial for Aspose.Words.
og_title: Set warning callback in C# – Complete Guide
tags:
- Aspose.Words
- C#
- Document Import
title: Set warning callback in C# – Complete Guide to Font Handling
url: /net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set warning callback in C# – Complete Guide to Font Handling

Ever needed to **set warning callback** when loading a Word document and wondered how to *configure default font* at the same time? You’re not alone. In many real‑world projects—like automated report generators or document conversion pipelines—missing fonts can silently break the layout, and the only way to catch those issues is to **monitor font changes** via a warning callback.

In this tutorial we’ll walk through a hands‑on example that shows you how to **set warning callback**, **configure default font**, and even **set default import font** using Aspose.Words for .NET. By the end you’ll have a ready‑to‑run snippet, understand why each piece matters, and know how to adapt it for edge cases such as custom font folders or silent substitutions.

---

## Prerequisites

- .NET 6.0 or later (the code works on .NET Framework 4.6+ as well)  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- A folder that contains the fallback font you want to use (e.g., `fonts/Arial.ttf`)  
- Basic familiarity with C# console apps  

No additional libraries are required.

---

## Step 1: Create LoadOptions and **configure default font**

The first thing you do when you want to control font handling is to build a `LoadOptions` instance. This object tells Aspose.Words how to treat missing fonts during import.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Why this matters:**  
If the source document references a font that isn’t installed on the server, Aspose.Words will look at the folder you supplied. This is the core of **set default import font**—you’re explicitly telling the library where to find a replacement before any warnings are even raised.

---

## Step 2: **Set warning callback** to **monitor font changes**

Aspose.Words emits a `WarningInfoCollection` whenever it has to substitute a font, among other things. By attaching a handler, you can log or react to each substitution.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Why this matters:**  
Simply **configure default font** isn’t enough if you need to audit which fonts were actually swapped. The callback gives you a real‑time log, satisfying the **monitor font changes** requirement and helping you catch unexpected fallbacks early in a CI pipeline.

---

## Step 3: Load the document with the prepared options

Now that the load options are fully prepared, you can safely load any `.docx` file. The callback fires automatically if a substitution occurs.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**What you’ll see:**  
If the source uses a font that isn’t present, the console will print something like:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

That output confirms you’ve successfully **set warning callback** and that the **default import font** took effect.

---

## Step 4: (Optional) Fine‑tune font substitution behavior

Sometimes you might want to replace *all* missing fonts with a single family, regardless of the original request. Aspose.Words lets you set a *fallback font* globally.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**When to use this:**  
If you’re generating PDFs for a brand that only allows a limited set of fonts, this ensures consistency across every document, even if the source tries to use something exotic.

---

## Step 5: Save or further process the document

After loading, you can continue with any processing you need—editing, converting to PDF, extracting text, etc. Here’s a quick example of saving the document as a PDF while preserving the substituted fonts.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

The resulting PDF will display the fallback font wherever a substitution took place, giving you a visual confirmation that the **set warning callback** worked as expected.

---

## Common Pitfalls & Pro Tips

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| **Callback never fires** | `LoadOptions.WarningCallback` wasn’t assigned *before* loading the document. | Always attach the callback **before** calling `new Document(...)`. |
| **Wrong font folder** | Path typo or missing read permissions. | Verify the folder exists and the app has `Read` access. Use absolute paths for reliability. |
| **Multiple substitutions, noisy output** | Large documents with many missing fonts. | Filter warnings by `WarningType.FontSubstitution` (as shown) or write them to a log file instead of console. |
| **Fallback font not applied** | The fallback font isn’t installed on the machine. | Place the `.ttf`/`.otf` file in the folder you passed to `SetFontsFolder`. Aspose.Words loads it directly, no OS install needed. |

**Pro tip:** When you’re running this in a CI/CD pipeline, redirect the console output to a build artifact. That way you have an audit trail of every font substitution that happened during the build.

---

## Full Working Example (Copy‑Paste Ready)

Below is the complete program you can drop into a new Console App project. It includes all the steps, using statements, and comments you need.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Expected console output** (assuming `Times New Roman` was missing):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Run the program, open `output.pdf`, and you’ll see the document rendered with the fallback font wherever necessary.

---

## Conclusion

You now have a solid, production‑ready pattern for how to **set warning callback** in C#, **configure default font**, **monitor font changes**, and **set default import font** when working with Aspose.Words. By attaching a warning collector before loading, pointing `FontSettings` at a reliable font folder, and optionally forcing a global fallback, you gain full visibility and control over font substitution—exactly what any robust document‑processing pipeline needs.

Ready for the next level? Try combining this approach with:

- **Dynamic font loading** from a database (use `FontSettings.SetFontsFolder` at runtime).  
- **Custom warning handlers** that write to a structured log (JSON or CSV) for analytics.  
- **Parallel document processing** where each thread gets its own `LoadOptions` to avoid cross‑talk.

Feel free to experiment, adapt the code to your own architecture, and share any discoveries in the comments. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}