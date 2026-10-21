---
category: general
date: 2026-08-04
description: Create word document programmatically using C#. Learn how to programmatically
  add command button with Aspose.Words in just a few steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- programmatically add command button
- Aspose.Words InsertForms2OleControl
- C# Word automation
- OLE command button in Word
language: en
lastmod: 2026-08-04
og_description: Create word document programmatically with Aspose.Words. This guide
  shows how to programmatically add command button, configure it, and save the file.
og_image_alt: Screenshot of a Word document that contains a Command Button added programmatically
og_title: Create word document programmatically – full C# tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  headline: Create word document programmatically – step‑by‑step guide
  type: TechArticle
- description: Create word document programmatically using C#. Learn how to programmatically
    add command button with Aspose.Words in just a few steps.
  name: Create word document programmatically – step‑by‑step guide
  steps:
  - name: The `ControlType` enum value (here `CommandButton`).
    text: The `ControlType` enum value (here `CommandButton`).
  - name: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
    text: A `RectangleF` that defines the X‑Y position and the width‑height of the
      control (measured in points, where 72 pt = 1 inch).
  - name: Optionally, additional OLE properties (not needed for the basic button).
    text: Optionally, additional OLE properties (not needed for the basic button).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Create word document programmatically – step‑by‑step guide
url: /net/working-with-form-fields/create-word-document-programmatically-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create word document programmatically – complete C# tutorial

If you need to **create word document programmatically**, this guide shows you exactly how to do it with Aspose.Words for .NET. In just a few lines of C# you can generate a blank `.docx` file, **programmatically add command button** controls, set their properties, and save the result.  

The steps below cover everything from project setup to handling edge cases, so you can copy the code into your own application and run it without modifications.

## What you’ll achieve

By the end of this tutorial you will be able to:

* Initialise a new Word document entirely in memory.  
* **Programmatically add command button** OLE controls at any location and size.  
* Configure the button’s caption, internal name, and other OLE properties.  
* Save the generated document to disk or a stream for further processing.

### Prerequisites

* .NET 6.0 or later (the code also works with .NET Framework 4.6+).  
* A valid Aspose.Words for .NET license (or a free evaluation).  
* Basic familiarity with C# and Visual Studio (or any IDE of your choice).  

> **Pro tip:** If you run the sample without a license, Aspose.Words will add a small evaluation watermark to the first page.

## Step 1: Set up the project and import required namespaces

Create a new Console App (or integrate into an existing service) and add the Aspose.Words NuGet package:

```bash
dotnet add package Aspose.Words
```

Then include the essential namespaces at the top of your `.cs` file:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
```

These imports give you access to `Document`, `DocumentBuilder`, `Forms2OleControl`, and the `RectangleF` struct used for positioning.

## Step 2: Initialize a fresh Word document

The first operation in any **create word document programmatically** workflow is to instantiate a `Document` object. This object lives only in memory until you explicitly save it.

```csharp
// Step 2: Create a new blank document
Document doc = new Document();

// Attach a DocumentBuilder to simplify content insertion
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` acts like a cursor that tracks where the next element will be placed. Using it keeps the code concise and mirrors the way you would type directly into Word.

## Step 3: Insert a command button OLE control

Aspose.Words provides the `InsertForms2OleControl` method to embed OLE objects such as command buttons, check boxes, or combo boxes. The method requires three arguments:

1. The `ControlType` enum value (here `CommandButton`).  
2. A `RectangleF` that defines the X‑Y position and the width‑height of the control (measured in points, where 72 pt = 1 inch).  
3. Optionally, additional OLE properties (not needed for the basic button).

```csharp
// Step 3: Programmatically add command button at (100,100) with size 120×30 points
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Why this works:** `InsertForms2OleControl` creates an OLE container in the document and returns a `Forms2OleControl` wrapper. The wrapper lets you manipulate the underlying OLE object (the actual button) without dealing with low‑level COM interop.

## Step 4: Configure the button’s caption and internal name

After insertion, you typically want to give the button a user‑visible label and an internal identifier that your macro or add‑in can reference later.

```csharp
// Step 4: Set caption and name of the button
commandButton.OleFormat.OleObject.Caption = "Click Me";
commandButton.OleFormat.OleObject.Name = "cmdClickMe";
```

* `Caption` is the text displayed on the button in the Word UI.  
* `Name` is the programmatic identifier used by VBA or external automation scripts.

### Optional: Assign a macro to the button

If you plan to run a VBA macro when the button is clicked, you can attach the macro name:

```csharp
commandButton.OleFormat.OleObject.MacroName = "MyMacro";
```

> **Edge case:** When the target document will be opened on a machine without the macro, Word will display a security warning. Always sign your macros or inform users about the required settings.

## Step 5: Save the document

You can write the file to disk, a `MemoryStream`, or directly to a response object in a web API. The simplest approach for a console demo is to save to a local folder:

```csharp
// Step 5: Persist the document containing the button
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

The resulting `.docx` opens in Microsoft Word with a functional command button that shows “Click Me”. Clicking the button will trigger the assigned macro (if any) or simply display a default message.

## Full working example

Copy the following program into `Program.cs` and run it. It demonstrates the entire **create word document programmatically** flow, including error handling.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Initialise a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a CommandButton OLE control
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                new RectangleF(100, 100, 120, 30));

            // 3️⃣ Set button properties
            commandButton.OleFormat.OleObject.Caption = "Click Me";
            commandButton.OleFormat.OleObject.Name = "cmdClickMe";
            // Optional macro assignment (uncomment if needed)
            // commandButton.OleFormat.OleObject.MacroName = "MyMacro";

            // 4️⃣ Save the document
            string outputPath = @"C:\Temp\CommandButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document created successfully at {outputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ Error: {ex.Message}");
        }
    }
}
```

**Expected result:** Opening `CommandButton.docx` in Word shows a button labeled “Click Me”. Hovering over the button reveals the name `cmdClickMe` in the properties pane.

## Common questions and troubleshooting

| Question | Answer |
|----------|--------|
| *Can I add the button to an existing document?* | Yes. Load the file with `new Document("Existing.docx")`, then use the same `InsertForms2OleControl` call. |
| *What units does `RectangleF` use?* | Points (1 inch = 72 pt). Adjust values to position the button precisely. |
| *Will the button work on Word for Mac?* | OLE controls are supported on Windows Word only. On Mac the button appears as a static image. |
| *Do I need a license for production use?* | A commercial license removes evaluation watermarks and unlocks full functionality. |
| *How do I change the button’s size after insertion?* | Modify `commandButton.Width` and `commandButton.Height` or re‑insert with a new `RectangleF`. |

## Extending the solution

Now that you know how to **programmatically add command button** controls, you can explore these related topics:

* **Insert other form controls** – use `ControlType.CheckBox`, `ControlType.OptionButton`, etc. (covers secondary keyword *Aspose.Words InsertForms2OleControl*).  
* **Populate the document with dynamic data** – merge data from a database into tables or mail‑merge fields.  
* **Export to PDF** – after adding the button, call `doc.Save("output.pdf", SaveFormat.Pdf)` to produce a PDF version (relevant to *C# Word automation*).  

## Conclusion

You now have a complete, production‑ready pattern for **create word document programmatically** and **programmatically add command button** using Aspose.Words for .NET. The tutorial covered project setup, document initialization, OLE button insertion, property configuration, and saving the file. Feel free to adapt the code to insert other form controls, attach macros, or integrate the logic into web services or background jobs.

Happy coding, and enjoy automating Word documents!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}