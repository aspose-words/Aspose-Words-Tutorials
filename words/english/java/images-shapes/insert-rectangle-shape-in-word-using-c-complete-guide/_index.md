---
category: general
date: 2026-08-04
description: Insert rectangle shape in a Word document with C#. Learn how to group
  shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: en
lastmod: 2026-08-04
og_description: Insert rectangle shape in a Word file using C# and then group shapes
  for advanced layouts. This tutorial also covers saving the document as docx and
  using DocumentBuilder efficiently.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Insert rectangle shape in Word – C# step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Insert rectangle shape in Word using C# – complete guide
url: /java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert rectangle shape in Word using C# – complete guide

If you need to **insert rectangle shape** in a Word document using C#, this tutorial shows you exactly how. You’ll also learn **how to group shapes** in Word, **save document as docx**, and **how to use Builder** for clean, maintainable code.

Working with shapes is a common requirement when generating reports, certificates, or custom layouts programmatically. By the end of this guide you will have a fully runnable example that creates a rectangle, adds an ellipse, groups them, and saves the result as a DOCX file.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later installed  
* Visual Studio 2022 (or any IDE that supports C#)  
* The **Aspose.Words for .NET** library (available via NuGet)  

You can add the library with the following command:

```bash
dotnet add package Aspose.Words
```

## Insert rectangle shape with DocumentBuilder

The first step is to create a new `Document` and a `DocumentBuilder`. The builder gives you a fluent API for inserting content, including shapes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

The `DocumentBuilder` instance is the core object you’ll use to **insert rectangle shape** and other elements. It tracks the current cursor position inside the document, so any insertion happens exactly where you need it.

## How to insert a rectangle shape

With the builder ready, call `InsertShape`. You specify the `ShapeType`, width, and height in points (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Why this matters*: Setting `FillColor` and `StrokeColor` makes the rectangle visually distinct, which helps when you later group it with other shapes.

## How to group shapes in Word

Grouping shapes lets you move, rotate, or format multiple objects as a single entity. After inserting the rectangle, add another shape (an ellipse in this example) and then create a `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

The `InsertGroupShape` call creates a placeholder that can hold any number of child shapes. By appending the rectangle and ellipse, you effectively **group shapes in Word**. The group behaves like a single shape—you can reposition it, apply a border, or resize it without affecting the internal layout of each child.

### Pro tip

After grouping, you can change the group's position relative to the page:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Save document as docx

Once the shapes are arranged, you need to persist the file. The `Document.Save` method automatically determines the format from the file extension. To **save document as docx**, pass a path ending with `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Running the program creates `output.docx`. Open the file in Microsoft Word, and you’ll see a light‑blue rectangle and a light‑coral ellipse grouped together. You can click the group and move it as a single object.

## How to use DocumentBuilder effectively

`DocumentBuilder` is more than a shape inserter; it also handles text, tables, headers, and footers. When you combine shape creation with text, remember to reset the cursor if you need to insert content elsewhere:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Keeping the builder’s state explicit avoids accidental overwrites and makes the code easier to maintain.

## Edge cases and variations

| Situation | Recommended approach |
|-----------|----------------------|
| **More than two shapes** | Insert each shape, then call `AppendChild` for every shape before saving. |
| **Nested groups** | Create a group, add shapes, then insert that group into another `GroupShape`. |
| **Different measurement units** | Use `builder.ConvertPixelsToPoints` if you have dimensions in pixels. |
| **Compatibility with older Word versions** | Save as `.doc` by changing the extension; most shape features still work. |

## Complete working example

Below is the full program you can copy‑paste into a new console project. No additional snippets are required.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Expected result**: Opening `output.docx` shows a light‑blue rectangle and a light‑coral ellipse grouped together, positioned 150 pt from the left margin and 100 pt from the top. The caption appears underneath the group.

## Conclusion

You now know how to **insert rectangle shape** in a Word file using C#, **how to group shapes in Word**, and **how to save document as docx** with the Aspose.Words `DocumentBuilder`. By mastering these steps you can build complex layouts—certificates, reports, or custom forms—entirely through code.

Next, explore related topics such as **adding text boxes**, **working with tables**, or **exporting to PDF**. Each of these builds on the same `DocumentBuilder` fundamentals you just practiced.

Ready to automate your Word documents? Try extending the example with more shapes, applying gradients, or looping over data to generate a full report in a single run. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}