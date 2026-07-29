---
category: general
date: 2026-07-29
description: draw rectangle word using Aspose.Words. Learn how to add rectangle shape,
  add line shape, and manage multiple shapes word in a single document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: en
lastmod: 2026-07-29
og_description: draw rectangle word with Aspose.Words. Follow this step‑by‑step guide
  to add rectangle shape, add line shape, and work with multiple shapes word effortlessly.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: draw rectangle word – Master Adding Shapes in Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: draw rectangle word – Add Shapes in Word with Aspose
url: /net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Complete Guide to Adding Shapes in Word

Ever wondered how to **draw rectangle word** documents without opening the UI every time? You’re not alone. Many developers need to generate Word files on the fly, and the easiest way is to let a library do the heavy lifting. In this tutorial we’ll show you exactly **how to add shapes**—specifically a rectangle and a line—using Aspose.Words for .NET, and we’ll keep the focus on the phrase *draw rectangle word* so you never get lost.

Think of it as a mini‑art studio that lives inside your code. By the end you’ll be able to **add rectangle shape**, **add line shape**, and even combine them into **multiple shapes word** groups. No UI, no manual fiddling, just clean, repeatable C#.

## What You’ll Learn

- Set up a new Word document with Aspose.Words.  
- Create a **GroupShape** that can hold several objects.  
- **Add rectangle shape** and **add line shape** inside that group.  
- Insert the grouped shapes into the document body.  
- Save the file and see the result instantly.  

If you’re comfortable with basic C# and have a copy of Aspose.Words, you’re ready. No extra NuGet packages beyond the core library are required.

> **Pro tip:** Aspose.Words works with .NET 6, .NET 7, and .NET Framework 4.6+. Choose the runtime that matches your project.

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – Setting Up the Document

Before we can **draw rectangle word** we need a clean canvas. The `Document` class is that canvas; the `DocumentBuilder` is our brush.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

The two lines above give us a fresh, in‑memory `.docx`. Nothing is written to disk yet, which means we can experiment without cluttering the file system.

## How to Add Shapes – Creating a GroupShape Container

When you want **multiple shapes word** to behave as a single unit—move together, rotate together—you wrap them in a `GroupShape`. Think of a group as a folder that holds other shapes.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Why a group? Because later you might want to **add rectangle shape** and **add line shape** and then move them together. Without a group, you'd have to reposition each shape individually.

## add rectangle shape – Inserting a Rectangle Inside the Group

Now that the container exists, let’s **add rectangle shape**. A rectangle is a `Shape` whose `ShapeType` is `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Notice the `Left` and `Top` values are relative to the group's origin, not the page. This makes it easy to line up shapes precisely. The rectangle will appear near the top‑left corner of the group.

## add line shape – Adding a Line to the Same Group

A line is just another `Shape`, but its `ShapeType` is `Line`. We’ll position it below the rectangle.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Because the line’s height is zero, the `Top` property determines where the line sits vertically. The `Width` controls how long the line stretches horizontally.

## multiple shapes word – Inserting the Group into the Document Body

We have a group that now holds **add rectangle shape** and **add line shape**. The final step is to drop the whole thing into the document.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` places the group exactly where the `DocumentBuilder` is currently positioned. If you need it at a specific paragraph, move the builder with `builder.MoveToParagraph(index)` first.

## Saving the Result – Seeing the draw rectangle word Output

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Open the generated file in Microsoft Word and you’ll see a single group containing a rectangle and a line. You can click the group, drag it around, or even resize it—all the shapes move together. That’s the power of **multiple shapes word**.

### Expected Output

- A `.docx` file named `GroupShape.docx`.  
- One page with a grouped rectangle (120 × 80 pt) near the top‑left corner.  
- A horizontal line (150 pt long) positioned just below the rectangle.  
- Both shapes are selectable as a single object.

If you double‑click the group, Word will let you edit each shape individually—perfect for fine‑tuning.

## Common Questions & Edge Cases

**What if I need more than two shapes?**  
Just keep calling `group.AppendChild(yourShape)` for each additional object. The group can hold any number of shapes, making it ideal for complex diagrams.

**Can I change the fill color of the rectangle?**  
Absolutely. After creating the rectangle, set `rectangle.FillColor = System.Drawing.Color.LightBlue;`. This works for any shape that supports filling.

**Do I have to set `Height = 0` for a line?**  
Yes, for a straight horizontal line the height should be zero. For a vertical line, set `Width = 0` and give `Height` a positive value.

**Will this work with .doc files (Word 97‑2003)?**  
Aspose.Words can save to the older `.doc` format, but some modern shape features may be limited. Stick to `.docx` for full fidelity.

**How do I rotate the whole group?**  
You can set `group.Rotation = 45;` (degrees) before inserting it. The rotation applies to every child shape.

## Recap – How to Add Shapes in Word Programmatically

- **draw rectangle word** starts with creating a `Document` and `DocumentBuilder`.  
- Build a **GroupShape** to hold **multiple shapes word**.  
- **add rectangle shape** and **add line shape** are appended to the group.  
- Insert the group into the body with `builder.InsertNode`.  
- Save the file and open it to verify the visual result.

That’s the entire workflow, wrapped in a single, easy‑to‑read code listing.

## Next Steps & Related Topics

Now that you know **how to add shapes**, consider exploring:

- **add rectangle shape** with rounded corners (`ShapeType.Rectangle` + `CornerRadius`).  
- Styling lines with different dash patterns (`line.LineFormat.DashStyle`).  
- Embedding images alongside shapes for richer reports.  
- Using **multiple shapes word** to build flowcharts or simple UML diagrams.  

Each of these topics builds naturally on the foundation we laid out here, and they all follow the same pattern of creating shapes, configuring them, and grouping them if needed.

---

Happy coding! If you run into quirks or have a cool use‑case to share, drop a comment below. Your feedback helps us all master the art of **draw rectangle word** and beyond.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}