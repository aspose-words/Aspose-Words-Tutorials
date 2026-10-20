---
category: general
date: 2026-02-13
description: Preserve line breaks while you convert DOCX to markdown. Learn how to
  save Word as markdown, export empty paragraphs, and keep formatting intact.
draft: false
keywords:
- preserve line breaks
- convert docx to markdown
- save word as markdown
- how to export empty
- how to preserve breaks
language: en
og_description: Preserve line breaks while converting DOCX to markdown. This guide
  shows how to save Word as markdown and export empty paragraphs correctly.
og_title: 'Preserve Line Breaks: Convert DOCX to Markdown'
tags:
- Aspose.Words
- C#
- Markdown
title: 'Preserve Line Breaks: Convert DOCX to Markdown'
url: /net/programming-with-markdownsaveoptions/preserve-line-breaks-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Preserve Line Breaks: Convert DOCX to Markdown

Ever needed to **preserve line breaks** when you convert a DOCX file to Markdown? It’s a common snag—your beautiful Word document ends up as a wall of text, and those intentional blank lines vanish. The good news? You can keep every line break, even the empty paragraphs, with a few straightforward settings.

In this tutorial we’ll walk through the entire process of **saving Word as Markdown**, covering everything from loading the source document to configuring the right export mode. By the end you’ll know *how to export empty* paragraphs, *how to preserve breaks* in complex layouts, and you’ll have a complete, copy‑paste‑ready code sample. No missing pieces, no “see the docs” dead‑ends.

## What You’ll Learn

- Why preserving line breaks matters for readability and downstream tools.  
- How to **convert DOCX to markdown** using Aspose.Words for .NET.  
- Which `MarkdownSaveOptions` settings control empty paragraph handling.  
- Real‑world tips for handling edge cases like tables, lists, and code blocks.  
- A full, runnable example you can drop into any C# project today.

### Prerequisites

- .NET 6+ (or .NET Framework 4.7.2+) installed.  
- A license for **Aspose.Words for .NET** (the free trial works for this demo).  
- Basic familiarity with C# and the concept of Markdown.  

If you’ve got those covered, let’s dive in.

![Preserve line breaks diagram](preserve-line-breaks.png "Diagram illustrating how empty paragraphs become line breaks in Markdown")

## Preserve Line Breaks – Why It Matters

When a Word document contains intentional blank lines—think of them as visual separators between sections—those blanks often get stripped during conversion. Markdown, by design, treats a single line break as a continuation of the same paragraph, so an empty line must be represented explicitly. If you don’t **preserve line breaks**, your output can look cramped, and downstream parsers (like static site generators) may merge sections unintentionally.

Keeping those breaks isn’t just about aesthetics; it also helps tools that rely on paragraph boundaries for things like footnote placement, custom styling, or even SEO‑friendly heading extraction. In short, a faithful conversion respects the author’s intent.

## Convert DOCX to Markdown with Aspose.Words

Aspose.Words gives you fine‑grained control over the conversion process. The key class is `MarkdownSaveOptions`, which lets you decide how empty paragraphs are exported. Below we’ll set the `EmptyParagraphExportMode` to `EmptyLine`, a mode that translates a blank Word paragraph into an empty Markdown line.

### Step‑by‑Step Implementation

### 1️⃣ Load the Source Document

First, point the library at your `.docx` file. The `Document` constructor does all the heavy lifting—parsing styles, images, and layout information.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Adjust the path to match your environment
string inputPath  = @"C:\Docs\MyReport.docx";
Document doc = new Document(inputPath);
```

> **Why this matters:** Loading the document early gives you access to its internal structure, allowing you to tweak options based on what you discover (e.g., detecting whether the file actually contains empty paragraphs).

### 2️⃣ Configure Markdown Save Options

Here’s where we answer the question **“how to export empty”** paragraphs. The `EmptyParagraphExportMode` enum offers three choices:

| Mode | Result in Markdown |
|------|--------------------|
| `EmptyLine` | Inserts a blank line (`\n\n`). |
| `PreserveLineBreaks` | Turns each line break into a hard break (`  \n`). |
| `None` | Omits the empty paragraph entirely. |

For most scenarios where you simply want a visual gap, `EmptyLine` does the trick.

```csharp
MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
{
    // Export empty paragraphs as a single empty line.
    // This is the most intuitive way to keep visual spacing.
    EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,

    // Optional: keep original line breaks inside paragraphs.
    // Uncomment if you need finer control.
    // PreserveLineBreaks = true
};
```

> **Pro tip:** If you also need to keep manual line breaks (Shift + Enter in Word), set `PreserveLineBreaks = true`. That way, both empty paragraphs and soft breaks survive the round‑trip.

### 3️⃣ Save the Document as Markdown

Now we write the output file. You can choose any folder you like; just make sure the extension is `.md`.

```csharp
string outputPath = @"C:\Docs\MyReport.md";
doc.Save(outputPath, mdOpts);
Console.WriteLine($"✅ Conversion complete! Markdown saved to {outputPath}");
```

That’s the entire pipeline. Run the program, open the `.md` file, and you’ll see blank lines exactly where they existed in the original Word file.

### Full Working Example

Putting it all together, here’s a self‑contained console app you can compile instantly:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source DOCX
        string inputPath = @"C:\Docs\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Set up Markdown options to preserve empty paragraphs
        MarkdownSaveOptions mdOpts = new MarkdownSaveOptions
        {
            EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine,
            // PreserveLineBreaks = true   // Uncomment if you need soft line breaks
        };

        // 3️⃣ Save as Markdown
        string outputPath = @"C:\Docs\WithEmptyParas.md";
        doc.Save(outputPath, mdOpts);

        Console.WriteLine($"✅ Document converted! Check: {outputPath}");
    }
}
```

