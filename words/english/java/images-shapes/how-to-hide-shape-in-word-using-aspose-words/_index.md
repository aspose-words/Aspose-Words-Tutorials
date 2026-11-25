---
category: general
date: 2026-11-25
description: Hide shape in Word with Aspise.Words and learn to create Word document
  aspose while you insert rectangle shape word in just a few lines of code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: en
lastmod: 2026-11-25
og_description: Hide shape in Word using Aspose.Words. This tutorial shows you how
  to create Word document aspose, insert rectangle shape word and hide it programmatically.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Hide shape in Word with Aspose.Words – quick step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: How to hide shape in Word using Aspose.Words
url: /java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to hide shape in Word using Aspose.Words

If you need to **hide shape in Word** while generating documents programmatically, Aspose.Words makes it effortless. In this guide you’ll see exactly how to create a Word document aspose, insert rectangle shape word, and then hide that shape so it doesn’t appear in the layout. The complete, runnable example is provided so you can copy‑paste it into your IDE and see the result immediately.

You’ll finish this tutorial with a Word file that contains a hidden rectangle—useful for placeholders, conditional content, or metadata that should stay invisible to the reader. No external tools are required beyond the Aspose.Words for Java (or .NET) library.

## What you’ll learn

* How to **create a Word document aspose** from scratch.  
* How to **insert rectangle shape word** using the `DocumentBuilder`.  
* How to set the shape’s `hidden` property so it is not rendered in the final layout.  
* How to verify that the shape is hidden and how to unhide it if needed.  

### Prerequisites

* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous).  
* Aspose.Words for Java 24.x (the latest version at the time of writing).  
* An IDE such as IntelliJ IDEA, Eclipse, or VS Code.  

> **Pro tip:** Use the free temporary license from Aspose if you don’t have a commercial one yet. The library works without a license for evaluation, but a license removes evaluation watermarks.

## Hide shape in Word with Aspose.Words

The core steps are:

1. **Create a new `Document`.**  
2. **Insert a rectangle shape** using `DocumentBuilder`.  
3. **Mark the shape as hidden** so it does not appear when the file is opened.  

Each step is explained below with code and reasoning.

### Step 1: Create a Word document aspose

First, instantiate a blank `Document` and a `DocumentBuilder`. The builder provides a fluent API for adding content, including shapes.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
Creating a fresh `Document` gives you a clean canvas. The `DocumentBuilder` is the recommended way to modify the document because it automatically tracks the current insertion point and handles section/page management for you.

### Step 2: Insert rectangle shape word

Now we add a rectangle shape. The `insertShape` method requires the shape type and its dimensions in points (1 point = 1/72 inch).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Why this matters:**  
`insertShape` creates a drawing object that lives in the document’s *drawing* part. By specifying the size, you control how much space the shape would occupy if it were visible. The optional styling helps you verify the shape before you hide it.

### Step 3: Hide the shape so it does not appear in the layout

Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to `true` tells Word to omit the shape from rendering, while keeping the object in the document structure.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Why this matters:**  
A hidden shape can still be accessed programmatically (e.g., for conditional processing) and can be unhidden later by toggling the property. This is ideal for scenarios such as **conditional placeholders** that should only appear for certain audiences.

### Step 4: Save and verify the result

Finally, write the document to disk. Open the file in Microsoft Word to confirm that the rectangle is not visible. You can also inspect the underlying XML to see the hidden flag.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Expected output:**  
Running the program prints:

```
Document saved to HideShapeResult.docx
```

When you open *HideShapeResult.docx* in Word, the page appears empty (or contains any other content you added before the shape). The rectangle is present in the file’s XML (`<w:hidden>` attribute) but does not render.

### Step 5: (Optional) Unhide the shape later

If you need to make the shape visible again, load the document, locate the shape, and set `hidden` to `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Why this matters:**  
Being able to toggle the hidden flag gives you full control over dynamic document generation—e.g., you can generate a master document with all optional elements hidden, then selectively unhide them based on user preferences.

## Full, runnable example (create word document aspose, insert rectangle shape word, hide shape)

Below is the complete program that you can compile and run directly.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Running the code**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Replace `aspose-words-24.10.jar` with the actual version you downloaded.

### What the output files contain

* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.  
* **UnhiddenShape.docx** – the same rectangle is visible, showing a red box with a black outline.

## Common questions & edge‑case handling

| Question | Answer |
|----------|--------|
| *Will the hidden shape affect pagination?* | No. Hidden objects are ignored by the layout engine, so they do not push text onto a new page. |
| *Can I hide other Word objects (e.g., images, tables)?* | Yes. Most `Node` subclasses (including `Shape`, `Paragraph`, `Run`) expose a `setHidden(boolean)` method. |
| *What if the document already contains shapes?* | Use `doc.getChildNodes(NodeType.SHAPE, true)` to iterate and hide only the shapes you target. |
| *Does hiding a shape increase file size?* | Slightly, because the shape XML remains. The impact is negligible for typical documents. |
| *Will the hidden flag survive when the document is saved as PDF?* | When converting to PDF, hidden shapes are omitted by default. You can control this with `PdfSaveOptions` if needed. |

## Best practices when working with hidden objects

* **Name your shapes** using `setName("MyPlaceholder")`. This makes it easier to locate them later.  
* **Group related hidden objects** inside a `GroupShape` if you need to toggle visibility for several elements at once.  
* **Document the purpose** of hidden elements in comments or a separate specification file—future maintainers will appreciate the context.  
* **Avoid over‑using hidden objects**; they increase document complexity and can confuse end‑users who inspect the XML manually.

## Conclusion

You now know how to **hide shape in Word** using Aspose.Words, how to **create Word document aspose**, and how to **insert rectangle shape word** before hiding it. The example demonstrates the full lifecycle: creation, insertion, hiding, saving, and optionally unhiding. Apply these techniques to build dynamic reports, conditional templates, or any automated Word workflow where invisible placeholders are needed.

### Next steps

* Explore **conditional content** by combining hidden shapes with mail‑merge fields.  
* Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular control.  
* Check the Aspose.Words documentation on **document protection** to prevent users from accidentally unhiding shapes.

Happy coding, and let your generated Word files stay clean while still carrying the hidden data you need!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}