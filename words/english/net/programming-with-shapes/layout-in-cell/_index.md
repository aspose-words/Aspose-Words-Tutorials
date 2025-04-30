---
title: Layout In Cell
linktitle: Layout In Cell
second_title: Aspose.Words Document Processing API
description: Learn how to set the layout in cell using Aspose.Words for .NET with this comprehensive, guide. Perfect for developers looking to customize Word documents.
weight: 10
url: /net/programming-with-shapes/layout-in-cell/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Layout In Cell

## Introduction

If you've ever wanted to fine-tune the layout of your table cells in Word documents programmatically, you're in the right place. Today, we'll dive into how to set the layout in cell using Aspose.Words for .NET. We'll walk through a practical example, breaking it down step-by-step so you can follow along with ease.

## Prerequisites

Before we jump into the code, let's ensure you have everything you need:

1. Aspose.Words for .NET: Make sure you have the Aspose.Words for .NET library installed. If you haven't, you can [download it here](https://releases.aspose.com/words/net/).
2. Development Environment: You'll need a development environment set up with .NET. Visual Studio is a great choice if you're looking for recommendations.
3. Basic Knowledge of C#: While I'll explain each step, a basic understanding of C# will help you follow along more easily.
4. Document Directory: Prepare a directory path where you'll save your documents. We'll refer to this as `YOUR DOCUMENT DIRECTORY`.

## Import Namespaces

To get started, ensure you're importing the necessary namespaces in your project:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Let's break down the process into manageable steps.

## Step 1: Create a New Document

First, we'll create a new Word document and initialize a `DocumentBuilder` object to help us construct our content.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 2: Start a Table and Set Row Format

We'll begin constructing a table and specify the height and height rule for the rows.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Step 3: Insert Cells and Populate with Content

Next, we loop to insert cells into the table. For every 7 cells, we'll end the row to create a new one.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Step 4: Add a Watermark Shape

Now, let's add a watermark to our document. We'll create a `Shape` object and set its properties.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Display the shape outside of the table cell if it will be placed into a cell.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Step 5: Customize Watermark Appearance

We'll further customize the watermark's appearance by setting its color and text properties.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Step 6: Insert Watermark into Document

We'll find the last run in the document and insert the watermark at that position.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Step 7: Optimize Document for Word 2010

To ensure compatibility, we'll optimize the document for Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Step 8: Save the Document

Finally, we'll save our document to the specified directory.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Conclusion

And there you have it! You've successfully created a Word document with a customized table layout and added a watermark using Aspose.Words for .NET. This tutorial aimed to provide a clear, step-by-step guide to help you understand each part of the process. With these skills, you can now create more sophisticated and customized Word documents programmatically.

## FAQ's

### Can I use a different font for the watermark text?
Yes, you can change the font by setting the `watermark.TextPath.FontFamily` property to your desired font.

### How do I adjust the position of the watermark?
You can modify the `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`, and `VerticalAlignment` properties to adjust the watermark's position.

### Is it possible to use an image instead of text for the watermark?
Absolutely! You can create a `Shape` with the type `ShapeType.Image` and set its image using the `ImageData.SetImage` method.

### Can I create tables with varying row heights?
Yes, you can set different heights for each row by changing the `RowFormat.Height` property before inserting cells into that row.

### How do I remove a watermark from the document?
You can remove the watermark by locating it in the document's shapes collection and calling the `Remove` method.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
