---
category: general
date: 2026-08-14
description: How to add ActiveX button in a Word document using Aspose.Words – learn
  to create an empty Word document and insert an ActiveX button programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert activex button
- create empty word document
- create word document aspose
language: en
lastmod: 2026-08-14
og_description: How to add ActiveX button in a Word document with Aspose.Words. This
  tutorial shows you how to create an empty Word document, insert an ActiveX button,
  and save the result.
og_image_alt: Screenshot of an ActiveX button inserted into a Word document using
  Aspose.Words
og_title: How to add ActiveX button in Word – Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  headline: How to add ActiveX button in a Word document with Aspose.Words
  type: TechArticle
- description: How to add ActiveX button in a Word document using Aspose.Words – learn
    to create an empty Word document and insert an ActiveX button programmatically.
  name: How to add ActiveX button in a Word document with Aspose.Words
  steps:
  - name: Does the button work in all Word versions?
    text: ActiveX controls are supported in the desktop version of Word on Windows.
      They are not rendered in Word Online, Word for macOS, or mobile clients. If
      you need cross‑platform interactivity, consider using content controls or HTML‑based
      solutions instead.
  - name: What if I need a different size or position?
    text: '`InsertForms2OleControl` places the control at the current builder cursor.
      To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify
      the control’s `Left` and `Top` properties after creation:'
  - name: Can I add other ActiveX types?
    text: Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`,
      `ListBox`, and more. Replace `CommandButton` with the desired enum value and
      adjust properties accordingly.
  - name: Is a macro required for the button to do something?
    text: The button itself does nothing until you attach VBA code. In Word, press
      **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the
      desired logic. The generated document will retain the VBA project if you enable
      the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- Word automation
- C#
title: How to add ActiveX button in a Word document with Aspose.Words
url: /net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to add ActiveX button in a Word document with Aspose.Words

If you need to **how to add ActiveX** controls to a generated Word file, this guide shows you the exact steps. You’ll learn to **insert ActiveX button** programmatically, starting from a **create empty Word document** and ending with a saved file that can be opened in Microsoft Word.

Adding a button that runs VBA code or triggers a macro is a common requirement for automated report generators, form templates, or interactive contracts. Using Aspose.Words for .NET lets you build the document without launching Office, keeping the process fast and server‑friendly.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 (or later) SDK installed.
* Visual Studio 2022 or any C#‑compatible IDE.
* Aspose.Words for .NET NuGet package (`Aspose.Words` version 24.9 or newer).  
  Install it with:
  ```bash
  dotnet add package Aspose.Words
  ```
* A Windows environment if you plan to test the ActiveX button, because ActiveX controls require the Windows version of Microsoft Word.

## Step 1: Create an empty Word document

The first task is to **create empty Word document** in memory. Aspose.Words provides the `Document` class for this purpose.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, blank Word document.
Document doc = new Document();
```

`Document` represents the entire .docx file. At this point the document contains no pages, but you can start adding content immediately.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` is a helper that lets you insert text, images, and other objects into the document. It works on the `Document` instance you just created.

```csharp
// Initialise the builder with the blank document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder maintains a cursor position; anything you insert after this line appears at the start of the first page.

## Step 3: Insert an ActiveX CommandButton control

Aspose.Words exposes the `InsertForms2OleControl` method for adding legacy form controls, including ActiveX. The method requires the control type and its size in points.

```csharp
// Insert an ActiveX CommandButton (150x30 points).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton, 150, 30);
```

The returned `Forms2OleControl` object lets you configure properties such as the control’s name and caption.

## Step 4: Configure the button’s properties

Setting a meaningful `Name` enables you to reference the control from VBA code later. The `Caption` is the text the user sees on the button.

```csharp
// Set the button’s programmatic name (used in VBA) and displayed caption.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

> **Pro tip:** Keep the name short and alphanumeric; Word will reject names that contain spaces or special characters.

## Step 5: Save the document

Finally, write the document to disk. Use the `.docx` extension for modern Word files; the ActiveX button works the same way in `.doc` files, but `.docx` is the preferred format for new projects.

```csharp
// Save the document containing the ActiveX button.
doc.Save(@"C:\Temp\ActiveXButton.docx");
```

When you open `ActiveXButton.docx` in Microsoft Word, you’ll see a clickable **Submit** button. If you enable macros, you can attach VBA code to `btnSubmit_Click` and have it execute when the user clicks the button.

## Full, runnable example

Putting all the pieces together gives you a self‑contained program that you can copy, paste, and run.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create an empty Word document.
            Document doc = new Document();

            // Step 2: Initialise DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX CommandButton control.
            Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, 150, 30);

            // Step 4: Set button properties.
            cmdBtn.Name = "btnSubmit";
            cmdBtn.Caption = "Submit";

            // Step 5: Save the document.
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output** – After running the program, the console prints the save location, and opening the generated file in Word shows a button labeled **Submit** positioned at the top of the first page.

## Handling common questions and edge cases

### Does the button work in all Word versions?

ActiveX controls are supported in the desktop version of Word on Windows. They are not rendered in Word Online, Word for macOS, or mobile clients. If you need cross‑platform interactivity, consider using content controls or HTML‑based solutions instead.

### What if I need a different size or position?

`InsertForms2OleControl` places the control at the current builder cursor. To move it, adjust the cursor with `builder.MoveTo` before insertion, or modify the control’s `Left` and `Top` properties after creation:

```csharp
cmdBtn.Left = 100;   // points from the left margin
cmdBtn.Top = 200;    // points from the top margin
```

### Can I add other ActiveX types?

Yes. The `Forms2OleControlType` enumeration includes `CheckBox`, `OptionButton`, `ListBox`, and more. Replace `CommandButton` with the desired enum value and adjust properties accordingly.

### Is a macro required for the button to do something?

The button itself does nothing until you attach VBA code. In Word, press **Alt+F11** to open the VBA editor, locate `btnSubmit_Click`, and write the desired logic. The generated document will retain the VBA project if you enable the **SaveFormat.Doc** (legacy `.doc`) format, but `.docx` files cannot store VBA macros. Use the `.doc` format if you need embedded VBA.

## Conclusion

You now know **how to add ActiveX** controls to a Word file using Aspose.Words. By following the steps to **create empty Word document**, initialise a `DocumentBuilder`, **insert ActiveX button**, configure its properties, and save the file, you can generate interactive Word templates directly from your .NET code.

Next, explore related topics such as **insert ActiveX button** event handling, adding **create word document aspose** for tables or images, and securing macro‑enabled documents for enterprise deployment. Experiment with different control types and layout options to tailor the user experience to your application’s needs.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}