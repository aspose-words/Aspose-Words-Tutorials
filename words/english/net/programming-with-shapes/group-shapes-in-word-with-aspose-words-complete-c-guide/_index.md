---
category: general
date: 2026-07-19
description: Group shapes in Word using Aspose.Words. Learn how to add rectangle shape,
  define ellipse shape, and insert shape into Word documents.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: en
lastmod: 2026-07-19
og_description: Group shapes in Word with Aspose.Words. Master adding rectangle shape,
  defining ellipse shape, and inserting shape into Word documents.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Group Shapes in Word – Step‑by‑Step C# Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Group Shapes in Word with Aspose.Words – Complete C# Guide
url: /net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Group Shapes in Word – Complete C# Guide

Ever wondered how to **group shapes in Word** without fiddling with the UI? You're not alone. Whether you're generating contracts, flyers, or diagrams programmatically, being able to **add rectangle shape**, **define ellipse shape**, and then **group shapes in Word** can save you hours of manual work.

In this tutorial we’ll walk through a real‑world example using **Aspose.Words for .NET**. By the end you’ll know exactly how to **insert shape into Word**, combine them, and produce a polished document that you can ship to clients or teammates.

---

## What You’ll Need

Before we dive in, make sure you have the following:

- **Aspose.Words for .NET** (latest version, e.g., 24.9). You can grab it from NuGet with `Install-Package Aspose.Words`.
- A .NET development environment (Visual Studio 2022 or VS Code with the C# extension works fine).
- Basic familiarity with C# syntax—nothing fancy, just the usual `using` statements and object creation.

That’s it. No extra libraries, no COM interop, just pure managed code.

---

## How to Group Shapes in Word Using Aspose.Words

Below is a step‑by‑step breakdown that mirrors the code you already have. Each step explains **why** we’re doing it, not just **what** the line does, so you can adapt the pattern to any shape you like.

### Step 1: Set Up the Document and Builder

We start by creating an empty `Document` and a `DocumentBuilder`. The builder is our “pen” that lets us insert content wherever we need it.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why?** The `Document` object represents the whole .docx file, while `DocumentBuilder` provides a convenient API for inserting nodes (like shapes) without dealing with the underlying node tree.

### Step 2: Add Rectangle Shape (add rectangle shape)

Now we **add rectangle shape** to the document. We set its size, position, and fill colour to make it stand out.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** You can change `FillColor` to any `System.Drawing.Color` you prefer. This is useful when you need colour‑coded sections in a report.

### Step 3: Define Ellipse Shape (define ellipse shape)

Next, we **define ellipse shape**. Notice the different `ShapeType` and the offset (`Left = 120`) so the ellipse sits beside the rectangle.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Why this matters:** By positioning shapes explicitly, you control how they appear before you group them. If you rely on automatic layout, the grouping might look off‑center.

### Step 4: (Optional) Insert Individual Shapes for Preview

If you want to see each shape before grouping, you can **insert shape into Word** individually. This step is optional but handy for debugging.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Comment out these two lines once you’re confident the shapes look right; otherwise you’ll end up with duplicate visuals after grouping.

### Step 5: How to Group Shapes – Create a GroupShape

Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`, attach our rectangle and ellipse, and decide how the group behaves with surrounding text.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explanation:** `GroupShape` is essentially a mini‑canvas that holds other shapes. By setting `WrapType` to `Inline`, the whole group moves as a single unit when you add or delete text.

### Step 6: Insert the Grouped Shape into the Document (insert shape into word)

Now we **insert shape into Word**—but this time it’s the grouped container, not the individual pieces.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **What happens under the hood?** The `InsertNode` call adds the `GroupShape` to the document’s node collection. Because the group already contains the rectangle and ellipse, they appear together as one object.

### Step 7: Save the Document

Finally, write the file to disk. You can change the path to suit your project layout.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Result:** Open `GroupShape.docx` in Microsoft Word and you’ll see a light‑blue rectangle and a coral ellipse locked together. Dragging one moves the other—exactly what “group shapes in word” promises.

---

## Visual Confirmation

Below is a mock‑up of what the grouped shapes look like inside the Word file.  

![Screenshot of grouped shapes in a Word document created with Aspose.Words](grouped_shapes_placeholder.png "group shapes in word")

*The image’s alt text contains the primary keyword for accessibility and SEO.*

---

## Common Questions & Edge Cases

### What if I need more than two shapes?

Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting the group. The API imposes no limit on the number of child shapes.

### Can I rotate or resize the whole group?

Absolutely. `GroupShape` inherits from `Shape`, so you can set properties like `RotationAngle`, `Width`, or `Height` on the group itself, and all child shapes will follow.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### How do I change the group’s background colour?

Use `groupShape.FillColor`. This fills the invisible bounding box; it can be handy for highlighting.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Does this work with older Word formats (.doc)?

`Aspose.Words` can save to `.doc` as well—just replace the file extension in `Save`. However, some advanced shape features (like grouping) are only fully supported in the OOXML `.docx` format.

---

## Full Working Example

Copy‑paste the following block into a new console app to see the whole process in action. No pieces are missing; this is a **complete, runnable example**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Expected output:** When you open `GroupShape.docx`, you’ll see a single grouped object consisting of a light‑blue rectangle and a light‑coral ellipse, perfectly aligned side‑by‑side.

---

## Recap

We’ve just covered everything you need to **group shapes in Word** with Aspose.Words:

1. Create a document and builder.  
2. **Add rectangle shape** and **define ellipse shape** with explicit dimensions.  
3. (Optionally) **insert shape into Word** for a quick preview.  
4. Use `GroupShape` to **how to group shapes**—append each child, set wrapping, and insert.  
5. Save the file and verify the


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}