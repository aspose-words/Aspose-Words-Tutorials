---
title: Loading Text Files with Aspose.Words for Java
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
description: Unlock the Power of Aspose.Words for Java. Learn to Load Text Documents, Manage Lists, Handle Spaces, and Control Text Direction.
weight: 13
url: /java/document-loading-and-saving/loading-text-files/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Loading Text Files with Aspose.Words for Java


## Introduction to Loading Text Files with Aspose.Words for Java

In this guide, we'll explore how to load text files using Aspose.Words for Java and manipulate them as Word documents. We'll cover various aspects such as detecting lists, handling spaces, and controlling text direction.

## Step 1: Detecting Lists

To load a text document and detect lists, you can follow these steps:

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

This code demonstrates how to load a text document with various list formats and use the `DetectNumberingWithWhitespaces` option to detect lists correctly.

## Step 2: Handling Spaces Options

To control leading and trailing spaces when loading a text document, you can use the following code:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

In this example, we load a text document and trim leading and trailing spaces using `TxtLeadingSpacesOptions.TRIM` and `TxtTrailingSpacesOptions.TRIM`.

## Step 3: Controlling Text Direction

To specify the text direction when loading a text document, you can use the following code:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

This code sets the document direction to auto-detection (`DocumentDirection.AUTO`) and loads a text document with Hebrew text. You can adjust the document direction as needed.

## Complete Source Code For Loading Text Files with Aspose.Words for Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Conclusion

In this guide, we've explored how to load text files using Aspose.Words for Java, detect lists, handle spaces, and control text direction. These techniques allow you to manipulate text documents effectively in your Java applications.

## FAQ's

### What is Aspose.Words for Java?

Aspose.Words for Java is a powerful document processing library that allows developers to create, manipulate, and convert Word documents programmatically in Java applications. It provides a wide range of features for working with text, tables, images, and other document elements.

### How can I get started with Aspose.Words for Java?

To get started with Aspose.Words for Java, follow these steps:
1. Download and install the Aspose.Words for Java library.
2. Refer to the documentation at [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) for detailed information and examples.
3. Explore the sample code and tutorials to learn how to use the library effectively.

### How do I load a text document using Aspose.Words for Java?

To load a text document using Aspose.Words for Java, you can use the `TxtLoadOptions` class and the `Document` class. Ensure that you specify the appropriate options for handling spaces and text direction as needed. Refer to the step-by-step guide in this article for a detailed example.

### Can I convert a loaded text document to other formats?

Yes, Aspose.Words for Java allows you to convert a loaded text document to various formats, including DOCX, PDF, and more. You can use the `Document` class to perform conversions. Check the documentation for specific conversion examples.

### How do I handle spaces in loaded text documents?

You can control how leading and trailing spaces are handled in loaded text documents using `TxtLoadOptions`. Options like `TxtLeadingSpacesOptions` and `TxtTrailingSpacesOptions` allow you to trim or preserve spaces as needed. Refer to the "Handling Spaces Options" section in this guide for an example.

### What is the significance of text direction in Aspose.Words for Java?

Text direction is essential for documents containing mixed scripts or languages, such as Hebrew or Arabic. Aspose.Words for Java provides options to specify the text direction, ensuring proper rendering and formatting of text in these languages. The "Controlling Text Direction" section in this guide demonstrates how to set the text direction.

### Where can I find more resources and support for Aspose.Words for Java?

For additional resources, documentation, and support, visit the [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/). You can also participate in the Aspose.Words community forums or contact Aspose support for assistance with specific issues or inquiries.

### Is Aspose.Words for Java suitable for commercial projects?

Yes, Aspose.Words for Java is suitable for both personal and commercial projects. It offers licensing options to accommodate various usage scenarios. Make sure to review the licensing terms and pricing on the Aspose website to choose the appropriate license for your project.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
