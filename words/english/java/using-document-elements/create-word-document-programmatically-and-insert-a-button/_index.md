---
category: general
date: 2026-09-21
description: Create word document programmatically and learn how to save word document
  button, insert command button word, and set command button caption using DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: en
lastmod: 2026-09-21
og_description: Create word document programmatically with Aspose.Words. Learn how
  to save word document button, insert command button word, set command button caption,
  and use DocumentBuilder for interactive forms.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Create word document programmatically and add a button
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Create word document programmatically and insert a button
url: /java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create word document programmatically and insert a button

If you need to **create word document programmatically**, Aspose.Words provides a fluent API that lets you add interactive controls such as a CommandButton. This tutorial also explains **how to use DocumentBuilder**, how to **save word document button**, and how to **set command button caption** so the button appears exactly as you expect inside the .docx file.

You will learn how to:

* Initialize a blank document with `Document`.
* Work with `DocumentBuilder` to edit the document.
* Insert a **CommandButton** (`insert command button word`).
* Set the button’s name and visible caption (`set command button caption`).
* Persist the result to disk (`save word document button`).

The steps are written for .NET developers using C# and the latest Aspose.Words for .NET (v24.10). No additional NuGet packages are required beyond Aspose.Words.

---

## What you need before you start

| Prerequisite | Reason |
|--------------|--------|
| Visual Studio 2022 (or any C# IDE) | To compile and run the sample code. |
| .NET 6.0 SDK or later | Provides the runtime for the example. |
| Aspose.Words for .NET (v24.10 or newer) | The library that lets you **create word document programmatically** and manipulate form controls. |
| Basic familiarity with C# and OOP concepts | Required to understand the code flow. |

You can install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Create word document programmatically

The first step is to instantiate an empty `Document`. This object represents the entire Word file in memory.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Creating the document programmatically gives you a clean canvas on which you can add paragraphs, tables, or interactive controls.  

---

## How to use DocumentBuilder

`DocumentBuilder` is the primary class for editing a `Document`. It provides methods to insert text, images, and form fields. In this tutorial we use it to place a CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder maintains an internal cursor that points to the current insertion location. By default it starts at the beginning of the first section, which is ideal for our example.

---

## Insert command button word

Aspose.Words treats a CommandButton as an ActiveX control. The `InsertForms2OleControl` method creates a generic OLE control that we then configure as a button.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

At this point the control exists in the document but has no visual representation until we define its type.

---

## Set command button caption

Now we tell the OLE control that it should behave like a CommandButton and give it a friendly label.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Setting the **command button caption** is essential because Word displays this text on the button surface. If you omit `SetCaption`, the button will appear with a generic label.

---

## Save word document button

Finally, persist the document to disk. The `Save` method writes the entire Word package, including the newly inserted button, to a .docx file.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

The file `CommandButton.docx` now contains a fully functional button labeled **Submit**. When the user opens the file in Microsoft Word and clicks the button, the default action (which you can later bind via VBA) will be triggered.

---

## Full working example

Below is the complete program that you can copy, paste, and run. It demonstrates the entire workflow from document creation to saving the button.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected result**

* A file named `CommandButton.docx` located at the path you specified.
* Opening the file in Microsoft Word shows a single **Submit** button on the first page.
* The button can be selected, resized, or linked to a macro from Word’s **Developer** tab.

---

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| *What if I need more than one button?* | Repeat steps 3–6 with different names and captions. Each button must have a unique `SetName` value. |
| *Can I set the button size?* | Yes. After inserting the control, you can modify its `Width` and `Height` properties via the `OleFormat` object. |
| *Will the button work on all Word versions?* | ActiveX controls are supported in the desktop version of Word (Windows). They are not rendered in Word Online or on macOS. |
| *How to add a click handler?* | You need to write VBA code that references the button’s name (`btnSubmit`). The VBA macro can be embedded using `doc.VbaProject`. |
| *What if I need to insert the button inside a table cell?* | Move the builder’s cursor to the desired cell (`builder.MoveTo(cell.FirstParagraph)`) before calling `InsertForms2OleControl`. |

---

## Pro tips

* **Pro tip:** Always set a meaningful name with `SetName`. It simplifies VBA automation and makes debugging easier.
* **Watch out for:** Forgetting to call `SetControlType`. Without this call the OLE object appears as a generic placeholder rather than a clickable button.
* **Performance tip:** If you are generating many documents in a loop, reuse a single `DocumentBuilder` instance and call `builder.MoveToDocumentEnd()` before each insertion to avoid unnecessary cursor resets.

---

## Next steps

Now that you know how to **create word document programmatically**, **insert command button word**, **set command button caption**, and **save word document button**, you can explore more advanced scenarios:

* Add **TextFormField** controls for user input.
* Combine buttons with **MacroButton** fields to execute VBA directly.
* Use **DocumentBuilder.InsertImage** to place icons on your buttons.
* Integrate with ASP.NET to generate Word forms on


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}