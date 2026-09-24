---
category: general
date: 2026-02-18
description: Create rectangle shape using Aspose.Words and learn how to add shadow,
  set shape size, and save Word document in a few minutes.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: en
og_description: Create rectangle shape in a Word file, learn how to add shadow, set
  shape size, and save the document with Aspose.Words in C#.
og_title: Create rectangle shape in Word – Complete Aspose.Words Tutorial
tags:
- Aspose.Words
- C#
- Word automation
title: Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide
url: /net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide

Ever needed to **create rectangle shape** in a Word file but weren’t sure where to start? You’re not the only one—developers often ask, “how do I add a shadow to a shape and still keep the document editable?” In this tutorial we’ll answer that and also show you **how to add shadow**, **set shape size**, and **save Word document** all in one smooth flow.

We’ll walk through everything you need, from initializing a new document (yes, that’s the first step to **how to create document**) to persisting the final *.docx* on disk. No external references, just a self‑contained example you can copy‑paste into Visual Studio and run today.

---

## Prerequisites

- .NET 6+ (or .NET Framework 4.7+). Aspose.Words works with any recent .NET runtime.
- A valid Aspose.Words license (or the free evaluation key) – otherwise you’ll see a watermark.
- Visual Studio, Rider, or any C# editor you prefer.
- Basic C# knowledge—nothing fancy, just the ability to run a console app.

> **Pro tip:** If you’re on a Mac, the same code runs under .NET 6 with VS Code—just make sure you reference the `Aspose.Words` NuGet package.

---

## Step 1: Initialize the document – the foundation of **how to create document**

Before we can draw anything, we need a blank canvas. Aspose.Words calls this a `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Why this matters:** The `Document` object represents the entire *.docx* file. All shapes, paragraphs, and sections you add become children of this object. Starting with a clean document ensures no hidden styles interfere with your rectangle.

---

## Step 2: Define the rectangle and **set shape size**

A rectangle is just a `Shape` with `ShapeType.Rectangle`. We’ll give it explicit dimensions so it looks exactly as intended.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **What the numbers mean:** Aspose.Words uses points (1 pt = 1/72 in). Adjust the values to fit your layout; for a typical A4 page, 200 pt is a comfortable width.

---

## Step 3: **How to add shadow** – making the shape pop

Shadows give a visual cue that the shape is “lifted” off the page. The `Shadow` property lets you tweak color, distance, transparency, and blur.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Why use transparency?** A fully opaque shadow can look harsh. Setting it to 0.4 makes the effect subtle and professional.

---

## Step 4: Position the rectangle – inline flow with surrounding text

If you want the shape to behave like a character in a paragraph, set its `WrapType` to `Inline`. This keeps the layout predictable, especially when the document is edited later.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Edge case:** If you need the rectangle to float over text (e.g., a watermark), change `WrapType` to `Square` or `BehindText`.

---

## Step 5: Insert the shape into the document body

Now we actually place the rectangle into the first paragraph. If the document has no content yet, `FirstParagraph` is automatically created.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tip:** You can also create a new paragraph first and then append the shape—useful when you need surrounding text.

---

## Step 6: **Save Word document** – the final step

With everything in place, persisting the file is a one‑liner. Choose any path you like; the example uses a placeholder you should replace with your own directory.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Result:** Open the generated *.docx* in Microsoft Word. You’ll see a black‑shadowed rectangle, 200 pt wide and 100 pt tall, sitting inline with the first paragraph.

---

## Expected output

When you open **ShadowShape.docx**, the document shows:

- A single paragraph containing a rectangular shape.
- The rectangle has a subtle black shadow offset by 5 pt.
- The shape size matches the dimensions set in Step 2.
- No extra text appears unless you add it manually.

If the shape doesn’t appear, double‑check that you’ve referenced the correct Aspose.Words version and that your license (or trial) is active.

---

## Common Questions & Variations

| Question | Answer |
|----------|--------|
| *Can I change the shadow color to something other than black?* | Absolutely—set `rectangleShape.Shadow.Color = Color.Blue;` or any `System.Drawing.Color`. |
| *What if I need a larger rectangle?* | Adjust `Width` and `Height` values. Remember they’re in points; 72 pt = 1 in. |
| *Is it possible to place the shape at an absolute position?* | Yes—use `WrapType = WrapType.Absolute` and set `Top`/`Left` properties. |
| *Does this work with .NET Core?* | It does. Aspose.Words is cross‑platform; just install the NuGet package for .NET Standard. |
| *Can I add text inside the rectangle?* | Not directly; you’d need to insert a `TextBox` shape instead of a plain rectangle. |

---

## Full Working Example (Copy‑Paste Ready)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Run the program, navigate to `C:\Temp\ShadowShape.docx`, and you’ll see the rectangle with a shadow exactly as described.

---

## Conclusion

You now know how to **create rectangle shape** in a Word file using Aspose.Words, how to **set shape size**, **add shadow**, and finally **save Word document** with the changes. The whole process—from **how to create document** to persisting the result—fits into a handful of lines of C# and can be expanded for more complex layouts.

Ready for the next challenge? Try swapping the rectangle for a rounded‑corner shape, experiment with different shadow colors, or embed the shape inside a table cell. Each tweak reinforces the same core concepts we covered here.

If you found this guide helpful, give it a share, drop a comment with your own variations, or explore our other tutorials on Word automation, such as inserting images or generating tables with Aspose.Words. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}