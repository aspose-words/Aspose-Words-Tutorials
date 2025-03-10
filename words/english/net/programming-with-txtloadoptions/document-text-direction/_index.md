---
title: Document Text Direction
linktitle: Document Text Direction
second_title: Aspose.Words Document Processing API
description: Learn how to set document text direction in Word using Aspose.Words for .NET with this step-by-step guide. Perfect for handling right-to-left languages.
weight: 10
url: /net/programming-with-txtloadoptions/document-text-direction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Document Text Direction

## Introduction

When working with Word documents, especially those containing multiple languages or special formatting needs, setting the text direction can be crucial. For instance, when dealing with right-to-left languages such as Hebrew or Arabic, you might need to adjust the text direction accordingly. In this guide, we'll walk through how to set the document text direction using Aspose.Words for .NET. 

## Prerequisites

Before we dive into the code, make sure you have the following:

- Aspose.Words for .NET Library: Ensure you have Aspose.Words for .NET installed. You can download it from the [Aspose website](https://releases.aspose.com/words/net/).
- Visual Studio: A development environment for writing and executing C# code.
- Basic Knowledge of C#: Familiarity with C# programming will be beneficial as we’ll be writing some code.

## Import Namespaces

To begin, you'll need to import the necessary namespaces for working with Aspose.Words in your project. Here's how you can do it:

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
```

These namespaces provide access to the classes and methods needed to manipulate Word documents.

## Step 1: Define the Path to Your Document Directory

First, set up the path to where your document is located. This is crucial for loading and saving files correctly.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where your document is stored.

## Step 2: Create TxtLoadOptions with Document Direction Setting

Next, you'll need to create an instance of `TxtLoadOptions` and set its `DocumentDirection` property. This tells Aspose.Words how to handle the direction of text in the document.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DocumentDirection = DocumentDirection.Auto };
```

In this example, we use `DocumentDirection.Auto` to let Aspose.Words automatically determine the direction based on the content.

## Step 3: Load the Document

Now, load the document using the `Document` class and the previously defined `loadOptions`.

```csharp
Document doc = new Document(dataDir + "Hebrew text.txt", loadOptions);
```

Here, `"Hebrew text.txt"` is the name of your text file. Ensure this file exists in your specified directory.

## Step 4: Access and Check the Paragraph's Bidirectional Formatting

To confirm that the text direction is correctly set, access the first paragraph of the document and check its bidirectional formatting.

```csharp
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;
Console.WriteLine(paragraph.ParagraphFormat.Bidi);
```

This step is useful for debugging and verifying that the document's text direction has been applied as expected.

## Step 5: Save the Document with the New Settings

Finally, save the document to apply and persist the changes.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
```

Here, `"WorkingWithTxtLoadOptions.DocumentTextDirection.docx"` is the name of the output file. Make sure to choose a name that reflects the changes you've made.

## Conclusion

Setting the text direction in Word documents is a straightforward process with Aspose.Words for .NET. By following these steps, you can easily configure how your document handles right-to-left or left-to-right text. Whether you're working with multilingual documents or need to format text direction for specific languages, Aspose.Words provides a robust solution to meet your needs.

## FAQ's

### What is the `DocumentDirection` property used for?

The `DocumentDirection` property in `TxtLoadOptions` determines the text direction for the document. It can be set to `DocumentDirection.Auto`, `DocumentDirection.LeftToRight`, or `DocumentDirection.RightToLeft`.

### Can I set the text direction for specific paragraphs instead of the whole document?

Yes, you can set text direction for specific paragraphs using the `ParagraphFormat.Bidi` property, but the `TxtLoadOptions.DocumentDirection` property sets the default direction for the entire document.

### What file formats are supported for loading with `TxtLoadOptions`?

`TxtLoadOptions` is used primarily for loading text files (.txt). For other file formats, use different classes like `DocLoadOptions` or `DocxLoadOptions`.

### How can I handle documents with mixed text directions?

For documents with mixed text directions, you may need to handle the formatting on a per-paragraph basis. Use the `ParagraphFormat.Bidi` property to adjust each paragraph's direction as needed.

### Where can I find more information about Aspose.Words for .NET?

For more details, check out the [Aspose.Words for .NET Documentation](https://reference.aspose.com/words/net/). You can also explore additional resources like [Download link](https://releases.aspose.com/words/net/), [Buy](https://purchase.aspose.com/buy), [Free trial](https://releases.aspose.com/), [Temporary license](https://purchase.aspose.com/temporary-license/), and [Support](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
