---
category: general
date: 2025-12-29
description: Create rectangle shape in a Word document using Aspose.Words C#. Learn
  to set shape transparency, set shadow color, and save word document effortlessly.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: en
og_description: Create rectangle shape in a Word document with Aspose.Words C#. This
  guide shows how to set shape transparency, set shadow color, and save word document.
og_title: Create rectangle shape in Word – Complete Aspose.Words Tutorial
tags:
- Aspose.Words
- C#
- Word Automation
title: Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide
url: /net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Word – Complete Aspose.Words Tutorial

Ever needed to **create rectangle shape** in a Word document but weren’t sure where to start? You’re not alone; many developers hit this wall when automating reports or invoices. In this guide we’ll walk through the exact steps to create a rectangle shape, set shape transparency, set shadow color, and finally **save word document** using Aspose.Words for .NET.  

We’ll cover everything from the initial document object to the final `.docx` file on disk, so by the end you’ll be able to **create word document** programmatically without guessing. No external references, just a self‑contained solution you can copy‑paste into your project.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.7+)
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- Basic familiarity with C# syntax
- An IDE of your choice (Visual Studio, Rider, VS Code, etc.)

> **Pro tip:** If you’re using a free trial of Aspose.Words, the library will add a watermark to the output file. For production you’ll need a valid license.

## Step 1: Initialize the Document and Builder

The first thing we do is create a fresh, empty Word document and a `DocumentBuilder` that lets us insert content. Think of the builder as a virtual pen that draws on the page.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this matters:** Without a `DocumentBuilder` you’d have to manipulate the low‑level node tree directly, which is error‑prone and harder to read.

## Step 2: Create rectangle shape

Now we actually **create rectangle shape**. The `InsertShape` method takes a `ShapeType` enum, width, and height (in points). The returned `Shape` object lets us tweak visual properties later.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

At this point the rectangle is a solid black box anchored to the current paragraph. You can move it, resize it, or even rotate it later if you need.

![create rectangle shape with shadow](/images/rectangle-shadow.png "A Word document showing a rectangle shape with a gray shadow")

*Image alt text: create rectangle shape with shadow in a Word document*

## Step 3: Set shape transparency

Transparency is the “see‑through” level of the shape’s fill. Aspose.Words uses a `Transparency` property ranging from `0.0` (opaque) to `1.0` (fully transparent). Here we **set shape transparency** to 40 % so the underlying text stays readable.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Edge case:** If you need a completely invisible shape but still want the shadow to appear, set `Transparency` to `1.0` and give the shape a non‑zero outline width.

## Step 4: Configure the shadow

A subtle drop shadow adds depth. We’ll **set shadow color** to a medium gray, adjust its blur radius, and offset it by a few points both horizontally and vertically.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Why this matters:** A shadow that’s too sharp or too dark can look like a printing artifact. Adjust `Blur` and `Transparency` until it feels natural.

## Step 5: Save the Word document

Finally we **save word document** to disk. The `Save` method automatically determines the file format from the extension; `.docx` is the modern OpenXML format.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

If the folder doesn’t exist, Aspose.Words will throw an `ArgumentException`. Make sure the path is valid or create the directory beforehand.

## Full Working Example

Below is the complete, ready‑to‑run program that puts all the steps together. Copy this into a new console project and hit **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Expected result

Open `ShadowRectangle.docx` in Microsoft Word. You should see a light‑gray rectangle with a soft, slightly offset shadow, both rendered at 40 % transparency. The shape sits on a blank page, ready for additional content.

## Common Questions & Variations

**What if I need a different shape?**  
Replace `ShapeType.Rectangle` with any other enum value (`Ellipse`, `Triangle`, `Star`, etc.). The rest of the code stays the same.

**Can I change the outline color?**  
Yes—use `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` and optionally set `rectangleShape.StrokeWeight = 1.5;`.

**How do I place the shape at a specific location on the page?**  
Set `rectangleShape.WrapType = WrapType.None;` and then adjust `rectangleShape.Left` and `rectangleShape.Top` properties (values are in points).

**Is it possible to add text inside the rectangle?**  
Absolutely. After creating the shape, you can call `rectangleShape.AppendChild(new Paragraph(document))` and then add a `Run` with your text. Remember to set `rectangleShape.TextBox` properties if you want richer formatting.

## Pro Tips & Pitfalls

- **License early:** If you forget to apply a license, Aspose.Words will insert a watermark on the first page, which can be confusing during testing.
- **Performance tip:** When generating many documents in a loop, reuse a single `Document` instance and call `document.RemoveAllChildren();` after each save to avoid excessive GC pressure.
- **Shadow visibility:** On low‑resolution screens a subtle shadow may appear invisible. Increase `Blur` or `OffsetX/Y` for debugging, then dial back for production.

## Next Steps

Now that you know how to **create rectangle shape**, **set shape transparency**, **set shadow color**, and **save word document**, consider extending the tutorial:

- Add multiple shapes and group them.
- Insert the rectangle inside a table cell for a report layout.
- Combine the shape with `DocumentBuilder.InsertHtml` to overlay HTML‑styled content.
- Explore other visual effects like `Glow` or `Reflection` for richer UI‑like documents.

Experiment, break things, and then refine—programmatic document generation is a playground where visual design meets code.

---

*Happy coding! If you ran into any snags, drop a comment below and we’ll troubleshoot together.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}