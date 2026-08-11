---
category: general
date: 2026-08-10
description: Create word document programmatically with Aspose.Words, then add an
  ActiveX control word button. Insert activex command button in minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add activex control word
- insert activex command button
language: en
lastmod: 2026-08-10
og_description: Create word document programmatically using Aspose.Words, then add
  an ActiveX control word button. Learn how to insert activex command button quickly.
og_image_alt: Screenshot of a Word document created programmatically with an ActiveX
  command button
og_title: Create word document programmatically – add an ActiveX button in C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  headline: Create word document programmatically and add ActiveX button
  type: TechArticle
- description: Create word document programmatically with Aspose.Words, then add an
    ActiveX control word button. Insert activex command button in minutes.
  name: Create word document programmatically and add ActiveX button
  steps:
  - name: Open `ActiveX_CommandButton.docx` in Microsoft Word.
    text: Open `ActiveX_CommandButton.docx` in Microsoft Word.
  - name: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
    text: Enable the **Developer** tab if it isn’t visible (`File → Options → Customize
      Ribbon → check Developer`).
  - name: Click **Design Mode**. The button should appear with the label “Submit”.
    text: Click **Design Mode**. The button should appear with the label “Submit”.
  - name: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
    text: If you added an `OnAction` macro, click the button while Design Mode is
      off to trigger the macro.
  type: HowTo
tags:
- Aspose.Words
- ActiveX
- C#
title: Create word document programmatically and add ActiveX button
url: /net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create word document programmatically and add ActiveX button

If you need to **create word document programmatically**, this guide walks you through the entire process with Aspose.Words for .NET. You’ll also learn how to **add activex control word** elements and **insert activex command button** objects in a single, self‑contained example.

Generating Word files from code removes the manual step of opening Microsoft Word, letting you build reports, invoices, or data‑driven contracts automatically. By the end of this tutorial you will have a ready‑to‑run C# console app that produces a `.docx` file containing an interactive ActiveX CommandButton.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later (the code also works with .NET Framework 4.6+)
* Visual Studio 2022 or any IDE that supports .NET development
* A valid Aspose.Words for .NET license (you can use the free evaluation key for testing)
* Basic familiarity with C# syntax and the concept of COM/ActiveX controls

> **Pro tip:** If you plan to distribute the generated document to users who don’t have Word installed, embed the ActiveX control’s runtime files alongside the `.docx` or provide a macro‑enabled template.

## Create word document programmatically – initial setup

First, add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

Then create a new console project (if you don’t already have one):

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
```

Open the generated `Program.cs` file – we’ll replace its contents with the full solution below.

## Step 1: Import namespaces and configure the license

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // OPTIONAL: Apply your Aspose.Words license to remove evaluation watermarks.
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");
```

*Why this matters*: Importing `Aspose.Words.Drawing` gives you access to `Forms2OleControl`, the class that represents an ActiveX control inside a Word document. Setting a license early prevents runtime warnings in production.

## Step 2: Create a blank document and a DocumentBuilder

```csharp
            // Create a new empty Word document.
            Document doc = new Document();

            // DocumentBuilder provides a convenient API for inserting text, tables, and controls.
            DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` object is the in‑memory representation of a `.docx` file. `DocumentBuilder` works like a cursor that you move around the document to insert elements.

## Step 3: Insert an ActiveX CommandButton control

```csharp
            // Insert an ActiveX CommandButton.
            // Parameters: control type, width, height, left position, top position (all in points).
            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton, // ActiveX type
                100,   // Width in points
                50,    // Height in points
                150,   // Left offset from the page margin
                200);  // Top offset from the page margin
```

`InsertForms2OleControl` creates an OLE object that Word treats as an ActiveX control. The coordinate system uses points (1 point = 1/72 inch), which matches Word’s layout engine.

## Step 4: Set the button’s caption and optional properties

```csharp
            // Set the text that appears on the button.
            commandBtn.Caption = "Submit";

            // Optional: assign a macro name that Word will call when the button is clicked.
            // commandBtn.OnAction = "MyMacroName";
```

Setting the `Caption` property is the most common way to label the button. If you need the button to execute a VBA macro, assign the macro name to `OnAction`. This tutorial focuses on the visual part; macro integration is covered in the “Next steps” section.

## Step 5: Save the document

```csharp
            // Define the output path – change this to a folder that exists on your machine.
            string outputPath = @"ActiveX_CommandButton.docx";

            // Save the document with the embedded ActiveX control.
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

When you run the program, you’ll see a console message confirming that `ActiveX_CommandButton.docx` has been written to disk.

### Full source code (copy‑paste ready)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Forms2OleControl commandBtn = builder.InsertForms2OleControl(
                Forms2OleControlType.CommandButton,
                100, 50, 150, 200);

            commandBtn.Caption = "Submit";
            // commandBtn.OnAction = "MyMacroName";

            string outputPath = @"ActiveX_CommandButton.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Running the snippet produces a Word file that contains a clickable **ActiveX command button**. Open the file in Microsoft Word, switch to **Design Mode** (Developer tab → Design Mode), and you’ll see the button rendered exactly where you placed it.

## Step 6: Verify the result

1. Open `ActiveX_CommandButton.docx` in Microsoft Word.
2. Enable the **Developer** tab if it isn’t visible (`File → Options → Customize Ribbon → check Developer`).
3. Click **Design Mode**. The button should appear with the label “Submit”.
4. If you added an `OnAction` macro, click the button while Design Mode is off to trigger the macro.

If the button does not show, ensure that Word’s security settings allow ActiveX controls (`File → Options → Trust Center → Trust Center Settings → ActiveX Settings`).

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Can I insert other ActiveX types?** | Yes. `Forms2OleControlType` enum includes `CheckBox`, `OptionButton`, `ComboBox`, etc. Replace `CommandButton` with the desired enum value


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}