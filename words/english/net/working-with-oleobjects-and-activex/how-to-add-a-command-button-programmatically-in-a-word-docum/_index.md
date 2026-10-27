---
category: general
date: 2026-10-13
description: Learn how to add a command button programmatically using Aspose.Words.
  This guide also shows how to create a Word document button with full C# code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: en
lastmod: 2026-10-13
og_description: Add a command button programmatically to a Word document using Aspose.Words.
  Follow this complete tutorial to create a Word document button with C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Add a command button programmatically to a Word document – step‑by‑step
  guide
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: How to add a command button programmatically in a Word document
url: /net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to add a command button programmatically in a Word document  

If you need to **add a command button programmatically**, Aspose.Words provides a clean API that lets you embed OLE form controls directly into a .docx file. This tutorial walks you through every step required to **create a Word document button** that behaves like a regular form button when the document is opened in Microsoft Word.  

You will learn how to set up the development environment, insert the button, configure its properties, and verify the result. No external utilities are required—just a .NET project and the Aspose.Words for .NET library.  

## Prerequisites  

Before you start, make sure you have:  

* .NET 6.0 SDK or later installed.  
* A recent version of Aspose.Words for .NET (the examples use 23.12, but any 22.x+ release works).  
* An IDE such as Visual Studio 2022 or Visual Studio Code.  

The code runs on Windows, macOS, and Linux because Aspose.Words is platform‑independent.  

## Step 1: Set up the project and reference Aspose.Words  

1. Create a new console project:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Add the Aspose.Words NuGet package:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Open **Program.cs** and replace its content with the scaffold shown in the next steps.  

Setting up the project this way ensures that the compiler can locate the `Aspose.Words` and `Aspose.Words.Drawing.Forms` namespaces required for form controls.  

## Step 2: Initialize a blank document and a DocumentBuilder  

The `Document` class represents the entire Word file, while `DocumentBuilder` provides a fluent API for adding content.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Why this step matters* – Without a `DocumentBuilder` you cannot position the button precisely on the page. The builder also respects the current cursor location, making it easy to insert multiple controls later.  

## Step 3: Insert the command button OLE control  

Aspose.Words treats a command button as an OLE control of type `ControlType.CommandButton`. You define its location and size with a `RectangleF` measured in points (1 point = 1/72 inch).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Key points**  

* The rectangle’s origin (X, Y) is relative to the page’s top‑left corner.  
* Changing the `Width` or `Height` modifies the visual size of the button.  
* `InsertForms2OleControl` returns a `Forms2OleControl` object that you can further configure.  

## Step 4: Configure the button’s name and caption  

The **name** is used by Word’s macro engine to identify the control, while the **caption** is the text the user sees.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

If you plan to add VBA macros later, use a descriptive name because Word’s macro recorder references this property.  

## Step 5: (Optional) Save the document and verify the result  

Saving the file lets you open it in Microsoft Word to confirm that the button appears and works.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

When you open *CommandButtonDemo.docx* in Word, you should see a button labelled **Submit** positioned roughly 1.4 inches from the left margin and 2.1 inches from the top of the page. Clicking the button does nothing by default because no macro is attached, but the visual control is fully functional.  

## Step 6: Edge cases and common pitfalls  

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Button overlaps existing text** | The rectangle may intersect with a paragraph, causing layout issues. | Insert the button after calling `builder.Writeln()` to move the cursor to a new line, or adjust the `Y` coordinate. |
| **Document opens with a warning** | Some Word versions flag OLE controls that lack a linked program. | Ensure the control type is `CommandButton`; Word treats it as a standard form element and does not require an external program. |
| **Running on Linux with headless environment** | Word cannot be launched to test the UI, but the file remains valid. | Use a unit test that reads the control’s properties (`commandButton.Name`, `commandButton.Caption`) to verify they were set correctly. |
| **Multiple buttons needed** | Re‑using the same `DocumentBuilder` without moving the cursor adds the button on top of the previous one. | Call `builder.MoveToDocumentEnd()` or adjust the rectangle’s `Y` value before each insertion. |

Addressing these edge cases early saves time when scaling the solution to full forms with dozens of controls.  

## Step 7: Full, runnable example  

Below is a self‑contained program that you can copy, paste, and run without modification (aside from the NuGet restore).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Expected output**  

Running the program prints a path similar to:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Opening the generated *CommandButtonDemo.docx* shows a single **Submit** button placed at the coordinates defined in the code. No additional UI elements appear, confirming that the **add command button programmatically** workflow succeeded.  

## Conclusion  

You now know how to **add a command button programmatically** to a Word document using Aspose.Words, and you also understand how to **create a Word document button** that can later be wired to VBA macros or external automation tools. The process consists of initializing a document, inserting an OLE `CommandButton` control, configuring its properties, and saving the file.  

From here you might:  

* Add more controls (checkboxes, text fields) by repeating step 3 with different `ControlType` values.  
* Attach VBA macros to the button to perform actions like saving a form or sending an email.  
* Generate entire forms dynamically by looping over a data‑driven collection of field definitions.  

Experiment with the rectangle coordinates and the button’s caption to match your UI design. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}