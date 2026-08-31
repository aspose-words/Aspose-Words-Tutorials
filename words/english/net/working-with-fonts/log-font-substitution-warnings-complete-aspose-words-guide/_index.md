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

## Step 1 – Set Up LoadOptions to Raise Typed Warnings

The heart of the solution lies in `LoadOptions.FontSubstitutionWarning`. By switching it to `RaiseTypedWarnings` you tell Aspose.Words to fire an event **every time** it can’t find the exact font you asked for.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Why this matters:**  
> The default behavior silently swaps a missing font with the closest match, which can lead to layout glitches you never see coming. Raising typed warnings gives you full visibility.

## Step 2 – Subscribe to the Warning Event

Now we hook into `loadOptions.FontSubstitutionWarning`. The lambda receives an `e` object that tells us exactly which font was missing and which one was used instead.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** If you run this on a web server, replace `Console.WriteLine` with a structured logger (Serilog, NLog, etc.) so you can query the data later.

## Step 3 – Load the Document Using the Configured Options

With the warning mechanism in place, simply load the document as you normally would. The event fires automatically for every missing font.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

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

Sometimes a document only uses system fonts that are already present. In that case the warning event never fires, and you’ll get a clean console with no output. That’s a good sign—your environment already has all required fonts.

### 4.2 Capturing Warnings for Later Analysis

If you need to store the warnings for a nightly report, collect them in a list:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

After loading, you can serialize `missingFonts` to JSON, write to a database, or email a summary.

### 4.3 Working with PDFs or Other Formats

The same `LoadOptions` approach works for `Load` calls on PDFs, RTF, and even HTML files. Just pass the same options instance, and Aspose.Words will raise warnings for any font it can’t match.

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
| Forgetting to set `RaiseTypedWarnings` | The default is `DoNotRaise`, so no events fire. | Explicitly set `FontSubstitutionWarning` as shown in Step 1. |
| Using `Console.WriteLine` in a web app | Console output disappears in IIS/ASP.NET Core. | Switch to a persistent logger (e.g., Serilog). |
| Loading a document with a relative path | The working directory may differ at runtime. | Use absolute paths or `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignoring the `SubstitutedFontName` | You lose insight into which fallback was chosen. | Always log both `FontName` and `SubstitutedFontName`. |

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

We’ve covered everything you need to **log font substitution warnings** when loading Word documents with Aspose.Words. By configuring `LoadOptions`, subscribing to the warning event, and optionally persisting the results, you can reliably **detect missing fonts** and understand **how to capture missing fonts** for any .NET project.

Take the code, tweak the logger to fit your stack, and you’ll never be surprised by a silent font swap again. Next steps might include:

- Integrating the warning list with your CI/CD pipeline to fail builds when critical fonts are missing.  
- Extending the approach to monitor font usage across a fleet of documents.  
- Exploring Aspose.Words’ `FontSettings` API to provide custom fallback fonts.

Got questions or a tricky scenario? Drop a comment, and let’s troubleshoot together. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}