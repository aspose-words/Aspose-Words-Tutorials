---
category: general
date: 2026-05-01
description: How to move shadow on a shape in Aspose.Words using C#. Learn to add
  shadow to shape, change blur, set transparency, and rotate shadow in minutes.
draft: false
keywords:
- how to move shadow
- add shadow to shape
- how to change blur
- how to set transparency
- how to rotate shadow
language: en
og_description: How to move shadow on a shape in Aspose.Words using C#. This tutorial
  shows you how to add shadow to shape, change blur, set transparency, and rotate
  shadow.
og_title: How to Move Shadow in Aspose.Words – Complete C# Guide
tags:
- Aspose.Words
- C#
- Document Automation
title: How to Move Shadow in Aspose.Words – Complete C# Guide
url: /net/programming-with-shapes/how-to-move-shadow-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Move Shadow in Aspose.Words – Complete C# Guide

Ever wondered **how to move shadow** on a shape inside a Word document without opening Word manually? In my day‑to‑day work, I’ve often needed to tweak a shape’s shadow programmatically—whether it’s for a polished report or a dynamic template. The good news? With Aspose.Words you can do it in a handful of lines, and you’ll also learn **add shadow to shape**, **how to change blur**, **how to set transparency**, and **how to rotate shadow** in the same pass.

In this tutorial we’ll walk through a real‑world scenario: loading an existing DOCX that already has a shape, adjusting the shadow’s position, softness, opacity, and direction, and finally saving the result. By the end you’ll have a reusable snippet that you can drop into any .NET project, and you’ll understand why each property matters.

## Prerequisites – What You Need Before You Start

- **Aspose.Words for .NET** (version 23.12 or later). You can grab it from NuGet with `Install-Package Aspose.Words`.
- A .NET 6+ development environment (Visual Studio, VS Code, Rider—whatever you prefer).
- An input Word file (`input.docx`) that already contains at least one shape (a rectangle, circle, or picture will do).
- Basic familiarity with C# syntax—nothing fancy.

If you’re missing any of those, pause for a moment and install the library; the rest of the guide assumes the package is already referenced.

## Step 1: Load the Document and Grab the Target Shape – **How to Move Shadow** Begins Here

The first thing we do is load the source document and locate the shape we want to modify. Aspose.Words treats every object (paragraphs, tables, shapes) as a node in a tree, so we can query it directly.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 📂 Load the source DOCX that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // 🎯 Retrieve the first shape in the document.
        // The GetChild method walks the node tree; the third argument (true) means “search deep”.
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        // If no shape is found, bail out early.
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // -------------------------------------------------
        // The next sections show **how to move shadow**,
        // **add shadow to shape**, **how to change blur**,
        // **how to set transparency**, and **how to rotate shadow**.
        // -------------------------------------------------
```

> **Why this matters:** Loading the document once and reusing the same `Document` instance is efficient. The `GetChild` call is safe because it returns `null` if the index is out of range, letting us handle missing shapes gracefully.

## Step 2: Adjust the Blur Radius – Master **How to Change Blur**

A soft shadow looks professional, while a hard edge can feel cheap. The `BlurRadius` property controls the softness in points (1 pt ≈ 1/72 inch). Let’s bump it up to 8 pt.

```csharp
        // Increase the blur radius to soften the shadow edges.
        shape.ShadowFormat.BlurRadius = 8.0; // 8 points ≈ 0.11 inches
```

> **Pro tip:** The default blur is 0.5 pt. Anything above 5 pt is usually noticeable, but beware of making it too large—it can make the shape look detached from the page.

## Step 3: Set Transparency – The Answer to **How to Set Transparency**

Transparency determines how see‑through the shadow is. A value of `0` means fully opaque; `1` means completely invisible. For a subtle effect we’ll use `0.3` (30 % transparent).

```csharp
        // Make the shadow semi‑transparent so the shape remains visible through it.
        shape.ShadowFormat.Transparency = 0.3; // 30% transparent
