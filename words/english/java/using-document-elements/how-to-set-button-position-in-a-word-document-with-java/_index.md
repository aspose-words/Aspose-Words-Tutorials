---
category: general
date: 2026-09-24
description: Set button position in a Word document using Java and Aspose.Words. Learn
  how to insert button, add ActiveX control, and create Word document Java style.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: en
lastmod: 2026-09-24
og_description: Set button position in a Word document using Java. This guide shows
  how to insert button, add ActiveX control, and create Word document Java with Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Set button position in a Word document with Java – complete guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: How to set button position in a Word document with Java
url: /java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to set button position in a Word document with Java

If you need to **set button position** inside a Word file, this guide shows you a complete, runnable solution. Whether you are building a template that requires user interaction or automating a form, you’ll learn exactly **how to insert button** using Aspose.Words for Java and control its placement.

The tutorial covers everything you need to **add ActiveX control** to a Word document, explains how to **add button to Word**, and demonstrates the full process to **create Word document Java** style. No external references are required—just copy, run, and verify the result.

## Prerequisites

Before you start, make sure you have:

* Java 17 (or any Java 8+ runtime) installed.
* Maven or Gradle to manage dependencies.
* An Aspose.Words for Java license (the free trial works for evaluation).
* A basic understanding of Java syntax.

> **Pro tip:** Keep your Aspose.Words JARs in a `libs/` folder and add them to your project’s classpath to avoid version conflicts.

## Step 1: Set up the Maven project

Create a simple Maven project (or use Gradle) and add the Aspose.Words dependency:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Running `mvn clean compile` downloads the library and prepares the build path.

## Step 2: Create a new Word document

The first operation is to **create Word document java** style. You instantiate a `Document` object and a `DocumentBuilder` that lets you edit the file.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` class represents the entire .docx file, while `DocumentBuilder` provides a fluent API for inserting content.

## Step 3: How to insert button – add ActiveX control

Aspose.Words exposes the `Forms2OleControl` class for inserting legacy ActiveX controls such as a CommandButton. This step shows the exact way to **how to insert button** into the document.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

The `insertForms2OleControl` method returns a `Forms2OleControl` instance that you can configure. This is the core of the **add ActiveX control** process.

## Step 4: Set button position

Now we actually **set button position**. The control’s `setLeft` and `setTop` methods accept values in points (1 pt = 1/72 in). To align the button with typical screen coordinates, you can convert pixels to points (1 px ≈ 0.75 pt). In the example we place the button 100 px from the left edge and 150 px from the top edge.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Because the **set button position** logic is encapsulated here, you can reuse these lines whenever you need to move a control. Adjust the numbers to fit your layout requirements.

## Step 5: Define size and caption

A button without a label is confusing. Use `setWidth`, `setHeight`, and `setCaption` to give it a visible appearance.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

The size is also expressed in points, so we convert from pixels for consistency.

## Step 6: Save the document – complete the create Word document java flow

Finally, persist the file to disk. The path can be absolute or relative to the project root.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Running the program produces `CommandButtonDemo.docx` inside the `output` folder. Opening the file in Microsoft Word shows a clickable button positioned exactly where you set it.

### Expected output

* A `.docx` file named **CommandButtonDemo.docx**.
* Inside the document, a **CommandButton** labeled “Click Me” appears 100 px from the left margin and 150 px from the top margin.
* The button responds to clicks when the document is opened in Word (it will display a default ActiveX message unless you attach custom VBA code).

## Step 7: Common variations and edge cases

### Adding multiple buttons

If you need to **add button to Word** more than once, repeat steps 3‑5 with a new `Forms2OleControl` instance each time. Remember to adjust the `setTop` value so buttons don’t overlap.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Working without a license

Aspose.Words adds a watermark when used without a license. For production code, purchase a license and apply it at the start of `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Compatibility with older Office versions

ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To create a legacy file, change the save format:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Full source code (runnable)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Save the file as `src/main/java/CommandButtonDemo.java`, run `mvn exec:java -Dexec.mainClass=CommandButtonDemo`, and open the generated document to see the result.

## Frequently asked questions

**Q: Does this work with OpenJDK?**  
A: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation, including OpenJDK.

**Q: Can I change the button’s font or color?**  
A: ActiveX button appearance is controlled by the host application (Word). You can attach VBA code to modify properties at runtime, but the static appearance is limited to the default style.

**Q: What if I need to place the button inside a table cell?**  
A: Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`. The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop` for fine‑tuning.

## Conclusion

You now know how to **set button position** in a Word document using Java, how to **how to insert button**, how to **add ActiveX control**, and how to **add button to Word** while following best practices for **create Word document java** projects. The complete example demonstrates the entire workflow—from project setup to a saved `.docx` file containing a functional CommandButton.

### Next steps

* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`, `TEXTBOX`) to build richer forms.
* Combine the button with VBA macros for custom click handling.
* Use Aspose.Words’ mail‑merge feature to generate personalized documents that already contain interactive controls.

Happy coding, and enjoy automating Word documents with Java!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [How to Load Word Documents with Aspose.Words Java: Comprehensive Guide](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}