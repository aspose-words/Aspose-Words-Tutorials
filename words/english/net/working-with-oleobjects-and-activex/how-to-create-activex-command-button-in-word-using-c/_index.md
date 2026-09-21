---
category: general
date: 2026-09-21
description: Learn how to create ActiveX command button in a Word document with Aspose.Words
  and C#. Step‑by‑step guide covers insertion, positioning, and saving.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: en
lastmod: 2026-09-21
og_description: Create ActiveX command button in a Word document using C# and Aspose.Words.
  Follow this complete tutorial to insert, position, and save the button programmatically.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Create an ActiveX command button in Word with C# – full guide
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: How to create ActiveX command button in Word using C#
url: /net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create ActiveX command button in Word using C#

If you need to **create ActiveX command button** inside a Word file, this guide shows you the exact steps. Using Aspose.Words for .NET you can add, position, and configure the button entirely from C# code.

Programmatic insertion of an ActiveX button eliminates manual UI work and enables automated document generation for forms, reports, or interactive templates. In this tutorial you’ll learn how to use **DocumentBuilder**, the **InsertForms2OleControl** method, and related properties to achieve a fully functional button.

## What you’ll need

Before you start, make sure you have:

* .NET 6.0 SDK or later (the code also works with .NET Framework 4.7+)
* Aspose.Words for .NET (NuGet package `Aspose.Words`)
* An IDE such as Visual Studio 2022 or VS Code
* Basic knowledge of C# and Word document concepts

No additional Office installation is required because Aspose.Words works independently of Microsoft Word.

## Step 1: Set up the C# project

Create a new console project and add the Aspose.Words package.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

The `Aspose.Words` library provides the **DocumentBuilder** class that we’ll use to manipulate the document.

## Step 2: Initialize the document and builder

The first code block creates a blank document and a `DocumentBuilder` instance. This object is the entry point for all Word‑processing operations.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `DocumentBuilder` maintains the current cursor position, so any insertion that follows will appear exactly where you place the cursor.

## Step 3: Insert the ActiveX command button

The **InsertForms2OleControl** method creates an ActiveX control of the requested type. Here we request a `CommandButton` and specify its size in points (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Explanation:**  
* `OleControlType.CommandButton` tells Aspose.Words to create a button rather than another control type.  
* The method returns a `Forms2OleControl` object, which exposes positioning and property fields.

## Step 4: Position the button and set its properties

After insertion you can move the button to any location on the page and give it a programmatic name and visible caption.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Pro tip:** The coordinate system starts at the top‑left corner of the page. Adjust `Left` and `Top` to align the button with other form fields.

## Step 5: Save the document

Finally, write the document to disk. The file will contain the ActiveX button, ready to be opened in Microsoft Word where the button becomes interactive.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

When you open `ActiveXCommandButton.docx` in Word, you’ll see a button labeled **Submit** at the specified location. Clicking it in Word will trigger the default command‑button behavior (which you can later customize with VBA or Word add‑ins).

## Complete, runnable example

Putting all the pieces together yields a self‑contained program you can copy, paste, and run.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Expected output:** The console prints *“Document created successfully.”* and the folder now contains `ActiveXCommandButton.docx`. Opening the file in Microsoft Word shows a clickable **Submit** button positioned 100 pt from the left margin and 150 pt from the top of the page.

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| The button appears off‑page | `Left`/`Top` values exceed page dimensions | Use `doc.FirstSection.PageSetup.PageWidth` and `PageHeight` to calculate safe coordinates |
| Button is not visible in Word | The document was saved in a format that strips ActiveX controls (e.g., `.txt`) | Always save as `.docx` or `.doc` |
| Runtime error `ArgumentOutOfRangeException` | Width or height is set to zero or negative | Ensure the size arguments passed to `InsertForms2OleControl` are positive numbers |

## Extending the solution

You can further customize the button by setting additional properties such as `Enabled`, `Visible`, or attaching a macro via VBA. The **Forms2OleControl** class also lets you insert other ActiveX controls like check boxes (`OleControlType.CheckBox`) or combo boxes (`OleControlType.ComboBox`).

If you need to generate multiple buttons in a loop, encapsulate the insertion logic in a helper method:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Conclusion

You now know how to **create ActiveX command button** in a Word document using C# and Aspose.Words. The tutorial covered setting up the project, inserting the button with `InsertForms2OleControl`, positioning it, and saving the final file. With this foundation you can automate complex forms, embed interactive controls, and integrate Word documents into larger .NET solutions.

Next, explore related topics such as **Aspose.Words ActiveX** form fields, **C# DocumentBuilder** advanced styling, or programmatically adding **ActiveX control in Word** for check boxes and drop‑down lists. Experiment with different coordinates and sizes to fit your specific layout requirements. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}