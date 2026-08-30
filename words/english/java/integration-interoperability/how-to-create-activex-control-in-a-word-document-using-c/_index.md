---
category: general
date: 2026-08-20
description: Learn how to create ActiveX control, set button size, and add button
  to Word with a complete C# example.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: en
lastmod: 2026-08-20
og_description: Create ActiveX control in a Word file with C#. This tutorial shows
  how to set button size, add button to Word, and make a clickable button.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Create an ActiveX control in Word – step‑by‑step C# guide
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: How to create ActiveX control in a Word document using C#
url: /java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create ActiveX control in a Word document using C#

If you need to **create ActiveX control** inside a Microsoft Word file, this guide shows you exactly how to do it. You’ll see how to **add button to Word**, set the button’s dimensions, and make the control clickable—all with a short, self‑contained C# program.

In this tutorial you will:

* Understand why an ActiveX control is useful for interactive Word documents.  
* Learn the exact code required to **set button size** and assign a caption.  
* See how to **create clickable button** that can later be wired to a macro or external logic.  

The steps work with Aspose.Words .NET 23.12 or later and require only a .NET development environment.

> **Prerequisite** – You have a valid Aspose.Words license (or you’re using the evaluation version) and Visual Studio 2022 or any C# IDE.

---

## How to create ActiveX control in a Word document

The first step is to instantiate a blank `Document` and a `DocumentBuilder`. The builder provides the high‑level API for inserting objects such as ActiveX controls.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

The `InsertActiveXButton` method (defined next) contains the logic for **how to insert button** and configure it.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

Running the program creates **ActiveXButton.docx**. Opening the file in Word shows a button labeled **Submit**. The control is fully functional—clicking it will raise the standard `CommandButton_Click` event, which you can later bind to a VBA macro.

### Why this works

* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**, which is the classic ActiveX button class.  
* The width and height arguments directly **set button size**; Word translates the values from points (1 pt ≈ 1/72 in).  
* Naming the control (`Name = "btnSubmit"`) makes it easy to locate from VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Set button size and caption

If you need a different appearance, adjust the numeric arguments in the `InsertForms2OleControl` call. The method signature is:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – The programmatic identifier of the ActiveX class (`"CommandButton"` for a standard button).  
* **width / height** – Size in points. For a 2 cm wide button, use `width = 56.7` (2 cm ≈ 56.7 pt).  

You can also modify the caption after insertion:

```csharp
commandButton.Caption = "Send Request";
```

Changing the caption does not affect the size, but it does affect the visual feedback for the user.

### Pro tip

If you want a square button, set both dimensions to the same value:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Add button to Word and make it clickable

The code above already **add button to Word**. To make the button perform an action, you must write a VBA macro that handles the `Click` event. Here’s a minimal macro you can paste into the Word VBA editor (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Because the control is named `btnSubmit`, Word automatically maps the `Click` event to `btnSubmit_Click`. This is the standard way to **create clickable button** functionality without external libraries.

> **Note:** Macro security settings in Word may block ActiveX controls. Ensure that “Enable all macros” or “Enable VBA macros” is selected for the document, or digitally sign the macro for production use.

---

## Common questions: how to insert button and troubleshooting

### 1. What if the button does not appear after saving?

* Verify that the Aspose.Words version supports `InsertForms2OleControl`. Versions prior to 22.5 lack this feature.  
* Ensure the target file format is `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.

### 2. Can I insert the button at a specific bookmark?

Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. How to **set button size** dynamically based on text length?

Calculate the required width using the `Graphics.MeasureString` method (from `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`). Then pass the computed width to `InsertForms2OleControl`.

### 4. Is there a way to add multiple buttons in a loop?

Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left` and `Top` properties for each iteration:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Expected output

When you run the program and open **ActiveXButton.docx**:

* A single **Submit** button appears near the top‑left of the first page.  
* The button size matches the dimensions you supplied (`100 pt × 30 pt`).  
* If you added the VBA macro, clicking the button shows a message box: “You clicked the Submit button!”.

You have now successfully **create ActiveX control**, **set button size**, and **add button to Word** while also learning **how to insert button** and **create clickable button** for future automation tasks.

---

## Conclusion

In this tutorial you learned how to **create ActiveX control** inside a Word document with C#. By following the steps you can **set button size**, give the control a meaningful name, and **add button to Word** so that it becomes a **clickable button** tied to a VBA macro.  

From here you might explore:

* Binding the button to a .NET COM add‑in instead of VBA.  
* Using other ActiveX classes such as `CheckBox` or `ComboBox`.  
* Automating the creation of full forms with multiple controls.

Feel free to experiment with different sizes


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}