---
title: Structured Document Tag Range Start Xml Mapping
linktitle: Structured Document Tag Range Start Xml Mapping
second_title: Aspose.Words Document Processing API
description: Learn how to dynamically bind XML data to structured document tags in Word using Aspose.Words for .NET. Follow our step-by-step guide.
weight: 10
url: /net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Structured Document Tag Range Start Xml Mapping

## Introduction

Have you ever wanted to dynamically insert XML data into a Word document? Well, you're in luck! Aspose.Words for .NET makes this task a breeze. In this tutorial, we're diving deep into structured document tag range start XML mapping. This feature allows you to bind custom XML parts to content controls, ensuring your document content updates seamlessly with your XML data. Ready to transform your documents into dynamic masterpieces.

## Prerequisites

Before we jump into the coding part, let’s make sure you have everything you need:

1. Aspose.Words for .NET Library: Ensure you have the latest version. You can download it [here](https://releases.aspose.com/words/net/).
2. Development Environment: Visual Studio or any other IDE that supports C#.
3. Basic Knowledge of C#: Familiarity with C# programming is a must.
4. Word Document: A sample Word document to work with.

## Import Namespaces

First things first, let’s import the necessary namespaces. This will ensure we have access to all the required classes and methods in Aspose.Words for .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Step 1: Set Up Your Document Directory

Every project needs a foundation, right? Here, we set up the path to your document directory.

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Step 2: Load the Word Document

Next, we load the Word document. This is the document where we’ll be inserting our XML data.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Step 3: Add Custom XML Part

We need to construct an XML part containing the data we want to insert and add it to the document’s CustomXmlPart collection. This custom XML part will serve as the data source for our structured document tags.

### Creating an XML Part

First, generate a unique ID for the XML part and define its content.

```csharp
// Construct an XML part that contains data and add it to the document's CustomXmlPart collection.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Verify the XML Part Content

To ensure the XML part is correctly added, we print its content.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Step 4: Create a Structured Document Tag

A Structured Document Tag (SDT) is a content control that can bind to an XML part. Here, we create an SDT that will display the contents of our custom XML part.

First, locate the SDT range start in the document.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Step 5: Set XML Mapping for the SDT

Now, it’s time to bind our XML part to the SDT. By setting an XML mapping, we specify which part of the XML data should be displayed in the SDT.

The XPath points to the specific element in the XML part that we want to display. Here, we point to the second `<text>` element within the `<root>` element.

```csharp
// Set a mapping for our StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Step 6: Save the Document

Finally, save the document to see the changes in action. The SDT in the Word document will now display the specified XML content.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Conclusion

And there you have it! You’ve successfully mapped an XML part to a structured document tag in a Word document using Aspose.Words for .NET. This powerful feature enables you to create dynamic and data-driven documents effortlessly. Whether you're generating reports, invoices, or any other document type, XML mapping can significantly streamline your workflow.

## FAQ's

### What is a structured document tag in Word?
Structured document tags, also known as content controls, are containers for specific types of content in Word documents. They can be used to bind data, restrict editing, or guide users in document creation.

### How can I update the XML part content dynamically?
You can update the XML part content by modifying the `xmlPartContent` string before adding it to the document. Simply update the string with the new data and add it to the `CustomXmlParts` collection.

### Can I bind multiple XML parts to different SDTs in the same document?
Yes, you can bind multiple XML parts to different SDTs in the same document. Each SDT can have its own unique XML part and XPath mapping.

### Is it possible to map complex XML structures to SDTs?
Absolutely! You can map complex XML structures to SDTs by using detailed XPath expressions that accurately point to the desired elements within the XML part.

### How can I remove an XML part from a document?
You can remove an XML part by calling the `Remove` method on the `CustomXmlParts` collection, passing the `xmlPartId` of the XML part you want to remove.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
