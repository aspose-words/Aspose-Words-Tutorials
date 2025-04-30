---
title: Reduce PDF Size with Scale Wmf Fonts To Metafile Size
linktitle: Reduce PDF Size with Scale Wmf Fonts To Metafile Size
second_title: Aspose.Words Document Processing API
description: Step-by-step guide to reduce pdf size with scale wmf fonts to metafile size size when converting to PDF with Aspose.Words for .NET.
weight: 10
url: /net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reduce PDF Size with Scale Wmf Fonts To Metafile Size

## Introduction

When working with PDF files, especially those generated from Word documents containing WMF (Windows Metafile) graphics, size management can become a crucial aspect of document handling. One way to control the PDF size is by adjusting how WMF fonts are rendered within the document. In this tutorial, we’ll explore how to reduce PDF size by scaling WMF fonts to the metafile size using Aspose.Words for .NET.

## Prerequisites

Before diving into the steps, ensure you have the following:

1. Aspose.Words for .NET: Make sure you have the Aspose.Words library installed. If not, you can [download it here](https://releases.aspose.com/words/net/).
2. Development Environment: This tutorial assumes you have a .NET development environment set up (like Visual Studio) where you can write and execute C# code.
3. Basic Understanding of .NET Programming: Familiarity with basic .NET programming concepts and C# syntax will be helpful.
4. Word Document with WMF Graphics: You’ll need a Word document containing WMF graphics. You can use your own document or create one for testing.

## Import Namespaces

First, you need to import the necessary namespaces in your C# project. This will give you access to the classes and methods required for working with Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Step 1: Load the Word Document

To start, load the Word document that contains the WMF graphics. This is done using the `Document` class from Aspose.Words.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Load the document
Document doc = new Document(dataDir + "WMF with text.docx");
```

Here, `dataDir` is a placeholder for your document directory path. We create an instance of the `Document` class by passing the path to the Word file. This loads the document into memory, ready for further processing.

## Step 2: Configure Metafile Rendering Options

Next, you need to configure the metafile rendering options. Specifically, set the `ScaleWmfFontsToMetafileSize` property to `false`. This controls whether WMF fonts are scaled to match the metafile size.

```csharp
// Create a new instance of MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

The `MetafileRenderingOptions` class provides options for how metafiles (like WMF) are rendered. By setting `ScaleWmfFontsToMetafileSize` to `false`, you are instructing Aspose.Words not to scale fonts according to the metafile size, which can help in reducing the overall PDF size.

## Step 3: Set PDF Save Options

Now, configure the PDF save options to use the metafile rendering options you’ve just set. This tells Aspose.Words how to handle metafiles when saving the document as a PDF.

```csharp
// Create a new instance of PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

The `PdfSaveOptions` class allows you to specify various settings for saving the document as a PDF. By assigning the previously configured `MetafileRenderingOptions` to the `MetafileRenderingOptions` property of `PdfSaveOptions`, you ensure that the document is saved according to your desired metafile rendering settings.

## Step 4: Save the Document as PDF

Finally, save the Word document as a PDF using the configured save options. This will apply all the settings, including the metafile rendering options, to the output PDF.


```csharp
// Save the document as PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

In this step, the `Save` method of the `Document` class is used to export the document to a PDF file. The path where the PDF will be saved is specified, along with the `PdfSaveOptions` that include the metafile rendering settings.

## Conclusion

By scaling WMF fonts to metafile size, you can significantly reduce the size of your PDF files generated from Word documents. This technique helps in optimizing document storage and distribution without compromising the quality of the visual content. Following the steps outlined above ensures that your PDF files are more manageable and efficient in size.

## FAQ's

### What is WMF and why is it important for PDF size?

WMF (Windows Metafile) is a graphic format used in Microsoft Windows. It can contain both vector and bitmap data. Since vector data can be scaled and manipulated, it’s important to handle it properly to avoid unnecessarily large PDF files.

### How does scaling WMF fonts to metafile size affect the PDF?

Scaling WMF fonts to metafile size can help reduce the overall PDF size by avoiding high-resolution font rendering that might increase file size.

### Can I use other metafile formats with Aspose.Words?

Yes, Aspose.Words supports various metafile formats, including EMF (Enhanced Metafile) in addition to WMF.

### Is this technique applicable to all types of Word documents?

Yes, this technique can be applied to any Word document that contains WMF graphics, helping in optimizing the size of the generated PDF.

### Where can I find more information about Aspose.Words?

You can explore more about Aspose.Words in the [Aspose.Words Documentation](https://reference.aspose.com/words/net/). For downloads, trials, and support, visit the [Aspose.Words Download Page](https://releases.aspose.com/words/net/), [Buy Aspose.Words](https://purchase.aspose.com/buy), [Free Trial](https://releases.aspose.com/), [Temporary License](https://purchase.aspose.com/temporary-license/), and [Support](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
