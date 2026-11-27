---
category: general
date: 2026-01-14
description: Log font substitution warnings while loading Word documents with Aspose.Words.
  Learn to detect missing fonts and how to capture missing fonts in C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: en
og_description: Log font substitution warnings while loading Word documents with Aspose.Words.
  Discover how to detect missing fonts and capture missing fonts in C#.
og_title: Log Font Substitution Warnings – Complete Aspose.Words Guide
tags:
- Aspose.Words
- C#
- Document Processing
title: Log Font Substitution Warnings – Complete Aspose.Words Guide
url: /net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Log Font Substitution Warnings – Complete Aspose.Words Guide

Log font substitution warnings is essential when you need to guarantee that a Word document looks exactly the same after it’s loaded by Aspose.Words. If you’ve ever wondered how to **detect missing fonts** or want to know **how to capture missing fonts**, you’re in the right place.  

In this tutorial we’ll walk through a real‑world scenario, show you the complete C# code, and explain why each line matters. By the end you’ll be able to log every font substitution event and act on it—no mystery warnings left behind.

![Log font substitution warnings example](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## What You’ll Learn

- How to configure `LoadOptions` so Aspose.Words raises typed warnings for font substitution.  
- The exact steps to **detect missing fonts** during document load.  
- A clean way to **capture missing fonts** and write them to your own log or monitoring system.  
- Edge‑case handling (e.g., when a document contains a font that isn’t installed on the server).  

### Prerequisites

- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).  
- A valid Aspose.Words for .NET license (or the free trial).  
- Basic familiarity with C# and console applications.  

If you already have those, let’s dive in.

## Step 1 – Set Up LoadOptions and a Warning Callback

Aspose.Words does not expose a `FontSubstitutionWarning` event. Instead, you collect warnings through a `WarningInfoCollection` assigned to `LoadOptions.WarningCallback`. When a missing font is encountered, Aspose.Words adds a `FontSubstitutionWarningInfo` object to this collection.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1: Create a WarningInfoCollection to receive warnings.
        var warningCollector = new WarningInfoCollection();

        // Step 2: Configure LoadOptions to use the collector.
        var loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };
```

> **Why this matters:**  
> By attaching a `WarningInfoCollection`, you get strongly‑typed warning objects (including font‑substitution details) instead of generic messages.

## Step 2 – Load the Document and Process Font‑Substitution Warnings

Now load the document with the configured `LoadOptions`. After loading, iterate over the collected warnings, filter for `WarningType.FontSubstitution`, and log the details. The `FontSubstitutionWarningInfo` class provides the original font name, whether bold/italic were requested, and the font that was actually used.

```csharp
        // Step 3: Load the document while the warning collector is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Step 4: Process the collected warnings.
        var missingFonts = new List<(string Requested, string Substituted)>();

        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution &&
                warning is FontSubstitutionWarningInfo fontWarning)
            {
                string requested = fontWarning.RequestedFamilyName;
                string substituted = fontWarning.ResolvedFont?.FamilyName ?? "unknown";

                // Log to console – replace with your own logger if needed.
                Console.WriteLine($"Missing font: {requested} – substituted with {substituted}");

                missingFonts.Add((requested, substituted));
            }
        }

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Expected Console Output

If `input.docx` references a font called *MyFancyFont* that isn’t installed, you’ll see:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Each line corresponds to a **detect missing fonts** event, giving you a complete audit trail.

## Step 3 – Handling Edge Cases and Advanced Scenarios

### 3.1 When No Substitution Happens

If the document only uses fonts that are already present on the server, the warning collection will remain empty and no console output will appear. That’s a good sign—your environment already has all required fonts.

### 3.2 Persisting the Warning List

You can serialize `missingFonts` to JSON, write it to a database, or email a summary for later analysis:

```csharp
// Example: serialize to JSON (requires System.Text.Json)
string json = System.Text.Json.JsonSerializer.Serialize(missingFonts);
System.IO.File.WriteAllText(@"YOUR_DIRECTORY\missing-fonts.json", json);
```

### 3.3 Working with PDFs or Other Formats

The same `LoadOptions` approach works for PDFs, RTF, HTML, and other supported formats. Just pass the same `loadOptions` instance to the appropriate `Document` constructor.

## Step 4 – Verify the Result Programmatically

If you prefer an automated test instead of eyeballing the console, assert that the list contains expected entries:

```csharp
// Simple verification (use a testing framework in real projects)
if (missingFonts.Count == 0)
{
    Console.WriteLine("All fonts were available – no substitution warnings.");
}
else
{
    Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
}
```

This snippet demonstrates **how to capture missing fonts** in code, not just in logs.

## Common Pitfalls & How to Avoid Them

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| Forgetting to assign `WarningCallback` | Without a callback the library silently substitutes fonts. | Set `loadOptions.WarningCallback = new WarningInfoCollection();` as shown in Step 1. |
| Using `Console.WriteLine` in a web app | Console output disappears in IIS/ASP.NET Core. | Switch to a persistent logger (e.g., Serilog, NLog). |
| Loading a document with a relative path | The working directory may differ at runtime. | Use absolute paths or `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignoring the `ResolvedFont` property | You lose insight into which fallback was chosen. | Always log both `RequestedFamilyName` and `ResolvedFont.FamilyName` (or “unknown” if null). |

## Bonus: Automating Font Installation

If you control the deployment environment, you can pre‑install the missing fonts using a PowerShell script:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Running this before your application starts eliminates most **detect missing fonts** warnings altogether.

## Conclusion

We’ve covered everything you need to **log font substitution warnings** when loading Word documents with Aspose.Words. By configuring `LoadOptions`, using a `WarningInfoCollection`, and optionally persisting the results, you can reliably **detect missing fonts** and understand **how to capture missing fonts** for any .NET project.

Take the code, adapt the logger to fit your stack, and you’ll never be surprised by a silent font swap again. Next steps might include:

- Integrating the warning list with your CI/CD pipeline to fail builds when critical fonts are missing.  
- Extending the approach to monitor font usage across a fleet of documents.  
- Exploring Aspose.Words’ `FontSettings` API to provide custom fallback fonts.

Got questions or a tricky scenario? Drop a comment, and let’s troubleshoot together. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}