---
category: general
date: 2026-07-23
description: Create blank word document and add rectangle shape in C#. Learn how to
  insert shapes and group shapes word using Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: en
lastmod: 2026-07-23
og_description: Create blank word document in C# and learn how to insert shapes, add
  rectangle shape, and group shapes word with Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Create blank word document with grouped rectangles – C# tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Create blank word document with grouped rectangles – C# guide
url: /java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank word document with grouped rectangles – C# guide

Ever needed to **create blank word document** that already contains a set of shapes, but weren't sure how to get them grouped nicely? You're not the only one. In many reporting or template‑generation scenarios you want a clean canvas with a couple of rectangles acting as placeholders, and you’d like them to move together as a single unit.

In this tutorial we’ll walk through the exact steps to **create blank word document**, **add rectangle shape**, and then **group shapes word** using the Aspose.Words library. By the end you’ll have a ready‑to‑use `.docx` file where the two rectangles are part of a group, so any later positioning or resizing affects them both at once.  

We’ll also answer the common “**how to insert shapes**” and “**how to group shapes**” questions that pop up on forums and Stack Overflow. No external docs required—everything you need is right here.

---

## Prerequisites

- .NET 6 or later (the code compiles with .NET Core as well)  
- Aspose.Words for .NET (NuGet package `Aspose.Words`)  
- A basic understanding of C# syntax (if you’ve written a “Hello World”, you’re good)  

If you haven’t installed Aspose.Words yet, run:

```bash
dotnet add package Aspose.Words
```

That’s it—no extra DLLs, no COM interop, just a clean NuGet reference.

---

## Step 1: Create blank word document and initialize the builder

The first thing we do is spin up an empty `Document` object. Think of it as a fresh piece of paper. Then we attach a `DocumentBuilder`, which is the handy tool Aspose provides for inserting content.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** Without a `DocumentBuilder` you’d have to manipulate the low‑level node tree manually, which is error‑prone. The builder abstracts away the XML intricacies of a `.docx` file.

---

## Step 2: How to insert shapes – add a group container first

Aspose lets you insert a *group shape* that can later hold other shapes. This is the foundation for **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Pro tip:** The group itself is invisible until you add child shapes, so you won’t see any artefacts in the resulting document until the next step.

---

## Step 3: Add rectangle shape – the actual visible objects

Now we’ll **add rectangle shape** twice, each with its own size. The `InsertShape` method takes a `ShapeType` and dimensions in points (1 pt ≈ 1/72 inch).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Why rectangles?** They’re the simplest geometric shape, perfect for placeholders, button‑like UI mocks, or simple graphic elements.

---

## Step 4: How to group shapes – attach rectangles to the group

With the rectangles created, we now **how to group shapes** by appending them as children of the group shape we inserted earlier.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **What happens under the hood?** The group shape becomes the parent node in the document’s XML tree. Moving the group moves both rectangles together, preserving their relative positions.

---

## Step 5: Save the document – you now have a grouped‑shape Word file

Finally, we persist the document to disk. Change the path to a location that exists on your machine.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

That’s the whole program. Run it, open `GroupShape.docx`, and you’ll see two rectangles sitting together. If you select one, the entire group is highlighted—exactly what **group shapes word** is supposed to do.

---

## Full source code in one place

For convenience, here’s the complete, copy‑paste‑ready example:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Expected output:** Opening `GroupShape.docx` shows a blank page with two rectangles grouped together. Selecting one rectangle automatically selects the other, confirming that the grouping succeeded.

---

## Common questions & edge‑case handling

### What if I need more than two shapes?

Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)` for each new shape. The group can hold any number of children.

### Can I set fill colour or border on the rectangles?

Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`, and `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### How do I move the whole group after it’s been created?

Use the group's `Left` and `Top` properties, measured in points:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### What about scaling the group?

Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`. The child rectangles retain their proportions relative to the group.

### Does this work with older .doc files?

Aspose.Words abstracts the file format, so the same code works for `.doc` and `.docx`. The only limitation is that some newer shape features may be down‑sampled when saving to the older binary format.

---

## Pro tips for production‑ready code

- **Dispose of resources** – Wrap `Document` in a `using` block if you’re dealing with large files to free memory promptly.  
- **Error handling** – Catch `Aspose.Words.Fonts.FontSettingsException` if you plan to embed custom fonts.  
- **Performance** – When inserting many shapes, disable layout updates temporarily with `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` and re‑enable afterward.

---

## Conclusion

You now know **how to create blank word document**, **add rectangle shape**, and **group shapes word** using Aspose.Words in C#. The example covers the essential “**how to insert shapes**” and “**how to group shapes**” steps, explains why each line exists, and even touches on customization, edge cases, and best practices.

Next, you might explore **how to insert images**, **add text inside grouped shapes**, or **export the document to PDF**—all of which follow the same pattern of using `DocumentBuilder` and shape manipulation. Keep experimenting; the Aspose API is rich enough to handle almost any Word automation scenario you can imagine.

Happy coding, and feel free to drop a comment if you hit any snags!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}