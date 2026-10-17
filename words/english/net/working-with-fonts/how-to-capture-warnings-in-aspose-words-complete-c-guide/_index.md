---
category: general
date: 2026-03-28
description: How to capture warnings when loading a DOCX with Aspose.Words and get
  warning messages for missing fonts. Learn to handle missing fonts efficiently.
draft: false
keywords:
- how to capture warnings
- get warning messages
- handle missing fonts
- Aspose.Words warning callback
- font substitution warning
language: en
og_description: How to capture warnings when loading a DOCX with Aspose.Words, get
  warning messages, and handle missing fonts with practical code examples.
og_title: How to Capture Warnings in Aspose.Words – Complete C# Guide
tags:
- Aspose.Words
- C#
- Document Processing
title: How to Capture Warnings in Aspose.Words – Complete C# Guide
url: /net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Capture Warnings in Aspose.Words – Complete C# Guide

Ever wondered **how to capture warnings** that pop up when you load a Word document with Aspose.Words? Maybe you’re seeing strange font changes and you need to know exactly why. In short, you can hook into the library’s warning system, **get warning messages**, and even **handle missing fonts** before they ruin your layout.  

In this tutorial we’ll walk through a real‑world scenario: loading a DOCX, collecting every warning that the engine emits, and printing out details about any font substitution that occurs. By the end you’ll have a ready‑to‑run code sample, understand the “why” behind each step, and know how to extend the approach for your own projects.

## What You’ll Learn

- How to configure `LoadOptions` so that warnings are captured automatically.  
- The exact way to **get warning messages** from the `WarningInfoCollection`.  
- How to identify and react to **missing fonts** via the `WarningType.FontSubstitution` flag.  
- Tips for troubleshooting edge cases, such as documents with embedded fonts or custom font folders.  

No external references needed – everything you need is right here.

---

## Prerequisites

- .NET 6.0 or later (the code also works on .NET Framework 4.7+).  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`).  
- A sample DOCX (`input.docx`) that either lacks some fonts or uses fonts not installed on your machine.  

That’s it. If you’re already comfortable with C# and Visual Studio, you can copy‑paste the code and run it immediately.

---

## Step 1: Prepare Load Options and a Warning Callback

The first thing Aspose.Words does when you call `new Document(path, loadOptions)` is parse the file. During parsing it may encounter missing fonts, unsupported features, or deprecated markup. To catch those events you need a **warning callback** object.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Create a collection that will hold all warnings.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Step 2: Wire the collection into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    // The library will push every warning into this collection.
    WarningCallback = warningCollector
};
```

**Why this matters:** Without a callback, Aspose.Words silently logs warnings to the console (or discards them), leaving you blind to font substitutions that could affect layout. By providing a dedicated `WarningInfoCollection`, you gain full visibility.

> **Pro tip:** If you only care about font‑related warnings, you can filter later – but collecting *all* warnings gives you a safety net for future issues.

---

## Step 2: Load the Document with the Configured Options

Now that the callback is ready, load the file. The `Document` constructor will automatically invoke the callback for any problems it finds.

```csharp
// Step 3: Load the DOCX while capturing warnings.
string filePath = @"YOUR_DIRECTORY/input.docx";
Document doc = new Document(filePath, loadOptions);
```

**What’s happening under the hood?** Aspose.Words parses the Open XML, resolves styles, and attempts to map each font reference to a system‑installed font. If a match isn’t found, it creates a `WarningInfo` entry of type `FontSubstitution`.

---

## Step 3: Retrieve and Inspect the Collected Warnings

After the load completes, your `warningCollector` now contains every warning that occurred. Let’s pull them out and focus on font substitution messages.

```csharp
// Step 4: Iterate through the collected warnings.
foreach (WarningInfo warning in warningCollector)
{
    // Only interested in font‑substitution warnings?
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {warning.Description}");
    }
}
```

**Sample output** (your console might show something like):

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

If you want *all* warnings, simply remove the `if` check or log `warning.Type` for each entry.

---

## Step 4: Handling Missing Fonts – Beyond Just Logging

Capturing warnings is useful, but often you need to **handle missing fonts** programmatically. Here are two common strategies:

