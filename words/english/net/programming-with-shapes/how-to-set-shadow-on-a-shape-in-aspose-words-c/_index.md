---
category: general
date: 2026-04-02
description: Learn how to set shadow on a shape in Aspose.Words using C#. We'll also
  show you how to add shadow to shape, adjust blur, customize shadow and save document
  with shadow.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- how to adjust blur
- how to customize shadow
- save document with shadow
language: en
og_description: How to set shadow on a shape in Aspose.Words using C#. Follow the
  step‑by‑step guide to add shadow to shape, adjust blur, customize shadow and save
  document with shadow.
og_title: How to Set Shadow on a Shape in Aspose.Words (C#)
tags:
- Aspose.Words
- C#
- Document Automation
title: How to Set Shadow on a Shape in Aspose.Words (C#)
url: /net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Set Shadow on a Shape in Aspose.Words (C#)

Ever wondered **how to set shadow** on a shape so your Word documents look a bit more professional? You're not the only one—developers often ask how to add a subtle drop‑shadow that makes a diagram pop without breaking the layout. In this tutorial we’ll walk through the exact steps to **how to set shadow** on a shape using Aspose.Words for .NET, and along the way we’ll also cover **add shadow to shape**, **how to adjust blur**, **how to customize shadow**, and finally **save document with shadow**.

We’ll start with the prerequisites, then dive into each property of the `ShadowFormat` class, and finish with a complete, runnable example you can copy‑paste into Visual Studio. By the end you’ll know why each setting matters, what edge cases to watch for, and how to verify that the shadow really made a difference.

---

## What You’ll Need

- **Aspose.Words for .NET** (latest version at the time of writing, 23.12). You can get it via NuGet: `Install-Package Aspose.Words`.
- A .NET development environment (Visual Studio 2022 or VS Code with the C# extension works fine).
- An input DOCX that already contains at least one shape (a rectangle, picture, or SmartArt). If you don’t have one, create a quick Word file and insert any shape—Aspose.Words will read it just the same.

No other third‑party libraries are required; everything lives inside the `Aspose.Words` namespace.

---

## How to Set Shadow on a Shape

### Step 1 – Load the Document and Grab the Target Shape

First we open the source file and fetch the first shape we want to style. This is the same pattern you’d use for any shape manipulation.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// The GetChild method walks the node tree recursively.
Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

> **Why this matters:**  
> `GetChild` with `true` ensures we search the whole document tree, so even if the shape lives inside a header, footer, or textbox we still find it. Skipping this step would leave you with a `null` reference and a `NullReferenceException`.

### Step 2 – Access the ShadowFormat Object

Every `Shape` exposes a `ShadowFormat` property that bundles all shadow‑related settings. Think of it as the “shadow toolbox”.

```csharp
// Grab the ShadowFormat – this is where we configure colour, distance, blur, etc.
ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Pro tip:** If the shape already has a shadow, the `ShadowFormat` will contain the existing values. You can read them before overwriting if you need to preserve any defaults.

### Step 3 – Add Shadow to Shape: Choose Colour and Distance

Now we actually **add shadow to shape** by setting a colour and an offset distance. The colour is defined with ARGB so you can control transparency directly.

```csharp
// Semi‑transparent purple (alpha 128, red 0, green 0, blue 128)
shadow.Color = Color.FromArgb(128, 0, 0, 128);

// Distance from the shape to the shadow, measured in points.
shadow.Distance = 5.0;   // 5 points ≈ 1.75 mm
```

> **Why colour matters:** The alpha channel (first number) determines how see‑through the shadow is. A fully opaque shadow (alpha 255) can look harsh, while a lower alpha gives a softer, more realistic effect.

### Step 4 – How to Adjust Blur for a Realistic Effect

A crisp, hard‑edged shadow rarely looks good in a business document. Use the `BlurRadius` property to feather the edges.

```csharp
// Blur radius in points – larger values create a softer edge.
shadow.BlurRadius = 3.0;
```

> **Common mistake:** Setting `BlurRadius` to `0` leaves a jagged shadow that can break the visual flow of your report. A value between `2` and `5` works well for most screen‑viewed documents.

### Step 5 – How to Customize Shadow Transparency and Style

Beyond colour and blur, you can tweak the overall transparency of the shadow itself. This is separate from the colour’s alpha channel.

```csharp
// Overall transparency (0 = opaque, 1 = fully transparent)
shadow.Transparency = 0.3;   // 30 % transparent
```

> **Edge case:** If you set both the colour’s alpha and `Transparency` to high values, the shadow may become invisible. Test with a preview to make sure it’s still noticeable.

### Step 6 – Save Document with Shadow

Finally, persist the changes. This step demonstrates **save document with shadow** so you can open the file in Word and see the result.

```csharp
// Save the updated document. Overwrite or use a new file name as you prefer.
doc.Save("YOUR_DIRECTORY/output.docx");
```

> **Verification tip:** Open `output.docx` in Microsoft Word, select the shape, and look at the “Shadow” dropdown under “Shape Format”. You should see the custom colour, offset, blur, and transparency you just set.

---

## Add Shadow to Shape – Choosing the Right Color and Distance

When you **add shadow to shape**, the visual impact depends heavily on the colour contrast with the page background. Dark shadows on light pages feel natural, while bright colours can be used for artistic effects.

- **Dark grey (e.g., #808080)** works well for formal reports.  
- **Accent colours** (like the semi‑transparent purple we used) can highlight a call‑out box in marketing material.

You can also change the `ShadowFormat.Angle` property to rotate the shadow direction, but the default (45°) usually gives a pleasing diagonal offset.

```csharp
shadow.Angle = 45.0;   // Default angle – feel free to experiment
```

---

## How to Adjust Blur for Different Output Media

If your document will be printed, you might want a slightly tighter blur because high‑resolution printers can render subtle gradients. Conversely, for screen‑only PDFs a larger blur avoids jagged edges on low‑DPI displays.

```csharp
// Example: tighter blur for print
if (doc.PageCount > 0 && doc.FirstSection.PageSetup.PaperSize == PaperSize.A4)
{
    shadow.BlurRadius = 2.0;   // Slightly sharper for print
}
else
{
    shadow.BlurRadius = 4.0;   // Softer for screen
}
```

> **Why this conditional helps:** It demonstrates **how to adjust blur** based on a simple runtime check, showing you can make the shadow responsive to the final consumption medium.

---

## How to Customize Shadow Transparency and Color Dynamically

Sometimes you need to generate documents for different brand guidelines. Let’s make the shadow colour and transparency configurable via method parameters.

```csharp
void ApplyCustomShadow(Shape shape, Color colour, double distance, double blur, double transparency)
{
    ShadowFormat sf = shape.ShadowFormat;
    sf.Color = colour;
    sf.Distance = distance;
    sf.BlurRadius = blur;
    sf.Transparency = transparency;
}
```

You can now call:

```csharp
ApplyCustomShadow(targetShape, Color.FromArgb(200, 255, 0, 0), 4.0, 2.5, 0.2);
```

> **Real‑world use case:** Marketing teams often ask for a brand‑specific red shadow on promotional flyers. This helper method lets you meet that request without rewriting the core logic.

---

## Save Document with Shadow – Persisting Your Changes

A frequent question is whether the shadow survives when the document is converted to PDF. The answer is **yes**, as long as you use `PdfSaveOptions` that preserve drawing objects.

```csharp
PdfSaveOptions pdfOpts = new PdfSaveOptions
{
    // Ensure all drawing effects, including shadows, are retained.
    EmbedFullFonts = true,
    Compliance = PdfCompliance.PdfA2b
};

doc.Save("YOUR_DIRECTORY/output.pdf", pdfOpts);
```

Now you have both a DOCX and a PDF where the shape’s shadow looks identical.

---

## Full Working Example

Below is the complete, copy‑and‑paste‑ready program that ties everything together. Replace `YOUR_DIRECTORY` with the actual path on your machine.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (you could loop over all shapes if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Access the shadow format.
        ShadowFormat shadow = shape.ShadowFormat;

        // 4️⃣ Set colour, distance, blur and transparency.
        shadow.Color = Color.FromArgb(128, 0, 0, 128); // semi‑transparent purple
        shadow.Distance = 5.0;                        // offset in points
        shadow.BlurRadius = 3.0;                      // soft edge
        shadow.Transparency = 0.3;                    // 30 % transparent

        // Optional: tweak angle for a different light source.
        shadow.Angle = 45.0;

        // 5️⃣ Save the DOCX – this demonstrates save document with shadow.
        doc.Save("YOUR_DIRECTORY/output.docx");

        // 6️⃣ Also export to PDF to prove the shadow carries over.
        PdfSaveOptions pdfOpts = new PdfSaveOptions

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}