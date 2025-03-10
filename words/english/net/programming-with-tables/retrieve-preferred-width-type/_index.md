---
title: Retrieve Preferred Width Type
linktitle: Retrieve Preferred Width Type
second_title: Aspose.Words Document Processing API
description: Learn how to retrieve the preferred width type of table cells in Word documents using Aspose.Words for .NET with our step-by-step guide.
weight: 10
url: /net/programming-with-tables/retrieve-preferred-width-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Retrieve Preferred Width Type

## Introduction

Have you ever wondered how to retrieve the preferred width type of table cells in your Word documents using Aspose.Words for .NET? Well, you're in the right place! In this tutorial, we'll break down the process step-by-step, making it as easy as pie. Whether you're a seasoned developer or just starting, you'll find this guide helpful and engaging. So, let's dive in and uncover the secrets behind managing table cell widths in Word documents.

## Prerequisites

Before we get started, there are a few things you'll need:

1. Aspose.Words for .NET: Make sure you have the latest version installed. You can download it from [here](https://releases.aspose.com/words/net/).
2. Development Environment: You'll need an IDE like Visual Studio.
3. Basic Knowledge of C#: Understanding the basics of C# will help you follow along.
4. Sample Document: Have a Word document ready with tables that you can work on. You can use any document, but we'll refer to it as `Tables.docx` in this tutorial.

## Import Namespaces

First things first, let's import the necessary namespaces. This step is crucial as it sets up our environment to use Aspose.Words features.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Step 1: Set Up Your Document Directory

Before we manipulate our document, we need to specify the directory where it's located. This is a simple but essential step.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path to your document directory. This tells our program where to find the file we want to work with.

## Step 2: Load the Document

Next, we load the Word document into our application. This allows us to interact with its contents programmatically.

```csharp
Document doc = new Document(dataDir + "Tables.docx");
```

This line of code opens the `Tables.docx` document from the specified directory. Now, our document is ready for further operations.

## Step 3: Access the Table

Now that our document is loaded, we need to access the table we want to work with. For simplicity, we'll target the first table in the document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

This line retrieves the first table from the document. If your document contains multiple tables, you can adjust the index to select a different one.

## Step 4: Enable AutoFit for the Table

To ensure the table adjusts its columns automatically, we need to enable the AutoFit property.

```csharp
table.AllowAutoFit = true;
```

Setting `AllowAutoFit` to `true` ensures that the table columns resize based on their contents, giving a dynamic feel to our table.

## Step 5: Retrieve the Preferred Width Type of the First Cell

Now comes the crux of our tutorial—retrieving the preferred width type of the first cell in the table.

```csharp
Cell firstCell = table.FirstRow.FirstCell;
PreferredWidthType type = firstCell.CellFormat.PreferredWidth.Type;
double value = firstCell.CellFormat.PreferredWidth.Value;
```

These lines of code access the first cell in the first row of the table and retrieve its preferred width type and value. The `PreferredWidthType` can be `Auto`, `Percent`, or `Point`, indicating how the width is determined.

## Step 6: Display the Results

Finally, let's display the retrieved information to the console.

```csharp
Console.WriteLine("Preferred Width Type: " + type);
Console.WriteLine("Preferred Width Value: " + value);
```

These lines will print the preferred width type and value to the console, allowing you to see the results of your code execution.

## Conclusion

And there you have it! Retrieving the preferred width type of table cells in Word documents using Aspose.Words for .NET is straightforward when broken down into manageable steps. By following this guide, you can easily manipulate table properties in your Word documents, making your document management tasks much more efficient.

## FAQ's

### Can I retrieve the preferred width type for all cells in a table?

Yes, you can loop through each cell in the table and retrieve their preferred width types individually.

### What are the possible values for `PreferredWidthType`?

`PreferredWidthType` can be `Auto`, `Percent`, or `Point`.

### Is it possible to set the preferred width type programmatically?

Absolutely! You can set the preferred width type and value using the `PreferredWidth` property of the `CellFormat` class.

### Can I use this method for tables in documents other than Word?

This tutorial specifically covers Word documents. For other document types, you would need to use the appropriate Aspose library.

### Do I need a license to use Aspose.Words for .NET?

Yes, Aspose.Words for .NET is a licensed product. You can get a free trial [here](https://releases.aspose.com/) or a temporary license [here](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
