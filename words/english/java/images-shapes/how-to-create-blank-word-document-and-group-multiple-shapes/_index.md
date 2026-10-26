---
category: general
date: 2026-10-26
description: Create a blank Word document in C# and learn how to insert a group shape,
  then add a rectangle shape to the group. This guide covers group multiple shapes
  step‑by‑step.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: en
lastmod: 2026-10-26
og_description: Create blank Word document in C# and see how to insert group, then
  add rectangle shape. Master grouping multiple shapes with a complete code example.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Create blank Word document and group multiple shapes – C# tutorial
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to create blank Word document and group multiple shapes
url: /java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create blank Word document and group multiple shapes

If you need to **create blank Word document** programmatically, this tutorial shows you exactly how. You’ll see how to insert a group shape, then **add rectangle** to that group, covering the full workflow from an empty document to a grouped drawing.

Working with Word files often means arranging several drawings together—think of a diagram made of multiple shapes. By the end of this guide you’ll be able to **group multiple shapes**, insert a **rectangle shape**, and understand **how to insert group** and **how to add rectangle** in a clean, reusable way.

## What you’ll need

* .NET 6.0 or later (the code also works with .NET Framework 4.6+)
* **Aspose.Words for .NET** NuGet package (`Install-Package Aspose.Words`)
* A basic understanding of C# and the Visual Studio IDE (any IDE works)

> **Pro tip:** Aspose.Words runs completely offline; you don’t need an internet connection after the package is installed.

## Step 1: Create a blank Word document

The first operation is to instantiate an empty `Document` object. This object represents the **blank Word document** that you will later enrich with shapes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* A `Document` without any sections or paragraphs is still a valid .docx file. Starting from a clean slate guarantees that no hidden formatting interferes with the shapes you will add later.

## Step 2: Insert a group shape (how to insert group)

A **group shape** acts like a container that can hold other drawing objects. In Aspose.Words you create it with `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Why use a group?* Grouping lets you move, rotate, or resize several shapes as a single unit. This is essential for diagrams where elements need to stay aligned.

## Step 3: Insert a rectangle shape (insert rectangle shape)

Now add a rectangle to the document. The `InsertShape` method returns a `Shape` object that you can later attach to the group.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Why a rectangle?* Rectangles are the most common building block for flowcharts, UI mock‑ups, and placeholder graphics. The dimensions are expressed in points (1 pt ≈ 1/72 inch).

## Step 4: Add the rectangle to the group (how to add rectangle)

A shape created with `InsertShape` lives directly in the document body. To make it part of the group, call `AppendChild` on the `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*What happens under the hood?* `AppendChild` moves the rectangle node from the document’s main story into the group’s internal collection, preserving its size and position relative to the group’s origin.

## Step 5: Save the document

Finally, write the file to disk. You can open the resulting `.docx` in Microsoft Word to see the grouped rectangle.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Edge case:** If you intend to add more shapes (e.g., circles, lines) to the same group, repeat **Step 3** and **Step 4** for each new shape before saving. The group will automatically adjust its bounding box to encompass all children.

## How to group multiple shapes – extending the example

Below is a quick snippet that adds a second shape (an ellipse) to the same group, demonstrating **group multiple shapes** in a single document.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

When you open `GroupedShapeExample.docx`, you’ll see the rectangle and ellipse move together when you select the group in Word.

## Common questions and troubleshooting

| Question | Answer |
|----------|--------|
| **Do I need a license for Aspose.Words?** | A free evaluation works without a license, but it adds a watermark. For production, apply a license to remove the watermark and unlock full performance. |
| **Can I position shapes precisely?** | Yes. After inserting a shape you can set `Shape.Left`, `Shape.Top`, `Shape.Width`, and `Shape.Height` properties. |
| **What if the rectangle disappears after saving?** | Ensure you call `group.AppendChild(rectangle)` *after* inserting the rectangle. Adding the shape to the document body first and then moving it into the group is required. |
| **Is it possible to group shapes across different sections?** | No. All shapes in a group must belong to the same story (section). Create separate groups per section if needed. |

## Recap

You now know how to **create blank Word document**, **insert group**, **add rectangle**, and **group multiple shapes** using Aspose.Words for .NET. The complete, runnable example above can be copied into a console app and executed immediately.

## Next steps

* Experiment with **insert rectangle shape** sizes and colors (`rectangle.FillColor = Color.LightBlue;`).  
* Explore other shape types (`ShapeType.Polygon`, `ShapeType.Line`) to enrich your diagrams.  
* Learn how to convert the final `.docx` to PDF (`doc.Save("output.pdf");`) for distribution.  
* Dive into **how to add rectangle** to existing documents that already contain text—use `DocumentBuilder.MoveTo` to position the group where you need it.

Feel free to adapt the code for your own reporting or diagram‑generation needs. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create blank Word document and group shapes in C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [How to group shapes in Word and add shapes to Word document](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}