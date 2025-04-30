---
title: Saving Documents as Markdown in Aspose.Words for Java
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
description: Learn how to convert Word documents to Markdown with Aspose.Words for Java. This step-by-step guide covers table alignment, image handling, and more.
weight: 18
url: /java/document-loading-and-saving/saving-documents-as-markdown/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Saving Documents as Markdown in Aspose.Words for Java


## Introduction to Saving Documents as Markdown in Aspose.Words for Java

In this step-by-step guide, we will demonstrate how to save documents as Markdown using Aspose.Words for Java. Markdown is a lightweight markup language that is commonly used for formatting text documents. With Aspose.Words for Java, you can easily convert your Word documents into Markdown format. We will cover different aspects of saving Markdown files, including table content alignment and handling images.

## Prerequisites

Before you begin, make sure you have the following prerequisites:

- Java Development Kit (JDK) installed on your system.
- Aspose.Words for Java library. You can download it from [here](https://releases.aspose.com/words/java/).

## Step 1: Creating a Word Document

Let's start by creating a Word document that we will later convert to Markdown format. You can customize this document as per your requirements.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

In this example, we create a simple table with two cells and set the alignment of the paragraphs within these cells. Then, we save the document as Markdown using the `MarkdownSaveOptions`.

## Step 2: Customize Table Content Alignment

Aspose.Words for Java allows you to customize the alignment of table content when saving as Markdown. You can align the table content to the left, right, center, or let it be determined automatically based on the first paragraph in each table column.

Here's how to customize table content alignment:

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

By changing the `TableContentAlignment` property, you can control how the content inside tables is aligned when converting to Markdown.

## Step 3: Handling Images

To include images in your Markdown document, you need to specify the folder where the images are located. Aspose.Words for Java allows you to set the images folder in the `MarkdownSaveOptions`.

Here's how to set the images folder and save the document with images:

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Make sure to replace `"document_with_images.docx"` with the path to your Word document containing images and `"images_folder/"` with the actual path to the folder where your images are stored.

## Complete Source Code For Saving Documents as Markdown in Aspose.Words for Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Conclusion

In this guide, we have explored how to save documents as Markdown using Aspose.Words for Java. We covered the creation of a Word document, customizing table content alignment, and handling images in Markdown files. You can now efficiently convert your Word documents to Markdown format, making them suitable for various publishing platforms and documentation needs.

## FAQ's

### How do I install Aspose.Words for Java?

Aspose.Words for Java can be installed by including the library in your Java project. You can download the library from [here](https://releases.aspose.com/words/java/) and follow the installation instructions provided in the documentation.

### Can I convert complex Word documents with tables and images to Markdown?

Yes, Aspose.Words for Java supports the conversion of complex Word documents with tables, images, and various formatting elements to Markdown. You can customize the Markdown output according to your document's complexity.

### How can I handle images in Markdown files?

To include images in Markdown files, set the images folder path using the `setImagesFolder` method in `MarkdownSaveOptions`. Ensure that the image files are stored in the specified folder, and Aspose.Words for Java will handle the image references accordingly.

### Is there a trial version of Aspose.Words for Java available?

Yes, you can obtain a trial version of Aspose.Words for Java from the Aspose website. The trial version allows you to evaluate the library's capabilities before purchasing a license.

### Where can I find more examples and documentation?

For more examples, documentation, and detailed information on Aspose.Words for Java, please visit the [documentation](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
