---
category: general
date: 2026-09-11
description: Group shapes in Word and add a rectangle shape using Aspose.Words for
  Java. Learn how to set shape size, group objects, and save the document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: en
lastmod: 2026-09-11
og_description: Group shapes in Word and add a rectangle shape using Aspose.Words
  for Java. This tutorial shows how to set shape size, group shapes, and export the
  document.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Group shapes in Word – add rectangle with Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Group shapes in Word and add a rectangle with Aspose.Words
url: /java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Group shapes in Word and add a rectangle with Aspose.Words

If you need to **group shapes in Word** while programmatically adding a rectangle, this guide gives you a complete, ready‑to‑run solution. You’ll see exactly how to insert a group shape, add a rectangle shape, set shape size, and finally save the document so you can view the result instantly.

Working with Word documents often means arranging multiple objects—pictures, charts, or simple geometric shapes—into a single logical unit. Grouping those objects makes it easier to move, rotate, or style them together. In this tutorial we’ll also cover **how to add rectangle** shapes and **set shape size** for perfect layout control.

## What you’ll learn

* How to create a new Word document with Aspose.Words for Java.  
* **How to group shapes** so they behave as a single object.  
* **Add rectangle shape** to a group and insert an image into the same group.  
* **Set shape size** for both the rectangle and the image.  
* Save the document and open it in Microsoft Word to verify the result.

### Prerequisites

* Java 17 or later installed.  
* Maven or Gradle to manage dependencies.  
* A valid Aspose.Words for Java license (or a free evaluation key).  
* An image file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with your actual path).

---

## How to group shapes in Word using Aspose.Words

The first step is to create a `Document` and a `DocumentBuilder`. The builder gives you a convenient API to insert shapes, text, and other elements.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `DocumentBuilder` works directly with the underlying `Document` object, allowing you to insert shapes without manually handling low‑level node collections.

### Add a group shape

A group shape is a container that can hold other shapes. Think of it as a folder for drawing objects.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

The `insertGroupShape()` method creates a `GroupShape` node and returns it so you can append child shapes later.  

---

## Add a rectangle shape to the group

Now we’ll **add rectangle shape** to the previously created group. The rectangle will serve as a background or a border for the picture.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tip:** Setting `FillColor` and `StrokeColor` makes the rectangle visible in the final document. If you omit these properties, the shape might appear transparent.

### How to add rectangle

The code above demonstrates **how to add rectangle** by creating a `Shape` instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`. This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).

---

## Set shape size for rectangle and image

Proper sizing ensures that the rectangle and the picture align correctly. Here we also **set shape size** for the image we’ll insert next.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Both the rectangle and the picture now share the same dimensions (100 × 50 points). Because they belong to the same group, moving or rotating the group will affect both shapes together.

> **Why match sizes?** Aligning the dimensions guarantees that the image sits neatly inside the rectangle, creating a clean “framed picture” effect.

---

## Save the document and view the result

Finally, we write the document to disk. Opening the file in Microsoft Word shows the grouped shapes as a single selectable object.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

When you open `output.docx`, you’ll see a rectangle with the image inside it. Clicking the shape selects both the rectangle and the picture because they are **grouped**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Image alt text:* *group shapes in word example* – a Word document showing a grouped rectangle and picture.

---

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| **What if I need a different size for the image?** | Adjust `picture.setWidth()` and `picture.setHeight()` after insertion. The rectangle can keep its original size, or you can also resize it to match. |
| **Can I add more shapes to the same group?** | Yes. Call `group.appendChild(newShape)` for any additional `Shape` objects. |
| **How do I rotate the whole group?** | Use `group.setRotationAngle(double angleInRadians)`. The rotation applies to every child shape. |
| **What if the image file is missing?** | `insertImage` throws `FileNotFoundException`. Wrap the call in a try‑catch block and provide a fallback placeholder shape. |
| **Is it possible to ungroup later?** | Call `group.removeAllChildren()` to detach children, then insert them back into the document individually. |

---

## Conclusion

You now have a complete, runnable example that shows **how to group shapes in Word**, **add rectangle shape**, **set shape size**, and **save** the document using Aspose.Words for Java. By grouping the rectangle and the picture, you can move, resize, or rotate them as a single unit—exactly what many document‑automation scenarios require.

From here you might explore:

* Adding text boxes to the same group (`how to add rectangle`‑style text).  
* Applying different fill patterns or gradients (`set shape size` combined with styling).  
* Using the same technique to group charts, tables, or SmartArt (`how to group shapes` across other object types).  

Feel free to experiment with other shape types, colors, and layout options. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}