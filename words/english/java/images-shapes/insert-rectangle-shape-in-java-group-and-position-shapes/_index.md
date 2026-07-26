---
category: general
date: 2026-07-26
description: Insert rectangle shape in Java using Aspose.Words. Learn how to set shape
  size, position shape, and how to group shapes in a DOCX file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: Java
lastmod: 2026-07-26
og_description: Insert rectangle shape in Java to create rich DOCX graphics. Follow
  this step‑by‑step guide to set shape size, position shape, and group shapes effortlessly.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Insert Rectangle Shape in Java – Master Grouping & Positioning
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Insert Rectangle Shape in Java – Group and Position Shapes
url: /java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert Rectangle Shape in Java – Group and Position Shapes

Ever needed to **insert rectangle shape** into a Word document while writing Java code? You’re not the only one—developers building reports, invoices, or custom templates hit this wall all the time. The good news is that with a few lines of Aspose.Words for Java you can **insert rectangle shape**, **set shape size**, **position shape**, and even **how to group shapes** so they move as a single unit.

In this guide we’ll walk through the entire process from creating a blank document to saving a `.docx` that contains two rectangles neatly grouped together. By the end you’ll know **how to add rectangle** objects, control their dimensions, place them exactly where you want, and bundle them into a reusable group. No external libraries beyond Aspose.Words are required, and the code works with Java 8‑plus.

## Prerequisites

- Java 8 or newer installed (I’m using JDK 17, but anything that supports Maven works)
- Aspose.Words for Java 23.9 or later – add the dependency to your `pom.xml` or download the JAR
- A basic understanding of Java syntax (if you can write a `main` method, you’re good)
- An IDE or text editor of your choice (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip:** If you’re using Maven, the dependency looks like this:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Now that we’ve got the groundwork set, let’s dive into the code.

## Insert Rectangle Shape and Set Its Size

The first thing you’ll do is create a fresh `Document` and a `DocumentBuilder`. The builder is your “pen” that draws shapes onto the page. Below we **insert rectangle shape** and immediately **set shape size** to 100 × 80 points.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Notice how the `setWidth`/`setHeight` calls **set shape size** in points (1 pt ≈ 1/72 inch). You could also use `setSize` if you prefer a single method, but the explicit calls make the intent crystal clear.

## Position Shape on the Page

After we have the first rectangle, we need to **position shape** the second one so it doesn’t overlap the first. Positioning works the same way: you set the `Left` and `Top` properties relative to the group’s origin.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

If you’re wondering why we use `setLeft` instead of `setX`, it’s because Aspose.Words adopts the classic Windows GDI coordinate system—`Left` is the horizontal offset, `Top` is the vertical offset. Changing these values lets you fine‑tune the layout without fiddling with tables or paragraphs.

## How to Group Shapes

You might ask, “Why bother with a group at all?” Grouping makes sense when you want shapes to move together, rotate as a unit, or share a common style. In the snippet above we already created a `GroupShape` via `builder.insertGroupShape`. That object is essentially a container—think of it as a folder that holds other shape files.

> **Why this matters:** If you later decide to add a caption or rotate the whole diagram, you only need to modify the group, not each rectangle individually.

## How to Add Rectangle to a Group

The act of **how to add rectangle** to the group is simply calling `group.appendChild(rectangle)`. Under the hood Aspose.Words updates the group’s internal collection and automatically recalculates the bounding box so the group still fits its declared width and height.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

You can experiment with other `ShapeType`s—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, etc.—and the same `appendChild` pattern works.

## Save the Document

Finally, we persist the document to disk. The path can be absolute or relative; just make sure the folder exists.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

When you open `GroupShape.docx` in Microsoft Word, you’ll see two rectangles side‑by‑side, both locked inside a light‑gray box. Selecting the gray box will highlight both rectangles at once—proof that **how to group shapes** really works.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file"}

*Image alt text (SEO):* **insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file**.

## Expected Output

- A `GroupShape.docx` file located in the `output` folder.
- Inside the document: a 400 × 200 pt group containing two rectangles (100 × 80 pt and 120 × 60 pt) positioned at (20, 30) and (150, 50) respectively.
- The group has a thin black border and a light‑gray fill, making the grouping visually obvious.

Open the file and try dragging the gray box—both rectangles should move together. If they don’t, double‑check that you called `group.appendChild` for each shape.

## Common Pitfalls & Edge Cases

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Rectangles appear outside the page** | `Left`/`Top` values exceed the group’s dimensions | Increase the group size (`insertGroupShape(width, height)`) or reduce offsets |
| **Group disappears after saving** | The group’s `Width`/`Height` are set to 0 | Provide non‑zero dimensions when calling `insertGroupShape` |
| **Shape colors look wrong** | Default fill is transparent; Word may render it as white | Explicitly set `setFillColor` or use `ShapeStyle` |
| **Exception `ArgumentOutOfRangeException`** | Using negative coordinates | Keep `Left` and `Top` non‑negative |

Addressing these early saves you from the “why does my shape vanish?” headaches that many newcomers encounter.

## Recap & Next Steps

We’ve covered the full lifecycle of **insert rectangle shape** in Java: creating a document, **set shape size**, **position shape**, **how to group shapes**, and **how to add rectangle** to that group. The complete, runnable example lives in the code block above, and you can paste it straight into a Maven project to see the result.

What’s next? Consider experimenting with:

- Adding text inside each rectangle via


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}