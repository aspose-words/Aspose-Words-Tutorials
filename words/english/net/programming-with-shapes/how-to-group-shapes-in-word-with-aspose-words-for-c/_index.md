---
category: general
date: 2026-09-21
description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
  guide covers creating, positioning, and saving grouped shapes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: en
lastmod: 2026-09-21
og_description: Group shapes in Word using Aspose.Words for C#. Follow this concise
  tutorial to create, position, and save grouped shapes programmatically.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Group shapes in Word with Aspose.Words – complete C# guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: How to group shapes in Word with Aspose.Words for C#
url: /net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Word with Aspose.Words for C#

If you need to **group shapes in Word** programmatically, Aspose.Words makes it straightforward. This tutorial shows you how to create two rectangle shapes, place them side‑by‑side, combine them into a `GroupShape`, and save the result as a DOCX file.

You’ll see a complete, runnable example, explanations of why each step matters, and tips for handling common edge cases such as overlapping shapes or dynamic sizing. By the end of this guide you can integrate shape grouping into any Word automation project.

## Prerequisites

Before you start, ensure you have:

* .NET 6.0 (or later) installed – Aspose.Words supports .NET Standard 2.0+, .NET Core, and .NET Framework.
* A valid Aspose.Words for .NET license (or a temporary evaluation key) – the library works without a license but adds a watermark.
* Visual Studio 2022 (or any C# IDE) to compile and run the sample.

No additional NuGet packages are required beyond `Aspose.Words`.

## How to group shapes in Word using Aspose.Words

The core of the solution is a **`GroupShape`** object that acts as a container for individual shapes. Below we break the process into clear steps.

### Step 1: Create a blank document and a `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step?*  
`Document` represents the entire DOCX file, while `DocumentBuilder` supplies fluent methods (e.g., `InsertShape`) that automatically place new elements at the current cursor position.

### Step 2: Insert the first rectangle shape

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

The `InsertShape` call adds the shape to the document and returns a `Shape` object you can further configure (color, border, etc.). The size is expressed in points (1 pt ≈ 1/72 in).

### Step 3: Insert the second rectangle and offset it

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Setting `Left` positions the shape relative to the page margin. The offset must be larger than the first shape’s width (100 pt) to avoid overlap; we use 120 pt to leave a small gap.

### Step 4: Create a `GroupShape` large enough for both rectangles

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` takes the owning `Document` and the container dimensions. The container’s width should exceed the farthest shape’s right edge; otherwise, the second shape would be clipped.

### Step 5: Append the individual shapes to the group

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Appending moves the shapes into the group’s internal collection. After this call the shapes are no longer independent objects in the document tree—they belong to the group.

### Step 6: Insert the grouped shape back into the document

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` places the entire `GroupShape` where the cursor currently resides. If you need the group in a specific paragraph, move the builder to that paragraph first.

### Step 7: Save the document

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

The resulting file contains two rectangles that behave as a single object—you can move, resize, or delete them together in Microsoft Word.

## Full source code

Putting all steps together yields a self‑contained program:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Expected output:** Opening *GroupedShapes.docx* in Microsoft Word shows two rectangles side by side, treated as a single selectable object. Dragging the group moves both rectangles together.

## Common variations and edge cases

| Situation | Recommended adjustment |
|-----------|------------------------|
| **More than two shapes** | Create additional `Shape` objects, position them accordingly, and append each to the same `GroupShape`. |
| **Dynamic size** | Compute the group width/height based on the maximum `Right` and `Bottom` values of the child shapes. |
| **Different shape types** | `ShapeType.Ellipse`, `ShapeType.Triangle`, etc., can be inserted the same way; the group container does not care about the type. |
| **Rotated shapes** | Set `shape.Rotation = 45;` before appending; the rotation is preserved inside the group. |
| **Saving as PDF** | Call `doc.Save("GroupedShapes.pdf");` – the group is retained in the PDF rendering. |

**Pro tip:** After grouping, you can still modify individual shapes by accessing `group.GetChildNodes(NodeType.Shape, true)`. This is useful when you need to change the fill color of one rectangle without breaking the group.

## How to verify the grouping programmatically

If you need to confirm that the shapes are correctly grouped (e.g., in unit tests), examine the document node hierarchy:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

The output should be:

```
Number of groups: 1
Children in first group: 2
```

This confirms that **group shapes in Word** were created as expected.

## Conclusion

You now know how to **group shapes in Word** with Aspose.Words for C#. The process involves creating individual shapes, positioning them, wrapping them in a `GroupShape`, and inserting the group back into the document. With the complete example above you can extend the technique to any number of shapes, different types, or even combine it with text boxes and images.

Next, explore related topics such as **Aspose.Words shape grouping**, **C# Word shape manipulation**, and **DocumentBuilder insert shape** for more advanced document automation scenarios. Experiment with dynamic sizing, conditional grouping, and exporting to PDF to fully leverage the power of Aspose.Words.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}