---
category: general
date: 2026-11-22
description: Programmatically create Word document in C# and insert rectangle shape,
  insert multiple shapes, and write shapes to Word using Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: en
lastmod: 2026-11-22
og_description: Programmatically create Word document in C# by inserting rectangle
  shape, insert multiple shapes, and write shapes to Word using Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Programmatically create Word document with shapes in C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Programmatically create Word document with shapes in C#
url: /net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmatically create Word document with shapes in C#

If you need to **programmatically create Word document** that contains custom graphics, this guide shows you how to do it with Aspose.Words for .NET. You’ll learn to insert a rectangle shape, add additional shapes, group them, and finally write the shapes to Word—all in a few lines of C#.

Creating a Word file with graphics no longer requires manual editing or macro scripts. By the end of this tutorial you will have a reusable method that produces a `.docx` file containing a rectangle and an ellipse grouped together, ready for downstream processing or reporting.

## What you’ll need

- .NET 6.0 or later (the code also works with .NET Framework 4.6+)
- Aspose.Words for .NET (NuGet package `Aspose.Words`)
- An IDE such as Visual Studio 2022 (any editor that can compile C# is fine)

> **Pro tip:** Install the package with the CLI command `dotnet add package Aspose.Words` before you start coding.

## Programmatically create Word document – overview

The overall flow consists of three logical phases:

1. **Initialize** a new `Document` and a `DocumentBuilder`.  
2. **Insert multiple shapes** (a rectangle and an ellipse) and place them inside a `GroupShape`.  
3. **Write shapes to Word** by saving the `Document` to a `.docx` file.

Each phase is encapsulated in a dedicated step below, so you can copy‑paste the code directly into your project.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Programmatically create Word document with grouped shapes"}

## Step 1: Initialize the document and builder

The `Document` class represents the entire Word file, while `DocumentBuilder` provides a fluent API to add content.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* Creating the `Document` first gives you a clean canvas. The `DocumentBuilder` tracks the current insertion point, which is essential when you later attach shapes to a paragraph hierarchy.

## Step 2: Insert a group shape container

A `GroupShape` lets you treat several individual shapes as a single unit. This is useful when you want to move or resize them together.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Explanation:* `InsertGroupShape` inserts an empty container and automatically makes it the current shape. All subsequent shape insertions will be added to this container until you close the group.

## Insert rectangle shape

Now we add the first graphic—a rectangle. This satisfies the **insert rectangle shape** requirement.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

The rectangle inherits the group’s formatting context, so it appears inside the `GroupShape`. You can also set line color, fill, or text later if needed.

## Insert multiple shapes

To demonstrate the **insert multiple shapes** capability, we add an ellipse right after the rectangle. You can keep adding any number of shapes (e.g., triangles, stars) before closing the group.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

At this point the group contains two distinct shapes: a rectangle and an ellipse. Because they share the same parent, you can move them as a unit.

## Step 3: Attach the group shape to the paragraph hierarchy

Word documents store content in a paragraph tree. To make the group visible in the final file, we must attach it to the current paragraph.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Why this step is required:* Without appending the group to a paragraph, the shapes exist only in memory and are omitted when the document is saved.

## Step 4: Save the document – write shapes to Word

Finally, we persist the in‑memory `Document` to disk. This fulfills the **write shapes to word** goal.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

When you open `GroupShape.docx` in Microsoft Word, you’ll see a rectangle and an ellipse grouped together, exactly as the code inserted.

### Expected output

- A file named **GroupShape.docx** located in the project’s output folder.
- Inside the Word file: a single paragraph containing a grouped rectangle (100 pt × 50 pt) and an ellipse (80 pt × 40 pt). Selecting either shape selects the whole group.

## Handling common edge cases

| Situation | Recommendation |
|-----------|----------------|
| **Different DPI or page size** | Explicitly set `builder.PageSetup.PaperSize` before inserting shapes to avoid unexpected scaling. |
| **Need to position shapes precisely** | Use `builder.MoveTo` to move the insertion point, then set `groupShape.Left` and `groupShape.Top` properties (values are in points). |


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}