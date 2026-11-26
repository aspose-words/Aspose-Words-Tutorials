---
category: general
date: 2026-03-22
description: Create rectangle shape in C# and add shadow to shape with Aspose.Words.
  Learn how to add shadow, how to create rectangle, and how to set shadow properties.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: en
og_description: Create rectangle shape in C# and add shadow to shape using Aspose.Words.
  Step‑by‑step guide covering how to add shadow, how to create rectangle, and how
  to set shadow.
og_title: Create rectangle shape with shadow in C# – Full Guide
tags:
- Aspose.Words
- C#
- Document Automation
title: Create rectangle shape with shadow in C# using Aspose.Words
url: /net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape with shadow in C# using Aspose.Words

Ever needed to **create rectangle shape** in a Word document but weren’t sure how to give it a subtle drop‑shadow? You’re not alone—many developers hit that snag when they first dabble with document automation. In this guide we’ll walk through exactly how to **add shadow to shape** using Aspose.Words, and we’ll also answer “**how to add shadow**”, “**how to create rectangle**”, and “**how to set shadow**” along the way.

We’ll start with a clean‑slate `Document`, draw a rectangle, turn on its shadow, tweak the preset type, color, and transparency, and finally save the file. By the end you’ll have a ready‑to‑use `.docx` that shows a gray‑toned rectangle floating just above the page. No mystery, just straight‑forward code you can copy‑paste into any .NET project.

## Prerequisites

Before we dive in, make sure you have:

* **Aspose.Words for .NET** (the latest version as of March 2026). You can grab it from NuGet with `Install-Package Aspose.Words`.
* A .NET development environment – Visual Studio, Rider, or even VS Code with the C# extension works fine.
* Basic C# knowledge – nothing fancy, just the ability to create a console or WinForms app.

That’s it. No extra libraries, no hidden steps. Ready? Let’s get started.

## Step 1: Initialize a new empty document

To **create rectangle shape**, we first need a container – a `Document` object – that represents the Word file.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

The `Document` class is the entry point for everything Aspose.Words does. Think of it as a blank canvas; without it you can’t add any shapes, tables, or text.

## Step 2: Create the rectangle that will hold the shadow

Now we’ll **how to create rectangle** by instantiating a `Shape` of type `Rectangle`. We also set its size in points (1 point ≈ 1/72 inch).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Why pick 200 × 100 points? It’s a decent size for a demo – large enough to see the shadow clearly, but not so huge that it overwhelms the page. Feel free to adjust these numbers to match your layout.

## Step 3: Enable the shadow effect and configure its appearance

Here’s the heart of the tutorial: **how to add shadow** and **how to set shadow** properties. Aspose.Words exposes a `ShadowFormat` object on every shape, letting you toggle the effect and tweak the visual parameters that are supported.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.ShadowFormat.Type = ShadowType.Shadow7;               // choose a preset shadow
rectangleShape.ShadowFormat.Color = System.Drawing.Color.Gray;     // shadow colour
rectangleShape.ShadowFormat.Transparency = 0.5;                    // 0 = opaque, 1 = fully transparent
```

* **Type** selects one of the predefined shadow presets (`Shadow1` … `Shadow43`). Choosing a preset automatically defines the blur, distance, and angle.
* **Color** lets you pick any `System.Drawing.Color`. Gray is a safe default, but you could use `Color.Black` or any other colour.
* **Transparency** controls how opaque the shadow is (0 = fully opaque, 1 = invisible).

Pro tip: If you leave `ShadowFormat.Type` at its default (`ShadowMixed`), no shadow will be rendered.

## Step 4: Insert the shape into the document body

With the rectangle ready and its shadow configured, we need to place it into the document. The simplest way is to append it to the first paragraph of the first section.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

If your document already contains text, you could locate a specific `Paragraph` or even a `Table` cell and insert the shape there. The `AppendChild` method is versatile – it works with any `Node` type.

## Step 5: Save the document and verify the result

Finally, we write the file to disk. Change the path to wherever you like; the folder must exist, otherwise you’ll get an exception.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Open the resulting `ShadowedRectangle.docx` in Microsoft Word (or LibreOffice) and you should see a gray rectangle with a crisp, diagonal shadow. If the shadow looks too faint, increase the `Transparency` value (closer to 0) or pick a different preset type and re‑run the code – experimentation is part of the fun.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Create rectangle shape with shadow example"}

### Expected output

* A single‑page Word document.
* A 200 × 100‑point gray rectangle positioned at the top‑left of the page.
* A subtle gray shadow defined by the chosen `ShadowType` preset.

## How to add shadow to shape – deeper dive

You might wonder, *“Can I animate the shadow or make it change based on user input?”* While Aspose.Words itself doesn’t support animation, you can programmatically adjust the shadow properties before saving, effectively creating multiple versions of the same document with different looks. For instance, looping over a collection of colours:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.ShadowFormat.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

That tiny snippet demonstrates **how to set shadow** dynamically—great for generating themed reports.

## How to create rectangle – alternative shapes

If you need a rounded rectangle, simply switch the `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.ShadowFormat.Type = ShadowType.Shadow7; // shadow works the same way
```

Or, for a perfect square, set `Width` equal to `Height`. The same shadow properties apply, so you’re already covered on **how to add shadow** for any shape you choose.

## Common pitfalls and troubleshooting

| Symptom | Likely cause | Fix |
|---------|--------------|-----|
| No shadow appears | `ShadowFormat.Type` left as `ShadowMixed` (default) | Set `rectangleShape.ShadowFormat.Type` to a concrete `ShadowType` value |
| Shadow looks too faint | `Transparency` set too high | Decrease `Transparency` (e.g., `0.3`) |
| Document throws `FileNotFoundException` on save | Destination folder doesn’t exist | Create the folder first or use a valid path |
| Shape is invisible | Width/Height set to 0 | Ensure both dimensions are > 0 |

Keeping an eye on these issues saves you from the classic “why isn’t my shape showing?” moment.

## Recap – what we’ve accomplished

* **Create rectangle shape** in a new Word document using Aspose.Words.  
* **Add shadow to shape** by configuring the `ShadowFormat` (preset type, colour, transparency).  
* Demonstrated **how to add shadow**, **how to create rectangle**, and **how to set shadow** in a clean, reusable code snippet.  
* Provided a complete, ready‑to‑run example that you can paste into any C# project.

## What’s next?

Now that you’ve mastered the basics, consider exploring:

* **How to add shadow to images** – the same `ShadowFormat` API works for `ShapeType.Image`.
* **Combining multiple shapes** – create flowcharts or infographics directly in Word.
* **Exporting to PDF** – call `document.Save("output.pdf")` after adding shadows for a printable version.

Feel free to experiment with different colours, presets, or even gradient fills. The API is flexible enough to let you craft professional‑looking documents without ever opening Word manually.

---

Happy coding! If you run into any hiccups, drop a comment below or check the Aspose.Words forums – the community is quick to help.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}