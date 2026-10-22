---
category: general
date: 2026-07-16
description: Create blank Word document in Java and learn how to hide shape, save
  document to file, and generate Word document Java examples in minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- save document to file
- generate word document java
- hide shape in word
language: en
lastmod: 2026-07-16
og_description: Create blank Word document in Java and instantly see how to hide shape,
  save document to file, and generate Word document Java code that works today.
og_image_alt: Screenshot of a Word file showing a hidden rectangle shape created by
  Java code
og_title: Create Blank Word Document with Java – Complete Aspose.Words Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create blank Word document in Java and learn how to hide shape, save
    document to file, and generate Word document Java examples in minutes.
  headline: Create Blank Word Document with Java – Full Aspose.Words Guide
  type: TechArticle
- description: Create blank Word document in Java and learn how to hide shape, save
    document to file, and generate Word document Java examples in minutes.
  name: Create Blank Word Document with Java – Full Aspose.Words Guide
  steps:
  - name: Why start with a blank document?
    text: A blank `Document` object gives you a pristine canvas—no headers, footers,
      or hidden metadata. This guarantees that the shape you later add is the only
      visual element, making the hiding logic easier to verify.
  - name: Understanding `setHidden`
    text: '`setHidden(true)` sets the shape’s *Hidden* attribute in the underlying
      OpenXML. Word respects this flag and treats the shape as if it never existed
      in the layout. It’s the same as checking “Hide” in the shape’s properties dialog—except
      we did it programmatically.'
  - name: Expected Output
    text: 'When you run the program, you’ll see a console line confirming the file
      location. Opening `HiddenShapeDemo.docx` in Microsoft Word shows a completely
      empty page—no orange rectangle, because we **hide shape in Word**. If you temporarily
      comment out `rectangle.setHidden(true);` and re‑run, the orange '
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Create Blank Word Document with Java – Full Aspose.Words Guide
url: /java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create Blank Word Document with Java – Full Aspose.Words Guide

Ever wondered **how to create blank Word document** programmatically while also controlling the visibility of shapes? You're not the only one. Whether you need a clean canvas for a report template or you’re building a mail‑merge engine, starting with a blank document is the first step toward any Word automation project.

In this tutorial we’ll walk through the entire process: creating a blank Word document, inserting a rectangle, hiding that shape, and finally **save document to file**. By the end you’ll have a complete, runnable Java snippet that **generates Word document Java** style, and you’ll understand the nuances of **how to hide shape** and **hide shape in Word** using Aspose.Words.

---

## Prerequisites

Before we dive in, make sure you have:

* **Java 17** (or any recent JDK) installed – older versions work but the latest gives you better performance.
* **Aspose.Words for Java** library (the Maven artifact `com.aspose:aspose-words`). You can grab it from Maven Central or download the JAR from the Aspose site.
* A modest IDE (IntelliJ IDEA, Eclipse, or VS Code) – anything that lets you compile and run Java code.
* Write permission to a folder where the demo file will be saved.

No additional dependencies are required; the code we’ll share is completely self‑contained.

---

## Step 1: Set Up the Maven Project

If you’re using Maven, add the following dependency to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

*Pro tip:* keep the version number up‑to‑date; Aspose releases frequent bug‑fixes that affect shape handling.

If you prefer a plain JAR, just place `aspose-words-24.9.jar` on your classpath and you’re good to go.

---

## Create Blank Word Document with Java

Now that the environment is ready, let’s **create blank word document**. This is the foundation for everything that follows.

```java
import com.aspose.words.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ... we’ll add more code here later ...

        // Step 6: Save the document to a file
        doc.save("output/HiddenShapeDemo.docx");
    }
}
```

### Why start with a blank document?

A blank `Document` object gives you a pristine canvas—no headers, footers, or hidden metadata. This guarantees that the shape you later add is the only visual element, making the hiding logic easier to verify.

---

## Insert a Rectangle Shape

With the builder ready, we’ll drop a rectangle onto the page. The dimensions are expressed in points (1 pt ≈ 1/72 inch).

```java
// Step 3: Insert a rectangle shape with specific dimensions
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 100);
```

The `insertShape` method returns a `Shape` object that we can style. By default the shape is visible, which is perfect for the next step where we’ll change its appearance.

---

## How to Hide Shape in Word Using Aspose.Words

Now for the core of the tutorial: **how to hide shape** so it never appears when the document is opened in Microsoft Word. The property we need is `setHidden(true)`. Before we hide it, we’ll give it a fill color so you can see the difference when testing.

