---
title: Preferred Width Settings
linktitle: Preferred Width Settings
second_title: Aspose.Words Document Processing API
description: Learn how to create tables with absolute, relative, and automatic width settings in Aspose.Words for .NET with this step-by-step guide.
weight: 10
url: /net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Preferred Width Settings

## Introduction

Tables are a powerful way to organize and present information in your Word documents. When working with tables in Aspose.Words for .NET, you have several options for setting the width of table cells to ensure they fit your document's layout perfectly. This guide will walk you through the process of creating tables with preferred width settings using Aspose.Words for .NET, focusing on absolute, relative, and automatic sizing options. 

## Prerequisites

Before diving into the tutorial, ensure you have the following:

1. Aspose.Words for .NET: Ensure you have Aspose.Words for .NET installed in your development environment. You can download it [here](https://releases.aspose.com/words/net/).

2. .NET Development Environment: Have a .NET development environment set up, such as Visual Studio.

3. Basic Knowledge of C#: Familiarity with C# programming will help you understand the code snippets and examples better.

4. Aspose.Words Documentation: Refer to the [Aspose.Words Documentation](https://reference.aspose.com/words/net/) for detailed API information and further reading.

## Import Namespaces

Before you start coding, you need to import the necessary namespaces into your C# project:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

These namespaces provide access to the core functionalities of Aspose.Words and the Table object, allowing you to manipulate document tables.

Let's break down the process of creating a table with different preferred width settings into clear, manageable steps.

## Step 1: Initialize the Document and DocumentBuilder

Heading: Creating a New Document and DocumentBuilder

Explanation: Start by creating a new Word document and a `DocumentBuilder` instance. The `DocumentBuilder` class provides a simple way to add content to your document.

```csharp
// Define the path to save the document.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Create a new Document.
Document doc = new Document();

// Create a DocumentBuilder for this Document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Here, you specify the directory where the document will be saved and initialize the `Document` and `DocumentBuilder` objects.

## Step 2: Insert the First Table Cell with Absolute Width

Insert the first cell into the table with a fixed width of 40 points. This will ensure that this cell always maintains a width of 40 points regardless of the table size.

```csharp
// Insert an absolute sized cell.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

In this step, you begin creating the table and insert a cell with an absolute width. The `PreferredWidth.FromPoints(40)` method sets the cell's width to 40 points, and `Shading.BackgroundPatternColor` applies a light yellow background color.

## Step 3: Insert a Relative Sized Cell

Insert another cell with a width that is 20% of the table's total width. This relative sizing ensures the cell adjusts proportionally to the table's width.

```csharp
// Insert a relative (percent) sized cell.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

This cell's width will be 20% of the table's total width, making it adaptable to different screen sizes or document layouts.

### Step 4: Insert an Auto Sized Cell

Finally, insert a cell that automatically sizes itself based on the remaining available space in the table.

```csharp
// Insert an auto sized cell.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` setting allows this cell to expand or contract based on the space left after the other cells are accounted for. This ensures the table layout looks balanced and professional.

## Step 5: Finalize and Save the Document

Once you have inserted all your cells, complete the table and save the document to your specified path.

```csharp
// Save the document.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

This step finalizes the table and saves the document with the filename "WorkingWithTables.PreferredWidthSettings.docx" in your designated directory.

## Conclusion

Creating tables with preferred width settings in Aspose.Words for .NET is straightforward once you understand the different sizing options available. Whether you need fixed, relative, or automatic cell widths, Aspose.Words provides the flexibility to handle various table layout scenarios efficiently. By following the steps outlined in this guide, you can ensure your tables are well-structured and visually appealing in your Word documents.

## FAQ's

### What is the difference between absolute and relative cell widths?
Absolute cell widths are fixed and do not change, while relative widths adjust based on the table's total width.

### Can I use negative percentages for relative widths?
No, negative percentages are not valid for cell widths. Only positive percentages are allowed.

### How does the auto sizing feature work?
Auto sizing adjusts the cell's width to fill any remaining space in the table after other cells have been sized.

### Can I apply different styles to cells with different width settings?
Yes, you can apply various styles and formatting to cells regardless of their width settings.

### What happens if the table's total width is less than the sum of all cell widths?
The table will automatically adjust the widths of cells to fit within the available space, which may cause some cells to shrink.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
