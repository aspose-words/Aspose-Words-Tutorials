---
title: How to Export Markdown with Aspose.Words for Java
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
description: Learn how to export markdown by converting Word documents to Markdown with Aspose.Words for Java. This step-by-step guide covers table alignment, image handling, and more.
weight: 18
url: /java/document-loading-and-saving/saving-documents-as-markdown/
date: 2025-12-22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to Export Markdown with Aspose.Words for Java

## Introduction to Exporting Markdown in Aspose.Words for Java

In this step‑by‑step tutorial, **you’ll learn how to export markdown** from Word documents using Aspose.Words for Java. Markdown is a lightweight markup language that’s perfect for documentation, static site generators, and many publishing platforms. By the end of this guide you’ll be able to **convert Word to markdown**, customize table alignment, and **handle images in markdown** effortlessly.

## Quick Answers
- **What is the primary class for saving as Markdown?** `MarkdownSaveOptions`
- **Can images be embedded automatically?** Yes – set the images folder via `setImagesFolder`.
- **How do I control table alignment?** Use `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **What are the minimum requirements?** JDK 8+ and Aspose.Words for Java library.
- **Is a trial version available?** Yes, download it from the Aspose website.

## What is “how to export markdown”?
Exporting markdown means taking a rich‑text Word document (`.docx`) and producing a plain‑text `.md` file that preserves headings, tables, and images in Markdown syntax.

## Why use Aspose.Words for Java to convert docx with images?
Aspose.Words handles complex layouts, embedded pictures, and table structures without losing fidelity. It also gives you fine‑grained control over the Markdown output, such as table alignment and image folder management.

## Prerequisites

- Java Development Kit (JDK) installed on your system.
- Aspose.Words for Java library. You can download it from [here](https://releases.aspose.com/words/java/).

## Step 1: Create a simple Word document

First, we’ll build a tiny document that contains a table. This will let us demonstrate **customize table alignment** later.

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

In the snippet above we:

1. Create a new `Document`.
2. Use `DocumentBuilder` to insert a two‑cell table.
3. Apply **right** and **center** paragraph alignment inside each cell.
4. Save the file as Markdown using `MarkdownSaveOptions`.

## Step 2: Customize table content alignment

Aspose.Words lets you dictate how table cells are rendered in the final Markdown. You can force left, right, center alignment, or let the library decide automatically based on the first paragraph in each column.

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

By switching the `TableContentAlignment` property you control **customize table alignment** for the Markdown output.

## Step 3: Handle images when exporting to markdown

When a document contains pictures, you’ll want those images to appear correctly in the generated `.md` file. Set the folder where Aspose.Words should dump the extracted images.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Replace `"document_with_images.docx"` with the path to your source file and `"images_folder/"` with the location where you’d like the images stored. The resulting Markdown will contain image links that point to this folder, allowing you to **handle images in markdown** seamlessly.

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

## Common Issues and Solutions

| Issue | Solution |
|-------|----------|
| Images not appearing in the `.md` file | Verify that `setImagesFolder` points to a writable directory and that the folder is referenced correctly in the generated Markdown. |
| Table alignment looks off | Use `TableContentAlignment.AUTO` to let Aspose.Words infer the best alignment based on the first paragraph of each column. |
| Output file is empty | Ensure the `Document` object actually contains content before calling `save`. |

## Frequently Asked Questions

**Q: How do I install Aspose.Words for Java?**  
A: Aspose.Words for Java can be installed by including the library in your Java project. You can download the library from [here](https://releases.aspose.com/words/java/) and follow the installation instructions provided in the documentation.

**Q: Can I convert complex Word documents with tables and images to Markdown?**  
A: Yes, Aspose.Words for Java supports the conversion of complex Word documents with tables, images, and various formatting elements to Markdown. You can customize the Markdown output according to your document’s complexity.

**Q: How can I handle images in Markdown files?**  
A: Set the images folder path using the `setImagesFolder` method in `MarkdownSaveOptions`. Ensure that the image files are stored in the specified folder; Aspose.Words will generate the appropriate Markdown image links.

**Q: Is there a trial version of Aspose.Words for Java available?**  
A: Yes, you can obtain a trial version of Aspose.Words for Java from the Aspose website. The trial version allows you to evaluate the library’s capabilities before purchasing a license.

**Q: Where can I find more examples and documentation?**  
A: For more examples, documentation, and detailed information on Aspose.Words for Java, please visit the [documentation](https://reference.aspose.com/words/java/).

---

**Last Updated:** 2025-12-22  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}