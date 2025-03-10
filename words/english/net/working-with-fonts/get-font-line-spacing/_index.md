---
title: Get Font Line Spacing
linktitle: Get Font Line Spacing
second_title: Aspose.Words Document Processing API
description: Learn how to get font line spacing using Aspose.Words for .NET with this step-by-step tutorial. Perfect for developers.
weight: 10
url: /net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Get Font Line Spacing

## Introduction

Aspose.Words for .NET is a powerful library that allows you to create, manipulate, and convert Word documents programmatically. One common task you might need to perform is retrieving the line spacing of a specific font in a document. In this tutorial, we’ll walk you through the process step-by-step, ensuring that you can easily get font line spacing using Aspose.Words for .NET. 

## Prerequisites

Before we dive into the code, make sure you have the following prerequisites in place:

1. Aspose.Words for .NET Library: Download and install the latest version from [here](https://releases.aspose.com/words/net/).
2. Development Environment: Ensure you have an IDE like Visual Studio set up.
3. Basic Knowledge of C#: This tutorial assumes you have a basic understanding of C# programming.

## Import Namespaces

First, you need to import the necessary namespaces in your C# project. These namespaces will allow you to access the Aspose.Words functionalities.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Let's break down the process of getting font line spacing into simple, manageable steps.

## Step 1: Create a New Document

The first step is to create a new Word document instance using Aspose.Words for .NET.

```csharp
Document doc = new Document();
```

## Step 2: Initialize DocumentBuilder

Next, we need to initialize the `DocumentBuilder` object. This object will help us to construct and manipulate the document content.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 3: Set the Font Properties

Now, we set the font properties for the text that we want to insert. For this example, we will use the "Calibri" font.

```csharp
builder.Font.Name = "Calibri";
```

## Step 4: Write Text to the Document

Using the `DocumentBuilder` object, write some text into the document. This text will use the font properties we set in the previous step.

```csharp
builder.Writeln("Sample Text");
```

## Step 5: Retrieve the Font Object

To get the line spacing, we need to access the font object of the text we just added. This can be done by navigating through the document structure to the first paragraph run.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Step 6: Get the Line Spacing

Finally, we retrieve the line spacing from the font object and print it to the console.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Conclusion

And there you have it! Retrieving the font line spacing using Aspose.Words for .NET is straightforward when you break it down into these simple steps. Whether you are creating a new document or working with an existing one, Aspose.Words provides all the tools you need to manage font properties efficiently.

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library that allows developers to create, manipulate, and convert Word documents programmatically using C#.

### Can I use Aspose.Words for .NET in other .NET languages?
Yes, you can use Aspose.Words for .NET with any .NET language, including VB.NET and F#.

### How can I download Aspose.Words for .NET?
You can download the latest version of Aspose.Words for .NET from [here](https://releases.aspose.com/words/net/).

### Is there a free trial available for Aspose.Words for .NET?
Yes, you can get a free trial from [here](https://releases.aspose.com/).

### Where can I find the documentation for Aspose.Words for .NET?
The documentation for Aspose.Words for .NET is available [here](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
