---
category: general
date: 2026-04-04
description: Create rectangle shape in C# with Aspose.Words and learn how to add shadow,
  apply blur to shadow, and make shadow transparent – step‑by‑step guide.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: en
og_description: Create rectangle shape in C# with Aspose.Words. Learn how to add shadow,
  apply blur to shadow, and make shadow transparent in a concise tutorial.
og_title: Create rectangle shape and how to add shadow in C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Create rectangle shape and how to add shadow in C#
url: /net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape and how to add shadow in C#

Ever needed to **create rectangle shape** in a Word document but weren’t sure how to give it a subtle drop‑shadow? You’re not alone. In many reporting or branding scenarios a simple rectangle with a soft, semi‑transparent shadow can make the layout feel polished without a lot of effort.

In this tutorial we’ll walk through **how to create document** using Aspose.Words, then show **how to add shadow**, **apply blur to shadow**, and even **make shadow transparent**. By the end you’ll have a ready‑to‑run C# snippet that produces a *.docx* file with a nicely shaded rectangle—all in a few minutes.

## What you’ll need

- .NET 6 or later (the API works with .NET Framework 4.6+ as well)
- Aspose.Words for .NET (the free trial works for this example)
- A code editor – Visual Studio, VS Code, Rider, whatever you prefer
- Basic C# knowledge – nothing fancy, just the ability to run a console app

If you’ve got those, we can jump straight into the solution.

## Step 1 – How to create document and initialize the canvas

First things first: you need a blank `Document` object. Think of it as an empty piece of paper that Aspose.Words will later turn into a Word file.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Why do we instantiate `Document` instead of loading a template? Starting from scratch guarantees that no hidden styles or sections interfere with our rectangle. It also keeps the file size tiny – a good habit when you’re generating many docs in a loop.

## Step 2 – Create rectangle shape (the core of our primary keyword)

Now we actually **create rectangle shape**. The `Shape` class is flexible; you tell it the type (Rectangle), size, and how it should wrap with surrounding text.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Notice the use of object initializer syntax – it’s concise and reduces the chance of forgetting to set a property later. The rectangle will sit inside the first paragraph, which we’ll add in the next step.

## Step 3 – How to add shadow and customize its look

Adding a shadow isn’t just a single line; you have several properties to tweak. This is where the secondary keywords **apply blur to shadow** and **make shadow transparent** come into play.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

A quick note on the numbers: `BlurRadius` of 5 gives a gentle feathering; increase it to 10 for a softer look, or drop it to 2 for a crisp edge. The `Transparency` value ranges from 0 (opaque) to 1 (invisible). Adjust based on your brand’s contrast requirements.

### Pro tip

If you ever need a colored shadow (say a corporate blue), just replace `Color.DarkGray` with `Color.FromArgb(80, 0, 120, 215)`. The first argument is the alpha channel – keep it low for subtlety.

## Step 4 – Insert the shape into the document

With the rectangle and its shadow ready, we now place it into the document’s first paragraph. This step ensures the shape appears at the very top of the file.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Why the first paragraph? It’s a safe default that works even when the document is completely empty. If you have a specific location (e.g., after a heading), you would locate that node and insert the shape there instead.

## Step 5 – Save the file and verify the result

Finally, we persist the document to disk. You can choose any path you like; just make sure the folder exists.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

When you open *ShadowRectangle.docx* in Microsoft Word, you should see a 200 × 100‑point rectangle with a dark‑gray, slightly blurred, 30 % transparent shadow offset by three points to the right and down. The effect is subtle but adds depth to otherwise flat layouts.

![create rectangle shape with shadow in Aspose.Words](https://example.com/placeholder-image.png "create rectangle shape with shadow in Aspose.Words")

*Image alt text:* **create rectangle shape with shadow in Aspose.Words** – the picture shows the final document with the shaded rectangle.

## Common variations and edge cases

### Changing the shadow colour dynamically

If your application supports themes, you might pull the shadow colour from a configuration file:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Making the shape non‑inline

Sometimes you want the rectangle to float over text. Switch `WrapType` to `WrapType.Square` and set `RelativeHorizontalPosition` to `RelativeHorizontalPosition.Margin` for more control.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Handling multiple pages

If you need a rectangle on every page, loop through `doc.Sections` and append a cloned shape to each section’s first paragraph. Remember to call `rect.Clone(true)` to duplicate the shadow settings as well.

## Recap – What we accomplished

- **Created rectangle shape** using Aspose.Words
- **How to add shadow** with colour, offset, blur, and transparency
- Demonstrated **apply blur to shadow** and **make shadow transparent**
- Saved a Word file that you can open instantly

All of this was achieved with just a handful of lines, proving that sophisticated visual tweaks don’t always require heavyweight graphics libraries.

## What’s next?

- Experiment with other `ShapeType`s (Ellipse, Cloud, etc.) and see how shadows behave.
- Combine the rectangle with text boxes to build labeled call‑outs.
- Dive into **how to create document** templates that already contain placeholders for shapes, then populate them programmatically.

Feel free to tweak the blur radius, colour, or transparency until the shadow looks just right for your design language. The API is forgiving, and the changes are instantly visible when you re‑run the console app.

Happy coding, and may your documents always have that extra touch of depth!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}