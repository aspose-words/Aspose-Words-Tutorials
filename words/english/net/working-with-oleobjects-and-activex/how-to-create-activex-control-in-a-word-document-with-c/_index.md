---
category: general
date: 2026-09-14
description: Create ActiveX control in a Word document with C#. Learn how to insert
  ActiveX, add interactive button, and generate the .docx file programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: en
lastmod: 2026-09-14
og_description: Create ActiveX control in a Word document with C#. Follow this complete
  example to insert ActiveX, add interactive button, and save the file.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Create ActiveX control in Word using C# – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: How to create ActiveX control in a Word document with C#
url: /net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create ActiveX control in a Word document with C#

If you need to **create ActiveX control** inside a Microsoft Word file, this guide shows you a complete, ready‑to‑run solution. You’ll see exactly how to insert an ActiveX CommandButton, set its properties, and save the resulting `.docx` file using only C# code.

Adding an interactive button to a Word document is a common requirement when you want end‑users to trigger macros or custom logic directly from the document UI. The example below demonstrates **how to insert ActiveX** without relying on third‑party tools, and it also covers **how to create Word document** programmatically.

By the end of this tutorial you will be able to **create button with code**, customize its caption, and produce a portable Word file that preserves the ActiveX control.

## Prerequisites

- .NET 6.0 or later (the Aspose.Words for .NET library works with .NET Core and .NET Framework)
- A reference to the `Aspose.Words` NuGet package  
  ```bash
  dotnet add package Aspose.Words
  ```
- Basic knowledge of C# and object‑oriented programming

## Step 1: Set up the project and import namespaces

Create a new console project (or integrate the code into any existing C# application). Import the required namespaces so the compiler can locate the Word‑processing classes.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Why this step matters** – The `Aspose.Words` API supplies the `Document`, `DocumentBuilder`, and `Forms2OleControl` classes that let you manipulate Word files at the object level. Without these references the rest of the code would not compile.

## Step 2: Create a new Word document and a DocumentBuilder

The `Document` object represents the entire `.docx` package, while `DocumentBuilder` offers a fluent API for inserting content.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Explanation** – Instantiating a fresh `Document` gives you a clean canvas. The builder’s cursor starts at the beginning of the first section, ready for the next insertion.

## Step 3: Insert the ActiveX CommandButton

Use `InsertForms2OleControl` to place an ActiveX control at a specific location. The method requires the control type, and a `RectangleF` that defines the X/Y coordinates and size (in points).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Why this works** – `OleControlType.CommandButton` tells the API to create a standard Windows CommandButton. The rectangle positions the button relative to the page’s top‑left corner, allowing you to **add interactive button** exactly where you need it.

## Step 4: Configure the button’s properties

Now set the button’s visible text (`Caption`) and its internal name (`Name`). These properties are what users see and what VBA code can reference later.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Practical tip** – The `Name` must be unique within the document; otherwise, VBA macros may reference the wrong control.

## Step 5: Save the document

Finally, write the file to disk. The ActiveX control is stored inside the Word package, so the saved file will retain full functionality when opened in Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Result** – Opening `CommandButton.docx` in Word shows a clickable CommandButton labeled “Click Me”. The control can be linked to a macro via the Word UI (`Developer → Design Mode → Properties`).

## Full source listing

Putting all steps together yields a single, self‑contained program you can copy, paste, and run.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Expected output

Running the program prints a confirmation line:

```
Document saved to C:\Temp\CommandButton.docx
```

When you open the generated file in Microsoft Word, you will see a **CommandButton** placed at the specified coordinates. Clicking the button in design mode highlights it; in run mode it behaves like any standard ActiveX button.

## Common variations and edge cases

| Scenario | Adjustment |
|----------|------------|
| **Different control type** | Replace `OleControlType.CommandButton` with `OleControlType.CheckBox`, `OleControlType.OptionButton`, etc. |
| **Multiple buttons** | Call `InsertForms2OleControl` repeatedly, updating the `RectangleF` coordinates for each new button. |
| **Dynamic sizing** | Compute rectangle dimensions based on page size (`builder.PageSetup.PageWidth`). |
| **Saving to a stream** | Use `document.Save(stream, SaveFormat.Docx)` when you need to return the file from a web API. |
| **Word 97‑2003 format** | Change the save format to `SaveFormat.Doc` to produce a `.doc` file that still embeds the ActiveX control. |

> **Pro tip:** Always test the generated document on the target version of Word, because older versions may enforce security settings that disable ActiveX controls by default.

## Frequently asked questions

**Does this work with .NET Core?**  
Yes. The Aspose.Words library is cross‑platform and fully compatible with .NET Core and .NET 5/6+.

**Can I assign a macro to the button programmatically?**  
The API does not embed VBA code directly. After the document is generated, open it in Word, enable the Developer tab, and record or write a macro that references `btnClick`.

**What if the button does not appear?**  
Check that the `Developer` tab is enabled in Word and that the document is not opened in **Protected View**. Also verify that the rectangle coordinates are within the page margins.

## Conclusion

You now know how to **create ActiveX control** inside a Word file using C#. The tutorial covered **how to insert ActiveX**, demonstrated **add interactive button**, showed **create Word document** from scratch, and illustrated **create button with code** that persists after saving.  

From here you can explore additional ActiveX types, connect the button to VBA macros, or embed the logic in a larger document‑generation service. Experiment with different sizes, positions, and control properties to fit the exact user experience you need.

---


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}