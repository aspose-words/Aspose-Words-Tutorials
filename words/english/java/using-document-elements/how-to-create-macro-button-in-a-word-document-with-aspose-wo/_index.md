---
category: general
date: 2026-11-22
description: Create macro button in a Word document using Java. Learn to insert command
  button, set button text, and link macro to button for interactive documents.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: en
lastmod: 2026-11-22
og_description: Create macro button in a Word document using Java. This tutorial shows
  how to insert command button, set button text, and link macro to button for full
  interactivity.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Create a macro button in a Word document with Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: How to create macro button in a Word document with Aspose.Words for Java
url: /java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create macro button in a Word document with Aspose.Words for Java

If you need to **create macro button** in a Word file, this guide walks you through the exact steps required. You’ll learn how to **insert command button**, **set button text**, and **link macro to button** so the document becomes fully interactive.

Developers often embed OLE controls to trigger VBA macros from within a document. This tutorial covers the complete workflow, from project setup to a runnable Java example that adds an **interactive button** to a .docx file. No external scripts are needed—everything runs inside the Java process.

## Prerequisites

Before you start, make sure you have:

* JDK 17 or later installed.
* Maven 3.8+ (or Gradle) for dependency management.
* Aspose.Words for Java 23.9 or newer – the library provides the `DocumentBuilder` and OLE control APIs.
* Basic familiarity with Java and VBA macros.

If any of these items are missing, install them first; the rest of the tutorial assumes they are available.

## How to create macro button with Aspose.Words for Java

The core of the solution consists of four actions:

1. **Insert command button** OLE control into the document.
2. **Set button text** (caption) that the user sees.
3. **Link macro to button** so clicking runs the desired VBA routine.
4. **Save the document** with the embedded macro.

Each action is explained in its own section below.

### Step 1: Insert command button into the document

`DocumentBuilder.insertForms2OleControl` creates an OLE control of the specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words to generate a command button that can host a macro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Why this matters:** The OLE control acts as a container for the macro. Without inserting it, there is no visual element for the user to click.

### Step 2: Set button text (caption)

The caption is the visible label on the button. Use `setCaption` to define what the user sees.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Why this matters:** Clear button text improves usability. The `setCaption` method updates the OLE control’s `Caption` property, which Word renders as the button label.

### Step 3: Link macro to button

A macro is identified by its name, for example `MyMacro`. The `setOnClick` method stores this name in the button’s `OnClick` event handler.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Why this matters:** Linking a macro creates the interactive behavior. When the user clicks the button in Word, the associated VBA routine executes.

### Step 4: Add interactive button to a Word document

After configuring the OLE control, you may want to position it, resize it, or add surrounding text. The `DocumentBuilder` continues to operate on the document, so you can insert paragraphs before or after the button.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Why this matters:** Saving as `.docm` preserves the macro code. If you save as `.docx`, the macro reference is lost.

## Full runnable example

Below is the complete Java program, including imports, exception handling, and comments that explain each step. Copy the code into a Maven project with the Aspose.Words dependency and run it.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Expected output

Running the program generates `MacroButtonDemo.docm`. Opening the file in Microsoft Word shows:

* A paragraph that reads *“Press the button to execute the macro:”*.
* A button labeled **Run Report** directly below the paragraph.
* When you click the button, Word attempts to run the macro `MyMacro`. (You must add the actual VBA code to the document manually or via another automation step.)

If the macro does not exist, Word displays a security warning, which is standard behavior for macro‑enabled documents.

## Common variations and edge cases

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Different button caption** | Change the string passed to `setCaption`. |
| **Multiple buttons** | Call `insertForms2OleControl` repeatedly, each with its own `setCaption` and `setOnClick`. |
| **Custom macro names** | Replace `"MyMacro"` with any valid VBA procedure name, e.g., `"ExportToExcel"`. |
| **Button size constraints** | Adjust `setWidth` and `setHeight` values; Word respects the points you provide. |
| **Embedding the macro programmatically** | Use `Document.getBuiltInDocumentProperties().add("Macros", …)` or a separate VBA injection step; Aspose.Words does not write VBA code itself. |

**Pro tip:** Always test the generated `.docm` on a machine with macro security set to *Enable all macros* for development. In production, sign the macro with a trusted certificate to avoid security prompts.

## Troubleshooting checklist

* **Button does not appear** – Verify that the document is saved as `.docm` and opened in a Word version that supports OLE controls.
* **Macro does not run** – Ensure the macro name matches exactly, including case, and that the macro exists in the document’s VBA project.
* **Button caption is truncated** – Increase the button width using `setWidth` to accommodate longer text.
* **Unexpected layout shift** – Use `builder.moveTo` to position the cursor precisely before inserting the control.

## Conclusion

You now know how to **create macro button** in a Word document using Java, **insert command button**, **set button text**, and **link macro to button** for full interactivity. The complete example demonstrates every required API call, explains why each step matters, and provides guidance for common variations.

Next, you might explore:

* **Add interactive button** to existing templates instead of a new document.
* **Programmatically inject VBA code** using the Open XML SDK or a secondary automation tool.
* **Combine multiple OLE controls** (checkboxes, list boxes) to build rich forms.

Experiment with different captions, macro names, and button sizes to fit your specific use case. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to insert command button in a Word document using Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [How to set button position in a Word document with Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [How to Insert ActiveX Button in Word – Set Button Caption](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}