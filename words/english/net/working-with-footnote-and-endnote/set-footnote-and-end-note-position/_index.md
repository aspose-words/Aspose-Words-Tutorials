---
title: Set Footnote And Endnote Position
linktitle: Set Footnote And End Note Position
second_title: Aspose.Words Document Processing API
description: Learn how to set footnote and endnote positions in Word documents using Aspose.Words for .NET with this detailed step-by-step guide.
weight: 10
url: /net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Set Footnote And Endnote Position

## Introduction

If you’re working with Word documents and need to manage footnotes and endnotes effectively, Aspose.Words for .NET is your go-to library. This tutorial will walk you through setting footnote and endnote positions in a Word document using Aspose.Words for .NET. We’ll break down each step to make it easy to follow and implement.

## Prerequisites

Before diving into the tutorial, ensure you have the following:

- Aspose.Words for .NET Library: You can download it from [here](https://releases.aspose.com/words/net/).
- Visual Studio: Any recent version will work fine.
- Basic Knowledge of C#: Understanding the basics will help you follow along easily.

## Import Namespaces

First, import the necessary namespaces in your C# project:

```csharp
using System;
using Aspose.Words;
```

## Step 1: Load the Word Document

To start, you need to load your Word document into the Aspose.Words Document object. This will allow you to manipulate the document’s contents.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

In this code, replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where your document is located.

## Step 2: Set Footnote Position

Next, you’ll set the position of the footnotes. Aspose.Words for .NET allows you to position footnotes either at the bottom of the page or beneath the text.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

Here, we’ve set the footnotes to appear beneath the text. If you prefer them at the bottom of the page, use `FootnotePosition.BottomOfPage`.

## Step 3: Set Endnote Position

Similarly, you can set the position of endnotes. Endnotes can be positioned either at the end of the section or at the end of the document.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

In this example, endnotes are placed at the end of each section. To place them at the end of the document, use `EndnotePosition.EndOfDocument`.

## Step 4: Save the Document

Finally, save the document to apply the changes. Ensure you specify the correct file path and name for the output document.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

This line saves the modified document to your specified directory.

## Conclusion

Setting footnote and endnote positions in Word documents using Aspose.Words for .NET is straightforward once you know the steps. By following this guide, you can customize your documents to suit your needs, ensuring that footnotes and endnotes are positioned exactly where you want them.

## FAQ's

### Can I set different positions for individual footnotes or endnotes?

No, Aspose.Words for .NET sets the position for all footnotes and endnotes in a document uniformly.

### Is Aspose.Words for .NET compatible with all versions of Word documents?

Yes, Aspose.Words for .NET supports a wide range of Word document formats, including DOC, DOCX, RTF, and more.

### Can I use Aspose.Words for .NET with other programming languages?

Aspose.Words for .NET is designed for .NET applications, but you can use it with any .NET-supported language like C#, VB.NET, etc.

### Is there a free trial available for Aspose.Words for .NET?

Yes, you can get a free trial [here](https://releases.aspose.com/).

### Where can I find more detailed documentation for Aspose.Words for .NET?

Detailed documentation is available [here](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
