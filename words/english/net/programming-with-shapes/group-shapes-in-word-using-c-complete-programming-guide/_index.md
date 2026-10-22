---
category: general
date: 2026-10-13
description: group shapes in Word with C# – learn how to group shapes and add shapes
  to group using Aspose.Words in a few easy steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: en
lastmod: 2026-10-13
og_description: group shapes in Word using C# and Aspose.Words. Follow this guide
  to learn how to group shapes and add shapes to group in a Word document.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Group shapes in Word with C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Group shapes in Word using C# – complete programming guide
url: /net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Group shapes in Word using C# – complete programming guide

If you need to **group shapes in Word** programmatically, this guide shows you exactly how. By the end of the first two sentences you’ll know the required code, the reasoning behind each step, and how to **add shapes to group** without surprises.

We’ll cover everything from loading a `.docx` file to saving the updated document. The tutorial assumes you have basic C# knowledge and a reference to the Aspose.Words for .NET library. No external documentation is required—just copy, paste, and run.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.7+)
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- A Word document (`input.docx`) that already contains at least two shapes (e.g., pictures, AutoShapes)

> **Pro tip:** If you’re testing, create a simple Word file with two rectangles via the Word UI. Save it as `input.docx` in a folder you control.

## Group shapes in Word – step‑by‑step guide

Below we break the process into five logical steps. Each step includes the exact C# code, an explanation of *why* the line is needed, and a short note on common pitfalls.

### Step 1: Load the Word document

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Why:** `Document` is the entry point for any Word manipulation. Providing the full file path loads the document into memory, allowing us to query and modify its node tree.

**Pitfall:** Passing a relative path can fail when the working directory differs. Use an absolute path or `Path.Combine` with `AppContext.BaseDirectory`.

### Step 2: Retrieve the shapes you want to group

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Why:** `GetChild` walks the document tree and returns the *n‑th* node of the requested type. Setting `isDeep` to `true` searches the entire document, not just the current section.

**Edge case:** If the document contains fewer than two shapes, `firstShape` or `secondShape` will be `null` and an exception will be thrown when we try to cast. Guard against this:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Step 3: Create a new `GroupShape` container

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Why:** `GroupShape` acts as a parent node that can hold multiple `Shape` objects. It inherits from `Shape`, so it can be inserted anywhere a regular shape is allowed (e.g., inside a paragraph).

### Step 4: Add the individual shapes to the group

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Why:** `AppendChild` moves the shapes from their original locations into the new group. After this call the original shapes no longer exist as independent nodes; they become part of `groupShape`.

**Tip:** Grouping automatically adjusts the relative positions of the child shapes. If you need a specific layout, set the `GroupShape.Bounds` property *before* appending children.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Step 5: Insert the group shape into the document body

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Why:** A `GroupShape` must be placed inside a paragraph (or a table cell) to be rendered. By appending it to the first paragraph we guarantee visible placement without disrupting existing layout.

### Step 6: Save the modified document

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Why:** `Save` writes the in‑memory changes back to a `.docx` file. You can also save to a stream or to PDF by changing the overload.

**Result verification:** Open `output.docx` in Microsoft Word. You should see the two original shapes now combined into a single grouped object. Selecting the group will show the standard Word grouping handles.

## How to group shapes programmatically – deeper insights

- **Node ownership:** When you call `AppendChild`, the shape’s `ParentNode` reference changes automatically. This prevents “orphaned” nodes that could corrupt the document.
- **Preserving formatting:** Grouping does **not** lose any shape formatting (fill color, line style, etc.). All child shapes retain their original properties.
- **Nested groups:** `GroupShape` can contain other `GroupShape` objects, enabling multi‑level hierarchies. Just treat the inner group as any other shape.

## Add shapes to group and manage them later

If you need to add more shapes after the initial group is created, you can reuse the same `GroupShape` instance:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

When you later need to ungroup, iterate over `groupShape.GetChildNodes(NodeType.Shape, true)` and re‑insert each child where you want them.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Why this matters:** Some workflows require temporary grouping (e.g., aligning multiple objects) followed by ungrouping for further individual edits.

## Complete runnable example

Below is a self‑contained program that you can compile and run as‑is. Replace `YOUR_DIRECTORY` with an actual folder path on your machine.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Expected output:** When you open `output.docx`, the two original shapes appear as a single grouped object. Selecting the group shows the familiar Word grouping handles, allowing you to move, resize, or rotate the whole set together.

## Conclusion

You now know how to **group shapes in Word** using C# and Aspose.Words, and you’ve seen the exact steps to **add shapes to group** and later manipulate or ungroup them. This technique is ideal for automating report layouts, creating composite diagrams, or preparing Word templates that require precise positioning of multiple objects.

Next, explore related topics such as **how to group shapes** with different anchor types, applying **advanced formatting** to grouped objects, or exporting the grouped result to PDF. Experiment with nesting groups to build complex graphics programmatically.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Shadow Effect to Word Shapes – Complete C# Guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}