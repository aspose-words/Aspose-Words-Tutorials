---
category: general
date: 2026-09-08
description: Set tag name and create a content control (SDT) in a Word document using
  C#. Learn how to add SDT, write text to tag, and modify the document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: en
lastmod: 2026-09-08
og_description: Set tag name and create a content control (SDT) in a Word document
  using C#. Follow this step‑by‑step guide to add SDT, write text to tag, and modify
  the document.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Set tag name and add SDT in a Word document – C# guide
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to set tag name and add SDT in a Word document with C#
url: /java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to set tag name and add SDT in a Word document with C#

If you need to **set tag name** for a StructuredDocumentTag (SDT) while working with Word files, this guide shows you exactly how. You’ll see a complete, runnable example that **creates a content control**, writes text to the tag, and **modifies the Word document** end‑to‑end.

Developers often ask, *“how to add sdt* to an existing .docx and then *write text to tag*?” – the answer lies in using the Aspose.Words for .NET API. By the end of this tutorial you will be able to open a Word file, insert a plain‑text SDT, set its tag name, populate it with content, and save the changes without leaving any dangling resources.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later installed.
* A valid Aspose.Words for .NET license (or you can work with the evaluation version).
* Visual Studio 2022 (or any IDE that supports C#).
* An input Word document (`input.docx`) placed in a folder you can reference from code.

## Step 1: Set up the project and import namespaces

Create a new Console App project and add the Aspose.Words NuGet package:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Then, add the necessary `using` directives at the top of `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

These namespaces give you access to `Document`, `DocumentBuilder`, and the `StructuredDocumentTag` class, which are essential for **modifying a Word document**.

## Step 2: Load the existing Word document

The first operation is to load the file you want to edit. This step is required for every scenario where you **modify word document** contents.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Why we load the document first** – The `Document` object represents the entire .docx package in memory. Only after loading can you safely insert new nodes such as an SDT.

## Step 3: Insert a StructuredDocumentTag (SDT) and set its tag name

Now we answer the core question: **how to add sdt** and **set tag name**. We use `DocumentBuilder.InsertStructuredDocumentTag` with `SdtType.PlainText`. The second argument is the tag name, which you can later reference programmatically or via Word’s UI.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Explanation** – `InsertStructuredDocumentTag` returns an `StructuredDocumentTag` instance. By passing `"MyTag"` we **set tag name** directly at creation time. If you need to change it later, you can assign a new value to `sdt.Tag`.

## Step 4: Write text to the newly created tag

After the SDT exists, you typically want to **write text to tag** so that end users see placeholder or default content. The `SetText` method does exactly that.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Why use SetText** – Directly assigning to the `Text` property would replace the whole node hierarchy. `SetText` safely updates the inner text of the content control while preserving its structure.

## Step 5: Save the modified document

Finally, persist the changes to a new file. This completes the **modify word document** workflow.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

When you open `output.docx` in Microsoft Word, you will see a plain‑text content control labeled **MyTag** containing the text “Sample content”. The control can be edited manually, and the tag name remains accessible via Word’s developer tools.

## Full source code

Below is the complete, self‑contained program. Copy it into `Program.cs` and run it; no additional snippets are required.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Expected output in the console

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### What the resulting Word file looks like

![Word document showing a content control named MyTag with the text “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Set tag name example in a Word document"}

*The screenshot illustrates the SDT with the **tag name** set to *MyTag* and the embedded text visible.*

## Common variations and edge cases

| Situation | How to handle it |
|-----------|------------------|
| **Create a rich‑text SDT** | Use `SdtType.RichText` instead of `PlainText`. |
| **Set a different tag name after insertion** | `sdt.Tag = "NewTag";` – you can re‑assign the tag name at any time. |
| **Add the SDT inside a specific paragraph** | Move the builder’s cursor (`builder.MoveToParagraph(index)`) before calling `InsertStructuredDocumentTag`. |
| **Multiple SDTs in the same document** | Repeat steps 3‑4 for each control; each can have a unique tag name. |
| **Working with protected documents** | Ensure the document is unprotected (`doc.Unprotect()`) before inserting an SDT. |

## Pro tips for robust Word automation

* **License early** – Call `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` at the start of `Main` to avoid evaluation watermarks.
* **Dispose objects** – Wrap `Document` in a `using` block if you target .NET Framework to guarantee file handles are released.
* **Validate tag existence** – When reading a document later, use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to locate tags by `Tag` property.
* **Performance** – For large documents, load only required sections using `LoadOptions` with `LoadFormat.Docx` and `LoadFormat.Auto`.  

## Conclusion

You now know how to **set tag name**, **create a content control**, **write text to tag**, and **modify a Word document** using C#. The complete example demonstrates the standard pattern for **how to add sdt** and persist changes safely.  

From here


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Word Document - How to Remove Content](/words/english/net/remove-content/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}