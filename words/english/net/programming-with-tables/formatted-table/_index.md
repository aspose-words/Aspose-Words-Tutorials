---
title: Formatted Table
linktitle: Formatted Table
second_title: Aspose.Words Document Processing API
description: Learn how to create and format tables in Word documents using Aspose.Words for .NET with this detailed step-by-step guide.
weight: 10
url: /net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatted Table

## Introduction

Creating and formatting tables in Word documents programmatically can seem like a daunting task, but with Aspose.Words for .NET, it becomes straightforward and manageable. In this tutorial, we'll walk you through how to create a formatted table in a Word document using Aspose.Words for .NET. We’ll cover everything from setting up your environment to saving your document with a beautifully formatted table.

## Prerequisites

Before diving into the code, let's make sure you have everything you need:

1. Aspose.Words for .NET Library: Download it from [here](https://releases.aspose.com/words/net/).
2. Development Environment: An IDE like Visual Studio.
3. .NET Framework: Ensure you have .NET Framework installed on your machine.

## Import Namespaces

Before writing the actual code, you need to import the necessary namespaces:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Step 1: Set Up Your Document Directory

First, you need to define the path where your document will be saved.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where you want to save the document.

## Step 2: Initialize the Document and DocumentBuilder

Now, initialize a new document and a DocumentBuilder object.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

The `DocumentBuilder` is a helper class that simplifies the process of building documents.

## Step 3: Start the Table

Next, start creating the table using the `StartTable` method.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Inserting a cell is necessary to begin the table.

## Step 4: Apply Table-Wide Formatting

You can apply formatting that affects the entire table. For example, setting the left indent:

```csharp
table.LeftIndent = 20.0;
```

## Step 5: Format the Header Row

Set the height, alignment, and other properties for the header row.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

In this step, we make the header row stand out by setting a background color, font size, and alignment.

## Step 6: Insert Additional Header Cells

Insert more cells for the header row:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Step 7: Format the Body Rows

After setting up the header, format the body of the table:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Step 8: Insert Body Rows

Insert the body rows with content:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Repeat for additional rows:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Step 9: Save the Document

Finally, save the document to the specified directory:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

This will create and save a Word document with the formatted table.

## Conclusion

And there you have it! By following these steps, you can create a well-formatted table in a Word document using Aspose.Words for .NET. This powerful library makes it easy to programmatically manipulate Word documents, saving you time and effort.

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library for creating, editing, and converting Word documents programmatically.

### Can I use different colors for different rows?
Yes, you can apply different formatting, including colors, to different rows or cells.

### Is Aspose.Words for .NET free?
Aspose.Words for .NET is a paid library, but you can get a [free trial](https://releases.aspose.com/).

### How do I get support for Aspose.Words for .NET?
You can get support from the [Aspose community forums](https://forum.aspose.com/c/words/8).

### Can I create other types of documents with Aspose.Words for .NET?
Yes, Aspose.Words for .NET supports various document formats, including PDF, HTML, and TXT.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
