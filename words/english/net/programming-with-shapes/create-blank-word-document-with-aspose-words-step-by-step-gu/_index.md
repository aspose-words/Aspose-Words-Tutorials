---
category: general
date: 2026-02-23
description: Create blank word document using C# and Aspose.Words. Learn how to add
  rectangle shape, add shadow word, and save word with shape in minutes.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: en
og_description: Create blank word document quickly. This guide shows how to add rectangle
  shape, add shadow word, and save word with shape using Aspose.Words.
og_title: Create blank word document – Full C# Tutorial
tags:
- Aspose.Words
- C#
- Document Automation
title: Create blank word document with Aspose.Words – Step‑by‑Step Guide
url: /net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank word document – Full C# Tutorial

Ever wondered how to **create blank word document** programmatically without opening Microsoft Word? You're not alone. In many automation projects we need a fresh .docx file, drop a shape on it, give that shape a nice shadow, and then **save word with shape** for later use.  

In this guide we’ll walk through exactly that—starting from an empty document, **adding a rectangle shape**, configuring an **add shadow word** effect, and finally persisting the file. By the end you’ll have a complete, runnable snippet that you can paste into any .NET console app. No mystery, no missing pieces.

## What You’ll Need

- **Aspose.Words for .NET** (any recent version, e.g., 24.10).  
- .NET 6 or later (the code works with .NET Framework 4.7+ as well).  
- A basic C# IDE—Visual Studio, Rider, or even VS Code with the C# extension.  

That’s it. No extra NuGet packages beyond Aspose.Words, and no Word installation required.

---

## Step 1: Create a blank word document

The first thing you do when you want to **create blank word document** is instantiate the `Document` class. Think of it as a clean canvas that Aspose.Words hands to you.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Why this matters:** The `Document` object holds all sections, paragraphs, and shapes. Starting with an empty instance guarantees you control every element that gets added later.

---

## Step 2: Add a rectangle shape to the document

Now that we have a clean document, let’s **add rectangle shape**. A rectangle is a simple `Shape` with `ShapeType.Rectangle`. You can of course pick other types, but a rectangle works great for demonstration.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Pro tip:** If you ever wonder **how to add shape** that isn’t a rectangle, just change `ShapeType.Rectangle` to any other enum value like `ShapeType.Ellipse` or `ShapeType.Polygon`. The rest of the code stays the same.

---

## Step 3: Configure a custom shadow for the shape

A plain rectangle looks a bit dull, so we’ll **add shadow word** to make it pop. Aspose.Words exposes a `ShadowFormat` object with many properties.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Why this matters:** The shadow gives a subtle depth cue, especially when the document will be viewed on screen. Adjust `OffsetX`, `OffsetY`, and `BlurRadius` to suit your design language.

---

## Step 4: Insert the shape into the document

With the shape ready, we need to place it somewhere. The simplest spot is the first paragraph of the first section. If the document has no paragraphs yet, Aspose automatically creates one.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Edge case:** If you plan to insert the shape into a specific location (e.g., after a particular heading), locate the target `Paragraph` via `document.GetChildNodes(NodeType.Paragraph, true)` and use `InsertAfter` or `InsertBefore` accordingly.

---

## Step 5: Save the Word document with the shape

Finally, we **save word with shape** to disk. The `Save` method automatically determines the format from the file extension.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **What you’ll see:** Open `shadowedRectangle.docx` in Word (or any compatible viewer) and you’ll see a gray rectangle with a soft shadow sitting at the top of the first page.

---

## Full Working Example

Below is the complete program you can copy‑paste into a console app. It includes all using directives, comments, and the exact steps we discussed.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Run the program, navigate to `YOUR_DIRECTORY`, and open the generated `shadow.docx`. You should see the rectangle with a subtle gray shadow—exactly what we set out to achieve.

---

## Frequently Asked Questions & Tips

### How do I change the shape’s color?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Just set `FillColor` before appending the shape.

### What if I need multiple shapes on the same page?
Create additional `Shape` objects and append each to the same paragraph or to different paragraphs. You can also control layout using `WrapType` and `RelativeHorizontalPosition`.

### Can I export to PDF while keeping the shadow?
Absolutely. Use `document.Save("output.pdf")`—Aspose.Words preserves the shadow effect in the PDF conversion.

### Does this work on .NET Core?
Yes. Aspose.Words is cross‑platform; the same code runs on .NET Core, .NET 5+, and .NET Framework.

### How to add a shape without a paragraph?
You can add the shape directly to a `Run` or to a `Story`. For more precise positioning, set `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` and adjust `Left`/`Top` properties.

---

## Visual Result

![Rectangle shape with gray shadow in a Word document – add shadow word example](https://example.com/placeholder-image.png "add shadow word example")

*Image alt text includes the secondary keyword **add shadow word** to satisfy SEO.*

---

## Conclusion

We’ve just demonstrated how to **create blank word document**, **add rectangle shape**, apply an **add shadow word** effect, and finally **save word with shape** using Aspose.Words for .NET. The process is straightforward: instantiate a `Document`, build a `Shape`, tweak its `ShadowFormat`, insert it, and call `Save`.  

From here you can experiment—try different shape types, play with colors, or layer multiple shapes. If you need to merge this document with existing content, just load the existing file via `new Document("existing.docx")` and follow the same steps.  

Got more questions? Drop a comment, and happy coding!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}