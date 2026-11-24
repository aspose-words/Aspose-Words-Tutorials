---
category: general
date: 2026-11-18
description: Learn how to create rectangle shape in a Word document with C#. The guide
  also covers set shape size, set shape position, and group shapes in Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: en
lastmod: 2026-11-18
og_description: Create rectangle shape in a Word file using C# and learn to set shape
  dimensions, set shape position, and group shapes in Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Create rectangle shape and group shapes in Word with C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: How to create rectangle shape and group shapes in Word using C#
url: /java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create rectangle shape and group shapes in Word using C#

If you need to **create rectangle shape** in a Word document, this tutorial shows you a complete, ready‑to‑run solution. You’ll see how to set shape size, set shape position, and group shapes in Word so that they behave as a single object.

Working with shapes is a common requirement when generating reports, invoices, or diagrams programmatically. By the end of this guide you’ll be able to generate a `.docx` file that contains a rectangle, an ellipse, and a grouped container—all created with Aspose.Words for .NET.

## Prerequisites

- .NET 6.0 SDK or later (the code also works with .NET Framework 4.7+)
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- A code editor or IDE (Visual Studio, VS Code, Rider, etc.)

No additional libraries are required.

## How to create rectangle shape and group shapes in Word

The core steps are:

1. **Create a blank document** and a `DocumentBuilder`.
2. **Insert a `GroupShape`** that will hold the individual shapes.
3. **Create a rectangle shape**, set its dimensions, and add it to the group.
4. **Create an ellipse shape**, set its size and position, and add it to the group.
5. **Save** the document.

Each step is explained below, and the complete source code follows the explanation.

### Step 1: Initialize the document and builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` represents the whole Word file, while `DocumentBuilder` provides a fluent API to insert content. Initializing them is mandatory before you can add any shapes.

### Step 2: Insert a group shape

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

A `GroupShape` works like a container; all child shapes move together. This is the recommended way to **group shapes in Word** when you need collective transformations (e.g., moving, rotating, or deleting).

### Step 3: Create the rectangle and set its size

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Here we **create rectangle shape** and **set shape size** by assigning `Width` and `Height`. In Aspose.Words, sizes are expressed in points (1 pt ≈ 1/72 in). Setting the dimensions explicitly ensures the rectangle appears exactly as intended.

### Step 4: Create the ellipse, set dimensions, and position it

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

The **set shape dimensions** for the ellipse are identical for width and height, producing a perfect circle. The `Left` property demonstrates **set shape position**: the ellipse starts 120 pt to the right of the group’s origin, so it does not overlap the rectangle.

### Step 5: Save the document

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Saving writes the Word file to disk. You can open `GroupShape.docx` in Microsoft Word to verify that the rectangle and ellipse are grouped and positioned correctly.

## Setting shape dimensions and size – deeper look

- **Points vs. inches**: 72 pt = 1 in. If you prefer inches, multiply by 72 (e.g., `2.5 * 72` for 2.5 in).
- **Automatic scaling**: If you omit `Width` or `Height`, the shape uses its default size. Explicitly **set shape size** to avoid layout surprises.
- **Aspect ratio**: For shapes like `Ellipse`, keeping `Width` and `Height` equal maintains a circular appearance.

## Positioning a shape in Word

The `Left` and `Top` properties control the shape’s offset inside its container (the group or the page). Positive values move the shape right/down; negative values shift it left/up. When grouping, positions are relative to the group's origin, which simplifies layout calculations.

## Grouping shapes in Word using Aspose.Words

Grouping is essential when you want multiple shapes to act as a single unit. The `GroupShape` object:

- Supports `AppendChild` to add any `Shape` (rectangle, ellipse, image, etc.).
- Allows you to move, rotate, or delete the whole group with a single call.
- Keeps child shape positions relative to the group, making complex diagrams easier to manage.

**Pro tip:** After adding all child shapes, you can adjust the group’s `Width`, `Height`, `Left`, and `Top` to reposition the entire collection in one step.

## Complete runnable example

Below is the full program you can copy, paste, and run. It includes all `using` directives, a `Main` method, and comments that explain each line.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Expected output:** After running the program, `GroupShape.docx` appears in the execution folder. Opening it in Word shows a rectangle (100 pt × 50 pt) on the left and an ellipse (80 pt × 80 pt) positioned 120 pt to the right, both inside a single grouped object.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Screenshot of a Word document showing a grouped rectangle and ellipse shape created with C#" }

*The image above illustrates the final result; the rectangle and ellipse are selectable as one group.*

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes?** | Yes. Call `group.AppendChild(yourShape)` for each additional shape. |
| **What if I need to rotate the group?** | Use `group.RotationAngle = 45;` (degrees) after adding all children. |
| **How do I change the group’s background color?** | Set `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Will this work with .doc files?** | Aspose.Words supports `.doc` and `.docx`. The same code works; just change the file extension in `Save`. |
| **Is there a memory impact when grouping many shapes?** | Grouping itself adds minimal overhead. The main concern is the total number of shapes; keep it reasonable for large documents. |

## Conclusion

In this tutorial you learned how to **create rectangle shape** in a Word file using C#, how to **set shape size**, **set shape dimensions**, **set shape position**, and finally how to **group shapes in Word** with Aspose.Words. The complete example demonstrates a clean, maintainable approach that you can extend to more complex diagrams, charts, or custom graphics.

Next, you might explore:

- Adding text inside shapes (`Shape.TextPath.Text = "Hello"`).
- Inserting images into a `GroupShape`.
- Exporting the grouped shapes to PDF with `doc.Save("output.pdf")`.

Feel free to experiment with different sizes, positions, and additional shape types to fit your project's needs. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}