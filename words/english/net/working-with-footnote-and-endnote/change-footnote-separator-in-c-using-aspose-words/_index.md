---
category: general
date: 2026-08-04
description: Change footnote separator in C# using Aspose.Words – learn how to edit
  footnote separator and change endnote separator in Word documents.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: en
lastmod: 2026-08-04
og_description: Change footnote separator in C# with Aspose.Words. This guide shows
  you how to edit footnote separator, customize endnote separator, and save the updated
  document.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Change footnote separator in C# – complete Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Change footnote separator in C# using Aspose.Words
url: /net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Change footnote separator in C# using Aspose.Words

If you need to **change footnote separator** in a Word document, this tutorial walks you through the exact steps with Aspose.Words for .NET. Whether you want to replace the default line with a symbol, or apply a different style to endnote separators, the code below covers the full workflow.

You’ll also learn how to **edit footnote separator** and the related **change endnote separator** operation, so the same document can have consistent styling for both footnotes and endnotes. No external tools are required—just a few lines of C#.

## What you’ll achieve

By the end of this guide you will be able to:

* Load an existing *.docx* file that contains footnotes and endnotes.  
* Access the separator nodes for footnotes, footnote continuations, and endnotes.  
* Replace the separator character (for example, change the default line to an asterisk).  
* Save the modified document without losing any other content.  

The tutorial assumes you have a basic understanding of C# and have installed the **Aspose.Words** NuGet package (version 24.9 or later).  

---

## Prerequisites

| Requirement | Reason |
|-------------|--------|
| .NET 6.0+ or .NET Framework 4.7.2+ | Required runtime for Aspose.Words |
| Aspose.Words for .NET library | Provides the `Document` and `FootnoteOptions` APIs |
| An input Word file (`input.docx`) with at least one footnote or endnote | Demonstrates the separator change |

You can add Aspose.Words to your project with the following CLI command:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Step 1: Load the document containing footnotes

The first operation is to read the source file into a `Document` object. This object represents the entire Word file in memory and gives you access to all its nodes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Why this matters:** Loading the document is the entry point for any manipulation. If the file cannot be found, Aspose.Words throws a `FileNotFoundException`, so ensure the path is correct before proceeding.

---

## Step 2: Access the footnote and endnote separator nodes

`Document.FootnoteOptions` exposes three separator nodes:

* `Separator` – the line that appears after the footnote collection on the first page.  
* `ContinuationSeparator` – the line used when footnotes continue onto the next page.  
* `EndnoteSeparator` – the line that separates the main text from the endnote list.

You retrieve these nodes as generic `Node` objects, then cast them to `Run` to modify the text.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Why this matters:** These nodes are the only places where the visual separator character lives. Changing any other node (e.g., a regular paragraph) will not affect the footnote formatting.

---

## Step 3: Change the footnote separator character

The most common requirement is to replace the default line with a symbol such as an asterisk (`*`). Because the separator is stored as a `Run`, you can safely modify its `Text` property.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Why this matters:** Directly editing the `Run.Text` updates the visual representation in the final document without affecting other footnote content. The same pattern can be used to apply any string, including Unicode symbols.

---

## Step 4: Change the endnote separator (optional)

If you also need to **change endnote separator**, the process mirrors the footnote change. Replace the text of `endnoteSeparator` with your desired character.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Why this matters:** Endnotes are often styled differently from footnotes. Providing a separate separator lets you maintain visual consistency with your document’s design guidelines.

---

## Step 5: Save the modified document

After all modifications, persist the changes using `Document.Save`. You can overwrite the original file or write to a new location.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Why this matters:** `Save` writes the in‑memory representation to disk, preserving all other elements (styles, images, tables) unchanged.

---

## Full, runnable example

Putting all the pieces together, here is a self‑contained console application that demonstrates the entire workflow:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Expected result:** Open *ModifiedSeparators.docx* in Microsoft Word. The footnote separator line at the bottom of the first footnote page will now be a single asterisk (`*`). If the document contains endnotes, the line separating the main text from the endnote list will appear as a dash (`-`). All other content (text, images, tables) remains untouched.

---

## Common questions & edge‑case handling

| Question | Answer |
|----------|--------|
| **What if the document has no footnotes?** | `FootnoteOptions.Separator` still returns a `Run` node, but its text may be empty. The code safely checks the node type before modifying it. |
| **Can I use a multi‑character string (e.g., "***")?** | Yes. The `Run.Text` property accepts any string, including Unicode characters. |
| **Will changing the separator affect existing footnote numbering?** | No. The separator is independent of the numbering scheme. |
| **Do I need to dispose of the `Document` object?** | `Document` implements `IDisposable` implicitly via `Node`. In a short‑lived console app it's optional, but for long‑running services you can wrap it in a `using` block. |
| **How does this work with .NET Core vs .NET Framework?** | The API is identical across runtimes; only the target framework version matters (must be supported by the Aspose.Words package). |

**Pro tip:** If you need to apply different separators for different sections, you can iterate through `doc.GetChildNodes(NodeType.Footnote, true)` and adjust each footnote’s `Separator` property individually. This is more advanced but useful for complex documents.

---

## Conclusion

You now know how to **change footnote separator** and **change endnote separator** in a Word file using Aspose.Words for C#. The guide covered loading the document, accessing the relevant separator nodes, modifying their text, and saving the result—all in a single, self‑contained program.

From here you can explore related topics such as **edit footnote separator style**, customizing footnote numbering, or applying conditional formatting based on page layout. The same pattern (retrieve a node, cast to `Run`, modify `Text`) works for many other Word‑processing scenarios.

Happy coding, and feel free to experiment with different symbols or even embed images as separators for a truly unique document layout!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}