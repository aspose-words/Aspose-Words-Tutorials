---
category: general
date: 2026-07-29
description: Add command button to word document using Aspose.Words. Learn how to
  set activex control properties and set command button caption in a few easy steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: en
lastmod: 2026-07-29
og_description: Add command button to word document with Aspose.Words. This tutorial
  shows how to set activex control properties and set command button caption quickly.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Add Command Button to Word Document – Aspose.Words Step‑by‑Step
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Add Command Button to Word Document with Aspose.Words – Complete Guide
url: /net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add Command Button to Word Document – Complete Programming Walkthrough

Ever needed to **add command button to word document** but weren’t sure which API calls to use? You’re not alone; many developers hit that wall when they first try to embed interactive controls in a DOCX file. The good news is that Aspose.Words makes it surprisingly painless. In this guide we’ll walk through creating a CommandButton ActiveX control, **set activex control properties**, and **set command button caption**—all with clean C# code you can copy‑paste right now.

By the end of this tutorial you’ll have a fully functional Word file that contains a clickable “Submit” button, ready to be opened in Microsoft Word. No external VBA scripts, no manual UI fiddling—just pure programmatic control.

## What You’ll Learn

* How to create a blank Word document and a `DocumentBuilder`.
* The exact method call to **add command button to word document** using Aspose.Words.
* Ways to **set activex control properties** such as size, position, and name.
* The proper technique to **set command button caption** so the button reads exactly what you want.
* Tips for handling edge cases like different button types, DPI scaling, and Word version compatibility.

> **Prerequisite:** Visual Studio (or any C# IDE) with Aspose.Words for .NET installed (NuGet package `Aspose.Words`). No prior ActiveX experience required.

---

## Step 1: Set Up the Project and Import Namespaces

Before we can **add command button to word document**, we need a C# project that references Aspose.Words. Create a new .NET console app, then add the NuGet package:

```bash
dotnet add package Aspose.Words
```

Now bring the required namespaces into your source file:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

These three `using` directives give you access to the `Document`, `DocumentBuilder`, and the `Forms2OleControl` classes that power ActiveX insertion.

*Pro tip:* If you’re using Visual Studio, the IDE will suggest adding these automatically when you type the class names.

---

## Step 2: Create a Blank Document and a Builder

A fresh `Document` object represents an empty Word file. The `DocumentBuilder` is our handy “pen” that lets us draw, insert text, and—crucially—place ActiveX controls.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

At this point the document is just a blank canvas—think of it as a clean sheet of paper waiting for your command button.

---

## Step 3: Insert the CommandButton ActiveX Control

Now we finally **add command button to word document**. Aspose.Words provides the `InsertForms2OleControl` method, which accepts the control type and dimensions. We’ll use `Forms2OleControlType.CommandButton` and give it a comfortable width of 150 points and a height of 30 points.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

The method returns a `Forms2OleControl` instance, which we’ll use to **set activex control properties** in the next step.

---

## Step 4: Configure the Control – Name, Caption, and Position

### Setting the Caption

The caption is the text that appears on the button itself. To **set command button caption**, simply assign a string to the `Caption` property:

```csharp
commandButton.Caption = "Submit";
```

You can change `"Submit"` to anything—“Save”, “Export”, “Launch”, etc.—and Word will display that exact text.

### Naming the Control

Giving the control a meaningful name makes it easier to reference later (for example, when automating Word macros). We’ll set the `Name` property:

```csharp
commandButton.Name = "btnSubmit";
```

### Positioning on the Page

Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top` properties to place the button where you need it:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

If you need to align the button relative to a paragraph, you can move the builder’s cursor first, then insert the control; the coordinates will be relative to that location.

*Edge case:* On high‑DPI monitors the visual size may appear slightly different in Word. To keep the button’s physical size consistent across devices, you can calculate the points based on the target DPI (normally 96 DPI for Word).

---

## Step 5: Save the Document

With the button fully configured, persisting the file is a one‑liner:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

The resulting `CommandButton.docx` contains a fully functional ActiveX button. Open it in Microsoft Word, and you’ll see a “Submit” button positioned exactly where you placed it.

### Expected Result

1. The Word document opens with a single page.
2. A rectangular button labeled **Submit** appears at the coordinates you specified.
3. If you right‑click the button and choose **Properties**, you’ll see the name `btnSubmit` and other properties you set.

---

## Step 6: Advanced Variations and Common Pitfalls

### Inserting Other ActiveX Types

The `InsertForms2OleControl` method isn’t limited to command buttons. You can embed check boxes, option buttons, or even custom ActiveX objects:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

The same **set activex control properties** pattern applies—just swap the type enum.

### Handling Word Versions

Older Word versions (pre‑2007) use the binary `.doc` format, which stores ActiveX controls differently. Aspose.Words automatically converts the control when you save as `.doc`, but some properties (like precise positioning) may shift. If you target legacy formats, test the output in the specific Word version you need.

### Security Settings

Word may disable ActiveX controls on machines with strict macro security. To avoid a “Security Warning” dialog, consider:

* Signing the document with a trusted certificate.
* Instructing users to enable ActiveX content for that file location.
* Using a macro‑free alternative (e.g., plain content controls) if security is a concern.

---

## Step 7: Full Working Example

Below is the complete, ready‑to‑run program that incorporates every step we discussed. Copy it into your `Program.cs`, adjust the output path if necessary, and hit **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**What this code does:**

* Starts with a fresh document.
* Inserts a command button, **sets activex control properties**, and **sets command button caption**.
* Adds a brief explanatory paragraph.
* Saves the file as `CommandButton.docx`.

Run the program, open the generated file, and you’ll see the button sitting beneath the explanatory text.

---

## Conclusion

We’ve just demonstrated how to **add command button to word document** using Aspose.Words, how to **set activex control properties**, and how to **set command button caption**—all in a concise, production‑ready C# snippet. The approach scales: swap the control type, tweak dimensions, or loop over a data source to embed dozens of buttons automatically.

Want to go further? Try:

* Binding the button to a macro that triggers a data export.
* Adding images or custom icons inside the button using the `Picture` property.
* Building a full form with multiple ActiveX controls (text boxes, combo boxes, etc.).

Experimentation is the best way to master Word automation. If you hit a snag, remember to double‑check your DPI calculations and Word security settings. Happy coding, and may your documents be ever more interactive!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}