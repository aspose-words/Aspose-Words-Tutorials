---
title: Horizontal Merge
linktitle: Horizontal Merge
second_title: Aspose.Words Document Processing API
description: Learn how to horizontally merge cells in a Word document using Aspose.Words for .NET with this detailed, step-by-step tutorial.
weight: 10
url: /net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Horizontal Merge

## Introduction

Hey there! Ready to dive into the world of Aspose.Words for .NET? Today, we're going to tackle a super useful feature: horizontal merge in tables. This might sound a bit technical, but don't worry, I've got your back. By the end of this tutorial, you'll be a pro at merging cells in your Word documents programmatically. So, let's roll up our sleeves and get started!

## Prerequisites

Before we jump into the nitty-gritty, there are a few things you'll need to have in place:

1. Aspose.Words for .NET Library: If you haven't already, download the Aspose.Words for .NET library. You can grab it [here](https://releases.aspose.com/words/net/).
2. Development Environment: Ensure you have a suitable development environment set up, such as Visual Studio.
3. Basic Knowledge of C#: A basic understanding of C# programming will be beneficial.

Once you've got these sorted, you're all set to go!

## Import Namespaces

Before diving into the code, let's ensure we have the necessary namespaces imported. In your C# project, make sure to include:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Alright, let's break down the process of horizontally merging table cells in a Word document using Aspose.Words for .NET.

## Step 1: Setting Up Your Document

First things first, we need to create a new Word document and initialize the `DocumentBuilder`:

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

This code snippet sets up a new document and prepares the `DocumentBuilder` for action.

## Step 2: Inserting the First Cell

Next, we start by inserting the first cell and marking it for horizontal merge:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Here, we insert a new cell and set its `HorizontalMerge` property to `CellMerge.First`, indicating that this cell is the start of a merged cell sequence.

## Step 3: Inserting the Merged Cell

Now, we insert the cell that will be merged with the previous one:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

This cell is set to merge with the previous cell by using `CellMerge.Previous`. Notice how we end the row with `builder.EndRow()`.

## Step 4: Inserting Unmerged Cells

To illustrate the difference, let's insert a couple of unmerged cells:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Here, we insert two cells with no horizontal merge. This shows how cells behave when they are not part of a merged sequence.

## Step 5: Finishing the Table

Finally, we end the table and save the document:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

This code snippet completes the table and saves the document to the specified directory.

## Conclusion

And there you have it! You've just mastered the art of horizontally merging cells in a Word document using Aspose.Words for .NET. By following these steps, you can create complex table structures with ease. Keep experimenting and exploring the capabilities of Aspose.Words to make your documents as dynamic and flexible as you need. Happy coding!

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library that allows developers to create, edit, and manipulate Word documents programmatically in .NET applications.

### Can I merge cells vertically with Aspose.Words for .NET?
Yes, you can also merge cells vertically by using the `CellFormat.VerticalMerge` property.

### Is Aspose.Words for .NET free to use?
Aspose.Words for .NET offers a free trial, but for full functionality, you will need to purchase a license. You can get a temporary license [here](https://purchase.aspose.com/temporary-license/).

### How can I learn more about Aspose.Words for .NET?
You can explore the detailed documentation [here](https://reference.aspose.com/words/net/).

### Where can I get support for Aspose.Words for .NET?
For any queries or issues, you can visit the Aspose support forum [here](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
