---
title: Export Word Document Header Footer Bookmarks to PDF Document
linktitle: Export Word Document Header Footer Bookmarks to PDF Document
second_title: Aspose.Words Document Processing API
description: Learn how to export header and footer bookmarks from a Word document to PDF using Aspose.Words for .NET with our step-by-step guide.
weight: 10
url: /net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Export Word Document Header Footer Bookmarks to PDF Document

## Introduction

Converting Word documents to PDF is a common task, especially when you want to share or archive documents while preserving their formatting. Sometimes, these documents contain important bookmarks within the headers and footers. In this tutorial, we’ll walk through the process of exporting these bookmarks from a Word document to a PDF using Aspose.Words for .NET.

## Prerequisites

Before we dive in, make sure you have the following:

- Aspose.Words for .NET: You need to have Aspose.Words for .NET installed. You can download it from [here](https://releases.aspose.com/words/net/).
- Development Environment: Set up your development environment. You can use Visual Studio or any other .NET compatible IDE.
- Basic Knowledge of C#: Familiarity with C# programming is required to follow along with the code examples.

## Import Namespaces

First things first, you need to import the necessary namespaces in your C# project. Add these lines at the top of your code file:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Let’s break down the process into easy-to-follow steps.

## Step 1: Initialize the Document

The first step is to load your Word document. Here’s how you can do it:

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

In this step, you’re simply specifying the path to your document directory and loading the Word document.

## Step 2: Configure PDF Save Options

Next, you need to configure the PDF save options to ensure that bookmarks in the headers and footers are exported correctly.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Here, we’re setting up the `PdfSaveOptions`. The `DefaultBookmarksOutlineLevel` property sets the outline level for bookmarks, and the `HeaderFooterBookmarksExportMode` property ensures that only the first occurrence of bookmarks in headers and footers is exported.

## Step 3: Save the Document as PDF

Finally, save your document as a PDF with the configured options.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

In this step, you’re saving the document to the specified path with the options you’ve configured.

## Conclusion

And there you have it! By following these steps, you can easily export bookmarks from the headers and footers of a Word document to a PDF using Aspose.Words for .NET. This method ensures that important navigational aids within your document are preserved in the PDF format, making it easier for readers to navigate through your document.

## FAQ's

### Can I export all bookmarks from the Word document to PDF?

Yes, you can. In the `PdfSaveOptions`, you can adjust the settings to include all bookmarks if needed.

### What if I want to export bookmarks from the body of the document as well?

You can configure the `OutlineOptions` in `PdfSaveOptions` to include bookmarks from the body of the document.

### Is it possible to customize the bookmark levels in the PDF?

Absolutely! You can customize the `DefaultBookmarksOutlineLevel` property to set different outline levels for your bookmarks.

### How do I handle documents with no bookmarks?

If your document has no bookmarks, the PDF will be generated without any bookmark outline. Ensure your document contains bookmarks if you need them in the PDF.

### Can I use this method for other document types like DOCX or RTF?

Yes, Aspose.Words for .NET supports various document types, including DOCX, RTF, and others.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
