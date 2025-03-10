---
title: Set Relative Horizontal Or Vertical Position
linktitle: Set Relative Horizontal Or Vertical Position
second_title: Aspose.Words Document Processing API
description: Learn how to set relative horizontal and vertical positions for tables in Word documents using Aspose.Words for .NET with this step-by-step guide.
weight: 10
url: /net/programming-with-tables/set-relative-horizontal-or-vertical-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Set Relative Horizontal Or Vertical Position

## Introduction

Ever felt stuck with how to position tables just the way you want in your Word documents? Well, you're not alone. Whether you're creating a professional report or a stylish brochure, aligning tables can make a world of difference. That's where Aspose.Words for .NET comes in handy. This tutorial will guide you step-by-step on how to set relative horizontal or vertical positions for tables in your Word documents. Let's dive in!

## Prerequisites

Before we get started, make sure you have the following:

1. Aspose.Words for .NET: If you haven't already, you can download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: Visual Studio or any other .NET-compatible IDE.
3. Basic Knowledge of C#: This tutorial assumes you're familiar with the basics of C# programming.

## Import Namespaces

First things first, you need to import the necessary namespaces. This is essential for accessing the Aspose.Words functionalities.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Step 1: Load Your Document

To get started, you'll need to load your Word document into the program. Here's how you can do it:

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

This code snippet sets up the path to your document directory and loads the specific document you want to work on. Ensure your document path is correct to avoid any loading issues.

## Step 2: Access the Table

Next, we need to access the table within the document. Typically, you would want to work with the first table in the body section.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

This line of code fetches the first table from the document's body. If your document has multiple tables, you can adjust the index accordingly.

## Step 3: Set Horizontal Position

Now, let's set the horizontal position of the table relative to a specific element. In this example, we'll position it relative to the column.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

By setting the `HorizontalAnchor` to `RelativeHorizontalPosition.Column`, you're telling the table to align itself horizontally with respect to the column it resides in.

## Step 4: Set Vertical Position

Similar to horizontal positioning, you can also set the vertical position. Here, we position it relative to the page.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

Setting the `VerticalAnchor` to `RelativeVerticalPosition.Page` ensures that the table is vertically aligned according to the page.

## Step 5: Save Your Document

Finally, save your changes to a new document. This is a crucial step to make sure your changes are preserved.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

This command saves the modified document with a new name, ensuring you don't overwrite your original file.

## Conclusion

And there you have it! You've successfully set the relative horizontal and vertical positions for a table in a Word document using Aspose.Words for .NET. With this newfound skill, you can enhance the layout and readability of your documents, making them look more professional and polished. Keep experimenting with different positions and see what works best for your needs.

## FAQ's

### Can I position tables relative to other elements?  
Yes, Aspose.Words allows you to position tables relative to various elements like margins, pages, columns, and more.

### Do I need a license to use Aspose.Words for .NET?  
Yes, you can purchase a license [here](https://purchase.aspose.com/buy) or get a temporary license [here](https://purchase.aspose.com/temporary-license/).

### Is there a free trial available for Aspose.Words for .NET?  
Absolutely! You can download a free trial [here](https://releases.aspose.com/).

### Can I use Aspose.Words with other programming languages?  
Aspose.Words is designed primarily for .NET, but there are versions available for Java, Python, and other platforms.

### Where can I find more detailed documentation?  
For more in-depth information, check out the Aspose.Words documentation [here](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
