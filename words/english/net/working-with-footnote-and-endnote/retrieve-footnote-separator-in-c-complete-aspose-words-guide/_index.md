---
category: general
date: 2026-08-07
description: retrieve footnote separator using Aspose.Words for .NET. Learn how to
  extract footnote and endnote separators, inspect node types, and modify them in
  C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: C#
lastmod: 2026-08-07
og_description: retrieve footnote separator with Aspose.Words for .NET. This guide
  shows how to extract footnote and endnote separators, check their node types, and
  save changes.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: retrieve footnote separator in C# – step‑by‑step Aspose.Words tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: retrieve footnote separator in C# – complete Aspose.Words guide
url: /net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# retrieve footnote separator in C# – complete Aspose.Words guide

If you need to **retrieve footnote separator** from a Word document, this tutorial shows you exactly how to do it with Aspose.Words for .NET. Whether you are building a document‑processing service or cleaning up footnote formatting, you’ll see a full, runnable example that extracts both footnote and endnote separators.

In this guide you’ll learn how to load a `.docx` file, call the `FootnoteSeparator` and `EndnoteSeparator` properties, inspect the returned `Node` objects, and optionally replace the separator line. No external documentation is required—everything you need is included below.

## Prerequisites

* .NET 6.0 or later (the code also works on .NET Framework 4.7.2)
* Aspose.Words for .NET NuGet package (version 24.9 or newer)
* A Word document that contains footnotes and/or endnotes (e.g., `Footnotes.docx`)

You can add the Aspose.Words package with the following CLI command:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Step 1: Set up the project and import namespaces

Create a new console project or add the code to an existing one. The required `using` directives are listed below.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

These namespaces give you access to the `Document` class, the `Node` hierarchy, and the `NodeType` enumeration needed for **retrieve footnote separator** operations.

## Step 2: Load the document that contains footnotes and endnotes

The first operation in any Aspose.Words workflow is to load the source file. Replace the placeholder path with the actual location of your `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Loading the file prepares the internal node tree, which is essential for **retrieve footnote separator** because the separator nodes live inside that tree.

## Step 3: Retrieve the footnote separator node

Now you can **retrieve footnote separator** by accessing the `FootnoteSeparator` property of the `Document` object. This node represents the line that separates footnotes from the main body text.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

The `NodeType` will be `Paragraph` for a standard separator line. Knowing the node type helps you decide whether you need to modify the separator or replace it entirely.

## Step 4: Retrieve the endnote separator node

Similarly, you can **retrieve endnote separator** using the `EndnoteSeparator` property. This node separates endnotes from the main content.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Both separator nodes share the same `NodeType` (`Paragraph`) in most documents, but they can be customized independently.

## Step 5: Inspect or modify the separator content (optional)

If you need to change the visual appearance of the separator—such as replacing a line of dashes with a thin rule—you can edit the `Paragraph` node directly. Below is an example that replaces the default separator text with a custom string.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

After modifying the nodes, you can save the document to see the changes reflected in Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Expected console output

When you run the program with the original `Footnotes.docx`, you should see something similar to:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

If you open `Footnotes_Updated.docx` in Microsoft Word, the footnote and endnote separators will display the custom text you inserted.

## Common questions and edge cases

**What if the document has no footnotes?**  
The `FootnoteSeparator` property still returns a `Paragraph` node because Word always includes a separator placeholder. The node will be empty, so you can safely add content or leave it as is.

**Can I retrieve the separator for a specific section?**  
Footnote and endnote separators are document‑wide, not section‑specific. If you need section‑level control, you must work with `Section.FootnoteOptions` and `Section.EndnoteOptions` instead of the global separator nodes.

**Does this work with .NET Core?**  
Yes. Aspose.Words for .NET is cross‑platform, and the same code runs on Windows, Linux, and macOS with .NET 6+.

**What node type should I expect?**  
Both `FootnoteSeparator` and `EndnoteSeparator` return a `Paragraph` node (`NodeType.Paragraph`). If you encounter a different type, the document may be corrupted, and you should reload or validate the source file.

## Full source code for quick copy‑paste

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Copy the code into a `Program.cs` file, adjust the file paths, and run `dotnet run`. The program demonstrates the complete **retrieve footnote separator** workflow, from loading the document to persisting changes.

## Conclusion

You now know how to **retrieve footnote separator** and **endnote separator retrieval** using Aspose.Words for .NET, inspect their `document node type`, and optionally replace their content. This technique lets you automate footnote formatting, generate custom separator lines, or validate document structure in any C# application.

Next, you might explore related topics such as **C# footnote extraction** for individual footnote texts, or learn how to **modify footnote reference marks** using `FootnoteOptions`. Both concepts build directly on the node‑tree fundamentals covered here.

Happy coding, and feel free to experiment with different separator styles to match your project's branding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}