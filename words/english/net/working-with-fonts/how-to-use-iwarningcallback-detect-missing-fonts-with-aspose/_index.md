---
category: general
date: 2026-06-24
description: How to use IWarningCallback to detect missing fonts in Aspose.Words documents.
  Learn a full, runnable example and best practices.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: en
og_description: How to use IWarningCallback to detect missing fonts in Aspose.Words.
  Follow the step‑by‑step guide for a complete, production‑ready solution.
og_title: How to Use IWarningCallback – Detect Missing Fonts
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
url: /net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words

How to use **IWarningCallback** is essential when you work with Aspose.Words and need to **detect missing fonts** in a DOCX file. In this guide we’ll walk through a complete, copy‑and‑paste example that shows you exactly how to use IWarningCallback to catch font‑substitution warnings, why it matters, and what to do once you’ve captured them.

If you’ve ever opened a document and seen garbled text because a custom font wasn’t installed, you know the frustration. By the end of this tutorial you’ll have a reliable way to surface those problems programmatically, log them, or even apply a fallback font automatically.

## What You’ll Learn

- The purpose of **IWarningCallback** and when to use it.  
- How to implement a custom warning collector that isolates **detect missing fonts** events.  
- Wiring the collector into **LoadOptions** so every document load is monitored.  
- Verifying the output and handling edge cases (multiple missing fonts, silent warnings, etc.).  

### Prerequisites

- .NET 6.0 or later (the code also works on .NET Framework 4.6+).  
- Aspose.Words for .NET installed via NuGet (`Install-Package Aspose.Words`).  
- A DOCX file that references a font not present on the machine (e.g., `DocumentWithMissingFont.docx`).  

No additional libraries are required—everything lives inside Aspose.Words.

---

## How to Use IWarningCallback to Detect Missing Fonts in Aspose.Words

Below is the **full, runnable program**. Copy it into a new console project, adjust the file path, and run. You’ll see console output for every missing‑font warning.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Expected Output

If `DocumentWithMissingFont.docx` references a font called *“MyFancyFont”* that isn’t installed, you’ll see something like:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Each line prefixed with **[Missing Font]** is generated by our **IWarningCallback** implementation, proving that we successfully **detect missing fonts**.

---

## Step 1: Implement the IWarningCallback Interface

Why do we need a custom class? Aspose.Words raises **warnings** for a variety of reasons—file format issues, deprecated features, and, most importantly for us, font substitution. By implementing `IWarningCallback`, we get a hook that receives every warning as it happens. Filtering for `WarningType.FontSubstitution` isolates the specific scenario where a font is missing.

**Pro tip:** If you need to capture *all* warnings for diagnostics, simply remove the `if` check and log every `info.Type`.

---

## Step 2: Wire the Callback into LoadOptions

`LoadOptions` is the gateway that tells Aspose.Words how to treat the incoming document. Setting `WarningCallback` to an instance of our collector ensures the callback is active for the entire load operation. You can reuse the same `LoadOptions` object for multiple documents, which is handy in batch‑processing pipelines.

**Common question:** *What if I load a document without specifying LoadOptions?*  
Answer: Aspose.Words will still raise warnings internally, but without a callback they’re discarded silently, and you lose the chance to **detect missing fonts**.

---

## Step 3: Load a Document and Capture Missing Font Warnings

The `Document` constructor that takes a file path and `LoadOptions` does the heavy lifting. As the file is parsed, any missing font triggers our `FontWarningCollector.Warning` method. The console output proves the mechanism works.

**Edge case:** A single document may reference several absent fonts. The callback fires once per missing font, so you’ll see multiple lines—perfect for building a comprehensive report.

---

## Why Use IWarningCallback Instead of Manual Font Checks?

You could manually scan the document’s `Run.Font` properties after loading, but that would require the document to load successfully first—something that fails if the font is completely unavailable. The warning system works **before** any substitution occurs, giving you a true picture of what’s missing.

Additionally, the callback runs **as part of the loading pipeline**, meaning you can abort early, replace fonts on the fly, or log detailed diagnostics without extra passes over the document tree.

---

## Handling Multiple Missing Fonts Gracefully

If you anticipate many missing fonts, consider aggregating them into a collection:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

After loading, you can iterate over `MissingFonts` and, for example, write them to a CSV file for the design team.

---

## Bonus: Logging Warnings to a File

Console output is fine for demos, but production code usually logs to a persistent store. Replace the `Console.WriteLine` call with something like:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Now you have an audit trail that can be reviewed later, satisfying compliance requirements.

---

## Conclusion

We’ve covered **how to use IWarningCallback** to **detect missing fonts** in Aspose.Words, from implementing the callback to wiring it into `LoadOptions` and handling the resulting warnings. This approach gives you real‑time insight into font‑related issues, letting you log, replace, or alert users before the document is rendered.

Next steps you might explore:

- **Fallback fonts:** programmatically assign a default font when a substitution occurs.  
- **Batch processing:** loop over a folder of documents, reusing the same `AggregatingFontCollector`.  
- **User feedback:** surface missing‑font warnings in a UI rather than the console.

Give it a try in your own project—no more mysterious garbled text, just clear, actionable diagnostics. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}