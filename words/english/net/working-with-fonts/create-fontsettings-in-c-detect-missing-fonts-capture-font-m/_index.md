---
category: general
date: 2026-03-01
description: Create FontSettings in C# to detect missing fonts, capture font messages,
  and handle missing fonts with Aspose.Words. Step‑by‑step guide for developers.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: en
og_description: Create FontSettings in C# to detect missing fonts, capture font messages,
  and handle missing fonts using Aspose.Words. Complete tutorial with code.
og_title: Create FontSettings in C# – Detect Missing Fonts & Capture Font Messages
tags:
- Aspose.Words
- C#
- Font Management
title: Create FontSettings in C# – Detect Missing Fonts & Capture Font Messages
url: /net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create FontSettings in C# – Detect Missing Fonts & Capture Font Messages

Ever needed to **create FontSettings** in a .NET project but weren’t sure how to spot fonts that aren’t installed on the target machine? You’re not alone. In many real‑world apps—think automated report generators or document converters—missing fonts can silently break layout, and you won’t know until the PDF looks wonky.  

What if you could **detect missing fonts**, **capture font messages**, and **handle missing fonts** before they ruin your output? The good news is that Aspose.Words makes this a piece of cake. In this tutorial we’ll walk through the entire process, from setting up the `FontSettings` object to wiring a warning callback that tells you exactly which glyphs were substituted.

> **TL;DR:** By the end you’ll have a ready‑to‑run C# console app that logs every font substitution, letting you decide whether to embed a replacement or alert the user.

---

## Prerequisites

- .NET 6 SDK (or any recent .NET version)  
- Visual Studio 2022 or VS Code with C# extensions  
- An Aspose.Words for .NET license (free trial works for this demo)  
- A sample DOCX that references a font you don’t have installed (e.g., *Comic Sans MS* on a Linux box)  

No special NuGet packages beyond `Aspose.Words` are required.

---

## Step 1 – Install Aspose.Words and Set Up the Project

First things first, create a new console project and bring the Aspose.Words library into the mix.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Pro tip:** If you already have a solution, just add the package via the NuGet Package Manager UI—makes version tracking easier.

---

## Step 2 – Create FontSettings (Primary Keyword Appears Here)

The **create FontSettings** step is the cornerstone of any font‑related workflow. `FontSettings` tells Aspose.Words where to look for fonts, whether to use system folders, and how to fall back when something is missing.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Why is this important? Without a properly configured `FontSettings`, the engine silently substitutes missing glyphs with the default system font, and you’ll never see a warning.

---

## Step 3 – Wire Up LoadOptions with the FontSettings

`LoadOptions` lets you pass the `FontSettings` into the document loader. This is the bridge that lets the engine **detect missing fonts** during the `Document` construction phase.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Now every time you load a DOCX with `loadOptions`, Aspose.Words will consult the `FontSettings` we set up earlier.

---

## Step 4 – Attach a Warning Callback to **Capture Font Messages**

Aspose.Words emits warnings for a variety of conditions—font substitution being a common one. By providing an implementation of `IWarningCallback`, you can **capture font messages** in real time.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### The Warning Handler Class

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

The `info.Description` field contains a human‑readable message such as *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* This is exactly the kind of output you need to **handle missing fonts** gracefully.

---

## Step 5 – Load the Document and Let the Callback Do Its Job

With everything wired, loading the document is straightforward. If the source file references a font absent from the system, our warning handler will fire.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

When you run the program, you’ll see console output similar to:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

That output is the **capture font messages** part of our workflow. You can extend the handler to log to a file, send telemetry, or even abort the conversion if critical fonts are missing.

---

## Step 6 – Full Working Example (All Pieces Together)

Below is a complete, copy‑paste‑ready program. Paste it into `Program.cs`, adjust the file paths, and hit `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Expected Output

Running the program on a machine that lacks *Comic Sans MS* will print something like:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

You’ll also end up with `Result.pdf` that uses the substituted fonts, ensuring the conversion never crashes.

---

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if I want the conversion to fail instead of substituting?** | Inside `FontSubstitutionWarningHandler`, throw an exception when `info.Description` contains a critical font name. |
| **Can I embed a replacement font automatically?** | Yes. After detecting a missing font, you can load a fallback `FontInfo` from a known path and add it to `fontSettings` via `fontSettings.SetFontsFolder`. |
| **Does this work on Linux/macOS?** | Absolutely. `FontSettings` works cross‑platform; just make sure the fallback folder contains the appropriate `.ttf` or `.otf` files. |
| **Is the warning callback thread‑safe?** | The callback runs on the same thread that loads the document, so you don’t need extra synchronization for console logging. For multi‑threaded scenarios, guard shared resources. |
| **How do I log warnings to a file?** | Replace `Console.WriteLine` with `File.AppendAllText("font_warnings.log", ...)` or use any logging framework (Serilog, NLog). |

---

## Pro Tips for Production‑Ready Font Handling

1. **Cache Font Lookups** – Re‑using the same `FontSettings` instance across multiple document loads avoids repeated filesystem scans.  
2. **Whitelist Critical Fonts** – If your brand requires a specific font, verify its presence early and abort with a clear error message.  
3. **Use `SetFontFolder` Recursively** – Setting `recursive: true` ensures subfolders are scanned, which is handy when you ship a whole font collection.  
4. **Combine with `FontSubstitutionSettings`** – You can fine‑tune substitution rules (e.g., prefer fonts with the same family name).  

---

## Conclusion

We’ve just **created FontSettings**, configured `LoadOptions` to **detect missing fonts**, attached a callback that **captures font messages**, and demonstrated how to **handle missing fonts** in a clean, production‑ready way. The entire flow fits into a few dozen lines of C#, yet it gives you full visibility into the font landscape of any DOCX you process.

Next, you might explore:

- **Embedding fallback fonts** directly into the output PDF (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** based on corporate branding rules.  
- **Integrating with a CI pipeline** to automatically flag documents that use unauthorized fonts.

Give it a spin, tweak the warning handler to suit your needs, and let your document pipelines run with confidence—no more mysterious layout glitches caused by invisible font swaps.

Happy coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}