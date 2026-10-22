---
category: general
date: 2026-10-16
description: Create a blank Word document with Java and learn how to add an ActiveX
  button, set its caption, and adjust its dimensions using Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add activex button
- set button caption
- set button dimensions
language: en
lastmod: 2026-10-16
og_description: Create a blank Word document with Java, then add an ActiveX button,
  set its caption, and define its dimensions using Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with an ActiveX button inserted
og_title: Create a blank Word document and embed an ActiveX button – Java guide
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document with Java and learn how to add an ActiveX
    button, set its caption, and adjust its dimensions using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button (Java)
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
title: Create a blank Word document and add an ActiveX button (Java)
url: /java/using-document-elements/create-a-blank-word-document-and-add-an-activex-button-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document and add an ActiveX button (Java)

If you need to **create a blank Word document** programmatically, this guide shows you how to do it with Java and Aspose.Words. You’ll also learn how to **add an ActiveX button**, **set button caption**, and **set button dimensions** so the control looks exactly as you expect.

This tutorial covers:

* Initializing an empty Word file with Aspose.Words for Java.  
* Inserting an ActiveX `CommandButton` control.  
* Configuring the button’s caption and size.  
* Saving the final `.docx` file.

You should have basic Java knowledge and a recent version of the Aspose.Words for Java library (the code works with 23.9 and later). No additional dependencies are required.

![Create a blank Word document with an ActiveX button](/images/activex-button-example.png){: .align-center alt="Create a blank Word document with an ActiveX button"}

## Create a blank Word document with Aspose.Words

The first step is to instantiate an empty `Document` object. This object represents the whole Word file in memory and provides the `DocumentBuilder` class for editing.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(doc);
        
        // The rest of the steps follow here...
```

**Why this matters:**  
Creating a blank document gives you a clean canvas, avoiding any hidden styles or sections that could interfere with later layout calculations.

## Add an ActiveX button to the document

Aspose.Words lets you embed legacy ActiveX controls via the `Forms2OleControl` class. The following code inserts a `CommandButton` control at the current cursor position.

```java
        // Step 2: Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Define the exact ActiveX class name (CommandButton)
        commandButton.setOleClassName("Forms.CommandButton.1");
```

**Tip:** The `setOleClassName` value `"Forms.CommandButton.1"` is the ProgID for the standard Microsoft Forms button. Using a different ProgID (e.g., `"Forms.CheckBox.1"`) would insert a different control type.

## Set button caption

A caption is the text that appears on the button face. You can change it at any time before saving the document.

```java
        // Step 3: Set the button's caption
        commandButton.setCaption("Click Me");
```

**Why you need this:** Users only understand a control when its purpose is clear. Setting a meaningful caption improves usability, especially when the document is opened in Word on Windows.

## Set button dimensions

Position and size are specified in points (1 point = 1/72 inch). Adjust the values to fit your layout.

```java
        // Step 4: Define button size and location
        commandButton.setLeft(100);    // distance from the left edge of the page
        commandButton.setTop(200);     // distance from the top edge of the page
        commandButton.setWidth(120);   // width of the button
        commandButton.setHeight(30);   // height of the button
```

**Common variations:**

| Scenario | Adjustment |
|----------|------------|
| Larger button for touch screens | Increase `setWidth` and `setHeight` proportionally |
| Centered button on the page | Calculate `left = (pageWidth - width) / 2` |
| Multiple buttons in a column | Increment `setTop` for each new button |

## Save the document containing the ActiveX button

Finally, write the document to disk. The `.docx` format preserves the ActiveX control for Windows versions of Microsoft Word.

```java
        // Step 5: Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

**Expected result:** Opening `ActiveXCommandButton.docx` in Word (Windows) shows a blank page with a clickable button labeled **Click Me** positioned 100 pt from the left margin and 200 pt from the top margin.

## Full, runnable example

Copy the entire class below into your IDE, add the Aspose.Words for Java JAR to the project classpath, and run it.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setOleClassName("Forms.CommandButton.1");

        // Set button caption
        commandButton.setCaption("Click Me");

        // Set button dimensions and position
        commandButton.setLeft(100);    // points from left edge
        commandButton.setTop(200);     // points from top edge
        commandButton.setWidth(120);   // width in points
        commandButton.setHeight(30);   // height in points

        // Save the document
        doc.save("ActiveXCommandButton.docx");
    }
}
```

Running the program produces `ActiveXCommandButton.docx` in the working directory. Open it with Microsoft Word (Windows) to verify that the button appears exactly as configured.

## Why this approach is recommended

* **Simplicity:** Only the core Aspose.Words API is used; no COM interop or additional libraries are required.  
* **Portability:** The code runs on any platform that supports Java, though the ActiveX control itself only works on Windows versions of Word.  
* **Maintainability:** All properties (caption, dimensions, position) are set through clear, self‑documenting methods, making future adjustments straightforward.

## Common pitfalls and how to avoid them

| Pitfall | Resolution |
|---------|------------|
| The button does not appear in Word on macOS or Linux | ActiveX controls are Windows‑only. Use a different control (e.g., a content control) for cross‑platform documents. |
| Caption is truncated | Ensure the button width is wide enough for the text; increase `setWidth` or use a shorter caption. |
| Button overlaps other content | Adjust `setTop` and `setLeft` values, or insert a new paragraph before the control to give it its own space. |

## Next steps

Now that you can **create a blank Word document**, **add an ActiveX button**, **set button caption**, and **set button dimensions**, you might explore:

* Adding event‑handling code via VBA macros (requires embedding a macro module).  
* Inserting multiple controls in a table layout for form‑like documents.  
* Using Aspose.Words’ **FormField** APIs for cross‑platform form solutions.

Experiment with different sizes, positions, and captions to fit your specific document design. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Add a watermark to a document using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}