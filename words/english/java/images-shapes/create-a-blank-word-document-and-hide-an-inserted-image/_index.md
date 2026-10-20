---
category: general
date: 2026-10-20
description: Create a blank Word document, insert an image, hide the shape, and save
  the file as DOCX. Learn how to hide image in Word with a clear step‑by‑step guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- how to hide image
- save document as docx
- hide shape in word
language: en
lastmod: 2026-10-20
og_description: Create a blank Word document, then hide an inserted image and save
  as DOCX with this complete tutorial.
og_image_alt: Screenshot of a blank Word document with a hidden image shape
og_title: Create a blank Word document and hide an image – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank Word document, insert an image, hide the shape, and
    save the file as DOCX. Learn how to hide image in Word with a clear step‑by‑step
    guide.
  headline: Create a blank Word document and hide an inserted image
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- Java
- Document processing
title: Create a blank Word document and hide an inserted image
url: /java/images-shapes/create-a-blank-word-document-and-hide-an-inserted-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create a blank Word document and hide an inserted image

If you need to **create blank word document** that later holds an image you don’t want to appear in the layout, this tutorial shows you exactly how. You’ll learn to insert an image into Word, hide the shape, and finally **save document as docx** so the hidden image stays invisible to readers.

The guide walks through every line of code, explains why each call matters, and covers common pitfalls such as missing image files or multiple hidden shapes. By the end you’ll have a reusable method that works with Aspose.Words for Java (version 23.10 or later).

## Prerequisites

Before you start, make sure you have:

* Java 17 or newer installed.
* Aspose.Words for Java library (Maven artifact `com.aspose:aspose-words:23.10`).
* An image file (e.g., `logo.png`) placed in a known directory.
* A basic understanding of Java project structure.

## Step 1: Create a blank Word document

The first operation is to instantiate an empty `Document` object. This object represents the whole DOCX file and starts with no sections or content.

```java
import com.aspose.words.*;

public class WordImageHider {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();          // <-- primary action
        // Continue with the remaining steps
        insertAndHideImage(doc, "YOUR_DIRECTORY/logo.png");
        doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX);
    }
}
```

**Why this matters:**  
A blank document gives you a clean canvas. Aspose.Words automatically adds a default section and a single empty body, so you can start adding shapes without worrying about page setup.

## Step 2: Insert image into Word

To place an image, you need a `DocumentBuilder`. The builder works against the current node (the document’s body) and provides the `insertImage` method, which returns a `Shape` object representing the picture.

```java
private static void insertAndHideImage(Document doc, String imagePath) throws Exception {
    // Initialize a DocumentBuilder to work with the document
    DocumentBuilder builder = new DocumentBuilder(doc);

    // Insert the image and capture the Shape object
    Shape imageShape = builder.insertImage(imagePath);   // <-- secondary keyword
    // Proceed to hide the shape
    hideShape(imageShape);
}
```

**Why this matters:**  
`insertImage` embeds the picture as a **shape**. The returned `Shape` lets you adjust properties such as size, layout, and visibility. If the file path is incorrect, Aspose throws an `IllegalArgumentException`, so you may want to wrap the call in a try‑catch block for production code.

## Step 3: Hide shape in Word

A shape can be hidden by setting its `Hidden` property to `true`. When the document is opened in Microsoft Word, the shape does not participate in layout or printing, yet it remains in the file.

```java
private static void hideShape(Shape shape) {
    // Hide the shape so it does not appear in the layout
    shape.setHidden(true);               // <-- how to hide image
}
```

**Why this matters:**  
Hiding the shape is useful for watermarks, background graphics, or metadata images that should not distract readers. The hidden flag is stored in the underlying XML (`<w:hidden/>`), making the image invisible without deleting it.

### Edge case: multiple hidden images

If you need several invisible pictures, repeat the insert‑and‑hide sequence for each image. The `setHidden(true)` call works independently on every `Shape` instance.

```java
// Example for inserting two hidden logos
builder.insertImage("logo1.png").setHidden(true);
builder.insertImage("logo2.png").setHidden(true);
```

## Step 4: Save document as DOCX

Finally, persist the in‑memory `Document` to a physical file. The `SaveFormat.DOCX` constant ensures the file is saved in the modern Office Open XML format.

```java
// Save the document with the hidden shape
doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX); // <-- save document as docx
```

**Why this matters:**  
Saving as DOCX preserves all shape properties, including the hidden flag. If you save as an older format (e.g., `.doc`), some shape attributes may be lost.

## Complete runnable example

Putting everything together, here’s a self‑contained program you can compile and run:

```java
import com.aspose.words.*;

public class WordImageHider {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();

        // 2️⃣ Insert an image and obtain the Shape object
        DocumentBuilder builder = new DocumentBuilder(doc);
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // 3️⃣ Hide the shape so it does not appear in the layout
        imageShape.setHidden(true);

        // 4️⃣ Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx", SaveFormat.DOCX);

        System.out.println("Document created and saved successfully.");
    }
}
```

**Expected result:**  
Opening `HiddenShape.docx` in Microsoft Word shows a completely blank page. The image file is present in the document package (you can verify by opening the DOCX as a zip), but it does not render because the shape is hidden.

## Common questions and troubleshooting

| Question | Answer |
|----------|--------|
| *What if the image file is missing?* | Aspose.Words throws `FileNotFoundException`. Wrap `insertImage` in a try‑catch block and log a helpful message. |
| *Can I later un‑hide the image?* | Yes. Retrieve the shape (`doc.getChildNodes(NodeType.SHAPE, true)`) and call `setHidden(false)`. |
| *Does hiding affect PDF conversion?* | When converting to PDF, hidden shapes are omitted by default. Use `PdfSaveOptions.setExportHiddenObjects(true)` if you need them. |
| *Is the hidden flag supported in older Word versions?* | Word 2007+ (DOCX) fully supports it. The legacy `.doc` format may drop the flag. |

## Pro tips

* **Reuse the builder:** If you plan to add more content after the image, keep the same `DocumentBuilder` instance; it maintains the cursor position.
* **Set shape size before hiding:** Adjust `imageShape.setWidth(100); imageShape.setHeight(50);` to control the hidden image’s dimensions, which can affect file size.
* **Batch processing:** For large batches, create the document once, insert all hidden images, then save—this reduces I/O overhead.

## Conclusion

You now know how to **create blank word document**, **insert image into word**, **hide shape in word**, and **save document as docx** using Aspose.Words for Java. The hidden image stays invisible to end users while remaining part of the file, enabling scenarios like invisible watermarks or metadata storage.

**Next steps:**  
* Explore other shape properties such as rotation, flip, and text wrap.  
* Learn how to add a visible watermark with `Shape.setWrapType(WrapType.NONE)`.  
* Integrate this routine into a web service that generates customized reports on the fly.

Feel free to experiment with multiple hidden shapes, different image formats (PNG, JPEG, SVG), and combine this technique with document merging for powerful automated document pipelines. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)
- [Insert Floating Image In Word Document](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}