---
title: Reduce PDF Size by Disabling Embeded Fonts
linktitle: Reduce PDF Size by Disabling Embeded Fonts
second_title: Aspose.Words Document Processing API
description: Reduce PDF size by disabling embedded fonts using Aspose.Words for .NET. Follow our step-by-step guide to optimize your documents for efficient storage and sharing.
weight: 10
url: /net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reduce PDF Size by Disabling Embeded Fonts

## Introduction

Reducing the size of PDF files can be crucial for efficient storage and quick sharing. One effective way to do this is by disabling embedded fonts, especially when the standard fonts are already available on most systems. In this tutorial, we'll explore how to reduce PDF size by disabling embedded fonts using Aspose.Words for .NET. We'll walk through each step to ensure you can easily implement this in your own projects.

## Prerequisites

Before diving into the code, make sure you have the following:

- Aspose.Words for .NET: If you haven't already, download and install it from the [Download link](https://releases.aspose.com/words/net/).
- A .NET Development Environment: Visual Studio is a popular choice.
- A Sample Word Document: Have a DOCX file ready that you want to convert to a PDF.

## Import Namespaces

To get started, ensure you have the necessary namespaces imported into your project. This allows you to access the classes and methods required for our task.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Let's break down the process into simple, manageable steps. Each step will guide you through the task, ensuring you understand what's happening at every point.

## Step 1: Initialize Your Document

First, we need to load the Word document that you want to convert to a PDF. This is where your journey begins.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Here, `dataDir` is a placeholder for the directory where your document is located. Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path.

## Step 2: Configure PDF Save Options

Next, we'll set up the PDF save options. This is where we specify that we don't want to embed the standard Windows fonts.

```csharp
// The output PDF will be saved without embedding standard windows fonts.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

By setting `FontEmbeddingMode` to `EmbedNone`, we instruct Aspose.Words not to include these fonts in the PDF, reducing the file size.

## Step 3: Save the Document as PDF

Finally, we save the document as a PDF using the configured save options. This is the moment of truth where your DOCX transforms into a compact PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

Replace `"YOUR DOCUMENT DIRECTORY"` with your actual directory path once again. The output PDF will now be saved in the specified directory without embedded standard fonts.

## Conclusion

By following these steps, you can significantly reduce the size of your PDF files. Disabling embedded fonts is a straightforward yet effective way to make your documents lighter and easier to share. Aspose.Words for .NET makes this process seamless, ensuring you can optimize your files with minimal effort.

## FAQ's

### Why should I disable embedded fonts in a PDF?
Disabling embedded fonts can significantly reduce the file size of a PDF, making it more efficient for storage and faster to share.

### Will the PDF still display correctly without embedded fonts?
Yes, as long as the fonts are standard and available on the system where the PDF is viewed, it will display correctly.

### Can I selectively embed only certain fonts in a PDF?
Yes, Aspose.Words for .NET allows you to customize which fonts are embedded, providing flexibility in how you reduce file size.

### Do I need Aspose.Words for .NET to disable embedded fonts in PDFs?
Yes, Aspose.Words for .NET provides the functionality needed to configure font embedding options in PDFs.

### How do I get support if I encounter issues?
You can visit the [Support forum](https://forum.aspose.com/c/words/8) for assistance with any issues you encounter.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
