---
category: general
date: 2026-08-17
description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
  Learn how to add form controls to a Word document programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: en
lastmod: 2026-08-17
og_description: Insert OleControlType.CommandButton example in Word with Aspose.Words.
  Follow this guide to add form controls to a Word document.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Insert OleControlType.CommandButton example in Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Insert OleControlType.CommandButton example in Word
url: /net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert OleControlType.CommandButton example in Word

If you need to **insert OleControlType.CommandButton example** into a Word file, this guide shows you how. You’ll learn **how to add form controls to a Word document** using Aspose.Words, with a complete, runnable C# program.

Form controls such as ActiveX buttons let you build interactive Word templates—useful for contracts, questionnaires, or internal tools. The steps below cover everything from project setup to verifying the button appears correctly in the saved `.docx` file.

## Prerequisites

Before you start, make sure you have:

- .NET 6.0 SDK or later installed  
- Visual Studio 2022 (or any C# IDE)  
- An Aspose.Words for .NET license or a free temporary license  
- Basic familiarity with C# and Word file concepts  

> **Pro tip:** If you’re using the free trial, place the license file in the same folder as the executable and load it at the start of `Main`.

## Step 1: Create a new console project and add Aspose.Words

Open a terminal and run:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

This creates a clean project and pulls the latest Aspose.Words package, which provides the `Document`, `DocumentBuilder`, and `InsertForms2OleControl` APIs needed for the **insert OleControlType.CommandButton example**.

## Step 2: Write the full program

Create or replace `Program.cs` with the following code. It contains all required `using` directives, license loading, and the four‑step workflow shown in the original snippet.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Why each line matters

* **License loading** – ensures you’re not limited by evaluation restrictions.  
* **`Document doc = new Document();`** – creates the container for all Word content; this is the foundation of the **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – provides a fluent API to add text, images, and controls.  
* **`InsertForms2OleControl`** – the core method that implements **how to add form controls to a Word document**. The `OleControlType.CommandButton` enum value tells Aspose.Words to create an ActiveX button.  
* **`new Rectangle(100, 100, 80, 30)`** – positions the button 100 pts from the left and top margins, with a width of 80 pts and height of 30 pts. Adjust these numbers to fit your layout.  
* **`doc.Save`** – writes the .docx file to disk; the file now contains the embedded button.

## Step 3: Build and run the program

From the project folder, execute:

```bash
dotnet run
```

You should see the console message:

```
Document saved to ActiveXButton.docx
```

Open `ActiveXButton.docx` in Microsoft Word. You’ll see a button labeled **ClickMe** positioned roughly in the middle of the page. Clicking the button triggers the default ActiveX behavior (which is typically a no‑op unless you attach a macro).

![insert olecontroltype.commandbutton example](/images/activex-button.png "ActiveX CommandButton inserted into a Word document")

*Image alt text:* insert olecontroltype.commandbutton example – an ActiveX CommandButton displayed in a Word document.

## Step 4: Customizing the button (optional)

The basic **insert OleControlType.CommandButton example** creates a default button. You can modify its caption, font, or even attach a macro by editing the underlying OLE object. Below is a concise way to change the button’s caption after insertion:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Note:** Direct manipulation of OLE properties requires understanding of the underlying COM interface. For most scenarios, the default caption is sufficient.

## Step 5: Common pitfalls and how to avoid them

| Issue | Why it happens | Fix |
|-------|----------------|-----|
| The button does not appear in Word | The document was saved as `.docx` but opened in a viewer that strips OLE controls (e.g., Google Docs). | Open the file in Microsoft Word or Word Online with editing rights. |
| Runtime error `ArgumentOutOfRangeException` | The `Rectangle` coordinates are outside the page margins. | Use values within the page size (e.g., 0‑500 for A4). |
| License exception | A trial license expires after 30 days. | Load a valid license file or request an extended trial from Aspose. |

## Step 6: How this example fits into larger automation projects

When you need to **how to add form controls to Word document** at scale—such as generating hundreds of contract templates—wrap the insertion logic in a reusable method:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

You can then call `AddCommandButton` inside loops that process data rows, ensuring each generated document contains a uniquely named button (e.g., `Approve_001`, `Approve_002`).

## Conclusion

You now have a complete **insert OleControlType.CommandButton example** that demonstrates **how to add form controls to a Word document** using Aspose.Words for .NET. The tutorial covered project setup, full source code, customization tips, and common troubleshooting steps. 

From here you might explore:

- Adding other control types such as **CheckBox** or **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Binding the button to a VBA macro for richer interactivity.  
- Generating PDFs from the same document while preserving the form fields.

Experiment with different sizes, positions, and control names to fit your specific use case. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Combo Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}