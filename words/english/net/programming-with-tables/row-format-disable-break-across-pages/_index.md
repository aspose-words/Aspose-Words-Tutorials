---
title: Row Format Disable Break Across Pages
linktitle: Row Format Disable Break Across Pages
second_title: Aspose.Words Document Processing API
description: Learn how to disable row breaks across pages in Word documents using Aspose.Words for .NET to maintain table readability and formatting.
weight: 10
url: /net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Row Format Disable Break Across Pages

## Introduction

When working with tables in Word documents, you might want to ensure that rows do not break across pages, which can be essential for maintaining the readability and formatting of your documents. Aspose.Words for .NET provides an easy way to disable row breaks across pages.

In this tutorial, we will walk you through the process of disabling row breaks across pages in a Word document using Aspose.Words for .NET.

## Prerequisites

Before we begin, ensure you have the following prerequisites:
- Aspose.Words for .NET library installed.
- A Word document with a table that spans multiple pages.

## Import Namespaces

First, import the necessary namespaces in your project:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Step 1: Load the Document

Load the document containing the table that spans multiple pages.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Step 2: Access the Table

Access the first table in the document. This assumes that the table you want to modify is the first table in the document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Step 3: Disable Breaking Across Pages for All Rows

Loop through each row in the table and set the `AllowBreakAcrossPages` property to `false`. This ensures that rows will not break across pages.

```csharp
// Disable breaking across pages for all rows in the table.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Step 4: Save the Document

Save the modified document to your specified directory.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Conclusion

In this tutorial, we demonstrated how to disable row breaks across pages in a Word document using Aspose.Words for .NET. By following the steps outlined above, you can ensure that your table rows remain intact and do not split across pages, maintaining the document's readability and formatting.

## FAQ's

### Can I disable row breaks across pages for a specific row instead of all rows?  
Yes, you can disable row breaks for specific rows by accessing the desired row and setting its `AllowBreakAcrossPages` property to `false`.

### Does this method work for tables with merged cells?  
Yes, this method works for tables with merged cells. The property `AllowBreakAcrossPages` applies to the entire row, regardless of cell merging.

### Will this method work if the table is nested inside another table?  
Yes, you can access and modify nested tables in the same way. Ensure you correctly reference the nested table by its index or other properties.

### How can I check if a row allows breaking across pages?  
You can check if a row allows breaking across pages by accessing the `AllowBreakAcrossPages` property of the `RowFormat` and checking its value.

### Is there a way to apply this setting to all tables in a document?  
Yes, you can loop through all tables in the document and apply this setting to each one.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
