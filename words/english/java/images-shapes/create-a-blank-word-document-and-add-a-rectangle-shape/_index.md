---
category: general
date: 2026-10-23
description: Create a blank Word document, add a rectangle shape, and hide the shape
  in Word using Aspose.Words. Step‑by‑step code for .NET developers.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: en
lastmod: 2026-10-23
og_description: Create a blank Word document, add a rectangle shape, and hide the
  shape in Word with Aspose.Words. Follow the complete C# example.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Create a blank Word document and add a hidden rectangle shape
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Create a blank Word document and add a rectangle shape with Aspose.Words
url: /java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document and add a rectangle shape

If you need to **create a blank Word document**, this guide shows you how to do it with Aspose.Words for .NET. You’ll also learn **how to insert shape**—specifically a rectangle—and **hide shape word** so it doesn’t affect the layout.

The tutorial walks through every line of code, explains why each step matters, and covers common pitfalls such as hidden‑shape visibility in different Word view modes. By the end you will have a fully functional `.docx` file that contains a hidden rectangle shape you can later reveal or manipulate programmatically.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.6+)
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- A development environment such as Visual Studio 2022 or VS Code with C# extensions
- Basic familiarity with C# syntax and Word document concepts

No additional Office installation is required because Aspose.Words works completely in memory.

## Create a blank Word document

The first step is to instantiate an empty `Document` object. This object represents a Word file that contains no sections, paragraphs, or content yet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Why this matters:**  
A blank `Document` gives you a clean canvas. If you start from an existing template, hidden shapes could inherit unwanted styles. Starting from scratch ensures the rectangle shape you add later is the only content you control.

## Add a rectangle shape to the document

Next, we need a `DocumentBuilder` to place content into the document. The builder’s `InsertShape` method is the standard way **to insert shape** objects, such as rectangles, circles, or custom drawings.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Why this matters:**  
`InsertShape` returns a `Shape` object that you can further configure (color, line style, etc.). The dimensions are given in points (1 point = 1/72 inch), which matches Word’s internal measurement system.

### Optional: style the rectangle (optional)

If you want the rectangle to have a visible border when you later un‑hide it, you can set its line weight and color:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

These lines are optional because the shape will be hidden in the next step.

## Hide the shape in Word

Word allows shapes to be hidden from the layout while still being part of the document’s object model. Setting the `Hidden` property to `true` makes the shape invisible in normal view but still selectable via the API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Why this matters:**  
A hidden shape is useful for storing metadata, placeholders for later processing, or conditional content that you reveal only under certain circumstances (e.g., when generating a final report). The shape remains in the file, so you can programmatically unhide it later with `rectangleShape.Hidden = false;`.

## Save the document

Finally, write the document to disk. The file extension determines the Word format; `.docx` is the modern Open XML format.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Result:**  
Opening `HiddenShape.docx` in Microsoft Word shows an otherwise empty page. The rectangle is not visible, but if you go to **Home → Select → Selection Pane**, you will see the shape listed and can toggle its visibility.

## Full working example

Below is the complete program you can copy, paste, and run. It includes all necessary `using` statements and comments.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output:**  

- Console prints the save path.  
- `HiddenShape.docx` opens as a blank page in Word.  
- The rectangle shape exists but is hidden; you can verify it via the *Selection Pane* or by programmatically setting `Hidden = false` and reopening the file.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Can I hide other shape types?** | Yes. Any `Shape` (e.g., `ShapeType.Ellipse`, `ShapeType.Picture`) supports the `Hidden` property. |
| **Will the hidden shape increase file size?** | The increase is negligible (a few kilobytes) because the shape data is stored as XML in the `.docx` package. |
| **What if I need the shape to appear only in print view?** | Use the `Shape.IsPrint` property instead of `Hidden`. Setting `IsPrint = false` hides the shape from printed output but keeps it visible on screen. |
| **How to unhide the shape later?** | Load the document, locate the shape (e.g., by `Shape.Name`), then set `shape.Hidden = false;` and save. |
| **Does this work with .doc (binary) format?** | Yes, Aspose.Words can save to `.doc` using `document.Save("file.doc");`. The hidden flag is preserved. |

## Pro tips

- **Name your shapes**: `rectangleShape.Name = "PlaceholderRectangle";` makes it easier to find later via `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Batch processing**: If you need to add hidden shapes to many documents, wrap the code in a method and reuse the `DocumentBuilder` instance.
- **Performance**: Creating a shape is cheap, but saving large documents frequently can be I/O‑bound. Consider using `MemoryStream` for intermediate processing.

## Conclusion

You now know how to **create a blank Word document**, **add a rectangle shape**, and **hide shape word** using Aspose.Words for .NET. This technique lets you embed invisible placeholders that you can reveal or manipulate later, a pattern useful for dynamic report generation, conditional content, and document templating.

Next steps you might explore:

- Replace the rectangle with a picture or chart using `ShapeType.Picture`.
- Use **how to insert shape** in header/footer sections for watermark‑style placeholders.
- Combine hidden shapes with **add rectangle shape**‑based data validation (e.g., storing JSON in a shape’s `AlternativeText` property).

Happy coding, and feel free to experiment with other shape types and visibility options to fit your document automation needs!

## What should you learn next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document – How to Add Rectangle Shape and Shadow](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< blocks/products/products-backtop-button >}}
{{< /blocks/products/pf/main-wrap-class >}}