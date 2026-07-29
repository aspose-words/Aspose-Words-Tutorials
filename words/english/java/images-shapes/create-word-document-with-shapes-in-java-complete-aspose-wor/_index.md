---
category: general
date: 2026-07-29
description: Create word document in Java using Aspose.Words. Learn to insert rectangle
  shape, group shapes in Word, and save document as docx quickly.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: en
lastmod: 2026-07-29
og_description: Create word document in Java with Aspose.Words. Insert rectangle shape,
  group shapes in Word, and save document as docx in minutes.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Create Word Document with Shapes – Java Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
url: /java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Word Document with Shapes in Java – Complete Aspose.Words Guide

Ever wondered how to **create word document** programmatically and sprinkle it with custom graphics? You're not the only one. Whether you need to generate a report with highlighted sections or design a flyer on the fly, mastering shape handling in Word can save you hours of manual work.

In this tutorial we'll walk through the exact steps to **create word document** using Aspose.Words for Java, **insert rectangle shape**, **group shapes in Word**, and finally **save document as docx**. By the end you’ll have a fully runnable example that you can drop into any project.

## What You’ll Walk Away With

- A fresh Word file generated entirely from Java code.  
- Two distinct shapes (a rectangle and an ellipse) added to the page.  
- Those shapes bundled together with the **group shapes in word** API, making them behave like a single object.  
- The file persisted on disk as a standard `.docx` that opens in Microsoft Word without a hitch.  

No external tools, no fiddly XML hacks—just clean, typed Java and Aspose.Words.

---

## Prerequisites

Before we dive, make sure you have:

1. **Java Development Kit (JDK) 8 or newer** – the code targets Java 8+.  
2. **Aspose.Words for Java** JAR (you can grab the latest version from the Maven Central repository).  
3. A modest IDE (IntelliJ IDEA, Eclipse, or even a simple text editor).  

If you’ve got those, great—let’s get started.

---

## Step‑by‑Step Implementation

Below we break the process into bite‑size steps. Each step includes a code snippet, a short explanation, and a tip you might not find in the official docs.

### ## Create Word Document with Shapes Using Aspose.Words

The first thing you need is an empty Word file to work with. Aspose.Words makes this a one‑liner.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Why this matters:**  
`Document` is the container for everything—text, tables, images, and shapes. `DocumentBuilder` is the friendly helper that lets you add content without wrestling with low‑level objects. Think of it as a pen that writes directly onto the page.

> **Pro tip:** If you plan to start with a template (e.g., a company letterhead), replace `new Document()` with `new Document("template.docx")`.

### ## Insert Rectangle Shape and Other Shapes

Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates the **insert rectangle shape** keyword, while the ellipse shows that you can mix shape types freely.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**What’s happening under the hood?**  
Each call to `insertShape` creates a `Shape` object and automatically adds it to the current paragraph. The `setLeft`/`setTop` methods position the shape relative to the page margins, measured in points (1 pt = 1/72 in). By tweaking these numbers you can place shapes anywhere you like.

> **Common question:** *Can I add a picture instead of a solid color?*  
> Absolutely—just replace the fill color with an image using `shape.getFill().setImage("path/to/image.png")`.

### ## Group Shapes in Word for Easy Manipulation

Having two separate objects is fine, but often you want to move them together. That’s where **group shapes in word** shines.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Why group?**  
When shapes are grouped, any transformation—move, rotate, resize—applies to the whole collection. This mirrors the behavior you get when you manually select multiple shapes in the Word UI and hit *Group*. It also simplifies later code because you only need to adjust one object instead of many.

> **Edge case:** If you later need to ungroup, call `group.getParentNode().removeChild(group)` and re‑insert the children individually.

### ## Save Document as DOCX and Verify Output

Finally, we persist the file. This step fulfills the **save document as docx** requirement.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**What to expect:**  
Open the generated `GroupShapeExample.docx` in Microsoft Word. You’ll see a blue rectangle and a green ellipse, neatly grouped. Drag the group around—both shapes move together, just like you’d expect from the UI.

> **Tip:** Use `SaveFormat.PDF` if you need a PDF version; the same code works without changes.

### ## Full Working Example and Common Pitfalls

Below is the complete, ready‑to‑run Java class. Copy‑paste it into your project, adjust the output folder, and hit *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Common Pitfalls & How to Avoid Them

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` on `builder`** | Forgetting to instantiate `DocumentBuilder` after creating `Document`. | Ensure `new DocumentBuilder(doc)` runs before any shape insertion. |
| **Shapes appear off‑page** | Using pixel values instead of points, or not accounting for margins. | Remember that Aspose.Words expects points; 72 pt = 1 in. Adjust `setLeft`/`setTop` accordingly. |
| **Group disappears after save** | Adding shapes to the group *after* the group has been saved. | Always group before calling `doc.save()`. |
| **File not found on save** | Output directory doesn’t exist. | Create the directory programmatically (`new File("output").mkdirs();`) or use an existing path. |

---

## Conclusion

We’ve just **create word document** from scratch, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, and finally **save document as docx**—all with a handful of lines of Java. The power of Aspose.Words lies in its clear object model; you can treat a Word file like a canvas, paint on it with shapes, and then export it wherever you need.

Feeling adventurous? Try swapping the rectangle for a star, add text inside the shapes using `Shape.getTextBox()`, or experiment with rotation (`shape.setRotationAngle(45)`). The API is rich, and the possibilities are practically endless.

Got questions about more advanced scenarios—like linking shapes to bookmarks or exporting to PDF with embedded fonts? Drop a comment below, and we’ll dive deeper together. Happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}