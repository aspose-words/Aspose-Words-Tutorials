---
category: general
date: 2026-11-22
description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
  guide covers DocumentBuilder, command button placement, and saving the .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert forms2ole control word
- Aspose.Words
- DocumentBuilder
- command button
- C# Word automation
language: en
lastmod: 2026-11-22
og_description: Insert Forms2Ole control in Word with C#. Follow this guide to add
  a command button using Aspose.Words and DocumentBuilder.
og_image_alt: Screenshot of a Word document showing an inserted Forms2Ole command
  button created with C#
og_title: Insert Forms2Ole control in Word with C# – complete guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn to insert a Forms2Ole control in Word with C#. This step‑by‑step
    guide covers DocumentBuilder, command button placement, and saving the .docx.
  headline: How to insert Forms2Ole control in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: How to insert Forms2Ole control in Word using C# and Aspose.Words
url: /net/working-with-oleobjects-and-activex/how-to-insert-forms2ole-control-in-word-using-c-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to insert Forms2Ole control in Word using C# and Aspose.Words

If you need to **insert Forms2Ole control in Word**, this tutorial shows you exactly how to do it with C#. Whether you’re building a fillable template or automating form creation, the solution below lets you add a command button programmatically.

You’ll learn how to create a blank document, use `DocumentBuilder` to place the control, and save the result as a `.docx`. The guide also covers common pitfalls, such as coordinate systems and compatibility with older Word versions.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.6+)
* Aspose.Words for .NET (NuGet package `Aspose.Words`)
* A basic understanding of C# and the Word object model
* An IDE like Visual Studio or VS Code

## Step 1: Set up the project and import namespaces

Create a new console application and add the Aspose.Words package:

```bash
dotnet new console -n InsertForms2OleDemo
cd InsertForms2OleDemo
dotnet add package Aspose.Words
```

In `Program.cs` import the required namespaces:

```csharp
using System;
using System.Drawing;               // for Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;        // for Forms2OleControl
```

> **Pro tip:** Use the latest Aspose.Words version to get full support for the `Forms2OleControl` API.

## Step 2: Create a blank document and initialize DocumentBuilder

The `Document` class represents the Word file, while `DocumentBuilder` provides methods to insert content.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Initialize DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` works like a cursor; after this line you can start placing elements anywhere in the document.

## Step 3: Define the button’s position and size

Word measures coordinates in points (1 pt ≈ 1/72 in). The `Rectangle` struct from `System.Drawing` describes the control’s bounds.

```csharp
// Step 3: Define the button's position and size (x, y, width, height)
Rectangle buttonBounds = new Rectangle(0, 0, 100, 30); // 100 pt wide, 30 pt tall
```

* `0,0` places the control at the top‑left corner of the current page.
* Adjust `x` and `y` to move the button elsewhere (e.g., `new Rectangle(150, 200, 100, 30)`).

## Step 4: Insert the Forms2Ole command button

Now use `InsertForms2OleControl` to add the control. The method requires the control type, a name, and the bounds defined above.

```csharp
// Step 4: Insert a Forms2Ole command button named "ClickMe"
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,   // type of control
    "ClickMe",                  // internal name (used for VBA or macros)
    buttonBounds);              // position and size
```

The returned `Forms2OleControl` object lets you modify properties such as `Enabled`, `Visible`, or even attach a macro name later.

### Why use Forms2Ole?

* **Legacy compatibility** – Forms2Ole controls work in Word 97‑2003 (`.doc`) and newer `.docx` files.
* **Macro support** – They can trigger VBA macros, making them ideal for interactive templates.
* **Precise placement** – Unlike content controls, you control exact coordinates.

## Step 5: Save the document

Finally, write the file to disk. Choose a folder you have write access to.

```csharp
// Step 5: Save the document to see the inserted button
string outputPath = @"./output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Open `output.docx` in Microsoft Word. You’ll see a button labeled **ClickMe** at the top‑left corner of the first page. Clicking it in Word will do nothing until you assign a macro, but the control is fully functional.

## Handling common edge cases

| Situation | How to address it |
|-----------|-------------------|
| **Button appears off‑page** | Verify the `Rectangle` coordinates are within the page margins. Use `builder.PageSetup.PageWidth` and `PageHeight` to calculate safe bounds. |
| **Control not visible in older Word versions** | Save the document as `.doc` (`doc.Save("output.doc", SaveFormat.Doc)`) to guarantee Forms2Ole compatibility with Word 97‑2003. |
| **Need to change the caption** | After insertion, set `commandButton.Caption = "Submit";`. |
| **Assign a macro** | Set `commandButton.MacroName = "MyMacro"`; the macro must exist in the document’s VBA project. |
| **Multiple buttons** | Repeat Step 4 with different `Rectangle` values and unique names. |

## Complete, runnable example

Putting everything together, here is a self‑contained program you can copy, paste, and run:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace InsertForms2OleDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document
            Document doc = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Define button bounds (x, y, width, height) in points
            Rectangle buttonBounds = new Rectangle(0, 0, 100, 30);

            // Insert a Forms2Ole command button named "ClickMe"
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                "ClickMe",
                buttonBounds);

            // Optional: set button caption
            commandButton.Caption = "Click Me!";

            // Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output:** After running the program, `output.docx` opens in Word with a clickable button labeled *Click Me!* positioned at the top‑left of the first page.

## Conclusion

You now know how to **insert Forms2Ole control in Word** using C# and Aspose.Words. The process involves creating a `Document`, positioning a `Rectangle`, and calling `InsertForms2OleControl` via `DocumentBuilder`. With the full code sample and edge‑case guidance, you can integrate command buttons into any automated Word workflow.

### Next steps

* Explore other `ControlType` values such as `CheckBox` or `OptionButton`.
* Combine Forms2Ole controls with VBA macros for interactive forms.
* Use `DocumentBuilder.MoveTo` to place buttons on specific paragraphs or tables.
* Review Aspose.Words’ **Forms2Ole** documentation for advanced property settings.

Happy coding, and enjoy building richer Word documents with C# and Aspose.Words!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to insert OLE command button in a Word document using C#](/words/english/net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/)
- [how to add activex control in Word with Aspose.Words – step‑by‑step guide](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}