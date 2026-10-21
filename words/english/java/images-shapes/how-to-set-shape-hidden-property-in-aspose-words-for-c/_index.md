---
category: general
date: 2026-08-20
description: Learn how to set shape hidden property in Aspose.Words for C#. This guide
  shows inserting an image and hiding the shape so it never appears in the UI or print
  output.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: en
lastmod: 2026-08-20
og_description: Set shape hidden property in Aspose.Words with C#. Insert an image,
  hide the shape, and ensure it never shows in UI or print output.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Set shape hidden property in Aspose.Words – complete C# guide
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: How to set shape hidden property in Aspose.Words for C#
url: /java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to set shape hidden property in Aspose.Words for C#

If you need to **set shape hidden property** in a Word document, this tutorial shows you the exact steps using Aspose.Words for .NET. Whether you’re building a template engine, generating reports, or embedding a logo that must stay invisible, you’ll learn how to insert an image and hide the shape so it never appears in the UI or print output.

In this guide we also cover **insert image into document**, explain why hiding a shape matters for printing, and walk through the complete, runnable code. No external references are required—just copy, paste, and run.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later (the latest Aspose.Words version targets .NET 6+)
* A valid Aspose.Words for .NET license (or use the free evaluation mode)
* Visual Studio 2022 or any C# IDE you prefer
* An image file (e.g., `logo.png`) placed in a folder you can reference from code

## Step 1: Create a new Document and DocumentBuilder

The `DocumentBuilder` class is the entry point for building Word content programmatically. It lets you insert paragraphs, tables, and shapes such as images.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this step?*  
Creating a `Document` gives you an in‑memory representation of a .docx file, while the `DocumentBuilder` supplies the fluent API that inserts objects. Without these objects you cannot place a shape in the document.

## Step 2: Insert the image as a shape

Aspose.Words treats every picture as a `Shape`. The `InsertImage` method returns that `Shape` instance, which you can later manipulate.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Why this step?*  
Using `InsertImage` not only adds the picture to the flow of text but also gives you a reference (`picture`) that you can configure. This is essential for the **C# shape hidden property** we’ll set next.

## Step 3: Set the shape hidden property

The `Hidden` property controls whether the shape participates in the UI and printing. Setting it to `true` makes the shape invisible in the Word UI and guarantees it won’t be printed.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Why this step?*  
When a shape is marked as hidden, Word treats it like a comment—present in the document structure but never rendered. This is the core of **set shape hidden property**.

## Step 4: Save the document

Finally, write the document to disk. You can choose any format supported by Aspose.Words (`.docx`, `.pdf`, `.html`, etc.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Why this step?*  
Saving finalizes the in‑memory changes. Opening the resulting `.docx` in Microsoft Word shows no visible image, and the PDF export confirms the shape never appears in print output.

## Full, runnable example

Putting everything together, here’s the complete program you can compile and run:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Expected output**

* Opening `HiddenImageDocument.docx` in Microsoft Word shows no visible image.
* Exporting or printing the document (or opening the PDF) also shows no image.
* The hidden shape still exists in the document XML, which you can verify by opening the `.docx` as a zip and inspecting `word/document.xml` – you’ll see a `<w:pict>` element with `w:hidden="true"`.

## Common variations and edge cases

| Situation | What to do | Why it matters |
|-----------|------------|----------------|
| **Image file missing** | Wrap `InsertImage` in a `try/catch` and handle `FileNotFoundException`. | Prevents the application from crashing and lets you log a clear error. |
| **Multiple hidden shapes** | Call `picture.Hidden = true` for each `Shape` you insert, or iterate over `doc.GetChildNodes(NodeType.Shape, true)`. | Guarantees every unwanted visual element stays invisible. |
| **Need the shape visible only in edit mode** | Set `picture.Hidden = false` after editing, then toggle back before saving. | Allows you to work with the shape in the UI while keeping the final output clean. |
| **Printing on older Word versions** | Verify the document with Word 2010 or later; the hidden flag is supported across all modern versions. | Ensures compatibility across your user base. |
| **Using a different file format (e.g., PDF directly)** | The `Hidden` flag works the same; Aspose.Words respects it during PDF conversion. | Confirms that **prevent shape from printing** works for all export targets. |

## Pro tip: Verify the hidden flag programmatically

If you need to confirm that a shape is hidden before saving, you can inspect the property:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

This simple check is helpful in automated pipelines where you must guarantee compliance with document‑generation policies.

## Conclusion

You now know how to **set shape hidden property** in Aspose.Words for C#. By inserting an image, applying `picture.Hidden = true`, and saving the document, the shape stays out of the UI and never appears in printed output. This technique is essential when you need placeholders, watermarks, or branding elements that should stay invisible to end users.

### What’s next?

* Explore other shape properties such as `picture.WrapType`, `picture.Rotation`, and `picture.RelativeHorizontalPosition`.
* Learn how to **hide shape in Aspose.Words** conditionally based on user input or configuration.
* Combine hidden shapes with **insert image into document** loops to generate dynamic, invisible markers for later processing (e.g., mail‑merge fields).

Feel free to experiment with different image formats, document layouts, and export targets. Hiding shapes gives you fine‑grained control over what your readers actually see—and what stays behind the scenes. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}