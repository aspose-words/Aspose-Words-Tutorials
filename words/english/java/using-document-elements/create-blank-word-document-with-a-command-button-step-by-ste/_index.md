---
category: general
date: 2026-08-04
description: Create blank word document and insert command button using Aspose.Words.
  Learn to set button size and add clickable button in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: en
lastmod: 2026-08-04
og_description: Create blank word document with Aspose.Words and insert a command
  button. This guide shows how to set button size, add clickable button, and save
  the file.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Create blank word document and add a command button – full C# tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Create blank word document with a command button – step‑by‑step guide
url: /java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank word document with a command button – step‑by‑step guide

If you need to **create blank word document** that contains an interactive button, this tutorial shows you exactly how to do it with Aspose.Words for .NET. You’ll learn to **insert command button**, adjust its appearance, and make it clickable—all in a few lines of C#.

The guide covers everything from project setup to saving the final file, so you can copy‑paste the complete solution into your own application. Along the way we’ll also explain how to **add clickable button**, **set button size**, and **create command button** programmatically.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed.
* Visual Studio 2022 (or any IDE that supports .NET).
* Aspose.Words for .NET NuGet package (`Aspose.Words` version 23.12 or newer).
* Basic familiarity with C# and object‑oriented programming.

No additional Office interop assemblies are required because Aspose.Words works completely independently of Microsoft Word.

## Step 1: Set up the .NET project

Create a console application that will host the Word automation code.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

This command creates a new folder `WordButtonDemo` with a ready‑to‑run `Program.cs` and adds the Aspose.Words library.

## Step 2: Create blank word document

The first operation is to **create blank word document**. Aspose.Words provides a `Document` class that represents an empty Word file out of the box.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Creating a blank document gives you a clean canvas on which you can add paragraphs, tables, or, in this case, an OLE command button.

## Step 3: Initialize DocumentBuilder

`DocumentBuilder` is the helper that lets you insert content into the document. You need to attach it to the document you just created.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder maintains the current cursor position, so any subsequent insertion happens exactly where you want it.

## Step 4: Insert command button

Now we **insert command button** (an OLE `Forms2OleControl`) into the document. The method `InsertForms2OleControl` requires three arguments:

1. The ProgID of the OLE control – `"CommandButton"` for a standard button.
2. A `Rectangle` that defines the **set button size** and position.
3. The caption that appears on the button.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

When the document is opened in Word, the button behaves like any native form control—you can click it, and Word will fire the associated macro (if one exists). This satisfies the **add clickable button** requirement.

### Why use Forms2OleControl?

`Forms2OleControl` embeds an OLE object directly into the DOCX file, preserving the control’s properties without needing the Word Interop assembly. It’s the most reliable way to **create command button** that works across Word versions.

## Step 5: Customize the button (optional)

You might want to **set button size** more precisely or change additional properties such as the font or background color. Aspose.Words exposes the underlying OLE object, allowing further tweaks.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

If you need a different size, simply adjust the `Rectangle` values in Step 4. The coordinates are measured in points (1 pt = 1/72 inch), so `120` corresponds to roughly 1.67 inches wide.

## Step 6: Save the document

Finally, write the document to disk. The resulting file contains a **blank word document** with a fully functional command button.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

When you open `CommandButtonDemo.docx` in Microsoft Word, you’ll see a button labeled “Click Me”. Clicking the button will display the default macro dialog unless you attach a custom macro.

## Complete source code

Below is the full program you can copy into `Program.cs`. It includes all the steps described above and compiles without modifications.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Expected result

Running the program produces `CommandButtonDemo.docx`. Opening the file in Word shows:

* A single page containing a button labeled **Click Me**.
* The button respects the **set button size** (120 × 30 points).
* Clicking the button triggers Word’s default command‑button behavior, confirming that the **add clickable button** operation succeeded.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Does this work with .doc files?** | Yes. Change the file extension in `doc.Save("file.doc")`. The OLE control is stored in the legacy binary format as well. |
| **What if I need multiple buttons?** | Call `InsertForms2OleControl` repeatedly, adjusting the `Rectangle` for each new button to avoid overlap. |
| **Can I attach a macro to the button?** | The button itself does not contain macro code. You must add a VBA macro to the document manually or via the `Document` object’s `Modules` collection. |
| **Is the button visible in PDF export?** | When you export the DOCX to PDF using Aspose.Words, the button is rendered as a static image, not an interactive control. |
| **What versions of Word are supported?** | The OLE command button works in Word 2007 and later, as it follows the standard Forms2.0 specification. |

## Conclusion

You now know how to **create blank word document**, **insert command button**, **add clickable button**, and **set button size** using Aspose.Words for .NET. The complete example demonstrates the **create command button** workflow from start to finish, giving you a solid foundation for more advanced Word automation tasks.

## Next steps

* Explore other OLE controls (e.g., `CheckBox`, `ListBox`) by changing the ProgID in `InsertForms2OleControl`.
* Combine the button with a VBA macro to perform custom actions when the user clicks it.
* Use Aspose.Words’ `DocumentBuilder` to add additional content such as tables, images, or footnotes before inserting the button.
* Experiment with **set button size** values to match your document’s layout requirements.

Happy coding, and enjoy building richer Word documents with interactive controls!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}