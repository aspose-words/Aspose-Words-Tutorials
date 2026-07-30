---
title: How to create plain text file with Aspose.Words for Java
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
description: Learn how to create plain text file from Word documents using Aspose.Words for Java. This guide shows how to convert Word to txt, use tab indentation, and save word as txt.
weight: 24
url: /java/document-loading-and-saving/saving-documents-as-text-files/
date: 2025-12-24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to create plain text file with Aspose.Words for Java

## Introduction to Saving Documents as Text Files in Aspose.Words for Java

In this tutorial, you’ll learn **how to create plain text file** from a Word document using the Aspose.Words for Java library. Whether you need to **convert word to txt**, automate report generation, or simply extract raw text for further processing, this guide walks you through the entire workflow—right from document creation to fine‑tuning save options such as **use tab indentation** or add bidi marks. Let’s get started!

## Quick Answers
- **What is the primary class to create a document?** `Document` from Aspose.Words.
- **Which option adds bidi marks for right‑to‑left languages?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **How can I indent list items with tabs?** Set `ListIndentation.Character` to `'\t'`.
- **Do I need a license for development?** A free trial works for testing; a license is required for production.
- **Can I save the file with a custom name and path?** Yes—pass the full path to `doc.save()`.

## Prerequisites

Before we begin, make sure you have the following prerequisites in place:

- Java Development Kit (JDK) installed on your system.  
- Aspose.Words for Java library integrated into your project. You can download it from [here](https://releases.aspose.com/words/java/).  
- Basic knowledge of Java programming.

## Step 1: Create a Document

To **save word as txt**, we first need a `Document` instance. Below is a simple Java snippet that creates a document and writes a few lines of multilingual text:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

In this code we create a new document, add English, Hebrew, and Arabic text, and enable right‑to‑left formatting for the Hebrew paragraph.

## Step 2: Define Text Save Options

Next, we configure how the document will be saved as a plain text file. Aspose.Words provides the `TxtSaveOptions` class, which lets you control everything from bidi marks to list indentation.

### Example 1: Adding Bidi Marks (how to save txt with proper RTL support)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Setting `AddBidiMarks` to `true` ensures that right‑to‑left characters are correctly represented in the resulting **plain text file**.

### Example 2: Using Tab Character for List Indentation (use tab indentation)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Here we tell Aspose.Words to prepend a tab character (`'\t'`) before each list level, making the text output easier to read.

## Step 3: Save the Document as Text

Now that the save options are ready, you can persist the document as a **plain text file**:

```java
doc.save("output.txt", saveOptions);
```

Replace `"output.txt"` with the full path where you want the file stored.

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

## Common Issues and Solutions

| Issue | Solution |
|-------|----------|
| **Bidi characters appear as garbled text** | Ensure `setAddBidiMarks(true)` is enabled and the output file is opened with UTF‑8 encoding. |
| **List indentation looks wrong** | Verify `ListIndentation.Count` and `Character` are set to the desired values (tab `'\t'` or space `' '` ). |
| **File not created** | Check that the directory path exists and the application has write permissions. |

## Frequently Asked Questions

### How do I add bidi marks to the text output?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Can I customize the list indentation character?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Is Aspose.Words for Java suitable for handling multilingual text?

Yes, Aspose.Words for Java supports a wide range of languages and character encodings, making it ideal for extracting and saving multilingual content as plain text.

### How can I access more documentation and resources for Aspose.Words for Java?

You can find comprehensive documentation and resources on the Aspose.Words for Java Documentation page: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Where can I download Aspose.Words for Java?

You can download the library from the official site: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### What if I need to **convert word to txt** in a batch process?

Wrap the code shown above in a loop that loads each `.docx` file, applies the same `TxtSaveOptions`, and saves each as `.txt`. Ensure you manage resources by disposing of `Document` objects after each iteration.

### Does the API support saving directly to a stream instead of a file?

Yes, you can pass an `OutputStream` to `doc.save(outputStream, saveOptions)` for in‑memory processing or when integrating with web services.

---

**Last Updated:** 2025-12-24  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}