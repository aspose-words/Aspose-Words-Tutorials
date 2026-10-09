---
category: general
date: 2026-03-19
description: Learn how to capture warnings in Aspose.Words, set default font settings,
  and detect missing fonts when loading a Word document.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: en
og_description: How to capture warnings in Aspose.Words, set default font settings,
  and detect missing fonts when loading a Word document.
og_title: How to Capture Warnings – Set Default Font Settings
tags:
- Aspose.Words
- C#
- Document Processing
title: How to Capture Warnings – Set Default Font Settings
url: /net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Capture Warnings – Set Default Font Settings

**How to capture warnings** is a common need when you work with Aspose.Words, especially if your documents rely on specific fonts that might not be present on the target machine. Ever opened a DOCX and wondered why the layout looked off? The answer is often hidden in a warning about a missing font.  

In this guide we’ll walk through **how to capture warnings** while you **load word document**, configure **set default font settings**, and finally **detect missing fonts** so you can react programmatically. No fluff—just a complete, runnable example and the reasoning behind each line.

> *Pro tip:* Capturing warnings early saves you from debugging mysterious layout glitches later.

---

## What You’ll Need

- **Aspose.Words for .NET** (latest version as of 2026).  
- A .NET development environment (Visual Studio, Rider, or VS Code).  
- A sample DOCX that references a font you *don’t* have installed (e.g., *Comic Sans MS* on a Linux box).  

That’s it. No additional NuGet packages are required beyond Aspose.Words.

---

## Step 1 – Understand Why You Need to Capture Warnings

When Aspose.Words parses a document, it may encounter fonts that are unavailable on the host. By default the library silently substitutes a fallback font, which can change line breaks, spacing, and even cause text to disappear.  

Using the **WarningCallback** together with a **FontSettings** object gives you two things:

1. **Visibility** – you get a `WarningInfo` entry for every substitution.  
2. **Control** – you can pre‑configure a default font to minimise visual surprises.

Think of it as installing a “watchdog” that shouts every time the engine swaps a part under the hood.

---

## Step 2 – Set Default Font Settings

The first secondary keyword, **set default font settings**, appears right here. You create a `FontSettings` instance and optionally point it at a folder that contains your fallback fonts.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Why?**  
> If you don’t specify a fallback, Aspose.Words picks the first system font that matches the style, which may be wildly different. By setting a known default, you guarantee consistent rendering across machines.

---

## Step 3 – Prepare a Warning Callback to Capture Warnings

Now we’ll **how to capture warnings** by attaching a `WarningInfoCollection` to the load options. This collection will store every warning emitted during the load process.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

The `WarningInfoCollection` implements `IWarningCallback`, so Aspose.Words automatically pushes each warning into `warningInfos`. No polling required.

---

## Step 4 – Load Word Document with the Configured Options

Here’s where the second secondary keyword, **load word document**, shines. We pass both the `FontSettings` and the `WarningCallback` through a `LoadOptions` instance.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

If the document references a font that isn’t installed, the warning callback will capture a `WarningType.FontSubstitution` entry.

---

## Step 5 – Detect Missing Fonts from Collected Warnings

Finally, we answer the third secondary keyword, **detect missing fonts**, by iterating over the collected warnings.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Typical output looks like:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

That line tells you exactly which font is missing and which fallback was used—information you can log, display to the user, or even trigger a custom font‑install routine.

---

## Complete Runnable Example

Below is the full program you can copy‑paste into a console application. It demonstrates **how to capture warnings**, **set default font settings**, **load word document**, and **detect missing fonts** all in one flow.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Expected result:** When the specified DOCX references a font that isn’t installed, the console prints a warning for each substitution. If all fonts are present, the loop produces no output.

---

## Common Pitfalls & Edge Cases

| Situation | Why it Happens | How to Handle It |
|-----------|----------------|------------------|
| **No warnings appear** even though the layout looks wrong | The document may be using *embedded* fonts, which Aspose.Words renders without substitution. | Check `Document.HasEmbeddedFonts` and consider extracting the embedded fonts if you need them on another machine. |
| **Multiple warnings for the

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}