```java
// Step 4: Apply a fill color to make the shape visible when not hidden
rectangle.setFillColor(java.awt.Color.ORANGE);

// Step 5: Hide the shape so it does not appear in the rendered document
rectangle.setHidden(true);
```

### Understanding `setHidden`

`setHidden(true)` sets the shape’s *Hidden* attribute in the underlying OpenXML. Word respects this flag and treats the shape as if it never existed in the layout. It’s the same as checking “Hide” in the shape’s properties dialog—except we did it programmatically.

*Edge case:* If you later export the document to PDF, the hidden shape stays hidden. However, some third‑party viewers that ignore the OpenXML hidden flag might still render it. Always test the final output if you target non‑Word consumers.

---

## Save Document to File – Persisting Your Work

After tweaking the shape, the final step is to **save document to file**. Aspose.Words offers a simple `save` method that accepts a path and optional format.

```java
// Step 6: Save the document to a file
doc.save("output/HiddenShapeDemo.docx"); // .docx is the default Word format
```

Make sure the `output` directory exists or use `Files.createDirectories(Paths.get("output"))` to create it on the fly.

*Why not use `doc.save(new FileOutputStream(...))`?* You can, but the one‑liner is clearer for a tutorial and works across all platforms.

---

## Full, Runnable Example

Putting everything together, here’s the complete program you can copy‑paste into your IDE:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;

public class ShapeVisibilityDemo {
    public static void main(String[] args) throws Exception {
        // Ensure output folder exists
        Path outDir = Paths.get("output");
        if (Files.notExists(outDir)) Files.createDirectories(outDir);

        // 1️⃣ Create a new blank document
        Document doc = new Document();

        // 2️⃣ Prepare a builder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle (150 pt × 100 pt)
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 150, 100);

        // 4️⃣ Give it a bright fill so we could see it if it weren’t hidden
        rectangle.setFillColor(Color.ORANGE);

        // 5️⃣ Hide the shape – this is the key part of “how to hide shape”
        rectangle.setHidden(true);

        // 6️⃣ Persist the document – “save document to file”
        doc.save(outDir.resolve("HiddenShapeDemo.docx").toString());

        System.out.println("Document created successfully at " + outDir.resolve("HiddenShapeDemo.docx"));
    }
}
```

### Expected Output

When you run the program, you’ll see a console line confirming the file location. Opening `HiddenShapeDemo.docx` in Microsoft Word shows a completely empty page—no orange rectangle, because we **hide shape in Word**. If you temporarily comment out `rectangle.setHidden(true);` and re‑run, the orange rectangle appears, confirming that the hiding logic works.

---

## Common Questions & Gotchas

| Question | Answer |
|----------|--------|
| **Can I hide other objects (e.g., images)?** | Yes. Any node that inherits from `ShapeBase` (pictures, charts, text boxes) exposes `setHidden(true)`. |
| **What if I need the shape visible only in the print view?** | Use `setVisible(true)` together with `setHidden(true)` on the *screen* view via `Shape.setVisible` and `Shape.setHidden` combined with `Shape.setLayoutInCell`. It’s a bit more involved—see Aspose docs for `Shape.isDisplayWhenHidden`. |
| **Does the hidden flag affect Word’s “Select Objects” mode?** | Hidden shapes are excluded from selection, which is handy when you embed metadata shapes. |
| **Is there any performance impact?** | Negligible. The hidden flag is just an attribute in the XML; Aspose processes it as it writes the file. |

---

## Next Steps: Extending the Document

Now that you know **how to hide shape** and **save document to file**, you might want to:

* **Add multiple hidden shapes** for storing custom data (e.g., JSON payloads) inside the document.
* **Combine hidden shapes with content controls** to build rich templates.
* **Export to PDF** using `doc.save("output/HiddenShapeDemo.pdf");` – the hidden shape stays hidden in the PDF as well.
* **Explore other shape types** (`ShapeType.ELLIPSE`, `ShapeType.CLOUD`) and experiment with `setStrokeColor` and `setStrokeWeight`.

Each of these topics ties back to our secondary keywords—**generate word document java**, **hide shape in word**, and **save document to file**—so you’ll continue to reinforce the concepts you just learned.

---

## Conclusion

You now have a solid, end‑to‑end example that **creates blank word document** with Java, inserts a rectangle, **hides shape in word**, and finally **saves document to file**. The code is ready to drop into any Java project, and the explanations show *why* each line matters, not just *what* it does. 

Feel free to tweak the dimensions, colors, or even hide multiple objects—your Word automation adventures have just begun. Got a twist you tried? Share it in the comments, and happy coding!


## What Should You Learn Next?


The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}