**Expected output:** Open `WithEmptyParas.md` in any editor. You’ll notice that every blank line from `input.docx` appears as an empty line in the Markdown file, preserving the visual separation you designed.

## Save Word as Markdown – Advanced Scenarios

### Handling Tables and Lists

Tables in Word become Markdown tables automatically, but empty rows can be tricky. If a table row contains only an empty cell, Aspose.Words treats it as an empty paragraph. The `EmptyParagraphExportMode` still applies, so you’ll get a blank line **outside** the table—not inside it. To keep a visual gap *within* the table, insert a non‑breaking space (`&nbsp;`) in the cell.

```csharp
// Example: Adding a placeholder to an empty cell
Table table = doc.GetChild(NodeType.Table, 0, true) as Table;
Cell emptyCell = table.Rows[2].Cells[1];
emptyCell.AppendChild(new Paragraph(doc));
emptyCell.FirstParagraph.AppendChild(new Run(doc, "\u00A0")); // non‑breaking space
```

### Code Blocks and Pre‑Formatted Text

If your DOCX contains pre‑formatted code, Aspose.Words will wrap it in triple backticks. Empty lines inside a code block are preserved automatically, regardless of the `EmptyParagraphExportMode`. However, if you notice missing blank lines, double‑check that the original Word paragraph style is set to “No Spacing”. That way, the library treats each line as a separate paragraph.

### When to Use `PreserveLineBreaks` Instead

Sometimes you need a hard line break (`  `) rather than a full empty paragraph. For instance, poetry or address blocks often rely on single line breaks. Switch the option:

```csharp
mdOpts.PreserveLineBreaks = true;   // Turns soft breaks into Markdown hard breaks
mdOpts.EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.None; // optional
```

Now each `Shift+Enter` in Word becomes `  \n` in Markdown, while truly empty paragraphs disappear (unless you also keep `EmptyLine`).

## How to Export Empty Paragraphs Correctly

The short answer: set `EmptyParagraphExportMode = MarkdownEmptyParagraphExportMode.EmptyLine`. The longer answer involves understanding *why* this works.

- **EmptyParagraphExportMode** tells the serializer *what* to do with a paragraph that contains no runs (text).  
- **EmptyLine** inserts a double newline, which Markdown interprets as a paragraph separator.  
- Other modes either collapse the paragraph (`None`) or treat line breaks as hard breaks (`PreserveLineBreaks`).

If you forget this setting, the default behavior is `None`, and all blank lines vanish—exactly the problem we’re trying to solve.

## How to Preserve Breaks in Complex Documents

Complex documents often mix headings, images, and footnotes. Here’s a checklist to ensure you don’t lose any line breaks:

| Checklist Item | Why It Matters |
|----------------|----------------|
| **Validate empty paragraphs** | Use `doc.GetChildNodes(NodeType.Paragraph, true)` to count blanks before conversion. |
| **Enable `PreserveLineBreaks` for poetry** | Guarantees single line breaks survive. |
| **Check image captions** | Captions are separate paragraphs; they need the same export mode. |
| **Run a post‑conversion diff** | Compare the original text (extracted via `doc.GetText()`) with the Markdown output. |
| **Test with a Markdown viewer** | Some renderers treat multiple blank lines differently; verify the visual result. |

### Sample Validation Code

```csharp
// Count empty paragraphs before saving
int emptyCount = 0;
NodeCollection paragraphs = doc.GetChildNodes(NodeType.Paragraph, true);
foreach (Paragraph p in paragraphs)
{
    if (p.GetText().Trim().Length == 0)
        emptyCount++;
}
Console.WriteLine($"Document contains {emptyCount} empty paragraph(s).");
```

Running this before the save step gives you confidence that the conversion will handle the exact number of line breaks you expect.

## Common Pitfalls & Pro Tips

- **Pitfall:**

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}