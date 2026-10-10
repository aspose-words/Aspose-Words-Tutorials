---
category: general
date: 2026-10-10
description: Set button text and add an ActiveX button in C# using Aspose.Words. Learn
  how to insert button, create button control, and customize the caption in a Word
  document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: en
lastmod: 2026-10-10
og_description: Set button text and add an ActiveX button in C# with Aspose.Words.
  Follow this step‑by‑step guide to insert a button, create button control, and customize
  its caption.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Set button text and add an ActiveX button in C# – complete guide
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Set button text and add an ActiveX button in C#
url: /java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set button text and add an ActiveX button in C#

If you need to **set button text** on an ActiveX button inside a Word document, this guide shows you exactly how. By the end of the tutorial you will be able to **insert button**, create a **button control**, and customize its caption with just a few lines of C# code.

Working with ActiveX controls is common when you want interactive forms in Word—whether you are building a contract template, a survey, or an internal tool. The example uses Aspose.Words for .NET, a library that lets you manipulate Word files without Microsoft Office installed.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* Visual Studio 2022 (or any IDE that supports C#)  
* An Aspose.Words for .NET license (the free evaluation works for learning)  

You also need a reference to the `Aspose.Words` NuGet package:

```bash
dotnet add package Aspose.Words
```

## How to insert button into a Word document

The first step is to create a new `Document` and a `DocumentBuilder`. The builder is the entry point for adding content, including ActiveX controls.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:** `Document` represents the entire .docx file, while `DocumentBuilder` provides high‑level methods like `InsertParagraph` and `InsertFormField`. Starting with a clean document ensures the button appears exactly where you want it.

## Create button control with Forms2OleControl

Now we create the actual button control. `Forms2OleControl` is the class Aspose.Words uses for all ActiveX objects, and the `COMMANDBUTTON` type renders as a clickable button in Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Explanation:**  
* `InsertForms2OleControl` places the control at the exact coordinates you provide.  
* The size is defined in points (1 point = 1/72 inch). Adjust these numbers to fit your layout.

## Add ActiveX control and give it a unique name

Every ActiveX object should have a distinct name so you can reference it later (for example, when handling events in VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Tip:** Avoid spaces or special characters in the name; Word treats the name as an identifier in its internal form model.

## Set button text (caption) on the ActiveX button

Here is where the primary keyword **set button text** comes into play. The `Caption` property defines the label that users see on the button.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

You can change the caption at any time before saving the document. If you later need to localize the UI, simply call `SetCaption` again with a different string.

## Save the document and verify the result

Finally, write the document to disk. Opening the file in Microsoft Word will show the button with the custom caption.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Expected output:** When you open *ActiveXButton.docx* in Word, you will see a button positioned at the specified coordinates, labeled **Click Me**. Clicking the button will trigger the default Word command button behavior (which you can later customize with VBA).

![Set button text example](https://example.com/activex-button.png){alt="Set button text example"}

## Add ActiveX button and handle events (optional)

If you need the button to perform a custom action, you can add a VBA macro that reacts to the `Click` event. The macro can be injected programmatically, but that is beyond the scope of this tutorial. The important part is that the button is already present and its caption is set—ready for any event handling you choose.

## Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| Button appears misaligned | Coordinates are in points, not pixels | Convert pixel values to points (`points = pixels * 72 / DPI`) |
| Caption does not change after saving | `SetCaption` called after `Save` | Always set the caption **before** calling `doc.Save` |
| Control not visible in older Word versions | Some older Word builds lack full ActiveX support | Test on the target Word version; consider using a `CheckBox` or `DropDownList` as fallback |
| License warning in output | Evaluation license expires | Apply a valid Aspose.Words license via `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Full, runnable example

Below is the complete program you can copy, paste, and run. It includes all necessary `using` directives and demonstrates the entire workflow from document creation to saving.

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
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Run the program with `dotnet run`. After execution, open *ActiveXButton.docx* to confirm that the button’s caption reads **Click Me**.

## Recap of what you learned

* You learned how to **set button text** on an ActiveX button using Aspose.Words.  
* You saw the exact steps to **how to insert button**, **create button control**, and **add activex control** to a Word document.  
* You now have a reusable code snippet that you can adapt for any form‑based Word automation project.

## Next steps

* Explore other `Forms2OleControlType` values such as `CHECKBOX` or `LISTBOX` to build richer forms.  
* Combine the button with a VBA macro to perform calculations or data validation.  
* Use Aspose.Words’ `FormField` API to read user input after the document is filled out.

Feel free to experiment with the size, position, and caption to match your design requirements. If you run into any issues, the Aspose.Words documentation provides detailed references for every class used in this tutorial.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}