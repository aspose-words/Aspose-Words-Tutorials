---
category: general
date: 2026-08-07
description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
  to a Word document using Java. Learn the full code, configuration, and saving steps.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: en
lastmod: 2026-08-07
og_description: Aspose.Words ActiveX tutorial explains how to embed a CommandButton
  ActiveX control in a Word document using Java. Follow the complete example to create,
  configure, and save the document.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Aspose.Words ActiveX tutorial – Java step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
url: /java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words ActiveX tutorial – insert a CommandButton with Java

If you need to embed an ActiveX control in a Word file, this **Aspose.Words ActiveX tutorial** walks you through the entire process. You’ll see how to create a blank document, insert a CommandButton, set its properties, and save the result—all with plain Java code.

The example uses the Aspose.Words for Java API, which eliminates the need for Microsoft Office on the build server. By the end of this guide you can generate .docx files that contain fully functional CommandButton controls ready for use in Windows environments.

## Prerequisites

Before you start, make sure you have:

- Java Development Kit (JDK) 8 or newer installed.
- Maven or another build tool to manage dependencies.
- An Aspose.Words for Java license (or a temporary evaluation key) to avoid evaluation watermarks.
- Basic familiarity with Java syntax and object‑oriented programming.

> **Pro tip:** Add the Aspose.Words Maven dependency to your `pom.xml` to let the IDE resolve classes automatically:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Step 1: Create a new blank document and a `DocumentBuilder`

The `Document` class represents the Word file in memory, while `DocumentBuilder` provides a fluent API for editing the document. Initializing both objects prepares the document for further modifications.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:**  
`DocumentBuilder` tracks the current cursor position, so any subsequent insert operation—like adding a control—appears exactly where you intend.

## Step 2: Insert a CommandButton ActiveX control

Aspose.Words exposes `Forms2OleControl` for ActiveX objects. The `insertForms2OleControl` method requires the control type, which you specify through the `Forms2OleControlType` enumeration.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Explanation:**  
The inserted control is a COM‑based object that Word will render as a clickable button when the document is opened in a Windows environment.

## Step 3: Configure the button’s properties

After insertion, you can adjust the button’s name, caption, size, and position. These properties affect how the control looks and behaves inside Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Why these settings are important:**  

- **Name** – Enables VBA macros to reference the control (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Determines the visible label that users click.
- **Left / Top** – Controls placement relative to the page margins.
- **Width / Height** – Guarantees a consistent visual size across different screen resolutions.

## Step 4: Save the document

Calling `save` writes the in‑memory representation to a physical file. You can choose any supported format (`.docx`, `.doc`, `.pdf`, etc.). For this tutorial we keep the native Word format.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Result:**  
Opening `ActiveXDemo.docx` in Microsoft Word displays a CommandButton labeled **Submit** positioned at the specified coordinates. Clicking the button triggers the default behavior (no VBA code attached by default).

## Full source code

Putting the pieces together, the complete, runnable program looks like this:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Expected output

- A file named **ActiveXDemo.docx** located in the `output` folder.
- When opened in Microsoft Word (Windows), the document shows a clickable **Submit** button at the defined position.
- The button can be selected, moved, or linked to VBA code via the Word UI (Developer → Properties).

## Handling common variations

| Scenario | Adjustment |
|----------|------------|
| **Save as .doc** (legacy format) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Add an event handler** | Word does not expose ActiveX events through Aspose.Words. You must add VBA code manually after the document is generated. |
| **Multiple controls** | Repeat the insert/configure block with different `setName` and `setCaption` values. |
| **Different control type (e.g., CheckBox)** | Use `Forms2OleControlType.CHECKBOX` in the `insertForms2OleControl` call. |
| **Non‑Windows platforms** | ActiveX controls render only on Windows Word. For cross‑platform solutions, consider content controls (`StructuredDocumentTag`). |

## Best practices and pitfalls

- **License early** – Register your Aspose.Words license before creating the `Document` to avoid evaluation prompts.
- **Coordinate system** – Positions are measured in points (1 pt = 1/72 in). Convert from pixels or centimeters if your UI design uses those units.
- **File paths** – Use absolute paths or Java’s `Paths` API to avoid `FileNotFoundException` when the output directory does not exist.
- **Thread safety** – `Document` and `DocumentBuilder` are not thread‑safe. Create separate instances per thread if you generate documents in parallel.
- **Testing** – Verify the generated document on the target Word version (e.g., Word 2016, Word 365) because older versions may display ActiveX controls differently.

## Conclusion

This **Aspose.Words ActiveX tutorial** demonstrates how to programmatically add a CommandButton control to a Word document using Java. You learned how to:

1. Initialize a `Document` and `DocumentBuilder`.
2. Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
3. Set the button’s name, caption, size, and position.
4. Save the document as a .docx file that contains the ActiveX control.

From here you can explore additional control types, automate VBA macro injection, or combine ActiveX controls with other Aspose.Words features such as mail‑merge and content controls. Experiment with different layouts and integrate the generated documents into your larger Java‑based reporting pipeline.

---


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convert Word to RTF with Aspose.Words for Java Tutorial](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}