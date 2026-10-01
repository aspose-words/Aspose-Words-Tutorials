---
category: general
date: 2026-09-30
description: Add an ActiveX control word to a Word document using C#. Learn how to
  insert an ActiveX button, add a command button, and make it clickable.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: en
lastmod: 2026-09-30
og_description: Add an ActiveX control word to a Word document with C#. Follow this
  complete guide to insert an ActiveX button, add a command button, and make it clickable.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Add an ActiveX control word to Word documents – step‑by‑step C# guide
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: How to add an ActiveX control word in Word with C#
url: /net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to add an ActiveX control word in Word with C#

If you need to embed an **ActiveX control word** inside a Microsoft Word file, this guide shows you exactly how to do it. You’ll see a complete, runnable example that inserts a clickable button, saves the document, and works with the latest Aspose.Words for .NET.

Adding an ActiveX control word lets you create interactive forms, custom dialogs, or simple UI elements that behave like native Word controls. Whether you’re building a contract template that requires user interaction or a report that needs a “Run” button, the steps below cover everything you need.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later (the code also works with .NET Framework 4.8)
* Visual Studio 2022 (or any IDE that supports C#)
* Aspose.Words for .NET installed (`dotnet add package Aspose.Words`)
* A basic understanding of C# and Word document structure

> **Pro tip:** The `InsertForms2OleControl` method works only with the legacy “Forms 2.0” controls, which are the ActiveX controls Word uses for form fields. If you target newer Office versions, the control still renders correctly in the desktop client.

## Step 1: Set up the project and import namespaces

Create a new console project and add the required `using` statements. This ensures the compiler can find the `Document`, `DocumentBuilder`, and `OleControlType` classes.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

The `Aspose.Words` namespace provides high‑level APIs for Word processing, while `Aspose.Words.Drawing` contains the `OleControlType` enumeration needed to specify the type of ActiveX control.

## Step 2: Load the source Word document

You must start with a Word file that you want to modify. The following code loads `input.docx` from a folder you specify.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

If the file does not exist, Aspose.Words throws a `FileNotFoundException`. Wrap the call in a `try/catch` block if you need graceful error handling.

## Step 3: Create a DocumentBuilder to edit the document

`DocumentBuilder` is the workhorse for inserting text, images, and controls. It maintains a cursor that points to the location where the next element will be placed.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

By default, the builder’s cursor is positioned at the beginning of the first section. You can move it with methods like `MoveToDocumentEnd()` or `MoveToParagraph(index)` if you want the button somewhere else.

## Step 4: Insert an ActiveX CommandButton control

Now comes the core of the tutorial: inserting an **ActiveX control word** that appears as a clickable button. The `InsertForms2OleControl` method takes two arguments—the control type and a caption (or name) for the control.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Why use `OleControlType.CommandButton`?**  
  It tells Word to create a classic Forms 2.0 command button, which displays a caption and can be wired to a macro or VBA script later.

* **What does the caption do?**  
  The string `"ClickMe"` becomes the button’s visible text. You can change it to anything that fits your UI.

### Inserting the button at a specific location

If you need the button after a particular paragraph, move the builder first:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Step 5: Save the modified document

After inserting the control, persist the changes to a new file (or overwrite the original).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

When you open `output.docx` in the desktop version of Word, you’ll see the button labeled **ClickMe** (or **Submit**, depending on the caption you used). Clicking the button in design mode does nothing by default; you can assign a macro later via Word’s “Developer” tab.

## Full, runnable example

Below is a self‑contained program that demonstrates the entire workflow. Copy it into `Program.cs` of a new console app and run it.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Expected output

* The console prints the success message with the output path.
* Opening `output.docx` shows a **ClickMe** button in the location where the builder inserted it.
* The button can be selected, resized, or assigned a macro via Word’s **Developer → Design Mode**.

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| **How to insert an ActiveX button in the header/footer?** | Move the builder to the header/footer with `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` before calling `InsertForms2OleControl`. |
| **What if I need a checkbox instead of a button?** | Use `OleControlType.CheckBox` and provide a caption like `"Agree"`. |
| **Will the button work in Word Online?** | No. Word Online does not support legacy Forms 2.0 ActiveX controls. The button only renders in the desktop client. |
| **Can I set the button’s size programmatically?** | After insertion, retrieve the `Shape` object via `builder.CurrentParagraph.Runs[0].GetShape()` and adjust `Width`/`Height`. |
| **Is there a way to assign a macro from code?** | Aspose.Words does not expose macro editing. You must open the document in Word and attach a macro manually or use the Office Interop API. |

## Tips for production use

* **Avoid hard‑coded paths** – use `Path.Combine` and configuration files.
* **Dispose of `Document`** – wrap it in a `using` statement if you work with large files to free memory promptly.
* **Validate the output** – programmatically check that the document contains a shape of type `OleControl` by iterating `doc.GetChildNodes(NodeType.Shape, true)`.
* **Security note** – ActiveX controls can run code on the client machine. Only distribute documents to trusted users and consider digital signatures.

## Conclusion

You now know how to add an **ActiveX control word** to a Word document using C#. By loading a document, creating a `DocumentBuilder`, inserting a command button with `InsertForms2OleControl`, and saving the file, you can automate the creation of interactive Word forms. Experiment with other `OleControlType` values, place controls in headers or tables, and combine them with macros for richer user experiences.

---

*Next steps*: explore **how to insert ActiveX** controls of other types, learn **how to add command button** event handlers via VBA, and read about **insert ActiveX button** best practices for cross‑platform compatibility.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}