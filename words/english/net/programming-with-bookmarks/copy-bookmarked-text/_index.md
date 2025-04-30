---
title: Copy Bookmarked Text In Word Document
linktitle: Copy Bookmarked Text In Word Document
second_title: Aspose.Words Document Processing API
description: Effortlessly copy bookmarked text between Word documents using Aspose.Words for .NET. Learn how with this step-by-step guide.
weight: 10
url: /net/programming-with-bookmarks/copy-bookmarked-text/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Copy Bookmarked Text In Word Document

## Introduction

Ever found yourself needing to copy specific sections from one Word document to another? Well, you're in luck! In this tutorial, we'll walk you through how to copy bookmarked text from one Word document to another using Aspose.Words for .NET. Whether you're building a dynamic report or automating document generation, this guide will simplify the process for you.

## Prerequisites

Before we dive in, make sure you have the following:

- Aspose.Words for .NET Library: You can download it from [here](https://releases.aspose.com/words/net/).
- Development Environment: Visual Studio or any other .NET development environment.
- Basic Knowledge of C#: Familiarity with C# programming and .NET framework.

## Import Namespaces

To start, ensure you have the necessary namespaces imported in your project:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Step 1: Load the Source Document

First things first, you need to load the source document that contains the bookmarked text you want to copy.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Here, `dataDir` is the path to your document directory, and `Bookmarks.docx` is the source document.

## Step 2: Identify the Bookmark

Next, identify the bookmark you wish to copy from the source document.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Replace `"MyBookmark1"` with the actual name of your bookmark.

## Step 3: Create the Destination Document

Now, create a new document where the bookmarked text will be copied.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Step 4: Import Bookmarked Content

To ensure the styles and formatting are preserved, use `NodeImporter` to import the bookmarked content from the source document to the destination document.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Step 5: Define the AppendBookmarkedText Method

Here's where the magic happens. Define a method to handle the copying of the bookmarked text:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Step 6: Save the Destination Document

Finally, save the destination document to verify the copied content.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Conclusion

And that's it! You've successfully copied bookmarked text from one Word document to another using Aspose.Words for .NET. This method is powerful for automating document manipulation tasks, making your workflow more efficient and streamlined.

## FAQ's

### Can I copy multiple bookmarks at once?
Yes, you can iterate through multiple bookmarks and use the same method to copy each one.

### What happens if the bookmark is not found?
The `Range.Bookmarks` property will return `null`, so ensure you handle this case to avoid exceptions.

### Can I preserve the formatting of the original bookmark?
Absolutely! Using `ImportFormatMode.KeepSourceFormatting` ensures that the original formatting is preserved.

### Is there a limit to the size of the bookmarked text?
There's no specific limit, but performance may vary with extremely large documents.

### Can I copy text between different Word document formats?
Yes, Aspose.Words supports various Word formats, and the method works across these formats.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
