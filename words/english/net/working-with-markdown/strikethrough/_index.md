---
title: Strikethrough
linktitle: Strikethrough
second_title: Aspose.Words Document Processing API
description: Learn how to apply strikethrough formatting to text using Aspose.Words for .NET with our step-by-step guide. Enhance your document processing skills.
weight: 10
url: /net/working-with-markdown/strikethrough/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Strikethrough

## Introduction

Welcome to this detailed guide on how to apply strikethrough formatting to text using Aspose.Words for .NET. If you're looking to enhance your document processing skills and add a unique touch to your text, you're in the right place. Let's dive in!

## Prerequisites

Before we get started, ensure you have the following:

- Aspose.Words for .NET: Download it [here](https://releases.aspose.com/words/net/).
- .NET Framework: Make sure you have .NET Framework installed on your system.
- Development Environment: An IDE like Visual Studio.
- Basic Knowledge of C#: Familiarity with C# programming is necessary.

## Import Namespaces

To begin, you'll need to import the necessary namespaces. These are essential for accessing the Aspose.Words library and its features.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Step 1: Initialize the DocumentBuilder

The `DocumentBuilder` class is a powerful tool in Aspose.Words that allows you to add content to your document with ease.

```csharp
// Initialize a DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Step 2: Set Strikethrough Property

Now, let’s apply the strikethrough property to our text. This involves setting the `StrikeThrough` property of the `Font` object to `true`.

```csharp
// Make the text Strikethrough.
builder.Font.StrikeThrough = true;
```

## Step 3: Write Text with Strikethrough

With the strikethrough property set, we can now add our text. The `Writeln` method will add the text to the document.

```csharp
// Write text with Strikethrough.
builder.Writeln("This text will be StrikeThrough");
```

## Conclusion

And there you have it! You’ve successfully added strikethrough formatting to your text using Aspose.Words for .NET. This powerful library opens up a world of possibilities for document processing and customization. Whether you're creating reports, letters, or any other type of document, mastering these features will undoubtedly enhance your productivity and the quality of your outputs.

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful document processing library that allows developers to create, manipulate, and convert Word documents programmatically.

### Can I use Aspose.Words for .NET in a commercial project?
Yes, you can use Aspose.Words for .NET in commercial projects. For purchasing options, visit the [buy page](https://purchase.aspose.com/buy).

### Is there a free trial available for Aspose.Words for .NET?
Yes, you can download a free trial [here](https://releases.aspose.com/).

### How do I get support for Aspose.Words for .NET?
You can get support from the Aspose community and experts on the [support forum](https://forum.aspose.com/c/words/8).

### Can I apply other text formatting options using Aspose.Words for .NET?
Absolutely! Aspose.Words for .NET supports a wide range of text formatting options including bold, italics, underline, and more.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
