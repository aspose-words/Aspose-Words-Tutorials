---
title: Delete Row By Bookmark In Word Document
linktitle: Delete Row By Bookmark In Word Document
second_title: Aspose.Words Document Processing API
description: Learn how to delete a row by bookmark in a Word document using Aspose.Words for .NET. Follow our step-by-step guide for efficient document management.
weight: 10
url: /net/programming-with-bookmarks/delete-row-by-bookmark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Delete Row By Bookmark In Word Document

## Introduction

Deleting a row by bookmark in a Word document might sound complicated, but with Aspose.Words for .NET, it's a breeze. This guide will walk you through everything you need to know to accomplish this task efficiently. Ready to dive in? Let's get started!

## Prerequisites

Before we jump into the code, make sure you have the following:

- Aspose.Words for .NET: Ensure you have Aspose.Words for .NET installed. You can download it from the [Aspose releases page](https://releases.aspose.com/words/net/).
- Development Environment: Visual Studio or any other IDE that supports .NET development.
- Basic Knowledge of C#: Familiarity with C# programming will help you follow along with the tutorial.

## Import Namespaces

To begin, you'll need to import the necessary namespaces. These namespaces provide the classes and methods required to work with Word documents in Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Let's break down the process into manageable steps. Each step will be explained in detail to ensure you understand how to delete a row by bookmark in your Word document.

## Step 1: Load the Document

First, you need to load the Word document that contains the bookmark. This document will be the one from which you want to delete a row.

```csharp
Document doc = new Document("your-document.docx");
```

## Step 2: Find the Bookmark

Next, locate the bookmark in the document. The bookmark will help you identify the specific row you want to delete.

```csharp
Bookmark bookmark = doc.Range.Bookmarks["YourBookmarkName"];
```

## Step 3: Identify the Row

Once you have the bookmark, you need to identify the row that contains the bookmark. This involves navigating to the ancestor of the bookmark, which is of type `Row`.

```csharp
Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
```

## Step 4: Remove the Row

Now that you have identified the row, you can proceed to remove it from the document. Ensure to handle any potential null values to avoid exceptions.

```csharp
row?.Remove();
```

## Step 5: Save the Document

After deleting the row, save the document to reflect the changes. This will complete the process of deleting a row by bookmark.

```csharp
doc.Save("output-document.docx");
```

## Conclusion

And there you have it! Deleting a row by bookmark in a Word document using Aspose.Words for .NET is straightforward when you break it down into simple steps. This method ensures you can precisely target and remove rows based on bookmarks, making your document management tasks more efficient.

## FAQ's

### Can I delete multiple rows using bookmarks?
Yes, you can delete multiple rows by iterating over multiple bookmarks and applying the same method.

### What happens if the bookmark is not found?
If the bookmark is not found, the `row` variable will be null, and the `Remove` method will not be called, preventing any errors.

### Can I undo the deletion after saving the document?
Once the document is saved, the changes are permanent. Ensure to keep a backup if you need to undo changes.

### Is it possible to delete a row based on other criteria?
Yes, Aspose.Words for .NET provides various methods to navigate and manipulate document elements based on different criteria.

### Does this method work for all types of Word documents?
This method works for documents compatible with Aspose.Words for .NET. Ensure your document format is supported.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
