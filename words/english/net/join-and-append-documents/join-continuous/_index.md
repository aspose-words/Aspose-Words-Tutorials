---
title: Join Continuous
linktitle: Join Continuous
second_title: Aspose.Words Document Processing API
description: Learn how to seamlessly join two Word documents using Aspose.Words for .NET. Follow our step-by-step guide for a smooth and efficient document merge.
weight: 10
url: /net/join-and-append-documents/join-continuous/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Join Continuous

## Introduction

Are you looking to seamlessly merge two Word documents into one without any breaks? Aspose.Words for .NET offers a fantastic way to achieve this by using the Continuous Section Break feature. This tutorial will guide you step-by-step through the process, ensuring you can easily join documents without any hassle. Let's dive in!

## Prerequisites

Before we get started, let's ensure you have everything you need:

- Aspose.Words for .NET: If you haven't already, download and install [Aspose.Words for .NET](https://releases.aspose.com/words/net/).
- Development Environment: You can use Visual Studio or any other .NET development environment.
- Sample Documents: Have two Word documents ready that you want to merge.

## Import Namespaces

To use Aspose.Words for .NET, you need to import the necessary namespaces in your project. Here's how you do it:

```csharp
using Aspose.Words;
```

Now, let's break down the example into multiple steps for clarity.

## Step 1: Set Up Your Document Directory

First, we need to set up the directory where your documents are stored. This will allow our code to locate the files we want to merge.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where your documents are stored.

## Step 2: Load the Source and Destination Documents

Next, we'll load the source and destination documents into our program. These are the two documents you want to merge.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Ensure that the filenames and paths match the actual files you want to use.

## Step 3: Set Section Start as Continuous

To make the content of the source document appear immediately after the destination document, we need to set the `SectionStart` property of the first section in the source document to `Continuous`.

```csharp
// Make the document appear straight after the destination document's content.
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

This ensures there are no breaks between the documents when they are merged.

## Step 4: Append the Source Document

Now, we append the source document to the destination document. This step ensures that the content from the source document is added to the end of the destination document.

```csharp
// Append the source document using the original styles found in the source document.
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

Using `ImportFormatMode.KeepSourceFormatting` ensures that the formatting from the source document is preserved in the final merged document.

## Step 5: Save the Merged Document

Finally, we save the merged document to the specified directory. This completes the process of joining the documents.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.JoinContinuous.docx");
```

Make sure the path and filename are correct for your needs.

## Conclusion

And there you have it! With just a few lines of code, you've successfully merged two Word documents into one continuous document using Aspose.Words for .NET. This process is not only simple but also highly efficient, ensuring that your documents retain their original formatting.

## FAQ's

### Can I merge more than two documents?
Yes, you can repeat the process to merge multiple documents by loading additional documents and appending them sequentially.

### Will the original formatting be preserved?
Yes, using `ImportFormatMode.KeepSourceFormatting` ensures that the formatting from the source document is preserved.

### Is Aspose.Words for .NET compatible with .NET Core?
Yes, Aspose.Words for .NET is compatible with both .NET Framework and .NET Core.

### Can I merge documents with different page setups?
Yes, but you might need to adjust the page setup properties to ensure a seamless merge.

### Where can I get support if I encounter issues?
You can get support from the Aspose community forum [here](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
