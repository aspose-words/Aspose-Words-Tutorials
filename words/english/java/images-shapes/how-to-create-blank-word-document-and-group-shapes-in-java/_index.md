---
category: general
date: 2026-09-27
description: Create a blank Word document in Java and group shapes using Aspose.Words.
  Learn to set shape size, set shape fill color, and append child to group.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: en
lastmod: 2026-09-27
og_description: Create blank word document in Java with Aspose.Words. This tutorial
  shows how to group shapes in Word, set shape size, set shape fill color, and append
  child to group.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Create a blank Word document and group shapes in Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: How to create blank word document and group shapes in Java
url: /java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to create blank word document and group shapes in Java

If you need to **create blank word document** programmatically, this guide shows you exactly how to do it with Aspose.Words for Java. You’ll also learn to **group shapes in word**, set each shape’s size, apply a fill color, and **append child to group** so the objects behave as a single unit.

Working with Word files from code saves you from manual formatting and enables you to generate reports, contracts, or marketing brochures automatically. By the end of this tutorial you will have a runnable Java program that produces a `.docx` file containing a blue rectangle and an image, both grouped together.

## Prerequisites

Before you start, make sure you have:

- Java 17 (or any recent JDK) installed.
- Maven or Gradle to manage dependencies.
- An Aspose.Words for Java license (the free evaluation works for testing).
- A sample image file (e.g., `sample.jpg`) placed in a folder you can reference from the code.

> **Pro tip:** Keep your image files in a `resources` directory and load them with `ClassLoader.getResourceAsStream` to avoid hard‑coded absolute paths.

## Step 1: Create a blank word document and add a GroupShape

The first step is to instantiate a new `Document` object, which represents an empty Word file, and then insert a `GroupShape`. The group will serve as a container for any shapes you add later.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Why this matters:* A `GroupShape` lets you move, rotate, or format multiple shapes together, which is essential for complex layouts like diagrams or watermarks.

## Step 2: Insert a rectangle and **set shape size**

Next, create a rectangle, define its dimensions, and add it to the group. This demonstrates the **set shape size** operation.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Explanation:* `setWidth` and `setHeight` control the exact size of the shape in points (1 point = 1/72 inch). Adjust these values to fit your layout requirements.

## Step 3: **Set shape fill color** for the rectangle

The rectangle’s background is set to blue using `setFillColor`. You can use any `java.awt.Color` constant or create a custom RGB color.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Why it’s useful:* Fill colors help differentiate objects visually, especially when you later export the document to PDF or print it.

## Step 4: Insert an image and **append child to group**

Now add an image to the same `GroupShape`. The image is inserted via `DocumentBuilder.insertImage`, then appended to the group so it moves together with the rectangle.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Edge case:* If the image path is wrong, Aspose.Words throws `FileNotFoundException`. Use a relative path or load the image from resources to avoid this issue.

## Step 5: **Save the document with the grouped shapes**

Finally, write the document to disk. The resulting file will contain the rectangle and the image grouped together.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Expected output

- A file named `GroupShape.docx` appears in the specified directory.
- Opening the file in Microsoft Word shows a blank page with a blue rectangle and the chosen image, both selected as a single object (you can move or resize them together).

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*The screenshot above demonstrates the final grouped shapes inside the newly created Word document.*

## Common variations and additional tips

| Situation | How to handle it |
|-----------|-----------------|
| **Multiple images** | Insert each image with `builder.insertImage` and call `group.appendChild(picture)` for each one. |
| **Different shape types** | Use `ShapeType.OVAL`, `ShapeType.LINE`, etc., when constructing the `Shape` object. |
| **Changing group position** | After adding all children, set `group.setLeft(x)` and `group.setTop(y)` to move the whole group. |
| **Export to PDF** | Call `doc.save("output.pdf")` after grouping; the PDF will preserve the grouping. |
| **License enforcement** | If you run the evaluation version, a watermark will appear. Install a valid license to remove it. |

## Conclusion

You now know how to **create blank word document**, insert a **GroupShape**, **set shape size**, **set shape fill color**, and **append child to group** using Aspose.Words for Java. This pattern lets you build complex, programmatic layouts that can be edited later in Word or exported to other formats.

Next, explore how to **group shapes in word** with text boxes, add hyperlinks to shapes, or automate the generation of multi‑page reports. The same principles apply—just create additional shapes, configure their properties, and append them to the same group.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}