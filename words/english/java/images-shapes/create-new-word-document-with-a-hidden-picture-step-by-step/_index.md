---
category: general
date: 2026-09-27
description: Create new Word document and insert an image shape that stays hidden.
  Learn how to hide shape and add hidden picture using Aspose.Words for Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert image shape
- how to hide shape
- how to insert image
- add hidden picture
language: en
lastmod: 2026-09-27
og_description: Create new Word document and insert an image shape that stays hidden.
  Learn how to hide shape and add hidden picture using Aspose.Words for Java.
og_image_alt: Screenshot showing a Word document with a hidden picture inserted using
  Java
og_title: Create new Word document with a hidden picture – Java guide
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create new Word document and insert an image shape that stays hidden.
    Learn how to hide shape and add hidden picture using Aspose.Words for Java.
  headline: Create new Word document with a hidden picture – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- hidden image
title: Create new Word document with a hidden picture – step‑by‑step guide
url: /java/images-shapes/create-new-word-document-with-a-hidden-picture-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create new Word document with a hidden picture – step‑by‑step guide

If you need to **create new Word document** that contains a logo but you don't want the logo to affect the page layout, this guide shows you exactly how to do it. You will learn how to **insert image shape**, understand **how to hide shape**, and finally **add hidden picture** to the file without any visual impact.

The tutorial covers everything from project setup to the final verification step. By the end you will have a fully functional Java program that creates a Word file, inserts an image shape, hides it, and saves the result. No extra tooling is required beyond the Aspose.Words for Java library.

## Prerequisites

Before you start, make sure you have:

* Java 17 (or newer) installed.
* A Maven or Gradle project where you can add dependencies.
* Aspose.Words for Java 23.9 (or the latest version) – see the official Maven repository for the correct coordinates.
* An image file (e.g., `logo.png`) placed in a folder you can reference from your code.

> **Pro tip:** Keep the image in the same directory as your source file during development; it simplifies the path handling.

## Step 1: Set up the project and import Aspose.Words

Add the Aspose.Words dependency to your `pom.xml` (Maven) or `build.gradle` (Gradle). Below is the Maven snippet:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Now create a Java class called `HiddenPictureDemo`. The first lines import the required classes and **create new Word document**:

```java
import com.aspose.words.*;

public class HiddenPictureDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder
        Document doc = new Document();               // creates new Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* `Document` represents the entire `.docx` file, while `DocumentBuilder` provides a fluent API to add content such as paragraphs, tables, and shapes.

## Step 2: Insert image shape into the Word document

The next operation demonstrates **how to insert image** as a shape. Using `DocumentBuilder.insertImage` returns a `Shape` object that you can further manipulate.

```java
        // Step 2: Insert an image shape (the picture will act as a shape)
        Shape imageShape = builder.insertImage("YOUR_DIRECTORY/logo.png");
        // Optional: set the shape size if needed
        imageShape.setWidth(100);
        imageShape.setHeight(50);
```

*Why you use a shape:* An image inserted as a shape gives you access to layout properties like visibility, wrapping, and positioning, which are essential for hiding the picture later.

## Step 3: Hide the shape so it does not appear in the layout

Now we answer **how to hide shape**. Setting the `Hidden` property to `true` removes the shape from the visual layout while keeping it in the document structure.

```java
        // Step 3: Hide the shape – this is the core of "add hidden picture"
        imageShape.setHidden(true);
        // You can also set the shape's wrap type to NONE to avoid affecting surrounding text
        imageShape.setWrapType(WrapType.NONE);
```

*Explanation:* `setHidden(true)` tells Word to treat the shape as invisible. The additional `setWrapType(WrapType.NONE)` ensures that the hidden picture does not reserve any space, preserving the original document flow.

## Step 4: Save the document and verify the hidden picture

Finally, persist the file to disk. The hidden picture remains part of the document but is not displayed when the file is opened in Microsoft Word.

```java
        // Step 4: Save the document with the hidden shape
        doc.save("YOUR_DIRECTORY/HiddenShape.docx");
        System.out.println("Document created successfully with a hidden picture.");
    }
}
```

When you open `HiddenShape.docx` in Word, you will see a normal, clean page with no visible logo, yet the image is stored inside the file. You can verify its presence by opening the `.docx` as a zip archive and inspecting the `word/media` folder.

### Expected output

Running the program prints:

```
Document created successfully with a hidden picture.
```

Opening the generated `HiddenShape.docx` shows an empty page (or whatever content you added elsewhere) and no visible image. If you unzip the `.docx`, you’ll find `logo.png` inside `word/media`, confirming that the picture was **add hidden picture** correctly.

## How to insert image in other contexts

If you need to **insert image shape** into a specific paragraph rather than the current cursor position, you can move the builder first:

```java
builder.moveToParagraph(0, 0); // moves to the first paragraph
Shape anotherShape = builder.insertImage("YOUR_DIRECTORY/banner.jpg");
anotherShape.setHidden(true);
```

This pattern works for headers, footers, or tables—just move the builder to the target node before calling `insertImage`.

## Common variations and edge cases

| Scenario | What to adjust |
|----------|----------------|
| **Multiple hidden pictures** | Repeat steps 2‑3 for each image. Each `Shape` can be hidden independently. |
| **Different image formats** | Aspose.Words supports PNG, JPEG, BMP, GIF, and TIFF. Use the appropriate file extension in the path. |
| **Large documents** | Create the document once, then reuse the same `DocumentBuilder` to insert hidden pictures at various locations. |
| **Conditional visibility** | Use `shape.setVisible(false)` together with `shape.setHidden(true)` if you need to toggle visibility via Word macros later. |
| **Compatibility with older Word versions** | Save as `doc.save("file.doc", SaveFormat.DOC)` if you must support Word 2003‑2007. Hidden shapes behave the same way. |

## Practical tips from experience

* **Path handling:** Use `Paths.get("...").toAbsolutePath().toString()` to avoid relative‑path surprises when running from an IDE versus a packaged JAR.
* **Performance:** Inserting many large images can increase memory usage. Consider scaling the image (`setWidth`/`setHeight`) before hiding it.
* **Testing:** Automate a quick check by loading the saved document and calling `doc.getChildNodes(NodeType.SHAPE, true).getCount()` to ensure the expected number of shapes exist, even if they are hidden.

## Conclusion

You now know how to **create new Word document**, **insert image shape**, and **how to hide shape** so that the picture remains invisible—effectively **add hidden picture** to any Word file using Aspose.Words for Java. This technique is useful for embedding watermarks, branding assets, or metadata images that should not disrupt the document layout.

### Next steps

* Explore other shape properties such as rotation, borders, and hyperlinks.
* Combine hidden pictures with custom document properties to store additional metadata.
* Look into **how to insert image** into headers or footers for consistent branding across pages.

Feel free to experiment with different image sizes, positions, and visibility settings. If you run into any issues, the Aspose.Words for Java documentation provides detailed API references and sample projects. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Add shadow to shape in Word – Complete Aspose.Words Guide](/words/english/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}