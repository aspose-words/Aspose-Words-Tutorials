---
category: general
date: 2026-10-20
description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for C#.
  Learn how to toggle shape visibility, handle edge cases, and save the result.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: en
lastmod: 2026-10-20
og_description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
  C#. Master shape visibility toggling and avoid common pitfalls.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
url: /net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#

If you need to **Hide/Show a Shape with the new `Hidden` prop** in a Word document, this guide shows you exactly how to do it with Aspose.Words for .NET. Whether you are generating reports, building templates, or cleaning up imported documents, controlling shape visibility programmatically saves you from manual editing.

In this tutorial you will learn how to load a document, locate a shape, toggle the `Hidden` property, and save the modified file. The steps also cover common variations such as handling multiple shapes and dealing with inline versus floating graphics.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 (or later) installed – Aspose.Words supports .NET Standard 2.0 and .NET Core.
* A licensed copy of **Aspose.Words for .NET** (the free trial works for exploration).
* An IDE such as Visual Studio 2022 or Visual Studio Code.
* A Word document (`input.docx`) that contains at least one shape (e.g., a picture, SmartArt, or drawing canvas).

## Step 1: Load the Word document

The first operation is to create a `Document` object that represents the .docx file on disk.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this step matters*: `Document` is the entry point for all Aspose.Words operations. Loading the file into memory gives you full access to its node tree, including shapes.

## Step 2: Retrieve the target shape

To toggle visibility you must obtain a reference to the shape node. The example below fetches the first shape in the document, but you can adapt the logic to locate shapes by name, type, or index.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Why this step matters*: `GetChild` with `true` performs a deep search, ensuring you find shapes even when they are nested inside tables or headers. Checking for `null` prevents a `NullReferenceException` when the document contains no shapes.

## Step 3: Hide the shape with the `Hidden` property

Aspose.Words introduced the `Hidden` property to control whether a shape is rendered or printed. Setting it to `true` hides the shape; setting it to `false` makes the shape visible again.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

If you need to **show** a previously hidden shape, simply assign `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Why this step matters*: The `Hidden` property works for both floating and inline shapes, and it integrates with Word’s native “Hidden” formatting. This approach is more reliable than removing the shape because the node remains in the document tree, preserving layout and references.

## Step 4: Save the modified document

After adjusting the visibility, write the changes back to a new file (or overwrite the original if desired).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Why this step matters*: `Save` serializes the in‑memory node tree into a .docx package that Word can open. The hidden flag is persisted, so opening the file in Microsoft Word will display the shape according to the `Hidden` setting.

## Full, runnable example

Putting all steps together gives you a self‑contained program you can copy, compile, and run.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Expected output** when you run the program:

```
Document saved. Shape hidden = True
```

Opening `ShapeHidden.docx` in Microsoft Word shows the document without the targeted shape. If you set `shape.Hidden = false;` before saving, the shape reappears.

## Handling multiple shapes

The example above works for a single shape. Real‑world documents often contain many graphics. Use a loop to hide or show all shapes that meet a condition (e.g., a specific name or type).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tip*: Filtering by `ShapeType` avoids unintentionally hiding decorative elements such as text boxes or SmartArt.

## Edge cases and best practices

| Situation | Recommended handling |
|-----------|----------------------|
| **Shape is inside a header/footer** | Retrieve the header/footer node first, then call `GetChild(NodeType.Shape, …)` on that sub‑document. |
| **Document contains no shapes** | Always check for `null` after `GetChild` or verify `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **You need to preserve the hidden flag across different Word versions** | The `Hidden` property is stored in the shape’s XML as `<w:hidden/>`, which is supported by Word 2007 and later. |
| **Performance with large documents** | Use `doc.GetChildNodes(NodeType.Shape, true)` once and reuse the collection instead of calling `GetChild` repeatedly. |

## Pro tip: Combine `Hidden` with `WrapType`

When a shape is hidden, Word still reserves the space it would occupy unless you also change its wrapping behavior. Setting `WrapType = WrapType.None` removes the placeholder area.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

This ensures the layout collapses as if the shape never existed, which is useful for generating clean reports.

## Conclusion

You now know how to **Hide/Show a Shape with the new `Hidden` prop** using Aspose.Words for C#. The solution covers loading a document, locating a shape, toggling the `Hidden` property, and persisting the change. By following the best‑practice tips—checking for null, handling multiple shapes, and adjusting wrap settings—you can reliably control shape visibility in any Word automation scenario.

Ready to explore more? Consider these next steps:

* **Hide/Show multiple shapes** based on custom metadata (uses the “programmatically hide shape” technique).
* **Combine `Hidden` with conditional content** using Aspose.Words fields for dynamic report generation.
* **Explore other node properties**, such as `Visible` for chart objects or `IsDeleted` for paragraph-level control.

Happy coding, and enjoy the fine‑grained control that Aspose.Words provides for Word document shape visibility!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}