```

> **Why you might care:** If the shape is dark, a fully opaque shadow can drown the underlying text. Adjusting transparency keeps the document readable while still giving depth.

## Step 4: Move the Shadow – The Core of **How to Move Shadow**

The `Distance` property defines how far the shadow is offset from the shape, measured in points. A larger distance pushes the shadow farther away, creating a more dramatic effect.

```csharp
        // Move the shadow farther from the shape for a more pronounced effect.
        shape.ShadowFormat.Distance = 4.0; // 4 points ≈ 0.055 inches
```

> **What if you need a tiny offset?** Setting `Distance` to `0` will make the shadow sit directly behind the shape, which can be useful for embossing effects.

## Step 5: Rotate the Light Source – Solving **How to Rotate Shadow**

Shadows aren’t just straight down; they follow the light source’s angle. The `Angle` property (in degrees) rotates the shadow around the shape. Let’s tilt it 45°.

```csharp
        // Rotate the light source to change the shadow direction.
        shape.ShadowFormat.Angle = 45; // 45 degrees clockwise from the vertical axis
```

> **Quick experiment:** Try `90` for a right‑hand shadow or `-30` for a left‑leaning one. The visual change is immediate.

## Step 6: Save the Document – Seeing the Result of **Add Shadow to Shape**

Now that we’ve tweaked the shadow, we’ll write the document back to disk. You can overwrite the original or create a new file; the example uses a new output file.

```csharp
        // Save the modified document with the adjusted shadow.
        doc.Save(@"YOUR_DIRECTORY\output.docx");

        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

> **Expected output:** Open `output.docx`. The shape’s shadow will appear softer, slightly offset, semi‑transparent, and angled at 45°. If you compare it side‑by‑side with `input.docx`, the difference is unmistakable.

### Full Working Example (Copy‑Paste Ready)

Below is the entire program in one block. Paste it into a new console project, replace `YOUR_DIRECTORY` with an actual folder path, and run.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the source document that already contains a shape with a shadow.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

        // Retrieve the first shape in the document (the one we will modify).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 1️⃣ Change blur – soften the edges.
        shape.ShadowFormat.BlurRadius = 8.0;

        // 2️⃣ Set transparency – make it 30% see‑through.
        shape.ShadowFormat.Transparency = 0.3;

        // 3️⃣ Move the shadow – increase distance from the shape.
        shape.ShadowFormat.Distance = 4.0;

        // 4️⃣ Rotate the shadow – change light direction.
        shape.ShadowFormat.Angle = 45;

        // Save the result.
        doc.Save(@"YOUR_DIRECTORY\output.docx");
        System.Console.WriteLine("Shadow adjustments applied and saved to output.docx");
    }
}
```

## Common Questions & Edge Cases

### What if the document has multiple shapes?

You can loop through all shapes:

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    // Apply the same shadow settings or customize per shape.
}
```

### Can I add a shadow to a shape that currently has none?

Absolutely. The `ShadowFormat` object is always present; you just need to enable it:

```csharp
shape.ShadowFormat.Enabled = true;
```

### Does this work with pictures and SmartArt?

Yes. Any node that derives from `Shape`—including pictures, charts, and SmartArt—exposes `ShadowFormat`. The same properties apply.

### How do I control the shadow color?

Use the `Color` property:

```csharp
shape.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Compatibility concerns?

Aspose.Words 23.12+ supports .NET 6, .NET Core 3.1, and .NET Framework 4.6.2+. The API shown is stable across these versions.

## Conclusion

We’ve just covered **how to move shadow** on a shape using Aspose.Words, and along the way we also demonstrated **add shadow to shape**, **how to change blur**, **how to set transparency**, and **how to rotate shadow**. The complete, runnable example lets you tweak any shape’s shadow in a matter of seconds, giving your documents a polished, professional look without ever opening Word.

Ready for the next step? Try combining these shadow tweaks with **conditional formatting**—for example, only apply a deeper shadow to headings or to charts that exceed a certain size. Or explore **gradient fills** for the shape itself to create a truly eye‑catching design.

If you hit any snags, drop a comment below. Happy coding, and may your shadows always fall just where you want them! 

![Diagram showing the effect of moving a shadow on a shape – how to move shadow example](https://example.com/images/shadow-demo.png "how to move shadow example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}