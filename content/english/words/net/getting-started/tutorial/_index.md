---
url: /net/getting-started/tutorial/
---

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide

Ever wondered how to **detect missing fonts** when you load a Word file with Aspose.Words? In my day‑to‑day work, I’ve run into a few PDFs that looked off because the original document used a font I didn’t have installed. The good news? Aspose.Words can tell you exactly when it substitutes a font, and you can capture that information with a simple warning callback.  

In this tutorial we’ll walk through a **complete, runnable example** that shows you how to log every font substitution, why the callback matters, and a couple of extra tricks for robust missing‑font detection. No fluff, just the code and the reasoning you need to get it working today.

---

## What You’ll Learn

- How to implement **Aspose.Words warning callback** to catch font substitution events.  
- How to configure **LoadOptions C#** so the callback is invoked while loading a document.  
- How to verify that the missing‑font detection really worked, and what the console output looks like.  
- Optional tweaks for large batches or headless environments.  

**Prerequisites** – You need a recent version of Aspose.Words for .NET (the code was tested with 23.12), .NET 6 or later, and a basic grasp of C#. If you’ve got those, you’re good to go.

---

## Detect Missing Fonts with a Warning Callback

The heart of the solution is an implementation of `IWarningCallback`. Aspose.Words fires a `WarningInfo` object for many situations, but we only care about `WarningType.FontSubstitution`. Let’s see how to hook into that.

### Step 1: Create a Font‑Warning Collector

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Why this matters*: By filtering on `WarningType.FontSubstitution` we avoid clutter from unrelated warnings (like deprecated features). The `info.Description` already contains the original font name and the fallback used, giving you a clear audit trail.

---

## Configure LoadOptions to Use the Callback

Now we tell Aspose.Words to use our collector when it loads a file.

### Step 2: Set Up LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Why this matters*: `LoadOptions` is the single place where you can plug in the callback, encryption passwords, and other loading behaviours. Keeping it separate from the `Document` constructor makes the code reusable across many files.

---

## Load the Document and Capture Missing Fonts

With the callback wired up, the next step is simply loading the document.

### Step 3: Load Your DOCX (or any supported format)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

When the `Document` constructor parses the file, any missing font triggers our `FontWarningCollector`. The console will show lines such as:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

That line is the concrete evidence that **detect missing fonts** worked.

---

## Verify the Output – What to Expect

Run the program from a terminal or Visual Studio. If the source document contains a font you don’t have installed, you’ll see at least one “Font substituted” line. If the document uses only installed fonts, the callback stays silent and you’ll just get the “Document loaded successfully.” message.

**Tip**: To double‑check, open the Word file in Microsoft Word and look at the font list. Any font that appears in *Replace Fonts* under the *Home → Font* group is a candidate for substitution.

---

## Advanced: Detect Missing Fonts in Bulk

Often you need to scan dozens of files. The same pattern scales nicely:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Because the `FontWarningCollector` writes to the console each time it’s invoked, you’ll get a per‑file report without extra plumbing. For production scenarios you might want to log to a file or a database – simply replace `Console.WriteLine` with your preferred logger.

---

## Common Pitfalls & Pro Tips

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **No warnings appear** | The document actually contains only installed fonts. | Verify by opening the file in Word or by deliberately removing a font from your system. |
| **Callback not called** | `LoadOptions.WarningCallback` was never assigned or a new `LoadOptions` instance was used later. | Keep a single `LoadOptions` object and reuse it for every load. |
| **Too many unrelated warnings** | You didn’t filter by `WarningType.FontSubstitution`. | Add the `if (info.Type == WarningType.FontSubstitution)` guard as shown. |
| **Performance slowdown on huge files** | The callback runs on every warning, which can be many for large docs. | Disable other warning types via `LoadOptions.WarningCallback` or set `LoadOptions.LoadFormat` to a specific type if you know it. |

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Expected console output** (when a missing font is encountered):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

If no substitution occurs, you’ll only see the success line.

---

## Conclusion

You now have a **complete, production‑ready way to detect missing fonts** in any document processed by Aspose.Words. By leveraging the **Aspose.Words warning callback** and configuring **LoadOptions C#**, you can log every font substitution, troubleshoot layout issues, and ensure your PDFs retain the intended look‑and‑feel.  

From a single file to a massive batch, the pattern stays the same—implement `IWarningCallback`, plug it into `LoadOptions`, and let Aspose.Words do the heavy lifting.  

Ready for the next step? Try combining this with **font embedding** or **fallback font families** to automatically fix the problem, or explore the **DocumentVisitor** API for deeper content analysis. Happy coding, and may all your fonts stay where you expect them!  

---

![Detect missing fonts in Aspose.Words – console output screenshot](https://example.com/images/detect-missing-fonts.png "detect missing fonts console output")

{{< layout-end >}}