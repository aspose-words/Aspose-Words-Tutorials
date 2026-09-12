---
category: general
date: 2026-09-11
description: Learn how to create word document c# and programmatically add a command
  button using Aspose.Words in a few simple steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: en
lastmod: 2026-09-11
og_description: Create word document c# and programmatically add a command button
  with Aspose.Words. Follow this complete guide for a working solution.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Create word document c# – add a command button programmatically
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: How to create word document c# and programmatically add a command button
url: /net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create word document c# and programmatically add a command button

If you need to **create word document c#** and embed an interactive button, this guide shows you exactly how to do it. Using Aspose.Words you can programmatically add a command button in just a few lines of code, eliminating the need for manual UI work in Word.

In this tutorial you’ll learn how to:

* Initialize a blank Word file with C#.
* Insert an ActiveX **CommandButton** control.
* Set the button’s properties such as name and caption.
* Save the document so the button appears when the file is opened in Microsoft Word.

No external tools are required beyond the Aspose.Words for .NET library, and the steps work with .NET 6+ or .NET Framework 4.6.2 and later.

## Prerequisites

Before you start, make sure you have:

| Requirement | Reason |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | Provides the runtime for the C# project. |
| Visual Studio 2022 (or any C# IDE) | Makes it easy to write, build, and run the code. |
| Aspose.Words for .NET NuGet package | Supplies the `Document`, `DocumentBuilder`, and `Forms2OleControl` classes used in the example. |
| Basic knowledge of C# syntax | Allows you to follow the code without additional learning curves. |

You can add the Aspose.Words package via the NuGet console:

```powershell
Install-Package Aspose.Words
```

## Step 1: Set up a new C# console project

Create a console application that will generate the Word file. Open a terminal and run:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

The generated `Program.cs` file will host the code shown in the following steps.

## Step 2: Create a blank document and a DocumentBuilder

The first operation is to instantiate a `Document` object, which represents an empty `.docx` file, and a `DocumentBuilder` that lets you edit the document’s contents.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`Document` is the container for all Word elements (paragraphs, tables, controls). `DocumentBuilder` provides a fluent API to insert objects at the current cursor location without dealing with low‑level node collections.

## Step 3: Insert an ActiveX CommandButton control

Aspose.Words supports inserting legacy ActiveX controls through the `InsertForms2OleControl` method. The method requires the control type and the desired size in points.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**What happens under the hood:**  
Word treats an ActiveX control as an OLE (Object Linking and Embedding) object. The `Forms2OleControl` class wraps the OLE data and exposes properties such as `Name` and `Caption`.

## Step 4: Configure the button’s name and caption

After the control is placed, you can customize its runtime properties. Setting a meaningful `Name` helps you identify the button later, while `Caption` defines the text displayed on the button.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Pro tip:**  
If you plan to handle the button’s click event with VBA, the `Name` becomes the macro name you reference, e.g., `Sub btnSubmit_Click()`.

## Step 5: Save the document to disk

Finally, write the document to a `.docx` file. Choose a folder you have write access to; the example uses a relative path, which resolves to the project’s output directory.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Running the program produces `CommandButton.docx`. Opening the file in Microsoft Word displays a clickable **Submit** button:

![Word document with a Submit command button](/images/command-button.png "Screenshot of a Word document containing a Submit command button created with C#")

*Image alt text (og_image_alt):* `Screenshot of a Word document containing a Submit command button created with C#`

## Verifying the result

1. Launch Word and open `CommandButton.docx`.  
2. You should see a button labeled **Submit** in the document body.  
3. Hovering over the button reveals the name `btnSubmit` in the **Properties** pane (Developer tab → Properties).  

If the button does not appear, ensure that the **Developer** tab is enabled in Word (File → Options → Customize Ribbon → check *Developer*). ActiveX controls are hidden when the tab is disabled.

## Handling common variations and edge cases

| Situation | Recommended adjustment |
|-----------|------------------------|
| **Different button size** | Change the width and height arguments in `InsertForms2OleControl`. For example, `150, 40` creates a larger button. |
| **Multiple buttons** | Call `InsertForms2OleControl` repeatedly, moving the builder’s cursor between calls (`builder.Writeln();`). |
| **Button without ActiveX** | Use `InsertFormField` to add a legacy form field (e.g., a checkbox) if you need compatibility with older Word versions that block ActiveX. |
| **Cross‑platform usage** | ActiveX controls only work on Windows versions of Word. For Mac or web‑based viewers, consider inserting a hyperlink styled as a button instead. |
| **Security warnings** | Word may display a security prompt when opening a document containing ActiveX controls. Signing the document with a trusted certificate reduces this friction. |

## Full, runnable example

Below is the complete program you can copy‑paste into `Program.cs`. It compiles and runs without modification after adding the Aspose.Words NuGet package.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected output in the console:**

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Opening the generated file shows the **Submit** button ready for interaction.

## Conclusion

You now know how to **create word document c#** and **programmatically add command button** controls using Aspose.Words. The process boils down to initializing a `Document`, inserting a `Forms2OleControl`, configuring its properties, and saving the file. From here you can:

* Add more controls (e.g., checkboxes, text fields) by changing `ControlType`.
* Attach VBA macros to the button for custom logic.
* Combine this technique with other Aspose.Words features such as mail merge or template filling.

Experiment with different sizes, captions, and multiple buttons to fit your automation scenario. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}