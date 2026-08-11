---
category: general
date: 2026-08-10
description: Create word document programmatically using Aspose.Words, learn how to
  group multiple shapes word, add rectangle to word, and create a group shape in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: en
lastmod: 2026-08-10
og_description: Create word document programmatically with Aspose.Words. This guide
  shows you how to group multiple shapes word, add rectangle to word, and embed a
  plain‑text content control, all in C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Create word document programmatically – group shapes in C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Create word document programmatically and group shapes in C#
url: /net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create word document programmatically and group shapes in C#

If you need to **create word document programmatically**, this tutorial shows you how to build a DOCX file with Aspose.Words and **group multiple shapes word** together. We'll also cover **add rectangle to word** and **how to create group shape** that contains both a rectangle and an ellipse, plus a plain‑text StructuredDocumentTag for user input.

You’ll finish with a ready‑to‑use Word file that contains a grouped rectangle‑ellipse shape and a content control where a user can type a name. No manual editing in Word is required after the code runs.

## What you’ll need

- .NET 6.0 or later (the sample targets .NET 6, but any recent .NET version works)
- An Aspose.Words for .NET license (the free trial works for testing)
- Visual Studio 2022 or any C# IDE you prefer
- Basic familiarity with C# syntax

## Create word document programmatically – overall workflow

The process consists of three logical phases:

1. **Initialize** a `Document` and a `DocumentBuilder` – the foundation for any Word file you generate.
2. **Build a group shape** that holds a rectangle and an ellipse – demonstrates **group multiple shapes word** and **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – a plain‑text content control that lets end users fill in data, illustrating **add rectangle to word** as part of the overall document layout.

Below is the complete, runnable code followed by a step‑by‑step breakdown.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Step 1 – Initialize the document and builder
The `Document` object represents the entire DOCX file, while `DocumentBuilder` provides a convenient API to add content. Initializing them is the first requirement whenever you **create word document programmatically**.

> **Pro tip:** If you plan to reuse the same document across multiple operations, keep a single `DocumentBuilder` instance to avoid unnecessary object creation.

### Step 2 – Create a group shape container
A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes. Setting `Width` and `Height` defines the bounding box for the group. This is the core of **how to create group shape** in Aspose.Words.

> **Edge case:** If the group’s width is smaller than the combined width of its children, the children will be clipped. Always make the group large enough to contain every child shape.

### Step 3 – Add a rectangle to word
A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top` properties position it relative to the group’s origin. This step demonstrates **add rectangle to word** and shows how you can control exact placement.

> **Common mistake:** Forgetting to set `Left`/`Top` results in the rectangle appearing at the group’s default origin (0,0), which may overlap other children.

### Step 4 – Add an ellipse (circle) to the group
An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`. The `Left = 210` moves it to the right of the rectangle, creating a visually distinct pair of shapes inside the same group.

> **Why use a group?** Grouping lets you move, rotate, or resize both shapes together with a single operation later on, preserving their relative layout.

### Step 5 – Insert the completed group shape into the document
`builder.InsertNode(groupShape)` places the whole group at the current cursor location. Because the group already contains its children, you do not need additional insert calls for the rectangle or ellipse.

### Step 6 – Create a plain‑text StructuredDocumentTag (SDT)
A StructuredDocumentTag is a content control that end users can fill in when the document is opened in Word. Setting `Title = "CustomerName"` gives the control a meaningful identifier, which is useful for later data extraction.

> **Why a plain‑text SDT?** It restricts input to plain text, preventing accidental formatting that could break downstream processing.

### Step 7 – Save the document
`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX contains the grouped shapes and the SDT. Opening the file in Microsoft Word will show a rectangle next to a circle, both selectable as a single object, followed by a placeholder “Enter name here …”.

#### Expected output
- A file named **GroupAndSDT.docx** in the execution folder.
- In Word: a grouped shape (rectangle + ellipse) that you can move as one unit.
- Directly below the group, a gray‑shaded content control prompting the user to type a name.

## Additional variations and best practices

### Using different shape types
You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic remains identical.

### Setting fill color and borders
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Adding fill and stroke improves visual distinction, especially when the document is shared with non‑technical stakeholders.

### Rotating the entire group
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Rotating the group is more efficient than rotating each child individually.

### Exporting to PDF
If you need a PDF version, simply call:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
All grouped shapes and the SDT (rendered as a text field) will appear in the PDF.

## Common pitfalls and how to avoid them

| Symptom | Cause | Fix |
|---------|-------|


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}