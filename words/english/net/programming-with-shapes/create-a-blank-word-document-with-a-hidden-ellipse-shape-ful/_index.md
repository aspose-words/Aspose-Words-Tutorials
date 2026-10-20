---
category: general
date: 2026-07-29
description: Create a blank word document and learn how to hide shape, create hidden
  object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: en
lastmod: 2026-07-29
og_description: Create a blank word document and hide shape instantly. Learn to create
  hidden object and draw an ellipse shape using Aspose.Words in C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Create a Blank Word Document with a Hidden Ellipse Shape – C# Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
url: /net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide

Ever needed to create a **blank word document** and then hide a shape inside it? Maybe you’re generating a template where certain markers must stay invisible until a later step. In this tutorial we’ll walk through exactly **how to hide shape**, how to **create hidden object**, and even how to **create ellipse shape** using Aspose.Words for .NET. By the end you’ll have a ready‑to‑run C# snippet that produces a DOCX file containing an invisible ellipse.

## What You’ll Learn

- Initialize a fresh blank Word document with Aspose.Words.  
- Build an ellipse shape, set its dimensions, and position it on the page.  
- Mark the shape as hidden so it never shows up on screen or in print.  
- Save the result to disk and verify that the hidden object is truly invisible.  

No external libraries beyond Aspose.Words are required, and the code works with version 24.10 or newer (the `Hidden` property was introduced in that release). Let’s get started.

![Diagram of a hidden ellipse inside a blank Word document](https://example.com/hidden-ellipse.png "Hidden ellipse shape inserted into a blank Word document")

## Create a Blank Word Document and Insert a Hidden Ellipse Shape

The first step is to spin up a brand‑new document. Think of `Document` as an empty canvas; `DocumentBuilder` is your brush.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why start with a blank document?**  
> A clean slate guarantees that no pre‑existing content interferes with the hidden shape you’re about to add. It also makes the example easier to copy‑paste into any project.

## How to Hide Shape: Setting the Hidden Property

Aspose.Words 24.10 introduced the `Hidden` flag on `Shape`. When set to `true`, Word treats the shape like a comment—completely invisible in the UI and when printed.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Pro tip:** If you later need to reveal the shape programmatically, simply toggle `ellipseShape.Hidden = false;` and re‑save the document.

## Create Hidden Object: Inserting the Shape into the Document

Now that the ellipse is prepared and hidden, we insert it at the builder’s current cursor location. The builder’s position defaults to the start of the first paragraph, which is perfect for a blank document.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **What if you need the shape on a specific page?**  
> Move the builder to the desired page first (`builder.MoveToDocumentEnd();` or `builder.MoveToPage(pageNumber);`) before calling `InsertNode`.

## Save the Document Containing the Hidden Shape

Finally, write the file to disk. The output will be a standard DOCX that any Word processor can open—except the ellipse will stay invisible.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Expected output:** Open `HiddenShape.docx` in Microsoft Word. You won’t see any graphics, but the file size will be slightly larger than a truly empty document because the hidden ellipse is stored in the XML.

## Verify the Hidden Ellipse Programmatically (Optional)

If you want to double‑check that the shape is indeed hidden, you can load the saved file and inspect the shape’s `Hidden` property:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Running this snippet prints `True`, confirming that the hidden object survived the save‑load cycle.

## Edge Cases and Common Questions

### What if the target Word version doesn’t support hidden shapes?

The `Hidden` flag is part of the Office Open XML spec and is respected by Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so always save as `.docx` when you need reliable hiding.

### Can I hide other types of objects (pictures, tables)?

Yes. Any node derived from `Shape`—including pictures, text boxes, and even SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.

### Does hiding a shape affect document performance?

Negligibly. The shape is stored as XML markup, and Word skips rendering hidden objects during layout. If you embed many hidden objects, the file size grows, but rendering stays fast.

### How does this differ from using a bookmark or comment as a marker?

Bookmarks are invisible by design, but they’re meant for navigation, not visual placeholders. Comments appear in the margin. A hidden shape gives you a visual object (size, position) that you can later reveal or manipulate, which is handy for templating scenarios.

## Full Working Example

Below is the complete, copy‑and‑paste‑ready program. It includes all using directives, the hidden ellipse creation, and a verification step.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Running the program creates `HiddenEllipse.docx` in the execution folder. Open it—you’ll see a perfectly normal blank page, yet the hidden ellipse lives quietly inside.

## Recap

We’ve covered how to **create a blank word document**, **hide a shape**, **create hidden object**, and **create ellipse shape** all with a handful of C# lines. The key takeaway is the `Hidden` property on `Shape`, which turns any visual element into an invisible marker without breaking Word compatibility.

## What’s Next?

- **Style the hidden shape** (fill color, line style) so when you later reveal it, it looks exactly as intended.  
- **Combine hidden shapes with bookmarks** to build dynamic templates that can be toggled on or off.  
- **Explore other shape types**—rectangles, arrows, or even custom SVG paths—by swapping `ShapeType.Ellipse`.  

Feel free to experiment: change the size, move the position, or insert multiple hidden ellipses. The same pattern works for any Aspose.Words shape you need to keep out of sight.

If you hit a snag or have ideas for extending this pattern, drop a comment below. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}