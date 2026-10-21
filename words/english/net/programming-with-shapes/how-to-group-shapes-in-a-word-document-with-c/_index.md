---
category: general
date: 2026-08-14
description: How to group shapes in a Word document using C#. Learn to create Word
  document, insert rectangle shape, group shapes in Word, and save document as docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: en
lastmod: 2026-08-14
og_description: How to group shapes in a Word document using C#. Follow this complete
  tutorial to create a Word file, insert rectangle shape, group shapes in Word, and
  save the result as a docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: How to group shapes in a Word document with C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: How to group shapes in a Word document with C#
url: /net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in a Word document with C#

If you need to **how to group shapes** in a Word document, this guide shows you the exact steps using C# and the Aspose.Words library. You’ll see how to create a Word document, insert rectangle shape, group shapes in Word, and finally **save document as docx**—all in a single, runnable program.

Creating and manipulating shapes is a common requirement when generating reports, contracts, or marketing brochures programmatically. By the end of this tutorial you’ll have a reusable code snippet that you can drop into any .NET project.

## Prerequisites

Before you begin, make sure you have:

- .NET 6.0 or later installed  
- Visual Studio 2022 (or any IDE that supports .NET)  
- An Aspose.Words for .NET license (or a free trial)  
- Basic familiarity with C# syntax  

No additional NuGet packages are required beyond `Aspose.Words`.

## How to group shapes in a Word document

The core of the solution is a five‑step process. Each step is explained in detail, and the complete source code is provided at the end of the article.

### Step 1: Create a new blank document

The first thing you do when you want to **create Word document** programmatically is instantiate a `Document` object. This object represents the entire .docx file in memory.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder` is a high‑level helper that lets you insert text, tables, and shapes without manually handling the underlying node tree.

### Step 2: Insert a rectangle shape

To demonstrate **insert rectangle shape**, we use the `InsertShape` method. The rectangle will act as the first member of the group.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Why this matters:** Shapes are positioned relative to the insertion point. Setting a fill color helps you see the shape when you open the resulting document.

### Step 3: Insert an ellipse shape

Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will be the second member of the group.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Why this matters:** By inserting the ellipse immediately after the rectangle, both shapes end up in the same paragraph, which simplifies grouping later on.

### Step 4: Group the rectangle and ellipse

Now we answer the central question **how to group shapes** in a Word document. Aspose.Words provides `AppendGroupShape` to create a group container, and then you call `Group()` on that container.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Why this matters:** Once grouped, any transformation (move, resize, rotate) applied to `groupedShape` automatically affects both the rectangle and the ellipse. This is essential for maintaining layout consistency in generated documents.

### Step 5: Save the document as a DOCX file

The final step is to **save document as docx**. You can choose any path you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should replace with a real folder.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Why this matters:** Saving as DOCX preserves the grouping metadata, so when you open the file in Microsoft Word you’ll see the rectangle and ellipse acting as a single object.

## Full, runnable example

Below is the complete program that combines all five steps. Copy it into a new console project, restore the Aspose.Words NuGet package, and run it.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Expected output

When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue rectangle and a light‑coral ellipse locked together. Clicking either shape selects both, allowing you to move or resize them as a single unit.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Can I group more than two shapes?** | Yes. Pass any number of `Shape` objects to `AppendGroupShape`. The method accepts an array, so you can build a collection dynamically. |
| **What if I need the group to be anchored to a table cell?** | Insert the shapes inside the cell’s paragraph, then call `AppendGroupShape` on that paragraph. The group inherits the cell’s anchoring. |
| **Does grouping affect the underlying XML?** | Aspose.Words writes a `<w:grpSp>` element that contains the child shapes. Word recognises this as a group, preserving relative positioning. |
| **How do I ungroup later?** | Call `groupedShape.Ungroup()`; the method returns the individual shapes so you can manipulate them separately. |
| **Is there a performance impact when grouping many shapes?** | Grouping itself is inexpensive, but rendering very large groups (hundreds of shapes) can increase the file size. Consider flattening images if size becomes an issue. |

## Pro tips

- **Set explicit positions** (`Left`, `Top`) if you need precise alignment before grouping.  
- **Use `Shape.WrapType = WrapType.Inline`** when you want the group to behave like a paragraph element rather than a floating object.  
- **Apply a line style** to the group (`groupedShape.LineFormat`) to give the whole collection a border.  
- **Reuse the group**: after calling `Group()`, you can clone `groupedShape` and insert the clone elsewhere in the document.

## Next steps

Now that you know **how to group shapes** in a Word document, you can explore related topics such as:

- **Insert rectangle shape** with custom text or images inside the shape.  
- **Create complex diagrams** by nesting groups (group a group).  
- **Export the document as PDF** while preserving shape grouping (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Each of these builds on the same fundamentals covered here, so you’re well‑positioned to expand your Word automation toolkit.

## Conclusion

This tutorial demonstrated **how to group shapes** in a Word document using C#. You learned to **create Word document**, **insert rectangle shape**, **group shapes in Word**, and finally **save document as docx**. With the complete, runnable example and the practical tips provided, you can integrate shape grouping into any document‑generation workflow. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}