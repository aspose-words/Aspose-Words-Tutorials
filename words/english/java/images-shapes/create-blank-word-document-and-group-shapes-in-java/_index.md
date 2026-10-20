---
category: general
date: 2026-08-23
description: Create blank Word document with Aspose.Words for Java, learn how to group
  shapes, color rectangle shape, and save document as docx in minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: en
lastmod: 2026-08-23
og_description: Create blank Word document with Aspose.Words for Java, then see how
  to group shapes, color rectangle shape, and save document as docx efficiently.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Create blank Word document and group shapes in Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Create blank Word document and group shapes in Java
url: /java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank Word document and group shapes in Java

If you need to **create blank Word document** programmatically, Aspose.Words for Java makes it straightforward. This tutorial shows you exactly how to **create blank Word document**, insert a **group shapes in Word**, apply **color rectangle shape**, and finally **save document as docx**. By the end you’ll have a reusable code snippet you can drop into any Java project.

You’ll learn:

* The required Maven/Gradle dependency for Aspose.Words.
* How to instantiate a blank document and a `DocumentBuilder`.
* The exact steps to **how to group shapes** inside a `GroupShape`.
* How to set fill colors on rectangle shapes.
* The best practice for **save document as docx** and where to find the output file.

No prior experience with Aspose.Words is assumed, but you should be comfortable with basic Java development and have a JDK 8 or newer installed.

---

## Prerequisites

| Requirement | Version / Detail |
|-------------|-------------------|
| Java Development Kit | 8 or higher |
| Build tool | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (optional) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## Step 1: Add Aspose.Words to your project

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro tip:** If you’re using a corporate proxy, configure Maven/Gradle to pull the package from the Aspose repository as described in the official docs.

---

## Step 2: **Create blank Word document** with a builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

The `Document` constructor creates an empty `.docx` container in memory. The `DocumentBuilder` gives you a fluent API to add content, including shapes.

---

## Step 3: Insert a **group shapes in Word** container

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

A `GroupShape` works like a mini‑canvas. All shapes added to it move together, which is exactly **how to group shapes** for layout consistency.

---

## Step 4: Add the first **color rectangle shape** (red)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

The `ShapeType.RECTANGLE` constant creates a simple rectangle. By calling `getFill().setForeColor(...)` you control the **color rectangle shape**. You can replace `java.awt.Color.RED` with any `java.awt.Color` constant or custom RGB value.

---

## Step 5: Add the second **color rectangle shape** (green) and position it

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Setting `setLeft` (or `setTop`) moves the shape relative to the top‑left corner of the **group shapes in Word** container. This demonstrates **how to group shapes** with precise positioning.

---

## Step 6: **Save document as docx** and verify the result

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

The `save` method automatically writes a `.docx` file because the file extension is `.docx`. If you need a different format (e.g., PDF), pass the appropriate `SaveFormat` enum.

> **Tip:** Ensure the target directory (`output/` in this example) exists or create it programmatically with `new File("output").mkdirs();`.

---

## Full source code for quick copy‑paste

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Expected output:** Opening `GroupShapeDemo.docx` in Microsoft Word shows a single page containing two colored rectangles (red on the left, green on the right) that move together when you select the group.

---

## Common questions and edge‑case handling

| Question | Answer |
|----------|--------|
| *Can I add more than two shapes to the same group?* | Yes. Call `groupShape.appendChild(yourShape)` for each additional shape. The group will automatically resize to fit the furthest extents, or you can manually adjust its width/height. |
| *What if I need a different shape type (e.g., ellipse)?* | Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. The same fill‑color logic applies. |
| *Do I need to dispose of the `Document` object?* | Aspose.Words manages native resources internally. When the JVM exits, resources are released. For long‑running applications, call `doc.dispose();` if you use the **Aspose.Words for Java (Native)** version. |
| *How do I change the Z‑order so one rectangle appears on top?* | Use `groupShape.insertAfter(shape, referenceShape);` or `groupShape.insertBefore(shape, referenceShape);` to reorder children within the group. |
| *Can I group shapes across different sections?* | No. A `GroupShape` must reside within a single paragraph or shape container. To group across sections, create separate groups in each section. |

---

## Conclusion

You now know how to **create blank Word document** with Aspose.Words for Java, **group shapes in Word**, apply **color rectangle shape** styling, and **save document as docx**. This pattern scales to more complex layouts—just add additional shapes, adjust offsets, and optionally set text, images, or hyperlinks inside the group.

**Next steps** you might explore:

* Use **group shapes in Word** to build flowcharts or UI mock‑ups.
* Experiment with **save document as docx** combined with PDF conversion (`doc.save("out.pdf")`).
* Apply gradients or patterns to the **color rectangle shape** for richer visual design.
* Combine grouped shapes with tables or charts for advanced reporting documents.

Feel free to modify the dimensions, colors, or shape types to match your project’s branding. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}