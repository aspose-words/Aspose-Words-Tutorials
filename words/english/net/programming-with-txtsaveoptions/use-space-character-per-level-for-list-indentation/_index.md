---
title: Use Space Character Per Level For List Indentation
linktitle: Use Space Character Per Level For List Indentation
second_title: Aspose.Words Document Processing API
description: Learn how to create multi-level lists with space character indentation in Aspose.Words for .NET. Step-by-step guide for precise document formatting.
weight: 10
url: /net/programming-with-txtsaveoptions/use-space-character-per-level-for-list-indentation/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Use Space Character Per Level For List Indentation

## Introduction

When it comes to document formatting, especially when working with lists, precision is key. In scenarios where you need to create documents with various levels of indentation, Aspose.Words for .NET offers powerful tools to handle this task. One particular feature that can come in handy is configuring list indentation in text files. This guide will walk you through how to use space characters for list indentation, ensuring your document maintains the desired structure and readability.

## Prerequisites

Before diving into the tutorial, here’s what you’ll need:

- Aspose.Words for .NET: Ensure you have the Aspose.Words library installed. If you don’t have it yet, you can download it from the [Aspose website](https://releases.aspose.com/words/net/).
- Visual Studio: A development environment to write and test your code.
- Basic Understanding of C#: Familiarity with C# and .NET framework will help you follow along smoothly.

## Import Namespaces

To start working with Aspose.Words, you'll need to import the necessary namespaces. Here's how you can include them in your project:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Let's break down the process of creating a document with a multi-level list and specifying space characters for indentation. 

## Step 1: Set Up Your Document

First, you'll need to create a new document and initialize the `DocumentBuilder` object. This object will allow you to easily add content and format it as needed.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Create the document and add content
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

In this snippet, replace `"YOUR DOCUMENTS DIRECTORY"` with the actual path where you want to save your document.

## Step 2: Create a List with Multiple Levels of Indentation

With the `DocumentBuilder` instance, you can now create a list with different levels of indentation. Use the `ListFormat` property to apply numbering and indent the list items as required.

```csharp
// Create a list with three levels of indentation
builder.ListFormat.ApplyNumberDefault();
builder.Write("Element 1");
builder.ListFormat.ListIndent();
builder.Write("Element 2");
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

In this step, `ApplyNumberDefault` sets up the list format, and `ListIndent` is used to increase the indentation level for each subsequent list item.

## Step 3: Configure Space Character for Indentation

Now that you have your list set up, the next step is to configure how the list indentation is handled when saving the document to a text file. You’ll use `TxtSaveOptions` to specify that space characters should be used for indentation.

```csharp
// Use one space character per level for list indentation
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 3;
saveOptions.ListIndentation.Character = ' ';
```

Here, `ListIndentation.Count` specifies the number of space characters per indentation level, and `ListIndentation.Character` sets the actual character used for indentation.

## Step 4: Save the Document with the Specified Options

Finally, save your document using the configured options. This will apply the indentation settings and save your file in the desired format.

```csharp
// Save the document with the specified options
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
```

This code snippet saves the document to the path specified in `dataDir` with the file name `"WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt"`. The saved file will have the list formatted according to your indentation settings.

## Conclusion

By following these steps, you've successfully created a document with multi-level list indentation using space characters for formatting. This approach ensures that your lists are well-structured and easy to read, even when saved as text files. Aspose.Words for .NET provides robust tools for document manipulation, and mastering these features can significantly enhance your document processing workflows.

## FAQ's

### Can I use different characters for list indentation besides spaces?
Yes, you can specify different characters for list indentation by setting the `Character` property in `TxtSaveOptions`.

### How do I apply bullet points instead of numbers in lists?
Use `ListFormat.ApplyBulletDefault()` instead of `ApplyNumberDefault()` to create a bulleted list.

### Can I adjust the number of spaces for indentation dynamically?
Yes, you can adjust the `ListIndentation.Count` property to set the number of spaces based on your requirements.

### Is it possible to change list indentation after the document is created?
Yes, you can modify list formatting and indentation settings at any time before saving the document.

### What other document formats support list indentation settings?
Besides text files, list indentation settings can be applied to other formats such as DOCX, PDF, and HTML when using Aspose.Words.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
