---
category: general
date: 2026-10-07
description: Create blank Word document in C# and learn to add rectangle shape, insert
  image shape, and group multiple shapes for dynamic reports.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: en
lastmod: 2026-10-07
og_description: Create blank Word document in C# with Aspose.Words. Learn how to add
  rectangle shape, insert image shape, and group multiple shapes for professional
  documents.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Create blank Word document and group shapes in C# – step-by-step guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to create blank Word document and group shapes in C#
url: /net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create blank Word document and group shapes in C#

If you need to **create blank Word document** programmatically, this guide shows you exactly how. You’ll see how to **add rectangle shape**, **insert image shape**, and **group multiple shapes** so they behave as a single object when you **add image to Word** later.

Working with Word files from code can feel intimidating, but Aspose.Words makes the process straightforward. By the end of this tutorial you will have a reusable C# snippet that generates a clean, empty Word file containing a grouped rectangle and logo. You can embed the result in invoices, reports, or any automated document workflow.

## Prerequisites

Before you start, ensure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.7+).  
* A valid Aspose.Words for .NET license or a free evaluation key.  
* An image file (e.g., `logo.png`) placed in a folder you can reference from code.  
* Visual Studio 2022 or any C#‑compatible IDE.

No additional NuGet packages are required beyond `Aspose.Words`.

## How to create blank Word document with Aspose.Words

The first step is always to **create blank Word document**. This object will host all subsequent shapes.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` represents the whole `.docx` file. At this point the file is empty, which satisfies the *create blank Word document* requirement.

## Create a container to group multiple shapes

Grouping shapes lets you move, rotate, or resize them together. Aspose.Words provides the `GroupShape` class for this purpose.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

The `Bounds` rectangle determines where the group appears on the page. By placing the group in the first paragraph you guarantee that the **create blank Word document** will immediately contain a visual container.

## How to add rectangle shape inside the group

A common requirement is to **add rectangle shape** as a background or border. The following code creates a rectangle and adds it to the previously defined group.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Because the rectangle lives inside the `GroupShape`, it will move together with any other shapes you add later. This is the core of **group multiple shapes** functionality.

## How to insert image shape inside the group

Next, you’ll **insert image shape** (the logo) and place it beside the rectangle. This demonstrates the **add image to Word** workflow.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

The `SetImage` method reads the file and embeds it directly into the Word document, ensuring the image persists even when the source file is moved. This completes the **insert image shape** step and finalizes the **add image to Word** requirement.

## Save the document

Finally, persist the file to disk. The saved file contains the blank document, the grouped rectangle, and the embedded logo.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

When you open `GroupShape.docx` in Microsoft Word, you’ll see a single group that includes a light‑gray rectangle and the logo positioned side‑by‑side. Selecting any part of the group lets you move or resize the whole collection, proving that the shapes are indeed **group multiple shapes**.

## Complete, runnable example

Below is the full program you can copy, paste, and run. Replace `YOUR_DIRECTORY` with an absolute or relative path that exists on your machine.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Expected output

* A file named `GroupShape.docx` located in `YOUR_DIRECTORY`.  
* Opening the file in Word shows a single visual group containing a gray rectangle on the left and the `logo.png` on the right.  
* Selecting any part of the visual group allows you to move or resize the whole collection, confirming that the shapes are correctly **group multiple shapes**.

## Common questions and edge‑case handling

| Question | Answer |
|---|---|
| **Can I add more than two shapes to the same group?** | Yes. Call `group.AppendChild(yourShape)` for each additional `Shape`. The group can contain any number of drawing objects. |
| **What if the image file is missing?** | `SetImage` will throw a `FileNotFoundException`. Wrap the call in a try‑catch block and provide a fallback (e.g., a placeholder shape). |
| **Do I need to set `WrapType` for the shapes?** | By default shapes are inline. If you need floating behavior, set `picture.WrapType = WrapType.Inline;` or another wrap mode before adding to the group. |
| **How does the document size affect the group’s bounds?** | The `Bounds` rectangle is defined in points (1 pt ≈ 1/72 in). Adjust the size if you place the group on a different page layout (e.g., A4 vs. Letter). |
| **Can I reuse the same group in another document?** | Yes. Clone the group with `GroupShape cloned = (GroupShape)group.Clone(true);` and insert it into a different `Document`. |

## Pro tips

* **Reuse the `DocumentBuilder`** for adding text before or after the group. It automatically respects the current cursor position.  
* **Set `Shape.StrokeColor`** if you need a visible border around the rectangle.  
* **Use high‑resolution PNGs** for the logo to avoid pixelation when


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}