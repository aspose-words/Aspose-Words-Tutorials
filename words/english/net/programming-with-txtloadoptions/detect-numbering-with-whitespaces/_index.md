---
title: Detect Numbering With Whitespaces
linktitle: Detect Numbering With Whitespaces
second_title: Aspose.Words Document Processing API
description: Discover how to use Aspose.Words for .NET to detect numbering with whitespaces in plaintext documents and ensure your lists are correctly recognized.
weight: 10
url: /net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Detect Numbering With Whitespaces

## Introduction

Aspose.Words for .NET enthusiasts! Today, we’re diving into a fascinating feature that can make handling lists in plaintext documents a breeze. Have you ever dealt with text files where some lines are supposed to be lists, but they just don’t look quite right when loaded into a Word document? Well, we have a neat trick up our sleeves: detecting numbering with whitespaces. This tutorial will walk you through how to use the `DetectNumberingWithWhitespaces` option in Aspose.Words for .NET to ensure your lists are recognized correctly, even when there’s whitespace between the numbers and the text.

## Prerequisites

Before we get started, make sure you have the following:

- Aspose.Words for .NET: You can download it from the [Aspose Releases](https://releases.aspose.com/words/net/) page.
- Development Environment: Visual Studio or any other C# IDE.
- .NET Framework installed on your machine.
- Basic Knowledge of C#: Understanding the basics will help you follow along with the examples.

## Import Namespaces

Before jumping into the code, ensure you have the necessary namespaces imported in your project. Here’s a quick snippet to get you started:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Let's break down the process into simple, manageable steps. Each step will guide you through the necessary code and explain what’s happening.

## Step 1: Define Your Document Directory

First things first, let’s set up the path to your document directory. This is where your input and output files will be stored.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Step 2: Create a Plaintext Document

Next, we’ll create a plaintext document as a string. This document will contain parts that may be interpreted as lists.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Step 3: Configure LoadOptions

To detect numbering with whitespaces, we need to set the `DetectNumberingWithWhitespaces` option to `true` in a `TxtLoadOptions` object.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Step 4: Load the Document

Now, let's load the document using the `TxtLoadOptions` as a parameter. This ensures that the fourth list (with whitespaces) is detected correctly.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Step 5: Save the Document

Finally, save the document to your specified directory. This will output a Word document with correctly detected lists.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Conclusion

And there you have it! With just a few lines of code, you’ve mastered the art of detecting numbering with whitespaces in plaintext documents using Aspose.Words for .NET. This feature can be incredibly handy when dealing with various text formats and ensuring your lists are accurately represented in your Word documents. So next time you encounter those tricky lists, you’ll know exactly what to do.

## FAQ's

### What is `DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` is an option in `TxtLoadOptions` that allows Aspose.Words to recognize lists even when there is whitespace between the numbering and the list item text.

### Can I use this feature for other delimiters like bullets and brackets?
Yes, Aspose.Words automatically detects lists with common delimiters like bullets and brackets. The `DetectNumberingWithWhitespaces` specifically helps with lists that have whitespace.

### What happens if I don't use `DetectNumberingWithWhitespaces`?
Without this option, lists with whitespace between the numbering and the text might not be recognized as lists, and the items could appear as plain paragraphs.

### Is this feature available in other Aspose products?
This specific feature is tailored for Aspose.Words for .NET, designed to handle Word document processing.

### How can I get a temporary license for Aspose.Words for .NET?
You can obtain a temporary license from the [Aspose Temporary License](https://purchase.aspose.com/temporary-license/) page.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
