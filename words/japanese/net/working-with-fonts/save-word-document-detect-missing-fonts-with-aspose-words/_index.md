---
category: general
date: 2026-03-22
description: Aspose.Words を使用して Word 文書を保存し、欠落フォントを検出します。C# で欠落フォントを追跡し、フォントエラーを取得する方法を学びましょう。
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: ja
og_description: C#でWord文書を保存し、欠落フォントを検出する。このガイドでは、欠落フォントを追跡し、警告コールバックを使用してフォントエラーを取得する方法を示します。
og_title: Word文書を保存 – Aspose.Wordsで欠落フォントを検出
tags:
- Aspose.Words
- C#
- Document Processing
title: Word文書を保存 – Aspose.Wordsで欠落フォントを検出
url: /ja/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word ドキュメントを保存 – Aspose.Words で欠落フォントを検出

Ever needed to **Word ドキュメントを保存** but weren’t sure whether some of the fonts inside would survive the round‑trip? It happens more often than you think, especially when documents travel between machines with different font libraries. The good news? Aspose.Words gives you a built‑in way to **欠落フォントを検出** while you **Word ドキュメントを保存**, so you can log, warn, or even replace them before the file lands on a user’s screen.

In this tutorial we’ll walk through a complete, ready‑to‑run example that not only saves a Word document but also **欠落フォントを追跡** and **フォントエラーを捕捉** using a custom warning handler. By the end you’ll know exactly why the warning callback matters, how to hook it up, and what the console output looks like when a substitution occurs. No extra fluff—just the code you can drop into a .NET project right now.

> **Prerequisites**  
> • .NET 6 (or any recent .NET Framework) installed  
> • Visual Studio 2022 or your favorite IDE  
> • A licensed copy of **Aspose.Words for .NET** (the free trial works for testing)  

If you’ve got those, let’s get started.

---

## Word ドキュメントを保存して欠落フォントを検出

The core idea is simple: before you call `Document.Save`, assign an object that implements `IWarningCallback` to `Document.WarningCallback`. Aspose.Words will invoke this object for every warning it encounters, including **font substitution** warnings that happen when the source document references a font your system can’t find.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**What you’ll see:**  
If `input.docx` references a font that isn’t installed, the console prints something like:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

That line tells you exactly which font was missing and what Aspose.Words used instead—perfect for **フォントエラーを捕捉** before you ship the file.

---

## Track Missing Fonts with a Warning Callback (Step‑by‑Step)

### 1️⃣ Install Aspose.Words

Open your project’s NuGet console and run:

```bash
dotnet add package Aspose.Words
```

This pulls the latest stable version (currently 24.10). Keeping the library up‑to‑date ensures you get the newest **欠落フォント検出** capabilities and bug fixes.

### 2️⃣ Define the Warning Handler

Why do we need a separate class? Implementing `IWarningCallback` lets you centralise all warning logic in one place. You could also log to a file, send telemetry, or throw an exception if a missing font is a hard error for your workflow.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Pro tip:** If you need to **欠落フォントを追跡** across many documents, store the messages in a `List<string>` inside the handler and expose it later for reporting.

### 3️⃣ Load Your Source Document

The `Document` constructor can accept a file path, a stream, or even raw bytes. In most cases you’ll point it at a `.docx` that you received from a user or another system.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

If the file is large, consider using `LoadOptions` to enable lazy loading, which reduces memory pressure.

### 4️⃣ Attach the Callback

Assign the instance to `doc.WarningCallback`. From this point onward, every warning (including font substitutions) will travel through your handler.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Save the Document

Now you can safely call `Save`. The warning handler runs **synchronously** during the save operation, so you’ll see output immediately.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

If you prefer to save to a different format (PDF, HTML, etc.), the same warning mechanism works—Aspose.Words will still report missing fonts before the conversion.

---

## Capture Font Errors – Common Edge Cases

While the basic flow covers most scenarios, real‑world projects often hit a few snags. Below are some variations you might encounter and how to handle them.

### Missing Font in a Header/Footer

Headers and footers are separate nodes, but the warning system treats them the same as body text. No extra code is needed; the callback will fire for those fonts too. Just make sure you load the full document (the default behavior does this).

### Multiple Substitutions in One Document

If a document uses several unknown fonts, the handler will be called once per substitution. To avoid flooding the console, you could deduplicate messages:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Turning Warnings into Exceptions

Sometimes a missing font is a deal‑breaker. Throw an exception inside the handler to abort the save:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Remember to wrap `doc.Save` in a `try/catch` block to handle the exception gracefully.

---

## Verify the Result – What to Expect

After the save completes, open `output.docx` in Microsoft Word (or any compatible viewer). You should see the same visual layout as the original, but the substituted fonts will appear as the fallback you observed in the console. To double‑check, you can:

1. Open **File → Options → Advanced → Show document content → Use draft quality** – this forces Word to reveal any hidden font substitutions.
2. Use Word’s **Replace Fonts** dialog (`Ctrl+Shift+F`) to see which fonts are actually embedded.

If everything lines up, you’ve successfully **Word ドキュメントを保存** while **欠落フォントを検出** and **フォントエラーを捕捉**. 🎉

---

## Full Working Example (Copy‑Paste Ready)

Below is the entire program you can drop into a new Console App project. Just replace `YOUR_DIRECTORY` with an actual folder path on your machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Expected console output** (example):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

That’s the whole story—no hidden steps, no external docs you have to chase.

---

## 結論

We’ve just shown you how to **Word ドキュメントを保存** while actively **欠落フォントを検出**, **欠落フォントを追跡**, and **フォントエラーを捕捉** using Aspose.Words’ warning callback. By wiring a small `IWarningCallback` implementation, you gain full visibility into font substitutions at save time, giving you the chance to log, replace, or abort as needed.  

Ready for the next challenge? Try extending the handler to write warnings into a structured JSON log, or combine it with Aspose.PDF to convert the same document while preserving font information. You could also explore embedding missing fonts directly into the output file—Aspose.Words supports font embedding via `LoadOptions.FontSettings`.  

Give it a spin, tweak the code to fit your pipeline, and let us know how it works for you. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}