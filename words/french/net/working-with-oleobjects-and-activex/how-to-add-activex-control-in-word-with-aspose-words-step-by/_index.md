---
category: general
date: 2026-08-07
description: Apprenez à ajouter un contrôle ActiveX dans un document Word en utilisant
  C#. Comprend l'association d’une macro à un bouton et l’ajout d’exemples de boutons
  cliquables dans Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: fr
lastmod: 2026-08-07
og_description: Comment ajouter un contrôle ActiveX dans un document Word à l'aide
  d'Aspose.Words. Suivez ce guide pour insérer un bouton, associer une macro au bouton
  et ajouter un bouton cliquable.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: Comment ajouter un contrôle ActiveX dans Word – tutoriel complet C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Comment ajouter un contrôle ActiveX dans Word avec Aspose.Words – guide étape
  par étape
url: /fr/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# comment ajouter un contrôle activex dans Word avec Aspose.Words

If you need to **how to add activex control** in a Microsoft Word file programmatically, this tutorial shows you the exact steps using Aspose.Words for .NET. You’ll see how to insert a command button, set its caption, and **associate macro with button** so the control reacts when a user clicks it. By the end you’ll have a macro‑enabled `.docm` file that contains a fully functional button.

Adding an ActiveX button is a common requirement when building interactive templates such as loan applications, employee onboarding forms, or automated reports. This guide walks through every line of code, explains **why** each step matters, and covers the typical pitfalls you might encounter.

## Prerequisites

Before you start, make sure you have:

* .NET 6 (or .NET Core 3.1 / .NET Framework 4.8) installed.
* A valid Aspose.Words for .NET license or a temporary evaluation key.
* Visual Studio 2022 (or any IDE that supports C#).
* Basic familiarity with Word macros (VBA) if you plan to write the macro that the button will trigger.

> **Pro tip:** When you run the sample, save the output to a folder you have write permission for, otherwise `doc.Save` will throw an exception.

## How to add ActiveX control in a Word document using Aspose.Words

The core of the solution is a short C# program that creates a new document, inserts an ActiveX **CommandButton** control, and saves the file as a macro‑enabled document (`.docm`). The code is complete and ready to copy‑paste.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Why each line matters

| Line | Purpose |
|------|---------|
| `Document doc = new Document();` | Instantiates a fresh Word package in memory. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Provides a fluent API for inserting content, including ActiveX controls. |
| `InsertForms2OleControl` | The only Aspose.Words method that creates an ActiveX control; you specify the control type (`CommandButton`) and its geometry. |
| `commandButton.Caption = "Click Me";` | Sets the **add clickable button word** that the end‑user sees. Without a caption the button appears blank. |
| `commandButton.OnAction = "MyMacro";` | **associate macro with button** – tells Word which VBA macro to run when the control is clicked. |
| `doc.Save("CommandButton.docm");` | Persists the document as a macro‑enabled file; a regular `.docx` would strip the control and macro. |

> **Note:** The coordinates (left, top) are measured in points (1 pt ≈ 1/72 in). Adjust them to position the button where you need it on the page.

## How to associate macro with button

The `OnAction` property links the button to a VBA macro named `MyMacro`. You still need to create that macro inside the Word file, either manually or by injecting VBA code programmatically (Aspose.Words does not write VBA code). Here’s a minimal macro you can add using Word’s **Developer → Visual Basic** editor:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

When the user opens `CommandButton.docm` and clicks the button, Word executes `MyMacro` and shows a message box. If macro security is set to **Disable all macros without notification**, the button will appear disabled. Advise users to enable macros for the document or sign the macro with a trusted certificate.

### Common pitfalls when associating a macro

* **Macro security settings** – If the document is opened on a machine with strict security policies, the macro may be blocked. Provide instructions to lower the security level or sign the macro.
* **Naming conflicts** – The macro name must be unique within the document’s VBA project; otherwise Word will raise “duplicate procedure name” errors.
* **64‑bit vs 32‑bit Word** – ActiveX controls work the same, but the VBA editor may display different warning messages depending on the Office version.

## How to add clickable button word to a Word form

The `Caption` property is what users see on the button. You can customize it further:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

If you need the caption to change dynamically based on user input, you can later access the control via Word’s object model:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Edge case: Long captions

Word truncates captions that exceed the button’s width. To avoid clipping, either increase the width argument in `InsertForms2OleControl` or shorten the text. Testing with different languages (e.g., German or Japanese) is advisable because character width varies.

## How to add command button word for form automation

Beyond the visual caption, the **add command button word** concept covers the programmatic name of the control. Aspose.Words does not expose a direct `Name` property for ActiveX controls, but you can set the `AltText` field, which Word treats as the control’s identifier:

```csharp
commandButton.AltText = "SubmitButton";
```

Later in VBA you can reference the button by its `AltText` value:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

This technique is useful when you have multiple buttons and need to differentiate them programmatically.

## Full working example

Below is the complete program that you can compile and run as a console application. It includes optional styling, macro association, and a comment block describing each step.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Expected result:** Opening `SubmitForm.docm` in Microsoft Word displays a blue‑bordered button labeled *Submit Form*. Clicking the button triggers the VBA macro `SubmitMacro` (provided you added the macro to the document). The button can be moved, resized, or styled further using the same `Forms2OleControl` object.

## Testing the solution

1. Build and run the C# console app.
2. Open the generated `SubmitForm.docm` in Word.
3. If prompted, enable macros.
4. Click the *Submit Form* button – you should see the message box defined in `SubmitMacro`.

If the button appears but does nothing, double‑check that the macro name matches exactly (`SubmitMacro`) and that macro security is not blocking execution.

## Frequently asked questions

| Question | Answer |
|----------|--------|
| *Can I add more than one ActiveX button?* | Yes. Call `InsertForms2OleControl` multiple times with different coordinates. Use distinct `OnAction` and `AltText` values to differentiate them. |
| *Is the ActiveX control visible in Word Online?* | No. |

## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Add a New Section to Word Document | Aspose.Words for .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}