---
category: general
date: 2026-01-03
description: Create rectangle shape in Word with C# and add shadow to shape. Learn
  how to insert shape in Word, add shadow to shape, and generate Word docs programmatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: en
og_description: Create rectangle shape in Word with C# and add shadow to shape. Follow
  this guide to insert shape in Word, configure shadows, and generate documents programmatically.
og_title: Create rectangle shape in Word using C# – Complete Tutorial
tags:
- C#
- Word Automation
- Aspose.Words
title: Create rectangle shape in Word using C# – Step‑by‑Step Guide
url: /net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Word using C# – Complete Tutorial

Ever needed to **create rectangle shape** in a Word document but weren't sure where to start? You're not alone—many developers hit the same snag when they want to **add shadow to shape** for that polished look. In this tutorial we’ll walk through the exact steps to **insert shape in Word**, apply a subtle shadow, and finally **c# generate word document** files you can ship to users.

We'll cover everything from setting up the project to tweaking shadow properties, and we’ll finish with a ready‑to‑run code sample. No fluff, just the practical bits that get the job done.

## What You’ll Learn

- How to **create rectangle shape** with Aspose.Words (or Open XML) in C#  
- The exact properties you need to **add shadow to shape** for depth  
- Where to place the shape using `DocumentBuilder`  
- How to save the file so it opens correctly in Microsoft Word  
- Tips, pitfalls, and variations for real‑world scenarios  

### Prerequisites

- .NET 6.0 or later (the code works on .NET Core and .NET Framework)  
- A NuGet package that can manipulate Word files – we’ll use **Aspose.Words for .NET** because its API is concise. If you prefer Open XML SDK, the concepts are the same, just the classes differ.  
- Visual Studio, VS Code, or any C# IDE you like  

> **Pro tip:** If you’re on a budget, Aspose offers a free trial that’s perfect for learning. Just replace the license line with a comment when you test.

## Step 1: Install the Word‑Processing Library

First, add the library to your project. Open a terminal in your solution folder and run:

```bash
dotnet add package Aspose.Words
```

If you’re using the Open XML SDK, the command would be `dotnet add package DocumentFormat.OpenXml`. The rest of this guide assumes Aspose.Words, but swapping the API calls is straightforward.

## Step 2: Create a New Blank Document

Now that the library is ready, we can **create rectangle shape** by starting with a clean `Document` object. Think of this as a fresh canvas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

The `DocumentBuilder` gives us a high‑level way to insert content without diving into low‑level node trees.

## Step 3: Insert the Rectangle Shape

With the builder in hand, we can **insert shape in Word**. The `InsertShape` method takes the shape type and its dimensions (width, height) in points.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

At this point the rectangle appears in the document, but it looks a bit flat. That's where the next step comes in.

## Step 4: Add Shadow to the Shape

Shadows give the shape a sense of depth. The `Shadow` object lets us fine‑tune blur, distance, angle, color, and transparency. Below is a full configuration that works well for most reports.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Why these values?**  
- **BlurRadius** of `5.0` keeps the edge smooth without looking fuzzy.  
- **Distance** of `4.0` offsets the shadow just enough to be noticeable.  
- **Angle** `45` mimics natural lighting from the top‑left, a common UI convention.  
- **Transparency** `0.3` prevents the shadow from overpowering the shape’s fill.

If you need a more dramatic effect, increase `BlurRadius` and lower `Transparency`. For a subtle, almost‑invisible lift, flip those numbers.

## Step 5: Save the Document

Finally, write the file to disk. The `Save` method detects the format from the file extension, so `.docx` gives you the modern Word format.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Open `ShadowRectangle.docx` in Microsoft Word, and you’ll see a crisp rectangle with a soft shadow—exactly what you wanted when you asked “**how to add shape**” with a professional finish.

![Create rectangle shape with shadow in Word](placeholder-image.png "Create rectangle shape with shadow in Word")

*Image alt text: create rectangle shape with shadow in Word*

## Full Working Example

Putting it all together, here’s the complete, ready‑to‑run program. Copy‑paste into a console app and hit **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Expected Result

- The generated `ShadowRectangle.docx` contains **one rectangle shape** centered where the cursor was positioned.  
- The rectangle displays a **soft, 30 % transparent black shadow** offset at a 45° angle.  
- No other content is added, keeping the file lightweight and easy to embed in larger reports.

## Common Questions & Edge Cases

### What if I need a different shape?

Replace `ShapeType.Rectangle` with any other `ShapeType` enum value (e.g., `Ellipse`, `Triangle`). The shadow API works the same way, so you can reuse the configuration.

### How do I change the fill color?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Can I add the shape to a specific paragraph?

Yes. Move the `DocumentBuilder` to the target paragraph with `builder.MoveToParagraph(index)` before calling `InsertShape`. This ensures the shape appears exactly where you need it.

### What about older Word formats (.doc)?

Just change the extension:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

The shadow feature is supported in Word 2003 and later, so you’ll still see the effect.

### Using Open XML SDK instead of Aspose?

The steps remain: create a `WordprocessingDocument`, add a `Drawing` element, set `<a:shadow>` properties. The XML is more verbose, but the same concepts (size, blur, distance, angle) apply.

## Tips to Avoid Pitfalls

- **Don’t forget the license** if you’re using a paid Aspose version; otherwise you’ll get a watermark.  
- **Units are points**, not pixels. A typical screen pixel ≈ 0.75 pt, so adjust dimensions accordingly.  
- **Shadow properties are ignored** if the shape’s `WrapType` is set to `Inline`. Use `WrapType = WrapType.Square` for floating shapes that respect shadow rendering.  
- **Saving to a network share** may require proper permissions; always test the path first.

## Conclusion

You now know how to **create rectangle shape** in a Word document using C#, **add shadow to shape**, and **c# generate word document** files that look polished out of the box. The core steps—install the library, instantiate `Document`, insert the shape, configure the shadow, and save—are easy to remember and adaptable to other shapes, colors, or even dynamic data.

What’s next? Try layering multiple shapes, embedding images, or generating a full report with tables and charts. You can also explore conditional formatting—changing shadow intensity based on data values—to make your documents not just functional but visually engaging.

Feel free to experiment, and if you run into quirks, drop a comment below. Happy coding, and may your Word docs always have that perfect drop shadow!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}