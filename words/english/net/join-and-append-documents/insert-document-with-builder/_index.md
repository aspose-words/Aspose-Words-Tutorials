---
title: Insert Document With Builder
linktitle: Insert Document With Builder
second_title: Aspose.Words Document Processing API
description: Learn how to merge two Word documents using Aspose.Words for .NET. Step-by-step guide to insert a document with DocumentBuilder and preserve formatting.
weight: 10
url: /net/join-and-append-documents/insert-document-with-builder/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insert Document With Builder

## Introduction

So, you’ve got two Word documents, and you’re looking to merge them into one. You might be thinking, "Is there an easy way to do this programmatically?" Absolutely! Today, I’m going to walk you through the process of inserting one document into another using the Aspose.Words for .NET library. This method is super handy, especially when you’re dealing with large documents or need to automate the process. Let’s dive right in!

## Prerequisites

Before we get started, let’s ensure you’ve got everything you need:

1. Aspose.Words for .NET: If you haven’t already, you can download it from [here](https://releases.aspose.com/words/net/).
2. Development Environment: Make sure you have Visual Studio or any other suitable IDE installed.
3. Basic Knowledge of C#: A little familiarity with C# will go a long way.

## Import Namespaces

First things first, you need to import the necessary namespaces to access the Aspose.Words library functionalities. Here’s how you can do it:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Now that we have our prerequisites in place, let's break down the process step-by-step.

## Step 1: Setting Up Your Document Directory

Before we begin coding, you need to set the path to your document directory. This is where your source and destination documents are stored.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where your documents are located. This will help the program find your files easily.

## Step 2: Loading the Source and Destination Documents

Next, we need to load the documents we want to work with. In this example, we have a source document and a destination document.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

Here, we’re using the `Document` class from the Aspose.Words library to load our documents. Make sure the file names match those in your directory.

## Step 3: Creating a DocumentBuilder Object

The `DocumentBuilder` class is a powerful tool in the Aspose.Words library. It allows us to navigate and manipulate the document.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

In this step, we’ve created a `DocumentBuilder` object for our destination document. This will help us insert content into the document.

## Step 4: Moving to the End of the Document

We need to move the builder cursor to the end of the destination document before inserting the source document.

```csharp
builder.MoveToDocumentEnd();
```

This ensures that the source document is inserted at the end of the destination document.

## Step 5: Inserting a Page Break

To keep things neat, let’s add a page break before inserting the source document. This will start the content of the source document on a new page.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

A page break ensures that the source document content starts on a new page, making the merged document look professional.

## Step 6: Inserting the Source Document

Now comes the exciting part—actually inserting the source document into the destination document.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

Using the `InsertDocument` method, we can insert the entire source document into the destination document. The `ImportFormatMode.KeepSourceFormatting` ensures that the formatting of the source document is preserved.

## Step 7: Saving the Merged Document

Finally, let’s save the merged document. This will combine the source and destination documents into one file.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

By saving the document, we complete the process of merging the two documents. Your new document is now ready and saved in the specified directory.

## Conclusion

And there you have it! You’ve successfully inserted one document into another using Aspose.Words for .NET. This method is not only efficient but also preserves the formatting of both documents, ensuring a seamless merge. Whether you’re working on a one-time project or need to automate document processing, Aspose.Words for .NET has got you covered.

## FAQ's

### What is Aspose.Words for .NET?  
Aspose.Words for .NET is a powerful library that allows developers to create, edit, convert, and manipulate Word documents programmatically.

### Can I keep the formatting of the source document?  
Yes, by using `ImportFormatMode.KeepSourceFormatting`, the formatting of the source document is preserved when it’s inserted into the destination document.

### Do I need a license to use Aspose.Words for .NET?  
Yes, Aspose.Words for .NET requires a license for full functionality. You can get a [temporary license](https://purchase.aspose.com/temporary-license/) for evaluation.

### Can I automate this process?  
Absolutely! The method described can be incorporated into larger applications to automate document processing tasks.

### Where can I find more resources and support?  
For more information, you can check the [documentation](https://reference.aspose.com/words/net/), or visit the [support forum](https://forum.aspose.com/c/words/8) for assistance.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
