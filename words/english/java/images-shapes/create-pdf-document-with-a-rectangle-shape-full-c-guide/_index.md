---
category: general
date: 2026-03-25
description: Create PDF document in C# and learn how to add rectangle shape, set fill
  color, adjust shape size and set shape transparency in just a few steps.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: en
og_description: Create PDF document in C# and see how to add a rectangle, set its
  fill color, size and transparency for polished PDF output.
og_title: Create PDF Document with a Rectangle Shape – C# Tutorial
tags:
- C#
- PDF
- Aspose.Words
title: Create PDF Document with a Rectangle Shape – Full C# Guide
url: /java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create PDF Document with a Rectangle Shape – Full C# Guide

Ever needed to **create PDF document** that contains a custom‑styled shape, but weren’t sure where to start? You’re not alone. Whether you’re building a report generator or a marketing flyer, being able to programmatically draw a rectangle, set its fill color, tweak its size and even adjust its transparency can make your PDFs look far more professional.

In this tutorial we’ll walk through a complete, ready‑to‑run C# example that **creates a PDF document**, **adds a rectangle shape**, **sets the fill color**, **defines the shape size**, and **sets shape transparency** for a subtle outer shadow. By the end you’ll have a single PDF file (`shadow.pdf`) you can open to see the result.

> **Pro tip:** The same approach works with other shape types (ellipse, line, etc.)—just swap `ShapeType.RECTANGLE` for the one you need.

---

## What You’ll Need

| Prerequisite | Why it matters |
|--------------|----------------|
| **.NET 6+** (or .NET Framework 4.6+) | The Aspose.Words library targets modern runtimes. |
| **Aspose.Words for .NET** NuGet package | Provides `Document`, `Shape`, `ShadowEffect`, and related classes. |
| **A C# IDE** (Visual Studio, Rider, VS Code) | Makes debugging and running the sample painless. |
| **Basic C# knowledge** | You’ll understand the syntax without a deep dive. |

You can install the library via the command line:

```bash
dotnet add package Aspose.Words
```

That’s it—no extra DLLs, no native dependencies. Once the package is in place, the code below will compile and run.

---

## Step‑by‑Step Implementation

Below we break the process into five logical steps. Each step has a clear heading (so AI models can index it) and a short code block that you can copy‑paste directly.

### ## 1. Create PDF Document and Prepare the Canvas

The very first thing we do is instantiate a `Document`. Think of it as a blank canvas that will eventually become your PDF file.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Why?** `Document` holds all sections, paragraphs, and shapes. Starting with a clean object guarantees no hidden artifacts from previous runs.

### ## 2. Add Rectangle Shape – Set Fill Color and Shape Size

Now we create a rectangle, give it a bright yellow fill, and define its dimensions. This covers both **add rectangle shape** and **set fill color** as well as **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Note:** Width/height are measured in points (1 point = 1/72 inch). Adjust these numbers to fit your layout.

### ## 3. Apply an Outer Shadow and Set Shape Transparency

Shadows add depth, and controlling their opacity is the essence of **set shape transparency**. Below we configure a gray outer shadow with 30 % transparency.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Why set transparency?** A 30 % transparent shadow looks subtle, preventing the rectangle from looking “flat” on the page.

### ## 4. Insert the Shape Into the Document Body

We now place the rectangle into the first paragraph of the document’s first section. This step ties everything together.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Edge case:** If you need the shape on a new page, prepend `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` before appending the shape.

### ## 5. Save the Document as a PDF File

Finally, we persist the in‑memory structure to a physical PDF file. The file will be written to the folder you specify.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

When you run the program, a file named `shadow.pdf` appears. Opening it shows a yellow rectangle with a soft gray shadow offset by 4 points—exactly what our code described.

> **Expected output:** A single‑page PDF where the rectangle sits near the top‑left corner of the page, filled with yellow, sized 200 × 100 points, and cast with a semi‑transparent outer shadow.

---

## Full Working Example (Copy‑Paste Ready)

Below is the entire source file, ready for you to drop into a new console project.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tip:** Replace `YOUR_DIRECTORY` with an absolute path like `C:\Temp` or a relative path such as `.\output`. The program will create the folder if it doesn’t already exist.

---

## Frequently Asked Questions (FAQ)

**Q: Can I change the rectangle’s position on the page?**  
A: Absolutely. Set `rectangle.Left` and `rectangle.Top` (both measured in points) before appending it to the paragraph.

**Q: What if I need a transparent fill instead of a transparent shadow?**  
A: Use `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – the first argument is the alpha channel (0‑255), where 128 yields ~50 % transparency.

**Q: Does this work with .NET Core?**  
A: Yes. Aspose.Words supports .NET Standard 2.0+, so you can run the same code on .NET 6, .NET 7, or .NET Framework 4.6+.

**Q: How can I add multiple shapes?**  
A: Just repeat steps 2‑4 for each shape, possibly inserting them into different paragraphs or sections.

---

## Conclusion

We’ve just **created a PDF document** from scratch, **added a rectangle shape**, **set its fill color**, **defined its size**, and **adjusted shape transparency** to achieve a polished shadow effect. The sample code is self‑contained, runs in under a minute, and demonstrates the core concepts you’ll need for more elaborate PDF layouts.

Ready for the next challenge? Try swapping the rectangle for a rounded‑corner shape, embed an image inside the shape, or generate a table of contents automatically. The same API lets you layer text, images, and vectors—so the sky’s the limit.

If you found this guide useful, give it a star on GitHub, share it with a teammate, or drop a comment with your own variations. Happy coding! 

---

![create pdf document with rectangle shape example](/images/rectangle-shadow.png "Screenshot showing the created PDF with a yellow rectangle and gray outer shadow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}