---
title: List Keep Source Formatting
linktitle: List Keep Source Formatting
second_title: Aspose.Words Document Processing API
description: Learn how to merge Word documents while preserving formatting using Aspose.Words for .NET. This tutorial provides step-by-step guidance for seamless document merging.
weight: 10
url: /net/join-and-append-documents/list-keep-source-formatting/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# List Keep Source Formatting

## Introduction

In this tutorial, we will explore how to utilize Aspose.Words for .NET to merge documents while preserving the source formatting. This capability is essential for scenarios where maintaining the original appearance of the documents is crucial.

## Prerequisites

Before proceeding, ensure you have the following prerequisites:

- Visual Studio installed on your machine.
- Aspose.Words for .NET installed. You can download it from [here](https://releases.aspose.com/words/net/).
- Basic familiarity with C# programming and .NET environment.

## Import Namespaces

First, import the necessary namespaces into your C# project:

```csharp
using Aspose.Words;
```

## Step 1: Set Up Your Project

Start by creating a new C# project in Visual Studio. Ensure that Aspose.Words for .NET is referenced in your project. If not, you can add it via NuGet Package Manager.

## Step 2: Initialize Document Variables

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Load source and destination documents
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Document destination with list.docx");
```

## Step 3: Configure Section Settings

To maintain continuous flow in the merged document, adjust the section start:

```csharp
srcDoc.FirstSection.PageSetup.SectionStart = SectionStart.Continuous;
```

## Step 4: Merge Documents

Append the content of the source document (`srcDoc`) to the destination document (`dstDoc`) while retaining the original formatting:

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Step 5: Save the Merged Document

Finally, save the merged document to your specified directory:

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.ListKeepSourceFormatting.docx");
```

## Conclusion

In conclusion, merging documents while preserving their original formatting is straightforward with Aspose.Words for .NET. This tutorial has guided you through the process, ensuring that your merged document maintains the source document's layout and styling.

## FAQ's

### What if my documents have different styles?
Aspose.Words handles different styles gracefully, preserving the original formatting as closely as possible.

### Can I merge documents of different formats?
Yes, Aspose.Words supports merging documents of various formats, including DOCX, DOC, RTF, and others.

### Is Aspose.Words compatible with .NET Core?
Yes, Aspose.Words fully supports .NET Core, enabling cross-platform development.

### How can I handle large documents efficiently?
Aspose.Words provides efficient APIs for document manipulation, optimized for performance even with large documents.

### Where can I find more examples and documentation?
You can explore more examples and detailed documentation at [Aspose.Words Documentation](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
