---
title: Keep Source Numbering
linktitle: Keep Source Numbering
second_title: Aspose.Words Document Processing API
description: Learn how to import documents while preserving formatting using Aspose.Words for .NET. Step-by-step guide with code examples.
weight: 10
url: /net/join-and-append-documents/keep-source-numbering/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Keep Source Numbering

## Introduction

When working with Aspose.Words for .NET, importing documents from one source to another while preserving formatting can be efficiently handled using the `NodeImporter` class. This tutorial will guide you through the process step-by-step.

## Prerequisites

Before starting, ensure you have the following:
- Visual Studio installed on your machine.
- Aspose.Words for .NET installed. If not, download it from [here](https://releases.aspose.com/words/net/).
- Basic knowledge of C# and .NET programming.

## Import Namespaces

First, include the necessary namespaces in your project:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Step 1: Set Up Your Project

Begin by creating a new C# project in Visual Studio and install Aspose.Words via NuGet Package Manager.

## Step 2: Initialize Documents
Create instances of the source (`srcDoc`) and destination (`dstDoc`) documents.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Step 3: Configure Import Options
Set up import options to maintain source formatting, including numbered paragraphs.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Step 4: Import Paragraphs
Iterate through paragraphs in the source document and import them into the destination document.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Step 5: Save the Document
Save the merged document to your desired location.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Conclusion

In conclusion, using Aspose.Words for .NET to import documents while preserving formatting is straightforward with the `NodeImporter` class. This method ensures that your documents maintain their original appearance and structure seamlessly.

## FAQ's

### Can I import documents with different formatting styles?
Yes, the `NodeImporter` class supports importing documents with varied formatting styles.

### What if my documents contain complex tables and images?
Aspose.Words for .NET handles complex structures like tables and images during import operations.

### Is Aspose.Words compatible with all versions of .NET?
Aspose.Words supports .NET Framework and .NET Core versions for seamless integration.

### How can I handle errors during document import?
Use try-catch blocks to handle exceptions that may occur during the import process.

### Where can I find more detailed documentation on Aspose.Words for .NET?
Visit the [documentation](https://reference.aspose.com/words/net/) for comprehensive guides and API references.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
