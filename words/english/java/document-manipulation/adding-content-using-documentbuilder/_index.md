---
title: Adding Content using DocumentBuilder in Aspose.Words for Java
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
description: Master Document Creation with Aspose.Words for Java. A Step-by-Step Guide to Adding Text, Tables, Images, and More. Create Stunning Word Documents Effortlessly.
weight: 26
url: /java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Adding Content using DocumentBuilder in Aspose.Words for Java


## Introduction to Adding Content using DocumentBuilder in Aspose.Words for Java

In this step-by-step guide, we'll explore how to use Aspose.Words for Java's DocumentBuilder to add various types of content to a Word document. We'll cover inserting text, tables, horizontal rules, form fields, HTML, hyperlinks, table of contents, inline and floating images, paragraphs, and more. Let's get started!

## Prerequisites

Before you begin, make sure you have the Aspose.Words for Java library set up in your project. You can download it from [here](https://releases.aspose.com/words/java/).

## Adding Text

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Tables

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Horizontal Rule

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Form Fields

### Text Input Form Field

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Check Box Form Field

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Combo Box Form Field

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Hyperlinks

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding a Table of Contents

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Images

### Inline Image

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Floating Image

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Adding Paragraphs

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Step 10: Moving the Cursor

You can control the cursor position within the document using various methods like `moveToParagraph`, `moveToCell`, and more. Here's an example:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

These are some common operations you can perform using Aspose.Words for Java's DocumentBuilder. Explore the library's documentation for more advanced features and customization options. Happy document creation!


## Conclusion

In this comprehensive guide, we have explored the capabilities of Aspose.Words for Java's DocumentBuilder to add various types of content to Word documents. We've covered text, tables, horizontal rules, form fields, HTML, hyperlinks, table of contents, images, paragraphs, and cursor movement.

## FAQ's

### Q: What is Aspose.Words for Java?

A: Aspose.Words for Java is a Java library that allows developers to create, modify, and manipulate Microsoft Word documents programmatically. It provides a wide range of features for document generation, formatting, and content insertion.

### Q: How can I add a table of contents to my document?

A: To add a table of contents, use the `DocumentBuilder` to insert a table of contents field into your document. Make sure to update the fields in the document after adding content to populate the table of contents. Here's an example:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: How do I insert images into a document using Aspose.Words for Java?

A: You can insert images, both inline and floating, using the `DocumentBuilder`. Here are examples of both:

#### Inline Image:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Floating Image:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Can I format text and paragraphs when adding content?

A: Yes, you can format text and paragraphs using the `DocumentBuilder`. You can set font properties, paragraph alignment, indentation, and more. Here's an example:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: How can I move the cursor to a specific location within the document?

A: You can control the cursor position using methods like `moveToParagraph`, `moveToCell`, and more. Here's an example:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

These are some common questions and answers to help you get started with Aspose.Words for Java's DocumentBuilder. If you have more questions or need further assistance, refer to the [library's documentation](https://reference.aspose.com/words/java/) or seek help from the Aspose.Words community and support resources.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
