---
category: general
date: 2026-10-20
description: How to group shapes in Aspose.Words for Java – learn how to insert rectangle
  shape, group them, and save the document in a single guide.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: en
lastmod: 2026-10-20
og_description: How to group shapes in Aspose.Words for Java. This tutorial shows
  how to insert rectangle shape, group them, and export the result.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: How to group shapes in Aspose.Words for Java – step‑by‑step guide
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: How to group shapes in Aspose.Words for Java
url: /java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# How to group shapes in Aspose.Words for Java

If you need to **how to group shapes** in a Word document using Aspose.Words for Java, this guide shows you the complete workflow. You’ll learn how to **insert rectangle shape**, add a second rectangle, group the two shapes, and finally save the file—all with clear, runnable code.

Grouping shapes is useful when you want to move, rotate, or style several drawings as a single unit. Whether you’re building a report template, a diagram, or a custom flyer, mastering shape grouping saves you time and keeps your layout consistent.

In this tutorial you will:

* Create a new `Document` and a `DocumentBuilder`.
* **How to insert rectangle** shapes with precise dimensions.
* Group the rectangles into a `GroupShape`.
* Save the document and verify the result.

> **Prerequisite** – You must have Aspose.Words for Java (v23.12 or later) added to your project. Maven users can include the dependency shown below.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## What you’ll need

| Item | Reason |
|------|--------|
| Java 17+ | Modern language features and better performance |
| Aspose.Words for Java | Provides the `DocumentBuilder`, `Shape`, and `GroupShape` APIs |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | To compile and run the example |
| Write permission to a folder | The document will be saved to disk |

---

## How to insert rectangle shape

The first step is to create a `Document` and a `DocumentBuilder`. The builder gives you methods such as `insertShape` to place drawing objects.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – Using `insertShape` is the standard way **how to insert rectangle** objects in Aspose.Words. It automatically adds the shape to the document’s current paragraph, so you don’t have to manage low‑level OpenXML.

---

## Adjusting rectangle positions (optional)

If the second rectangle needs a custom location relative to the first one, you can modify its `left` and `top` properties. This step is optional but often required for precise diagram layout.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** All measurements are in points (1 pt ≈ 1/72 in). Use `convertPointsToPixels` if you need pixel values for UI‑based calculations.

---

## How to group shapes

Now that the rectangles exist, you can place them inside a `GroupShape`. Grouping makes the two rectangles behave like a single object—moving, rotating, or formatting the group will affect both shapes.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape` inherits from `Shape`, so you can treat the group exactly like any other drawing object. When you call `appendChild`, the shapes are removed from their original location and become children of the group.

---

## Saving the document containing the grouped shapes

Finally, write the document to disk. The file will contain a single `GroupShape` with two rectangles inside.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Expected result

Open `GroupShape.docx` in Microsoft Word:

* You will see two rectangles (blue and green) positioned side‑by‑side.
* Selecting either rectangle selects the whole group—dragging moves both together.
* The group has a thin red border, confirming that the `GroupShape` properties are applied.

If you right‑click the group and choose **Group → Ungroup**, the rectangles return to independent shapes, demonstrating that the grouping operation is reversible.

---

## Common variations and edge cases

| Situation | How to handle it |
|-----------|------------------|
| **More than two shapes** | Insert each shape, then append all to the same `GroupShape`. |
| **Different shape types** (e.g., ellipse, picture) | Use `builder.insertShape(ShapeType.ELLIPSE, …)` or `builder.insertImage(...)` before appending. |
| **Scaling the group** | Call `group.setWidth(newWidth)` or `group.setHeight(newHeight)`; children scale proportionally. |
| **Rotating the group** | `group.setRotationAngle(45);` rotates the whole collection around its center. |
| **Preserving original positions** | Store each shape’s `left`/`top` before grouping and restore after ungrouping if needed. |

---

## Full, runnable example

Below is the complete Java class you can copy‑paste into your IDE. It includes all imports, error handling, and comments for clarity.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Run the program, open the resulting `GroupShape.docx`, and you’ll see the grouped rectangles exactly as described.

---

## Conclusion

You now know **how to group shapes** in Aspose.Words for Java, from creating a document to inserting rectangle shapes, adjusting their positions, and finally grouping them with `GroupShape`. This technique lets you treat multiple drawings as a single entity, simplifying layout adjustments and visual consistency.

**Next steps**

* Explore **how to insert rectangle** shapes with different fill patterns or borders.
* Combine **insert rectangle shape** with text boxes to create labeled diagrams.
* Experiment with rotating or scaling the group to produce more complex graphics.

Feel free to adapt the code for other shape types, larger groups, or dynamic document generation scenarios. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [how to insert group shape in Java – Complete Guide](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [How to Set Shadow on a Shape in Aspose.Words – Complete Guide](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}