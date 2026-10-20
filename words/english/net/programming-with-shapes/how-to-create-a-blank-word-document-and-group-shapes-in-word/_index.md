---
category: general
date: 2026-10-20
description: Learn how to create a blank Word document, group shapes in Word, set
  shape fill color, and use wrap type inline with a complete C# example.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: en
lastmod: 2026-10-20
og_description: Create a blank Word document, group shapes in Word, and set shape
  fill color with wrap type inline using Aspose.Words and C#. Follow the complete
  tutorial.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Create a blank Word document and group shapes in Word – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: How to create a blank Word document and group shapes in Word using Aspose.Words
url: /net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create a blank Word document and group shapes in Word

If you need to **create a blank Word document** that contains multiple shapes acting as a single unit, this guide shows you exactly how. You’ll see how to **group shapes in Word**, set a shape’s fill color, and apply **wrap type inline**—all with a concise, runnable C# program.

The tutorial walks you through every line of code, explains why each step matters, and highlights common pitfalls. By the end you’ll have a .docx file that displays a rectangle and a text box grouped together, ready for further automation.

## What you’ll learn

* How to initialize an empty Word file with Aspose.Words.
* The correct way to create a **GroupShape** and add child shapes.
* Techniques for **set shape fill color** and control positioning.
* Using **wrap type inline** so the group behaves like a single inline object.
* How to save and verify the result.

No prior experience with Aspose.Words is required, but you should be comfortable with basic C# syntax and have Visual Studio (or another IDE) installed.

## Prerequisites

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later | Provides the runtime for the C# project. |
| Aspose.Words for .NET (latest version) | Supplies the `Document`, `DocumentBuilder`, and shape classes used in the example. |
| A writable folder path | The `doc.Save` call needs a valid directory to write the output file. |
| Basic C# knowledge | Enables you to follow the code and modify it for your own scenarios. |

Install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Step 1: Create a blank Word document

The first operation is to **create a blank Word document**. Aspose.Words’ `Document` class represents an in‑memory Word file, and `DocumentBuilder` provides a convenient API for editing it.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: Starting with a clean document guarantees that the group shape you add will be the only content, making verification straightforward.

## Step 2: Define a group shape with wrap type inline

A **GroupShape** acts as a container for other shapes. Setting its `WrapType` to `Inline` ensures the group behaves like a single inline object in the paragraph flow.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Why this matters*: Using **wrap type inline** prevents the group from floating away from surrounding text, which is essential when you want the group to move as a unit.

## Step 3: Add a rectangle and set shape fill color

A rectangle is a common visual element. The `Shape` constructor takes a `ShapeType`; we then specify dimensions and fill color.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Why this matters*: The `FillColor` property demonstrates **set shape fill color** in practice, giving the rectangle a light‑blue background that stands out in the final document.

## Step 4: Add a text box – how to group shapes effectively

A text box provides editable text inside the group. Position it relative to the group's coordinate system by adjusting the `Top` property.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Why this matters*: This step answers **how to group shapes**—by appending each child shape to the same `GroupShape` instance. The `Top` offset ensures the text box appears below the rectangle, demonstrating precise layout control.

## Step 5: Insert the completed group shape into the document

Now that the group contains both child shapes, insert it at the current builder position.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Why this matters*: Inserting the group as a single node guarantees that Word treats the rectangle and text box as one logical object, preserving their relative positions during editing.

## Step 6: Save the document and verify the output

Finally, write the document to disk. Replace `YOUR_DIRECTORY` with a real path on your machine.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

When you open `GroupShape.docx` in Microsoft Word, you should see a light‑blue rectangle with a text box labeled “Grouped text” positioned directly beneath it. Selecting either shape will select the entire group, confirming that **group shapes in Word** works as intended.

### Expected result

* A .docx file containing a single paragraph.
* Inside the paragraph, an inline group that looks like a single composite object.
* The rectangle is filled with light blue, and the text box displays “Grouped text”.

![Screenshot of the generated Word document](grouped_shapes.png){.center width=600 alt="Screenshot of a blank Word document with grouped rectangle and text box created using Aspose.Words"}

## Common questions and edge‑case handling

### What if I need the group to float rather than be inline?

Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType` enum value). Floating groups can be positioned independently of paragraph flow, but they lose the automatic inline alignment.

### Can I add more shapes, such as circles or images?

Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`, configure their properties, and call `group.AppendChild(newShape)`. The group will automatically expand to accommodate the new bounds if you update `group.Bounds` accordingly.

### How do I change the group’s overall size after adding children?

Adjust `group.Bounds` after all children are appended, or compute the union of child bounds programmatically. This ensures the group’s hit‑test area matches the visual content.

### What if the output folder does not exist?

Aspose.Words throws a `DirectoryNotFoundException`. Create the directory first:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Does this work with .NET Framework instead of .NET Core?

All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are available in the .NET Framework version of Aspose.Words, so the same code works unchanged.

## Pro tips

* **Performance tip** – Reuse a single `DocumentBuilder` instance when inserting many groups; creating a new builder per group adds overhead.
* **Visual consistency** – Set `rectangle.StrokeColor` to match `FillColor` for a seamless look, or set `rectangle.LineWidth = 0` to hide the border.
* **Debugging** – Call `doc.UpdatePageLayout()` before saving if you modify many shapes; this forces Word to recalculate layout and can prevent unexpected clipping.

## Conclusion

You now know how to **create a blank Word document**, **group shapes in Word**, **set shape fill color**, and apply **wrap type inline** using Aspose.Words for .NET. The complete example demonstrates the standard approach for building composite graphics that behave as a single object in Word.

From here you can explore:

* Adding additional shapes such as images or charts.
* Experimenting with different `WrapType` values for floating groups.
* Automating batch generation of grouped diagrams across multiple documents.

Feel free to adapt the code to your own automation scenarios, and share your results in the comments!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [How to Save PDF from Word with Inline Shapes – Complete Guide](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}