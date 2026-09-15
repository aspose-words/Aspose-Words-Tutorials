---
category: general
date: 2026-09-14
description: Learn how to hide shape in Word using C#—including create word document
  code, insert rectangle shape word, and hide shape in word programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: en
lastmod: 2026-09-14
og_description: How to hide shape in Word using C#—step‑by‑step guide that also shows
  how to create word document code and insert rectangle shape word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: How to hide shape in a Word document with C# code
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to hide shape in a Word document with C# code
url: /net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to hide shape in a Word document with C# code

If you need to **how to hide shape** in a Word file, this tutorial shows the complete solution. You’ll see how to create a Word document, insert a rectangle shape, add an ellipse, and hide that ellipse so only the rectangle appears when the file is opened.

The guide covers everything you need—no external references, just the code and explanations. By the end you’ll be able to embed hidden graphics in any Word document you generate programmatically.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.7+)
- Aspose.Words for .NET (free trial or licensed version)  
  Install it via NuGet: `dotnet add package Aspose.Words`
- Basic familiarity with C# and Visual Studio or any IDE you prefer

## Step 1: Set up the project and import namespaces

Start a new console application and add the required `using` statements. These imports give you access to the `Document`, `DocumentBuilder`, and drawing classes needed to manipulate shapes.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Why this matters** – Importing the correct namespaces prevents compilation errors and makes the API surface available for shape creation and visibility control.

## Step 2: Create a new Word document and a builder

A `Document` represents the file, while a `DocumentBuilder` provides a fluent API for adding content. This is the first place where you apply **how to hide shape** logic: you need a document context before any shape can exist.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explanation** – The `Document` object starts empty. The `DocumentBuilder` is positioned at the beginning of the first paragraph, ready to insert shapes or text.

## Step 3: Insert a visible rectangle shape

The rectangle will be the shape that remains visible when the document is opened. You can control its size, position, and formatting directly through the shape object.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Why this step** – Adding a rectangle demonstrates the **insert rectangle shape word** requirement. Setting `FillColor` and `LineColor` makes the shape easy to spot in the final document.

## Step 4: Insert an ellipse shape and hide it

Now you add the shape you intend to conceal. The `Hidden` property tells Word not to render the shape in the UI, though it remains part of the document structure.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explanation** – Setting `Hidden = true` is the core of **hide shape in word**. Word respects this flag during normal viewing and printing, but the shape can still be accessed programmatically if needed.

## Step 5: Save the document

Finally, write the document to disk. Choose a folder you have write access to, and give the file a clear name that reflects the tutorial’s purpose.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Result** – Opening `ShapeVisibility.docx` in Microsoft Word shows only the light‑blue rectangle. The hidden ellipse does not appear, confirming that you have successfully mastered **how to hide shape** in a Word file.

## Full working example

Putting all the snippets together gives you a single, runnable program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Expected output

- **Visual**: When you open `ShapeVisibility.docx`, you see a light‑blue rectangle positioned near the left margin. No ellipse is visible.
- **Programmatic**: The hidden ellipse remains in the document’s XML (`<w:drawing>` element) with the `w:hidden` attribute set, which you can verify by opening the file as a zip and inspecting `document.xml`.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| *Can I hide multiple shapes?* | Yes. Set `Hidden = true` on each shape you want to conceal. |
| *Will hidden shapes print?* | By default Word does not print hidden objects. If you need them printed, clear the `Hidden` flag before printing. |
| *Is the hidden property supported in older Word versions?* | The `Hidden` attribute is part of the Office Open XML standard and works in Word 2007 and later. |
| *What if I need to toggle visibility at runtime?* | Retrieve the shape via `document.GetChildNodes(NodeType.Shape, true)` and flip the `Hidden` property based on your logic. |

## Pro tips

- **Performance**: If you generate many documents, reuse a single `DocumentBuilder` instance instead of creating a new one for each file.
- **Version control**: Store the generated `.docx` files in a version‑controlled folder; hidden shapes can act as metadata markers for downstream processing.
- **Testing**: Automate a quick visual test by converting the DOCX to PDF with Aspose.Words (`document.Save("out.pdf")`). The PDF will also hide the ellipse, confirming that the hidden flag propagates through format conversions.

## Conclusion

You now know **how to hide shape** in a Word document using C#. The tutorial walked through creating a document, **insert rectangle shape word**, adding an ellipse, and applying the `Hidden` flag to achieve **hide shape in word** behavior. With the complete, runnable code you can integrate hidden graphics into any automated reporting or templating workflow.

### Next steps

- Explore other shape properties such as rotation, shadow, and text wrapping.  
- Combine hidden shapes with custom document properties to embed machine‑readable data.  
- Look into **create word document code** patterns for tables, charts, and content controls to expand your automation toolkit.

Feel free to experiment with different shape types and visibility settings—your next Word automation project is just a few lines of code away!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}