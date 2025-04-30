---
title: Export Custom Properties in a PDF Document
linktitle: Export Custom Properties in a PDF Document
second_title: Aspose.Words Document Processing API
description: Learn how to export custom properties in a PDF document using Aspose.Words for .NET with our detailed, step-by-step guide.
weight: 10
url: /net/programming-with-pdfsaveoptions/custom-properties-export/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Export Custom Properties in a PDF Document

## Introduction

Exporting custom properties in a PDF document can be incredibly useful for various business needs. Whether you're managing metadata for better searchability or embedding critical information directly within your documents, Aspose.Words for .NET makes the process seamless. This tutorial will guide you through creating a Word document, adding custom properties, and exporting them into a PDF with these properties intact.

## Prerequisites

Before diving into the code, ensure you have the following:

- Aspose.Words for .NET installed. If you haven't installed it yet, you can download it [here](https://releases.aspose.com/words/net/).
- A development environment like Visual Studio.
- Basic knowledge of C# programming.

## Import Namespaces

First, you need to import the necessary namespaces in your project. These namespaces contain the classes and methods required to manipulate Word documents and export them as PDFs.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Let's break down the process into simple, manageable steps.

## Step 1: Initialize the Document

To start, you'll need to create a new document object. This object will serve as the foundation for adding custom properties and exporting to PDF.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## Step 2: Add Custom Properties

Next, you'll add custom properties to your document. These properties can include metadata like company name, author, or any other relevant information.

```csharp
doc.CustomDocumentProperties.Add("Company", "Aspose");
```

## Step 3: Configure PDF Save Options

Now, configure the PDF save options to ensure that the custom properties are included when exporting the document. The `PdfSaveOptions` class provides various settings to control how the document is saved as a PDF.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    CustomPropertiesExport = PdfCustomPropertiesExport.Standard
};
```

## Step 4: Save the Document as a PDF

Finally, save the document as a PDF in the specified directory. The `Save` method combines all the previous steps and produces a PDF with the custom properties included.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.CustomPropertiesExport.pdf", saveOptions);
```

## Conclusion

Exporting custom properties in a PDF document using Aspose.Words for .NET is a straightforward process that can greatly enhance your document management capabilities. By following these steps, you can ensure that critical metadata is preserved and accessible, improving the efficiency and organization of your digital documents.

## FAQ's

### What are custom properties in a PDF document?
Custom properties are metadata added to a document that can include information like the author, company name, or any other relevant data that needs to be embedded within the document.

### Why should I use Aspose.Words for .NET for exporting custom properties?
Aspose.Words for .NET provides a robust and easy-to-use API for manipulating Word documents and exporting them as PDFs, ensuring that custom properties are preserved and accessible.

### Can I add multiple custom properties to a document?
Yes, you can add multiple custom properties to a document by calling the `Add` method for each property you want to include.

### What other formats can I export to using Aspose.Words for .NET?
Aspose.Words for .NET supports exporting to various formats, including DOCX, HTML, EPUB, and many more.

### Where can I get support if I encounter issues?
For support, you can visit the [Aspose.Words support forum](https://forum.aspose.com/c/words/8) for assistance.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
