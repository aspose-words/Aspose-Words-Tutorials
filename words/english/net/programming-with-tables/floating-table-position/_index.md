---
title: Floating Table Position
linktitle: Floating Table Position
second_title: Aspose.Words Document Processing API
description: Learn how to control the floating position of tables in Word documents using Aspose.Words for .NET with our detailed, step-by-step guide.
weight: 10
url: /net/programming-with-tables/floating-table-position/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Floating Table Position

## Introduction

Are you ready to dive into the world of manipulating table positions in Word documents using Aspose.Words for .NET? Buckle up, because today we’re going to explore how to control the floating position of tables with ease. Let’s turn you into a table positioning wizard in no time!

## Prerequisites

Before we embark on this exciting journey, let's make sure we have everything we need:

1. Aspose.Words for .NET Library: Ensure you have the latest version. If you don't, [download it here](https://releases.aspose.com/words/net/).
2. .NET Framework: Make sure your development environment is set up with .NET.
3. Development Environment: Visual Studio or any preferred IDE.
4. A Word Document: Have a Word document ready that contains a table.

## Import Namespaces

To get started, you need to import the necessary namespaces in your .NET project. Here’s the snippet to include at the top of your C# file:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Step-by-Step Guide

Now, let's break down the process into simple, digestible steps.

## Step 1: Load the Document

First things first, you need to load your Word document. This is where your table is located.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Imagine your Word document is a canvas and your table is a piece of art on it. Our goal is to position this art exactly where we want on the canvas.

## Step 2: Access the Table

Next, we need to access the table within the document. Typically, you'll be working with the first table in the document’s body.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Think of this step as locating the table you want to work with in a physical document. You need to know exactly where it is to make any changes.

## Step 3: Set Horizontal Position

Now, let's set the horizontal position of the table. This determines how far from the left edge of the document the table will be placed.

```csharp
table.AbsoluteHorizontalDistance = 10;
```

Visualize this as moving the table horizontally across your document. The `AbsoluteHorizontalDistance` is the exact distance from the left edge.

## Step 4: Set Vertical Alignment

We also need to set the vertical alignment of the table. This will center the table vertically within its surrounding text.

```csharp
table.RelativeVerticalAlignment = VerticalAlignment.Center;
```

Imagine hanging a picture on a wall. You want to ensure it's centered vertically for aesthetic appeal. This step achieves that.

## Step 5: Save the Modified Document

Finally, after positioning the table, save your modified document.

```csharp
doc.Save(dataDir + "WorkingWithTables.FloatingTablePosition.docx");
```

This is like hitting ‘Save’ on your edited document. All your changes are now preserved.

## Conclusion

And there you have it! You've just mastered how to control the floating position of tables in a Word document using Aspose.Words for .NET. With these skills, you can ensure your tables are perfectly positioned to enhance the readability and aesthetics of your documents. Keep experimenting and exploring the vast capabilities of Aspose.Words for .NET.

## FAQ's

### Can I set the vertical distance of the table from the top of the page?

Yes, you can use the `AbsoluteVerticalDistance` property to set the vertical distance of the table from the top edge of the page.

### How do I align the table to the right of the document?

To align the table to the right, you can set the `HorizontalAlignment` property of the table to `HorizontalAlignment.Right`.

### Is it possible to position multiple tables differently in the same document?

Absolutely! You can access and set positions for multiple tables individually by iterating through the `Tables` collection in the document.

### Can I use relative positioning for horizontal alignment?

Yes, Aspose.Words supports relative positioning for both horizontal and vertical alignments using properties like `RelativeHorizontalAlignment`.

### Does Aspose.Words support floating tables in different sections of a document?

Yes, you can position floating tables in different sections by accessing the specific section and its tables within your document.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
