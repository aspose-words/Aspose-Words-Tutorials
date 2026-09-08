---
category: general
date: 2026-09-08
description: Learn how to create blank Word document, insert rectangle shape and group
  multiple shapes using C#. Follow this step‑by‑step guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: en
lastmod: 2026-09-08
og_description: Create blank Word document, insert rectangle shape and group multiple
  shapes in C#. This tutorial walks you through the complete process.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Create blank Word document with grouped shapes in C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: How to create blank Word document with grouped shapes
url: /java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create blank Word document with grouped shapes

If you need to **create blank Word document** that contains custom graphics, this guide shows you exactly how. You’ll learn to **insert rectangle shape**, **group multiple shapes**, and **add shapes to group** using Aspose.Words for .NET.

A blank document gives you a clean canvas, and grouping shapes lets you move, resize, or rotate them as a single unit. This tutorial covers every step—from initializing the document to saving the final file—so you can copy the code into your own project and see immediate results.

## What you’ll need

Before you start, make sure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.6+)
* A valid Aspose.Words for .NET license (the free evaluation works for testing)
* An IDE such as Visual Studio 2022 or Visual Studio Code
* Basic familiarity with C# syntax

No additional NuGet packages are required beyond `Aspose.Words`.

## How to create blank Word document

The first step is to instantiate a `Document` object. This object represents an empty `.docx` file that you can edit with a `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` constructor creates a **blank Word document** in memory. The `DocumentBuilder` provides a fluent API for inserting text, images, and drawing objects.

## Insert rectangle shape into the document

Next, add a rectangle shape. The rectangle will be the first child of the group we’ll create later.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Calling `InsertShape` with `ShapeType.Rectangle` **inserts rectangle shape** at the current cursor position. The width and height are expressed in points (1 pt ≈ 1/72 in).

## Group multiple shapes together

A `GroupShape` acts like a container. All child shapes inside the group move and transform together. First, create the group, then add the rectangle we just built.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

The `InsertGroupShape` method places an empty group at the builder’s cursor. By appending the rectangle, we **group multiple shapes**—the rectangle becomes part of the group’s internal node collection.

## Add shapes to group and save the file

Now add a second shape—an ellipse—to demonstrate how multiple objects share the same container. Afterward, save the document.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

The `InsertShape` call **adds shapes to group** when you append the returned `Shape` to the `GroupShape`. Saving the `Document` writes a `.docx` file that you can open in Microsoft Word, LibreOffice, or any compatible viewer.

### Expected result

When you open *GroupShapeDemo.docx*, you’ll see a blank page with a grouped object that contains a light‑blue rectangle and a pink ellipse. Selecting the group lets you move both shapes together, confirming that **group multiple shapes** worked as intended.

## Why use a GroupShape?

* **Atomic transformations** – Scaling, rotating, or moving the group affects all children uniformly.
* **Logical organization** – Keeps related graphics together, making the document structure easier to maintain.
* **Performance** – Rendering a single container is often faster than handling many independent shapes.

If you need to modify a single child later, you can retrieve it from `group.ChildNodes` by index or by its `Name` property.

## Common variations and edge cases

| Scenario                                 | How to adapt the code                                                            |
|------------------------------------------|----------------------------------------------------------------------------------|
| **Different shape types**                | Replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other `ShapeType` |
| **Adding text inside a shape**           | Use `Shape.TextPath.Text = "Hello"` after inserting the shape                    |
| **Setting a rotation angle**             | `group.Rotation = 45;` (degrees)                                                 |
| **Saving as PDF instead of DOCX**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Applying a border to the group**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Pro tips

* **Name your shapes** – `rectangle.Name = "MyRect";` makes it easier to locate them later.
* **Use relative positioning** – Set `group.RelativeHorizontalPosition` to `RelativeHorizontalPosition.Page` if you want the group to stay anchored to the page margins.
* **Dispose resources** – Wrap the `Document` in a `using` block when working in larger applications to free unmanaged memory promptly.

## Full source code for quick copy‑paste

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Copy the code into a new console project, restore the `Aspose.Words` NuGet package, and run. The output file appears in the project’s `bin/Debug/net6.0` (or equivalent) folder.

## Next steps

Now that you can **create blank Word document**, **insert rectangle shape**, and **group multiple shapes**, you might explore:

* Adding **text boxes** inside a group to create labeled diagrams.
* Exporting the grouped graphic to an image with `doc.Save("image.png", SaveFormat.Png)`.
* Combining groups with tables for richly formatted reports.

Experiment with different shape properties, group hierarchies, and export formats to fully leverage Aspose.Words’ drawing capabilities.

--- 

*Remember*: grouping shapes is a powerful way to keep your Word documents tidy and your code maintainable. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}