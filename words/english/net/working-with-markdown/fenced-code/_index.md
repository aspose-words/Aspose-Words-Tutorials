---
title: Fenced Code
linktitle: Fenced Code
second_title: Aspose.Words Document Processing API
description: Learn how to add fenced code and info strings to Word documents using Aspose.Words for .NET. Step-by-step guide included. Enhance your document formatting skills.
weight: 10
url: /net/working-with-markdown/fenced-code/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fenced Code

## Introduction

Hey there, fellow coder! Today, we're diving into the world of Aspose.Words for .NET to master the art of adding fenced code and fenced code with info strings to your Word documents. Imagine your Word document as a canvas, and you, the artist, are about to paint with the precision of a seasoned developer. With Aspose.Words, you get the power to programmatically enhance your documents with structured, formatted code blocks, making your technical documents shine with professionalism and clarity.

## Prerequisites

Before we jump into the tutorial, let's make sure you have everything you need:

- Basic knowledge of C#: A general understanding of C# will help you grasp the concepts quickly.
- Aspose.Words for .NET: You need to have Aspose.Words for .NET installed. If you haven't got it yet, grab it [here](https://releases.aspose.com/words/net/).
- Development Environment: Visual Studio or any other C# IDE you're comfortable with.

## Import Namespaces

First things first, you need to import the necessary namespaces. This is like gathering all your tools before starting a project.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Now, let’s break down the process step by step.

## Step 1: Setting Up Your Project

Before we can create beautiful, formatted code blocks in our Word document, we need to set up a new project in Visual Studio.

1. Create a New Project: Open Visual Studio and create a new C# Console Application.
2. Add Aspose.Words Reference: Install Aspose.Words via NuGet Package Manager. You can do this by right-clicking on your project in Solution Explorer, selecting "Manage NuGet Packages," and searching for Aspose.Words.

## Step 2: Initialize the DocumentBuilder

Now that your project is set up, let's initialize the DocumentBuilder, which will be our main tool for adding content to the Word document.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Step 3: Create a Style for Fenced Code

To add fenced code, we first need to create a style. Think of this as setting the theme for our code block.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Step 4: Add Fenced Code to the Document

With our style ready, we can now add a fenced code block to the document.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Step 5: Create a Style for Fenced Code with Info String

Sometimes, you might want to specify the programming language or add extra information to your code block. Let's create a style for that.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Step 6: Add Fenced Code with Info String to the Document

Now, let's add a fenced code block with an info string to indicate that it's C# code.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Conclusion

Congratulations! You've just added fenced code blocks and fenced code with info strings to your Word documents using Aspose.Words for .NET. This is just the tip of the iceberg. With Aspose.Words, you can automate and enhance your document processing to new heights. Keep exploring and happy coding!

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library that allows developers to create, manipulate, and convert Word documents programmatically.

### Can I use Aspose.Words with other programming languages?
Aspose.Words primarily supports .NET languages, but there are versions available for Java, Python, and other languages.

### Is Aspose.Words free to use?
Aspose.Words is a commercial product, but you can download a free trial [here](https://releases.aspose.com/) to explore its features.

### How can I get support for Aspose.Words?
You can get support from the Aspose community and developers [here](https://forum.aspose.com/c/words/8).

### What other features does Aspose.Words offer?
Aspose.Words offers a wide range of features including document conversion, template-based document generation, reporting, and much more.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
