---
title: Saving Documents as Text Files in Aspose.Words for Java
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
description: Learn how to save documents as text files in Aspose.Words for Java. Follow our step-by-step guide with Java code examples.
weight: 24
url: /java/document-loading-and-saving/saving-documents-as-text-files/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Saving Documents as Text Files in Aspose.Words for Java


## Introduction to Saving Documents as Text Files in Aspose.Words for Java

In this tutorial, we will explore how to save documents as text files using the Aspose.Words for Java library. Aspose.Words is a powerful Java API for working with Word documents, and it provides various options for saving documents in different formats, including plain text. We will cover the steps to achieve this and provide sample Java code along the way.

## Prerequisites

Before we begin, make sure you have the following prerequisites in place:

- Java Development Kit (JDK) installed on your system.
- Aspose.Words for Java library integrated into your project. You can download it from [here](https://releases.aspose.com/words/java/).
- Basic knowledge of Java programming.

## Step 1: Create a Document

To save a document as a text file, we first need to create a document using Aspose.Words. Here's a simple Java code snippet to create a document with some content:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In this code, we create a new document and add some text to it, including text in different languages.

## Step 2: Define Text Save Options

Next, we need to define the text save options that specify how the document should be saved as a text file. We can configure various settings such as adding bidi marks, list indentation, and more. Let's look at two examples:

### Example 1: Adding Bidi Marks

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

In this example, we create a `TxtSaveOptions` object and set the `AddBidiMarks` property to `true` to include bidi marks in the text output.

### Example 2: Using Tab Character for List Indentation

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Here, we configure the save options to use a tab character for list indentation with a count of 1.

## Step 3: Save the Document as Text

Now that we have defined the text save options, we can save the document as a text file. The following code demonstrates how to do this:

```java
doc.save("output.txt", saveOptions);
```

Replace `"output.txt"` with the desired file path where you want to save the text file.

## Complete Source Code For Saving Documents as Text Files in Aspose.Words for Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Conclusion

In this tutorial, we've learned how to save documents as text files in Aspose.Words for Java. We covered the steps to create a document, define text save options, and save the document in text format. Aspose.Words provides extensive flexibility when it comes to saving documents, allowing you to tailor the output to your specific requirements.

## FAQ's

### How do I add bidi marks to the text output?

To add bidi marks to the text output, set the `AddBidiMarks` property of `TxtSaveOptions` to `true`. For example:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Can I customize the list indentation character?

Yes, you can customize the list indentation character by configuring the `ListIndentation` property of `TxtSaveOptions`. For example, to use a tab character for list indentation, you can do the following:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Is Aspose.Words for Java suitable for handling multilingual text?

Yes, Aspose.Words for Java is suitable for handling multilingual text. It supports various languages and character encodings, making it a versatile choice for working with documents in different languages.

### How can I access more documentation and resources for Aspose.Words for Java?

You can find comprehensive documentation and resources for Aspose.Words for Java on the Aspose documentation website: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Where can I download Aspose.Words for Java?

You can download the Aspose.Words for Java library from the Aspose website: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
