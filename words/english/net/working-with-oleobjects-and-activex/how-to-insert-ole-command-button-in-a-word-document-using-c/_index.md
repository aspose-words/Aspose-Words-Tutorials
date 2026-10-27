---
category: general
date: 2026-10-07
description: Learn how to insert OLE command button in a Word document with Aspose.Words
  C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert OLE command button
- Aspose.Words OLE control
- C# DocumentBuilder InsertForms2OleControl
- OleControlType CommandButton
- Word OLE command button
language: en
lastmod: 2026-10-07
og_description: Insert OLE command button in a Word document using C#. Follow this
  concise tutorial to add, configure, and save a functional CommandButton with Aspose.Words.
og_image_alt: Insert OLE command button example in Word document
og_title: Insert OLE command button in Word with C# – complete Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  headline: How to insert OLE command button in a Word document using C#
  type: TechArticle
- description: Learn how to insert OLE command button in a Word document with Aspose.Words
    C#. Step‑by‑step guide covering DocumentBuilder, properties, and saving the file.
  name: How to insert OLE command button in a Word document using C#
  steps:
  - name: Why this works
    text: '* `DocumentBuilder` is the primary API for building Word documents programmatically.
      * `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**,
      which is the legacy Word form technology that supports command buttons, check
      boxes, etc. * The `OleControlType.CommandButton` enum va'
  - name: 1. What if the button does not appear where I expect?
    text: '* Word uses points, not pixels. Convert screen pixels to points (`points
      = pixels * 72 / DPI`). * Ensure the rectangle does not intersect page margins;
      otherwise Word may shift the control.'
  - name: 2. Can I insert the button into an existing document?
    text: Yes. Load the document with `new Document("Existing.docx")` and use the
      same `DocumentBuilder` workflow. Just remember to move the builder’s cursor
      (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.)
      before calling `InsertForms2OleControl`.
  - name: 3. How do I attach a macro to the button?
    text: 'Aspose.Words does not create VBA code, but you can embed a macro after
      the document is generated:'
  - name: 4. Does this work with .NET Core on Linux?
    text: The OLE control is a Windows‑specific feature because it relies on COM.
      On Linux the button will be inserted, but it will appear as a static picture
      without interactive behavior. For cross‑platform interactive forms, consider
      using content controls (`StructuredDocumentTag`) instead.
  - name: 5. What if I need a different size or multiple buttons?
    text: Create additional `Rectangle` objects with unique coordinates and repeat
      the `InsertForms2OleControl` call. Each button can have its own `Caption` and
      `Name`.
  type: HowTo
tags:
- Aspose.Words
- C#
- OLE
- Word automation
title: How to insert OLE command button in a Word document using C#
url: /net/working-with-oleobjects-and-activex/how-to-insert-ole-command-button-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to insert OLE command button in a Word document using C#

If you need to **insert OLE command button** into a Word file programmatically, this guide shows you exactly how to do it with Aspose.Words for .NET. Whether you’re building a form‑filled report or automating a template that requires user interaction, the steps below give you a complete, runnable solution.

You’ll learn how to create a blank document, use the `DocumentBuilder` to place a `Forms2OleControl`, set the button’s caption and name, and finally save the `.docx`. No external tools are required beyond the Aspose.Words library.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later (the code also works with .NET Framework 4.7+)
* A valid Aspose.Words for .NET license or a free evaluation key
* Visual Studio 2022 (or any C# IDE you prefer)
* Basic familiarity with C# syntax and Word OLE concepts

> **Pro tip:** If you’re using the free evaluation, the generated document will contain a small watermark. A licensed version removes it automatically.

## Step 1: Install Aspose.Words

Add the Aspose.Words package to your project via NuGet:

```bash
dotnet add package Aspose.Words
```

The package includes the `Aspose.Words.Drawing` and `Aspose.Words.Drawing.Ole` namespaces required for OLE controls.

## Step 2: Insert OLE command button with DocumentBuilder

The core of the tutorial is the `InsertForms2OleControl` method. It creates a **Forms2 OLE CommandButton** at a specific location and size.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System.Drawing;

// Create a new blank document and a DocumentBuilder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Define the rectangle where the button will appear (x, y, width, height)
// Values are in points (1 point = 1/72 inch)
Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

// Insert the Forms2 OLE CommandButton control
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,   // <-- OleControlType CommandButton (secondary keyword)
    buttonRect);

// Set the button's caption and name properties
commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";
```

### Why this works

* `DocumentBuilder` is the primary API for building Word documents programmatically.  
* `InsertForms2OleControl` tells Aspose.Words to embed a **Forms2 OLE control**, which is the legacy Word form technology that supports command buttons, check boxes, etc.  
* The `OleControlType.CommandButton` enum value specifies that the inserted control is a **command button**—the exact type you asked for when you wanted to **insert OLE command button**.  
* The `Rectangle` determines the visual placement. Adjust the X/Y coordinates or the width/height to match your layout.

