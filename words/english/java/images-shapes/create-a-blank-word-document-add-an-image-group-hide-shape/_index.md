---
category: general
date: 2026-10-10
description: Create a blank Word document, insert image into Word, add an image group,
  and hide shape in the saved file. Follow this step‑by‑step guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: en
lastmod: 2026-10-10
og_description: Create a blank Word document, insert image into Word, add an image
  group, and hide the shape. This guide shows the complete C# code.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Create a blank Word document, add an image group, hide shape
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Create a blank Word document, add an image group, hide shape
url: /java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document, add an image group, hide shape

If you need to **create blank word document** and later hide visual elements, this tutorial shows you exactly how. You’ll learn to insert image into word, add image group, and hide shape word document in a single, reusable C# routine.

We’ll use the Aspose.Words for .NET library, which lets you manipulate .docx files without Microsoft Word installed. By the end of this guide you will have a runnable program that produces a Word file containing a hidden image group, ready for downstream processing or conditional display.

## Prerequisites

- .NET 6.0 or later (the code also works with .NET Framework 4.6+)
- Aspose.Words for .NET NuGet package (`Install-Package Aspose.Words`)
- A folder on disk where you can read an image file and write the output document
- Basic familiarity with C# and Visual Studio (or any IDE you prefer)

## Create a blank Word document with Aspose.Words

The first step is to **create blank word document**. Aspose.Words provides the `Document` class that represents an in‑memory Word file. Instantiating it without arguments gives you an empty document ready for content.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* Starting with a blank document ensures no hidden formatting or leftover sections interfere with the shape you will add later.

## Insert image into Word using DocumentBuilder

Next, we **insert image into word** by first creating a group shape that will hold the picture. Group shapes let you treat several drawing objects as a single unit, which is useful when you later want to hide or move them together.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

The `InsertGroupShape` method creates an empty container. The dimensions are in points (1 point = 1/72 inch). Adjust the size to match the resolution of the image you plan to embed.

## Add image group to the document

Now we **add image group** by moving the builder’s cursor inside the newly created group and inserting the picture. All subsequent inserts will be part of the group.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Tip:* Use an absolute or correctly escaped relative path; otherwise `InsertImage` throws a `FileNotFoundException`.

## Hide shape in a Word document

Finally, we **hide shape word document** by setting the group’s `Hidden` property to `true`. Hidden shapes are not displayed when the document is opened in Word, but they remain in the file and can be revealed programmatically later.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

When you open *GroupHidden.docx* in Microsoft Word, you’ll see a completely blank page because the image group is hidden. The file still contains the image data, which you can unhide later with `group.Hidden = false` if needed.

## Full, runnable example

Below is the complete program you can copy‑paste into a new console project:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Expected output**

- A file named `GroupHidden.docx` appears in `YOUR_DIRECTORY`.
- Opening the file in Word shows an empty page.
- The hidden image can be revealed by changing `group.Hidden = false` and re‑saving.

## Common variations and edge cases

| Situation | How to adapt the code |
|-----------|----------------------|
| **Multiple images** | Insert additional `InsertImage` calls after `builder.MoveTo(group)`. All images stay inside the same group and share the hidden flag. |
| **Different image formats** | Aspose.Words supports PNG, JPEG, BMP, GIF, TIFF. Just change the file extension; no code change needed. |
| **Conditional visibility** | Store a custom document variable (`doc.Variables.Add("ShowImages", "true")`) and toggle `group.Hidden` based on its value at runtime. |
| **Large documents** | Create the group on a specific page (`builder.InsertBreak(BreakType.PageBreak)`) before inserting the group to avoid layout shifts. |
| **Compatibility with older Word versions** | Save as `doc.Save("output.doc", SaveFormat.Doc)` if you need the legacy `.doc` format; hidden shapes behave the same way. |

**Pro tip:** Always set `group.Hidden = true` *after* you have inserted every child element. Changing the flag before adding content can cause some elements to be rendered unexpectedly in older Word versions.

## Conclusion

You now know how to **create blank word document**, **insert image into word**, **add image group**, and **hide shape word document** using Aspose.Words for .NET. The complete example demonstrates every step from initializing the document to saving a file that contains a hidden image group.

Next, you might explore:

- Adding text boxes or charts to the same group
- Using `DocumentBuilder.StartBookmark` / `EndBookmark` to mark hidden sections
- Programmatically toggling visibility based on user input or document variables

Feel free to experiment with different shapes, sizes, and visibility rules to fit your automation scenario. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}