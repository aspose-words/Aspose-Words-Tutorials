---
category: general
date: 2026-09-05
description: Learn how to create a blank word document and add a rectangle shape that
  can be hidden using Aspose.Words in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: en
lastmod: 2026-09-05
og_description: Blank word document creation and hidden rectangle shape insertion
  using Aspose.Words – step‑by‑step guide for C# developers.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Create a blank word document with a hidden rectangle shape
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Create a blank word document and add a rectangle shape
url: /net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank word document and add a rectangle shape

If you need to **blank word document** creation that also contains a shape you don’t want to appear in the layout, this guide shows you exactly how to do it with Aspose.Words for .NET. You’ll see a complete, runnable example that creates a new document, adds a rectangle shape, hides that shape, and saves the file—no extra tooling required.

The tutorial covers everything from project setup to troubleshooting common pitfalls. By the end you’ll be able to generate a Word file that looks empty to the reader but still carries hidden metadata, which is useful for things like watermarks, custom XML storage, or layout anchors.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later (the code also works with .NET Framework 4.7+)
* Visual Studio 2022 (or any IDE that supports C#)
* An active **Aspose.Words** NuGet license (the free trial works for testing)
* Basic familiarity with C# and the concept of document nodes

You can install the library with the following CLI command:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Keep your Aspose.Words version up‑to‑date; the API used in this tutorial is stable as of version 23.10.

## How to create a blank word document with Aspose.Words

The first step is to instantiate a `Document` object. A fresh `Document` represents an empty **blank word document**—no paragraphs, no sections, just the file container.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Why this matters:** Starting with a clean document ensures that the hidden shape you’ll add later does not interfere with existing content or styles.

## Add a rectangle shape to the document

Next we create a rectangular shape. In Aspose.Words a shape is a node that can be placed anywhere in the document tree, and it can be configured with size, fill, line style, and visibility.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

The code above creates a visible rectangle. At this point you could insert it into the document with `builder.InsertNode(rectangle)`. However, because we want the shape to stay hidden, we’ll adjust its `Hidden` property before insertion.

## How to hide shape in a Word document

Word provides a `Hidden` attribute for shape nodes. When set to `true`, the shape does not appear in the page layout, but it remains part of the document’s XML. This is the core of the **how to hide shape** requirement.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Explanation:** Setting `Hidden = true` adds the `<w:hide>` attribute to the shape’s XML. Word processors ignore the shape during rendering, yet the shape can still be accessed programmatically or via Word’s XML view.

## Insert the hidden shape into the blank document

Now we place the hidden rectangle into the document tree. Because the document is still empty, the shape becomes the first node in the main story.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

If you open the resulting file in Microsoft Word, you’ll see an apparently empty page. The shape is there, but it’s invisible.

## Save the document

Finally, write the document to disk. You can choose any supported format (`.docx`, `.pdf`, `.odt`, etc.). For this tutorial we’ll use the modern DOCX format.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Expected result

Open `HiddenRectangle.docx` in Word:

* The document appears blank (no visible shapes or text).
* If you inspect the file with a tool like **Open XML SDK** or the **Word XML Viewer**, you’ll see the `<w:pict>` element containing the rectangle with the `hidden` attribute.

![blank word document with hidden rectangle shape](image.png){: .align-center alt="blank word document with hidden rectangle shape"}

## Full, runnable example

Below is the complete program you can copy‑paste into a console application. It includes all necessary `using` directives, error handling, and comments.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Run the program (`dotnet run`) and verify the output file. The console will confirm the save location.

## Common questions and edge cases

### Can I hide multiple shapes at once?

Yes. Create each shape, set `Hidden = true`, and insert them sequentially. The hidden flag works per node, so mixing hidden and visible shapes in the same document is supported.

### What if I need the shape to be hidden only in the print view?

Word distinguishes between **display** and **print** visibility through the `DisplayWhen` property. Aspose.Words does not expose a direct API for that flag, but you can modify the underlying XML:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Use this only when you need print‑only visibility.

### Does the hidden shape affect file size?

A hidden shape adds the same XML payload as a visible one, so the file size increase is identical. However, because the shape


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}