### 4.1 Replace Missing Fonts with a Specific Fallback

```csharp
// Define a fallback font that you know is available.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";

// Apply the settings before loading (or after, if you reload).
loadOptions.FontSettings = fontSettings;
```

Now any missing font will be swapped with *Calibri* instead of the library’s default fallback.

### 4.2 Embed a Substitute Font Dynamically

If you have a custom font file (e.g., `MyFallback.ttf`) you can register it at runtime:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", true); // true = recursive search
loadOptions.FontSettings = fontSettings;
```

This approach is handy when you distribute a specific corporate font with your application.

> **Edge case:** Documents that already embed the required font will ignore the system substitution rules. In that scenario, the warning collection will be empty for that font, which is exactly what you want.

---

## Step 5: Full Working Example (Copy‑Paste Ready)

Below is a self‑contained program that demonstrates everything from start to finish. Just replace `YOUR_DIRECTORY/input.docx` with the path to your test file.

```csharp
// ------------------------------------------------------------
// Complete example: Capture warnings and handle missing fonts
// ------------------------------------------------------------
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();

        // 2️⃣ Configure LoadOptions with the collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = warningCollector
        };

        // OPTIONAL: Set a global fallback font (e.g., Calibri).
        FontSettings fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Calibri";
        loadOptions.FontSettings = fontSettings;

        // 3️⃣ Load the document.
        string filePath = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ Process warnings – focus on font substitution.
        Console.WriteLine("=== Font Substitution Warnings ===");
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"⚠️ {warning.Description}");
            }
        }

        // 5️⃣ (Optional) Save the document to verify that the fallback was applied.
        string outPath = @"YOUR_DIRECTORY/output.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**What to expect**

- The console prints every font‑substitution warning, prefixed with a warning emoji for visibility.  
- The output DOCX (`output.docx`) uses *Calibri* wherever a missing font was detected.  
- No unhandled exceptions – the warning system gracefully handles any unknown font.

---

## Common Questions & Answers

**Q: Will this work with PDFs generated from Word?**  
A: Yes. Aspose.Words treats PDFs as another output format. The warning capture happens during the *load* phase, so it’s independent of the final export.

**Q: What if I need to capture warnings for **all** document operations (save, convert, etc.)?**  
A: You can reuse the same `WarningInfoCollection` by assigning it to `Document.WarningCallback` after the document is instantiated. Every subsequent operation will push new entries into the same collection.

**Q: Does the warning callback affect performance?**  
A: Negligibly. The collection simply stores objects; unless you’re processing thousands of warnings in a tight loop, you won’t notice any slowdown.

**Q: How do I suppress warnings I don’t care about?**  
A: Implement a custom class that inherits `IWarningCallback` and filter inside the `Warning` method. The built‑in `WarningInfoCollection` only stores, it doesn’t filter.

---

## Pro Tips & Pitfalls

- **Pro tip:** Always inspect the `Warning.Description` – it contains the exact font name that was missing. This can help you decide whether to ship the font with your app.  
- **Watch out for embedded fonts:** If the source DOCX already embeds the needed font, Aspose.Words will not emit a substitution warning, even if the font isn’t installed locally.  
- **Thread safety:** `WarningInfoCollection` isn’t thread‑safe. If you load multiple documents concurrently, give each thread its own collection.  
- **Version check:** The warning API has been stable since Aspose.Words 20.8. Make sure you’re on a recent version to avoid missing newer warning types.

---

## Conclusion

We’ve covered **how to capture warnings** from Aspose.Words, demonstrated how to **get warning messages**, and shown practical ways to **handle missing fonts** through fallback fonts or custom font folders. The full example is ready to drop into any .NET project, and the concepts scale to larger automation pipelines.

Next, you might explore:

- Using `Document.WarningCallback` to capture warnings during **save** operations.  
- Logging warnings to a file or telemetry system for production monitoring.  
- Extending the callback to automatically replace missing fonts with brand‑specific typefaces.

Feel free to experiment—swap the fallback font, add more documents to the batch, or integrate the warning collector into a CI pipeline that flags font‑related regressions. Happy coding, and may your documents always render exactly as you expect!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}