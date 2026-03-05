---
category: general
date: 2026-03-04
description: Learn how to create rectangle shape, add shadow to shape and apply shadow
  effect in a Word document, then save Word document automatically.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: en
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: Create rectangle shape in Word – Complete C# Tutorial
tags:
- C#
- Aspose.Words
- Document Automation
title: Create rectangle shape in Word with C# – Step‑by‑Step Guide
url: /java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape in Word with C# – Complete Programming Tutorial

Ever needed to **create rectangle shape** in a Word file but weren’t sure where to start? You’re not alone—many developers hit that wall when they first dive into programmatic document generation. The good news is that with a few lines of C# you can insert a rectangle, **add shadow to shape**, and **apply shadow effect** without ever opening Word yourself. In this guide we’ll walk through the entire process, from a fresh **create blank document** to saving the final **save word document** on disk.

We’ll cover everything you need: the required NuGet package, the exact APIs, why each property matters, and a handful of tips to avoid the most common pitfalls. By the end you’ll have a fully runnable example that you can drop into any .NET project.

## Prerequisites

- .NET 6.0 or later (the code works with .NET Framework 4.7+ as well)
- Visual Studio 2022 or any IDE you prefer
- **Aspose.Words for .NET** installed via NuGet (`Install-Package Aspose.Words`)
- Basic familiarity with C# syntax

No additional Word interop libraries are needed—Aspose.Words handles everything in memory.

## Step 1 – Create a blank document

The first thing we do is **create blank document**. Think of it as the empty canvas on which we’ll later **create rectangle shape**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Why this matters:** Starting with a clean `Document` object guarantees that no hidden styles or sections interfere with the shape positioning later on.

## Step 2 – Insert a rectangle shape into the document

Now we actually **create rectangle shape**. We’ll set its size, positioning, and tell Word not to wrap text around it.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Pro tip:** If you need the rectangle to sit inside a table cell, change `WrapType` to `WrapType.Inline`. For most reports, `None` keeps the shape floating above the text.

## Step 3 – Add shadow to shape and configure its appearance

Here’s where the magic happens: we **add shadow to shape** and **apply shadow effect**. The shadow makes the rectangle pop on the page, especially when printed.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Why these values?**  
> - **BlurRadius** controls how fuzzy the edges appear; a value around `5` gives a subtle, professional look.  
> - **Transparency** lets the underlying text remain readable.  
> - **OffsetX/Y** move the shadow away from the shape, creating depth.  
> - Using a **blue** tint is just an example—any `System.Drawing.Color` works.

## Step 4 – Add the configured shape to the document body

With the rectangle fully styled, we now **add rectangle shape** to the document’s first section. This step actually places the shape in the file.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Edge case:** If your document already contains sections, you may want to target a specific one (`doc.Sections[2]` for example). The code above works for a single‑section document, which is common for quick reports.

## Step 5 – Save the Word document

Finally, we **save word document** to disk. The file will contain the rectangle with its shadow, ready to be opened in Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Tip:** Use `doc.Save(outputPath, SaveFormat.Docx)` if you need to be explicit about the format. The `Save` method automatically detects the extension, but being explicit can avoid confusion when the path is generated programmatically.

## Full, Runnable Example

Below is the complete program you can copy‑paste into a console application. It includes all `using` statements and the `Main` method, so you can run it straight away.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Expected Result

When you open *shadowed_rectangle.docx* in Microsoft Word, you’ll see a blue‑bordered rectangle floating near the top of the first page, with a soft blue shadow shifted 8 pt to the right and bottom. No extra text surrounds it because we set `WrapType.None`.

## Frequently Asked Questions & Variations

| Question | Answer |
|----------|--------|
| **Can I change the shape to an ellipse?** | Yes—replace `ShapeType.Rectangle` with `ShapeType.Ellipse`. All shadow properties remain the same. |
| **What if I need multiple shapes?** | Simply repeat Steps 2‑4 for each new `Shape` instance, adjusting `OffsetX/Y` or `Left/Top` to avoid overlap. |
| **Is there a way to make the shadow color match the shape’s fill?** | Absolutely. Set `rectangle.FillColor` first, then assign `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **How do I insert the shape into a table cell?** | Use `cell.FirstParagraph.AppendChild(rectangle);` after locating the desired `Cell` object. |
| **Will this work on .NET Core?** | Yes—Aspose.Words is cross‑platform. Just ensure you reference the appropriate NuGet package version for .NET Core/5/6. |

## Common Pitfalls & Pro Tips

- **Pitfall:** Forgetting to set `ShadowFormat.Visible = true`. The shadow properties will be ignored silently.  
  **Fix:** Always enable visibility before tweaking other shadow parameters.

- **Pitfall:** Using a very large `BlurRadius` (e.g., 20) can make the shadow look fuzzy and unprofessional.  
  **Fix:** Stick to values between `3` and `8` for most business documents.

- **Pro tip:** If you need the shape to be selectable later (e.g., for end‑user editing), avoid setting `WrapType.Inline`. Floating shapes (`WrapType.None`) are easier to move around programmatically.

- **Pro tip:** When generating many documents in a loop, reuse a single `Document` instance and call `doc.Clone(true)` for each iteration to improve performance.

## Related Topics You Might Explore Next

- **Add text inside a rectangle shape** – learn how to use `Shape.TextPath` for labels.  
- **Create complex diagrams** – combine multiple shapes, connectors, and grouping.  
- **Export to PDF** – convert the same document to PDF with a single `doc.Save("output.pdf")`.  
- **Apply different fill styles** – gradients, textures, or even pictures inside shapes.

## Conclusion

We’ve just **create rectangle shape**, **add shadow to shape**, and **apply shadow effect** in a Word file using C#. By following the five concise steps you now have a reusable pattern for any document‑automation scenario, and you know how to **save word document** reliably. Feel free to tweak dimensions, colors, or even swap the rectangle for another geometry—Aspose.Words makes it all straightforward.

If you found this tutorial helpful, give it a star on GitHub, or share your own variations in the comments. Happy coding, and may your documents always look as polished as this shadowed rectangle!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}