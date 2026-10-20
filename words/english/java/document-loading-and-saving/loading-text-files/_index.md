---
title: How to Set Direction and Load Text Files with Aspose.Words for Java
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
description: Learn how to set direction, load txt files, trim spaces, and convert txt to docx using Aspose.Words for Java.
weight: 13
url: /java/document-loading-and-saving/loading-text-files/
date: 2025-12-27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to Set Direction and Load Text Files with Aspose.Words for Java

## Introduction to Loading Text Files with Aspose.Words for Java

In this guide, you’ll discover **how to set direction** when loading plain‑text documents and see practical ways to **load txt**, **trim spaces**, and **convert txt to docx** using Aspose.Words for Java. Whether you’re building a document‑conversion service or need fine‑grained control over list detection, this tutorial walks you through every step with clear explanations and ready‑to‑run code.

## Quick Answers
- **How do I set text direction for a loaded TXT file?** Use `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` or specify `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Can Aspose.Words detect numbered lists in plain text?** Yes – enable `DetectNumberingWithWhitespaces` in `TxtLoadOptions`.
- **How can I trim leading and trailing spaces?** Set `TxtLeadingSpacesOptions.TRIM` and `TxtTrailingSpacesOptions.TRIM`.
- **Is it possible to convert a TXT file to DOCX in one line?** Load the TXT with `TxtLoadOptions` and call `Document.save("output.docx")`.
- **What Java version is required?** Java 8+ is sufficient for Aspose.Words 24.x.

## What is “how to set direction” in Aspose.Words?
When a text file contains right‑to‑left scripts (e.g., Hebrew or Arabic), the library must know the reading order. The `DocumentDirection` enum lets you **set direction** manually or let Aspose auto‑detect it, ensuring correct layout and bidi formatting.

## Why use Aspose.Words for loading TXT files?
- **Accurate list detection** – handles numbered, bulleted, and whitespace‑delimited lists.
- **Fine‑grained space handling** – trim or preserve leading/trailing spaces.
- **Automatic text‑direction detection** – perfect for multilingual documents.
- **One‑step conversion** – load a `.txt` and save as `.docx`, `.pdf`, or any supported format.

## Prerequisites
- Java 8 or newer.
- Aspose.Words for Java library (add the Maven/Gradle dependency or the JAR to your project).
- Basic knowledge of Java I/O streams.

## Step‑by‑Step Guide

### Step 1: Detecting Lists (how to load txt)
To load a text document and automatically detect lists, create a `TxtLoadOptions` instance and enable list detection. The code below shows several list styles and enables whitespace‑aware numbering.

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

> **Pro tip:** If you only need basic list detection, you can skip the whitespace option – Aspose will still recognize standard `1.` and `1)` patterns.

### Step 2: Handling Spaces Options (how to trim spaces)
Leading and trailing spaces often cause formatting glitches. Use `TxtLeadingSpacesOptions` and `TxtTrailingSpacesOptions` to control this behavior.

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

> **Why it matters:** Trimming spaces prevents unwanted indentation in the resulting DOCX, making the document look clean without manual post‑processing.

### Step 3: Controlling Text Direction (how to set direction)
For right‑to‑left languages, set the document direction before loading. The example below loads a Hebrew text file and prints the bidi flag to confirm the direction.

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

> **Common pitfall:** Forgetting to set `DocumentDirection` can lead to garbled Arabic/Hebrew text where characters appear in the wrong order.

### Complete Source Code for Loading Text Files with Aspose.Words for Java
Below is the full, ready‑to‑run source that combines list detection, space handling, and direction control. You can copy‑paste it into a single class and run the three test methods individually.

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

## Common Issues and Solutions
| Issue | Cause | Fix |
|-------|-------|-----|
| Lists not detected | `DetectNumberingWithWhitespaces` left `false` for whitespace‑delimited lists | Enable `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Extra indentation after loading | Leading spaces were preserved | Set `TxtLeadingSpacesOptions.TRIM` |
| Hebrew text appears reversed | Document direction not set or set to `LEFT_TO_RIGHT` | Use `DocumentDirection.AUTO` or `RIGHT_TO_LEFT` |
| Output DOCX is empty | Input stream was not reset before second load | Re‑create `ByteArrayInputStream` for each load call |

## Frequently Asked Questions

### Q: What is Aspose.Words for Java?
A: Aspose.Words for Java is a powerful document processing library that allows developers to create, manipulate, and convert Word documents programmatically in Java applications. It supports a wide range of features, from simple text loading to complex formatting and conversion.

### Q: How can I get started with Aspose.Words for Java?
A: 1. Download and install the Aspose.Words for Java library. 2. Refer to the documentation at [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) for detailed information and examples. 3. Explore the sample code and tutorials to learn how to use the library effectively.

### Q: How do I load a text document using Aspose.Words for Java?
A: Use the `TxtLoadOptions` class together with the `Document` constructor. Specify options such as list detection, space handling, or text direction as demonstrated in the step‑by‑step sections above.

### Q: Can I convert a loaded text document to other formats?
A: Yes. After loading the TXT file into a `Document` object, call `doc.save("output.pdf")`, `doc.save("output.docx")`, or any other supported format.

### Q: How do I handle spaces in loaded text documents?
A: Control leading and trailing spaces with `TxtLeadingSpacesOptions` and `TxtTrailingSpacesOptions`. Set them to `TRIM` to remove unwanted whitespace, or to `PRESERVE` if you need to keep the original spacing.

### Q: What is the significance of text direction in Aspose.Words for Java?
A: Text direction ensures correct rendering of right‑to‑left scripts (Hebrew, Arabic, etc.). By setting `DocumentDirection`, you guarantee that bidi text is displayed properly in the resulting document.

### Q: Where can I find more resources and support for Aspose.Words for Java?
A: Visit the [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) for API references, code samples, and detailed guides. You can also join the Aspose community forums or contact Aspose support for specific questions.

### Q: Is Aspose.Words for Java suitable for commercial projects?
A: Yes. It offers licensing options for both personal and commercial use. Review the licensing terms on the Aspose website to choose the appropriate plan for your project.

## Conclusion
You now have a complete toolkit to **load txt files**, **detect lists**, **trim spaces**, and **set direction** when converting plain‑text into rich Word documents with Aspose.Words for Java. Apply these patterns to automate document workflows, improve multilingual support, and ensure clean, professional output every time.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}