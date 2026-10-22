---
category: general
date: 2026-09-11
description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
  This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
  usage, and sizing.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: en
lastmod: 2026-09-11
og_description: Create forms2olecontrol in code with Aspose.Words. Follow this guide
  to insert an ActiveX command button, set its class name, and adjust its size.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Create forms2olecontrol in code – complete Aspose.Words guide
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: How to create forms2olecontrol in code with Aspose.Words
url: /java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create forms2olecontrol in code with Aspose.Words

If you need to **create forms2olecontrol in code**, this guide shows you exactly how to do it using the Aspose.Words .NET API. Whether you are automating a template that requires an ActiveX command button or you simply want to enrich a Word document programmatically, the steps below cover everything from inserting the control to configuring its appearance.

In this tutorial you’ll learn how to use the **Aspose.Words DocumentBuilder** to insert an **ActiveX command button**, set its class with the **setOleClassName method**, and adjust its **Forms2OleControl size**. No external tools are required—just a .NET development environment and the Aspose.Words library.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 or later installed (the code also works with .NET Framework 4.7+)
* A recent version of the Aspose.Words for .NET NuGet package
* Basic familiarity with C# and the concept of ActiveX controls in Word documents

If any of these are missing, install the NuGet package with:

```bash
dotnet add package Aspose.Words
```

## What this tutorial covers

* Creating a `DocumentBuilder` instance
* Inserting a `Forms2OleControl` (the underlying object for an ActiveX command button)
* Assigning the correct class name with `setOleClassName`
* Setting the visual width and height using the **Forms2OleControl size** properties
* Saving the document and verifying the result

By the end of the guide you will have a fully functional Word file containing a clickable button that you can further customize or bind to VBA macros.

---

## How to create forms2olecontrol in code – step‑by‑step

### Step 1: Initialise the DocumentBuilder

The `DocumentBuilder` class is the entry point for most document‑generation tasks in Aspose.Words. It gives you methods to add text, images, tables, and, importantly for this tutorial, OLE controls.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`DocumentBuilder` maintains the current cursor position inside the document. By creating it early, you ensure that any subsequent insertion—such as the **ActiveX command button**—appears exactly where you want it.

### Step 2: Insert the Forms2OleControl

The `insertForms2OleControl` method returns a `Forms2OleControl` object. This object represents the OLE control placeholder that Word will render as an ActiveX button.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Why this matters:**  
Without this call you cannot manipulate the control’s properties. The returned `Forms2OleControl` gives you full access to the **setOleClassName method**, size attributes, and other OLE‑specific settings.

### Step 3: Specify the ActiveX class with setOleClassName

Word needs to know which type of ActiveX control to render. The class name for a standard command button is `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Why this matters:**  
The `setOleClassName` method is the bridge between the generic OLE placeholder and the concrete **ActiveX command button**. Using the wrong class name results in a blank object or a runtime error when the document is opened.

### Step 4: Adjust the Forms2OleControl size

A button that is too small or too large looks unprofessional. You can control its dimensions with `setWidth` and `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Why this matters:**  
These properties constitute the **Forms2OleControl size**. They affect how the button appears in the Word UI and ensure that any attached macro has enough clickable area.

### Step 5: Save the document and test

After configuring the control, save the document to a location of your choice.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Open `ActiveXButton.docx` in Microsoft Word. You should see a button labeled “CommandButton1” (the default caption). Clicking it will do nothing unless you add a VBA macro, but the control itself is fully functional.

**Expected output:**  

![Word document with an inserted ActiveX command button](/images/activeX-button.png "Screenshot of a Word document showing a newly created ActiveX command button inserted via code")

*The image alt text contains the primary keyword for accessibility and SEO.*

---

## Understanding the ActiveX Forms2OleControl class

The `Forms2OleControl` class wraps the low‑level OLE infrastructure that Word uses for ActiveX elements. It inherits from `Shape`, which means you can also apply typical shape formatting (e.g., borders, rotation) if needed.

* **ActiveX command button** – The most common use case; you can bind it to a macro via Word's developer tools.
* **setOleClassName method** – Determines which COM class Word loads; other valid values include `"Forms.TextBox.1"` and `"Forms.ComboBox.1"`.
* **Forms2OleControl size** – Controlled through `SetWidth`/`SetHeight`. These methods accept points (1 pt = 1/72 in).

### When to use Forms2OleControl vs. Content Controls

If you only need simple data entry (e.g., a plain text field), Word’s built‑in content controls are lighter weight. Use `Forms2OleControl` when you require full ActiveX functionality such as event handling or custom VBA interaction.

---

## Setting additional properties (optional)

While the core steps are enough to **create forms2olecontrol in code**, you often want to fine‑tune the button’s appearance or behavior.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Why this matters:**  
`SetOleData` lets you write arbitrary property values directly into the OLE stream. This is the most flexible way to customize an **ActiveX command button** without resorting to VBA.

---

## Common pitfalls and troubleshooting

| Symptom | Likely cause | Fix |
|--------|--------------|-----|
| Button appears as a gray box | Incorrect class name passed to `setOleClassName` | Verify the string is exactly `"Forms.CommandButton.1"` (case‑sensitive) |
| Size does not change | Width/Height set before inserting the control | Always call `SetWidth`/`SetHeight` **after** `InsertForms2OleControl` |
| Document throws “OLE object not found” on open | Missing Aspose.Words license (evaluation version may limit OLE) | Apply a valid license or use the free trial with full OLE support |
| Button caption stays “CommandButton1” | `SetOleData` not used or macro not reading the property | Use a VBA macro to read the `"Caption"` property or set the caption via the Word UI |

---

## Full, runnable example

Below is a complete console application that you can copy, paste, and run. It demonstrates everything covered in this tutorial.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Explanation of each section**

* **Using directives** – Pull in the Aspose.Words namespace required for `Document`, `DocumentBuilder`, and `Forms2OleControl`.
* **Document creation** – Instantiates an empty Word file.
* **InsertForms2OleControl** – Places the OLE control at the builder’s current cursor.
* **SetOleClassName** – Tells Word the control is a **ActiveX command button**.
* **SetWidth / SetHeight** – Adjust the **Forms2OleControl size** for a professional look.
* **SetOleData (optional)** – Demonstrates how to write extra properties like a caption.
* **Save** – Writes the final `.docx` file to disk.

Run the program (`dotnet run`) and open `ActiveXButton.docx`. You should see a button that you can later link to a macro.

---

## Conclusion

You now know how to **create forms2olecontrol in code** using Aspose.Words, from initializing the `DocumentBuilder` to configuring the **ActiveX command button** with `setOleClassName` and controlling its **Forms2OleControl size**. This approach lets you automate complex Word documents, embed interactive UI elements, and keep all logic inside


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}