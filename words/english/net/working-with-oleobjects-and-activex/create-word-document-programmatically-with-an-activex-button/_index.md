---
category: general
date: 2026-10-20
description: Create Word document programmatically and add a command button using
  Aspose.Words. Learn to insert an ActiveX control and set button caption.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add command button
- add activex control
- insert activex button
- set button caption
language: en
lastmod: 2026-10-20
og_description: Create Word document programmatically and embed an ActiveX command
  button. This tutorial explains how to insert the control and set its caption with
  Aspose.Words.
og_image_alt: Word file showing an ActiveX command button inserted by Aspose.Words
og_title: Create Word document programmatically – add ActiveX button
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  headline: Create Word document programmatically with an ActiveX button
  type: TechArticle
- description: Create Word document programmatically and add a command button using
    Aspose.Words. Learn to insert an ActiveX control and set button caption.
  name: Create Word document programmatically with an ActiveX button
  steps:
  - name: 'Open a terminal or Visual Studio and create a new console project:'
    text: 'Open a terminal or Visual Studio and create a new console project:'
  - name: 'Add the Aspose.Words package:'
    text: 'Add the Aspose.Words package:'
  - name: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
    text: '(Optional) If you have a license file, place it in the project root and
      add the following line at the start of `Program.cs` to avoid evaluation watermarks:'
  - name: Open `ActiveXCommandButton.docx` in Microsoft Word.
    text: Open `ActiveXCommandButton.docx` in Microsoft Word.
  - name: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
    text: Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s
      borders.
  - name: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
    text: If the button does not appear, check that the **Developer** tab is enabled
      and that your Word version supports ActiveX controls.
  - name: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
    text: For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches
      a VBA routine; otherwise Word will display a security warning.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Create Word document programmatically with an ActiveX button
url: /net/working-with-oleobjects-and-activex/create-word-document-programmatically-with-an-activex-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word document programmatically with an ActiveX button

Create Word document programmatically with Aspose.Words, then add a command button that users can click. This guide walks you through inserting an ActiveX control, configuring its properties, and saving the result as a **.docx** file.

You’ll see a complete, runnable example that you can copy into a console application. By the end of the tutorial you can generate a Word file that contains a fully functional command button, and you’ll understand how to **add command button**, **add activex control**, **insert activex button**, and **set button caption** without leaving your C# code.

## Prerequisites

Before you start, make sure you have:

* .NET 6.0 SDK or later installed  
* Visual Studio 2022 (or any C#‑compatible IDE)  
* An Aspose.Words for .NET license file (the free trial works for this example)  
* Basic familiarity with C# and the .NET project system  

No additional NuGet packages are required beyond **Aspose.Words** because the ActiveX support is built into the library.

## Step 1: Set up the project and add Aspose.Words

1. Open a terminal or Visual Studio and create a new console project:

   ```bash
   dotnet new console -n WordActiveXDemo
   cd WordActiveXDemo
   ```

2. Add the Aspose.Words package:

   ```bash
   dotnet add package Aspose.Words
   ```

3. (Optional) If you have a license file, place it in the project root and add the following line at the start of `Program.cs` to avoid evaluation watermarks:

   ```csharp
   Aspose.Words.License license = new Aspose.Words.License();
   license.SetLicense("Aspose.Words.lic");
   ```

## Step 2: Create Word document programmatically – initialize the document

The first operation is to **create Word document programmatically**. You do this by instantiating a `Document` object and a `DocumentBuilder` that lets you edit the document content.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;   // Provides ActiveX control types
using System.Drawing;        // For Point and Size structs

// Initialize a new blank document
Document document = new Document();

// DocumentBuilder gives a cursor‑based API for inserting elements
DocumentBuilder builder = new DocumentBuilder(document);
```

The `Document` represents the entire file, while the `DocumentBuilder` maintains a cursor that you can move to any location in the document. This separation keeps the API clean and enables you to **add activex control** later without manually managing low‑level structures.

## Step 3: Add command button – inserting an ActiveX control

Now you’ll **add command button** by inserting an ActiveX control of type `OleControlType.CommandButton`. The `InsertForms2OleControl` method requires the control type, a location (`Point`), and a size (`Size`).

```csharp
// Define where the button will appear (X = 100 pt, Y = 150 pt)
Point buttonPosition = new Point(100, 150);

// Define the button dimensions (width = 120 pt, height = 30 pt)
Size buttonSize = new Size(120, 30);

// Insert the ActiveX command button at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton, // control type
    buttonPosition,              // position
    buttonSize);                 // size
```

The call above **insert activex button** into the document at the exact coordinates you specify. The coordinates are measured in points (1 pt ≈ 1/72 in). If you need the button on a specific paragraph, move the builder’s cursor first:

```csharp
builder.Writeln("Click the button below:");
builder.MoveToDocumentEnd(); // places the cursor after the paragraph
```

## Step 4: Set button caption – customizing the command button text

A button without a label is confusing, so you’ll **set button caption** to something meaningful. The `Caption` property defines the text displayed on the button, while `Name` gives the control a programmatic identifier.

```csharp
// Give the button a unique name for later reference
commandButton.Name = "btnSubmit";

// Set the visible text on the button
commandButton.Caption = "Submit";

// Optional: assign a macro name that Word will call when the button is clicked
commandButton.OnClick = "SubmitForm()";
```

If you later export the document to a macro‑enabled format (`.docm`), the `OnClick` value must match a VBA macro name. For a plain `.docx`, the property is stored but not executed, which is fine for most automation scenarios.

## Step 5: Save the document containing the ActiveX button

After configuring the control, you can **save the document**. Choose a directory you have write access to, and use the `.docx` extension for maximum compatibility.

```csharp
// Replace with your desired output folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ActiveXCommandButton.docx");

// Save the document to disk
document.Save(outputPath);
```

When you open the generated file in Microsoft Word, you’ll see a button labeled **Submit** at the coordinates you specified. Clicking the button in the desktop client will attempt to run the `SubmitForm` macro (if it exists).

## Step 6: Verify the result and troubleshoot common issues

1. Open `ActiveXCommandButton.docx` in Microsoft Word.  
2. Switch to **Design Mode** (Developer tab → **Design Mode**) to see the button’s borders.  
3. If the button does not appear, check that the **Developer** tab is enabled and that your Word version supports ActiveX controls.  
4. For macro‑enabled files (`.docm`), ensure the macro name in `OnClick` matches a VBA routine; otherwise Word will display a security warning.

### Pro tip

ActiveX controls are Windows‑only. If you need cross‑platform interactivity, consider using **Content Controls** (`RichTextContentControl`) instead of an ActiveX button.

## Full source code

Below is the complete, ready‑to‑run program. Copy it into `Program.cs` and execute `dotnet run`.

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Optional: apply a license to remove evaluation watermarks
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // Step 2: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a paragraph to give context
        builder.Writeln("Please click the button below to submit the form:");
        builder.MoveToDocumentEnd();

        // Step 3: Add command button – insert ActiveX control
        Point position = new Point(100, 150);
        Size size = new Size(120, 30);
        Forms2OleControl commandButton = builder.InsertForms2OleControl(


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with ActiveX Button – C# Guide](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)
- [create word document button with Aspose.Words – Full Code Example](/words/english/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}