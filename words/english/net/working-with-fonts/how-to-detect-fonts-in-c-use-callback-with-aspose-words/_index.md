---
category: general
date: 2026-03-17
description: How to detect fonts in C# using Aspose.Words and a warning callback.
  Learn how to use callback to capture missing‑font substitutions while loading documents.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: en
og_description: How to detect fonts in C# using Aspose.Words. This guide shows how
  to use callback to capture missing‑font warnings while loading a document.
og_title: How to Detect Fonts in C# – Use Callback with Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: How to Detect Fonts in C# – Use Callback with Aspose.Words
url: /net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Detect Fonts in C# – Use Callback with Aspose.Words

Ever needed **how to detect fonts** in a Word document programmatically and wondered why some characters look odd after conversion? You're not alone. In many real‑world projects—invoice generators, report exporters, or batch‑processing pipelines—missing fonts cause silent layout glitches that are hard to debug.  

The good news? Aspose.Words gives you a clean way to surface those problems with a warning callback. In this tutorial you’ll see **how to use callback** to capture every font substitution Aspose performs while loading a document, and you’ll walk away with a ready‑to‑run example that prints a clear report of missing fonts.

We’ll cover:

* The minimal prerequisites (a .NET project and the Aspose.Words NuGet package).  
* How to implement `IWarningCallback` to listen for `WarningType.FontSubstitution`.  
* How to plug the callback into `LoadOptions` and load a document.  
* What the output looks like, plus a few practical tips for production code.

By the end, you’ll be able to automatically **detect fonts** in any DOCX, DOC, or RTF file and act on missing‑font information—whether that means logging, alerting a user, or substituting a fallback font.

---

![How to detect fonts in a Word document using Aspose.Words warning callback](https://example.com/images/detect-fonts.png "how to detect fonts in a Word document")

## What You’ll Need

* **.NET 6.0** or later (the example compiles with .NET Framework 4.6+ as well).  
* **Aspose.Words for .NET** – install via NuGet: `Install-Package Aspose.Words`.  
* A sample Word file that deliberately references a font you don’t have installed (e.g., `MissingFont.docx`).  

No additional libraries are required; everything lives inside the Aspose namespace.

---

## How to Detect Fonts with a Warning Callback

### Step 1: Create a warning‑callback class

The callback implements `IWarningCallback`. When Aspose.Words encounters a font it can’t find, it raises a `WarningInfo` with `WarningType.FontSubstitution`. Our class simply writes a friendly line to the console.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Why this matters:** By filtering on `WarningType.FontSubstitution` we avoid noisy warnings (like deprecated features) and keep the log focused on the exact problem you’re trying to solve—**detecting fonts** that aren’t present on the machine.

---

### Step 2: Wire the callback into `LoadOptions`

`LoadOptions` lets you customize how a document is parsed. Assigning our `FontWarningCollector` to the `WarningCallback` property tells Aspose to invoke it whenever a missing font is encountered.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Tip:** You can also set `LoadOptions.FontSettings` here if you want to supply a fallback font programmatically. That’s an advanced scenario we’ll mention later.

---

### Step 3: Load the document and watch the output

Now we actually load the file. As soon as Aspose parses the document, any font it can’t locate triggers our callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Expected console output** (assuming the document references *Comic Sans MS* which isn’t installed):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

If the document contains multiple missing fonts, you’ll see one line per font—exactly the **how to detect fonts** information you need.

---

## How to Use Callback for More Complex Scenarios

### Logging to a file instead of the console

In production you probably want a persistent log. Swap `Console.WriteLine` for a `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Collecting warnings for later analysis

Sometimes you need the list of missing fonts after the document is loaded, perhaps to display a UI dialog. Store the warnings in a `List<string>` and expose it:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Providing a fallback font programmatically

If you have a corporate font you want to enforce, you can add it to `FontSettings` before loading:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Now Aspose substitutes missing fonts with *Arial Unicode MS* while still reporting the substitution through the callback. This is a neat way to **how to use callback** for both detection and automatic remediation.

---

## Common Pitfalls and Pro Tips

| Pitfall | Why it Happens | How to Avoid |
|--------|----------------|--------------|
| **Forgetting to reference `Aspose.Words.Warnings`** | The `IWarningCallback` interface lives there. | Add `using Aspose.Words.Warnings;` at the top. |
| **Loading a document without `LoadOptions`** | The default loader silently substitutes fonts with no notification. | Always create a `LoadOptions` instance and assign your callback. |
| **Running on a server with limited permissions** | Writing to a log file may throw `UnauthorizedAccessException`. | Use a write‑able folder (e.g., the app’s data directory) or stick to in‑memory collections. |
| **Multiple threads sharing the same collector** | `FontWarningCollector` isn’t thread‑safe by default. | Create a separate collector per thread or protect the list with a lock. |
| **Assuming the callback fires for embedded fonts** | Embedded fonts are already present in the document; no warning is raised. | If you need to verify embedded font integrity, inspect `FontInfo` via `FontSettings`. |

---

## Full Working Example (Copy‑Paste Ready)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**What you should see** (assuming the file references two absent fonts):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

If the file uses only installed fonts, the console simply prints:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Wrapping Up

We’ve walked through **how to detect fonts** in a Word document by wiring a custom warning callback into Aspose.Words. The approach is lightweight, requires

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}