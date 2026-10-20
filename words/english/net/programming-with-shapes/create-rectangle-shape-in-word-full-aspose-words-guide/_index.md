---
category: general
date: 2026-02-26
description: Create rectangle shape in Word using Aspose.Words and learn how to add
  shape to Word, apply shadow to shape, and set shape transparency in minutes.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: en
og_description: Create rectangle shape in Word using Aspose.Words. Learn to add shape
  to Word, apply shadow to shape, and set shape transparency quickly.
og_title: Create Rectangle Shape in Word – Full Aspose.Words Guide
tags:
- Aspose.Words
- C#
- Word Automation
title: Create Rectangle Shape in Word – Full Aspose.Words Guide
url: /net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Rectangle Shape in Word – Full Aspose.Words Guide

Ever needed to **create rectangle shape** in a Word document but weren’t sure where to start? You’re not alone—many developers hit that wall when automating reports or invoices. In this tutorial we’ll walk through a complete, ready‑to‑run example that shows you how to **add shape to Word**, apply a subtle shadow, and control the shape’s transparency, all with Aspose.Words for .NET.

By the end of the guide you’ll have a `.docx` file containing a clean rectangle with a polished shadow—perfect for branding, call‑outs, or just making your document look a little more professional. No external tools required, just a few lines of C#.

## What You’ll Need

- **Aspose.Words for .NET** (the latest version as of early 2026). You can grab it from NuGet (`Install-Package Aspose.Words`).
- A .NET development environment (Visual Studio, Rider, or VS Code with the C# extension).
- Basic familiarity with C# syntax—nothing fancy, just the usual `using` statements and object creation.

If you already have those, great—let’s dive in.

## Create Rectangle Shape – Core Steps

Below is the full source code. Copy‑paste it into a new console project, hit **F5**, and you’ll see `ShadowDemo.docx` appear in the folder you specify.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Why This Works

- **`Document`** is the entry point; it represents the entire Word file.
- **`Shape`** with `ShapeType.Rectangle` tells Aspose we want a rectangular drawing object.
- Setting **`Width`** and **`Height`** gives the shape a deterministic size; otherwise it defaults to a tiny placeholder.
- The **`Shadow`** object lets us fine‑tune every visual aspect: blur, distance, direction, colour, transparency, and spread. That’s the heart of *apply shadow to shape*.
- Finally, **`AppendChild`** injects the shape into the document’s first paragraph, which is the simplest way to *add shape to Word* without dealing with tables or headers.

When you open `ShadowDemo.docx`, you’ll see a gray rectangle sitting comfortably in the document, its shadow slanting down‑right at a 45° angle. The shadow isn’t a solid block; the blur radius softens the edges, and the transparency makes it look like a natural drop shadow rather than a harsh overlay.

![create rectangle shape example](image.png "create rectangle shape with shadow in Word using Aspose.Words")

*(The image above shows the final result of the code snippet.)*

## Add Shape to Word Document – Placement Options

The example uses the **first paragraph** because it’s the quickest way to see something on screen. In real‑world scenarios you might want to:

- Insert the shape into a specific **section** or **header/footer**.
- Place it inside a **table cell** for alignment with tabular data.
- Wrap it with **text wrapping** options (e.g., `WrapType.Square`) so that surrounding text flows around the rectangle.

Here’s a quick variation that puts the shape into a new paragraph with a custom style:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Pro tip:* Always add the shape **after** you configure its properties; otherwise you may need to call `UpdateLayout` to refresh the visual appearance.

## Apply Shadow to Shape – Fine‑Tuning the Look

Shadows can dramatically change a document’s aesthetics. The `Shadow` class exposes several properties:

| Property      | What It Controls                                   | Typical Values |
|---------------|----------------------------------------------------|----------------|
| `BlurRadius`  | Softness of the shadow edges                      | 2.0 – 10.0      |
| `Distance`    | How far the shadow is offset from the shape        | 1.0 – 8.0       |
| `Direction`   | Angle in degrees (0 = left, 90 = up)              | 0 – 360         |
| `Color`       | Shadow colour (any `System.Drawing.Color`)        | Gray, Black, Custom |
| `Transparency`| Opacity (0 = fully opaque, 1 = invisible)        | 0.0 – 0.5       |
| `Spread`      | Expansion of the shadow before blur is applied    | 0.0 – 1.0       |

If you want a **subtle, professional look**, keep `BlurRadius` around 4‑6 and `Transparency` near 0.2, just like the code above. For a **dramatic effect**, bump `Distance` to 6, set `Direction` to 135°, and turn `Transparency` down to 0.05.

## Set Shape Transparency and Shadow Spread

Transparency isn’t just about the shadow; you can also make the rectangle itself partially see‑through:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Combining a semi‑transparent fill with a soft shadow often yields a modern UI feel—great for dashboards or design mock‑ups embedded in reports.

### Edge Cases to Watch

1. **Older Word versions** (pre‑2007) don’t support some shadow properties. If you target `.doc` files, consider simplifying the shadow (e.g., set `BlurRadius` to 0).
2. **High DPI displays** may render the shadow slightly differently. Test on the target environment if visual fidelity is critical.
3. **Overlapping shapes**—Aspose renders shadows in the order they’re added. Insert shapes from back to front to avoid unwanted occlusion.

## Save and Verify the Result

The `Document.Save` method automatically detects the output format from the file extension. For a **`.docx`** file you get the Open XML format, which most modern Word processors understand. If you need a **PDF** version with the same visual styling, just change the extension:

```csharp
document.Save("ShadowDemo.pdf");
```

Opening the generated `ShadowDemo.docx` (or `ShadowDemo.pdf`) should show a clean **rectangle with shadow**, confirming that you’ve successfully *create rectangle shape* and *apply shadow to shape* using Aspose.Words.

## Frequently Asked Questions

**Q: Can I use a different shape, like an ellipse?**  
A: Absolutely. Swap `ShapeType.Rectangle` with `ShapeType.Ellipse` (or any other `ShapeType` enum). The shadow properties remain the same.

**Q: What if I need the rectangle to be clickable?**  
A: You can assign a hyperlink to the shape:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Does this work on .NET 6+?**  
A: Yes. Aspose.Words 23.11 and later fully support .NET 6, .NET 7, and .NET 8. Just reference the appropriate NuGet package.

**Q: How do I change the shadow colour to match my brand?**  
A: Use any `System.Drawing.Color` you like:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Wrap‑Up

We’ve covered everything you need to **create rectangle shape** in a Word document, **add shape to Word**, **apply shadow to shape**, and **set shape transparency**. The complete, runnable code sits at the top of this page, and the explanations should give you enough confidence to tweak sizes, colours, and shadow parameters for any project.

Ready for the next step? Try experimenting with:

- Multiple shapes layered together for a badge effect.
- Dynamic sizing based on document content (e.g., calculate width from a table column).
- Exporting the document to PDF or HTML while preserving the shadow.

Feel free to drop a comment if you hit any snags, or share your own variations on the “rectangle with shadow” theme.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}