---
category: general
date: 2026-10-26
description: Learn how to create Word document C# and add an ActiveX button programmatically.
  This step‑by‑step guide covers inserting a command button, hiding it at design time,
  and saving the file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: en
lastmod: 2026-10-26
og_description: Create Word document C# and programmatically add an ActiveX button.
  Follow this complete tutorial to embed a command button that appears only at runtime.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Create a Word document C# with an ActiveX command button – full guide
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: How to create Word document C# with an ActiveX command button
url: /net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create Word document C# with an ActiveX command button

If you need to **create Word document C#** that contains an interactive button, this guide shows you exactly how. By the end of the first two sentences you’ll know the overall approach, and the following steps walk you through every line of code you must write.

You’ll learn how to add an ActiveX button, hide it during design, and make it visible only when the user opens the file. The tutorial also covers common pitfalls such as security warnings and version compatibility, so you can ship reliable documents.

## Prerequisites

Before you start, ensure you have:

* .NET 6.0 or later installed  
* A licensed copy of **Aspose.Words for .NET** (the free trial works for experimentation)  
* Basic familiarity with C# and Visual Studio (any IDE that supports .NET will do)  

No additional NuGet packages are required beyond `Aspose.Words`.

## Step 1: Create a Word document C# and initialize the DocumentBuilder

The first step is to instantiate a `Document` object and a `DocumentBuilder`. The `Document` represents the entire .docx file, while the `DocumentBuilder` provides fluent methods to add content.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** Without a `DocumentBuilder` you would have to manipulate the OpenXML DOM manually, which is error‑prone and harder to read. The builder abstracts those details and guarantees a well‑formed Word file.

## Step 2: How to add ActiveX button – insert a CommandButton control

Now we insert a **CommandButton ActiveX control** at a specific location. The rectangle defines the button’s position (X, Y) and size (width, height) in points.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Why this matters:** `InsertForms2OleControl` is the only Aspose.Words method that creates a true ActiveX OLE object. The `Forms2OleControlType.CommandButton` enum value tells Word to embed a clickable button rather than a generic OLE container.

## Step 3: Programmatically add command button – hide it until runtime

Word treats any inserted shape as visible by default. To keep the button invisible while you design the template, set the `Hidden` property on the shape that the builder just created.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Why this matters:** Setting `Hidden = true` prevents the button from cluttering the design view. When the document is opened in Word, the runtime environment automatically reveals the control, preserving the intended user experience.

## Step 4: Save the file – create command button word document

Finally, write the document to disk. Choose a path that your application can write to, and use the `.docx` extension to ensure modern compatibility.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Why this matters:** Saving as `.docx` guarantees that the embedded ActiveX control complies with the Office Open XML standard, which is supported by Word 2007 and later. If you need legacy `.doc` support, replace the extension and use `SaveFormat.Doc`.

## Full working example

Putting everything together, here is the complete program you can copy, paste, and run:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Expected output:** After running the program, open `C:\Temp\ActiveX.docx` in Microsoft Word. You will see a blank document; the button is not visible in design mode. Press **Alt + F9** to toggle field codes, then click the button area—Word will render the ActiveX control, and you can interact with it (e.g., double‑click to view its properties).

## Edge cases and best‑practice tips

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **User disables ActiveX** | Word may display a security warning or block the control. | Instruct end users to enable “ActiveX controls” in Trust Center, or provide a macro‑signed alternative. |
| **Document opened in Word Online** | Word Online does not support ActiveX; the button will be omitted. | Use a fallback hyperlink or a content control if you need cloud compatibility. |
| **Different DPI settings** | The rectangle size may appear larger or smaller on high‑DPI displays. | Use `GraphicsUnit.Point` (the default) and test on common DPI settings (96 dpi, 120 dpi). |
| **Multiple buttons** | The `GetChildNodes(NodeType.Shape, true)[0]` call only retrieves the first shape. | Loop through `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` and set `Hidden` for each shape you add. |
| **Legacy .doc format** | Some ActiveX properties are lost when saving as `.doc`. | Prefer `.docx` unless you have a strict legacy requirement. |

**Pro tip:** After inserting the button, you can assign a macro to its `OnAction` property via the Word UI. This lets you define custom click behavior without writing additional C# code.

## Frequently asked questions

* **Does this work with .NET Core?**  
  Yes. Aspose.Words for .NET is fully compatible with .NET 5, .NET 6, and later. Just reference the same NuGet package.

* **Can I change the button caption after the document is generated?**  
  The caption set in `InsertForms2OleControl` becomes the default design‑time text. Users can edit it in Word, but you can also update the caption programmatically by accessing the OLE object's properties via the `Shape.OleFormat` API.

* **What if I need a different size for the button?**  
  Adjust the `RectangleF` values. The first two parameters are the X‑ and Y‑coordinates; the last two are width and height in points (1 pt = 1/72 inch).

## Conclusion

You now know how to **create Word document C#** and **programmatically add command button** using Aspose.Words. The tutorial covered initializing the document, inserting an ActiveX button, hiding it until runtime, and saving the final file. With these building blocks you can embed interactive controls in any Word template you generate.

Next, explore related topics such as **how to add ActiveX button** event handling, **create command button word** styling with VBA, and **programmatically add command button** to existing documents. Extending this pattern to checkboxes, combo boxes, or custom OLE objects follows the same steps—just change the `Forms2OleControlType` enum value.

Start experimenting: replace the caption, adjust the position, or chain multiple controls together. The more you practice, the more fluent you’ll become at delivering rich, interactive Word documents from C#. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [How to add ActiveX button in a Word document with Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}