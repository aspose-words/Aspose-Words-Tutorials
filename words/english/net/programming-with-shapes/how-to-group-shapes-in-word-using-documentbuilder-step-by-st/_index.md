---
category: general
date: 2026-09-08
description: Learn how to group shapes in Word with a DocumentBuilder, create a blank
  Word doc, and insert a rectangle shape in just a few lines of C# code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: en
lastmod: 2026-09-08
og_description: Group shapes in Word using DocumentBuilder. This tutorial shows how
  to create a blank Word doc, insert a rectangle shape, and combine shapes into a
  GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Group shapes in Word with DocumentBuilder – complete C# example
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
url: /net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word using DocumentBuilder – step‑by‑step guide

If you need to **group shapes in Word** programmatically, this tutorial shows a complete solution in C#. You’ll see how to **create a blank Word doc**, use **DocumentBuilder**, and **insert a rectangle shape** before grouping it with an ellipse. The result is a single `GroupShape` that you can move, resize, or style as one object.

This guide covers everything you need to know to generate a Word document with grouped graphics using the Aspose.Words for .NET library. By the end of the article you’ll have a runnable project that produces `GroupedShapes.docx` containing a rectangle and an ellipse combined into a single shape.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.7.2+)
- Aspose.Words for .NET NuGet package (`Aspose.Words`) – version 23.12 or newer
- A C# IDE such as Visual Studio 2022 or Visual Studio Code
- Basic familiarity with C# syntax and object‑oriented programming

> **Pro tip:** Install the NuGet package from the command line to keep your project tidy:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Step 1: Create a blank Word document

The first operation is to instantiate a `Document` object, which represents an empty Word file, and a `DocumentBuilder` that lets you add content.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` provides the file container, while `DocumentBuilder` offers a fluent API for inserting text, images, and shapes. Without a `DocumentBuilder` you would have to manipulate the document's node tree manually, which is error‑prone.

## Step 2: Insert a rectangle shape

A rectangle is a common building block for diagrams. Use `InsertShape` with `ShapeType.Rectangle` and specify width and height in points (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Why this matters:** Setting `Left` and `Top` positions the rectangle precisely on the page, which is essential when you later group it with other shapes. The `InsertShape` method automatically adds the shape to the current paragraph.

## Step 3: Insert an ellipse shape

Next, add an ellipse that will sit beside the rectangle.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Why this matters:** Using a different `ShapeType` demonstrates how the same `DocumentBuilder` API can create varied graphics. Positioning the ellipse so that it overlaps the rectangle makes the grouping effect obvious.

## Step 4: Group the two shapes

A `GroupShape` acts like a container. By appending the rectangle and ellipse as children, they behave as a single object.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Why this matters:** The `Bounds` property tells Word where the group sits on the page. By appending the child shapes, you preserve their individual formatting while enabling collective transformations (move, rotate, resize).

## Step 5: Save the document

Finally, write the document to disk. You can change the path to any folder you prefer.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

When you open `GroupedShapes.docx` in Microsoft Word, you’ll see a rectangle and an ellipse grouped together. Selecting the group will highlight both shapes, allowing you to drag or resize them as a single unit.

### Expected output

- A Word file named **GroupedShapes.docx**
- The first page contains a **rectangle** (100 pt × 50 pt) at position (50, 50)
- An **ellipse** (80 pt × 80 pt) at position (200, 70)
- Both shapes are part of a **GroupShape** with a bounding box of 300 pt × 200 pt

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different page size** | Set `document.Sections[0].PageSetup.PageWidth` and `PageHeight` before inserting shapes. |
| **More than two shapes** | Create additional `Shape` objects and call `groupShape.AppendChild(newShape)` for each. |
| **Apply fill color** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Rotate the group** | `groupShape.Rotation = 45;` (degrees) |
| **Export to PDF** | After saving the DOCX, call `document.Save("GroupedShapes.pdf");` |

## Full source code (ready to run)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Copy the code into a new console project, restore the Aspose.Words NuGet package, and run. The console will confirm the file location, and opening the file will show the grouped graphics.

## Conclusion

You now know **how to group shapes in Word** with the Aspose.Words `DocumentBuilder`. The tutorial walked through creating a **blank Word doc**, **inserting a rectangle shape**, adding an ellipse, and combining them into a `GroupShape`. With this foundation you can build richer diagrams, flowcharts, or custom graphics directly from C#.

### What’s next?

- Explore **how to use DocumentBuilder** for tables, headers, and footers.
- Combine **insert rectangle shape Word** techniques with text boxes for annotated diagrams.
- Use **create blank word doc** as a template for automated report generation.

Feel free to experiment with colors, gradients, and additional shapes. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}