---
category: general
date: 2026-09-11
description: Learn how to hide shape in Word using C#. This guide also shows how to
  insert rectangle shape and insert shape into Word document with Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: en
lastmod: 2026-09-11
og_description: How to hide shape in Word using C# and Aspose.Words. Follow the step‑by‑step
  tutorial to insert rectangle shape and manage shapes in a Word document.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: How to hide shape in Word – complete C# guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: How to hide shape in Word with C# and Aspose.Words
url: /java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to hide shape in Word with C# and Aspose.Words

If you need to hide shape in Word while keeping the shape in the document structure, this tutorial shows you exactly how. Using Aspose.Words for .NET you can insert a rectangle shape, hide it, and still retain its position for later processing.

Word automation often requires fine‑grained control over shapes—whether you are generating templates, preparing reports, or building a document‑editing service. By the end of this guide you will be able to:

* Insert a rectangle shape into a Word document (`insert rectangle shape`).
* Hide any shape without deleting it (`how to hide shape in word`).
* Save the result and verify that the hidden shape does not appear in the rendered view (`insert shape into word document`).

The example works with Aspose.Words 24.10 or later and targets .NET 6.0+, but the concepts apply to earlier versions as well.

## Prerequisites

* **Aspose.Words for .NET** ≥ 24.10. You can obtain a free temporary license from the Aspose website.
* **.NET SDK** 6.0 or newer installed on your machine.
* A development environment such as Visual Studio 2022, VS Code, or Rider.
* Basic familiarity with C# and the Word Open XML concept (optional but helpful).

## How to hide shape in Word with Aspose.Words

Below is a complete, runnable program that demonstrates the entire workflow—from creating a document to inserting a rectangle shape and finally hiding it.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Explanation of each step

1. **Create a new document** – `Document` represents the Word file in memory. `DocumentBuilder` provides a fluent API for inserting content.
2. **Insert rectangle shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions are expressed in points (1 pt ≈ 1/72 in). This satisfies the `insert rectangle shape` requirement.
3. **Hide the shape** – Setting `Shape.Hidden = true` marks the shape as hidden in the Word markup (`<w:hidden/>`). The shape remains part of the document tree, so you can later unhide it or reference it programmatically. This is the core of `how to hide shape in word`.
4. **Save the file** – The document is written to `output.docx`. When opened in Microsoft Word, the rectangle will not be visible, but it still exists in the XML and can be inspected with a ZIP viewer or the Open XML SDK.

### Expected result

Open `output.docx` in Microsoft Word:

* The document appears empty—no visible shape.
* If you inspect the underlying XML (`word/document.xml`) you will find a `<w:pict>` element with a `<w:hidden/>` attribute, confirming that the shape is present but hidden.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

The hidden shape can be made visible again by setting `Hidden = false` and re‑saving the document.

## Insert rectangle shape into a Word document

While the primary goal is to hide a shape, many scenarios start with inserting a shape first. The `InsertShape` method supports many `ShapeType` values, including `Rectangle`, `Ellipse`, `Line`, and custom images.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Why use a rectangle?**  
A rectangle provides a clean, axis‑aligned container that can hold text, images, or other nested shapes. It is often used as a placeholder for dynamic content such as tables or charts. By inserting the rectangle first, you preserve layout consistency even after you hide it later.

## Insert shape into Word document – best practices

When you `insert shape into word document`, consider the following:

* **Set explicit dimensions** – Avoid relying on automatic sizing; specify width and height in points to ensure consistent layout across platforms.
* **Define positioning** – By default the shape is anchored to the current paragraph. Use `builder.MoveTo` or `builder.StartBookmark` to place it precisely.
* **Apply styling early** – Fill color, line style, and text wrapping affect the final appearance. Even hidden shapes benefit from proper styling because the markup remains unchanged.
* **Version compatibility** – The `Hidden` property is only available from Aspose.Words 24.10 onward. If you target an older version, you can manually add the `<w:hidden/>` attribute using the `Node` API.

### Manually adding the hidden attribute (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Complete end‑to‑end example

Putting everything together, here is a single program that:

1. Inserts a rectangle shape.
2. Hides the shape.
3. Inserts a visible ellipse for contrast.
4. Saves the document.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Running the program produces `demo_output.docx`. When opened, you will see only the coral ellipse; the green rectangle is present in the XML but hidden from view.

## Common questions and edge cases

**Q: Does hiding a shape affect pagination?**  
A: No. Hidden shapes are ignored by the layout engine, so they do not consume space. This is useful for placeholder content that should not affect page breaks.

**Q: Can I hide a shape that is part of a header or footer?**  
A: Yes. The same `Hidden` property works on shapes located anywhere in the document tree, including headers, footers, and even inside tables.

**Q: What if I need to hide multiple shapes at once?**  
A: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection and set `Hidden = true` for each target shape.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**Q: Is the hidden attribute preserved when converting to PDF?**  
A: When converting to PDF, hidden shapes are omitted by default, matching Word’s rendering behavior. If you need them in the PDF, you must unhide them before conversion.

## Tips and pitfalls

* **Pro tip:** Set `shape.WrapType = WrapType.None` before hiding if you later plan to unhide the shape without disturbing surrounding text.
* **Watch out for older Aspose.Words versions:** The `Hidden` property throws `NotSupportedException` before 24.10. Use the manual XML approach in that case.
* **Testing:** Always open the generated `.docx` in Word and use “Show XML markup” (Developer tab) to verify that the `<w:hidden/>` attribute is present.

## Conclusion

You now know how to hide shape in Word using C# and Aspose.Words, as well as how to insert rectangle shape and insert shape into Word document with full control over visibility. By leveraging the `Hidden` property you can keep shapes in the document model for later processing while presenting a clean view to end users.

Next, explore related topics such as **updating shape properties at runtime**, **converting hidden shapes to images**, or **using the Open XML SDK to manipulate hidden elements directly**. These extensions will deepen


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}