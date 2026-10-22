---
category: general
date: 2026-10-07
description: Create ActiveX command button in Java and programmatically add command
  button to Word docs. Learn how to set button left top positions.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: en
lastmod: 2026-10-07
og_description: Create ActiveX command button in Java to embed interactive controls
  in your Word documents. Learn how to programmatically add command button, set its
  position, and customize its appearance.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Create ActiveX command button in Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: How to create ActiveX command button in Java
url: /java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create ActiveX command button in Java

If you need to **create ActiveX command button** in a Word document using Java, this guide shows you exactly how. You’ll see a complete, runnable example that **programmatically adds a command button**, positions it with `setLeft` and `setTop`, and saves the result as a `.docx` file.

Embedding an interactive button lets you build forms, automate workflows, or collect user input directly inside a Word file. The steps below cover everything from project setup to final verification, so you can copy the code into your own project without missing a detail.

## Prerequisites

Before you start, make sure you have:

- JDK 17 or newer installed  
- Maven 3.8+ (or your preferred build tool)  
- Aspose.Words for Java 23.9 or later – the library that provides `DocumentBuilder` and OLE control support  
- Basic familiarity with Java syntax and object‑oriented concepts  

If you’re using Maven, add the dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Pro tip:** Use the latest Aspose.Words version to benefit from bug fixes and new OLE features.

## Step 1: Create a new empty document and a DocumentBuilder

The first step to **create ActiveX command button** is to instantiate a blank `Document` and a `DocumentBuilder`. The builder gives you a fluent API for inserting content, including OLE controls.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` represents the Word file in memory, while `DocumentBuilder` acts as a cursor that lets you place elements precisely where you need them.

## Step 2: Insert an OLE command button control

ActiveX controls are inserted as OLE objects. Aspose.Words supplies the `Forms2OleControl` class for this purpose.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

When you call `insertForms2OleControl()`, Aspose automatically creates a placeholder shape that will host the ActiveX button.

## Step 3: Configure the button’s properties

Now you **programmatically add command button** details such as its ProgID, caption, and size. The most common ProgID for a command button is `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### How to set button left top

Positioning the button is where the secondary keyword **how to set button left top** becomes relevant. The `setLeft` and `setTop` methods accept values measured in points (1 point = 1/72 in).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Adjust these numbers to fit your layout. For example, to align the button with a table cell, calculate the cell’s coordinates and pass them to `setLeft`/`setTop`.

## Step 4: Save the document

Finally, write the document to disk. The file will contain the ActiveX button ready for interaction when opened in Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Running the `main` method produces `CommandButton.docx`. Open the file in Word, enable content if prompted, and you’ll see a clickable button labeled **Click Me** positioned at the coordinates you specified.

![Create ActiveX command button in Java](/images/activex-button-screenshot.png){.center width=600 alt="Create ActiveX command button in Java screenshot showing the button inside the Word document"}

## Common variations and edge cases

### Adding multiple buttons

If you need several buttons, repeat **Step 2** and **Step 3** for each control. Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.

### Changing button behavior

ActiveX buttons can run VBA macros when clicked. To attach a macro, set the `setOnAction` property with the macro name:

```java
commandButton.setOnAction("MyMacro");
```

Make sure the target document contains the corresponding VBA module; otherwise Word will display an error.

### Compatibility notes

- The button works only in desktop versions of Word that support ActiveX (e.g., Word for Windows). It will appear as a static image in Word for Mac or online editors.  
- If you target a mixed environment, consider using a **content control** (`RichTextContentControl`) instead of an ActiveX control.

## Full source code for reference

Below is the complete, self‑contained example that you can copy into a new Maven project and run immediately.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Expected output:** After execution, you’ll find `CommandButton.docx` in your project’s working directory. Opening the file in Microsoft Word shows a button at the specified location with the caption “Click Me”.

## Conclusion

You now know how to **create ActiveX command button** in Java, **programmatically add command button** to a Word document, and precisely control its layout using **how to set button left top** methods. This technique opens the door to rich, interactive Word forms that can trigger macros, launch external applications, or collect user input directly inside the document.

### Next steps

- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.  
- Combine multiple controls with a VBA module to implement full‑featured forms.  
- Replace ActiveX with content controls if you need cross‑platform compatibility.  

Feel free to experiment with size, caption, and positioning to match your UI design. If you run into issues, double‑check that the Aspose.Words version you’re using supports OLE controls, and verify that Word’s security settings allow ActiveX execution. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Embedding OLE Objects and ActiveX Controls in Word Documents](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}