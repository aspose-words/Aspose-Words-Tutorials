---
category: general
date: 2026-10-23
description: Learn how to insert ellipse and how to add rectangle shape in Word using
  Aspose.Words. Includes move cursor to shape and how to create group shape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: en
lastmod: 2026-10-23
og_description: How to insert ellipse and how to add rectangle shape in Word with
  Aspose.Words. Follow step‑by‑step guide to move cursor to shape and create group
  shape.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: How to insert ellipse and rectangle shapes in a Word group shape
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
url: /java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words

If you need to know **how to insert ellipse** in a Word document programmatically, this guide shows the complete process. You will also see **how to add rectangle** shape, learn to **move cursor to shape**, and discover **how to create group shape** that holds multiple drawing objects.

Word automation often requires precise positioning of drawing objects. By the end of this tutorial you can generate a `.docx` file that contains a grouped rectangle and ellipse, ready for further styling or export. No external tools are required beyond the Aspose.Words for .NET library and a .NET development environment.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later installed.
* Aspose.Words for .NET (NuGet package `Aspose.Words`) added to your project.
* Basic knowledge of C# syntax and Visual Studio (or any IDE).

These requirements ensure the code compiles without additional configuration.

## How to create group shape in Word

A group shape acts as a container that lets you move, rotate, or format several shapes as a single unit. The following code creates a group with a specific size (300 × 200 points) and prepares the document for further drawing operations.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Why this step matters*: The group shape defines a local coordinate system. All shapes added after moving the cursor into the group will be positioned relative to the group's origin, making layout calculations straightforward.

## How to add rectangle shape word

Now that the group exists, you can **insert rectangle shape** inside it. The rectangle will serve as a background or a visual placeholder for other content.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Explanation*: `MoveTo(group)` tells the builder that the active insertion point is the group shape. Without moving the cursor, `InsertShape` would add the rectangle to the main document body instead of the group.

## How to insert ellipse

With the rectangle in place, you can now demonstrate **how to insert ellipse**. The ellipse will be centered within the same group, overlapping the rectangle if desired.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Why the cursor must be moved*: Each call to `InsertShape` respects the current cursor location. Re‑calling `MoveTo(group)` guarantees that the ellipse is also a child of the group, preserving the intended hierarchy.

## Move cursor to shape before inserting additional objects

If you need to add more shapes later, always **move cursor to shape** before each insertion. This pattern avoids accidental placement outside the group.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tip*: Re‑using `MoveTo(group)` is cheap and improves code readability. It also makes future maintenance easier because the insertion context is explicit.

## Save the document

Finally, persist the document to disk. The example saves the file as `GroupShape.docx` in a folder you specify.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

When you open the saved file in Microsoft Word, you will see a single group containing a rectangle and an ellipse, both correctly positioned.

### Expected output

* A `.docx` file named `GroupShape.docx`.
* Inside the document, a grouped drawing object sized 300 × 200 points.
* Within the group:
  * A rectangle (100 × 50 points) located at the group's origin.
  * An ellipse (80 × 80 points) overlapping the rectangle.
  * Any additional shapes you added after moving the cursor.

## Common variations and edge cases

| Situation | Recommended approach |
|-----------|----------------------|
| **Different unit sizes** | Aspose.Words uses points (1 pt = 1/72 in). Convert centimeters or inches to points before calling `InsertShape`. |
| **Rotating shapes inside the group** | After inserting a shape, retrieve its `ShapeBase` object and set `ShapeBase.RotationAngle`. |
| **Adding text inside a shape** | Use `ShapeBase.AppendChild(new Paragraph(document))` and then add a `Run` with the desired text. |
| **Saving to PDF instead of DOCX** | Call `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – the group hierarchy is preserved in the PDF output. |

These variations demonstrate that the same **how to insert ellipse** logic can be adapted for many real‑world scenarios.

## Pro tips

* **Reuse the same `DocumentBuilder` instance** – it reduces memory overhead and keeps the document state consistent.
* **Validate shape dimensions** – extremely large widths or heights may cause rendering issues in older Word versions.
* **Group before styling** – applying fill colors or line styles to the group after all children are added ensures uniform appearance.

## Conclusion

You now understand **how to insert ellipse** and **how to add rectangle** shape inside a grouped container in a Word document using Aspose.Words. By consistently **move cursor to shape** before each insertion, you maintain a clean hierarchy and avoid accidental placement. The complete example compiles, runs, and produces a grouped shape that can be further customized or exported.

Ready to explore more? Try combining this technique with **how to create group shape** for complex diagrams, or experiment with **insert rectangle shape word** alongside text boxes for rich report generation. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [How to create blank Word document and add a hidden ellipse shape in C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [How to create group shape docx and add interactive controls in C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}