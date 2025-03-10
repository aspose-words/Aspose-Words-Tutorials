---
title: Add Bidi Marks in Word Document
linktitle: Add Bidi Marks in Word Document
second_title: Aspose.Words Document Processing API
description: Learn how to add bidirectional (Bidi) marks in Word documents using Aspose.Words for .NET with this guide. Ensure proper text direction for multi-language content.
weight: 10
url: /net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Add Bidi Marks in Word Document

## Introduction

In the world of document processing, bidirectional (Bidi) text can often be a bit tricky to manage. This is especially true when dealing with languages that have different text directions, such as Arabic or Hebrew. Fortunately, Aspose.Words for .NET makes it easy to handle such scenarios. In this tutorial, we'll walk through how to add Bidi marks to a Word document using Aspose.Words for .NET.

## Prerequisites

Before we dive into the code, make sure you have the following:

1. Aspose.Words for .NET: You need to have Aspose.Words for .NET installed. You can download it from the [Aspose Downloads page](https://releases.aspose.com/words/net/).
2. .NET Framework or .NET Core: Ensure that you have a compatible .NET environment set up for running the examples.
3. Basic Knowledge of C#: Familiarity with C# programming language and basic operations in .NET.

## Import Namespaces

To get started, you need to import the necessary namespaces. Here's how you can include them in your project:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Let’s break down the process of adding Bidi marks in a Word document into clear steps. Each step will guide you through the code and its purpose.

## Step 1: Set Up Your Document

Start by creating a new instance of the `Document` class and a `DocumentBuilder` to add content to the document.

```csharp
// Path to your documents directory
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Create the document and add content
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In this step, you initialize a new Word document and set up a `DocumentBuilder` to facilitate content insertion.

## Step 2: Add Content to Your Document

Next, add some text to your document. Here, we'll add text in different languages to illustrate Bidi text handling.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Here, we first add a standard English phrase. Then, we enable Bidi text formatting for the subsequent text, which is written in Hebrew and Arabic. This demonstrates how to incorporate bidirectional text.

## Step 3: Configure Save Options for Bidi Marks

To ensure that the Bidi marks are correctly saved in the document, you need to configure the `TxtSaveOptions` and enable the `AddBidiMarks` option.

```csharp
// Add Bidi marks
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

In this step, we create an instance of `TxtSaveOptions` and set the `AddBidiMarks` property to `true`. This ensures that the Bidi marks are included when saving the document as a text file.

## Conclusion

Adding Bidi marks to your Word documents can be a crucial step when dealing with multilingual content that includes languages with different text directions. With Aspose.Words for .NET, this process is straightforward and efficient. By following the steps outlined above, you can ensure that your documents correctly represent Bidi text, enhancing readability and accuracy.

## FAQ's

### What are Bidi marks and why are they important?
Bidi marks are special characters used to control the direction of text in documents. They are essential for properly displaying languages that read from right to left, like Arabic and Hebrew.

### Can I use Aspose.Words for .NET to handle other types of text direction issues?
Yes, Aspose.Words for .NET provides comprehensive support for various text direction and formatting needs, including right-to-left and left-to-right languages.

### Is it possible to apply Bidi formatting to specific parts of a document only?
Yes, you can apply Bidi formatting to specific paragraphs or sections of your document as needed.

### What formats can I save the document in with Bidi marks?
In the example provided, the document is saved as a text file. However, Aspose.Words also supports saving documents in various formats while preserving Bidi marks.

### Where can I find more information about Aspose.Words for .NET?
You can explore more about Aspose.Words for .NET through the [Aspose Documentation](https://reference.aspose.com/words/net/) and access the [Support Forum](https://forum.aspose.com/c/words/8) for additional help.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
