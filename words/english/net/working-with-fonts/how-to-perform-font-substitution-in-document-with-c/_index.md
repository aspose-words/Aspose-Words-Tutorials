---
category: general
date: 2026-10-13
description: Learn font substitution in document using C#. This guide shows how to
  set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: en
lastmod: 2026-10-13
og_description: Font substitution in document is essential when working with legacy
  Chinese files. Follow this step‑by‑step tutorial to load a DOCX with big5 encoding
  and replace old fonts.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Font substitution in document with C# – complete guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: How to perform font substitution in document with C#
url: /net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Font substitution in document – complete C# tutorial

If you need **font substitution in document** to render legacy Chinese files correctly, this guide shows you exactly how to do it. By configuring the proper text encoding and swapping an outdated font for a modern one, you guarantee that the final DOCX displays as intended.

Document processing often breaks when the source uses an old encoding like **big5** or references a font that no longer exists on the system. This tutorial walks you through loading a DOCX with the correct **big5 encoding**, applying **legacy font replacement**, and producing a clean output that works on any Windows machine.

You’ll learn:

* How to create a `LoadOptions` object with **big5 encoding**.  
* How to open a DOCX file using **C# LoadOptions**.  
* How to perform **font substitution in document** by mapping an old font to a modern equivalent.  
* Edge‑case handling for missing fonts and multiple font families.

No external tools are required beyond the Aspose.Words for .NET library, and the complete code can be copied into a console project and run immediately.

## Prerequisites

* .NET 6.0 or later (the sample uses .NET 6 console syntax).  
* Aspose.Words for .NET – install via `dotnet add package Aspose.Words`.  
* A DOCX file saved with **big5 encoding** that references the legacy font `MingLiU-ExtB`.  
* Basic familiarity with C# and Visual Studio or any IDE of your choice.

## Step 1: Set up the project and import namespaces

Create a new console application and add the required `using` directives. This ensures the code compiles without extra modifications.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Pro tip:** Keep the `Main` method minimal; it improves readability and makes the tutorial easier to follow.

## Step 2: Define load options with the correct text encoding (big5 for Traditional Chinese)

The `LoadOptions` class tells Aspose.Words how to interpret the raw bytes in the source file. Using **big5 encoding** is critical for Traditional Chinese characters that were saved with that legacy code page.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Why this matters:** If you omit the encoding or use the default UTF‑8, characters may appear as garbled symbols (mojibake). Specifying `big5` preserves the original glyphs before any font substitution occurs.

## Step 3: Load the DOCX file using the specified encoding

Pass the `loadOptions` instance to the `Document` constructor. This loads the file while respecting the **document encoding for Chinese** you defined earlier.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

If the file cannot be found, the program throws a `FileNotFoundException`. Ensure the path is correct and that the application has read permissions.

## Step 4: Substitute a legacy font with a modern equivalent

Many older Chinese documents reference `MingLiU-ExtB`, which may not be present on newer Windows installations. Mapping it to `Microsoft JhengHei` (a widely available Unicode font) ensures proper rendering.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Explanation:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` registers a global replacement rule. Every time Aspose.Words encounters `MingLiU-ExtB`, it swaps it for `Microsoft JhengHei`.  
* The optional loop prints the mapping, which is useful for debugging in large documents with multiple font families.

## Step 5: Save the processed document

After substitution, write the document to a new file. The output will display the Chinese text using the modern font, eliminating missing‑glyph warnings.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Open the resulting file in Microsoft Word or any DOCX viewer; you should see the Traditional Chinese characters rendered cleanly with `Microsoft JhengHei`.

## Handling edge cases and common pitfalls

| Situation | Recommended approach |
|-----------|----------------------|
| **The source font is not listed in the document** | Use `doc.FontInfos.Substitution.Add` with a wildcard pattern, e.g., `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Multiple legacy fonts need replacement** | Call `Add` for each pair, or load a substitution dictionary from a configuration file. |
| **The target font is unavailable on the target machine** | Choose a font that ships with Windows (e.g., `Arial Unicode MS`) or embed the font using `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Encoding errors still appear** | Verify the source file truly uses **big5**; you can inspect the file with a hex editor or use `File.ReadAllBytes` and compare byte patterns. |

## Full working example

Below is the complete, self‑contained program. Copy it into `Program.cs`, adjust the file paths, and run it.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Expected result:** Opening `big5_doc_fixed.docx` shows all Traditional Chinese characters correctly rendered, with no missing‑glyph warnings, because `MingLiU-ExtB` has been replaced by `Microsoft JhengHei`.

## Conclusion

You now have a reliable method for **font substitution in document** tasks using C#. By configuring **big5 encoding**, loading the DOCX with `LoadOptions`, and mapping legacy fonts to modern equivalents, you eliminate rendering problems that plague older Chinese files.  

From here you can:

* Extend the substitution map to cover additional legacy fonts.  
* Automate the process for batches of documents (loop over a directory).  
* Combine font substitution with other document transformations such as watermarking or PDF conversion.

Feel free to experiment with different target fonts or embed custom fonts for full portability. If you run into any issues, revisit the edge‑case table above or consult the Aspose.Words documentation for advanced font handling.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Log Font Substitution Warnings – Complete Aspose.Words Guide](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}