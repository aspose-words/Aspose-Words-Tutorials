---
title: Get Distance Between Table Surrounding Text
linktitle: Get Distance Between Table Surrounding Text
second_title: Aspose.Words Document Processing API
description: Learn how to retrieve the distance between a table and the surrounding text in Word documents using Aspose.Words for .NET. Improve your document layout with this guide.
weight: 10
url: /net/programming-with-table-styles-and-formatting/get-distance-between-table-surrounding-text/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Get Distance Between Table Surrounding Text

## Introduction

Imagine you're preparing a sleek report or an important document, and you want your tables to look just right. You need to ensure there's enough space between the tables and the text around them, making the document easy to read and visually appealing. Using Aspose.Words for .NET, you can easily retrieve and adjust these distances programmatically. This tutorial will guide you through the steps to achieve this, making your documents stand out with that extra touch of professionalism.

## Prerequisites

Before we jump into the code, let's make sure you have everything you need:

1. Aspose.Words for .NET Library: You need to have the Aspose.Words for .NET library installed. If you haven't already, you can download it from the [Aspose Releases](https://releases.aspose.com/words/net/) page.
2. Development Environment: A working development environment with .NET Framework installed. Visual Studio is a good option.
3. Sample Document: A Word document (.docx) containing at least one table to test the code.

## Import Namespaces

First things first, let's import the necessary namespaces into your project. This will enable you to access the classes and methods required to manipulate Word documents using Aspose.Words for .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Now, let's break down the process into easy-to-follow steps. We'll cover everything from loading your document to retrieving the distances around your table.

## Step 1: Load Your Document

The first step is to load your Word document into the Aspose.Words `Document` object. This object represents the entire document.

```csharp
// Path to your document directory
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Load the document
Document doc = new Document(dataDir + "Tables.docx");
```

## Step 2: Access the Table

Next, you need to access the table within your document. The `GetChild` method allows you to retrieve the first table found in the document.

```csharp
// Get the first table in the document
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Step 3: Retrieve Distance Values

Now that you have the table, it's time to get the distance values. These values represent the space between the table and the surrounding text from each side: top, bottom, left, and right.

```csharp
// Get distance between table and surrounding text
Console.WriteLine("\nGet distance between table left, right, bottom, top and the surrounding text.");
Console.WriteLine("Distance from Top: " + table.DistanceTop);
Console.WriteLine("Distance from Bottom: " + table.DistanceBottom);
Console.WriteLine("Distance from Right: " + table.DistanceRight);
Console.WriteLine("Distance from Left: " + table.DistanceLeft);
```

## Step 4: Display the Distances

Finally, you can display the distances. This can help you verify the spacing and make any necessary adjustments to ensure your table looks perfect in the document.

```csharp
// Display the distances
Console.WriteLine("Distance from Top: " + table.DistanceTop);
Console.WriteLine("Distance from Bottom: " + table.DistanceBottom);
Console.WriteLine("Distance from Right: " + table.DistanceRight);
Console.WriteLine("Distance from Left: " + table.DistanceLeft);
```

## Conclusion

And there you have it! By following these steps, you can easily retrieve the distances between a table and the surrounding text in your Word documents using Aspose.Words for .NET. This simple yet powerful technique allows you to fine-tune your document layout, making it more readable and visually appealing. Happy coding!

## FAQ's

### Can I adjust the distances programmatically?
Yes, you can adjust the distances programmatically using Aspose.Words by setting the `DistanceTop`, `DistanceBottom`, `DistanceRight`, and `DistanceLeft` properties of the `Table` object.

### What if my document has multiple tables?
You can loop through the document's child nodes and apply the same method to each table. Use `GetChildNodes(NodeType.Table, true)` to get all tables.

### Can I use Aspose.Words with .NET Core?
Absolutely! Aspose.Words supports .NET Core, and you can use the same code with minor adjustments for .NET Core projects.

### How do I install Aspose.Words for .NET?
You can install Aspose.Words for .NET via NuGet Package Manager in Visual Studio. Simply search for "Aspose.Words" and install the package.

### Are there any limitations on the document types supported by Aspose.Words?
Aspose.Words supports a wide range of document formats, including DOCX, DOC, PDF, HTML, and more. Check the [documentation](https://reference.aspose.com/words/net/) for a full list of supported formats.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
