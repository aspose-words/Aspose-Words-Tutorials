---
category: general
date: 2026-07-20
description: Create blank word document in Java using Aspose.Words. Learn how to create
  group, insert rectangle shape, and embed image in shape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: en
lastmod: 2026-07-20
og_description: Create blank word document in Java with Aspose.Words. This guide shows
  how to create group, insert rectangle shape, and embed image in shape for dynamic
  Word files.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Create blank word document with grouped shape – Java guide
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Create blank word document with grouped shape – Java guide
url: /java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank word document with grouped shape – Java guide

Ever wondered how to **create blank word document** that already contains a nicely grouped shape? Maybe you’re building a report template, or you need a placeholder for a logo and a caption. Either way, the problem is common: you start with an empty file, then you have to add a group, drop a rectangle inside, and finally embed an image—all programmatically.

In this tutorial we’ll walk through a complete, ready‑to‑run Java example that does exactly that. You’ll learn **how to create group**, **insert rectangle shape**, and **add image word document** inside the same group. By the end you’ll have a Word file that looks like a polished template, ready for further customization.

> **What you’ll get:** a fully functional Java class, step‑by‑step explanations, tips for handling file paths, and a preview of the expected output. No external documentation required—everything you need is right here.

---

## Create blank word document – Step‑by‑Step Overview

The first thing we need is a truly blank Word file. Aspose.Words makes this trivial: just instantiate the `Document` class with its default constructor. This gives you a clean canvas, equivalent to opening Word and clicking **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why start with a blank document?**  
> A blank document guarantees that no hidden styles or sections interfere with the shapes you’ll add later. It also keeps the file size minimal, which is handy when you generate dozens of files in a batch job.

---

## How to create group and add shapes

A **group shape** is essentially a container that can hold multiple child shapes—think of it as a folder for drawing objects. By grouping, you can move, resize, or rotate the whole set with a single command.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

The `insertGroupShape` method returns a `GroupShape` object that we’ll use as the parent for the rectangle and the image. The size is expressed in points (1 point = 1/72 inch), so 200 points gives you roughly a 2.78 × 2.78 inch box.

> **Pro tip:** If you need the group to be transparent, set `group.setFillColor(Color.getWhite());` after creation.

Now that the group exists, we have to tell the builder where to place the next shapes. The builder’s cursor must be positioned inside the group’s first paragraph.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Insert rectangle shape inside the group

A rectangle is often used as a placeholder for text or as a visual cue. Adding it as the **first child** of the group ensures it sits behind any subsequent images.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

The rectangle inherits the group’s coordinate system, so its 100 × 50‑point size will be centered by default. You can style it further—add a border, change the fill color, or apply a shadow—by accessing the returned `Shape` object.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Add image word document – embedding image in shape

Now for the fun part: **embed image in shape**. We’ll insert a JPEG picture as the second child of the same group. Because the cursor is still inside the group, the image will automatically become a child node.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

If the image file isn’t found, Aspose.Words throws an `FileNotFoundException`. To avoid that, either place `sample.jpg` in the project’s working directory or use an absolute path.

> **What if you need a different image format?**  
> Aspose.Words supports PNG, BMP, GIF, TIFF, and even SVG. Just change the file extension and the library will handle the conversion.

---

## Save the document and see the result

Finally, we persist the in‑memory document to disk. The resulting `.docx` will contain a single page with a grouped shape that holds both the rectangle and the image.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

When you open `output.docx` in Microsoft Word, you should see a 200 × 200‑point group in the top‑left corner. Inside the group, a light gray rectangle sits at the top, and directly beneath it the picture you specified appears, perfectly aligned.

![Grouped shape example](grouped-shape.png){:alt="Screenshot of a blank Word document with a grouped shape containing a rectangle and an embedded image"}

---

## Common variations and edge‑case handling

| Scenario | What to change | Why it matters |
|----------|----------------|----------------|
| **Different group size** | Adjust the parameters of `insertGroupShape(width, height)` | Larger groups can accommodate more complex layouts. |
| **Multiple images** | Call `builder.insertImage()` repeatedly after moving to the group’s paragraph each time | Each call adds a new child; you can also position them using `Shape.setLeft()` / `setTop()`. |
| **Dynamic image paths** | Use `String.format("images/%s.jpg", imageName)` | Makes the code reusable for batch processing. |
| **Saving as PDF** | Replace `doc.save("output.pdf")` | Aspose.Words can convert on the fly, letting you generate PDFs directly. |
| **Rotating the group** | `group.setRotation(45);` | Useful for decorative watermarks or stylized headers. |

---

## Expected output and verification

After running the class:

1. `output.docx` appears in the project folder.  
2. Opening the file shows a single page with a grouped shape.  
3. Inside the group, the rectangle is positioned at the top‑left, and the image sits directly below it.  
4. Selecting the group in Word highlights both child objects, confirming they are truly grouped.

If any of these steps fail, double‑check the image path and ensure the Aspose.Words JAR is on your classpath.

---

## Conclusion

You now know **how to create blank word document** and enrich it with a grouped shape that contains a rectangle and an embedded picture. By mastering **how to create group**, **insert rectangle shape**, and **add image word document**, you can build sophisticated Word templates entirely in code—no manual tweaking required.

Ready for the next challenge? Try adding text boxes inside the same group, or experiment with different shape styles to match your corporate branding. You could even generate a whole report library where each document starts with this exact layout.

Happy coding, and feel free to share your own variations in the comments below!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}