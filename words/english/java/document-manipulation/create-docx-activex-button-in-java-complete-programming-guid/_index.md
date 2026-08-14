---
category: general
date: 2026-08-14
description: Create docx ActiveX button in Java with Aspose.Words. Learn how to add
  a form button in Word programmatically and save the document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: en
lastmod: 2026-08-14
og_description: Create docx ActiveX button in Java using Aspose.Words. This guide
  shows you how to add a form button in Word, configure it, and save the file.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Create docx ActiveX button in Java – step‑by‑step tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Create docx ActiveX button in Java – complete programming guide
url: /java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create docx ActiveX button in Java – complete programming guide

If you need to **create docx ActiveX button** in Java, this guide walks you through the entire process. You’ll see how to add a form button in Word, configure its properties, and produce a ready‑to‑use .docx file.

Working with ActiveX controls is a common requirement when automating legacy Word forms. In this tutorial you’ll learn to **add form button word** documents using the Aspose.Words for Java library, so you can embed interactive controls without manual editing.

## What you’ll need

Before you start, make sure you have:

* Java 17 or later (the code compiles with earlier versions, but Java 17 is recommended).
* Aspose.Words for Java 23.10 or newer – download the JAR from the Aspose website or add the Maven dependency.
* An IDE (IntelliJ IDEA, Eclipse, or VS Code) or a simple text editor and command‑line build tools.
* Basic knowledge of Java syntax and object‑oriented programming.

## How to create docx ActiveX button with Aspose.Words

The following steps show the exact sequence required to **create docx ActiveX button** objects and embed them in a Word document.

### Step 1: Set up the project and import Aspose.Words

Add the Aspose.Words dependency to your `pom.xml` if you use Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Or, if you prefer Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

After the dependency resolves, import the required classes in your Java source file:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

These imports give you access to `Document`, `DocumentBuilder`, and the `Forms2OleControl` API used to insert ActiveX controls.

### Step 2: Create a new blank document

Instantiate a `Document` object, which represents an empty Word file ready to receive content.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Creating the document first ensures that the subsequent builder operates on a clean canvas.

### Step 3: Initialize a DocumentBuilder

`DocumentBuilder` provides a fluent interface for inserting text, images, and controls. Attach it to the document you just created.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

The builder tracks the current cursor position inside the document, so the next insertion occurs exactly where you need it.

### Step 4: Insert an ActiveX CommandButton control

Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`. This method returns a `Forms2OleControl` instance that you can further configure.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

At this point the .docx file contains a placeholder for a button, but it has no visual caption or size yet.

### Step 5: Configure the button’s properties

Set the control’s name, caption, and layout attributes. These values determine how the button appears in Word and how you can reference it later via VBA or automation scripts.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Pro tip:** Word measures positions in points (1 pt ≈ 1/72 in). Adjust `setTop` and `setLeft` to align the button with surrounding content.

### Step 6: Save the document

Finally, write the document to disk. Use the `.docx` extension to keep the file in the modern Office Open XML format.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

When you open the resulting file in Microsoft Word, you’ll see a **Submit** button positioned at the coordinates you specified. Clicking the button in Word will not trigger any action unless you attach VBA code, but the control is fully functional for form‑based workflows.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| **Do I need a special Word version?** | ActiveX controls are supported in the desktop version of Microsoft Word on Windows. They are not available in Word for Mac or Word Online. |
| **Can I use this with `.doc` files?** | Yes. Save the document with a `.doc` extension (`document.save("ActiveXButton.doc")`). The same API works for the older binary format. |
| **What if the button doesn’t appear?** | Ensure that **File → Options → Trust Center → Trust Center Settings → ActiveX Settings** allows ActiveX controls. Also verify that the document isn’t opened in “Protected View”. |
| **Can I add other ActiveX controls?** | Absolutely. Replace `Forms2OleControlType.COMMAND_BUTTON` with `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, etc. |
| **Is there a size limit?** | The control size is limited only by the page layout. Very large dimensions may cause layout overflow. |

## Full, runnable example

Below is a complete Java class that you can copy, compile, and run. It includes all imports, the main method, and inline comments for clarity.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected result:** After running the program, `ActiveXButton.docx` appears in the working directory. Opening it in Microsoft Word shows a clickable **Submit** button positioned near the top‑left of the first page.

## Conclusion

You now know how to **create docx ActiveX button** objects in Java using Aspose.Words, and you’ve seen how to **add form button word** documents programmatically. The steps—setting up the project, creating a document, inserting the control, configuring its properties, and saving—cover the entire workflow from start to finish.

Next, you might explore:

* Adding VBA macros that respond to the button click.
* Embedding other ActiveX controls such as check boxes or list boxes.
* Automating the generation of multi‑page forms with several interactive elements.

Feel free to experiment with sizes, positions, and captions to match your specific form design requirements. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}