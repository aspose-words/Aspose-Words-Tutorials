---
category: general
date: 2026-03-27
description: Create word document c# and learn how to add shape, apply shadow to shape,
  and set shadow distance. Step‑by‑step guide for Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: en
og_description: Create word document c# with a rectangle shape and custom shadow.
  Follow this complete tutorial to set shadow distance and style.
og_title: Create Word Document C# – Add Shape with Shadow
tags:
- Aspose.Words
- C#
- Document Automation
title: Create Word Document C# – Add Shape with Shadow
url: /net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document C# – Add Shape with Shadow

Ever needed to **create word document c#** that contains a nicely styled rectangle? Maybe you’re building a report template and want a subtle drop‑shadow to make the layout pop. In this tutorial we’ll walk through exactly that – how to add shape, apply shadow to shape, and even tweak the shadow distance using Aspose.Words.

We’ll start with a blank document, drop in a rectangle, give it a preset shadow, and finish by saving the file. By the end you’ll have a ready‑to‑use .docx that you can open in Word and see the effect instantly. No external tools, just pure C# code.

## Prerequisites

- .NET 6 (or any recent .NET Framework) installed.
- Visual Studio 2022 or VS Code with C# extension.
- Aspose.Words for .NET NuGet package (`Aspose.Words` version 23.12 or later).  
  You can add it via the Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

That’s it – no extra DLLs or COM interop required.

## Step 1: Initialize a New Document and Builder – *create word document c#* Basics

First we need a `Document` object that represents the Word file and a `DocumentBuilder` to edit it.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this step matters:** The `Document` class is the container for all Word parts (pages, styles, images). The builder is the high‑level API that abstracts away low‑level node manipulation, making it easy to **create word document c#** without dealing with XML directly.

## Step 2: Insert a Rectangle Shape – *how to create rectangle*  

Now we’ll place a rectangle on the page. The size is expressed in points (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro tip:** If you need a different shape, just swap `ShapeType.Rectangle` for `ShapeType.Ellipse`, `ShapeType.Triangle`, etc. The same code works for **how to add shape** of any type.

## Step 3: Apply a Preset Shadow and Fine‑Tune It – *apply shadow to shape*  

Aspose.Words ships with several preset shadow formats. We’ll use `Preset1` and then customize distance, blur, transparency, and color.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Why customize the shadow?** The `Distance` property controls how far the shadow sits from the rectangle – think of it as the “lift” you’d see in a 3‑D rendering. Changing `BlurRadius` softens the edges, while `Transparency` lets you create a subtle, professional look. This covers the **set shadow distance** requirement and shows you how to **apply shadow to shape** in a flexible way.

## Step 4: Save the Document – *create word document c#* Completion

Finally, write the document to disk. Adjust the path to a folder you have write access to.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Open the resulting file in Microsoft Word, and you’ll see a light‑blue rectangle with a soft gray shadow offset by 5 pt. That’s the visual proof that you successfully **create word document c#** with a styled shape.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# example showing rectangle with shadow"}

## Optional Variations & Edge Cases

| Scenario | What to Change | Why it Matters |
|----------|----------------|----------------|
| **Different shadow style** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Gives you a more dramatic look without extra code. |
| **No preset – custom shadow** | Omit `Format` and set `OffsetX`, `OffsetY` manually. | Full control over direction and depth. |
| **Multiple shapes** | Call `builder.InsertShape` again before saving. | Useful for complex templates with icons, logos, etc. |
| **Compatibility with older Aspose versions** | Use `ShadowEffect` class (available in v20.x). | Ensures your code runs on legacy projects. |
| **Saving as PDF** | `document.Save("ShadowShape.pdf");` | Same shadow rendering appears in PDF output. |

> **Common question:** *What if the shadow doesn’t appear in Word?*  
> Make sure you’re using a recent version of Aspose.Words (≥ 22.9). Older releases had limited shadow support. Also verify that the document is opened in a recent version of Word (2016+).

## Full Working Example

Below is the complete, copy‑paste‑ready program. It includes all `using` directives, comments, and error handling for a smooth experience.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Run the program, navigate to `C:\Temp\ShadowShape.docx`, and you’ll see the rectangle with the exact shadow we configured.

## Recap & Next Steps

- You now know how to **create word document c#**, insert a rectangle, and **apply shadow to shape** with a custom **set shadow distance**.  
- The example uses Aspose.Words, which abstracts away the OpenXML complexities and guarantees consistent rendering across Word versions.  
- Want to go further? Try combining multiple shapes, adding text inside the rectangle, or exporting the same document as PDF to see how the shadow translates.

### Related Topics You Might Explore

- **How to add shape** to a header/footer for branding.  
- Using **Aspose.Words** to insert charts and tables programmatically.  
- Customizing **shadow effects** on pictures instead of vector shapes.  
- Automating bulk document generation for invoices or certificates.

Feel free to experiment, break the code, and then rebuild it – that’s the fastest way to internalize the concepts. If you hit a snag, drop a comment below or check the official Aspose.Words documentation for deeper API insights.

Happy coding, and enjoy making your Word files look a little more polished!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}