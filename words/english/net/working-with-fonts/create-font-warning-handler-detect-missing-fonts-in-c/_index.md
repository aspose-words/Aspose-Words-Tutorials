---
category: general
date: 2026-02-12
description: Create Font warning handler to detect missing fonts and track missing
  fonts in Aspose.Words. Learn how to log warnings efficiently.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: en
og_description: Create Font warning handler in C# to detect missing fonts and learn
  how to log warnings when Aspose.Words substitutes fonts.
og_title: Create Font Warning Handler – Detect Missing Fonts
tags:
- Aspose.Words
- C#
- Document Processing
title: Create Font Warning Handler – Detect Missing Fonts in C#
url: /net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Font Warning Handler – Detect Missing Fonts in C#

Ever needed to **create font warning handler** because a Word document silently swapped out a font you didn't expect? You're not the only one. When Aspose.Words loads a DOCX that references a font absent on the server, it silently falls back to a default font—leaving your layout subtly broken.  

In this tutorial we’ll show you exactly how to **detect missing fonts**, **track missing fonts**, and **how to log warnings** so you can spot those substitutions before they bite you. By the end you’ll have a reusable warning handler that prints every font‑substitution event to the console (or any logger you prefer). No mystery, just clear, actionable code.

## Prerequisites

- .NET 6.0 or later (the API is the same for .NET Framework 4.6+)
- Aspose.Words for .NET installed (`dotnet add package Aspose.Words`)
- A Word file that references a font not installed on your machine (e.g., `MissingFont.docx`)

If you already have those, great—let’s jump in.

## Step 1: Set Up LoadOptions with a Warning Callback  

The first thing you do when you want to **create font warning handler** is tell Aspose.Words to fire a callback whenever it encounters a problem. `LoadOptions` is the container for that configuration.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Why this matters:**  
`LoadOptions` is the only place you can plug in an `IWarningCallback`. Without it, Aspose.Words will log warnings internally but you’ll never see them. By assigning `FontWarningHandler` we gain full control over what happens when a missing font is substituted.

## Step 2: Implement the FontWarningHandler Class  

Now we actually **create font warning handler** code. The class implements `IWarningCallback` and receives a `WarningInfo` object for every warning Aspose.Words raises.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Explanation:**  
- `info.Type` tells us the category of the warning. We care about `WarningType.FontSubstitution` because that’s what indicates a missing font.
- `info.Description` contains a human‑readable message like *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- By writing to `Console.WriteLine` we **log warnings** instantly. In a real‑world app you might replace that with `ILogger`, a file writer, or a telemetry service.

> **Pro tip:** If you need to collect all missing fonts for later reporting, store `info.Description` in a `List<string>` instead of printing it.

## Step 3: Load the Document Using the Configured LoadOptions  

With the callback in place, loading a document will automatically trigger our handler whenever a font is missing.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**What you’ll see:**  
Running the program prints something similar to:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

That line confirms you have successfully **detected missing fonts** and are now **tracking missing fonts** in real time.

## Step 4: Verify the Handler Works with Different Scenarios  

It’s easy to assume the handler works only for DOCX files, but Aspose.Words supports many formats. Try loading a PDF that references an embedded font, or an older `.doc` file. The same callback fires for any format that goes through the font‑resolution pipeline.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

If the PDF references a font that isn’t installed, you’ll get the same console output. This demonstrates that your **create font warning handler** solution is format‑agnostic.

## Step 5: Extending the Handler – Logging to a File  

Console output is handy for demos, but production code usually writes to a log file. Here’s a quick tweak.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Now every time a font is substituted, the message gets appended to `font-warnings.log`. This satisfies the **how to log warnings** part of the brief and gives you a persistent audit trail.

## Step 6: Putting It All Together – Full, Runnable Example  

Below is the complete program you can copy‑paste into a console app. No pieces are missing; just replace the file path with your own document.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Expected outcome:**  

- The console prints each substitution line.  
- `font-warnings.log` now contains a timestamped record of every missing‑font event.  
- The `output.pdf` file is created using the substituted fonts, ensuring the conversion succeeds even when the original fonts are unavailable.

## Common Questions & Edge Cases  

| Question | Answer |
|----------|--------|
| *What if I want to ignore certain fonts?* | Inside `Warning`, check `info.Description` for the font name and `return;` early for fonts you consider acceptable. |
| *Will the handler fire for embedded fonts?* | No—embedded fonts are always available to the document, so no substitution warning occurs. |
| *Can I capture other warning types (e.g., image‑resolution issues)?* | Absolutely. Remove the `if (info.Type == WarningType.FontSubstitution)` guard or add additional `if` blocks for `WarningType.ImageResolution`. |
| *Is the handler thread‑safe?* | The default implementation shown writes to a file without synchronization. For multi‑threaded scenarios, wrap file writes in a lock or use a concurrent logger. |

## Next Steps  

Now that you know **how to log warnings** for missing fonts, you might want to:

- **Detect missing fonts** during a batch import process and generate a summary report.  
- **Track missing fonts** across multiple documents and send an email alert when a particular font appears frequently.  
- **Integrate with a monitoring system** (e.g., Azure Application Insights) to surface font‑substitution trends over time.  

All of these extensions build on the same `IWarningCallback` foundation we created.

---

*Happy coding! If you run into quirks—maybe a custom font folder or a network share—drop a comment below. The community (and I) are always happy to help you fine‑tune your font‑warning strategy.* 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}