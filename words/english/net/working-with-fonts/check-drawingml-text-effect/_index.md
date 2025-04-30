---
title: Check DrawingML Text Effect
linktitle: Check DrawingML Text Effect
second_title: Aspose.Words Document Processing API
description: Learn how to check DrawingML text effects in Word documents using Aspose.Words for .NET with our detailed, step-by-step guide. Enhance your documents with ease.
weight: 10
url: /net/working-with-fonts/check-drawingml-text-effect/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Check DrawingML Text Effect

## Introduction

Welcome to another detailed tutorial on working with Aspose.Words for .NET! Today, we’re diving into the fascinating world of DrawingML text effects. Whether you're looking to enhance your Word documents with shadows, reflections, or 3D effects, this guide will show you how to check for these text effects in your documents using Aspose.Words for .NET. Let's get started!

## Prerequisites

Before we jump into the tutorial, there are a few prerequisites you'll need to have in place:

- Aspose.Words for .NET Library: Make sure you have the Aspose.Words for .NET library installed. You can download it from the [Aspose releases page](https://releases.aspose.com/words/net/).
- Development Environment: You should have a development environment set up, such as Visual Studio.
- Basic Knowledge of C#: Some familiarity with C# programming will be helpful.

## Import Namespaces

First, you need to import the necessary namespaces. These namespaces will give you access to the classes and methods required to manipulate Word documents and check for DrawingML text effects.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Step-by-Step Guide to Check DrawingML Text Effects

Now, let's break down the process into multiple steps, making it easier to follow along.

## Step 1: Load the Document

The first step is to load the Word document you want to check for DrawingML text effects. 

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

This code snippet loads the document named "DrawingML text effects.docx" from your specified directory.

## Step 2: Access the Runs Collection

Next, we need to access the collection of runs in the first paragraph of the document. Runs are portions of text with the same formatting.

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

This line of code retrieves the runs from the first paragraph in the document's first section.

## Step 3: Get the Font of the First Run

Now, we will get the font properties of the first run in the runs collection. This allows us to check for various DrawingML text effects applied to the text.

```csharp
Font runFont = runs[0].Font;
```

## Step 4: Check for DrawingML Text Effects

Finally, we can check for different DrawingML text effects such as Shadow, 3D Effect, Reflection, Outline, and Fill.

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

These lines of code will print out `true` or `false` depending on whether each specific DrawingML text effect is applied to the run's font.

## Conclusion

Congratulations! You’ve just learned how to check for DrawingML text effects in Word documents using Aspose.Words for .NET. This powerful feature allows you to programmatically detect and manipulate sophisticated text formatting, giving you greater control over your document processing tasks.


## FAQ's

### What is a DrawingML text effect?
DrawingML text effects are advanced text formatting options in Word documents, including shadows, 3D effects, reflections, outlines, and fills.

### Can I apply DrawingML text effects using Aspose.Words for .NET?
Yes, Aspose.Words for .NET allows you to both check for and apply DrawingML text effects programmatically.

### Do I need a license to use Aspose.Words for .NET?
Yes, Aspose.Words for .NET requires a license for full functionality. You can obtain a [temporary license](https://purchase.aspose.com/temporary-license/) for evaluation.

### Is there a free trial available for Aspose.Words for .NET?
Yes, you can download a [free trial](https://releases.aspose.com/) to try out Aspose.Words for .NET before purchasing.

### Where can I find more documentation on Aspose.Words for .NET?
You can find detailed documentation on the [Aspose.Words for .NET Documentation page](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
