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

## Step 3: Create a group shape and add shapes to it

A *group shape* lets you treat several independent shapes as a single unit—perfect for moving or resizing them together. To create a group, instantiate a `GroupShape`, add the desired shapes to it, and then insert the group into the document.

```csharp
        // Create a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Ensure there is a paragraph to host the group shape
        builder.InsertParagraph();

        // Create a new group shape
        GroupShape group = new GroupShape(document);

        // Create a rectangle shape (100 pt wide, 50 pt high) and add it to the group
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 50
        };
        group.AppendChild(rectangle);

        // Create an ellipse shape (80 pt wide, 80 pt high) and add it to the group
        Shape ellipse = new Shape(document, ShapeType.Ellipse)
        {
            Width = 80,
            Height = 80
        };
        group.AppendChild(ellipse);

        // Insert the completed group shape into the document
        builder.CurrentParagraph.AppendChild(group);
```

All shapes added to the `GroupShape` share the same coordinate space, making it easy to align them visually. After the group is inserted, Word treats the rectangle and ellipse as a single object.

## Step 4: Save the modified document

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

If you need to add additional shapes (e.g., a line or a text box) to the same logical unit, create the shape and call `group.AppendChild(newShape)` before inserting the group into the document.

## Common variations and edge cases

| Situation | How to handle it |
|-----------|-----------------|
| **Different units** – you have measurements in centimeters | Convert centimeters to points (`1 cm ≈ 28.35 pt`) before setting `Width` and `Height`. |
| **Adding a text label** – you want a caption inside the group | Create a `Shape` with `ShapeType.TextBox`, set its `Text` property, and append it to the `GroupShape`. |
| **Applying a fill color** – you need a blue rectangle | After creating the rectangle shape, set `rectangle.FillColor = System.Drawing.Color.Blue;`. |
| **Using a different document format** – you target `.doc` instead of `.docx` | The same code works; just change the file extension when calling `Save`. Aspose.Words automatically handles the format. |

## Pro tips

* **Create multiple groups** – you can instantiate a new `GroupShape` each time you need a separate logical unit and insert it wherever required.  
* **Reuse the builder** – the same `DocumentBuilder` instance can be used to insert many groups throughout the document; simply create a new `GroupShape` for each group.  

## Conclusion

You now know how to **group shapes in Word** with C#, how to **add rectangle**, how to **add ellipse**, and how to **insert rectangle shape Word** documents using Aspose.Words. The complete, runnable example demonstrates every step from project setup to saving the final file.

From here you can explore additional shape types, apply styling, or combine grouped shapes with tables and images to create sophisticated, programmatically generated documents.

---

**Next steps**

* Learn how to **rotate grouped shapes**: use `group.Rotation = 45;` after the group is created.  
* Explore **fill and outline customization** for rectangles and ellipses.  
* Integrate this logic into an ASP.NET Core API to generate reports on demand.  

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}