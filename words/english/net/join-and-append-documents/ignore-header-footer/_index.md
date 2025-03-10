---
title: Ignore Header Footer
linktitle: Ignore Header Footer
second_title: Aspose.Words Document Processing API
description: Learn how to merge Word documents while ignoring headers and footers using Aspose.Words for .NET with this step-by-step guide.
weight: 10
url: /net/join-and-append-documents/ignore-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ignore Header Footer

## Introduction

Merging Word documents can sometimes be a bit tricky, especially when you want to keep some parts intact while ignoring others, like headers and footers. Luckily, Aspose.Words for .NET provides an elegant way to handle this. In this tutorial, I'll walk you through the process step-by-step, ensuring you understand every part. We'll keep it light, conversational, and engaging, just like chatting with a friend. Ready? Let's dive in!

## Prerequisites

Before we get started, let's make sure we have everything we need:

- Aspose.Words for .NET: You can download it from [here](https://releases.aspose.com/words/net/).
- Visual Studio: Any recent version should work.
- Basic Understanding of C#: Don't worry, I'll guide you through the code.
- Two Word Documents: One to be appended to the other.

## Import Namespaces

First things first, we need to import the necessary namespaces in our C# project. This is crucial as it allows us to use Aspose.Words classes and methods without constantly referencing the full namespace.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Step 1: Set Up Your Project

### Create a New Project

Let's start by creating a new Console App project in Visual Studio.

1. Open Visual Studio.
2. Select "Create a new project".
3. Choose "Console App (.NET Core)".
4. Name your project and click "Create".

### Install Aspose.Words for .NET

Next, we need to add Aspose.Words for .NET to our project. You can do this via NuGet Package Manager:

1. Right-click on your project in the Solution Explorer.
2. Select "Manage NuGet Packages".
3. Search for "Aspose.Words" and install it.

## Step 2: Load Your Documents

Now that our project is set up, let's load the Word documents that we want to merge. For the sake of this tutorial, we'll call them "Document source.docx" and "Northwind traders.docx".

Here's how you load them using Aspose.Words:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDocument = new Document(dataDir + "Document source.docx");
Document dstDocument = new Document(dataDir + "Northwind traders.docx");
```

This code snippet sets the path to your document directory and loads the documents into memory.

## Step 3: Configure Import Options

Before merging the documents, we need to set up our import options. This step is essential because it allows us to specify that we want to ignore headers and footers.

Here's the code to configure the import options:

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { IgnoreHeaderFooter = true };
```

By setting `IgnoreHeaderFooter` to `true`, we're telling Aspose.Words to ignore headers and footers during the merge process.

## Step 4: Merge the Documents

With our documents loaded and import options configured, it's time to merge the documents.

Here's how to do it:

```csharp
dstDocument.AppendDocument(srcDocument, ImportFormatMode.KeepSourceFormatting, importFormatOptions);
```

This line of code appends the source document to the destination document while keeping the source formatting and ignoring headers and footers.

## Step 5: Save the Merged Document

Finally, we need to save the merged document. 

Here's the code to save your merged document:

```csharp
dstDocument.Save(dataDir + "JoinAndAppendDocuments.IgnoreHeaderFooter.docx");
```

This will save the merged document in the specified directory with the filename "JoinAndAppendDocuments.IgnoreHeaderFooter.docx".

## Conclusion

And there you have it! You've successfully merged two Word documents while ignoring their headers and footers using Aspose.Words for .NET. This method is handy for various document management tasks where maintaining specific document sections is crucial.

Working with Aspose.Words for .NET can significantly streamline your document processing workflows. Remember, if you ever get stuck or need more information, you can always check out the [documentation](https://reference.aspose.com/words/net/).

## FAQ's

### Can I ignore other parts of the document besides headers and footers?

Yes, Aspose.Words provides various options to customize the import process, including ignoring different sections and formatting.

### Is it possible to keep the headers and footers instead of ignoring them?

Absolutely. Simply set `IgnoreHeaderFooter` to `false` in the `ImportFormatOptions`.

### Do I need a license to use Aspose.Words for .NET?

Yes, Aspose.Words for .NET is a commercial product. You can get a [free trial](https://releases.aspose.com/) or purchase a license [here](https://purchase.aspose.com/buy).

### Can I merge more than two documents using this method?

Yes, you can append multiple documents in a loop by repeating the `AppendDocument` method for each additional document.

### Where can I find more examples and documentation for Aspose.Words for .NET?

You can find comprehensive documentation and examples on the [Aspose website](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
