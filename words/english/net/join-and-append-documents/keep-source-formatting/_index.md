---
title: Keep Source Formatting
linktitle: Keep Source Formatting
second_title: Aspose.Words Document Processing API
description: Learn how to merge Word documents while preserving formatting using Aspose.Words for .NET. Ideal for developers looking to automate document assembly tasks.
weight: 10
url: /net/join-and-append-documents/keep-source-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Keep Source Formatting

## Introduction

In this tutorial, we will explore how to merge and append Word documents using Aspose.Words for .NET. This powerful library provides developers with extensive capabilities for manipulating Word documents programmatically. We'll focus on the method to keep the source formatting intact during document merging, ensuring that the original styles and layouts are preserved seamlessly.

## Prerequisites

Before diving into the tutorial, ensure you have the following prerequisites set up:

- Development Environment: Visual Studio or any IDE that supports .NET development.
- Aspose.Words for .NET Library: Download and install the library from [here](https://releases.aspose.com/words/net/).
- Basic Knowledge of C# Programming: Familiarity with C# syntax and object-oriented programming concepts.

## Import Namespaces

Start by importing the necessary namespaces in your C# project:

```csharp
using Aspose.Words;
```

## Step 1: Set Up Your Project

Create a new C# console application in Visual Studio and install the Aspose.Words NuGet package. This package contains the libraries needed to work with Word documents in your project.

## Step 2: Include Aspose.Words Namespace

Ensure you include the Aspose.Words namespace at the beginning of your C# file to access the Aspose.Words classes and methods.

## Step 3: Initialize Document Paths

Define the path to your document directory where the source and destination documents are located.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Step 4: Create Destination Document

Initialize a new instance of the Document class to create a destination document where the merged content will be stored.

```csharp
Document dstDoc = new Document();
```

## Step 5: Load Source Document

Similarly, create another Document object to load the source document that you want to append to the destination document.

```csharp
Document srcDoc = new Document();
```

## Step 6: Append Source Document with Keeping Formatting

To merge the source document into the destination document while preserving its original formatting, use the AppendDocument method with ImportFormatMode set to KeepSourceFormatting.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Step 7: Save the Merged Document

Finally, save the merged document to the specified directory using the Save method.

```csharp
dstDoc.Save(dataDir + "MergedDocument.docx");
```

## Conclusion

In this tutorial, we've covered how to merge Word documents while maintaining the original formatting using Aspose.Words for .NET. This approach ensures that styles, fonts, and layouts from the source documents are seamlessly integrated into the destination document, providing a robust solution for document assembly tasks.

## FAQ's

### Can I merge multiple documents in one operation using Aspose.Words for .NET?
Yes, you can merge multiple documents by sequentially appending each document to the destination document.

### Does Aspose.Words preserve all formatting attributes during document merging?
Aspose.Words supports various import modes; the KeepSourceFormatting mode ensures that most formatting attributes are retained.

### Is Aspose.Words compatible with .NET Core applications?
Yes, Aspose.Words supports .NET Core, allowing you to use it across different platforms.

### How can I handle large documents efficiently using Aspose.Words?
Aspose.Words provides efficient APIs for working with large documents, including features for pagination and memory management.

### Where can I find more resources and support for Aspose.Words?
Visit the [Aspose.Words for .NET documentation](https://reference.aspose.com/words/net/) for detailed API references, examples, and guides.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
