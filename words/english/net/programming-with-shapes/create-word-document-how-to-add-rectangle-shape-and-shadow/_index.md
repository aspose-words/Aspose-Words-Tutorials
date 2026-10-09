---
category: general
date: 2026-03-19
description: Create word document in C# with Aspose.Words, learn how to add shape,
  add rectangle shape, apply shadow, and save document as docx in minutes.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: en
og_description: Create word document with Aspose.Words, add rectangle shape, apply
  outer shadow, and save document as docx. Step‑by‑step guide.
og_title: Create Word Document – Add Rectangle Shape & Shadow
tags:
- Aspose.Words
- C#
- Document Automation
title: Create Word Document – How to Add Rectangle Shape and Shadow
url: /net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document – How to Add Rectangle Shape and Shadow

Ever needed to **create word document** programmatically and wondered where to start? You're not alone. Many developers hit the same wall when they first try to generate a .docx file that contains custom graphics. In this tutorial we’ll walk through the whole process—how to add shape, specifically an **add rectangle shape**, give it a stylish **add shadow to shape**, and finally **save document as docx**.  

By the end of the guide you’ll have a ready‑to‑use C# snippet that you can drop into any .NET project. No vague references, just a complete, runnable example.  

## Prerequisites

- .NET 6.0 or later (the code works with .NET Framework too).  
- Aspose.Words for .NET installed (NuGet package `Aspose.Words`).  
- A basic understanding of C# syntax—nothing fancy required.  

If you’re missing the library, run:

```bash
dotnet add package Aspose.Words
```

That’s it—no extra SDKs, no COM interop, just a single NuGet reference.

---

## Step 1: Create a Word Document (Primary Goal)

The first thing we need is a clean canvas. Think of the `Document` class as a fresh page in Microsoft Word; it holds sections, paragraphs, and everything else you’ll add later.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Why start with a blank `Document`? Because it guarantees that no hidden formatting sneaks in from a template. In my experience, starting from scratch avoids mysterious layout shifts when you later insert shapes.

---

## Step 2: Insert a Rectangle Shape – Adding the Visual Element

Now that we have a document, let’s **add rectangle shape** to the first paragraph. The `Shape` object is versatile; you can pick `ShapeType.Rectangle`, `Ellipse`, or even custom drawings. Here’s the minimal code:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**What’s happening under the hood?**  
- `ShapeType.Rectangle` tells Aspose we want a simple box.  
- `WrapType.Inline` ensures the rectangle moves with the text flow, which is usually what you expect in a word‑processing scenario.  
- By appending to `FirstParagraph`, we avoid the need to manually insert a new paragraph; Aspose creates one for us if the document is truly empty.

> **Pro tip:** If you need the shape to sit *behind* text, switch `WrapType` to `WrapType.Transparent`. That small change can make a huge visual difference.

---

## Step 3: Apply an Outer Shadow – Enhancing the Look

A flat rectangle is… well, flat. Adding an **add shadow to shape** gives it depth without extra images. Aspose’s `ShadowFormat` makes this a one‑liner.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Why bother with those specific values?  
- **Blur** of `5.0` gives a subtle feathered edge that looks professional on most monitors.  
- **Distance** of `3.0` and **Angle** of `45` create a natural light source from the top‑left, a common design convention.  
- **Color.Gray** works on both light and dark themes; you can swap it for `Color.Black` if you need a stronger contrast.

If you ever need an *inner* shadow (think of a recessed button), just change `ShadowType.OuterShadow` to `ShadowType.InnerShadow`. The same properties still apply.

---

## Step 4: Save the Document as DOCX – Persisting Your Work

All the fun is great, but you’ll eventually want a file on disk. The **save document as docx** step is straightforward:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

A couple of notes:  
- The `SaveFormat.Docx` enum guarantees the modern Office Open XML format, which is compatible with Word 2007+.  
- If you need to stream the file directly to a web response, replace the file path with a `MemoryStream` and write it to the HTTP response.

After running the code, open `ShadowedRectangle.docx` in Microsoft Word. You should see a gray rectangle with a soft shadow, sitting inline with the first paragraph—exactly what we set out to achieve.

---

## How to Add Shape – Alternative Approaches

The example above uses the *inline* approach, but sometimes you want a shape that floats over text. That’s where **how to add shape** with different wrapping comes into play.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Here we switched `WrapType` to `Square` and centered the shape on the page. This pattern is useful for cover pages or decorative banners. Remember: floating shapes increase the file size slightly because Word stores additional positioning data.

---

## Expected Output & Verification

When you open the generated file, you should see:

- A single paragraph containing a gray rectangle.  
- The rectangle measured roughly 2.8 × 1.4 inches.  
- A subtle outer shadow offset to the bottom‑right.  

If the shape appears *outside* the paragraph, double‑check the `WrapType`. If the shadow looks too harsh, lower the `Blur` value or switch the `Color` to a lighter shade.

---

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shape disappears after saving | `WrapType` set to `Inline` but paragraph was removed | Ensure the paragraph exists; use `doc.FirstSection.Body.FirstParagraph` to guarantee it. |
| Shadow looks pixelated | Using a very low `Blur` value | Increase `Blur` to at least `3.0` for smooth edges. |
| File size balloons | Adding many high‑resolution images alongside shapes | Use `doc.RemoveUnusedResources()` before saving if you added images. |
| Color not showing on dark mode | Using a dark `Color` for the shape itself | Choose a contrasting color (e.g., `Color.White`) for better visibility. |

---

## Full Working Example

Below is the complete, copy‑and‑paste‑ready code that incorporates everything we’ve discussed. Feel free to run it as a console app.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Explanation of each block** is inline as comments, satisfying both SEO readers and AI assistants that love self‑contained answers.

---

## Conclusion

We’ve just **create word document** from scratch, learned **how to add shape**, specifically an **add rectangle shape**, gave it an **add shadow to shape**, and finally **save document as docx**. The steps are simple, the code is compact, and the result looks polished.  

If you’re ready to take it further, try swapping the rectangle for a custom image, experiment with different shadow colors, or generate a whole report with multiple shaped sections. The Aspose.Words API is flexible enough to handle everything from invoices to marketing brochures.

Got questions about other shape types or need help integrating this into an ASP.NET Core service? Drop a comment below, and happy coding! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}