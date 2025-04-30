---
title: Append Bookmarked Text In Word Document
linktitle: Append Bookmarked Text In Word Document
second_title: Aspose.Words Document Processing API
description: Learn how to append bookmarked text in a Word document using Aspose.Words for .NET with this step-by-step guide. Perfect for developers.
weight: 10
url: /net/programming-with-bookmarks/append-bookmarked-text/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Append Bookmarked Text In Word Document

## Introduction

Hey there! Ever tried to append text from a bookmarked section in a Word document and found it tricky? You're in luck! This tutorial will walk you through the process using Aspose.Words for .NET. We’ll break it down into simple steps so you can follow along easily. Let's dive in and get that bookmarked text appended like a pro!

## Prerequisites

Before we get started, let's make sure you have everything you need:

- Aspose.Words for .NET: Make sure you have it installed. If not, you can [download it here](https://releases.aspose.com/words/net/).
- Development Environment: Any .NET development environment like Visual Studio.
- Basic Knowledge of C#: Understanding basic C# programming concepts will help.
- Word Document with Bookmarks: A Word document with bookmarks set up, which we'll use to append text from.

## Import Namespaces

First things first, let's import the necessary namespaces. This will ensure we have all the tools we need at our fingertips.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

Let's break down the example into detailed steps.

## Step 1: Load the Document and Initialize Variables

Alright, let's start by loading our Word document and initializing the variables we’ll need.

```csharp
// Load the source and destination documents.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Initialize the document importer.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Find the bookmark in the source document.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Step 2: Identify the Start and End Paragraphs

Now, let's locate the paragraphs where the bookmark starts and ends. This is crucial as we need to handle the text within these bounds.

```csharp
// This is the paragraph that contains the beginning of the bookmark.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

// This is the paragraph that contains the end of the bookmark.
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## Step 3: Validate Paragraph Parents

We need to ensure the start and end paragraphs have the same parent. This is a simple scenario to keep things straightforward.

```csharp
// Limit ourselves to a reasonably simple scenario.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## Step 4: Identify the Node to Stop

Next, we need to determine the node where we'll stop copying text. This will be the node immediately after the end paragraph.

```csharp
// We want to copy all paragraphs from the start paragraph up to (and including) the end paragraph,
// therefore the node at which we stop is one after the end paragraph.
Node endNode = endPara.NextSibling;
```

## Step 5: Append Bookmarked Text to Destination Document

Finally, let's loop through the nodes from the start paragraph to the node after the end paragraph, and append them to the destination document.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // This creates a copy of the current node and imports it (makes it valid) in the context
    // of the destination document. Importing means adjusting styles and list identifiers correctly.
    Node newNode = importer.ImportNode(curNode, true);

    // Append the imported node to the destination document.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Save the destination document with the appended text.
dstDoc.Save("appended_document.docx");
```

## Conclusion

And there you have it! You've successfully appended text from a bookmarked section in a Word document using Aspose.Words for .NET. This powerful tool makes document manipulation a breeze, and now you have one more trick up your sleeve. Happy coding!

## FAQ's

### Can I append text from multiple bookmarks in one go?
Yes, you can repeat the process for each bookmark and append the text accordingly.

### What if the start and end paragraphs have different parents?
The current example assumes they have the same parent. For different parents, a more complex handling is required.

### Can I keep the original formatting of the appended text?
Absolutely! The `ImportFormatMode.KeepSourceFormatting` ensures the original formatting is preserved.

### Is it possible to append text to a specific position in the destination document?
Yes, you can append the text to any position by navigating to the desired node in the destination document.

### What if I need to append text from a bookmark to a new section?
You can create a new section in the destination document and append the text there.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
