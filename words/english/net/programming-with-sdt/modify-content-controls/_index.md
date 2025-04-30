---
title: Modify Content Controls
linktitle: Modify Content Controls
second_title: Aspose.Words Document Processing API
description: Learn how to modify structured document tags in Word using Aspose.Words for .NET. Update text, dropdowns, and images step-by-step.
weight: 10
url: /net/programming-with-sdt/modify-content-controls/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Modify Content Controls

## Introduction

If you’ve ever worked with Word documents and needed to modify structured content controls—like plain text, dropdown lists, or pictures—using Aspose.Words for .NET, you’re in the right place! Structured Document Tags (SDTs) are powerful tools that make document automation easier and more flexible. In this tutorial, we’ll dive into how you can modify these SDTs to fit your needs. Whether you’re updating text, changing dropdown selections, or swapping out images, this guide will walk you through the process step-by-step.

## Prerequisites

Before we jump into the nitty-gritty of modifying content controls, make sure you have the following:

1. Aspose.Words for .NET Installed: Ensure you have the Aspose.Words library installed. If not, you can [download it here](https://releases.aspose.com/words/net/).

2. Basic Knowledge of C#: This tutorial assumes you’re familiar with basic C# programming concepts.

3. A .NET Development Environment: You should have an IDE like Visual Studio set up for running .NET applications.

4. A Sample Document: We’ll be using a sample Word document with various types of SDTs. You can use the one from the example or create your own.

5. Access to Aspose Documentation: For more detailed information, check out the [Aspose.Words documentation](https://reference.aspose.com/words/net/).

## Import Namespaces

To start working with Aspose.Words, you need to import the relevant namespaces into your C# project. Here’s how you do it:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

These namespaces will give you access to the classes and methods necessary for manipulating structured document tags in your Word documents.

## Step 1: Set Up Your Document Path

Before making any changes, you need to specify the path to your document. Replace `"YOUR DOCUMENT DIRECTORY"` with the actual path where your document is stored.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Step 2: Loop Through Structured Document Tags

To modify SDTs, you first need to loop through all SDTs in the document. This is done using the `GetChildNodes` method to get all nodes of type `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modify SDTs based on their type
}
```

## Step 3: Modify Plain Text SDTs

If the SDT is a plain text type, you can replace its content. First, clear existing content, then add new text.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Explanation: Here, `RemoveAllChildren()` clears the existing content of the SDT. We then create a new `Paragraph` and `Run` object to insert the new text.

## Step 4: Modify Dropdown List SDTs

For dropdown list SDTs, you can change the selected item by accessing the `ListItems` collection. Here, we select the third item in the list.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Explanation: This code snippet selects the item at index 2 (third item) from the dropdown list. Adjust the index based on your needs.

## Step 5: Modify Picture SDTs

To update an image within a picture SDT, you can replace the existing image with a new one.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

Explanation: This code checks if the shape contains an image and then replaces it with a new image located at `ImagesDir`.

## Step 6: Save Your Modified Document

After making all necessary changes, save the modified document with a new name to keep your original document intact.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Explanation: This saves the document with a new filename so you can easily differentiate it from the original.

## Conclusion

Modifying content controls in a Word document using Aspose.Words for .NET is straightforward once you understand the steps involved. Whether you're updating text, changing dropdown selections, or swapping images, Aspose.Words provides a robust API for these tasks. By following this tutorial, you can effectively manage and customize your document’s structured content controls, making your documents more dynamic and tailored to your needs.

## FAQs

1. What is a Structured Document Tag (SDT)?

SDTs are elements in Word documents that help manage and format document content, like text boxes, dropdown lists, or pictures.

2. How can I add a new dropdown item to an SDT?

To add a new item, use the `ListItems` property and append a new `SdtListItem` to the collection.

3. Can I use Aspose.Words to remove SDTs from a document?

Yes, you can remove SDTs by accessing the document’s nodes and deleting the desired SDT.

4. How do I handle SDTs that are nested within other elements?

Use the `GetChildNodes` method with appropriate parameters to access nested SDTs.

5. What should I do if the SDT I need to modify is not visible in the document?

Ensure the SDT is not hidden or protected. Check document settings and ensure your code is correctly targeting the SDT type.


### Example source code for Modify Content Controls using Aspose.Words for .NET 

```csharp
// Path to your document directory 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

That's it! You have successfully modified different types of content controls in your Word document using Aspose.Words for .NET.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
