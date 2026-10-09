---
category: general
date: 2026-02-24
description: How to detect fonts in a Word document using Aspose.Words. Learn how
  to set callback and load word document with full code example.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: en
og_description: How to detect fonts in a Word document using a warning callback. This
  guide shows how to set callback and load word document with Aspose.Words.
og_title: How to Detect Fonts in Word Documents – Step‑by‑Step C# Tutorial
tags:
- C#
- Aspose.Words
- Document Processing
title: How to Detect Fonts in Word Documents – Complete C# Guide
url: /net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Detect Fonts in Word Documents – Complete C# Guide

Ever wondered **how to detect fonts** that are missing when you load a Word file? Maybe you’ve run into a document that looks fine in the editor, but the PDF you generate swaps a few typefaces behind the scenes. That’s a classic symptom of font substitution, and catching it early can save you from nasty layout surprises.

In this tutorial we’ll walk through a practical solution: using **Aspose.Words** to load a `.docx`, attach a warning callback, and **how to set callback** that reports every font substitution. By the end you’ll not only know **how to detect fonts** programmatically, you’ll also understand **how to set callback** correctly and **load word document** safely—all in a single, runnable C# example.

> **What you’ll get**
> * A complete, copy‑paste‑ready code sample  
> * Step‑by‑step explanation of each line  
> * Tips for handling edge cases like multiple missing fonts or custom font folders  
> * Expected console output so you can verify everything works

---

## Prerequisites

- .NET 6.0 or later (the code works with .NET Core as well)  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- A Word file that intentionally references a font you don’t have installed (e.g., `MissingFont.docx`)  
- Visual Studio, Rider, or any editor you like

No other libraries are needed; everything else is part of the standard .NET runtime.

---

## How to Detect Fonts in a Word Document

### Step 1: Create Load Options and Attach a Warning Callback

The first thing we do is tell Aspose.Words that we want to be notified about any issues that arise while loading the file. This is where **how to set callback** comes into play.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Why this matters:**  
`LoadOptions` is the gateway to customizing the loading process. By assigning an instance of `FontWarningCollector` to `WarningCallback`, Aspose.Words will invoke our `Warning` method every time it replaces a missing font with a fallback. This is the core of **how to detect fonts** that aren’t present on the machine.

---

### Step 2: Prepare the LoadOptions Instance

Now we instantiate `LoadOptions` and hook up our callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Pro tip:** If you need to control *where* Aspose looks for replacement fonts, you can also set `loadOptions.FontSettings` here. That’s useful when you have a private font folder on the server.

---

### Step 3: Load the Word Document

With the options ready, we finally **load word document**. This is the moment where Aspose parses the DOCX and, if any fonts are missing, our callback fires.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**What happens under the hood?**  
Aspose.Words reads the XML parts of the DOCX, resolves each `<w:font>` reference, and checks the system’s font collection. Whenever a reference can’t be satisfied, it substitutes the first matching fallback font and raises a `FontSubstitution` warning.

---

### Step 4: Verify the Output

Run the program and watch the console. For every missing font you’ll see a line like:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

If the document contains no missing fonts, the console stays silent—meaning **how to detect fonts** returned no hits.

---

### Step 5: Full Working Example (Console App)

Below is a self‑contained `Program.cs` you can drop into a new console project. It includes all the pieces we discussed plus a tiny helper to keep the console window open when debugging.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Expected console output** (example):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

If you replace `MissingFont.docx` with a file that uses only installed fonts, you’ll see only the “Press any key…” line—confirming that the detection logic works as intended.

---

## Common Questions & Edge Cases

### What if I need to capture *all* warnings, not just font substitution?

Simply remove the `if (info.Type == WarningType.FontSubstitution)` guard. The `WarningInfo` object contains a `Type` enum you can switch on for other scenarios (e.g., `DocumentStructure`, `ImageLoading`).

### Can I log warnings to a file instead of the console?

Absolutely. Replace `Console.WriteLine` with any logging framework call (`Serilog`, `NLog`, etc.). The callback runs on the same thread that loads the document, so make sure your logger is thread‑safe.

### How does this behave in a web application?

In ASP.NET Core you’d typically inject a singleton `IWarningCallback` implementation and pass it via `LoadOptions`. Remember to avoid writing to the response stream directly—log to a database or an in‑memory collection that you can later expose via an API endpoint.

### What about custom fonts stored in a non‑system folder?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Now Aspose.Words will search `C:\MyCustomFonts` before falling back to the OS fonts, reducing the number of substitution warnings you see.

---

## Visual Summary

![Detect fonts warning callback in Aspose.Words](/images/font-warning-callback.png "How to detect fonts using a warning callback")

*The screenshot shows the console output when a missing font is substituted. The alt text contains the primary keyword for SEO.*

---

## Conclusion

You now have a solid, production‑ready pattern for **how to detect fonts** in any Word file you load with Aspose.Words. By **how to set callback** you gain real‑time insight into missing or substituted typefaces, and you’ve learned the proper way to **load word document** while keeping your code clean and maintainable.

Next steps? Try extending the callback to collect warnings into a list, then surface them in a UI or an automated report. You might also explore `FontSettings.SubstitutionSettings` to control *which* fonts get chosen as fallbacks.

Feel free to experiment—swap out the document, add more missing fonts, or integrate the logic into a larger document‑processing pipeline. If you run into any hiccups, drop a comment below or ping me on GitHub.

Happy coding, and may your documents always render with the fonts you expect!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}