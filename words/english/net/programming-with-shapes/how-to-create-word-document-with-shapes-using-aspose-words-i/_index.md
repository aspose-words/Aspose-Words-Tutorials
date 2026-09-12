---
category: general
date: 2026-09-11
description: Learn how to create word document, add rectangle shape, and set shape
  dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: en
lastmod: 2026-09-11
og_description: Create word document with Aspose.Words in C#. This guide shows how
  to add rectangle shape, set shape size, and manage shape dimensions programmatically.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Create word document with shapes – Aspose.Words C# tutorial
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: How to create word document with shapes using Aspose.Words in C#
url: /net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create word document with shapes using Aspose.Words in C#

If you need to **create word document** that contains custom graphics, you can do it entirely in code. This tutorial walks you through creating a Word file, adding a rectangle shape, and controlling every dimension of the shape. By the end you’ll have a reusable snippet that you can drop into any .NET project.

You’ll learn how to **add rectangle shape**, **set shape size**, and **set shape dimensions** inside a grouped container. The example uses Aspose.Words 13.9, but the concepts apply to later versions as well. No prior experience with the Aspose drawing API is required—just basic C# knowledge.

## Prerequisites

- .NET 6.0 or later installed  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- An IDE such as Visual Studio 2022 (any editor that supports C# works)  

Having these tools ready lets you run the code immediately without additional configuration.

## Step 1: Initialize the document and builder – create word document basics

The first operation is to instantiate a `Document` object and a `DocumentBuilder`. The `Document` represents the file itself, while the `DocumentBuilder` provides a fluent API for inserting content.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
Creating the document up front gives you a clean canvas. The builder’s cursor starts at the first paragraph, which is where we’ll later **create shapes in word**.

## Step 2: Build a GroupShape to hold multiple graphics

A `GroupShape` acts like a container; you can move, rotate, or resize the whole group as a single unit. Here we define the container’s width and height in points (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Why this matters:**  
Grouping shapes simplifies layout management. If you later need to add more shapes (e.g., circles or text boxes), they will inherit the group’s position and scaling.

## Step 3: Create a rectangle shape and configure its dimensions

Now we add the actual rectangle. The `Shape` constructor requires the document reference and the shape type. After creation we explicitly **set shape size** and **set shape dimensions**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Why this matters:**  
Specifying width, height, left, and top gives you pixel‑perfect control over the shape. This is essential when the document must match a design specification or a printed form.

## Step 4: Assemble the group by appending the rectangle

Appending the rectangle to the `GroupShape` makes it a child node. You can add as many children as needed before inserting the group into the document.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tip:** If you plan to add a second shape, create it the same way and call `group.AppendChild(secondShape)`. All children share the group’s coordinate system.

## Step 5: Insert the grouped shape into the document and save

With the group fully built, we place it into the current paragraph. The builder’s `CurrentParagraph` property gives direct access to the underlying node tree.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Why this matters:**  
Appending the group to a paragraph ensures the shape appears inline with text flow. Saving the document finalizes the **create word document** operation.

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different page orientation** | Set `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` before creating the group. |
| **Multiple rectangles** | Create additional `Shape` objects and call `group.AppendChild(newRect)` for each. |
| **Dynamic size based on content** | Compute width/height from image dimensions or text metrics, then assign to `rectangle.Width` / `rectangle.Height`. |
| **Export to PDF** | After `doc.Save`, call `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Compatibility with older Word versions** | Save using `SaveFormat.Doc` instead of `Docx` for Word 97‑2003 compatibility. |

These variations illustrate how the same core logic can be adapted to many real‑world requirements.

## Full, runnable example

Below is the complete program you can copy, paste, and run. It includes all `using` directives, a `Main` entry point, and comments that explain each line.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Expected output:**  
When you open *GroupShape.docx*, the first page shows a gray‑bordered rectangle positioned 50 pt from the left/top margin, with the rectangle itself offset 10 pt inside the group. The dimensions match the values set in the code.

## Conclusion

You now know how to **create word document**, **add rectangle shape**, and precisely **set shape size** and **set shape dimensions** using Aspose.Words. The grouped‑shape approach keeps your layout flexible and ready for future extensions such as additional graphics or text boxes.

Next, explore related topics like **create shapes in word** for circles, arrows, or custom SVG paths, and learn how to **set shape fill color** or **apply rotation**. Experiment with different measurements to see how Word renders points versus centimeters, and integrate the code into larger document‑generation pipelines.

Happy coding, and feel free to adapt this pattern to any automated reporting or form‑filling scenario you encounter!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}