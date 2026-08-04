---
category: general
date: 2026-08-04
description: Save docx file programmatically while add rectangle shape and group shapes
  in Word. Learn to set shape dimensions and create textbox programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: en
lastmod: 2026-08-04
og_description: Save docx file using C# by adding rectangle shape, grouping shapes
  in Word, setting shape dimensions, and creating textbox programmatically.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Save docx file with grouped shapes in Word – C# step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Save docx file with grouped shapes in Word using C#
url: /net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Save docx file with grouped shapes in Word using C#

If you need to **save docx file** that contains several shapes arranged together, this guide shows you how to do it with C#. You will learn how to **add rectangle shape**, group multiple shapes in a Word document, **set shape dimensions**, and **create textbox programmatically**. The solution works with the latest Aspose.Words for .NET and runs on .NET 6 or later.

The tutorial walks through every step, from project setup to the final `doc.Save` call. By the end you will have a reusable code snippet that you can paste into any console or ASP.NET project. No external scripts or manual editing of the DOCX file are required.

## Prerequisites

Before you start, make sure you have:

* .NET 6 SDK (or newer) installed.
* A valid license for **Aspose.Words for .NET** (the free trial works for testing).
* Visual Studio 2022, VS Code, or any IDE that can build .NET projects.

The code uses only the Aspose.Words namespace, so no additional NuGet packages are necessary.

## Save docx file with grouped shapes in Word

The core of the solution is building a `GroupShape` that contains a rectangle and a textbox, then inserting the group into the document and calling `doc.Save`. The following sections break the process into manageable pieces.

### 1. Create a new document and a builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step matters* – A fresh `Document` object represents an empty *.docx* file. `DocumentBuilder` supplies high‑level methods such as `InsertNode`, which we will use to place the group shape.

### 2. Add rectangle shape to a group

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Why this step matters* – The **add rectangle shape** operation demonstrates how to define a visual element with exact size and position. The rectangle lives inside `group`, so moving the group later moves the rectangle automatically.

### 3. Group shapes in Word document

The `GroupShape` class aggregates multiple drawing objects. Grouping is useful when you want to treat several objects as a single unit (e.g., moving, rotating, or copying them together).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Why we group* – Grouping reduces layout complexity. Instead of positioning each shape individually on the page, you adjust the group’s `Left`, `Top`, `Width`, and `Height` once.

### 4. Set shape dimensions for precise layout

Both the group and its child shapes need explicit dimensions; otherwise Word applies default sizes that may not match your design.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Why we set dimensions* – Precise measurement ensures that the rectangle and the textbox do not overlap unintentionally and that the final **save docx file** matches the intended layout.

### 5. Create textbox programmatically inside the group

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Why this step matters* – The **create textbox programmatically** segment shows how to embed rich text inside a shape. Using a `Paragraph` and `Run` gives you full control over formatting later on.

### 6. Insert group shape and **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Why this final step matters* – The `InsertNode` call places the grouped shapes exactly where the builder’s cursor resides. The `doc.Save` method performs the **save docx file** operation, writing a fully‑featured Word document to disk.

> **Result:** Opening *GroupShape.docx* in Microsoft Word displays a rectangle on the left and a textbox on the right, both locked together inside a single group. You can move the group as a unit, resize it, or apply additional formatting.

## Full, runnable example

Copy the code below into a new console project (`dotnet new console`) and run `dotnet run`. The program creates `GroupShape.docx` in the project’s output folder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Expected output

* A file named **GroupShape.docx** appears in the output directory.
* Opening the file shows a rectangular shape on the left and a textbox containing “Grouped text” on the right, both locked together.
* Selecting either shape moves the entire group, confirming that **group shapes word** functionality works as intended.

## Common variations and edge cases

| Situation | Recommendation |
|-----------|----------------|
| Need more than two shapes | Append additional `Shape` objects to `group` before calling `builder.InsertNode`. |
| Want the group to appear on a specific page | Move the builder’s cursor with `builder.MoveToDocumentEnd()` or `builder.MoveToPage(pageNumber)`. |
| Require different units (e.g., centimeters) | Use `ConvertUtil.InchToPoint(1.0)` to convert inches to points, the unit Word expects. |
| Want the textbox to wrap text | Set `textBox.TextBoxWrap = TextBoxWrapType.Square` after creating the textbox. |
| Working with older .NET Framework versions | The same API works with .NET Framework 4.7+, but ensure you reference the correct Aspose.Words version. |

**Pro tip:** Always set the group’s `Width` and `Height` *after* adding all child shapes. This guarantees the group fully encloses its contents, preventing clipping when the document is opened in Word.

## Conclusion

You now know how to **save docx file** while **add rectangle shape**, **group shapes word**, **set shape dimensions**, and **create textbox programmatically** using Aspose.Words for .NET. The complete example demonstrates a clean, repeatable pattern that you can adapt to more complex layouts, such as charts, images,


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}