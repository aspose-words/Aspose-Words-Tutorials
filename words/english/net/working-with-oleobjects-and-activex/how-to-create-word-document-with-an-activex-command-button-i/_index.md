---
category: general
date: 2026-09-05
description: Create Word document using Aspose.Words C# and learn how to insert ActiveX
  command button, set button size, and add interactive button functionality.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to insert activex
- add command button
- add interactive button
- set button size
language: en
lastmod: 2026-09-05
og_description: Create Word document in C# and insert an ActiveX command button. This
  tutorial shows how to set button size and add interactive button features.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
  created with C#
og_title: Create Word document with ActiveX command button in C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  headline: How to create Word document with an ActiveX command button in C#
  type: TechArticle
- description: Create Word document using Aspose.Words C# and learn how to insert
    ActiveX command button, set button size, and add interactive button functionality.
  name: How to create Word document with an ActiveX command button in C#
  steps:
  - name: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
    text: '**Initialize a new document** and a `DocumentBuilder` to edit it.'
  - name: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
    text: '**Insert an ActiveX command button** using `InsertForms2OleControl`.'
  - name: '**Configure the button** – caption, size, and position.'
    text: '**Configure the button** – caption, size, and position.'
  - name: '**Save** the document to disk.'
    text: '**Save** the document to disk.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
- UI controls
title: How to create Word document with an ActiveX command button in C#
url: /net/working-with-oleobjects-and-activex/how-to-create-word-document-with-an-activex-command-button-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create Word document with an ActiveX command button in C#

If you need to **create Word document** programmatically and embed a clickable UI element, this guide shows you exactly how. Using Aspose.Words for .NET you can **create Word document**, **add command button**, and control its appearance—all without opening Microsoft Word.

You’ll learn to **how to insert ActiveX** controls, **set button size**, and make the button behave like an interactive UI component. No prior experience with COM or VBA is required; just a .NET development environment and the Aspose.Words library.

## What you’ll achieve

By the end of this tutorial you will:

* **Create a Word document** from scratch with C#.
* **Insert an ActiveX command button** (the classic “Click Me” control).
* **Set the button size** and position precisely.
* Optionally add simple **interactive button** logic (e.g., a macro placeholder).
* Save the file as a `.docx` that can be opened in Microsoft Word or any compatible viewer.

### Prerequisites

| Requirement | Reason |
|-------------|--------|
| .NET 6.0 or later | Provides the runtime for C# code. |
| Aspose.Words for .NET (latest version) | Supplies the `Document`, `DocumentBuilder`, and `Forms2OleControl` APIs used in the example. |
| Visual Studio 2022 (or any C# IDE) | Makes it easy to compile and run the sample. |
| Basic C# knowledge | Needed to understand the code flow. |

> **Pro tip:** If you’re using a trial version of Aspose.Words, make sure to set the license before running the code to avoid evaluation watermarks.

## How to create Word document – overall workflow

The process consists of four logical steps:

1. **Initialize a new document** and a `DocumentBuilder` to edit it.  
2. **Insert an ActiveX command button** using `InsertForms2OleControl`.  
3. **Configure the button** – caption, size, and position.  
4. **Save** the document to disk.

Each step is explained in its own section below.

![Word document with an ActiveX button](/images/activex-button.png "Screenshot of a Word document that contains an ActiveX command button created with C#")

## How to insert ActiveX command button

The **how to insert activex** part starts with the `InsertForms2OleControl` method. This method creates a COM‑based control that Word treats as an ActiveX object.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// 1️⃣ Create a blank document and a builder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 2️⃣ Insert an ActiveX CommandButton control.
//    Parameters: control type, width, height, left, top (all in points).
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // ActiveX type
    150,                           // Width (points)
    100,                           // Height (points)
    50,                            // Left offset from page margin
    50);                           // Top offset from page margin
