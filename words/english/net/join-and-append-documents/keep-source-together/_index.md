---
title: Keep Table Together
linktitle: Keep Table Together
second_title: Aspose.Words Document Processing API
description: Learn how to prevent tables from breaking across pages using Aspose.Words for .NET with this step-by-step guide. Ensure neat, professional-looking Word documents
weight: 10
url: /net/join-and-append-documents/keep-source-together/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Keep Table Together

## Introduction

Tables are an essential part of many Word documents, but sometimes, you might run into a situation where your table breaks across two pages. This can disrupt the flow of your document and affect its readability. Wouldn't it be nice if there was a way to keep the entire table together on one page? Well, with Aspose.Words for .NET, there's an easy solution to this problem! In this tutorial, we’ll walk through how to prevent tables from splitting across pages, ensuring your document looks neat and professional.

## Prerequisites

Before we jump into the tutorial, let’s make sure you have everything you need to follow along smoothly.

### Aspose.Words for .NET Library

First, you’ll need to have Aspose.Words for .NET installed. This is the powerful library that allows you to work with Word documents programmatically.

- [Download Aspose.Words for .NET](https://releases.aspose.com/words/net/)

### Development Environment

You should have a development environment set up to run C# code, such as:

- Visual Studio (any recent version)
- .NET Framework 2.0 or later

### A Word Document with a Table

You’ll need a Word document that contains a table. In this tutorial, we’ll work with a sample document called `"Table spanning two pages.docx"`. This file contains a table that currently spans across two pages.

### Temporary License (Optional)

While Aspose.Words comes with a free trial, you might want to use a [temporary license](https://purchase.aspose.com/temporary-license/) to unlock the full potential of the library.

## Import Packages

Before writing any code, we need to import the necessary namespaces for working with Aspose.Words for .NET. Add the following imports at the top of your code file:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

These namespaces give you access to classes like `Document`, `Table`, `Cell`, and others that we’ll use in this tutorial.

## Step 1: Load the Document

The first thing we need to do is load the Word document that contains the table. For this, we’ll use the `Document` class from Aspose.Words. This class allows you to open and manipulate Word files programmatically.

```csharp
// The path to the documents directory.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

In this code snippet, we specify the location of our document. Replace `"YOUR DOCUMENTS DIRECTORY"` with the actual directory where your document is stored.

## Step 2: Access the Table

Once the document is loaded, the next step is to access the table that we want to keep together. In this example, we assume the table is the first table in the document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

This line of code finds the first table in the document. The `GetChild` method retrieves a specific type of node, which in this case is `NodeType.Table`. The `0` indicates we want the first table, and the `true` flag ensures that we search recursively through all child nodes.

## Step 3: Loop Through Table Cells

Now, we need to loop through each cell in the table. Since a table contains multiple rows and each row contains multiple cells, we’ll iterate through each cell and ensure that it doesn’t break across pages.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Here, `GetChildNodes` retrieves all the cells in the table, and we loop through each of them. The `EnsureMinimum()` method makes sure that each cell contains at least one paragraph, as an empty cell could cause problems later.

## Step 4: Set KeepWithNext Property

To prevent the table from breaking across pages, we need to set the `KeepWithNext` property for each paragraph within the table. This property ensures that the paragraph stays with the next paragraph, effectively preventing page breaks between them.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

This loop checks every paragraph inside each cell. The condition ensures that we don’t apply the `KeepWithNext` property to the last paragraph in the last row. Otherwise, the property would have no effect since there is no next paragraph.

## Step 5: Save the Document

Finally, after applying the `KeepWithNext` property, we need to save the modified document.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

This line saves the updated document with a new name, preserving the original file. You can now open the resulting file and see that the table is no longer split across two pages!

## Conclusion

And there you have it! By following these simple steps, you can easily keep tables from breaking across pages in Word documents using Aspose.Words for .NET. Whether you’re working on reports, contracts, or other documents, keeping tables intact ensures a more polished, professional look.

The beauty of Aspose.Words is its flexibility and ease of use, allowing you to manipulate Word documents programmatically without needing Microsoft Word installed on your machine. Now that you've got the hang of keeping tables together, explore other features of the library to take your document processing skills to the next level!

## FAQ's

### Why is my table still breaking across pages after using this code?

If your table is still breaking, make sure you’ve applied the `KeepWithNext` property correctly. Double-check that all paragraphs except the last one in each cell have this property set.

### Can I keep only specific rows together?

Yes, you can selectively apply the `KeepWithNext` property to specific rows or paragraphs within the table to control which parts should stay together.

### Does this method work with large tables?

For very large tables, Word may still split them across pages if there isn’t enough space to fit the entire table on one page. Consider adjusting your table’s formatting or margins to accommodate larger tables.

### Can I use this method with other document formats?

Yes! Aspose.Words for .NET supports many formats such as DOC, DOCX, PDF, and others. The same method works across all formats that support tables.

### Is Aspose.Words for .NET a free library?

Aspose.Words for .NET offers a free trial, but for full access to all features, you'll need to purchase a license. You can explore licensing options on the [Aspose purchase page](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
