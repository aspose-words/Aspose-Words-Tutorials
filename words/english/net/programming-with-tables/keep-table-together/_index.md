---
title: Keep Table Together
linktitle: Keep Table Together
second_title: Aspose.Words Document Processing API
description: Learn how to keep tables from breaking across pages in Word documents using Aspose.Words for .NET. Follow our guide to maintain professional, readable documents.
weight: 10
url: /net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Keep Table Together

## Introduction

Ever found yourself frustrated when a table in your Word document splits across two pages? It's like your carefully laid-out information suddenly decided to take a break halfway through! Keeping tables together on one page is crucial for readability and presentation. Whether it's for a report, a project proposal, or just a personal document, having tables split can be quite jarring. Lucky for us, Aspose.Words for .NET has a nifty way to solve this issue. In this tutorial, we'll walk through the steps to keep your tables intact and looking sharp. Let's dive in!

## Prerequisites

Before we get started, make sure you have the following:

1. Aspose.Words for .NET - If you haven't installed it yet, you can download it from [here](https://releases.aspose.com/words/net/).
2. A Word Document with a Table - We'll be working with a sample document that has a table spanning multiple pages.
3. Basic Knowledge of C# - This tutorial assumes you have a basic understanding of C# programming.

## Import Namespaces

First things first, let's import the necessary namespaces. This will give us access to the classes and methods we need from Aspose.Words for .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Let's break down the process into easy, digestible steps. We'll start by loading our document and end with saving the updated document where the table stays together.

## Step 1: Load the Document

To work with a Word document, we first need to load it. We'll use the `Document` class for this.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Step 2: Access the Table

Next, we need to get the table we want to keep together. We'll assume it's the first table in the document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Step 3: Set KeepWithNext for Paragraphs

To prevent the table from breaking across pages, we need to set the `KeepWithNext` property for each paragraph in the table, except for the last paragraphs in the last row.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Step 4: Save the Document

Finally, we save the updated document. This will apply our changes and ensure the table stays together on one page.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusion

And there you have it! With just a few lines of code, you can keep your tables from splitting across pages in your Word documents. This simple yet effective solution ensures your tables remain neat and professional, enhancing the readability of your documents. Aspose.Words for .NET makes handling such formatting issues a breeze, allowing you to focus on creating great content.

## FAQ's

### Can I keep multiple tables together using this method?  
Yes, you can apply the same logic to multiple tables by iterating through each table in your document.

### What if my table is too large to fit on one page?  
If a table is too large to fit on a single page, it will still span across pages. This method ensures smaller tables stay intact without splitting.

### Is there a way to automate this for all tables in a document?  
Yes, you can loop through all tables in your document and apply the `KeepWithNext` property to each paragraph.

### Do I need a paid license for Aspose.Words for .NET?  
You can start with a free trial from [here](https://releases.aspose.com/), but for full functionality, a paid license is recommended.

### Can I apply other formatting to the table while keeping it together?  
Absolutely! You can format your table as needed while ensuring it stays together on one page.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
