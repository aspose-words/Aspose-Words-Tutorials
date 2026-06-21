---
category: general
date: 2026-06-20
description: Enable font substitution warnings in C# using Aspose.Words. Learn how
  to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: en
og_description: Enable font substitution warnings in C# with Aspose.Words. This guide
  shows you how to set up LoadOptions, read WarningInfo, and display missing‑font
  messages.
og_title: Enable Font Substitution Warnings in C# – Complete Guide
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Enable Font Substitution Warnings in C# with Aspose.Words
url: /net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enable Font Substitution Warnings in C# with Aspose.Words

Ever wondered how to **enable font substitution warnings** when a Word document references a font that isn’t installed on the server? You’re not the only one. Missing fonts can silently corrupt the layout of generated PDFs or images, and the only way to catch that early is to listen to the warnings Aspose.Words emits.

In this tutorial we’ll walk through a hands‑on example that shows you exactly how to turn those warnings on, pull them out of the `WarningInfo` collection, and print meaningful messages to the console. By the end you’ll know how to configure **Aspose.Words LoadOptions**, handle **C# font substitution warnings**, and keep your document‑processing pipeline bullet‑proof.

We’ll also touch on a few edge cases—what happens if you suppress warnings, or if you need to log them instead of printing—and give you a complete, copy‑and‑paste‑ready code sample that works with the latest Aspose.Words for .NET (as of version 24.10).

## What You’ll Need

- .NET 6.0 or later (the code also works on .NET Framework 4.7+)
- A NuGet reference to `Aspose.Words` (install via `dotnet add package Aspose.Words`)
- A Word file that references a font you **don’t** have installed (e.g., `DocumentWithMissingFont.docx`)
- A decent IDE (Visual Studio, Rider, or VS Code)

That’s it—no extra services, no proprietary tools. Ready? Let’s dive in.

## Step 1: Enable Font Substitution Warnings

The first thing you have to do is tell Aspose.Words that you want to be notified when it substitutes a missing font. This is done through the `FontSettings` property of a `LoadOptions` object. By default, warnings are **disabled** to keep the API quiet, so we have to flip the switch ourselves.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Why this works:** When `FontSettings` is not `null`, the library automatically populates `Document.WarningInfo` with any `WarningType.FontSubstitution` entries it encounters while loading a document. Think of it as turning on a “debug‑mode” for fonts.

## Step 2: Load the Document with Configured Options

Now that the warning collection is active, load your document using the `LoadOptions` we just prepared. If the document contains a missing font, Aspose.Words will substitute a fallback and push a warning into the `WarningInfo` list.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Pro tip:** If you’re processing many files in a loop, reuse the same `LoadOptions` instance—creating it once saves a few milliseconds per iteration.

## Step 3: Iterate Over WarningInfo and Display Font Substitution Messages

Once the document is loaded, the `WarningInfo` collection holds every warning that occurred during the load. We’re only interested in `WarningType.FontSubstitution`, so we filter accordingly.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Running the snippet above against a document that references the missing “Papyrus” font might produce output like:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

That’s the **font substitution messages** you’ve been looking for—clear, actionable, and ready to be logged or sent to an alerting system.

## Full Working Example

Below is a self‑contained console program that puts everything together. Copy‑paste it into a new `.csproj` and hit **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Expected Output

If the document references fonts that aren’t installed, you’ll see something similar to:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

If every font is present on the machine, the program will simply print:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Common Pitfalls & Pro Tips

| Issue | Why It Happens | How to Fix / Avoid |
|-------|----------------|--------------------|
| **Warnings disappear** | You cleared `FontSettings` or used a `LoadOptions` without it. | Always instantiate `FontSettings` even if you don’t modify any properties. |
| **Too many warnings** | The document uses many exotic fonts. | Consider adding a custom font folder to `FontSettings` via `SetFontsFolder` to reduce substitutions. |
| **Performance hit in a tight loop** | Re‑creating `LoadOptions` each iteration adds overhead. | Reuse a single `LoadOptions` instance across all documents. |
| **Missing console output** | Running inside a GUI app where `Console.WriteLine` is ignored. | Redirect warnings to a logger (`ILogger`) or write to a file. |

### Handling Warnings in a Real‑World Service

In a web API you probably don’t want to write to the console. Instead, pipe the warnings into a structured log:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

That way you retain **document warning handling** while keeping your service clean.

## Extending the Example

- **Capture other warning types** (e.g., `WarningType.UnknownFileFormat`) by removing the `if` filter.
- **Save a report** of all warnings to JSON for downstream analytics.
- **Force a specific fallback font** by setting `FontSettings.SubstitutionSettings.DefaultFontName`.

All of these are natural extensions once you’ve mastered **enable font substitution warnings**.

## Conclusion

We’ve shown you how to **enable font substitution warnings** in C# using Aspose.Words, from configuring `LoadOptions` to iterating over `WarningInfo` and printing friendly messages. By following the steps above you can safeguard your document‑processing pipelines against silent layout changes caused by missing fonts.

Next, try adding a custom font folder, logging the warnings to a file, or even sending them to a monitoring dashboard. The same pattern works for any **document warning handling** scenario, whether you’re converting to PDF, rendering images, or performing mail‑merge.

Got questions about **C# font substitution warnings** or want to share a clever workaround? Drop a comment below—happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}