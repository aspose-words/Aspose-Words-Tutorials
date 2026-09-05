---
category: general
date: 2026-09-05
description: Learn how to create group shape docx, insert ActiveX command button,
  and load Markdown into a Word document with a complete C# example.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: en
lastmod: 2026-09-05
og_description: Create group shape docx, insert ActiveX command button, and load Markdown
  into a Word document using C#. Follow this step‑by‑step tutorial.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Create group shape docx and embed ActiveX controls – C# guide
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: How to create group shape docx and add interactive controls in C#
url: /java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create group shape docx and add interactive controls in C#

If you need to **create group shape docx** files programmatically, this guide shows you exactly how. You’ll also see how to **insert ActiveX command button** controls and **load Markdown into a Word document** without losing underline formatting. By the end of the tutorial you’ll have a fully functional `.docx` that combines vector graphics, interactive UI elements, and markdown‑based content.

This tutorial assumes you have a basic C# development environment and the Aspose.Words for .NET library installed. No external tools are required—everything runs inside a standard .NET console or desktop application.

## Prerequisites

- .NET 6.0 SDK or later (the code also works with .NET Framework 4.7+)
- Aspose.Words for .NET (NuGet package `Aspose.Words`)
- A valid X.509 certificate (`.pfx`) if you want to test the signing step
- An image file (e.g., `logo.png`) and a markdown file (`sample.md`) placed in a known folder

> **Pro tip:** Keep all input files in a single *resources* folder to simplify relative paths.

## Step 1: Set up the project and import namespaces

Create a new console project and add the required `using` directives. This block also demonstrates how to reference the Aspose.Words classes you’ll use later.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

The `using` statements give you direct access to `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl`, and other types used throughout the tutorial.

## Step 2: **Create group shape docx** – add a grouped shape with child elements

A *group shape* lets you treat multiple drawing objects as a single unit. This is useful for moving or resizing related graphics together.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**Why a group shape?**  
Grouping keeps the rectangle and ellipse aligned when the user drags them in Word. It also simplifies later operations such as applying a common border or moving the whole graphic programmatically.

## Step 3: Insert a plain‑text content control (placeholder for user input)

Content controls give end users a structured area to type text. The placeholder text disappears once the user starts typing.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

The `PlaceholderName` property is what Word shows in a light‑gray cue. Users can replace it with their own text, and the underlying XML remains well‑formed.

## Step 4: **Insert ActiveX command button** – add interactive UI to the document

ActiveX controls are still supported in modern Word files and can trigger macros or external automation. Below we add a *command button* and set its caption.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**When to use an ActiveX button?**  
If you distribute the document within a corporate environment that relies on VBA macros, an ActiveX button can launch a macro or launch an external application. For pure HTML‑based interactivity, consider using *content controls* with *Office.js* instead.

## Step 5: Insert a hidden image (e.g., a logo) for branding or later script access

Hidden shapes are not displayed in the printed document but remain in the XML, allowing you to retrieve them programmatically later.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Step 6: **Load markdown into a Word document** while preserving underline formatting

Aspose.Words can import Markdown directly. Enabling `ImportUnderlineFormatting` ensures that markdown underlines (`<u>` or `__text__`) become Word underline styles instead of plain text.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Edge case:** If the markdown file contains tables, they are automatically converted to Word tables. If you need custom table styling, apply a `DocumentBuilder` after insertion.

## Step 7: Sign the document with XAdES‑EPES (optional security step)

Digital signatures guarantee document integrity. The following code signs the **create group shape docx** file using an XAdES‑EPES profile.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** Keep the certificate password out of source control. Use environment variables or a secure vault in production.

## Full runnable example

Putting all steps together yields a single, self‑contained program. Save the file as `Program.cs` and run it from the command line.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Running the program generates `CompleteGroupShape.docx` containing:

- A grouped rectangle + ellipse (the **create group shape docx** core)
- A plain‑text content control with placeholder text
- An **insert ActiveX command button** labeled “Click Me”
- A hidden logo image
- Markdown content with preserved underlines
- An XAdES‑EPES digital signature (if certificate provided)

## Common questions and troubleshooting

| Question | Answer |
|---|---|
| **Will the ActiveX button work on macOS Word?** | macOS Word does not support ActiveX controls. The button will appear as a static image. Use content controls with Office.js for cross‑platform interactivity. |
| **What if the markdown file contains custom CSS?** | Aspose.Words ignores CSS; only standard markdown syntax is processed. Convert CSS‑styled elements to Word styles manually after import. |
| **Can I add more shapes to the same group later?** | Yes. Retrieve the `GroupShape` by its name or index, then call `AppendChild(newShape)`. Remember to re‑save the document after modifications. |
| **How do I change the signature algorithm?** | Set `signature.SignatureAlgorithm` before calling `Sign`. The default is SHA‑256, which meets most compliance requirements. |
| **Is the hidden image visible in the Word UI?** | No, but it can be displayed by toggling *Show hidden text* in Word’s options. This is useful for storing metadata without cluttering the layout. |

## Next steps

Now that you can **create group shape docx**, **insert ActiveX command button**, and **load markdown into a Word document**, you might explore:

- **Embedding VBA macros** that react to the ActiveX button click.
- **Applying custom styles** to the markdown‑generated paragraphs.
- **Generating PDFs** from the same document using `doc.Save("output.pdf", SaveFormat.Pdf)`.
- **Automating batch processing** of multiple markdown files into a single compiled report.

These extensions let you build fully automated document pipelines that combine rich graphics, interactive controls, and markdown‑based authoring—all from C#.

---

*Happy coding! If you found this tutorial


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create markdown from word – Complete C# Guide](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}