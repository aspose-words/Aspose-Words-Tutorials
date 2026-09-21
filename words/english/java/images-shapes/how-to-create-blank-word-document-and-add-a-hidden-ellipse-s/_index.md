---
category: general
date: 2026-09-21
description: Create blank Word document with a hidden ellipse using C#. Learn how
  to hide shape in Word and generate a hidden shape programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: en
lastmod: 2026-09-21
og_description: Create blank Word document with a hidden ellipse using C#. This guide
  shows how to hide shape in Word and build hidden shapes programmatically.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Create blank Word document with a hidden ellipse shape in C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: How to create blank Word document and add a hidden ellipse shape in C#
url: /java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create blank Word document and add a hidden ellipse shape in C#

If you need to **create blank Word document** that contains an invisible graphic, this guide shows you exactly how. By the end of the tutorial you’ll have a .docx file that looks empty but actually stores an ellipse shape that is hidden from the layout.

We’ll use Aspose.Words for .NET to build the document, insert an ellipse, hide it, and save the file. The steps also cover **how to create ellipse** objects, the proper way to **hide shape in Word**, and how to **create hidden shape** code that works with any .NET project.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* Visual Studio 2022 (or any C# editor)  
* An Aspose.Words for .NET license or a free evaluation copy  
* Basic familiarity with C# syntax  

No additional NuGet packages are required beyond `Aspose.Words`.

## Create blank Word document with Aspose.Words

The first step is to generate an empty Word file. This gives us a clean canvas where we can later insert hidden graphics.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Why we start with a blank document** – Starting from an empty file guarantees that no unwanted content interferes with the hidden shape. It also keeps the file size minimal, which is useful when the document is later used as a template.

## How to create ellipse inside the blank document

Next we need a `DocumentBuilder` to add content. The builder lets us place shapes precisely where we want them.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Explanation** – `ShapeType.Ellipse` tells Aspose.Words to draw a circular‑ish figure. The width and height are measured in points (1 pt ≈ 1/72 inch). You can adjust these values to fit your design needs.

## Hide shape in Word so it doesn’t appear in the layout

A shape that is hidden still lives in the document’s XML, which can be useful for metadata, conditional formatting, or later programmatic modifications. To hide it, we set the `Hidden` property to `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Why hide the shape** – Hidden shapes are ignored by the layout engine, so the page looks completely blank. However, the shape data persists, which can be useful for storing markers, bookmarks, or custom XML that downstream processes can read.

## Save the document with the hidden shape

Finally we write the file to disk. The saved `.docx` will open in Microsoft Word with no visible content, yet the hidden ellipse is still present.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verification** – Open the generated file in Word, then press `Alt+F9` to toggle field codes and `Ctrl+A` → `Ctrl+Shift+F9` to view hidden objects. You’ll see the ellipse in the document’s XML (`word/document.xml`) but nothing on the page.

---

## Full, runnable example

Below is the complete program you can copy‑paste into a new console project. It includes all `using` directives and the `Main` method so you can run it without additional scaffolding.

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
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Expected output** – When you run the program, the console prints the file path, and the resulting Word file contains no visible objects. If you inspect the document with a zip tool (`.docx` is a zip archive), you’ll find the `<w:pict>` element describing the ellipse inside `word/document.xml`.

---

## Common variations and edge cases

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **Different shape** | Replace `ShapeType.Ellipse` with `ShapeType.Rectangle`, `ShapeType.Line`, etc. | Allows you to hide other graphics while keeping the same workflow. |
| **Multiple hidden shapes** | Call `InsertShape` several times and set `Hidden = true` on each. | Useful for embedding a collection of markers or placeholders. |
| **Conditional visibility** | Use `shape.Visible = false` together with `shape.Hidden = true` for extra safety. | Some older Word versions respect `Visible` differently; setting both covers all cases. |
| **Saving to a stream** | Replace `doc.Save(path)` with `doc.Save(stream, SaveFormat.Docx)`. | Enables sending the document directly over HTTP or storing it in a database. |
| **Applying a style** | After insertion, modify `ellipse.FillColor`, `ellipse.LineWeight`, etc. before hiding. | The shape’s styling is retained in the XML, which can be useful for later un‑hiding. |

**Pro tip:** Always test the hidden shape on the target Word version (e.g., Word 2019, Word 365) because rendering quirks occasionally surface when hidden objects interact with complex page layouts.

---

## Frequently asked questions

**Q: Does hiding a shape affect document size?**  
A: The shape’s XML adds a few hundred bytes, which is negligible for most use cases. The file remains essentially the same size as a truly empty document.

**Q: Can I unhide the shape later programmatically?**  
A: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape, true)`), and set `shape.Hidden = false`.

**Q: Will the hidden shape appear when printing?**  
A: No. Hidden objects are excluded from the print layout, so the printed page stays blank.

**Q: Is this approach compatible with Office Open XML (OOXML) only?**  
A: The `Hidden` property is part of the OOXML spec, so any Word processor that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the hidden flag.

---

## Conclusion

You now know how to **create blank Word document**, **how to create ellipse**, **hide shape in Word**, and **create hidden shape** using Aspose.Words for .NET. The tutorial covered the full lifecycle—from initializing an empty file to inserting, hiding, and saving the shape—plus verification steps and common variations.

Next, you might explore:

* Adding hidden text boxes for metadata (`hide shape in word` technique applied to text)  
* Using custom XML parts to store structured data alongside hidden shapes  
* Converting the hidden‑shape document to PDF while preserving the hidden elements  

Experiment with different shapes and visibility settings to see how hidden content can serve as a lightweight data store inside Word files.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}