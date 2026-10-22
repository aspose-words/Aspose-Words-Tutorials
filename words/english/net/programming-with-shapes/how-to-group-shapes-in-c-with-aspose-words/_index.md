---
category: general
date: 2026-08-23
description: Learn how to group shapes in C# using Aspose.Words. The guide also covers
  how to insert rectangle shape and add shapes word for complex documents.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: en
lastmod: 2026-08-23
og_description: How to group shapes in C# with Aspose.Words. Follow this complete
  tutorial to insert rectangle shape, add shapes word, and group multiple shapes efficiently.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: How to group shapes in C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: How to group shapes in C# with Aspose.Words
url: /net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in C# with Aspose.Words

If you need to **how to group shapes** in a Word document programmatically, this tutorial shows you the exact steps using Aspose.Words for .NET. Whether you are building a report generator, a template engine, or a diagramming tool, you’ll learn how to start a group, insert a rectangle shape, and add shapes word‑level content without leaving your code.

You’ll also see how to **group multiple shapes** together, which is essential when you want to move, rotate, or style a collection of objects as a single entity. The example below works with the latest Aspose.Words 24.x release and requires only .NET 6 or later.

## Prerequisites

- .NET 6 SDK (or any .NET version supported by Aspose.Words)
- Visual Studio 2022 or VS Code
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- Basic familiarity with C# and the Aspose.Words object model

> **Pro tip:** Use the free evaluation license from Aspose to avoid watermark limitations while testing.

## How to group shapes with Aspose.Words

Below is a complete, runnable program that demonstrates **how to start group**, add a rectangle, and finalize the group. The code follows the same logical flow as the snippet you provided, but it adds context, error handling, and comments for clarity.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Why each step matters

| Step | Purpose | How it relates to the keywords |
|------|---------|--------------------------------|
| **Create a new blank document** | Provides a clean canvas for shape operations. | Sets the stage for **add shapes word** later. |
| **Initialize DocumentBuilder** | The builder is the primary API for inserting objects. | Needed before you can **how to start group**. |
| **StartGroupShape** | Begins a logical container; all following shapes become members of this group. | Directly answers **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Places individual shapes inside the group. The rectangle call satisfies **insert rectangle shape**; the text shape satisfies **add shapes word**. | Demonstrates **group multiple shapes**. |
| **EndGroupShape** | Finalizes the group so you can move or style it as a unit. | Completes the **how to group shapes** workflow. |

## Inserting a rectangle shape – deeper dive

The `InsertShape` method accepts a `ShapeType` enum, width, and height. To **insert rectangle shape** with custom styling, you can extend the example:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Why style it?** Styling ensures the rectangle stands out when the group is later repositioned. It also demonstrates that shape properties can be set *before* the group is closed.

## Adding Word‑level shapes (add shapes word)

If you need to embed text directly inside a shape—commonly called “WordArt” or “text box”—use `ShapeType.TextPlainText`. After inserting, you can write text into the shape with `DocumentBuilder.Writeln` or by accessing the shape’s `TextBox` property:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

This satisfies the **add shapes word** keyword and shows how text can travel with the group.

## Grouping multiple shapes – practical scenarios

When you **group multiple shapes**, you can treat them like a single object for positioning, rotation, or scaling. For example, after the group is closed, you can move the whole group:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Or rotate the group:

```csharp
group.Rotation = 45; // degrees
```

These operations are only possible because the shapes share the same parent group.

## Handling edge cases

1. **Nested groups** – Aspose.Words allows groups within groups. To create a nested group, call `StartGroupShape` again before calling `EndGroupShape` for the inner group.
2. **Empty groups** – If you start a group but never insert a shape, `EndGroupShape` will still create an empty container. This is harmless but may increase file size slightly.
3. **Compatibility** – The generated DOCX works with Word 2010 and later. Older versions may ignore grouping metadata, so always test with the target Word version.

## Full source file for reference

Save the following as `Program.cs` in a .NET console project. The code compiles and runs without modification.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Expected output

Opening `GroupedShapes.docx` in Microsoft Word will show:

- A light‑coral rectangle, an ellipse, and a text box—all visually bound together.
- Selecting any part of the group also selects the entire group (a single bounding box appears).
- Moving or rotating the group moves all three shapes together.

## Frequently asked questions

**Q: Can I group shapes that already exist in the document?**  
A: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`, re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.

**Q: Does grouping affect the underlying XML?**  
A: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>` node. This is fully compliant with the Office Open XML specification.

**Q: What if I need to ungroup later?**  
A: There is no direct “ungroup” API, but you can iterate through the child shapes of the group (`group.GroupShape.Children`) and copy them out to the document body.

## Next steps

Now that you know **how to group shapes**, consider exploring these related topics:

- **Apply complex formatting to grouped shapes** – learn how to set gradient fills, shadow effects, and line styles.
- **Export grouped shapes as images** – use `Shape.GetShapeRenderer().Save(...)` to rasterize a group.
- **Create dynamic diagrams** – combine data‑driven positioning with grouping to generate flowcharts automatically.

Each of these builds on the foundation covered here and will help you create richer, more interactive Word documents.

---

*Happy coding! If you found this guide useful, share it with teammates or star the repository that contains the sample project.*


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}