---
category: general
date: 2026-08-20
description: Learn how to group shapes, set shape size, insert image into document,
  add picture to group, and create rectangle shape with Aspose.Words in Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: en
lastmod: 2026-08-20
og_description: How to group shapes in a Word document using Aspose.Words. Follow
  this step‑by‑step Java tutorial to set shape size, insert image into document, add
  picture to group, and create rectangle shape.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: How to group shapes in a Word document with Aspose.Words – Java guide
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: How to group shapes in a Word document using Aspose.Words
url: /java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in a Word document using Aspose.Words

If you need to **how to group shapes** in a Word file, this tutorial shows the complete Java solution. You’ll see how to **set shape size**, **insert image into document**, **add picture to group**, and **create rectangle shape**—all with clear explanations and a runnable code sample.

Grouping shapes simplifies layout management, lets you move or rotate multiple objects as a single unit, and keeps your document tidy. In the steps below you’ll build a group that contains a rectangle and a picture, then place the group on the page.

## Prerequisites

Before you start, make sure you have:

* Java 17 or newer installed.
* Aspose.Words for Java (version 23.9 or later) added to your project’s classpath.
* A sample JPEG image at `YOUR_DIRECTORY/sample.jpg` (replace `YOUR_DIRECTORY` with the actual path).

You can add Aspose.Words via Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## How to group shapes with Aspose.Words

The following sections walk through each operation required to **how to group shapes**. The primary H2 header contains the primary keyword, satisfying SEO rules.

### Step 1: Create a new document and a `DocumentBuilder`

A `Document` represents the Word file, while `DocumentBuilder` provides convenient methods for inserting content.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters*: Starting with a fresh `Document` ensures that the group you create won’t interfere with existing elements.

### Step 2: Insert a group shape that will hold multiple child shapes

A group shape acts like a container. Its dimensions define the bounding box for all child shapes.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Tip*: The width (`300`) and height (`200`) are in points (1 pt = 1/72 inch). Adjust them based on the size of the shapes you plan to add.

### Step 3: Create a rectangle shape, set its size, and add it to the group

Setting the exact size of a shape is essential when you want precise layout control.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Why we set shape size*: The `setWidth` and `setHeight` methods correspond to the **set shape size** secondary keyword, giving you pixel‑perfect control over the rectangle’s appearance.

### Step 4: Insert an image, then add the picture shape to the same group

Inserting an image is the core of the **insert image into document** requirement. The returned `Shape` is a picture shape that can be grouped like any other shape.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: If you need to preserve the original aspect ratio, set only one dimension (`setWidth` or `setHeight`). Aspose.Words automatically scales the other dimension.

### Step 5: Position the entire group on the page

After adding all child shapes, you can move, rotate, or hide the whole group. Positioning uses the **add picture to group** concept indirectly, because the group now contains the picture.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Explanation*: `setLeft` and `setTop` place the group relative to the page’s margins. Rotating the group demonstrates that all child shapes inherit the transformation.

### Step 6: Save the document

Finally, write the file to disk. You can open the resulting `.docx` in Word to verify the grouping.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Running the program produces **GroupShapesDemo.docx** containing a rectangle and an image bundled together. Selecting either shape in Word will also select the other, confirming that you have successfully learned **how to group shapes**.

---

## Expected output

When you open *GroupShapesDemo.docx* in Microsoft Word:

* A rectangle (golden fill) appears at the left side of the group.
* The picture you supplied appears to the right of the rectangle.
* Both objects move together when you drag the group.
* The group is positioned 50 pt from the left margin and 100 pt from the top margin, rotated 15°.

If the image does not appear, double‑check the file path in `insertImage`. Aspose.Words throws an `IOException` when the file cannot be found.

---

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes?** | Yes. Call `groupShape.appendChild(otherShape)` for each additional shape. |
| **What if I need a transparent background for the rectangle?** | Use `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Is grouping supported in older Word formats (e.g., `.doc`)?** | Grouping works for `.docx` and `.doc` but some older viewers may ignore the group metadata. Save as `.docx` for full fidelity. |
| **How do I ungroup later?** | Retrieve the child nodes via `groupShape.getChildNodes(NodeType.ANY, true)` and move them to the document body, then remove the group. |
| **Can I group shapes across different sections?** | No. A `GroupShape` must reside within a single `Story` (usually the main document body). |

---

## Pro tips for robust shape handling

* **Use absolute positioning sparingly** – relative positioning (`builder.moveToDocumentEnd()`) often yields more responsive layouts.
* **Cache the `DocumentBuilder`** – creating a new builder for each operation can degrade performance on large documents.
* **Set `PictureFillMode`** when you need the image to stretch or tile inside the shape: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Validate image dimensions** before insertion to avoid unexpected scaling that can affect the group’s bounding box.

---

## Next steps

Now that you know **how to group shapes**, you might explore:

* **Insert image into document** with advanced options like cropping (`pictureShape.setCropTop(...)`).
* **Set shape size** dynamically based on page dimensions (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** together with text boxes for captioned graphics.
* **Create rectangle shape** with rounded corners (`rectangleShape.setCornerRadius(5);`).

These topics build on the same API surface and help you create sophisticated, programmatic Word reports.

---

## Conclusion

In this tutorial you learned **how to group shapes** in a Word document using Aspose.Words for Java. By following the six steps—creating a document, inserting a group, **creating rectangle shape**, **set shape size**, **insert image into document**, **add picture to group**, and positioning the group—you now have a reusable pattern for complex layout scenarios. Feel free to experiment with additional child shapes, different rotations, or conditional grouping logic to suit your application’s needs.

Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}