---
category: general
date: 2026-11-15
description: Learn how to programmatically insert a shape and group multiple shapes using the Aspose.Words DocumentBuilder for .NET, including examples for inserting rectangle shapes and multiple shapes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: en
lastmod: 2026-11-15
og_description: How to insert shape in a Word file using Aspose.Words. This guide
  covers grouping multiple shapes, inserting rectangle shape, and adding multiple
  shapes efficiently.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: How to insert shape and group multiple shapes with DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: How to insert shape and group multiple shapes using Aspose.Words DocumentBuilder in C#
url: /net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to insert shape and group multiple shapes using Aspose.Words DocumentBuilder in C#

If you need to know **how to insert shape** into a Word document with Aspose.Words, this guide shows you the exact steps. You’ll also learn how to **group multiple shapes** so they behave as a single object, and how to **insert rectangle shape** alongside other graphics.

Document automation often requires adding several graphics—charts, logos, call‑outs—while keeping them organized. By the end of this tutorial you will be able to **insert multiple shapes**, place them inside a group, and save a clean, reusable layout.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later installed  
* Visual Studio 2022 (or any C# IDE)  
* An Aspose.Words for .NET license or a free evaluation key  
* Basic familiarity with C# and the Aspose.Words `DocumentBuilder` class  

You do **not** need any other third‑party libraries; everything needed is part of Aspose.Words.

## Step 1: install Aspose.Words via nuGet

Open your project in Visual Studio and run the following command in the Package Manager Console:

```powershell
Install-Package Aspose.Words
```

The package includes the `DocumentBuilder`, `Shape`, and `GroupShape` classes used throughout this tutorial.

## Step 2: Create a DocumentBuilder instance – the foundation for **how to insert shape**

The first actionable line of code is creating a `DocumentBuilder`. This object gives you direct access to the document tree, allowing you to place shapes exactly where you want them.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Why this matters*: `DocumentBuilder` maintains a cursor (the “insertion point”). Every subsequent `Insert...` call uses that cursor, which is why we later move it into a `GroupShape` to keep all shapes together.

## Step 3: **Insert rectangle shape** – the first graphic you’ll add

A rectangle is a common placeholder for tables, images, or call‑outs. Use `InsertShape` with `ShapeType.Rectangle` and specify width and height in points (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

The rectangle appears at the current cursor location. You can customize its fill, line style, or text later if required.

## Step 4: Insert another shape – an ellipse for visual variety

Adding more than one shape demonstrates **insert multiple shapes**. The ellipse will sit after the rectangle in the document flow.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

At this point the document contains two independent shapes. If you move the cursor or add text, the shapes stay where they were inserted.

## Step 5: **Group multiple shapes** so they act as a single unit

Grouping is essential when you need to move, rotate, or format several graphics together. The following code creates a `GroupShape`, moves the builder’s cursor inside it, and then inserts the same shapes again—this time they become children of the group.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Why use a group?

* **Single‑point transformation** – rotate or resize the whole group with one call.  
* **Logical organization** – the Word document tree reflects the grouping, making later edits easier.  
* **Consistent layout** – moving the group keeps the relative positions of its children intact.

### Adding more shapes – extending **insert multiple shapes** inside the group

You can keep calling `InsertShape` while the cursor remains inside the `GroupShape`. For example, to add a triangle:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Each call respects the group context, so the triangle automatically becomes part of the same grouped set.

## Step 6: Save the document and verify the result

After all shapes are placed, persist the document to a `.docx` file. Opening the file in Microsoft Word (or any compatible viewer) should show two separate shapes followed by a grouped set containing the same rectangle, ellipse, and triangle.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Expected output

* **First two shapes** – a rectangle and an ellipse placed independently on the page.  
* **Grouped block** – a rectangle, an ellipse, and a triangle that move together when you click any of them in Word.

You can test the grouping by selecting any shape inside the group; Word will highlight the entire collection, confirming that the **group multiple shapes** operation succeeded.

## Common pitfalls and pro tips

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Shapes appear outside the intended page | The builder’s cursor was not moved into the `GroupShape` before inserting. | Always call `builder.MoveTo(group)` **before** any `InsertShape` calls that belong to the group. |
| Group disappears after saving | The group was inserted without being added to the document’s node collection. | Use `builder.InsertNode(group)` immediately after creating the `GroupShape`. |
| Unexpected size because of document DPI | Aspose.Words uses points; if you think in pixels you may get mismatched dimensions. | Convert pixels to points (`points = pixels * 72 / 96`) or work directly in points. |
| Shapes overlap unintentionally | No explicit positioning was set; Word places them sequentially. | Set `Shape.Left` and `Shape.Top` after insertion to control exact placement. |

**Pro tip:** After grouping, you can retrieve the group’s `Shapes` collection (`group.Shapes`) to iterate, rename, or apply bulk formatting.

## Step 7: Extending the example – what’s next?

Now that you know **how to insert shape**, **insert rectangle shape**, and **group multiple shapes**, you can explore:

* **Animating grouped shapes** – set rotation or flip properties on the group.  
* **Applying styles** – use `Shape.FillColor`, `Shape.LineFormat`, or `Shape.TextBox` to add labels.  
* **Exporting to PDF** – the same grouped layout renders correctly when you call `doc.Save("output.pdf")`.  

All of these extensions reuse the same `DocumentBuilder` workflow, keeping your code clean and maintainable.

## Conclusion

This tutorial demonstrated **how to insert shape** into a Word document with Aspose.Words, how to **insert rectangle shape**, and how to **group multiple shapes** so they behave as a single object. By following the step‑by‑step code, you can reliably **insert multiple shapes**, organize them into groups, and produce professional‑grade documents programmatically.

Feel free to experiment with different shape types, colors, and group transformations. When you’re ready, integrate the pattern into larger reporting or templating solutions to automate complex document layouts. Happy coding!


## What should you learn next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [How to group shapes in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}