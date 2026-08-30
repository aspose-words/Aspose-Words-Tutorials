---
category: general
date: 2026-07-26
description: How to insert ActiveX button in a Word document using Aspose.Words –
  learn to set button caption, position, and size in just a few lines.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: en
lastmod: 2026-07-26
og_description: How to insert ActiveX button in a Word document with Aspose.Words.
  Follow this step‑by‑step tutorial to set button caption, position, and size.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: How to Insert ActiveX Button in Word – Quick Guide
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: How to Insert ActiveX Button in Word – Set Button Caption
url: /java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to Insert ActiveX Button in Word – Set Button Caption

Ever wondered **how to insert ActiveX** controls into a Word file without opening the UI? You're not the only one. In many enterprise apps you need a clickable button that runs a macro, and doing it programmatically saves hours. This guide shows you exactly **how to insert ActiveX** CommandButton using Aspose.Words for Java, and—yes—how to **set button caption** so the user knows what to click.

We'll walk through the whole process: from setting up the library, creating a fresh document, dropping the button, tweaking its size and location, giving it a friendly caption, and finally saving the file. By the end you’ll have a runnable `.docx` that opens in Word with a fully functional ActiveX button ready to fire your macro.

---

## What You’ll Learn

- Install and reference Aspose.Words in a Java project.  
- Create a new `Document` and `DocumentBuilder`.  
- **Insert ActiveX** CommandButton control with a single line of code.  
- **Set button caption**, adjust its position, and define its dimensions.  
- Save the document and open it in Word to see the result.

No prior experience with ActiveX is required; just basic Java knowledge and a copy of Aspose.Words.

---

## Prerequisites

- Java 8 or newer installed on your machine.  
- Maven or Gradle for dependency management (we’ll show the Maven snippet).  
- A licensed or evaluation copy of **Aspose.Words for Java** (the free trial works fine for this demo).  
- Microsoft Word (any recent version) to test the generated file.

---

## Step 1: Set Up Aspose.Words in Your Project

First things first—add the Aspose.Words dependency. If you use Maven, drop this into your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gradle users can add:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

After a quick `mvn clean install` (or `gradle build`) the library will be on your classpath and you’re ready to code.

---

## Step 2: Create a New Document and Builder

A `Document` represents the whole Word file, while `DocumentBuilder` lets you edit it. Think of the builder as a pen that draws on a fresh canvas.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Why start with a blank document? It guarantees you have full control over every element you add, and there’s no hidden formatting to surprise you later.

---

## Step 3: Insert the ActiveX CommandButton Control

Now for the star of the show. Aspose.Words exposes `insertForms2OleControl` which can place any ActiveX control you specify. Here we ask for a **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

The method returns a `Forms2OleControl` object, giving you programmatic access to the button’s properties. This is where **how to insert activex** becomes a one‑liner—no fiddling with low‑level COM APIs.

---

## Step 4: Position, Size, and Set Button Caption

A button that floats in the middle of the page isn’t very useful. You’ll want to place it where users expect it, give it a sensible size, and—most importantly—**set button caption** so they know what clicking will do.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Why these numbers?** Word uses points (1 pt ≈ 1/72 inch). `100 pt` ≈ 1.4 in from the left, `150 pt` ≈ 2.1 in from the top—roughly the centre of a standard A4 page. Adjust them to suit your layout.

Setting the caption is crucial; without it the button looks like a blank rectangle. The `setCaption` method accepts any string, so you can localise it later if needed.

---

## Step 5: Save the Document

Finally, write the document to disk. You can choose any folder you like; just make sure the path exists.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

When you open `ActiveXButton.docx` in Word, you’ll see a nicely placed button labeled **“Click Me.”** If you double‑click it, Word will prompt you to enable macros (since ActiveX controls are considered macro‑enabled). From there you can bind a VBA routine to the button’s `Click` event.

---

## Edge Cases & Tips You Might Miss

- **Macro‑Enabled Format**: Word disables ActiveX controls in plain `.docx` files unless the user enables macros. If you need the button to work out‑of‑the‑box, consider saving as `.docm` (macro‑enabled) by using `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibility**: Older versions of Word (pre‑2007) use the binary `.doc` format. Aspose.Words can save to that format, but the control’s properties may render slightly differently.
- **Security Settings**: Some corporate environments lock down ActiveX. If your button doesn’t appear, check Word’s Trust Center → ActiveX Settings.
- **Multiple Buttons**: Want more than one? Just repeat the `insertForms2OleControl` call and adjust each button’s `Left`/`Top` values. Keep track of the returned objects so you can set individual captions.
- **Styling the Caption**: The caption inherits the default font. To change it, you’d need to edit the underlying XML or apply a Word style after insertion—beyond the scope of this quick guide, but doable with Aspose.Words’ `ParagraphFormat` API.

---

## Full Working Example

Below is the complete, ready‑to‑run Java class. Copy‑paste it into your IDE, adjust the output path, and hit **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Expected output**: After running, the console prints the save location. Opening the generated file in Word shows a button placed roughly in the middle of the page, labeled “Click Me”. Clicking it will trigger the standard ActiveX click event (you’ll need to attach a VBA macro to respond).

---

## Conclusion

You now know **how to insert ActiveX** CommandButton controls into a Word document programmatically with Aspose.Words, and you’ve seen exactly how to **set button caption**, position, and size the control. This approach eliminates manual UI work, integrates cleanly into automated report generators, and gives you full control over the


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert an Image into Word Document Header | Aspose.Words for .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}