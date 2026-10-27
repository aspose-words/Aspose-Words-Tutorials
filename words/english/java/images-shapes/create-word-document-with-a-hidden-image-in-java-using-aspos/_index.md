---
category: general
date: 2026-09-24
description: Create word document in Java and learn how to hide image, add image word,
  and insert hidden picture with Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to hide image
- add image word
- how to hide shape
- insert hidden picture
language: en
lastmod: 2026-09-24
og_description: Create word document in Java and discover how to hide image, add image
  word, and insert hidden picture using Aspose.Words.
og_image_alt: Screenshot of a create word document example with a hidden image
og_title: Create word document with a hidden image – step‑by‑step Java guide
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Create word document in Java and learn how to hide image, add image
    word, and insert hidden picture with Aspose.Words.
  headline: Create word document with a hidden image in Java using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Create word document with a hidden image in Java using Aspose.Words
url: /java/images-shapes/create-word-document-with-a-hidden-image-in-java-using-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create word document with a hidden image in Java using Aspose.Words

If you need to **create word document** programmatically, Aspose.Words for Java makes it straightforward. This tutorial shows **how to hide image**, **add image word**, and **insert hidden picture** in a single document while keeping the layout clean.

Document automation often requires embedding logos, watermarks, or placeholders that should not disrupt the visible content. By marking a shape as hidden, you keep the image in the file for later use (e.g., for conditional content generation) without showing it to the end user. You’ll walk through the complete workflow, from initializing a document to saving the final `.docx` file.

## What you’ll learn

* How to **create word document** from scratch using `Document` and `DocumentBuilder`.
* The exact steps to **add image word** and then hide that image with the `setHidden(true)` method.
* How the **how to hide shape** technique works under the hood and why it’s reliable across Word versions.
* Ways to **insert hidden picture** so that the image remains in the file but stays invisible in the layout.
* Common pitfalls such as incorrect file paths, unsupported image formats, and how to verify that the image is truly hidden.

> **Prerequisites** – You need Java 8+ installed, a Maven or Gradle project, and a valid Aspose.Words for Java license (or a free evaluation license). No other external libraries are required.

## Create word document and insert a hidden image

The first step is to instantiate a new `Document` object. This object represents the entire Word file in memory.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: `Document` is the container for all parts of a Word file (styles, sections, images, etc.). `DocumentBuilder` provides a fluent API to add content without dealing with low‑level Open XML structures.

## How to hide image using shape properties

Images in a Word document are stored as `Shape` objects. Setting the `Hidden` flag tells Word to exclude the shape from the layout while preserving it in the file.

```java
        // Step 3: Insert an image into the document
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // Step 4: Mark the inserted shape as hidden so it won't appear in the layout
        imageShape.setHidden(true);
```

*Explanation*:  
* `insertImage` creates a `Shape` of type `Picture`.  
* `setHidden(true)` toggles the Word “Hidden” attribute, which is respected by the layout engine. The picture remains embedded, so you can later unhide it programmatically or via Word’s UI.

> **Pro tip**: Use PNG for lossless quality, and keep the image size modest (under 200 KB) to avoid bloating the `.docx` file.

## Add image word and verify hidden status

Although the image is hidden, you might still want to reference it in the document text (e.g., “Company logo”). You can add a caption or a placeholder paragraph before hiding the shape.

```java
        // Optional: Add a caption that explains the hidden image
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)"); // This text is visible
```

*Why you might do this*: Some workflows require a textual marker so that downstream processes can locate the hidden picture without parsing the document’s binary parts.

## Insert hidden picture and save the file

Finally, persist the document to disk. The hidden picture stays embedded but invisible when the file is opened in Microsoft Word.

```java
        // Step 5: Save the document with the hidden shape
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

*Verification*: Open `HiddenShapeDemo.docx` in Word. You should see the caption “Company logo (hidden)” but no visible image. To confirm the image exists, open the file as a ZIP archive (`.docx` files are ZIP containers) and inspect `word/media`. The PNG you added will be present.

## Common edge cases and how to handle them

| Situation | What to watch for | Recommended fix |
|-----------|-------------------|-----------------|
| **Invalid image path** | `FileNotFoundException` at `insertImage` | Use `Paths.get(...).toAbsolutePath()` or check `Files.exists()` before insertion. |
| **Unsupported image format** (e.g., BMP) | Aspose throws `UnsupportedImageFormatException` | Convert the image to PNG or JPEG before calling `insertImage`. |
| **Hidden flag ignored** (rare Word versions) | Image still appears in layout | Ensure you’re using Aspose.Words 22.9+ where `setHidden` maps to the correct OOXML attribute (`<w:hidden/>`). |
| **Large image size** | Document becomes sluggish | Resize the image using `imageShape.setWidth(100); imageShape.setHeight(50);` before hiding. |

## Full, runnable example

Below is the complete program you can copy, adjust the paths, and run directly.

```java
import com.aspose.words.*;

public class HiddenShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document document = new Document();

        // 2. Prepare a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Insert the image (replace with your actual file)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");

        // 4. Hide the shape so it doesn't affect layout
        imageShape.setHidden(true);

        // 5. (Optional) Add a visible caption for context
        builder.moveToDocumentEnd();
        builder.writeln("Company logo (hidden)");

        // 6. Save the result
        document.save("YOUR_DIRECTORY/HiddenShapeDemo.docx");
    }
}
```

**Expected output**: When you open `HiddenShapeDemo.docx` in Microsoft Word, the document contains the text “Company logo (hidden)” and no visible picture. The hidden PNG can be confirmed inside the `word/media` folder of the zipped `.docx`.

## How to hide shape vs. how to hide image

In Word terminology, both pictures and drawings are treated as **shapes**. The `setHidden(true)` method works for any shape type, so the same approach applies to vector graphics, text boxes, or charts. If you need to hide a shape that isn’t an image, simply obtain the `Shape` reference (e.g., via `builder.insertShape(ShapeType.LINE, 100, 0)`) and call `setHidden(true)`.

## Next steps and related topics

* **Replace hidden picture at runtime** – Load the document later, locate the hidden shape by its `Name` or `AlternativeText`, and swap the image data.  
* **Conditional content** – Combine hidden shapes with Mail Merge to show or hide images based on data fields.  
* **Working with WordprocessingML** – Inspect the underlying XML (`<w:pict>` and `<w:hidden/>`) if you need low‑level tweaks.  

These extensions let you build sophisticated document generation pipelines while keeping the core **create word document** logic clean and maintainable.

---

*You now know how to create a Word document, add an image, and hide that image using Aspose.Words for Java. Experiment by inserting multiple hidden pictures, toggling their visibility, or integrating the technique into a larger reporting system.*


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Inline Image In Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Insert Floating Image In Word Document](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}