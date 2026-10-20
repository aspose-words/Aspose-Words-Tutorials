---
category: general
date: 2026-09-21
description: Create a blank Word document using Aspose.Words, set shape size, set
  shape position, set shape color, and save the docx file in a single walkthrough.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: en
lastmod: 2026-09-21
og_description: Create a blank Word document, set shape size, set shape position,
  set shape color, and save the docx file with Aspose.Words in minutes.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Create a blank Word document and add colored shapes – Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Create a blank Word document and add colored shapes with Aspose.Words
url: /net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document and add colored shapes with Aspose.Words

If you need to **create a blank Word document** programmatically, this guide shows you how with Aspose.Words. You’ll learn how to **set shape size**, **set shape position**, **set shape color**, and finally **save the docx file** without leaving your IDE.

Working with Word files in C# often means juggling low‑level OpenXML calls, but Aspose.Words abstracts the complexity. By the end of this tutorial you will have a fully functional `.docx` that contains a grouped shape made of two colored rectangles—perfect for reports, certificates, or custom templates.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 or newer (install via NuGet: `Install-Package Aspose.Words`)
- Basic familiarity with C# and Visual Studio (or any C# editor)

No existing Word file is required; the tutorial starts by **creating a blank Word document** from scratch.

## Create a blank Word document with Aspose.Words

The first step is to instantiate a `Document` object. This object represents an empty Word file in memory.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` starts out empty, which is exactly what you need when you **create a blank Word document**. The `builder` will later be used to insert the shape group at the current cursor location.

## Set shape size and create a GroupShape

A `GroupShape` works like a container that can hold multiple individual shapes. First, define the container’s overall dimensions.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Here we **set shape size** for the group itself (300 × 200). The same property names (`Width`, `Height`) are used for each child shape, giving you fine‑grained control over every element.

## Add the first rectangle and set shape color

Now add a rectangle to the group and give it a background color.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

The `FillColor` property **sets shape color**. Using `System.Drawing.Color` lets you pick any predefined or custom ARGB value.

## Add a second rectangle, set its size, position, and color

A second rectangle demonstrates how to **set shape position** relative to the group and how to change its color.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Because the group’s width is 300 points, the two 120‑point rectangles fit comfortably with a 30‑point gap. Adjust `Left` and `Top` if you need a different layout.

## Insert the GroupShape into the document

With the group fully configured, place it at the current cursor position.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` writes the shape directly into the document’s body, preserving the exact **set shape position** you defined earlier.

## Save the docx file

The final step is to persist the document to disk. This demonstrates the **save docx file** operation.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

After running the program, open `GroupShape.docx` in Microsoft Word. You should see a blank page with a grouped shape containing two colored rectangles positioned side‑by‑side.

### Expected output

- A single‑page `.docx` file.
- The page contains a group shape located 100 pts from the left and top margins.
- Inside the group, a light‑blue rectangle sits on the left, and a light‑coral rectangle sits on the right, each 120 × 80 pts.

## Full, runnable example

Below is the complete program you can copy‑paste into a console application. No additional files are required.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Running this program creates the exact document described earlier, fulfilling all four objectives: **create blank word document**, **set shape size**, **set shape position**, **set shape color**, and **save docx file**.

## Common variations and edge cases

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **Different shape types** | Replace `ShapeType.Rectangle` with `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. | Allows you to build more complex graphics without external images. |
| **Dynamic dimensions** | Compute `Width` and `Height` from user input or configuration files. | Makes the solution reusable across multiple document templates. |
| **Saving as PDF** | Call `document.Save("output.pdf", SaveFormat.Pdf);` | If recipients need a non‑editable format, PDF is a safe choice. |
| **Adding text inside a shape** | Create a `TextBox` shape and set `TextBox.Text`. | Useful for creating labeled badges or callouts. |
| **Multiple groups on one page** | Repeat steps 2‑5 with different `Left`/`Top` values. | Enables you to build dashboards or multi‑section layouts. |

### Pro tip

When you need to align shapes precisely, use the `ShapeBase.WrapType = WrapType.Inline` property before inserting the group. This forces the group to behave like a paragraph, preventing unexpected text flow around it.

## Conclusion

You now know how to **create a blank Word document** with Aspose.Words, **set shape size**, **set shape position**, **set shape color**, and **save the docx file**. The complete example demonstrates a clean, reusable pattern for adding grouped graphics to any Word automation project.

From here you can explore:

- Adding more shapes or images to the same `GroupShape` (**set shape size**, **set shape color** variations).
- Using `ShapeBase.Rotation` to rotate rectangles for decorative effects.
- Exporting the same document as PDF or HTML to broaden distribution (**save docx file** alternative).

Feel free to experiment with different colors, sizes, and layout logic to match your specific reporting or templating needs. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}