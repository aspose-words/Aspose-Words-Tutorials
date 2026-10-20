---
category: general
date: 2026-07-19
description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
  command button, set button size, and insert button programmatically.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: en
lastmod: 2026-07-19
og_description: Create Word Document with Aspose.Words C# and embed an ActiveX command
  button in seconds. Follow the step‑by‑step guide to set button size and insert button
  easily.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Create Word Document with ActiveX Button – C# Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Create Word Document with ActiveX Button – C# Guide
url: /net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document with ActiveX Button – Complete C# Guide

Ever wondered how to **create word document** that contains a functional ActiveX button? Maybe you’re automating a report and need a clickable “Approve” control right inside the file. In this tutorial we’ll walk through exactly that—using Aspose.Words for .NET to add an ActiveX command button, set its size, and insert it where you need it.  

If you’ve ever asked yourself *how to add activex* controls without opening Word manually, you’re in the right place. By the end you’ll have a runnable example, a clear explanation of each step, and tips for handling common pitfalls.

## What You’ll Learn

- How to set up Aspose.Words in a C# project  
- The exact code to **create word document** and embed an ActiveX command button  
- Ways to **set button size** and customize its caption and name  
- The proper method to **insert command button** and **how to insert button** at any location in the document  
- Edge‑case considerations (Word version, platform limits, security warnings)

### Prerequisites

- .NET 6.0 or later (the code also works on .NET Framework 4.7+).  
- A valid Aspose.Words for .NET license (or a free evaluation key).  
- Visual Studio 2022 (or any IDE you like).  
- Basic familiarity with C# and object‑oriented programming.

No other third‑party libraries are required.

---

## Step 1: Create Word Document – Project Setup

Before we can **insert command button**, we need a blank Word file to work with. This step also shows the classic “create word document” pattern using Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `Document` represents the whole .docx file, while `DocumentBuilder` tracks the current cursor position. All subsequent inserts (including our ActiveX control) happen relative to this builder.

---

## Step 2: How to Add ActiveX – Build the CommandButton Control

Now that the document exists, let’s tackle the **how to add activex** part. Aspose.Words exposes the `Forms2OleControl` class for ActiveX objects. Here we’ll create a command button and configure its properties, including the **set button size** requirement.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Pro tip:** The size is measured in points (1 point = 1/72 inch). Adjust the values to fit your layout; for a typical toolbar button, 120 × 30 works nicely.

---

## Step 3: Insert Command Button – The Core of **Insert Command Button**

With the control ready, we now **insert command button** into the document at the builder’s current location. You can move the builder anywhere (e.g., after a paragraph) before calling this method.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

If you need to **how to insert button** at a specific bookmark, just move the builder first:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **What happens behind the scenes?** Aspose.Words writes the necessary OLE object streams into the .docx package, so Word can render the button without any extra macros.

---

## Step 4: Save the Document – Finishing the **Create Word Document** Cycle

The final step is straightforward: persist the file to disk. This completes the round‑trip of **create word document**, embed the ActiveX, and save.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Open the resulting file in Microsoft Word (Windows only). You should see a clickable button labeled “Click Me”. Clicking it will trigger the default Action for a CommandButton—nothing happens unless you attach VBA code, but the control is fully functional.

> **Expected output:** A .docx file with a single page, a button centered at the insertion point, sized 120 × 30 pt, captioned “Click Me”.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Image alt text:* **ActiveX button inserted into a Word document using C#** (matches `og_image_alt`).

---

## Step 5: Edge Cases, Security, and Best Practices

### Platform Limitations
- ActiveX controls only run on the Windows version of Word. If your audience includes macOS or Word Online users, the button will appear as a static image.
- Some corporate environments disable ActiveX for security; you may need to sign the document or inform users to enable content.

### VBA Interaction (Optional)
If you want the button to execute a macro, you’ll have to add a VBA project to the document after saving. Aspose.Words does not generate VBA code automatically, but you can use the `Document.VbaProject` API to inject it.

### Naming Collisions
Always give each control a unique `Name`. Re‑using the same name can cause runtime errors when Word tries to resolve the control.

### Performance Tip
When inserting many controls, reuse a single `DocumentBuilder` instance and avoid calling `doc.Save` inside a loop. Batch the inserts and save once at the end.

---

## Full Working Example

Putting everything together, here’s a complete, copy‑and‑paste‑ready program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Run the program, open the saved file, and you’ll see the button exactly where the builder was positioned.

---

## Conclusion

We’ve just **created word document** from scratch, learned **how to add activex** by configuring a `Forms2OleControl`, mastered the **set button size** properties, and demonstrated the proper way to **insert command button** and **how to insert button** at any spot in the file.  

From a single code sample you now have a solid foundation for richer Word automation—whether you’re building templates with interactive forms, generating contracts that require user acknowledgment, or simply sprinkling a few handy controls throughout a report.

### What’s Next?

- **Style the button** – change fonts, colors, or add an image background.  
- **Attach VBA macros** – make the button perform calculations or launch external programs.  
- **Combine with other controls** – checkboxes, list boxes, or even embedded Excel sheets.  

Feel free to experiment, and if you hit a snag, drop a comment below. Happy coding, and enjoy automating Word with Aspose.Words!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}