---
category: general
date: 2026-10-23
description: Create blank Word document with C# and learn how to insert ActiveX controls,
  including a button, using Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: en
lastmod: 2026-10-23
og_description: Create blank Word document with C# and learn how to insert ActiveX
  controls, including a button, using Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Create a blank Word document and add an ActiveX button in C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Create a blank Word document and add an ActiveX button in C# using Aspose.Words
url: /java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document and add an ActiveX button in C#

If you need to **create blank Word document** programmatically, this guide shows you exactly how. You’ll see a complete, runnable example that creates a new document, inserts an ActiveX CommandButton, and saves the file—all with Aspose.Words for .NET.

Working with Word files often requires more than plain text. Adding an **ActiveX button** lets you embed interactive functionality that can be used in macro‑enabled templates or Windows‑only solutions. By the end of this tutorial you’ll be able to insert any ActiveX control, but we focus on the most common scenario: a **word document activex button** that submits a form.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.7+)
* Visual Studio 2022 (or any C# IDE)
* **Aspose.Words for .NET** NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
* Basic familiarity with C# syntax

> **Pro tip:** Aspose.Words is a commercial library, but it offers a free temporary license for testing. Install the license early to avoid the evaluation watermark.

## Step 1: Create a blank Word document with Aspose.Words

The first step is to instantiate a `Document` object. This represents an empty `.docx` file in memory.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` starts with no sections, pages, or content. It’s the clean slate you need for **create blank word document** scenarios such as generating reports from scratch.

## Step 2: Obtain a DocumentBuilder to edit the document

`DocumentBuilder` provides a convenient API for adding text, images, and controls. We’ll use it to position the ActiveX control.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

The builder automatically adds a default section and a first page, so you can start inserting objects immediately.

## Step 3: How to insert ActiveX controls into the document

Aspose.Words exposes `InsertForms2OleControl` for embedding OLE/ActiveX objects. The method requires the control type, width, and height (in points). Below we insert a **CommandButton**—the classic form button you see in legacy Word templates.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Why this works:** `Forms2OleControlType.COMMANDBUTTON` tells Word to create a button that can respond to click events when the document is opened in a Windows environment that supports ActiveX.

## Step 4: Create an ActiveX control – set its properties

Now we give the button a programmatic name and a visible caption. This is the part of **create activex control** that developers often overlook.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` is the identifier you’ll reference from VBA macros (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` is the label displayed on the button itself.

## Step 5: Save the Word document with the ActiveX button

Finally, write the document to disk. The file extension must be `.docx` (or `.docm` if you plan to add macros later). The example saves to a placeholder folder—replace it with your own path.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

When you open the resulting file in Microsoft Word (Windows only), you’ll see a functional **word document activex button** that can be wired to VBA code.

## Full working example

Below is the complete program you can copy‑paste into a new console project.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output when you run the program**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Open the generated `ActiveXButton.docx` in Word, and you’ll see a button labeled **Submit** positioned at the top of the first page.

## Edge cases and common pitfalls

| Situation | What to watch for | Recommendation |
|-----------|-------------------|----------------|
| Running on macOS or Linux | ActiveX is a Windows‑only technology, so the button will appear as a placeholder. | Use the tutorial only for Windows‑targeted templates. |
| Document opened in Word Online | ActiveX controls are not supported in the browser view. | Provide a fallback UI or instruct users to open the file in the desktop client. |
| Need a macro‑enabled file | `.docx` files cannot store VBA code. | Save as `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) and add the macro separately. |
| Control size mismatch | Width/height values are in points (1 pt ≈ 1/72 in). | Adjust the numeric values to achieve the visual size you want. |

## Frequently asked questions

**How to insert ActiveX controls other than a button?**  
Use the same `InsertForms2OleControl` method but pass a different `Forms2OleControlType` enum value, such as `COMBOBOX` or `LISTBOX`.

**Can I change the button’s font or color?**  
ActiveX button appearance is governed by the host application (Word) and the underlying Windows theme. You can modify properties like `ForeColor` and `BackColor` via VBA after the document is opened.

**Is there a way to add a click handler directly from C#?**  
No. The click event must be handled by VBA or a Word add‑in because the button runs inside Word’s process, not your .NET application.

## Conclusion

You now know how to **create blank Word document** programmatically and embed an **ActiveX button** using Aspose.Words for .NET. The steps covered:

1. Instantiate a `Document`.
2. Use `DocumentBuilder` to work with the file.
3. Call `InsertForms2OleControl` to **how to insert activex** controls.
4. Configure the control’s properties (**create activex control**).
5. Save the file, yielding a **word document activex button** ready for VBA integration.

From here you can explore adding other control types, wiring VBA macros, or converting the document to PDF while preserving the button (as a static image). Experiment with different sizes, captions, and names.

## What should you learn next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step‑by‑step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}
{{< /blocks/products/products-backtop-button >}}