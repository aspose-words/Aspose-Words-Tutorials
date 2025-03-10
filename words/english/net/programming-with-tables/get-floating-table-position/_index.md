---
title: Get Floating Table Position
linktitle: Get Floating Table Position
second_title: Aspose.Words Document Processing API
description: Learn how to get floating table positions in Word documents using Aspose.Words for .NET. This detailed, step-by-step guide will walk you through everything you need to know.
weight: 10
url: /net/programming-with-tables/get-floating-table-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Get Floating Table Position

## Introduction

Are you ready to dive into the world of Aspose.Words for .NET? Today, we’re going to take you on a journey to uncover the secrets of floating tables in Word documents. Imagine you have a table that doesn’t just sit still but elegantly floats around the text. Pretty cool, right? This tutorial will walk you through how to get the positioning properties of such floating tables. So, let’s get started!

## Prerequisites

Before we jump into the fun part, there are a few things you need to have in place:

1. Aspose.Words for .NET: If you haven’t already, download and install Aspose.Words for .NET from the [Aspose releases page](https://releases.aspose.com/words/net/).
2. Development Environment: Make sure you have a .NET development environment set up. Visual Studio is a great option.
3. Sample Document: You’ll need a Word document with a floating table. You can create one or use an existing document. 

## Import Namespaces

To get started, you need to import the necessary namespaces. This ensures that you have access to the Aspose.Words classes and methods required for manipulating Word documents.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Alright, let’s break down the process into easy-to-follow steps.

## Step 1: Load Your Document

First things first, you need to load your Word document. This document should contain the floating table you want to examine.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

In this step, you’re essentially telling Aspose.Words where to find your document. Make sure to replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your document.

## Step 2: Access the Tables in the Document

Next, you need to access the tables within the document’s first section. Think of the document as a big container, and you’re digging into it to find all the tables.

```csharp
foreach (Table table in doc.FirstSection.Body.Tables)
{
    // Your code to process each table goes here
}
```

Here, you’re looping through each table found in the body of the first section of your document.

## Step 3: Check if the Table is Floating

Now, you need to determine if the table is a floating type. Floating tables have specific text wrapping settings.

```csharp
if (table.TextWrapping == TextWrapping.Around)
{
    // Your code to print table positioning properties goes here
}
```

This condition checks if the table’s text wrapping style is set to “Around,” which indicates that it’s a floating table.

## Step 4: Print the Positioning Properties

Finally, let’s extract and print the positioning properties of the floating table. These properties tell you where the table is positioned in relation to the text and page.

```csharp
if (table.TextWrapping == TextWrapping.Around)
{
    Console.WriteLine("Horizontal Anchor: " + table.HorizontalAnchor);
    Console.WriteLine("Vertical Anchor: " + table.VerticalAnchor);
    Console.WriteLine("Absolute Horizontal Distance: " + table.AbsoluteHorizontalDistance);
    Console.WriteLine("Absolute Vertical Distance: " + table.AbsoluteVerticalDistance);
    Console.WriteLine("Allow Overlap: " + table.AllowOverlap);
    Console.WriteLine("Relative Vertical Alignment: " + table.RelativeVerticalAlignment);
    Console.WriteLine("..............................");
}
```

These properties give you a detailed look at how the table is anchored and positioned within the document.

## Conclusion

And there you have it! By following these steps, you can easily retrieve and print the positioning properties of floating tables in your Word documents using Aspose.Words for .NET. Whether you’re automating document processing or just curious about table layouts, this knowledge will definitely come in handy.

Remember, working with Aspose.Words for .NET opens up a world of possibilities for document manipulation and automation. Happy coding!

## FAQ's

### What is a floating table in Word documents?
A floating table is a table that is not fixed to the text but can move around, typically with text wrapping around it.

### How can I tell if a table is floating using Aspose.Words for .NET?
You can check if a table is floating by examining its `TextWrapping` property. If it’s set to `TextWrapping.Around`, the table is floating.

### Can I change the positioning properties of a floating table?
Yes, using Aspose.Words for .NET, you can modify the positioning properties of a floating table to customize its layout.

### Is Aspose.Words for .NET suitable for large-scale document automation?
Absolutely! Aspose.Words for .NET is designed for high-performance document automation and can handle large-scale operations efficiently.

### Where can I find more information and resources on Aspose.Words for .NET?
You can find detailed documentation and resources on the [Aspose.Words for .NET documentation page](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
