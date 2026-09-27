---
category: general
date: 2026-09-27
description: Programmatically create a Word document with a group shape using Aspose.Words
  in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: en
lastmod: 2026-09-27
og_description: Programmatically create a Word document with a group shape using Aspose.Words.
  This tutorial walks you through the complete C# code, explains each step, and shows
  the final output.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Programmatically create a Word document with a group shape – C# guide
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Programmatically create a Word document with a group shape
url: /net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmatically create a Word document with a group shape

If you need to **programmatically create a Word document** that contains a grouped drawing, this guide shows you exactly how to do it with Aspose.Words for .NET. Whether you are building a contract generator, a report builder, or a form‑filling tool, you’ll learn the complete C# code, why each API call matters, and how to handle common edge cases.

Creating a grouped shape in Word can feel tricky because the Word object model treats group shapes as containers for other drawing objects. This tutorial not only answers **how to create group shape word** documents, but also demonstrates how to embed a plain‑text StructuredDocumentTag (SDT) inside the group so the shape can hold editable content.

## What you’ll accomplish

- Initialize a new blank Word document with `Document` and `DocumentBuilder`.
- Insert a `GroupShape` at the current cursor position.
- Add a plain‑text `StructuredDocumentTag` (SDT) to the group shape.
- Save the file as a `.docx` that can be opened in Microsoft Word.
- Understand the key properties of `GroupShape` and `StructuredDocumentTag` for future extensions.

### Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.7+).
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`).
- A C# IDE such as Visual Studio 2022 or VS Code with the C# extension.

---

## Programmatically create a Word document – set up the project

1. **Create a new console project**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Open the project in your IDE** and replace the content of `Program.cs` with the code shown in the next sections.

> **Pro tip:** Keep your project folder clean; Aspose.Words writes the output file to the working directory unless you provide an absolute path.

## Step 1: Initialize the document and builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Why this matters:**  
`Document` represents the whole Word file, while `DocumentBuilder` lets you position new elements without manually navigating the node tree. Setting page dimensions early ensures the group shape does not overflow the page.

## Step 2: Insert a GroupShape at the current cursor location

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Explanation:**  
A `GroupShape` is a drawing object that can hold other shapes, pictures, or text boxes. By setting `Width`, `Height`, `Left`, and `Top`, you control its exact placement on the page. The `InsertNode` method places the shape in the main document flow, behaving like a floating object.

## Step 3: Add a plain‑text StructuredDocumentTag (SDT) inside the group

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Why use an SDT?**  
StructuredDocumentTags are Word’s native content controls. They allow users to edit the text directly in the saved document, and they can be programmatically accessed later for data extraction. Placing an SDT inside a group shape lets you combine visual grouping with editable content.

## Step 4: Save the document

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Result:**  
Opening `GroupShapeDemo.docx` in Microsoft Word shows a floating rectangle (the group shape) containing a text placeholder that reads “Enter text here”. Users can click inside the shape and type directly.

### Expected output screenshot (conceptual)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

The outer box is the `GroupShape`; the inner gray area is the `StructuredDocumentTag`.

---

## How to create group shape word – additional considerations

### Adding more child shapes

You can enrich the group by appending additional drawing objects, such as pictures or text boxes:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Controlling wrapping style

If you need the group shape to stay behind text or to have tight wrapping, set the `WrapType` property:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Edge case: Empty group shape

A `GroupShape` without children renders as an invisible placeholder. Always verify that at least one child (e.g., an SDT or a picture) is added; otherwise Word may drop the group during saving.

### Compatibility note

Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`. If you target older versions, the `AppendChild` method may behave differently, and you might need to call `UpdatePageLayout` after saving.

---

## Complete runnable example

Copy the entire snippet below into `Program.cs` and run the project. The code includes all the steps above in a single, self‑contained program.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}