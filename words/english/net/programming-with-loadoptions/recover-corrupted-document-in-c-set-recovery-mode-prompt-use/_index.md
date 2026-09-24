---
category: general
date: 2026-01-11
description: Recover corrupted document in C# using Aspose.Words. Learn how to set
  recovery mode, load docx with recovery, and prompt user on error in a few simple
  steps.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: en
og_description: Recover corrupted document in C# by setting recovery mode, loading
  a DOCX with recovery, and prompting the user on error. Complete step‑by‑step tutorial.
og_title: Recover Corrupted Document in C# – Quick Guide
tags:
- Aspose.Words
- C#
- Document Recovery
title: Recover Corrupted Document in C# – Set Recovery Mode & Prompt User
url: /net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Recover Corrupted Document in C# – Full Guide

Ever tried to open a DOCX that looks fine in Word but throws an exception in your code? You’re probably dealing with a **recover corrupted document** scenario. The good news is Aspose.Words gives you fine‑grained control over how to handle those nasty files—whether you want to silently fix them, throw an exception, or ask the user what to do.

In this tutorial we’ll walk through everything you need to **recover corrupted document** files, from installing the library to choosing the right **set recovery mode** option, **load docx with recovery**, and finally **prompt user on error** when something goes sideways. No fluff, just a complete, runnable example you can drop into any .NET project.

> **Quick preview:** By the end you’ll have a console app that loads a possibly broken `corrupt.docx`, logs any warnings, and asks the user if they want to continue when recovery fails.

---

## What You’ll Need

- **.NET 6.0** or later (the code works on .NET Framework 4.6+ as well).  
- **Aspose.Words for .NET** – install via NuGet (`Install-Package Aspose.Words`).  
- A **corrupt DOCX** file handy for testing (you can deliberately damage a file by opening it in a hex editor or renaming its extension).  
- Any IDE you like—Visual Studio, Rider, or even VS Code will do.

> *Pro tip:* Keep a backup of the original file. Recovery can rewrite parts of the document, and you don’t want to lose the good bits.

---

## Step 1 – Install Aspose.Words and Add Namespaces

First things first. Grab the library from NuGet and bring the required namespaces into scope.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

That’s all you need for the rest of the guide. The `Aspose.Words.Loading` namespace contains the `LoadOptions` class, which is the key to **set recovery mode**.

---

## Step 2 – Choose a Recovery Mode (Primary H2 with Keyword)

### Recover Corrupted Document – Setting the Right Recovery Mode

Aspose.Words offers three recovery behaviours:

| Mode | What Happens | When to Use |
|------|--------------|------------|
| **PromptUser** | Shows a dialog (or you can implement your own prompt) and tries to fix the file. | Ideal for interactive tools where the user can decide. |
| **Silent** | Attempts to fix automatically, no UI. | Good for batch jobs or services. |
| **ThrowException** | Stops processing and throws an exception. | Use when you want strict validation. |

Below is how you **set recovery mode** to `PromptUser`. If you prefer silent handling, just swap the enum value.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Why this matters:** By explicitly **set recovery mode**, you tell Aspose.Words how aggressive it should be. The default is `PromptUser`, but being explicit makes your intent crystal clear—both for future maintainers and for search engines crawling the code.

---

## Step 3 – Load the DOCX with Recovery

Now we’ll **load docx with recovery** using the `LoadOptions` we just configured. If the file is damaged, Aspose.Words will either repair it or raise a warning, depending on the mode.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

The `Document` constructor does the heavy lifting. In **PromptUser** mode, you’ll see a console prompt (or a custom UI if you hook into the `LoadOptions` events) asking whether to continue. In **Silent** mode, the method just tries its best and moves on.

---

## Step 4 – Inspect Warnings and Prompt the User

Aspose.Words records any issues it encounters in the `Warnings` collection. Let’s iterate over them and give the user a chance to decide what to do next.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

The snippet above **prompt user on error** in a console-friendly way. If you’re building a Windows Forms or WPF app, swap the `Console.ReadLine` with a `MessageBox` or custom dialog.

---

## Step 5 – Work With the Recovered Document

At this point the document is in memory, repaired as best as Aspose.Words could. You can now read its contents, save a clean copy, or perform any manipulation you need.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Running the full program against a broken file will produce console output similar to this:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

If the file was actually fine, you’ll see “Document loaded without any warnings.” and the clean copy will be identical to the source.

---

## Full Working Example

Here’s the entire program in one place. Copy‑paste it into a new console project and hit **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Run it, corrupt a test file, and watch the recovery in action. 🎉

---

## Edge Cases & Variations

| Scenario | What to Change | Why |
|----------|----------------|-----|
| **Batch processing** (no user interaction) | Set `RecoveryMode = RecoveryMode.Silent` and remove the console prompt. | Keeps the pipeline moving automatically. |
| **Strict validation** (fail fast) | Use `RecoveryMode.ThrowException`. Wrap the load call in a try/catch and log the exception. | Guarantees you never work with a partially repaired file. |
| **Custom UI** (WinForms/WPF) | Subscribe to `LoadOptions.LoadingProgress` or use `Document.LoadOptions` events to show a dialog. | Provides a richer experience than the console. |
| **Large documents** (memory constraints) | Load with `LoadOptions.LoadFormat = LoadFormat.Docx` and consider `Document.SaveOptions` to stream output. | Prevents OutOfMemory exceptions. |

---

## Practical Tips (E‑E‑A‑T Signals)

- **Always keep a backup** before attempting recovery; the process can overwrite parts of the file.  
- **Log warnings** to a file for later analysis; they often hint at the root cause (e.g., missing parts, corrupted XML).  
- **Test with multiple corruption types** – truncate the file, corrupt XML tags, or change the zip structure to see how each mode behaves.  
- **Upgrade Aspose.Words regularly**; newer versions improve recovery algorithms and add new warning types.  
- **Combine with validation** – after recovery, run a quick `document.UpdateFields()` and `document.Save()` to ensure the document is fully functional.

---

## Conclusion

You now know how to **recover corrupted document** files in C# by **set recovery mode**, **load docx with recovery**, and **prompt user on error** when something goes wrong. The full example demonstrates a clean, end‑to‑end flow that works in console apps, services, or UI projects.

Next steps? Try swapping the console prompt for a modal dialog in a WinForms app, experiment with the **Silent** mode for background jobs, or integrate the recovery logic into an ASP.NET file‑upload endpoint so users can upload broken DOCX files and receive a repaired version instantly.

Happy coding, and may your documents stay whole!  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}