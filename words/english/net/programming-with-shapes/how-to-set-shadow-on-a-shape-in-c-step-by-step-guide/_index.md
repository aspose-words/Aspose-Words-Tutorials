---
category: general
date: 2026-04-10
description: how to set shadow on a shape in C# – learn how to apply drop shadow,
  change transparency, adjust blur, and add shape shadow using Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: en
og_description: how to set shadow on a shape in C# – this tutorial shows how to apply
  drop shadow, change transparency, adjust blur, and add shape shadow with clear code
  examples.
og_title: how to set shadow on a shape in C# – Complete Guide
tags:
- Aspose.Words
- C#
- Document Automation
title: how to set shadow on a shape in C# – step‑by‑step guide
url: /net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# how to set shadow on a shape in C# – Complete Guide

Ever wondered **how to set shadow** on a shape when you’re programmatically building a Word document? You’re not alone. Many developers hit a wall when they need a subtle drop shadow for a textbox, a logo, or a call‑out box, and the API docs feel a bit thin.  

In this tutorial we’ll walk through the entire process: from loading a `.docx`, grabbing the first `Shape`, to applying a drop shadow, tweaking its transparency, adjusting the blur radius, and finally positioning it just right. By the end you’ll have a reusable snippet that works with Aspose.Words .NET 2023 or later, and you’ll understand *why* each property matters.

## What You’ll Need

- **Aspose.Words for .NET** (NuGet package `Aspose.Words`) – the library that gives us the `Document`, `Shape`, and `ShadowFormat` classes.  
- **.NET 6+** (or .NET Framework 4.7.2) – any recent runtime will do.  
- A simple Word file (`input.docx`) that already contains at least one shape, such as a textbox.  
- Visual Studio, VS Code, or your favorite IDE.

That’s it. No extra third‑party tools, no COM interop, just plain C#.

![how to set shadow example](image-placeholder.png){:alt="how to set shadow on a shape in a Word document"}

## How to Set Shadow – Overview

The core idea behind **how to set shadow** is to manipulate the `ShadowFormat` object that lives on a `Shape`. Think of `ShadowFormat` as a miniature “style sheet” for the shadow itself: it tells the renderer whether the shadow is visible, what colour it should be, how transparent it is, how blurry, and where it sits relative to the shape.  

Below is the *complete* runnable program. Feel free to copy‑paste it into a console app, hit **F5**, and watch the shadow appear in the saved `output.docx`.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Why These Settings Matter

- **Visible** – Without turning this flag on, all the other properties are ignored.  
- **Color** – A dark gray mimics a typical UI drop shadow; you can swap in any `Color`.  
- **Transparency** – 0.3 gives a *soft* look while still keeping the shape legible.  
- **Size** – Controls the blur; a value of 6 is usually enough for a professional feel.  
- **Distance & Angle** – Together they define the *offset*; 2 pts at 45° yields a subtle diagonal shadow.

That’s the essence of **how to set shadow**. Next, we’ll break each piece down so you can **apply drop shadow**, **change transparency**, **adjust blur**, and **add shape shadow** in isolation.

---

## Apply Drop Shadow to a Shape

When people ask “how do I **apply drop shadow** in C#?”, they often only need the visibility toggle and a colour. The following snippet isolates those two lines:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** If you’re targeting older Word versions (2003‑2007), stick to standard colours. Some exotic ARGB values may be ignored by the legacy renderer.

---

## How to Change Transparency of the Shadow

Transparency is expressed as a **float between 0 and 1**. A value of **0** means a completely opaque shadow; **1** makes it invisible. Most designers settle around **0.2‑0.4** for a natural look.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Edge Cases

- **Negative values** – Aspose.Words will clamp them to 0, but it’s better to validate input.  
- **Values > 1** – Clamped to 1, effectively hiding the shadow.  

If you need to let users pick a percentage, convert it first:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## How to Adjust Blur (Size) of the Shadow

The **Size** property controls the blur radius. Larger numbers produce a softer, more diffused shadow. It’s measured in points (pt), not pixels.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### When to Use a Small vs. Large Blur

- **Small blur (2‑4 pt)** – Good for UI‑style callouts where you want a crisp edge.  
- **Large blur (8‑12 pt)** – Works well for printed reports or when the shape is far from the background.

---

## Add Shape Shadow – Positioning and Direction

The final piece of **add shape shadow** is the offset. Two properties work together:

| Property | Meaning |
|----------|---------|
| **Distance** | How far the shadow sits from the shape (in points). |
| **Angle**    | Direction of the offset (0° = right, 90° = down, 180° = left, 270° = up). |

Example that creates a subtle bottom‑right shadow:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

You can experiment with angles to simulate light coming from different sources. A common trick is to let the user pick a “light source” from a dropdown and map it to an angle value.

---

## Full Working Example (All Steps Combined)

Below is the same program as earlier, but with **extra comments** that make the logic crystal‑clear. Copy this into `Program.cs` and run it; the output file will contain a textbox with a perfectly tuned shadow.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Expected result:** Open `output.docx`. The first textbox will display a dark gray, 30 % transparent shadow that is slightly blurred (size = 6) and offset 2 pt at a 45° angle. The effect is subtle yet noticeable—exactly what most UI designers aim for.

---

## Common Questions & Gotchas

- **“Does this work with images as well?”**  
  Yes. Any `Shape`—whether a textbox, picture, or auto‑shape—exposes `ShadowFormat`. Just replace the shape retrieval logic with the appropriate index or name.

- **“What if the document has multiple shapes?”**  
  Loop through `doc.GetChildNodes(NodeType.Shape, true)` and apply the same settings to each. You can also filter by `shape.Name` or `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}