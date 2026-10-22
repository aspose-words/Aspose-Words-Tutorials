---
category: general
date: 2026-09-18
description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
  Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
  quickly.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: en
lastmod: 2026-09-18
og_description: Create a blank Word document and hide an ellipse shape in Word. This
  guide shows you step‑by‑step how to insert ellipse, hide shape in Word, and create
  hidden shape with Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Create a blank Word document with a hidden ellipse shape
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Create a blank Word document with a hidden ellipse shape
url: /java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document with a hidden ellipse shape

If you need to **create a blank Word document** that contains a shape you don't want to appear in the layout, this guide shows you exactly how to do it. By using Aspose.Words for .NET you can programmatically insert an ellipse and then hide the shape so the document stays visually empty while still holding the shape data.

In this tutorial you will learn:

* how to **create blank Word document** objects,
* how to **insert ellipse** using `DocumentBuilder`,
* how to **hide shape in Word** so it doesn't affect the page,
* how to **create hidden shape** objects for later processing.

The steps work with .NET 6+ and the latest Aspose.Words version (23.9 at time of writing). No additional Office installation is required.

## Prerequisites

* Visual Studio 2022 (or any C# IDE)
* .NET 6 SDK or later
* Aspose.Words for .NET NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* Basic knowledge of C# and Word document concepts

## Step 1: Create a blank Word document

The first thing you must do is instantiate a `Document` object. This object represents an empty `.docx` file and is the foundation for all further operations.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Creating a **blank Word document** gives you a clean canvas – no paragraphs, no sections, just the underlying package structure. This is the ideal starting point when you only need a hidden shape and nothing else.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` provides a convenient API for adding content to a `Document`. It works like a cursor that you move through the document.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder automatically creates a default first section and paragraph, so you can start inserting shapes without manually adding sections.

## Step 3: Insert an ellipse shape

Now we **insert ellipse** using the `InsertShape` method. The method takes a `ShapeType` enumeration, the width, and the height (in points).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Why an ellipse? An ellipse is a vector shape that can be hidden without affecting surrounding text flow. The width of 100 pt and height of 50 pt are arbitrary; you can adjust them to suit your later processing needs.

## Step 4: Hide the shape so it does not appear in the layout

To **hide shape in Word**, set the `Hidden` property on the `Shape` object to `true`. When the document is opened in Microsoft Word, the shape will be invisible and will not take up space in the layout.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

The `Hidden` flag is stored in the shape's XML (`<w:hidden/>`). Word respects this attribute during rendering, which is why the document looks completely blank even though the shape exists.

### Pro tip

If you later need to make the shape visible again, simply set `ellipse.Hidden = false;` and save the document.

## Step 5: Save the document with the hidden shape

Finally, persist the document to disk. The file will be a regular `.docx` that any Word processor can open.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

The saved file, `HiddenEllipse.docx`, is a **create blank word document** that contains a hidden ellipse. Opening it in Microsoft Word shows an empty page, but the shape is still present in the Open XML structure.

## Full working example

Below is the complete, self‑contained program you can copy, paste, and run.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output**

* A file named `HiddenEllipse.docx` appears in `C:\Temp`.
* Opening the file in Microsoft Word displays a completely blank page.
* If you inspect the document with the Open XML SDK or a zip viewer, you will find the `<w:shape>` element with `<w:hidden/>` inside the document part.

## Common questions and edge cases

### What if the shape still appears?

* Ensure you are using Aspose.Words 23.9 or later – older versions had a bug where `Hidden` was ignored for some shape types.
* Verify that you are not applying any additional formatting (e.g., `WrapType`) that forces the shape to occupy layout space.

### Can I hide other shape types?

Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`, etc. Just replace `ShapeType.Ellipse` with the desired type.

### How to list hidden shapes later?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

This snippet iterates over all shapes and prints those that are hidden, which is useful for **create hidden shape** workflows where you later need to process or unhide them.

## Conclusion

You now know how to **create a blank Word document**, **insert ellipse**, and **hide shape in Word** to produce a **create hidden shape** that remains invisible to the reader. This technique is handy for storing metadata, bookmarks, or custom XML within a document without altering its visual appearance.

### Next steps

* Explore **how to hide shape** conditionally based on document content.
* Learn **how to unhide shape** when generating a final version of the document.
* Combine hidden shapes with **custom document properties** to embed machine‑readable data.

Feel free to experiment with different shape types, sizes, and hidden‑state logic to fit your automation scenario. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}