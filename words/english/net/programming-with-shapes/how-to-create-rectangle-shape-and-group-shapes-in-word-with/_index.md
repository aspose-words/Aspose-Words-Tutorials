---
category: general
date: 2026-09-05
description: Create rectangle shape in a Word document using Aspose.Words, then learn
  how to insert ellipse word and group shapes in Word for richer layouts.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: en
lastmod: 2026-09-05
og_description: Create rectangle shape in a Word document with Aspose.Words, then
  see how to insert ellipse word and group shapes in Word for complex layouts.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Create rectangle shape and group shapes in Word – Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: How to create rectangle shape and group shapes in Word with Aspose.Words
url: /net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create rectangle shape and group shapes in Word with Aspose.Words

If you need to **create rectangle shape** in a Word document, this guide shows you the exact steps with Aspose.Words for .NET. You will also see how to insert ellipse word, group shapes in Word, and save the result as a DOCX file. The solution works in any .NET 6+ project and does not require Microsoft Office installed on the server.

The tutorial covers everything from project setup to handling common layout pitfalls, so you can copy the code and run it immediately.

## Prerequisites

Before you start, make sure you have:

* .NET 6 SDK or later installed  
* A NuGet‑compatible IDE (Visual Studio, Rider, or VS Code)  
* An Aspose.Words for .NET license (or a temporary evaluation key)  
* Basic knowledge of C# and Word document structure  

These items let the code compile and the shapes render correctly.

## Step 1: Set up the project and add Aspose.Words

Create a new console project and add the Aspose.Words package:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

The package provides the `Document`, `DocumentBuilder`, `Shape`, and `GroupShape` classes used throughout this tutorial.

## Step 2: Initialize a blank document and a builder

The `Document` object represents the whole Word file, while `DocumentBuilder` lets you insert content programmatically.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Creating the document first ensures that all subsequent shape operations have a valid container.

## Step 3: **Create rectangle shape** and set its dimensions

A rectangle is the most common container for text or images. You define its size in points (1 pt ≈ 1/72 inch).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Why this step matters: the `Shape` class encapsulates geometry, fill, and line properties. Setting `Width` and `Height` before insertion guarantees the shape appears with the expected size.

## Step 4: **How to insert ellipse word** – add an ellipse shape

An ellipse can be used for icons, markers, or decorative elements. The code mirrors the rectangle creation, only the `ShapeType` changes.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

The `FillColor` and `Line.Color` properties illustrate how to customize appearance without external images.

## Step 5: **Group shapes in Word** – combine rectangle and ellipse

Grouping lets you move, resize, or rotate multiple shapes as a single unit. This is essential when you need a composite graphic (e.g., a labeled icon).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

When you call `AppendChild`, the original shapes are removed from the main document flow and become children of the `GroupShape`. The group behaves like a single shape, which simplifies later layout adjustments.

## Step 6: Save the document

Finally, write the document to disk. You can choose any supported format (`.docx`, `.pdf`, `.html`, etc.). For this tutorial we keep the native Word format.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

After running the program, open *GroupShape.docx* in Microsoft Word. You will see a rectangle and an ellipse grouped together, positioned at the coordinates you specified.

## Common variations and edge cases

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Different size units** | Use `ConvertUtil.InchToPoint(2.5)` for inches or `ConvertUtil.MillimeterToPoint(30)` for millimetres. | Keeps code readable when you work with non‑point measurements. |
| **Adding text inside the rectangle** | Create a `Paragraph` node, set its `Text` property, and add it to `rectangleShape` via `AppendChild`. | Allows you to label the shape without separate text boxes. |
| **Rotating the group** | Set `groupShape.Rotation = 45;` (degrees). | Useful for creating diagonal badges or watermarks. |
| **Saving as PDF** | Call `doc.Save("GroupShape.pdf");`. | Aspose.Words automatically rasterizes vector shapes for PDF output. |
| **Multiple groups** | Create additional `GroupShape` instances and repeat the append/insert steps. | Enables complex page layouts with several independent composites. |

### Pro tip

Always add shapes **before** you group them. If you try to group a shape that is already part of another group, Aspose.Words throws an `ArgumentException`. Building the group in a single method prevents this runtime error.

### Watch out for

* **Coordinate system** – `Left` and `Top` are measured from the page’s left and top margins, not from the document edge. Misunderstanding this can place shapes off‑page.
* **Licensing** – Without a valid license, the saved document will contain a watermark that says “Aspose.Words for .NET Evaluation”. Apply your license early in the code (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) to avoid it.

## Full source code (runnable)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Running this program produces *GroupShape.docx* with the grouped shapes exactly as described.

## Conclusion

You now know how to **create rectangle shape**, **how to insert ellipse word**, and **group shapes in Word** using Aspose.Words. The complete example demonstrates the full workflow—from initializing a document to saving the final file—so you can integrate shape handling into any automated reporting or document‑generation solution.

### What’s next?

* Explore **aspose.words create shapes** for more complex geometry such as `Polygon` or `Freeform`.  
* Combine grouped shapes with **content controls** to build dynamic templates.  
* Convert the DOCX to PDF or HTML to see how vector shapes are rendered across formats.  

Feel free to experiment with different sizes, colors, and rotations. When you master shape grouping, you can build sophisticated diagrams, badges, and custom UI elements directly inside Word documents.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}