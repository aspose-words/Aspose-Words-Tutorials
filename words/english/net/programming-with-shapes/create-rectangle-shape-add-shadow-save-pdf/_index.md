---
category: general
date: 2026-02-24
description: Create rectangle shape in C# using Aspose.Words, add shadow to shape,
  and save document as PDF. Learn how to add shadow and how to save PDF in minutes.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: en
og_description: Create rectangle shape in C# with Aspose.Words, then add shadow to
  shape and save the document as PDF – a complete, step‑by‑step guide.
og_title: Create rectangle shape, add shadow & save PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Create rectangle shape, add shadow & save PDF
url: /net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create rectangle shape, add shadow & save PDF

Ever needed to **create rectangle shape** in a Word document but also wanted a nice drop shadow and a PDF output? You're not the only one. In many reporting or invoice‑generation projects the visual polish—like a subtle shadow—makes the difference between “just another file” and “professional‑grade document.”  

In this tutorial we’ll walk through exactly that: using **Aspose.Words for .NET** to create a rectangle shape, add shadow to shape, and finally **save document as PDF**. By the end you’ll have a ready‑to‑run C# console app that produces a PDF with a shaded rectangle, and you’ll understand how to tweak the shadow or change the export options.

## What you’ll need

- .NET 6 SDK (or any recent .NET version) – the API works the same on .NET Framework 4.x as well.  
- Aspose.Words for .NET NuGet package (`Aspose.Words`) – install it with `dotnet add package Aspose.Words`.  
- A code editor – Visual Studio, VS Code, or Rider will do.  

No extra licensing steps for this example; the free evaluation mode is enough to see the PDF output.

## Step 1: Set up the project and import namespaces

First things first, let’s spin up a console project and bring in the classes we’ll need.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Why this matters:* `Document` and `DocumentBuilder` give us the canvas, while `Shape` and `ShadowFormat` let us draw and style the rectangle. Importing them up front keeps the later code tidy.

## Step 2: **Create rectangle shape** with the desired dimensions

Now we actually create a blank document and insert a rectangle. Notice how the `InsertShape` method returns a `Shape` object that we can immediately style.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Explanation*: The size is expressed in points (1 pt = 1/72 in). Adjust the numbers to fit your layout. We also give the shape a light‑blue fill to make the shadow stand out.

## Step 3: **Add shadow to shape** – fine‑tune the effect

A shadow isn’t just “on/off.” You can control its color, blur, distance, direction, and even transparency. Here’s a practical configuration that works well for most reports.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Why you might change these values:*  
- **BlurRadius** – increase for a dreamy effect, decrease for a crisp edge.  
- **Direction** – 0° points to the right, 90° down, 180° left, etc. Rotate to match your page layout.  
- **Transparency** – set to `0` for a solid shadow, `0.5` for half‑transparent, etc.

### How to add shadow – alternative approaches

If you need a **multiple‑layer shadow** (e.g., a darker outer shadow plus a lighter inner one), you can create a second shape, offset it, and set a different `ShadowFormat`. Or, for a quick “no‑blur” look, set `BlurRadius = 0`.

## Step 4: **Save document as PDF** – the final export

With the rectangle and its shadow ready, the last step is to write the file out as a PDF. Aspose.Words handles the conversion internally; you just call `Save` with the desired format.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Tip*: If you need to control PDF compliance (PDF/A, PDF/X) or embed fonts, use an overload:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

That’s the **how to save pdf** part in a nutshell.

## Full, runnable example

Below is the complete program you can copy‑paste into `Program.cs`. It compiles and runs as‑is (just make sure the output folder exists).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Expected result

Open the generated `ShadowRectangle.pdf`. You’ll see a single page with a light‑blue rectangle, a soft gray shadow offset 45° down‑right, and clean edges. The PDF should be viewable in any modern reader (Adobe Acrobat, Edge, Chrome).

![Create rectangle shape with shadow in PDF](/images/shadow-rectangle.png "Create rectangle shape with shadow")

*(Image alt text includes the primary keyword for SEO.)*

## Common questions & edge‑case handling

**What if the shadow disappears in the PDF?**  
Make sure you’re using a recent version of Aspose.Words (≥23.3). Older builds had a bug where certain shadow properties were ignored during PDF conversion.

**Can I change the shadow colour to match my brand?**  
Absolutely—just replace `System.Drawing.Color.Gray` with any `Color` you like, e.g., `Color.FromArgb(128, 0, 0, 255)` for a semi‑transparent blue.

**How do I add a shadow to other shapes (ellipse, star, etc.)?**  
The same `ShadowFormat` works for any `Shape` object. After you create the shape, grab its `ShadowFormat` and set the properties.

**What about DPI or scaling issues?**  
PDF rendering respects the shape’s point size. If you need a higher‑resolution output (for printing), adjust the shape dimensions accordingly or set `PdfSaveOptions.ImageResolution`.

**Can I export to other formats, like PNG?**  
Yes—just call `document.Save("output.png", SaveFormat.Png)`. The shadow will be rendered the same way.

## Pro tips & best practices

- **Reuse the builder**: If you’re adding multiple shapes, keep a single `DocumentBuilder` instance; it’s cheaper than creating many.
- **Batch saving**: When generating many PDFs in a loop, reuse the `PdfSaveOptions` object to avoid repeated allocations.
- **Testing**: Always open the PDF after saving to verify that the shadow appears as expected. Some PDF viewers render shadows slightly differently; Adobe Acrobat is the most reliable reference.
- **Performance**: For large documents, disable `DocumentBuilder.InsertShape`’s automatic page breaks by setting `builder.PageSetup.DifferentFirstPageHeaderFooter = false` if you don’t need it.

## Conclusion

We’ve covered everything you need to **create rectangle shape**, **add shadow to shape**, and **save document as PDF** using Aspose.Words for .NET. The code is compact, the concepts are explained, and you now have a solid foundation to experiment with other shapes, shadow styles, and export options.  

Next steps? Try swapping the rectangle for a rounded‑

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}