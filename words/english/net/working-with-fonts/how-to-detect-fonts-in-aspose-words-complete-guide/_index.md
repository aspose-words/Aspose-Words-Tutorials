---
category: general
date: 2026-04-21
description: Learn how to detect fonts, capture warnings, configure callback, and
  enumerate warnings with Aspose.Words in C#. Step‑by‑step guide for reliable font
  handling.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: en
og_description: How to detect fonts in Aspose.Words? This tutorial shows you how to
  capture warnings, configure a callback, and enumerate warnings in C#.
og_title: How to Detect Fonts in Aspose.Words – Complete Guide
tags:
- Aspose.Words
- C#
- Document Processing
title: How to Detect Fonts in Aspose.Words – Complete Guide
url: /net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Detect Fonts in Aspose.Words – Complete Guide

Ever wondered **how to detect fonts** that are missing when you load a Word document? It’s a scenario that pops up more often than you’d like, especially when dealing with legacy files or cross‑platform deployments. In this tutorial we’ll walk through a complete, runnable example that **captures warnings**, **configures a callback**, and **enumerates warnings** so you always know which fonts were substituted.

We’ll be using Aspose.Words for .NET (v24.9 at the time of writing) and plain C#. No external services, no magic—just the API and a few lines of code. By the end you’ll be able to spot every font substitution, log it, and even decide whether to abort the load if a critical font is missing.  

### What You’ll Need
- **Aspose.Words for .NET** (install via NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 or later (the code works on .NET Framework too)
- A sample DOCX that references a font not present on the machine (e.g., “MyCustomFont.ttf”)
- Visual Studio, Rider, or any C# editor you prefer

> **Pro tip:** If you don’t have a document with missing fonts, simply rename a font file on your system or edit the DOCX XML to reference a non‑existent font family.

---

## How to Detect Fonts with Aspose.Words

The core idea is to hook into Aspose.Words’ warning system. When the library can’t find a requested font, it emits a `WarningType.FontSubstitution` warning. By providing a custom `IWarningCallback` implementation, you can **detect fonts** that were swapped out during the load process.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Why this works:** Aspose.Words calls the `Warning` method for every non‑critical issue. By storing the `WarningInfo` objects you get full access to the type, message, and context, which is exactly what you need to **detect fonts** that were substituted.

---

## How to Capture Warnings When Loading a Document

Now that we have a collector, we need to tell the `LoadOptions` to use it. This is the **how to capture warnings** part of the puzzle.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Edge case:** If you load a document from a stream (`new Document(stream, loadOptions)`), the same callback works—just pass the stream instead of a file path.

At this point the document is fully loaded, but any font substitution warnings are safely stored inside `warningCollector.Warnings`.

---

## How to Enumerate Warnings and Report Font Substitutions

Finally, we sift through the collected warnings and **enumerate warnings** that are specifically about font substitution. This step turns raw data into a readable report.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Expected output** (example):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

If the document contains no missing fonts, the loop simply produces no output—nothing to worry about.

---

## Full Working Example (All Steps in One File)

Below is the complete program you can copy‑paste into a console project. It ties together **how to detect fonts**, **how to capture warnings**, **how to configure callback**, and **how to enumerate warnings** in a single, cohesive flow.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Running this program** will print every font that Aspose.Words had to replace. You can redirect the output to a log file, raise an alert, or even abort loading if a critical font is missing.

---

## Common Questions & Gotchas

### What if I need to stop loading when a required font is missing?
You can inspect the `WarningInfo` objects inside the callback and throw an exception when a particular font name appears. The exception will abort the load, giving you full control.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Does this work with PDFs or other formats?
Yes. Aspose.Words uses the same warning infrastructure for PDFs, RTF, and HTML. Just replace the file extension and the rest of the code stays identical.

### How can I log warnings to a file instead of the console?
Replace `Console.WriteLine` with any logging framework you prefer (`Serilog`, `NLog`, etc.). The `WarningInfo` class exposes `Message`, `Source` and `Exception` for detailed logs.

### Will this impact performance?
The overhead is negligible—Aspose.Words already generates the warnings internally. Adding a callback simply stores them in a list, which is O(n) in the number of warnings. For typical documents, the impact is far below 1 % of total load time.

---

## Visual Summary

![How to Detect Fonts in Aspose.Words – warning flow diagram](https://example.com/images/font-detection-diagram.png "how to detect fonts")

*Alt text:* **how to detect fonts** – diagram showing warning callback, collection, and enumeration steps.

---

## Wrap‑Up

We’ve covered **how to detect fonts** in Aspose.Words by **capturing warnings**, **configuring a callback**, and **enumerating warnings**. The complete code sample shows a production‑ready pattern you can drop into any .NET application.  

Next, you might want to explore:

- **How to capture warnings** for other issues (e.g., image conversion problems)
- **How to configure callback** for custom logging frameworks
- **How to enumerate warnings** across multiple documents in a batch job
- Using **Aspose.Words.Fonts.FontSettings** to provide fallback font folders, which can reduce the number of substitutions in the first place.

Give it a try, tweak the collector to fit your logging style, and you’ll never be surprised by an unexpected font swap again. If you run into any quirks, drop a comment below—happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}