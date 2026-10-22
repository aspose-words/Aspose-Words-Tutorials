---
category: general
date: 2026-05-26
description: Create Word document in C# with Aspose.Words, insert rectangle shape,
  set fill color, and add shadow effect – step‑by‑step guide.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: en
og_description: Create Word document in C# using Aspose.Words. Learn how to insert
  a rectangle shape, set its fill color, and add a shadow effect.
og_title: Create Word Document – Insert Rectangle Shape & Shadow in C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Create Word Document – Insert Rectangle Shape & Shadow in C#
url: /net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document – Insert Rectangle Shape & Shadow in C#

Ever wondered how to **create Word document** programmatically without opening Microsoft Word first? You're not the only one. In many automation scenarios—think invoices, contracts, or bulk report generation—you need a reliable way to spin up a .docx file, drop a shape inside, give it a color, and maybe even a shadow for that polished look.

In this tutorial we'll walk through exactly that: using Aspose.Words for .NET to **create Word document**, **insert rectangle shape**, apply a fill, and **add shadow**. By the end you’ll have a ready‑to‑save file you can pipe into any downstream workflow.  

We’ll also touch on **how to insert shape** in a flexible way, and why **how to set fill** matters for visual consistency. No fluff, just the code you can copy‑paste and run.

## Prerequisites

Before we dive, make sure you have:

- .NET 6+ (or .NET Framework 4.7+) installed.
- A valid Aspose.Words for .NET license (or a temporary evaluation key).
- Visual Studio, Rider, or any C# IDE you like.
- Basic familiarity with C# syntax—nothing fancy required.

Got those? Great, let’s get started.

## Step 1 – Create Word Document

The first thing you need is a blank document object. This is the canvas where everything else lives.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` represents the .docx file in memory, while `DocumentBuilder` gives us a convenient API to insert text, tables, and shapes. **Creating the Word document** this way is instant—no UI, no COM interop, just pure .NET.

## Step 2 – Insert Rectangle Shape

Now that we have a document, let’s **insert rectangle shape**. The `InsertShape` method takes a `ShapeType` enum, width, and height (in points). We’ll use a rectangle sized 150 × 80 points, which translates roughly to 2 × 1 inch.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Behind the scenes, Aspose creates a `Shape` object, adds it to the current paragraph, and returns a reference you can style. This is the core of **how to insert shape**—just one line of code, yet incredibly powerful.

## Step 3 – How to Set Fill

A shape without fill is invisible on a white page. Let’s give it a pleasant light‑blue background.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

You could also use gradients, textures, or even a picture fill, but a solid color keeps the example simple. This demonstrates **how to set fill** on any shape you create, ensuring the visual cue your readers expect.

## Step 4 – How to Add Shadow

Shadows add depth and make the shape pop. Aspose.Words exposes a `ShadowFormat` object where you can toggle visibility, pick a color, and fine‑tune blur, distance, and angle.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Why these particular values? A 45° angle gives a natural top‑right light source, a modest blur keeps the shadow subtle, and a short distance prevents the shape from looking detached. Feel free to experiment—changing the angle to 135° will make the shadow fall to the bottom‑left, for instance.

## Step 5 – Save the Document

All the work is done; now we write the file to disk. Choose any path you like; just be sure the folder exists.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

When you open `ShadowShape.docx` in Microsoft Word, you’ll see a light‑blue rectangle with a soft gray shadow—exactly what we scripted.

## Full Working Example

Putting it all together, here’s the complete, copy‑paste‑ready program:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Expected Result

- A file named **ShadowShape.docx** appears in the target folder.
- Opening it in Word shows a light‑blue rectangle centered on the first page.
- The rectangle casts a gray shadow at a 45° angle, giving a subtle 3‑D effect.

## Common Questions & Edge Cases

**What if I need a different shape?**  
Replace `ShapeType.Rectangle` with any other enum value (`Ellipse`, `Star`, `Arrow`, etc.). The rest of the code stays the same.

**Can I add text inside the shape?**  
Yes—after creating the shape, call `shape.AppendChild(new Paragraph(doc))` and then insert a `Run` with your text. Remember to set `shape.TextBox` properties if you want wrapping.

**What about DPI or measurement units?**  
Aspose works in points (1 pt = 1/72 inch). If you prefer centimeters, multiply by 28.35 (since 1 cm ≈ 28.35 pt).

**Do I need a license for this to work?**  
The evaluation version adds a watermark on the first page. A proper license removes it and unlocks the full API.

## Tips & Gotchas

- **Pro tip:** Call `builder.MoveToDocumentEnd()` before inserting a shape if you want it at the very end of the document.
- **Watch out for:** Saving to a read‑only folder will throw an `UnauthorizedAccessException`. Ensure your app has write permissions.
- **Performance note:** For bulk generation (hundreds of docs), reuse a single `Document` instance as a template and clone it with `doc.Clone(true)` to avoid repeated initialization overhead.

## Conclusion

You now know how to **create Word document**, **insert rectangle shape**, **set fill**, and **add shadow** using Aspose.Words for .NET. The snippet above is a self‑contained solution you can drop into any C# project, whether it’s a console app, a web API, or a background service.

From here you might explore:

- Adding multiple shapes with varying colors.
- Using gradients or picture fills (`shape.FillColor = ...` → `shape.FillPattern`).
- Combining shapes with tables for complex report layouts.

Give it a try, tweak the parameters, and watch your automated Word files look more professional with just a few lines of code. Happy coding!


## Related Tutorials

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}