## Step 3: Save the document

After configuring the button, write the document to disk. You can choose any format supported by Aspose.Words (`.docx`, `.pdf`, `.odt`, …). For this tutorial we’ll save as a Word document.

```csharp
// Choose a folder you have write access to
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");

// Save the document containing the button
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

When you open `CommandButton.docx` in Microsoft Word, you’ll see a clickable button labeled **Click Me**. Pressing it in Word triggers the default “Run Macro” dialog because the button is an OLE form control; you can later attach a macro or VBA code if needed.

## Step 4: Verify the result (expected output)

Open the generated file:

1. The button appears at the coordinates you specified (roughly 1.4 in from the left and top of the page).  
2. The caption reads **Click Me**.  
3. The name property (`cmdSubmit`) is visible in Word’s **Developer → Properties** pane, which is useful when you need to reference the control from VBA.

![Insert OLE command button example in Word document](insert-ole-button.png)

*Image alt text*: **Insert OLE command button example in Word document** (includes primary keyword for accessibility and SEO).

## Edge Cases & Common Questions

### 1. What if the button does not appear where I expect?

* Word uses points, not pixels. Convert screen pixels to points (`points = pixels * 72 / DPI`).  
* Ensure the rectangle does not intersect page margins; otherwise Word may shift the control.

### 2. Can I insert the button into an existing document?

Yes. Load the document with `new Document("Existing.docx")` and use the same `DocumentBuilder` workflow. Just remember to move the builder’s cursor (`builder.MoveToDocumentEnd()`, `builder.MoveToBookmark("myBookmark")`, etc.) before calling `InsertForms2OleControl`.

### 3. How do I attach a macro to the button?

Aspose.Words does not create VBA code, but you can embed a macro after the document is generated:

```csharp
// Load the generated document
Document doc = new Document(outputPath);

// Add a VBA macro module (requires Aspose.Words licensing)
doc.VbaProject.Modules.Add("Module1", "Sub cmdSubmit_Click()\n MsgBox \"Button clicked!\"\nEnd Sub");

// Save again
doc.Save(outputPath);
```

### 4. Does this work with .NET Core on Linux?

The OLE control is a Windows‑specific feature because it relies on COM. On Linux the button will be inserted, but it will appear as a static picture without interactive behavior. For cross‑platform interactive forms, consider using content controls (`StructuredDocumentTag`) instead.

### 5. What if I need a different size or multiple buttons?

Create additional `Rectangle` objects with unique coordinates and repeat the `InsertForms2OleControl` call. Each button can have its own `Caption` and `Name`.

## Full Working Example

Below is the complete program you can copy‑paste into a console application. It includes all necessary `using` directives, error handling, and comments.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

namespace OleCommandButtonDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document
                Document document = new Document();
                DocumentBuilder builder = new DocumentBuilder(document);

                // 2️⃣ Define button rectangle (x, y, width, height) in points
                Rectangle buttonRect = new Rectangle(100, 100, 120, 30);

                // 3️⃣ Insert the Forms2 OLE CommandButton control
                Forms2OleControl commandButton = builder.InsertForms2OleControl(
                    OleControlType.CommandButton,
                    buttonRect);

                // 4️⃣ Set visual properties
                commandButton.OleFormat.ObjectProps["Caption"] = "Click Me";
                commandButton.OleFormat.ObjectProps["Name"] = "cmdSubmit";

                // 5️⃣ Save the document
                string outputPath = Path.Combine(
                    Environment.CurrentDirectory,
                    "CommandButton.docx");

                document.Save(outputPath);
                Console.WriteLine($"Document saved successfully: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Error: {ex.Message}");
            }
        }
    }
}
```

Run the program, open the generated `CommandButton.docx`, and you’ll see the **Click Me** button ready for further customization.

## Conclusion

You now know how to **insert OLE command button** into a Word document using C# and Aspose.Words. The tutorial covered:

* Installing the Aspose.Words package  
* Using `DocumentBuilder.InsertForms2OleControl` with `OleControlType.CommandButton`  
* Setting button properties (`Caption`, `Name`)  
* Saving and verifying the output  

From here you can explore related topics such as **Aspose.Words OLE control** for check boxes, combo boxes, or embedding entire Excel worksheets. You might also experiment with **Word OLE command button** automation in larger templates, or replace OLE controls with modern **content controls** for better cross‑platform support.

Feel free to adapt the rectangle values, add multiple buttons, or attach VBA macros to meet your application’s needs. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Ole Object In Word Document](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object/)
- [Insert Ole Object In Word Document As Icon](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon/)
- [Insert Ole Object In Word With Ole Package](/words/english/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}