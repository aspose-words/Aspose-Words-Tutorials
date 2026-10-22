---
category: general
date: 2026-09-30
description: Create blank document and insert rectangle shape, ellipse, and group
  multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
  create group.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: en
lastmod: 2026-09-30
og_description: Create blank document in C# and learn how to insert shapes and group
  multiple shapes with Aspose.Words. Follow the step‑by‑step tutorial.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Create a blank document and group shapes in C# – Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: How to create blank document and add shapes with Aspose.Words in C#
url: /java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create blank document and add shapes with Aspose.Words in C#

If you need to **create blank document** and populate it with graphics, this guide shows you exactly how. You’ll see how to **insert rectangle shape**, add other drawing objects, and then **group multiple shapes** so they behave as a single unit.

Working with shapes is a common requirement when generating contracts, certificates, or custom reports. In this tutorial you’ll learn the complete workflow, from initializing the document to saving the final file, using the Aspose.Words API for .NET.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 (or later) SDK installed  
* A valid Aspose.Words for .NET license (the free trial works for this example)  
* An IDE such as Visual Studio 2022 or Visual Studio Code  

No additional NuGet packages are required beyond `Aspose.Words`.

## How to create blank document and work with shapes

The first step is to instantiate a `Document` object. This object represents the in‑memory Word file and gives you access to the `DocumentBuilder`, which is the primary tool for inserting content.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** A blank document gives you a clean canvas. The `DocumentBuilder` maintains the current insertion point, so every shape you add is automatically placed on the appropriate page.

## Insert rectangle shape and other shapes

Next, we add a rectangle and an ellipse. Both calls use the same `InsertShape` method, which is the recommended way **how to insert shapes** in Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*The `InsertShape` method automatically positions the shape at the current cursor location.* If you need precise placement, you can adjust `Shape.Left` and `Shape.Top` after insertion.

## Group multiple shapes into a single object

Now we combine the rectangle and ellipse into one logical entity. Grouping is useful when you want to move or resize several shapes together.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**How this works:** `InsertGroupShape` creates a container that behaves like any other `Shape`. By calling `AppendChild`, you move the existing shapes into the container, which automatically updates their relative coordinates.

### Practical tip

If you later need to **how to create group** programmatically for more than two shapes, simply repeat `AppendChild` for each additional `Shape` instance. The group can contain any number of drawing objects, including pictures, text boxes, or even other groups.

## Full example – how to insert shapes and save the document

Below is the complete, runnable program that demonstrates every step discussed so far. Running the code produces a `ShapesDemo.docx` file containing a rectangle, an ellipse, and a grouped shape.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output:** Opening `ShapesDemo.docx` in Microsoft Word shows a single page with a blue rectangle, a green ellipse, and a surrounding gray border that represents the group. Moving the group moves both shapes together, confirming that the **group multiple shapes** operation succeeded.

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| *What if I need the shapes on a specific page?* | Call `builder.MoveToDocumentEnd();` before inserting the shapes, or use `builder.MoveToSection(sectionIndex);` to target a particular section. |
| *Can I add text inside a grouped shape?* | Yes. Create a `Shape` of type `ShapeType.TextBox`, configure its text, and then `AppendChild` it to the `GroupShape`. |
| *Do shape dimensions use points or pixels?* | Aspose.Words uses **points** (1 pt = 1/72 inch). This ensures consistent sizing across printers and displays. |
| *How to change the group’s rotation?* | Set `groupShape.RotationAngle = 45;` (degrees). All child shapes rotate around the group’s origin. |

## Conclusion

You now know how to **create blank document**, **insert rectangle shape**, **how to insert shapes** like ellipses, and **group multiple shapes** into a single object using Aspose.Words for .NET. The full code example demonstrates the recommended approach, and the tips above help you adapt the solution to more complex scenarios such as adding text boxes or rotating groups.

Ready to explore more? Try adding a picture shape to the group, experiment with different fill colors, or generate a multi‑page report where each page contains its own grouped diagram. The same principles apply, so you can scale this pattern to any document‑automation project.


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}