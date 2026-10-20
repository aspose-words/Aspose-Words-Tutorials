---
category: general
date: 2026-08-07
description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
  shape, set fill color, and add rectangle shape to a Word document efficiently.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: en
lastmod: 2026-08-07
og_description: Insert rectangle shape in a Word document with C#. Learn how to hide
  shape, set fill color, and add rectangle shape using Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Insert rectangle shape in C# – complete Aspose.Words tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
url: /net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide

If you need to **insert rectangle shape** in a Word document from C#, this guide shows you exactly how to do it. You’ll see how to set the fill color, hide the shape so it doesn’t appear in the final layout, and save the file—all with just a few lines of code.

In the following sections we cover everything you need to know: prerequisites, the complete code listing, explanations for each step, and tips for common variations such as making the shape visible again or using a different color. By the end you’ll be able to **add rectangle shape** to any .docx file programmatically.

## Prerequisites

Before you start, make sure you have:

* **Aspose.Words for .NET** (version 23.10 or later). You can install it via NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK or later installed on your machine.
* A basic understanding of C# and Visual Studio (or any IDE you prefer).

No additional libraries are required—the shape‑related APIs are part of the core Aspose.Words package.

## Insert rectangle shape with Aspose.Words

The core of the solution is a short, self‑contained program that creates a blank document, inserts a rectangle, colors it, hides it, and then saves the file. Below is the full source code with inline comments that explain the *why* behind each line.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### What each step does

| Step | Reason |
|------|--------|
| **Create a new document** | Provides a clean canvas; you can also load an existing .docx by passing a file path to `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` is the high‑level helper that lets you insert text, tables, and shapes without dealing with low‑level node trees. |
| **Insert rectangle shape** | The `InsertShape` method returns a `Shape` object that you can further customize (size, position, borders, etc.). |
| **Set fill color** | The `FillColor` property controls the interior color; you could use any `Color` value (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, etc.). |
| **Hide the shape** | `Hidden = true` tells Word to ignore the shape during layout while still keeping it in the document’s XML. This is the standard way to store invisible objects. |
| **Save the document** | Persists the changes to a .docx file. The saved file will contain the hidden rectangle shape. |

## How to set fill color for a shape

Changing the fill color is as simple as assigning a `System.Drawing.Color` to the `FillColor` property. If you need a custom shade, use `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Why this matters*: The fill color is stored in the shape’s XML (`<w:fill>` attribute). When the shape is hidden, the color still exists, which can be useful for downstream processing (e.g., extracting metadata based on color codes).

## How to hide shape in the final document

The `Hidden` flag is a boolean property on the `Shape` class. Setting it to `true` ensures the shape is ignored by the Word layout engine.

```csharp
rectangleShape.Hidden = true;
```

**Common pitfalls**

* **Hidden vs. Visible** – If you later need the shape to appear, simply set `Hidden = false`.
* **Compatibility** – Older versions of Word (pre‑2007) may treat hidden drawing objects differently. Aspose.Words maintains compatibility by storing the flag in the appropriate OOXML element.

## How to insert shape programmatically

While the example uses a rectangle, the same `InsertShape` method works for many other shapes (ellipse, triangle, line, etc.). The first argument is a `ShapeType` enum value:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tip**: If you need to place the shape at a specific location on the page, use `builder.MoveTo` to set the insertion point before calling `InsertShape`.

## Add rectangle shape to an existing document

Often you’ll be enhancing a template rather than starting from scratch. Replace step 1 with:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

All subsequent steps remain identical, and the rectangle will be added wherever the builder’s cursor is positioned (usually at the end of the document by default).

## Handling edge cases and variations

### 1. Making the shape visible again

If a later part of your workflow needs to reveal the hidden rectangle, you can toggle the flag:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Adding a border (stroke)

A hidden shape can still have a visible border when you decide to show it. Set the `LineColor` and `LineWidth` properties:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Positioning the rectangle absolutely

For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline` (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Using a different measurement unit

Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters, convert first:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Complete runnable example

Below is the *full* program you can copy, paste, and run. It includes all necessary `using` directives and uses absolute paths that you should adjust for your environment.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected result**: The file `HiddenRectangleShape.docx` opens in Microsoft Word with *no visible shape*, but the hidden rectangle is present in the document XML. You can verify its existence by opening the .docx as a zip archive and inspecting `word/document.xml` for a `<w:shape>` element with `w:fill="yellow"` and `w:hidden="true"` attributes.

## Conclusion

You now know how to **insert rectangle shape** in a Word document using C# and Aspose.Words, how to **set fill color**, and how to **hide shape** so it stays invisible in the final layout. The same pattern works for other shape types, custom colors, and existing templates. Experiment with borders, absolute positioning, and different measurement units to tailor the shape to your exact requirements.

### Next steps

* Explore **how to insert shape** inside tables or headers/footers for watermarks.
* Combine **add rectangle shape** with content controls to create dynamic placeholders.
* Review Aspose.Words’ **shape manipulation** API for advanced features like rotation, gradient fills, and SVG import.

Feel free to adapt the code to your own project, and let us know in the comments which shape‑related challenge you solved next!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}