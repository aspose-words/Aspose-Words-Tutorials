---
category: general
date: 2026-09-08
description: Create rectangle shape in a Word document with C#. Learn to set shape
  size, group multiple shapes, and create blank Word document programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: en
lastmod: 2026-09-08
og_description: Create rectangle shape in a Word document with C#. This guide shows
  how to set shape size, group multiple shapes, and create a blank Word document programmatically.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Create rectangle shape and group shapes in Word using C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Create rectangle shape and group shapes in Word using C#
url: /net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape and group shapes in Word using C#

If you need to **create rectangle shape** inside a Word file, this tutorial gives you a complete, ready‑to‑run solution. You’ll see how to set shape size, group multiple shapes, and create a blank Word document from scratch—all with the Aspose.Words for .NET library.

Working with Word documents programmatically often feels like juggling many small details. By the end of this guide you’ll have a single method that produces a `.docx` file containing a rectangle and an ellipse grouped together, ready for further editing or printing.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.6+)
* A licensed copy of **Aspose.Words for .NET** (you can use a free evaluation key)
* An IDE such as Visual Studio 2022 or Visual Studio Code
* Basic familiarity with C# syntax

No additional NuGet packages are required beyond `Aspose.Words`.

## Step 1: Create a blank Word document

The first step is to create an empty document that will host the shapes. This satisfies the *create blank word document* requirement.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Creating a blank document gives you a clean canvas. The `Document` object represents the entire `.docx` file, and its `FirstSection.Body.FirstParagraph` is the default insertion point for new nodes.

## Step 2: Create rectangle shape

Now you can add the rectangle. This is where the **create rectangle shape** operation happens.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Setting the dimensions directly answers the **set shape size** keyword. All size values are expressed in points, which provides precise control over how the shape appears in the final document.

## Step 3: Create an additional shape (ellipse)

A typical use case is to combine several shapes. Here we add an ellipse that will later share the same container.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Both shapes are still independent at this point. The next step shows how to **group multiple shapes** together.

## Step 4: Group shapes in Word

Grouping shapes lets you move, resize, or format them as a single unit. This satisfies the **group shapes in word** and **group multiple shapes** requirements.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

The `GroupShape.Bounds` property determines the coordinate system for the child shapes. By placing the rectangle and ellipse inside the same `GroupShape`, you can later move or rotate them together with a single call.

## Step 5: Save the document

Finally, write the document to disk. The file will contain the grouped shapes you just created.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

After running the program, open `GroupedShapes.docx` in Microsoft Word. You should see a rectangle and an ellipse grouped together; selecting one shape also selects the other, confirming that the grouping succeeded.

## Full source code

Copy the following complete program into a new console‑app project and run it. No additional code is required.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Expected output

Running the program produces `GroupedShapes.docx`. Opening the file in Word shows:

* A **rectangle** (100 pt × 50 pt) with a blue border and light‑gray fill.
* An **ellipse** (80 pt × 80 pt) with a dark‑green border and light‑yellow fill.
* Both shapes are inside a single group, so moving one moves the other.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes to the group?** | Yes. Create additional `Shape` objects and call `group.AppendChild(yourShape)` for each. |
| **What if I need to rotate the group?** | Set `group.RotationAngle = 45;` (degrees). All child shapes rotate together. |
| **Is it possible to group shapes after the document is saved?** | You must modify the document structure before saving; otherwise you’d need to load the file, locate the shapes, and recreate the group. |
| **Do I need to dispose of any objects?** | Aspose.Words manages its own resources, but you should dispose of `FileStream` objects if you open streams manually. |
| **Will the code work with .doc (binary) format?** | Yes, change `doc.Save("output.doc")`. The grouping behavior is identical. |

## Conclusion

You now know how to **create rectangle shape**, **set shape size**, and **group multiple shapes** inside a Word file using C#. This approach lets you programmatically build complex diagrams, watermarks, or template‑based reports without manual editing.

### Next steps

* Explore **group shapes in word** further by adding text boxes or images to the same group.
* Use the `SetShapeSize` pattern to dynamically calculate dimensions based on page layout.
* Combine this technique with mail‑merge fields to generate personalized documents at scale.

Feel free to experiment with different shape types, colors, and group transformations. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}