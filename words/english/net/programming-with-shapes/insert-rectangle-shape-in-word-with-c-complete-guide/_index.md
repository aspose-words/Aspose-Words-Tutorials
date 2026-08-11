---
category: general
date: 2026-08-10
description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
  shape in Word, and create hidden shape with Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: en
lastmod: 2026-08-10
og_description: Insert rectangle shape in Word using C#. This tutorial explains how
  to hide shape, hide shape in Word, and create hidden shape with full code examples.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Insert rectangle shape in Word with C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Insert rectangle shape in Word with C# – complete guide
url: /net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert rectangle shape in Word with C# – complete guide

If you need to **insert rectangle shape** in a Word document using C#, this guide shows you the exact steps. You will also learn **how to hide shape** so it does not appear in the final file, which answers the common query **hide shape in Word** and demonstrates how to **create hidden shape** programmatically.

The tutorial covers everything from setting up the Aspose.Words SDK to verifying that the shape is hidden. By the end of the article you will have a reusable code snippet that you can drop into any .NET project.

## Prerequisites

Before you start, make sure you have:

- .NET 6.0 or later installed (the code also works with .NET Framework 4.6+)
- A valid Aspose.Words for .NET license or a temporary evaluation key
- Visual Studio 2022 (or any IDE that supports C#)
- Basic familiarity with C# syntax and the Document Object Model (DOM) of Word files

No additional NuGet packages are required beyond `Aspose.Words`.

## Step 1: Create a new blank document and a DocumentBuilder

The first operation is to instantiate a `Document` object. The `DocumentBuilder` provides a convenient API for inserting content such as shapes, paragraphs, and tables.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` represents the whole .docx file, while `DocumentBuilder` maintains a cursor that tracks where the next element will be placed. Initializing both objects is the foundation for any Word automation task.

## Step 2: Insert rectangle shape

Now you insert the rectangle. The `InsertShape` method requires the shape type and its dimensions in points (1 point ≈ 1/72 inch). A size of **200 × 100 points** yields a rectangle roughly 2.78 × 1.39 inches.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Why this matters:** The `Shape` object you receive is fully configurable—color, border, text, and visibility can all be altered before the document is saved.

## Step 3: Hide the shape

To prevent the rectangle from being displayed or printed, set its `Hidden` property to `true`. This property maps directly to the Word “Hidden” attribute, which Word respects in both view and print modes.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Why this matters:** Setting `Hidden` is the standard way to **hide shape in Word** without removing it from the document structure. The shape remains accessible to code, enabling later manipulations such as conditional formatting or data-driven visibility toggles.

## Step 4: Save the document

Finally, persist the document to disk. Choose any folder you like; the example uses a placeholder path that you should replace with a real one.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Why this matters:** Saving finalizes the file and writes the hidden flag into the underlying Open XML. When you open the document in Microsoft Word, the rectangle will be invisible, confirming that you have successfully **created hidden shape**.

## Step 5: Verify the hidden shape

Open the generated `HiddenShape.docx` in Microsoft Word:

1. Go to **File → Options → Display** and ensure *“Show hidden text”* is **unchecked**.  
2. The rectangle should not be visible on any page.  
3. To double‑check, enable *“Show hidden text”*; the rectangle will appear with a faint dotted outline, proving that the shape exists but is hidden.

If the rectangle is still visible, verify that you saved the file after setting `Hidden = true` and that you are opening the correct file.

## Full runnable example

Below is the complete program you can copy, paste, and run directly.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Expected output:** The console prints the file path and a short reminder. When the file is opened in Word, the rectangle is invisible unless hidden text is enabled.

## Common questions and edge cases

### Can I hide only the outline but keep the fill visible?

Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible = false` to hide the border while keeping the fill color. This is a variation of **how to hide shape** that preserves part of the visual appearance.

### Does the hidden flag work in older Word versions (2003, 2007)?

The hidden attribute is part of the Open XML specification introduced with Word 2007. Documents saved in the older binary `.doc` format will not preserve the flag. To support legacy formats, save the document as `.docx` and, if needed, convert it later using Aspose.Words’ `SaveFormat.Doc`.

### What if I need to hide multiple shapes at once?

Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection and set `Hidden = true` on each shape that meets your criteria (e.g., a specific `ShapeType` or a custom `AlternativeText` value).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Is there a performance impact when hiding shapes?

The hidden flag adds a tiny XML attribute; it does not affect rendering speed. However, a very large number of hidden objects can increase file size marginally. Remove shapes you never need to keep the document lean.

## Tips and best practices

- **Give the shape a meaningful name** using `rectangle.Name = "MyHiddenRectangle"`; this helps when you later search for the shape in the DOM.
- **Set `AlternativeText`** to a custom tag (e.g., `"HiddenShape"`). This allows you to locate the shape without relying on its index.
- **Wrap the code in a try‑catch block** to handle licensing errors or I/O exceptions gracefully.
- **Dispose of the Document** after saving if you are processing many files in a loop to free unmanaged resources: `document.Dispose();`.

## Conclusion

You now know how to **insert rectangle shape** in a Word document with C#, how to **hide shape in Word**, and how to **create hidden shape** that remains part of the document structure but stays invisible to end users. The complete, runnable example demonstrates the entire workflow, from document creation to verification.

Next, you might explore **how to hide shape** based on user input, or combine hidden shapes with content controls for dynamic document generation. You can also apply the same technique to other shape types such as ellipses, arrows, or custom drawings.

Feel free to experiment with different dimensions, colors, and visibility settings. If you encounter any issues, revisit the steps above or consult the Aspose.Words documentation for deeper API details. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}