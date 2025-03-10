---
title: Creating Table Repeating Section Mapped To Custom Xml Part
linktitle: Creating Table Repeating Section Mapped To Custom Xml Part
second_title: Aspose.Words Document Processing API
description: Learn how to create a table with a repeating section mapped to a CustomXmlPart in a Word document using Aspose.Words for .NET.
weight: 10
url: /net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creating Table Repeating Section Mapped To Custom Xml Part

## Introduction

In this tutorial, we'll walk through the process of creating a table with a repeating section that is mapped to a custom XML part using Aspose.Words for .NET. This is particularly useful for dynamically generating documents based on structured data.

## Prerequisites

Before we begin, make sure you have the following:
1. Aspose.Words for .NET library installed. You can download it from the [Aspose website](https://releases.aspose.com/words/net/).
2. A basic understanding of C# and XML.

## Import Namespaces

Make sure to include the necessary namespaces in your project:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Step 1: Initialize Document and DocumentBuilder

First, create a new document and initialize a `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Step 2: Add Custom XML Part

Add a custom XML part to the document. This XML contains the data we want to map to our table:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Step 3: Create the Table Structure

Next, use the `DocumentBuilder` to create the table header:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Step 4: Create Repeating Section

Create a `StructuredDocumentTag` (SDT) for the repeating section and map it to the XML data:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Step 5: Create Repeating Section Item

Create an SDT for the repeating section item and add it to the repeating section:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Step 6: Map XML Data to Table Cells

Create SDTs for the title and author, map them to the XML data, and append them to the row:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Step 7: Save the Document

Finally, save the document to the specified directory:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Conclusion

By following these steps, you've successfully created a table with a repeating section mapped to a custom XML part using Aspose.Words for .NET. This allows for dynamic content generation based on structured data, making document creation more flexible and powerful.

## FAQ's

### What is a StructuredDocumentTag (SDT)?
An SDT, also known as a content control, is a bounded region in a document that is used to contain structured data.

### Can I use other data types in the custom XML part?
Yes, you can structure your custom XML part with any data types and map them accordingly.

### How do I add more rows to the repeating section?
The repeating section automatically replicates the row structure for each item in the mapped XML path.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
