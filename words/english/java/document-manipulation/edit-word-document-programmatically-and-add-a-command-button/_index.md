---
category: general
date: 2026-11-15
description: Edit Word document programmatically to insert a command button. Learn
  how to add button, set command button name, and create form button Word in minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: en
lastmod: 2026-11-15
og_description: Edit Word document programmatically and insert a command button. This
  guide shows how to add button, set command button name, and create form button Word
  quickly.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Edit Word document programmatically – add a command button
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Edit Word document programmatically and add a command button
url: /java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Edit Word document programmatically and add a command button

If you need to **edit Word document programmatically**, the fastest way is to use the Aspose.Words API. This tutorial shows you exactly **how to add button** controls, configure their caption, and **set command button name** so the document can act as a simple form. By the end you’ll have a fully editable *.docx* that contains a functional command button ready for downstream processing.

You’ll learn how to **insert command button word**, **create form button word**, and manage button properties without opening Word manually. The only prerequisite is a basic Java development environment and the Aspose.Words for Java library.

## Prerequisites

- Java 17 or later (the code works with Java 8+ as well)
- Aspose.Words for Java (download from [Aspose.Words for Java](https://products.aspose.com/words/java/))
- An existing Word document (`input.docx`) that you want to modify
- Familiarity with Maven or Gradle to add the Aspose.Words dependency

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Step 1: Load the Word document

The first operation when you **edit Word document programmatically** is to load the source file into a `Document` object. This object represents the entire Word file in memory, allowing you to manipulate its contents.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:** Loading the document creates a DOM‑like structure that Aspose.Words can traverse and modify. Skipping this step would leave you without a target for the button insertion.

## Step 2: Create a `DocumentBuilder` to edit the document

A `DocumentBuilder` acts like a cursor inside the Word file. It lets you insert text, images, and form controls at the current position.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Tip:** If you need the button in a specific paragraph, move the builder first with `builder.moveToParagraph(index, true);`.

## Step 3: Insert a Forms2OleControl (command button)

Now we answer the central question **how to add button** in a Word file. The `insertForms2OleControl()` method creates a legacy *Forms2.0* command button, which is the most compatible control across Word versions.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Edge case:** The Forms2.0 control is visible only in the *Design Mode* of Word. If you need a newer ActiveX button, consider `insertOleControl()` instead, but the legacy control works for most automation scenarios.

## Step 4: Configure the button’s properties

After inserting the control, you can **set command button name** and **insert command button word** (caption) to make it user‑friendly.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Why these properties?**  
> - `setName` gives the button an identifier that VBA or external tools can reference.  
> - `setCaption` is the visible label, effectively **creating form button word** that end users click.

You can also adjust size, position, or add a macro by accessing the underlying OLE object, but those topics are beyond the scope of this quick guide.

## Step 5: Save the modified document

Finally, persist the changes to a new file. This step **creates form button word** in the output document.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Result:** Opening `output.docx` in Microsoft Word, you’ll see a button labeled “Submit”. When you switch Word to *Design Mode* (Developer → Design Mode), you can double‑click the button to attach a macro or simply use it as a placeholder in a form.

### Expected output

When you open the saved file:

- The cursor‑insertion point is replaced by a button.
- The button displays the caption **Submit**.
- The button’s internal name is **cmdSubmit**, which you can reference in VBA or external automation scripts.

## Common questions and variations

### How to add button to a specific paragraph?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### How to insert a button inside a table cell?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### What if I need a larger button?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### How to **insert command button word** using a different language (e.g., C#)?

The same logic applies; replace Java syntax with C# equivalents:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Pro tips and pitfalls

- **Pro tip:** Always call `builder.moveToDocumentEnd()` before inserting a button if you want it at the very end of the document.  
- **Watch out for:** Saving to the same file you opened can corrupt the document if an exception occurs. Use a separate output path as shown.  
- **Compatibility:** The legacy Forms2.0 button works in Word 2007‑2021. For Word on the web, consider using content controls instead.  
- **Performance:** Loading very large documents (>100 MB) may consume significant memory. Use `Document.load(InputStream, LoadOptions)` with `LoadOptions.setLoadFormat(LoadFormat.DOCX)` to limit resource usage.

## Full working example

Below is the complete, ready‑to‑run Java program. Copy it into a class named `WordButtonDemo.java`, adjust the file paths, and run `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Run the program and open `output.docx` to verify the button appears as expected.

## Conclusion

You now know how to **edit Word document programmatically** to **insert command button word**, **create form button word**, and **set command button name** using Aspose.Words for Java. This approach eliminates manual editing, enables batch processing of forms, and integrates seamlessly with automated workflows.

Next, you might explore:

- Adding VBA macros to the button (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Using **content controls** for richer form experiences (`builder.insertCheckBox()` etc.)  
- Automating bulk insertion across multiple documents with a loop  

Feel free to experiment with button size, position, and event handling to fit your specific scenario. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to add a command button programmatically in a Word document](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Create word document programmatically and add ActiveX button](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Add Command Button to Word Document with Aspose.Words – Complete Guide](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}