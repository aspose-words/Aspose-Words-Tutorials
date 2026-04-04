---
category: general
date: 2026-04-04
description: Learn how to capture warnings, detect missing fonts, and how to log substitution
  events using Aspose.Words LoadOptions in C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: en
og_description: How to capture warnings, detect missing fonts, and how to log substitution
  events using Aspose.Words LoadOptions in C#.
og_title: How to Capture Warnings in C# – Detect Missing Fonts & Log Substitution
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: How to Capture Warnings in C# – Detect Missing Fonts & Log Substitution
url: /net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Capture Warnings in C# – Detect Missing Fonts & Log Substitution

Ever wondered **how to capture warnings** that pop up when you load a Word document with missing fonts? You’re not alone. In many real‑world projects, fonts get lost during migration, and the silent fallback can break your layout. The good news? Aspose.Words gives you a clean way to listen for those warnings, detect missing fonts, and even log every substitution so you can fix the source later.

In this tutorial we’ll walk through a complete, ready‑to‑run solution that shows **how to capture warnings**, demonstrates **detect missing fonts**, and explains **how to log substitution** events. By the end, you’ll have a reusable warning handler, a fully configured `LoadOptions` object, and a sample console output you can verify.

> **Prerequisite:** You need Aspose.Words for .NET (v24.x or later) installed via NuGet and a basic C# development environment (Visual Studio 2022 or VS Code works fine).

---

## How to Capture Warnings When Loading Documents

The core of the solution is a class that implements `IWarningCallback`. Aspose.Words calls this callback automatically for every warning generated during document loading, including font substitution warnings.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Why this step?**  
> By filtering on `WarningType.FontSubstitution` we avoid clutter from unrelated warnings (like deprecated features). This makes the log focused on the exact problem you care about—missing fonts.

---

## Detect Missing Fonts with Aspose.Words

When a document references a font that isn’t installed on the machine, Aspose.Words substitutes the nearest match and raises a warning. Our handler above will catch each occurrence, effectively **detect missing fonts**.

To see it in action, we need to configure `LoadOptions` and attach the handler:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** If you prefer to collect warnings for later processing (e.g., write to a file), replace `Console.WriteLine` with code that adds the message to a `List<string>`.

---

## How to Log Substitution Events

Logging is as simple as directing the warning output to a persistent store. Below is a quick example that writes each substitution warning to a text file named `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Why log to a file?**  
> Persistent logs let you audit font issues across multiple runs, automate alerts, or feed the data into a build‑pipeline check.

---

## Full Working Example

Putting everything together, here’s a self‑contained console application you can copy, paste, and run. It demonstrates **how to capture warnings**, **detect missing fonts**, and **how to log substitution** in one go.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Expected Console Output

If `input.docx` references a font that isn’t installed, you’ll see something like:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

If you switched to `FileLoggingWarningHandler`, the same lines will appear inside `font-warnings.log` with timestamps.

![how to capture warnings console output](image-placeholder.png)

---

## Common Questions & Edge Cases

### What if I need to capture *all* warnings, not just font substitution?

Simply remove the `if (info.Type == WarningType.FontSubstitution)` check. The callback will receive every warning type (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, etc.). You can then branch on `info.Type` to handle each case differently.

### Does this work with PDFs or only Word documents?

`LoadOptions` and `IWarningCallback` are part of Aspose.Words, so they apply to Word‑compatible formats (`.docx`, `.doc`, `.rtf`, `.html`). For PDFs you’d use Aspose.PDF’s own warning mechanisms.

### How can I suppress warnings instead of logging them?

Set `LoadOptions.WarningCallback = null` or implement the callback but leave the method body empty. The library will still perform the substitution silently.

### What about thread‑safety?

The callback instance is invoked on the same thread that loads the document, so you don’t need extra synchronization unless you share the handler across parallel loads. In that case, protect shared resources (e.g., the log file) with a lock or use concurrent collections.

---

## Conclusion

We’ve covered **how to capture warnings** from Aspose.Words, shown you how to **detect missing fonts**, and explained **how to log substitution** events for later analysis. By plugging a simple `IWarningCallback` implementation into `LoadOptions`, you gain full visibility into font‑related issues without cluttering your codebase.

Next steps? Try extending the logger to send emails, integrate with Azure Monitor, or automatically install missing fonts on a build server. You might also explore other warning types—`WarningType.DegradedDocument` can alert you to features that didn’t survive the conversion process.

Got more questions about font handling or Aspose.Words in general? Drop a comment or fire up a new issue on the Aspose forums. Happy coding, and may your documents always render with the right typeface!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}