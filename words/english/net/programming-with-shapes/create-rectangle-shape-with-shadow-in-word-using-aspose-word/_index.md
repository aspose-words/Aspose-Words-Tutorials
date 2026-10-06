---
category: general
date: 2026-03-06
description: Create rectangle shape in Word and add shape shadow with Aspose.Words.
  Learn how to insert rectangle in Word and how to add shadow to shape in C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: en
og_description: Create rectangle shape in Word and add shape shadow with Aspose.Words.
  Step‑by‑step guide on how to insert rectangle in Word and how to add shadow to shape.
og_title: Create rectangle shape with shadow in Word using Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Create rectangle shape with shadow in Word using Aspose.Words
url: /net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape with shadow in Word using Aspose.Words

Ever needed to **create rectangle shape** in a Word document but weren’t sure how to give it that polished look? You’re not alone—most developers hit the same snag when they first try to add visual flair to automated docs. The good news? With Aspose.Words for .NET you can both **create rectangle shape** and **add shape shadow** in just a few lines of C#.

In this tutorial we’ll walk through exactly **how to insert rectangle in Word**, then show **how to add shadow to shape** so it pops off the page. By the end you’ll have a ready‑to‑save `Shadow.docx` that you can open in Word and see a gray‑tinted rectangle with a soft drop shadow. No extra image files, no manual tweaking—just code.

## What You’ll Learn

- The exact C# statements needed to **create rectangle shape** with Aspose.Words.  
- How to enable and configure a shadow using the `Shadow` object.  
- Why each property matters (e.g., `Transparency`, `Blur`, `Angle`).  
- Common pitfalls (units, version compatibility) and quick fixes.  
- A complete, copy‑and‑paste‑ready program you can run today.

### Prerequisites

- .NET 6+ (or .NET Framework 4.7+).  
- Aspose.Words for .NET 23.10 or later (the NuGet package is `Aspose.Words`).  
- A basic understanding of C# and Visual Studio (or any IDE you prefer).  

If you already have those, let’s jump straight in.

---

## Step 1: Set up the project and import namespaces

First, create a new console app (or reuse an existing one) and add the Aspose.Words NuGet package:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Now bring the required namespaces into your `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** If you’re targeting .NET 6+, you can enable global `using` directives to avoid repeating these lines in every file.

---

## Step 2: **Create rectangle shape** in a blank Word document

We’ll start with a fresh `Document` object and a `DocumentBuilder` to manipulate it. The builder’s `InsertShape` method is where the magic happens.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Why 200 × 100 points? In Word, a point equals 1/72 of an inch, so the rectangle ends up roughly 2.8 × 1.4 inches—big enough to notice but not overwhelming. You can change these numbers to suit your layout; just remember they’re measured in **points**, not pixels.

---

## Step 3: **Add shape shadow** – configuring the look

Now that we have a rectangle, let’s give it a subtle gray shadow. The `Shadow` object lives on the `Shape` and exposes several handy properties.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### What each property does

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | Turns the shadow on/off | `true` or `false` |
| **Color** | Base colour of the shadow | Any `System.Drawing.Color` |
| **Transparency** | Opacity (0 = solid, 1 = invisible) | 0.0 – 1.0 |
| **Blur** | Softness of the edge | 0 – 10 (higher = softer) |
| **Distance** | Gap between shape and shadow | 0 – 20 points |
| **Angle** | Direction the light appears to come from | 0 – 360 degrees |
| **Size** | Scale of the shadow relative to the shape | 0 – 200 % |

> **Why bother with these settings?**  
> Fine‑tuning the shadow lets you match corporate branding guidelines (e.g., a subtle 20 % transparency for a professional look) without resorting to external image editors.

---

## Step 4: Save the document and verify the result

Finally, write the file to disk. You can choose any folder you like; just replace `YOUR_DIRECTORY` with a real path.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Open `Shadow.docx` in Microsoft Word and you should see a gray rectangle with a gentle drop shadow offset at a 45° angle. That visual cue makes the shape feel “lifted” off the page—exactly what you’d expect from a polished report or invoice.

---

## Full Working Example

Below is the complete program you can copy‑paste into `Program.cs`. No pieces are missing; it compiles and runs as‑is.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Expected Output

- **File:** `Shadow.docx` placed in the project’s execution folder.  
- **Visual:** A single rectangle centered on the page, filled with the default white, and a gray shadow offset 4 points to the lower‑right, blurred slightly for a natural look.

---

## Common Questions & Edge Cases

### 1. What if I need a different unit (e.g., centimeters)?

Aspose.Words works in points, but you can convert centimeters to points with the simple formula:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Does this work with older Aspose.Words versions?

The `Shadow` API was introduced in version 14.0. If you’re on an older release, you’ll need to upgrade via NuGet. The rest of the code (creating shapes) has been stable for many years, so you won’t hit breaking changes.

### 3. Can I add a shadow to other shapes (e.g., circles)?

Absolutely—any `Shape` object exposes a `Shadow` property. Just replace `ShapeType.Rectangle` with `ShapeType.Ellipse` or `ShapeType.Cloud`, then apply the same shadow settings.

### 4. What if I need a colored shadow (e.g., blue for a brand)?

Swap `Color.Gray` with any `Color` you like:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Remember to adjust `Transparency` so the colour doesn’t become too dominant.

---

## 🎨 Visual Summary

![create rectangle shape with shadow in Word using Aspose.Words](image-placeholder.png "create rectangle shape with shadow in Word using Aspose.Words")

*Alt text: create rectangle shape with shadow in Word using Aspose.Words*

The screenshot (placeholder) shows the final document—just the rectangle and its soft gray shadow.

---

## Conclusion

You now know how to **create rectangle shape** in a Word file, **add shape shadow**, and fine‑tune every visual aspect using Aspose.Words for .NET. The short program we built covers the entire workflow—from

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}