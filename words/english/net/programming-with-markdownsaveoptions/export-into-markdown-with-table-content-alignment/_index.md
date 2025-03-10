---
title: Export Into Markdown With Table Content Alignment
linktitle: Export Into Markdown With Table Content Alignment
second_title: Aspose.Words Document Processing API
description: Learn how to export Word documents into Markdown with aligned tables using Aspose.Words for .NET. Follow our step-by-step guide for perfect Markdown tables.
weight: 10
url: /net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Into Markdown With Table Content Alignment

## Introduction

Hey there! Ever wondered how to export your Word document into Markdown format with perfectly aligned tables? Whether you’re a developer working on documentation or just someone who loves Markdown, this guide is for you. We'll be diving into the nitty-gritty of using Aspose.Words for .NET to achieve this. Ready to turn your Word tables into neatly aligned Markdown tables? Let's get started!

## Prerequisites

Before we dive into the code, there are a few things you'll need to have in place:

1. Aspose.Words for .NET Library: Make sure you have the Aspose.Words for .NET library. You can download it from the [Aspose Releases Page](https://releases.aspose.com/words/net/).
2. Development Environment: Set up your development environment. Visual Studio is a popular choice for .NET development.
3. Basic Knowledge of C#: Understanding C# is essential as we will be writing code in this language.
4. Sample Word Document: Have a Word document that you can use for testing.

## Import Namespaces

Before we start coding, let's import the necessary namespaces. These will give us access to the Aspose.Words classes and methods we'll be using.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Step 1: Initialize Document and DocumentBuilder

First things first, we need to create a new Word document and initialize a `DocumentBuilder` object to start building our document.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Create a new document.
Document doc = new Document();

// Initialize DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 2: Insert Cells and Align Content

Next, we'll insert some cells into our document and set their alignment. This is crucial for ensuring that the Markdown export retains the correct alignment.

```csharp
// Insert a cell and set alignment to the right.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Insert another cell and set alignment to the center.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Step 3: Set Table Content Alignment for Markdown Export

Now, it's time to configure the `MarkdownSaveOptions` to control the alignment of table content in the exported Markdown file. We'll save the document with different alignment settings to see how it works.

```csharp
// Create MarkdownSaveOptions object.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Save document with left alignment.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Change alignment to right and save.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Change alignment to center and save.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Step 4: Use Auto Table Content Alignment

The `Auto` alignment option takes the alignment from the first paragraph in the corresponding table column. This can be handy when you have mixed alignments in a single table.

```csharp
// Set alignment to Auto.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Save document with auto alignment.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Conclusion

And there you have it! Exporting Word documents into Markdown with aligned tables using Aspose.Words for .NET is a breeze once you know how to do it. This powerful library makes it easy to control the formatting and alignment of your tables, ensuring that your Markdown documents look just the way you want them to. Happy coding!

## FAQ's

### What is Aspose.Words for .NET?
Aspose.Words for .NET is a powerful library that enables developers to create, modify, convert, and export Word documents programmatically.

### Can I set different alignments for different columns in the same table?
Yes, by using the `Auto` alignment option, you can have different alignments based on the first paragraph in each column.

### Do I need a license to use Aspose.Words for .NET?
Yes, Aspose.Words for .NET requires a license for full functionality. You can get a [temporary license](https://purchase.aspose.com/temporary-license/) for evaluation.

### Is it possible to export other document elements to Markdown using Aspose.Words?
Yes, Aspose.Words supports exporting various elements like headings, lists, and images to Markdown format.

### Where can I get support if I run into issues?
You can get support from the [Aspose.Words Support Forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
