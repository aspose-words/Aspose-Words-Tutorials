---
category: general
date: 2026-11-18
description: Learn how to create a blank Word document and insert an ActiveX button using Aspose.Words for .NET with C#. Add control, set button caption, and save the file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- how to add control
- insert activex button
- set button caption
language: en
lastmod: 2026-11-18
og_description: Create a blank Word document and insert an ActiveX button using C#.
  Follow this complete tutorial to add control, set button caption, and save the result.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX button with
  the caption “Press”
og_title: Create a blank Word document and insert an ActiveX button – step‑by‑step
  guide
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  headline: Create a blank Word document and insert an ActiveX button
  type: TechArticle
- description: Create a blank Word document and insert an ActiveX button with C#.
    Learn how to add control, set button caption, and save the file.
  name: Create a blank Word document and insert an ActiveX button
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET installed (`Install-Package Aspose.Words`). * Basic familiarity with
      C# and Visual Studio or any .NET‑compatible IDE.'
  - name: Tip
    text: 'If you need the button to appear on a specific page, move the builder’s
      cursor first:'
  - name: Expected result
    text: Opening `with_button.docx` in Word shows a blank page with a rectangular
      button labeled **Press**. Clicking the button does nothing by default because
      no VBA macro is attached, but the control is fully functional and can be wired
      to code later.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Create a blank Word document and insert an ActiveX button using Aspose.Words for .NET
url: /net/working-with-oleobjects-and-activex/create-a-blank-word-document-and-insert-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document and insert an ActiveX button

If you need to **create a blank Word document** and place an interactive ActiveX button inside it, this guide shows you exactly how to do it with Aspose.Words for .NET. You’ll see the full code, understand why each line matters, and learn how to **set button caption** so the control looks ready for user interaction.

In addition to the primary goal, we’ll cover **how to insert ActiveX**, the steps **how to add control** to a Word file, and the nuances of **insert ActiveX button** with a custom caption. By the end you’ll have a reusable pattern for any document‑automation scenario that requires embedded UI elements.

## What you’ll learn

* How to **create a blank Word document** programmatically.  
* The exact API calls required to **insert ActiveX button** and configure its properties.  
* How to **set button caption** so the control displays the desired text.  
* Tips for saving the file in a location of your choice and handling common pitfalls.

### Prerequisites

* .NET 6.0 or later (the code also works with .NET Framework 4.6+).  
* Aspose.Words for .NET installed (`Install-Package Aspose.Words`).  
* Basic familiarity with C# and Visual Studio or any .NET‑compatible IDE.

---

## Create a blank Word document with Aspose.Words

The first step is to instantiate an empty `Document` object. This object represents a Word file that contains no content until we add something.

```csharp
// Step 1: Create a new blank document
Document document = new Document();
```

*Why this matters*: An empty `Document` gives you a clean canvas. You can later add paragraphs, tables, or controls without worrying about existing formatting.

---

## Initialise a DocumentBuilder to work with the document

`DocumentBuilder` is a helper class that lets you insert content at the current cursor position. It automatically tracks where you are in the document.

```csharp
// Step 2: Initialise a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: Without a `DocumentBuilder` you would need to manipulate the low‑level node tree manually. The builder simplifies insertion of text, images, and ActiveX controls.

---

## How to insert an ActiveX button (insert activex button)

Now we use `InsertForms2OleControl` to embed an ActiveX control. The method requires three arguments:

1. The type of control (`Forms2OleControlType.CommandButton`).  
2. An internal name for the control (used by VBA or macro code).  
3. A `RectangleF` that defines the position and size on the page.

```csharp
// Step 3: Insert a CommandButton ActiveX control at the current cursor position
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,          // type of control
    "ClickMe",                             // internal name (identifier)
    new System.Drawing.RectangleF(0, 0, 100, 30)); // x, y, width, height
```

*Why this matters*: This is the core of **how to insert activex** into a Word document. The rectangle’s coordinates are expressed in points (1 point = 1/72 inch). Adjust them to position the button where you need it.

### Tip

If you need the button to appear on a specific page, move the builder’s cursor first:

```csharp
builder.MoveToSection(0);  // moves to the first (and only) section
builder.InsertParagraph(); // ensures there is a paragraph to host the control
```

---

## How to set button caption (set button caption)

After the control is placed, you can modify its properties. The most visible property is `Caption`, which determines the text shown on the button.

```csharp
// Step 4: Set the visible caption of the button
commandButton.Caption = "Press";
```

*Why this matters*: Users see the caption, not the internal name. Changing it makes the button meaningful in the final document.

---

## Save the document containing the button

Finally, write the document to disk. You can choose any supported format (`.docx`, `.pdf`, etc.). Here we save as a Word document.

```csharp
// Step 5: Save the document with the ActiveX button
string outputPath = @"C:\Temp\with_button.docx";
document.Save(outputPath);
```

*Why this matters*: Persisting the file allows you to open it in Microsoft Word and test the button. When the document is opened, the button will appear with the caption “Press”.

### Expected result

Opening `with_button.docx` in Word shows a blank page with a rectangular button labeled **Press**. Clicking the button does nothing by default because no VBA macro is attached, but the control is fully functional and can be wired to code later.

---

## How to add control to a specific paragraph (how to add control)

Sometimes you want the button inside a particular paragraph, for example after some instructional text. Use `MoveTo` to position the builder before inserting the control.

```csharp
// Example: add a paragraph, then insert the button after it
builder.Writeln("Click the button below to continue:");
builder.InsertParagraph(); // creates a new empty paragraph
builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    "ContinueBtn",
    new System.Drawing.RectangleF(0, 0, 120, 35));
```

*Why this matters*: This pattern demonstrates **how to add control** in context, ensuring the document layout remains logical.

---

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Button appears off‑page | Rectangle coordinates are outside the page margins | Use `builder.PageSetup` to get page dimensions and calculate a safe `RectangleF`. |
| Caption does not show | `Caption` set before the control is fully initialised | Set `Caption` **after** the `InsertForms2OleControl` call, as shown in Step 4. |
| Document saves without the button | Builder’s cursor was moved after insertion without committing changes | Keep the builder on the same page or call `builder.Document.UpdatePageLayout()` before saving. |

---

## Full, runnable example

Below is the complete program you can copy, paste, and run. It creates a blank Word file, inserts an ActiveX button, sets its caption, and saves the result.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Initialise DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // Optional: add some explanatory text
        builder.Writeln("Below is an ActiveX button created programmatically:");
        builder.InsertParagraph();

        // 3️⃣ Insert the ActiveX CommandButton
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            "MyButton",
            new RectangleF(0, 0, 100, 30));

        // 4️⃣ Set the button caption
        commandButton.Caption = "Press";

        // 5️⃣ Save the document
        string outputPath = @"C:\Temp\with_button.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output**: After running the program, open `C:\Temp\with_button.docx` in Microsoft Word. You’ll see a single page with the text “Below is an ActiveX button created programmatically:” followed by a button labeled **Press**.

---

## Conclusion

You now know how to **create a blank Word document**, **insert an ActiveX button**, **set button caption**, and **save** the result using Aspose.Words for .NET. The same pattern can be extended to other ActiveX controls (checkboxes, list boxes, etc.) by changing `Forms2OleControlType`.  

Next, you might explore **how to insert ActiveX button** events with VBA, or **how to add control** to existing documents that already contain content. Both topics build directly on the concepts covered here.

Happy coding, and feel free to experiment with different sizes, positions, and captions to fit your application’s UI requirements!


## What should you learn next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create Word document C# with an ActiveX command button](/words/english/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}