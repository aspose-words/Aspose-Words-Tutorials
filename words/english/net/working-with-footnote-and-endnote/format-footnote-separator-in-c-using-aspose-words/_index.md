---
category: general
date: 2026-08-10
description: Format footnote separator in C# with Aspose.Words to customize footnote
  and endnote lines. Learn C# footnote formatting in minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: en
lastmod: 2026-08-10
og_description: Format footnote separator in C# using Aspose.Words. Follow this tutorial
  to style footnote and endnote separators quickly and reliably.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Format footnote separator in C# – complete Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Format footnote separator in C# using Aspose.Words
url: /net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Format footnote separator in C# using Aspose.Words

If you need to **format footnote separator** in a Word document, this guide shows you how to do it with Aspose.Words for .NET. You’ll see a complete, runnable example that changes the alignment and color of the separator paragraph, and you’ll learn how to apply the same technique to endnote separators.

The tutorial covers every step—from loading the source file to saving the modified document—so you can copy‑paste the code into your own project without additional research.

## What you’ll need

Before you start, make sure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.6+)
* A valid Aspose.Words for .NET license (the free trial works for evaluation)
* A Word file that contains at least one footnote or endnote (e.g., `Footnotes.docx`)
* Visual Studio 2022 or any C# IDE you prefer

Having these items ready lets you focus on the **C# footnote formatting** logic instead of environment setup.

## Step 1: Load the document that contains footnotes and endnotes

The first operation is to create a `Document` object that points to your source file. Aspose.Words reads the entire DOCX package into memory, giving you full access to footnote and endnote nodes.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Why this matters*: Loading the document is the prerequisite for any manipulation. If the file path is wrong, Aspose.Words throws a `FileNotFoundException`, so verify the path before proceeding.

## Step 2: Retrieve the separator and continuation‑separator nodes

Footnote and endnote separators are stored as special nodes inside the `Footnotes` and `Endnotes` collections. Each collection exposes `Separator` and `ContinuationSeparator` properties that return a `Node` reference.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Why this matters*: The `Separator` node represents the line that visually separates the main text from the footnote block. By obtaining a reference, you can modify its paragraph format, font, or even replace the node entirely.

## Step 3: Change the visual style of the footnote separator

In most Word documents the separator is a single paragraph that contains a dash or an asterisk. The code below checks whether the separator is a `Paragraph` and, if so, centers it and changes its text color to gray.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Styling the continuation separator (optional)

The continuation separator appears when a footnote spans multiple pages. You can style it similarly:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Why this matters*: Aligning the separator improves readability, and changing the color distinguishes it from regular paragraph text. You can replace `ParagraphAlignment.Center` with `Left` or `Right` to match your document’s design guidelines.

## Step 4: Save the modified document

After applying the desired style, write the document back to disk. You can overwrite the original file or create a new version.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

When you open `Footnotes_Styled.docx` in Microsoft Word, the footnote separator appears centered and gray, exactly as the code specified.

## Advanced variations

### Formatting the endnote separator

If your document also uses endnotes, you can apply the same logic to the `Endnotes` collection:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Using a custom string for the separator

Sometimes you want the separator to be a series of asterisks (`***`). Replace the existing runs with a new run:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Handling documents without a separator node

A rare edge case is a document that omits the separator node (e.g., when the author deleted it). In that scenario `document.Footnotes.Separator` returns `null`. Guard against it:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Common pitfalls and how to avoid them

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Separator is not a `Paragraph`** | Some Word templates use a `Table` or `Shape` as a separator. | Check the node type with `is Paragraph` before casting. |
| **`Runs` collection is empty** | The separator may be an empty paragraph. | Verify `Runs.Count > 0` before accessing `Runs[0]`. |
| **License not applied** | Without a license, Aspose.Words inserts a watermark and may limit API usage. | Call `License license = new License(); license.SetLicense("Aspose.Words.lic");` at the start of your program. |
| **Saving to a read‑only folder** | The `Save` method throws an `UnauthorizedAccessException`. | Ensure the target directory has write permissions. |

Addressing these issues early prevents runtime exceptions and ensures a smooth **modify footnote separator** experience.

## Complete, runnable example

Below is a self‑contained console application that demonstrates every step discussed above. Copy the code into a new .NET console project, replace the file paths, and run it.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Expected result**  

When you open `Footnotes_Styled.docx`:

* The footnote separator line is centered beneath the main text.
* Its color appears as a light gray, making it visually distinct.
* If the document contains endnotes, their separators are also centered and colored gray (or slate


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}