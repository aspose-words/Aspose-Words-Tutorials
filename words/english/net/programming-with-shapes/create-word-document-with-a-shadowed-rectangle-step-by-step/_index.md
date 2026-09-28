---
category: general
date: 2026-01-13
description: Create word document using Aspose.Words and learn how to insert rectangle
  shape, how to add shadow, and add shape shadow in C#. Complete example included.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: en
og_description: Create word document with Aspose.Words, see how to insert rectangle
  shape and how to add shadow. Follow the complete C# example.
og_title: Create Word Document with a Shadowed Rectangle – Full Tutorial
tags:
- Aspose.Words
- C#
- Document Automation
title: Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide
url: /net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide

Ever needed to **create word document** that contains a nicely shaded rectangle, but weren’t sure where to start? You’re not the only one—many developers hit the same wall when they first play with Aspose.Words.  

In this tutorial we’ll walk through everything you need to **create word document** programmatically, **insert rectangle shape**, and show **how to add shadow** so the shape really pops. By the end you’ll have a ready‑to‑run C# snippet that you can drop into any .NET project.

## What You’ll Learn

- The exact code to **how to insert shape** (a rectangle) into a Word file.
- The properties you must tweak to **add shape shadow** and control its appearance.
- How to save the result and verify that the shadow is visible.
- A few practical tips and edge‑case notes that save you headaches later.

No external documentation required—everything is right here.

## Prerequisites

Before we dive in, make sure you have:

1. **.NET 6.0** (or any recent .NET version) installed.  
2. A **license** for Aspose.Words for .NET, or you can use the free evaluation mode for testing.  
3. A development environment—Visual Studio 2022 works great, but any editor that can compile C# will do.

That’s it. No extra NuGet packages beyond `Aspose.Words` are needed.

## Step 1 – Set Up the Project and Reference Aspose.Words

First, create a new console app and add the Aspose.Words package:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro tip:** If you’re using the free trial, remember to call `License.SetLicense` with your license file; otherwise the library will add a watermark.

## Step 2 – Initialise the Document Builder

Now we’ll start the actual **create word document** process. The `Document` class gives us a blank canvas, and `DocumentBuilder` lets us paint on it.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Why do we need a builder? It abstracts away the low‑level OpenXML details, so you can focus on *what* you want rather than *how* the file is structured. This is the core of **how to insert shape** quickly.

## Step 3 – Insert Rectangle Shape

Here’s where we actually **insert rectangle shape**. The rectangle will be 150 × 100 points (roughly 2 in × 1.3 in).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

The `InsertShape` method returns a `Shape` object, which we can further customise. At this point, the rectangle is just a solid white box—no shadow yet.

## Step 4 – How to Add Shadow (Add Shape Shadow)

Adding a shadow is surprisingly simple once you know which properties to touch. The `ShadowFormat` object controls visibility, color, blur, offset, and size.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

That block answers **how to add shadow** in plain English: turn it on, pick a colour, tweak transparency, offset, blur, and size. You can experiment with these numbers to get a heavy drop‑shadow or a whisper‑thin one.

### Common Variations

- **Different colours:** Use `Color.Black` for a classic drop shadow, or `Color.BlueViolet` for a stylised effect.  
- **Zero blur:** Set `BlurRadius = 0` for a crisp, sharp edge.  
- **Larger offsets:** Increase `OffsetX`/`OffsetY` to push the shadow farther away from the shape.

## Step 5 – Save the Document and Verify

Finally, write the document to disk. The file will be a standard `.docx` that any modern Word processor can open.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Open the resulting *ShadowRectangle.docx* in Microsoft Word. You should see a rectangle with a soft gray shadow offset to the bottom‑right—exactly what the code specified.

> **Expected output:** A single‑page Word file containing a 150 × 100‑point rectangle with a 30 % transparent gray shadow, offset by 5 pts, blurred by 4 pts, and sized at 75 % of the shape.

## Full Working Example

Putting everything together, here’s the complete, ready‑to‑run program:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Run the program (`dotnet run`) and you’ll have a fresh Word file with a nicely shadowed rectangle—perfect for reports, certificates, or any visual cue you need.

## Frequently Asked Questions (FAQs)

**Q: Can I insert other shapes (ellipse, star) and still use the same shadow code?**  
A: Absolutely. The `InsertShape` method accepts any `ShapeType` enum value. Once you have a `Shape` instance, the `ShadowFormat` properties work identically, so **how to add shadow** is shape‑agnostic.

**Q: What if I need the shadow on both sides of the shape?**  
A: Aspose.Words only supports a single drop shadow per shape. To simulate a double‑sided effect, duplicate the shape, offset each copy differently, and set one’s `ShadowFormat.Visible` to `false` while keeping the other’s shadow visible.

**Q: Does this work on .NET Framework 4.8?**  
A: Yes. The API is version‑agnostic; just reference the appropriate Aspose.Words DLL for your target framework.

## Tips & Pitfalls

- **Don’t forget to set `Visible = true`**—the shadow properties are ignored otherwise.  
- **Transparency values range from 0.0 (opaque) to 1.0 (fully transparent).** A common mistake is using `30` instead of `0.3`.  
- **Saving to a read‑only folder throws an exception.** Make sure the output directory is writable.

## Next Steps

Now that you know **how to insert shape**, **add shape shadow**, and **create word document** with Aspose.Words, you might want to explore:

- Adding **text inside the rectangle** using `builder.InsertParagraph()` before inserting the shape.  
- Applying **gradient fills** or **patterned borders** for richer visual styling.  
- Automating the generation of multiple pages, each with a different shaded shape, to build dynamic reports.

Feel free to experiment—changing the shadow’s colour, blur, or size can dramatically alter the look of your document.

---

*Ready to put this into production? Grab the code, tweak the parameters, and watch your Word files gain a professional polish in seconds.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}