```

**Why this works:** `OleControlType.CommandButton` tells Aspose.Words to create the classic VB‑style button. The size and location are expressed in points (1 point = 1/72 inch), which gives precise control over layout.

## How to add command button and set button size

After the control is inserted you can adjust its visual properties. The **add command button** step also covers **set button size**.

```csharp
// 3️⃣ Set the button's caption – the text the user sees.
commandButton.Caption = "Click Me";

// 4️⃣ Optionally change size after insertion (if you need dynamic sizing).
//    Width and height are mutable properties.
commandButton.Width = 200;   // New width in points
commandButton.Height = 80;   // New height in points

// 5️⃣ Move the button if you need a different position.
commandButton.Left = 100;    // New left offset
commandButton.Top = 120;     // New top offset
```

**Explanation:**  

* `Caption` is the label displayed on the button.  
* `Width` and `Height` let you **set button size** after the initial insertion—useful when the size depends on runtime data.  
* `Left` and `Top` reposition the control without recreating the document.

> **Common pitfall:** Forgetting to use points instead of pixels will cause the button to appear too small or too large. Always convert pixel values (`px * 72 / DPI`) if you start from screen measurements.

## How to add interactive button (optional)

An ActiveX button can execute a macro when clicked, but embedding VBA code from C# is out of scope for a pure Aspose.Words workflow. Instead, you can add a placeholder property that Word will recognize as a macro name.

```csharp
// 6️⃣ Assign a macro name (the macro must exist in the Word template).
commandButton.OleFormat.Object = "MyMacroName";
```

When the user opens the generated `.docx` in Word, clicking the button will attempt to run `MyMacroName`. If the macro does not exist, Word will prompt the user to create it.

**Why you might use this:** For corporate forms where a macro fills out fields, the C# code only needs to place the button; the macro logic lives in the document’s VBA project.

## Save the document and verify the result

```csharp
// 7️⃣ Save the document to the desired folder.
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "CommandButton.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

**Expected output:** Opening `CommandButton.docx` in Microsoft Word shows a button labeled **Click Me** positioned 100 pts from the left margin and 120 pts from the top. The button’s dimensions are **200 pts × 80 pts**. Clicking the button triggers the macro placeholder (if present).

## Full working example

Below is the complete, runnable program that puts everything together. Copy it into a new Console App project, add the Aspose.Words NuGet package, and run.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton, // ActiveX type
            150,                         // Initial width
            100,                         // Initial height
            50,                          // Left offset
            50);                         // Top offset

        // Set button caption and resize.
        commandButton.Caption = "Click Me";
        commandButton.Width = 200;   // Set button size (width)
        commandButton.Height = 80;   // Set button size (height)
        commandButton.Left = 100;    // Re‑position horizontally
        commandButton.Top = 120;     // Re‑position vertically

        // Optional: link to a macro named MyMacroName.
        commandButton.OleFormat.Object = "MyMacroName";

        // Save the document.
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Run the program, then open the generated file. You’ll see the **interactive button** ready for further customization.

## Frequently asked questions

| Question | Answer |
|----------|--------|
| **Does this work with .NET Core?** | Yes. Aspose.Words supports .NET Standard, so the same code runs on .NET 5/6/7. |
| **Can I use other ActiveX controls (e.g., CheckBox)?** | Absolutely. Replace `OleControlType.CommandButton` with `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **What if I need a larger button on a landscape page?** | Adjust the `Width`, `Height`, `Left`, and `Top` properties proportionally. Remember that points remain the same regardless of page orientation. |
| **Is a macro required for the button to be clickable?** | No. The button is fully functional as a UI element; a macro only adds custom behavior when clicked. |

## Conclusion

You now know how to **create Word document** with Aspose.Words, **add command button**, **set button size**, and optionally link the button to a macro for **add interactive button** behavior. This approach lets you automate form creation, generate dynamic reports, or build Word‑based UI prototypes directly from C#.

Next, you might explore:

* **How to insert ActiveX check boxes** for survey forms.  
* **How to add rich text content** around the button using `DocumentBuilder`.  
* **How to protect the document** while keeping the button functional.  

Feel free to experiment with different control types, sizes, and macro names to fit your specific scenario. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}