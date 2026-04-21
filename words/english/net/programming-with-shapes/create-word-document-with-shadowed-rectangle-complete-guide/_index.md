---
category: general
date: 2026-04-21
description: Create word document with a styled rectangle and shadow. Learn how to
  add shadow, insert rectangle shape, set shadow color, and more in C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: en
og_description: Create word document and add a shadowed rectangle shape in C#. Follow
  this guide to set shadow color, blur, and offsets easily.
og_title: Create Word Document with Shadowed Rectangle – Step‑by‑Step
tags:
- Aspose.Words
- C#
- Document Automation
title: Create Word Document with Shadowed Rectangle – Complete Guide
url: /net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document with Shadowed Rectangle – Complete Guide

Ever needed to **create word document** that looks a bit more polished than a plain page of text? Maybe you’re building a report template or a flyer and a simple rectangle with a subtle shadow would do the trick. In this tutorial we’ll walk through exactly that—how to insert a rectangle shape, turn on the shadow, and customize its color, blur, and offsets—all with C# and Aspose.Words.

We’ll also cover **how to add shadow** in a way that works whether you’re targeting Word 2016, 2019, or the latest Office 365 build. By the end you’ll have a ready‑to‑save *.docx* file that showcases a nicely shaded rectangle, and you’ll understand the “why” behind each property you set.

## Prerequisites

- .NET 6 (or any recent .NET Framework version)  
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)  
- Basic familiarity with C# syntax  
- An IDE such as Visual Studio (but any editor will do)

No additional libraries are required; everything else lives inside Aspose.Words.

## Step 1 – Initialize the Document and Builder (Create Word Document)

To **create word document** programmatically you start with the `Document` class. The `DocumentBuilder` is your paintbrush; it lets you add text, shapes, and other elements.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters:* The `Document` object represents the entire .docx file. Without it you have nowhere to attach the rectangle or its shadow.

## Step 2 – Insert a Rectangle Shape (Insert Rectangle Shape)

Now we actually **insert rectangle shape**. The `InsertShape` method takes a `ShapeType` enum, plus the width and height in points.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Pro tip:* 1 point ≈ 1/72 inch, so 200 pts is roughly 2.78 inches wide. Adjust these numbers to fit your layout.

## Step 3 – Enable the Shadow (How to Add Shadow)

Shadows are disabled by default. Flip the `Visible` flag to turn it on.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*What’s happening?* When `Visible` is true, Word will render a drop‑shadow based on the other properties you set next.

## Step 4 – Customize Shadow Appearance (Set Shadow Color, Blur, Offsets)

Here’s where you **set shadow color**, blur radius, and the X/Y offsets. Feel free to experiment—different values give you a soft glow, a deep drop, or even a “floating” effect.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Why these numbers?* A blur of 5 pts gives a gentle feathered edge, while an offset of 4 pts shifts the shadow down‑right, mimicking a light source from the top‑left. Change `Color` to `Color.Black` for a stronger contrast, or use `Color.FromArgb(128, 0, 0, 0)` for a semi‑transparent black.

### Edge Cases & Variations

- **No blur:** Set `Blur = 0` for a crisp, hard‑edged shadow.  
- **Negative offsets:** Use `OffsetX = -4` to push the shadow left.  
- **Different shapes:** The same shadow properties work for circles, triangles, or even free‑drawn shapes—just change `ShapeType` in Step 2.  
- **Compatibility:** Aspose.Words writes the shadow data in the Office Open XML format, which works across Word 2010‑2021 and Office 365.

## Step 5 – Save the Document (Create Word Document)

Finally, persist the file to disk. You can choose any supported format (`.docx`, `.pdf`, `.odt`, …) but for this guide we’ll stick with the classic Word format.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

When you open **ShadowRectangle.docx** in Microsoft Word you’ll see a gray rectangle with a subtle, blurred shadow offset to the bottom‑right—exactly what we scripted.

### Expected Output

- A single‑page *.docx* file.  
- A 200 pt × 100 pt rectangle centered where the cursor was when `InsertShape` was called.  
- A gray shadow that appears 4 pts right and 4 pts down, with a 5 pt blur.

If the shape looks off‑center, you can move the cursor with `builder.MoveTo` before inserting, or adjust the shape’s `Left` and `Top` properties after insertion.

## Common Questions & Troubleshooting

**Q: The shadow isn’t showing up in Word.**  
A: Make sure `ShadowFormat.Visible` is `true`. Also verify you’re using a recent version of Aspose.Words (the shadow feature was added in version 20.3).  

**Q: Can I apply a gradient to the shadow?**  
A: Not directly via `ShadowFormat`. Word’s UI supports gradient shadows, but the Open XML schema (which Aspose.Words follows) only exposes solid colour shadows. You’d need to edit the underlying XML manually—a more advanced scenario.

**Q: What if I need a transparent rectangle with just a shadow?**  
A: Set `rectangle.FillColor = Color.Transparent;` after insertion. The shadow will still render because it’s independent of the fill.

## Pro Tips for Production Code

- **Reuse the builder:** If you’re adding multiple shapes, keep the same `DocumentBuilder` instance—creating a new one for each shape adds unnecessary overhead.  
- **Batch saves:** Save once after all modifications; frequent I/O slows down large document generation.  
- **Error handling:** Wrap the whole block in a `try / catch` and log `Aspose.Words` exceptions; they often contain helpful line numbers if the document template is corrupted.

## Next Steps (Related Topics)

- **How to add shadow** to pictures or text boxes (similar `ShadowFormat` usage).  
- **Insert rectangle shape** inside a table cell for custom cell styling.  
- **Create rectangle in Word** using Word’s native XML (for those who prefer raw Open XML).  
- **Set shadow color** dynamically based on user input or theme colors.

Experiment with different colours, blur radii, and offsets—maybe a soft blue glow for a corporate report, or a deep black shadow for a dramatic flyer. The possibilities are endless, and the code changes are minimal.

---

### Quick Recap

- We **created a word document** from scratch.  
- We **inserted a rectangle shape** and turned on its shadow.  
- We **set shadow color**, blur, and offsets to achieve a professional look.  
- We saved the file, ready for distribution.

Now you have a solid foundation for adding visual flair to any Word automation project. Got more ideas? Drop a comment, and let’s keep the conversation going. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}