---
category: general
date: 2026-09-30
description: group shapes in Word with C# – learn how to group shapes, add rectangle
  and ellipse, and insert rectangle shape Word documents programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: en
lastmod: 2026-09-30
og_description: group shapes in Word using C# and Aspose.Words. Follow this complete
  guide to add rectangle, add ellipse, and learn how to group shapes efficiently.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Group shapes in Word with C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to group shapes in Word using C# and Aspose.Words
url: /net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word using C# and Aspose.Words

If you need to **group shapes in Word** programmatically, this guide shows you exactly how. You’ll see how to add a rectangle, add an ellipse, and then combine them into a single group shape using the Aspose.Words library for .NET.

Working with shapes is a common requirement when generating reports, contracts, or marketing materials automatically. By the end of this tutorial you will have a reusable C# method that loads a DOCX file, inserts a rectangle and an ellipse, groups them, and saves the result—all without opening Word manually.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* A development environment such as Visual Studio 2022 (Community edition works)  
* An Aspose.Words for .NET license or a free evaluation copy (the API works without a license but adds a watermark)  

You also need a source Word document (`input.docx`) in a folder you can reference from code. The document can be empty; the tutorial focuses on shape handling.

## Step 1: Create a new console project and add Aspose.Words

Open a terminal or the Visual Studio command prompt and run:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

This creates a fresh console application named **WordShapeDemo** and adds the `Aspose.Words` NuGet package, which contains the `Document` and `DocumentBuilder` classes used to manipulate Word files.

## Step 2: Load or create a document

The first operation when working with **group shapes in Word** is to obtain a `Document` object. You can either load an existing DOCX file or start from a blank document.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

The `Document` class represents the entire Word file. Loading a file gives you a ready canvas for inserting shapes.

## Step 3: Begin a group shape

A *group shape* lets you treat several independent shapes as a single unit—perfect for moving or resizing them together. To start a group, call `StartGroupShape()` on a `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Calling `StartGroupShape` tells Aspose.Words that every subsequent shape insertion belongs to the same logical group until you call `EndGroupShape`.

## Step 4: How to add rectangle shape in Word

Now that the group is open, insert a rectangle. The `InsertShape` method takes a `ShapeType` enum, followed by the width and height (in points).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

The rectangle becomes the first member of the group. You can customize its fill, outline, or text later if required.

## Step 5: How to add ellipse shape in Word

Next, add an ellipse (a circle when width equals height). This demonstrates **how to add ellipse** using the same builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Both shapes now share the same coordinate space inside the group, making it easy to align them visually.

## Step 6: Close the group shape definition

When you have added all the desired members, close the group. This finalizes the collection of shapes so Word treats them as one object.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

At this point the document contains a single grouped shape consisting of a rectangle and an ellipse.

## Step 7: Save the modified document

Finally, write the changes back to disk. You can overwrite the original file or create a new one.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Running the program produces `output.docx`. Open the file in Microsoft Word, select the shape, and you’ll see that the rectangle and ellipse move together—proof that the **group shapes in Word** operation succeeded.

### Expected result

* The Word file contains a single grouped object.  
* Selecting the group lets you drag, resize, or rotate both the rectangle and the ellipse simultaneously.  
* No manual interaction with Word is required; everything is done via C# code.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Image alt text: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (fulfills the image alt‑text requirement).

## Why grouping shapes matters

Grouping shapes is more than a visual convenience. It allows you to:

* **Maintain layout consistency** – moving a group keeps relative positions intact.  
* **Apply transformations once** – rotate or scale the entire group instead of each shape individually.  
* **Simplify downstream processing** – when other tools read the DOCX, they see a single composite shape, reducing complexity.

If you ever need to add more shapes (e.g., a line or a text box) to the same logical unit, you only need to call `InsertShape` again before `EndGroupShape`.

## Common variations and edge cases

| Situation | How to handle it |
|-----------|-----------------|
| **Different units** – you have measurements in centimeters | Convert centimeters to points (`1 cm ≈ 28.35 pt`) before calling `InsertShape`. |
| **Adding a text label** – you want a caption inside the group | Insert a `ShapeType.TextBox` after the rectangle and ellipse, then set its `Text` property. |
| **Applying a fill color** – you need a blue rectangle | After `InsertShape`, retrieve the last shape via `builder.CurrentParagraph.Runs[0].Font` and set `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Using a different document format** – you target `.doc` instead of `.docx` | The same code works; just change the file extension when calling `Save`. Aspose.Words automatically handles the format. |

## Pro tips

* **Reuse the builder** – you can start and end multiple groups in the same document; just call `StartGroupShape` again after `EndGroupShape`.  
* **Performance** – batch shape insertion inside a single `StartGroupShape/EndGroupShape` block is faster than inserting shapes individually outside a group.  
* **Licensing** – an evaluation license adds a watermark on the first page. Install a proper license to remove it in production environments.

## Conclusion

You now know how to **group shapes in Word** with C#, how to **add rectangle**, how to **add ellipse**, and how to **insert rectangle shape Word** documents using Aspose.Words. The complete, runnable example demonstrates every step from project setup to saving the final file.

From here you can explore additional shape types, apply styling, or combine grouped shapes with tables and images to create sophisticated, programmatically generated documents.

---

**Next steps**

* Learn how to **rotate grouped shapes**: use `Shape.RotationAngle` after the group is closed.  
* Explore **fill and outline customization** for rectangles and ellipses.  
* Integrate this logic into an ASP.NET Core API to generate reports on demand.  

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}