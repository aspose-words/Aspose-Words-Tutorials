---
title: Reduce PDF File Size by Not Embedding Core Fonts
linktitle: Reduce PDF File Size by Not Embedding Core Fonts
second_title: Aspose.Words Document Processing API
description: Learn how to reduce PDF file size by not embedding core fonts using Aspose.Words for .NET. Follow our step-by-step guide to optimize your PDFs.
weight: 10
url: /net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reduce PDF File Size by Not Embedding Core Fonts

## Introduction

Do you ever find yourself scratching your head, wondering why your PDF files are so large? Well, you’re not alone. One common culprit is embedding core fonts like Arial and Times New Roman. Luckily, Aspose.Words for .NET has a nifty way to tackle this issue. In this tutorial, I’ll show you how to reduce your PDF file size by avoiding the embedding of these core fonts. Let’s dive right in!

## Prerequisites

Before we embark on this exciting journey, let’s make sure you’ve got everything you need. Here’s a quick checklist:

- Aspose.Words for .NET: Make sure you have Aspose.Words for .NET installed. If you don’t have it yet, you can download it [here](https://releases.aspose.com/words/net/).
- Development Environment: You’ll need a development environment like Visual Studio.
- A Word Document: We’ll be using a Word document (e.g., "Rendering.docx") for this tutorial.
- Basic C# Knowledge: A basic understanding of C# will help you follow along.

Alright, now that we’re all set, let’s get into the nitty-gritty!

## Import Namespaces

First things first, let’s import the necessary namespaces. This step ensures we have access to all the Aspose.Words functionalities we need.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Step 1: Initialize Your Document Directory

Before we start manipulating our document, we need to specify the directory where our documents are stored. This is essential for accessing the files.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where your Word document is located.

## Step 2: Load the Word Document

Next, we need to load the Word document that we want to convert to PDF. In this example, we’re using a document named "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

This line of code loads the document into memory, ready for further processing.

## Step 3: Configure PDF Save Options

Now comes the magic part! We’ll configure the PDF save options to avoid embedding core fonts. This is the key step that helps in reducing the PDF file size.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

Setting `UseCoreFonts` to `true` ensures that core fonts like Arial and Times New Roman are not embedded in the PDF, which significantly reduces the file size.

## Step 4: Save the Document as PDF

Finally, we save the Word document as a PDF using the configured save options. This step generates the PDF file without embedding the core fonts.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

And there you have it! Your PDF file is now saved in the specified directory without those bulky core fonts.

## Conclusion

Reducing PDF file size can be a breeze with Aspose.Words for .NET. By avoiding the embedding of core fonts, you can significantly decrease the file size, making it easier to share and store your documents. I hope this tutorial was helpful and gave you a clear understanding of the process. Remember, small tweaks can make a big difference!

## FAQ's

### Why should I avoid embedding core fonts in PDFs?
Avoiding embedding core fonts reduces the file size, making it easier to share and store.

### Can I still view the PDF correctly without embedded core fonts?
Yes, core fonts like Arial and Times New Roman are generally available on most systems.

### What if I need to embed custom fonts?
You can customize the `PdfSaveOptions` to embed specific fonts as needed.

### Is Aspose.Words for .NET free to use?
Aspose.Words for .NET requires a license. You can get a free trial [here](https://releases.aspose.com/).

### Where can I find more documentation on Aspose.Words for .NET?
You can find detailed documentation [here](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
