---
category: general
date: 2026-01-06
description: Learn how to get warnings while loading documents and how to monitor
  fonts using Aspose.Words. This guide covers warning callbacks and font‑substitution
  tracking.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: en
og_description: How to get warnings in Aspose.Words? Follow this step‑by‑step tutorial
  to monitor fonts and capture substitution messages while loading documents.
og_title: How to Get Warnings in Aspose.Words – Monitor Fonts
tags:
- Aspose.Words
- C#
- Font Monitoring
title: How to Get Warnings in Aspose.Words – Monitor Fonts in C#
url: /net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Get Warnings in Aspose.Words – Monitor Fonts in C#

Ever wondered **how to get warnings** when a Word document contains fonts you don’t have installed? It’s a common snag—your app silently swaps missing fonts, and you never know what changed. The good news is you can hook into Aspose.Words’ warning system and **monitor fonts** in real time.

In this tutorial we’ll show you exactly how to capture those font‑substitution warnings, why it matters, and what to do with the information once you have it. No external docs, just a complete, runnable example you can paste into Visual Studio right now.

> **Pro tip:** If you’re building a document‑conversion pipeline, logging missing fonts early saves you from nasty layout surprises downstream.

---

## What You’ll Need

- **Aspose.Words for .NET** (latest version; the API hasn’t changed since v23.10)
- A .NET development environment (Visual Studio, Rider, or VS Code with the C# extension)
- A sample `.docx` that references a font you don’t have installed (e.g., **“NonExistentFont”**)

That’s it—no extra NuGet packages beyond Aspose.Words.

---

## Step 1 – Set Up a Warning Collector (Primary Keyword in Header)

The first thing you need is a place to store warnings as they happen. Aspose.Words provides the `WarningCallback` property on `LoadOptions` for exactly this purpose.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Why this matters:**  
When the library encounters a missing font, it doesn’t throw an exception; it emits a `WarningInfo` object. By wiring up a collector, you gain full visibility into every substitution event, allowing you to **monitor fonts** without polluting your console with unrelated messages.

---

## Step 2 – Load the Document with the Warning‑Enabled Options

Now we actually read the file. The `LoadOptions` we prepared in the previous step ensure that any font‑related warnings are captured.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**What’s happening under the hood?**  
Aspose.Words parses the Word file, resolves fonts, and whenever it can’t find a requested font, it falls back to a substitute (usually Arial). The fallback triggers a `WarningType.FontSubstitution` warning, which lands in `warningCollector`.

---

## Step 3 – Inspect the Collected Warnings (Primary Keyword Appears Again)

After the document is loaded, we simply iterate over the `warningCollector` and print out any font‑substitution messages.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Expected output** (assuming the missing font is *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

If the document contains multiple unknown fonts, you’ll see one line per substitution—perfect for logging or alerting.

---

## Step 4 – Optional: Log or Persist the Warning Information

In production you probably want more than a `Console.WriteLine`. Here’s a quick example that writes the warnings to a JSON file for later analysis.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Now you have a permanent record you can feed into a monitoring dashboard, or even trigger an automated request for the missing font files.

---

## Step 5 – Verify the Result and Clean Up

Run the program. If you see the substitution messages, you’ve successfully **got warnings** and are now actively **monitoring fonts**. If nothing appears, double‑check that the test document truly references a font that isn’t installed on the machine.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

A count of zero usually means either:

1. All fonts were resolved (maybe the font *is* installed locally), or
2. The document didn’t contain any font references that needed substitution.

---

## Common Pitfalls & How to Avoid Them

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **No warnings appear** | The font actually exists on the system, or the document uses only built‑in fonts. | Rename the font in the source file to something impossible (e.g., `XYZ123`) and try again. |
| **Too many warnings (noise)** | You’re loading many documents in a loop without clearing the collector. | Re‑instantiate `WarningInfoCollection` for each document, or call `warningCollector.Clear()` after processing. |
| **Performance impact** | Excessive logging to disk can slow down batch processing. | Buffer warnings in memory and write them in bulk, or use asynchronous file I/O. |
| **Missing `using Aspose.Words.Loading;`** | The `LoadOptions` class lives in this namespace. | Add the missing `using` directive, as shown in Step 1. |

---

## Extending the Solution – Monitoring Other Warning Types

While font substitution is the most visible, Aspose.Words can emit warnings for:

- **Deprecated features** (`WarningType.Deprecated`),
- **Potential data loss** (`WarningType.DataLoss`),
- **Unsupported file formats** (`WarningType.UnsupportedFileFormat`).

You can broaden the filter in Step 3 to capture these as well:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

That way you’re not just **how to monitor fonts** but also **how to get warnings** for any scenario your application might encounter.

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Run it:** Build the project, execute, and you’ll see the warnings printed and saved. That’s the complete answer to **how to get warnings** and **how to monitor fonts** with Aspose.Words.

---

## Conclusion

You now know **how to get warnings** from Aspose.Words, specifically for font‑substitution scenarios, and you’ve learned **how to monitor fonts** throughout the document‑loading process. By attaching a `WarningCallback`, iterating the collected `WarningInfo` objects, and optionally persisting the data, you gain full transparency over missing‑font events—an essential capability for any document‑processing pipeline.

Next steps? Try expanding the warning filter to cover data‑loss or deprecated‑feature warnings, or integrate the JSON log into a monitoring dashboard like Grafana. The same pattern works for all warning types, so you’ll be well‑equipped to keep an eye on any issue Aspose.Words throws your way.

Happy coding, and may your documents always render exactly as you expect! 

---

<img src="font-warnings.png" alt="how to get warnings in Aspose.Words" style="max-width:100%;">

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}