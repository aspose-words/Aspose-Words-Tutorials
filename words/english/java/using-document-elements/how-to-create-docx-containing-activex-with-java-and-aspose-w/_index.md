---
category: general
date: 2026-09-27
description: Create docx containing ActiveX in Java using Aspose.Words. Learn to insert
  an ActiveX command button step‑by‑step.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: en
lastmod: 2026-09-27
og_description: Create docx containing ActiveX in Java with Aspose.Words. Follow this
  guide to insert an ActiveX command button and save the document.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Create docx containing ActiveX in Java – complete guide
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: How to create docx containing ActiveX with Java and Aspose.Words
url: /java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create docx containing ActiveX with Java and Aspose.Words

If you need to **create docx containing ActiveX**, this guide shows you a complete solution. You will learn how to **insert ActiveX command button** into a Word file using Aspose.Words for Java, then save the result as a .docx that can be opened in Microsoft Word.

Generating a Word document programmatically saves you from manual editing and guarantees consistency across reports, contracts, or form templates. The steps below cover everything from project setup to handling common pitfalls, so you can integrate the technique into any Java application.

## Prerequisites

Before you start, make sure you have:

* Java Development Kit (JDK) 8 or newer installed.
* Maven 3.6+ (or another build tool you prefer).
* An Aspose.Words for Java license file (the free evaluation works for testing).
* Microsoft Word installed on the target machine if you want to verify the ActiveX control visually.

These items are required because Aspose.Words provides the API that creates the document, while Word is needed to render the ActiveX control.

## Step 1: Set up the Maven project

Create a new Maven project or add the Aspose.Words dependency to an existing `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Pro tip:** Keep the Aspose.Words version in sync with the official release notes to benefit from bug fixes and new ActiveX features.

## Step 2: Write the Java code that creates the document

Create a class named `ActiveXDocxCreator`. The code below includes all required imports, a `main` method, and detailed comments that explain each operation.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Why each line matters

* `Document` is the container for all Word content. Creating a fresh instance gives you a clean canvas.
* `DocumentBuilder` provides a fluent API to insert elements; it automatically tracks the insertion point.
* `insertForms2OleControl()` creates a generic OLE control placeholder. Aspose.Words treats it as an ActiveX container.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` tells Word that the placeholder must render as a CommandButton.
* `setCaption("Click Me")` defines the text displayed on the button.
* `setLeft` and `setTop` place the button relative to the page margins. Adjust these values to suit your layout.
* `setWidth` and `setHeight` are optional but improve the button’s appearance, especially when the default size is too small.
* `doc.save` writes the in‑memory structure to a physical .docx file that Word can open.

## Step 3: Verify the generated document

Open `output/ActiveXCommandButton.docx` in Microsoft Word:

1. The document should show a single page with a button labeled **Click Me** positioned near the top‑left corner.
2. If the button does not appear, check that **ActiveX controls are enabled** in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings → ActiveX Settings).
3. The button is functional only on Windows versions of Word that support ActiveX. On macOS or web‑based Word, the control will be displayed as a static image.

## Step 4: Handling common edge cases

| Situation | Reason | Recommended action |
|-----------|--------|--------------------|
| The button is missing after opening the file | Word’s security settings block ActiveX | Enable “Run all controls without restrictions” for trusted locations. |
| The generated .docx cannot be opened | Incompatible Aspose.Words version | Upgrade to the latest Aspose.Words release; older versions may not embed the required OLE parts correctly. |
| You need the button to execute a macro | ActiveX alone does not contain macro code | Combine the ActiveX control with a VBA macro that handles the `Click` event. Use the `DocumentBuilder.insertOleObject` method to embed a macro‑enabled template. |
| The layout is off on different page sizes | Coordinates are absolute points | Use `builder.getPageSetup().setPageWidth` and `setPageHeight` to standardize the page size before positioning the control. |

## Step 5: Extending the solution

You can insert other ActiveX controls by changing the `ControlType` enum:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words also supports inserting **ActiveX text boxes**, **list boxes**, and **combo boxes**. The same positioning methods (`setLeft`, `setTop`, `setWidth`, `setHeight`) apply.

If you need to place multiple controls, call `builder.insertForms2OleControl()` repeatedly and adjust each control’s coordinates accordingly.

## Complete source file

Below is the entire `ActiveXDocxCreator.java` file ready for copy‑and‑paste:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Running this program produces a **docx containing ActiveX** that you can distribute to end users who need interactive forms.

## Conclusion

You now know how to **create docx containing ActiveX** using Java and Aspose.Words, and how to **insert ActiveX command button** programmatically. The tutorial covered project setup, full source code, verification steps, and strategies for dealing with typical issues. 

From here you might explore:

* Adding VBA macros to respond to the button click.
* Embedding other ActiveX controls such as checkboxes or combo boxes.
* Automating the generation of multi‑page forms with dynamic data.

Experiment with different coordinates, sizes, and control types to fit your specific document layout. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Using OLE Objects and ActiveX Controls in Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}