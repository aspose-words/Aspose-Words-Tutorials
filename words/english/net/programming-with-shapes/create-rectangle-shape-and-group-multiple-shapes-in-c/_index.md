---
category: general
date: 2026-09-18
description: Create rectangle shape in a Word document using C#. Learn how to add
  multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: en
lastmod: 2026-09-18
og_description: Create rectangle shape in a Word file with C#. This guide shows how
  to add multiple shapes, add shapes to a group, and insert group shape using Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Create rectangle shape and group shapes in C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Create rectangle shape and group multiple shapes in C#
url: /net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape and group multiple shapes in C#

If you need to **create rectangle shape** in a Word document, this tutorial shows a complete solution. You will see how to **add multiple shapes**, **add shapes to a group**, and **insert group shape** using the Aspose.Words API for .NET.

Working with shapes is a common requirement when generating reports, contracts, or marketing materials programmatically. By the end of this guide you will have a runnable C# console application that produces a `.docx` file containing a rectangle, an ellipse, and a group that holds both shapes.

The only prerequisites are a recent .NET SDK (6.0 or later) and a licensed copy of Aspose.Words for .NET. No additional tools are required.

## Prerequisites

- .NET 6.0 SDK or newer  
- Aspose.Words for .NET (NuGet package `Aspose.Words`)  
- Basic familiarity with C# syntax  

You can install the package with the following command:

```bash
dotnet add package Aspose.Words
```

## Step 1: Create rectangle shape with Aspose.Words

The first step is to create a `Shape` object of type `Rectangle`. This object represents the visual rectangle that will appear in the document.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Why this matters:** `ShapeType.Rectangle` tells Aspose.Words to render a geometric rectangle. Setting `Width` and `Height` defines its size in points (1 point = 1/72 inch). Adding fill and stroke colors makes the shape visible without needing additional styling.

## Step 2: Add multiple shapes to the document

After the rectangle, you can create any number of additional shapes. In this example we add an ellipse to demonstrate how **add multiple shapes** works.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Why this matters:** Each call to `new Shape` creates an independent drawing object. By inserting them sequentially you build up a collection of shapes that can later be grouped or positioned individually.

## Step 3: Add shapes to group

Grouping shapes simplifies layout management because the group behaves as a single node. This step shows how to **add shapes to group** using `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Why this matters:** `GroupShape` acts like a container. When you move, rotate, or resize the group, all child shapes follow automatically. The bounding box (200 × 200 points) defines the coordinate space for the child shapes.

## Step 4: Insert group shape into the document

Now that the group contains the rectangle and ellipse, you need to **insert group shape** at the desired location. The builder already placed the empty group, but you can also insert it elsewhere if needed.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Why this matters:** Adjusting `Left` and `Top` moves the entire group within the page. Saving the document writes the shape hierarchy to a `.docx` file that can be opened in Microsoft Word, LibreOffice, or any compatible viewer.

## Complete runnable example

Below is the full program that combines all steps. Copy the code into a new console project and run it to generate `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Expected output:**  
Opening `GroupShapeExample.docx` shows a single group containing a light‑blue rectangle and a light‑coral ellipse, both positioned inside a 200 × 200 point container. The group can be selected as one object in Word, confirming that **add shapes to group** succeeded.

## Common variations and edge cases

| Situation | Recommended adjustment |
|-----------|------------------------|
| Different shape types (e.g., `ShapeType.Line`) | Create the shape with the desired `ShapeType` and set its geometry accordingly. |
| Need to rotate a shape | Use `shape.Rotation = 45;` (degrees) before adding it to the group. |
| Larger documents with many groups | Reuse a single `DocumentBuilder` instance; avoid creating a new builder for each group to reduce memory overhead. |
| Saving to PDF instead of DOCX | Call `doc.Save("output.pdf", SaveFormat.Pdf);` after the group is inserted. |

**Pro tip:** Always set explicit `Left` and `Top` values for the group when you need precise placement. If you omit them, the group inherits the builder’s current cursor position, which can lead to unexpected layout results.

## Conclusion

You now know how to **create rectangle shape**, **add multiple shapes**, **add shapes to group**, and **insert group shape** in a Word document using C#. The complete example demonstrates the full workflow from document creation to saving the final file.  

Next, explore related topics such as **positioning shapes relative to text**, **applying text wrapping**, and **exporting grouped shapes to PDF**. These extensions let you build sophisticated, programmatic document layouts with Aspose.Words.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}