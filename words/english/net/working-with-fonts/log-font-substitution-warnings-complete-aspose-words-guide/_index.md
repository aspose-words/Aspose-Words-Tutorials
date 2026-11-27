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

- How to configure `LoadOptions` so Aspose.Words records font‑substitution warnings.  
- The exact steps to **detect missing fonts** during document load.  
- A clean way to **capture missing fonts** and write them to your own log or monitoring system.  
- Edge‑case handling (e.g., when a document contains a font that isn’t installed on the server).  

### Prerequisites

- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).  
- A valid Aspose.Words for .NET license (or the free trial).  
- Basic familiarity with C# and console applications.  

If you already have those, let’s dive in.

## Step 1 – Set Up LoadOptions and a Warning Collector

Aspose.Words uses a `WarningInfoCollection` to store warnings that occur while loading a document. By assigning this collection to `LoadOptions.WarningCallback` you can retrieve detailed font‑substitution information after the document is loaded.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words;   // contains WarningInfo, WarningInfoCollection, etc.

class Program
{
    static void Main()
    {
        // Step 1: Create a WarningInfoCollection to collect warnings.
        var warningCollector = new WarningInfoCollection();

        // Create LoadOptions and attach the collector.
        var loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };
```

## Step 2 – Load the Document

With the warning collector in place, load the document as usual. All font‑substitution warnings will be stored in `warningCollector`.

```csharp
        // Step 2: Load the target document while the warning collector is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);
```

## Step 3 – Process the Collected Font‑Substitution Warnings

After loading, iterate through the collected warnings, filter for `FontSubstitutionWarningInfo`, and log the details you need.

```csharp
        // Step 3: Examine the collected warnings.
        foreach (WarningInfo info in warningCollector)
        {
            if (info.WarningType == WarningType.FontSubstitution && info is FontSubstitutionWarningInfo fsw)
            {
                // Log to console – replace with your own logger if needed.
                Console.WriteLine($"Missing font: {fsw.RequestedFamilyName} – substituted with {fsw.ResolvedFont.FullFontName}");
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

## Step 4 – Handling Edge Cases and Advanced Scenarios

### 4.1 When No Substitution Happens

If the document only uses fonts that are already present, the warning collector will remain empty and no output will be produced. That indicates your environment already has all required fonts.

### 4.2 Capturing Warnings for Later Analysis

If you need to store the warnings for a nightly report, collect them in a list:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        foreach (WarningInfo info in warningCollector)
        {
            if (info.WarningType == WarningType.FontSubstitution && info is FontSubstitutionWarningInfo fsw)
            {
                missingFonts.Add((fsw.RequestedFamilyName, fsw.ResolvedFont.FullFontName));
                Console.WriteLine($"Missing font: {fsw.RequestedFamilyName} – substituted with {fsw.ResolvedFont.FullFontName}");
            }
        }

        // Serialize `missingFonts` to JSON, write to a database, or email a summary as needed.
```

### 4.3 Working with Other Document Types

The same `LoadOptions` approach works for loading DOCX, DOC, RTF, and other formats supported by Aspose.Words. Simply pass the same `loadOptions` instance to the `Document` constructor for the format you are loading.

## Step 5 – Verify the Result Programmatically

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
| Forgetting to assign a `WarningCallback` | Without a callback the warnings are not collected. | Assign a `WarningInfoCollection` to `LoadOptions.WarningCallback` as shown in Step 1. |
| Using `Console.WriteLine` in a web app | Console output disappears in IIS/ASP.NET Core. | Switch to a persistent logger (e.g., Serilog). |
| Loading a document with a relative path | The working directory may differ at runtime. | Use absolute paths or `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignoring the `ResolvedFont` information | You lose insight into which fallback was chosen. | Always log both `RequestedFamilyName` and `ResolvedFont.FullFontName`. |

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

We’ve covered everything you need to **log font substitution warnings** when loading Word documents with Aspose.Words. By configuring `LoadOptions`, attaching a warning collector, and processing the results, you can reliably **detect missing fonts** and understand **how to capture missing fonts** for any .NET project.

Take the code, tweak the logger to fit your stack, and you’ll never be surprised by a silent font swap again. Next steps might include:

- Integrating the warning list with your CI/CD pipeline to fail builds when critical fonts are missing.  
- Extending the approach to monitor font usage across a fleet of documents.  
- Exploring Aspose.Words’ `FontSettings` API to provide custom fallback fonts.

Got questions or a tricky scenario? Drop a comment, and let’s troubleshoot together. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}