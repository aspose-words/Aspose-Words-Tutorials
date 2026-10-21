---
category: general
date: 2026-09-18
description: Create blank document in Java and add an ActiveX button. Learn how to
  insert command button, build an interactive form, and save a Word document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: en
lastmod: 2026-09-18
og_description: Create blank document in Java and embed an ActiveX command button.
  Follow this step‑by‑step guide to build an interactive form and save the Word file.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Create blank document with an interactive command button in Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Create blank document with an interactive command button in Word using Java
url: /java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank document with an interactive command button in Word using Java

If you need to **create blank document** that contains a clickable button, this guide shows you exactly how to do it with Aspose.Words for Java. You’ll learn to build an interactive form, add an ActiveX button, and finally save the Word file—all in a few concise steps.

Embedding a command button turns a static .docx into a functional form that end users can interact with directly inside Microsoft Word. This tutorial also covers **how to insert command button**, handling common pitfalls, and extending the solution for more complex forms.

## Prerequisites

Before you start, make sure you have:

* Java 17 or later (the code compiles with JDK 17+)
* Aspose.Words for Java 23.9 or newer – the library provides `Document`, `DocumentBuilder`, and `Forms2OleControl`.
* An IDE or build tool (Maven/Gradle) that can add the Aspose.Words dependency.
* Basic knowledge of Java syntax and Word document concepts.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Step 1: Create a blank document

The first operation is to instantiate a new `Document` object. This object represents an empty Word file ready for content.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Creating a blank document gives you a clean canvas, which is essential when you want to **create word document** programmatically without any pre‑existing template.

## Step 2: Initialize a DocumentBuilder

`DocumentBuilder` is the primary class for adding text, tables, and form controls. It works on the `Document` you just created.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

The builder maintains the current insertion point, so subsequent commands affect the correct location in the file.

## Step 3: Insert a Forms2Ole command button control

Aspose.Words exposes the `Forms2OleControl` class for ActiveX controls. To **add activex button**, you request a `COMMANDBUTTON` type from the builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

The `insertForms2OleControl` method inserts the control at the builder’s current cursor location. Because the control is an ActiveX object, it works only in the desktop version of Microsoft Word, not in Word Online.

## Step 4: Configure the button’s appearance and position

You can set the button’s caption, size, and location using the control’s setters. Position values are measured in points (1 point = 1/72 inch).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Why configure these properties?* Setting `Top` and `Left` ensures the button appears where you expect on the page, while `Caption` defines the user‑visible label. If you skip width/height, Word assigns default dimensions, which may not match your design.

### Pro tip
If you plan to add multiple controls, call `builder.moveToDocumentEnd()` before each insertion to avoid overlapping objects.

## Step 5: Save the document with the embedded command button

Finally, write the document to disk. The file extension must be `.docx` (or `.doc` for older Word versions) to preserve the ActiveX control.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

When you open `CommandButton.docx` in Microsoft Word, you’ll see a button labeled **Click Me**. Clicking it will trigger the default ActiveX action (which, by default, does nothing). You can later attach a macro or VBA script to define custom behavior.

## How to insert command button into an existing form (optional)

If you already have a form with text fields and want to **create interactive form** that includes a button, follow these extra steps:

1. Load the existing document: `Document doc = new Document("ExistingForm.docx");`
2. Move the builder to the desired location: `builder.moveToParagraph(5, 0); // 6th paragraph, first node`
3. Insert the button as shown in Step 3.
4. Adjust the button’s `Top`/`Left` based on the paragraph’s layout.

This approach lets you enrich any pre‑built Word template with an ActiveX button without recreating the whole file.

## Edge cases and troubleshooting

| Situation | What to check | Recommended fix |
|-----------|---------------|-----------------|
| Button does not appear in Word | Ensure you opened the file in the desktop version of Word (Word Online strips ActiveX). | Open the file in Word 2016+ desktop. |
| Caption is truncated | Verify that the button width is large enough to contain the text. | Increase `setWidth` until the caption fits. |
| Save throws `IOException` | Confirm the output directory exists and you have write permissions. | Create the directory or run the program with elevated rights. |
| Multiple buttons overlap | The builder’s cursor may not have moved after the previous insertion. | Call `builder.moveToDocumentEnd()` before inserting each new control. |

## Full runnable example

Below is a complete, self‑contained Java program that you can copy, compile, and run. It demonstrates **create blank document**, **add activex button**, and **save word document** in one flow.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output**

```
Document created: CommandButton.docx
```

Opening `CommandButton.docx` shows a single page with a button labeled **Click Me** positioned 100 pt from the top and left edges.

## Conclusion

You now know how to **create blank document**, embed an **ActiveX button**, and turn a plain Word file into an **interactive form**. By mastering **how to insert command button**, you can extend this pattern to add checkboxes, combo boxes, or even custom VBA‑driven logic.

Next, consider exploring these related topics:

* **Create interactive form** with text fields (`builder.insertField`)  
* **Add activex button** that runs a VBA macro (`builder.insertOleObject`)  
* **Create word document** from a template using `Document(docTemplatePath)`  
* Converting the resulting .docx to PDF while preserving the button (note: PDF will render the button as a static image).

Feel free to experiment with button size, position, and caption to match your UI design. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Vba Project in Word Document](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}