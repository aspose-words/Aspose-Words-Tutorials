---
title: Optimize PDF Size with Skip Embedded Arial & Times Roman Fonts
linktitle: Optimize PDF Size with Skip Embedded Arial & Times Roman Fonts
second_title: Aspose.Words Document Processing API
description: Optimize PDF size by skipping embedded Arial and Times Roman fonts using Aspose.Words for .NET. Follow this step-by-step guide to streamline your PDF files.
weight: 10
url: /net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Optimize PDF Size with Skip Embedded Arial & Times Roman Fonts

## Introduction

Ever found yourself in a situation where your PDF file size is just too large? It’s like packing for a vacation and realizing your suitcase is bursting at the seams. You know you need to shed some weight, but what do you let go of? When working with PDF files, especially those converted from Word documents, embedded fonts can bloat your file size. Thankfully, Aspose.Words for .NET provides a sleek solution to keep your PDFs lean and mean. In this tutorial, we’ll dive into how to optimize your PDF size by skipping embedded Arial and Times Roman fonts. Let's get started!

## Prerequisites

Before we jump into the nitty-gritty, there are a few things you’ll need:
- Aspose.Words for .NET: Make sure you have this powerful library installed. If not, you can download it from [here](https://releases.aspose.com/words/net/).
- A basic understanding of C#: This will help you follow along with the code snippets.
- A Word document: We’ll be using a sample document to demonstrate the process. 

## Import Namespaces

First things first, ensure you have the necessary namespaces imported. This sets the stage for accessing the Aspose.Words functionalities.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Alright, let’s break down the process step by step.

## Step 1: Set Up Your Environment

To begin, you need to set up your development environment. Open your favorite C# IDE (like Visual Studio) and create a new project.

## Step 2: Load the Word Document

The next step is to load the Word document that you want to convert to a PDF. Make sure your document is in the correct directory.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

In this snippet, replace `"YOUR DOCUMENT DIRECTORY"` with the path to your document directory.

## Step 3: Configure PDF Save Options

Now, we need to configure the PDF save options to control how fonts are embedded. By default, all fonts are embedded, which can increase the file size. We’ll change this setting.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## Step 4: Save the Document as PDF

Finally, save the document as a PDF with the specified save options. This is where the magic happens.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

This command saves your document as a PDF named "OptimizedPDF.pdf" in the specified directory.

## Conclusion

And there you have it! You’ve just learned how to optimize your PDF file size by skipping the embedding of Arial and Times Roman fonts using Aspose.Words for .NET. This simple tweak can significantly reduce your file sizes, making them easier to share and store. It’s like hitting the gym for your PDFs, shedding unnecessary weight while keeping all the essentials intact.

## FAQ's

### Why should I skip embedding Arial and Times Roman fonts?
Skipping these common fonts can reduce your PDF file size, as most systems already have these fonts installed.

### Will this affect the appearance of my PDF?
No, it won’t. Since Arial and Times Roman are standard fonts, the appearance remains consistent across different systems.

### Can I skip embedding other fonts too?
Yes, you can configure the save options to skip embedding other fonts if needed.

### Is Aspose.Words for .NET free?
Aspose.Words for .NET offers a free trial which you can download [here](https://releases.aspose.com/), but for full access, you need to purchase a license [here](https://purchase.aspose.com/buy).

### Where can I find more tutorials on Aspose.Words for .NET?
You can find comprehensive documentation and tutorials [here](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
