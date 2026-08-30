---
category: general
date: 2026-05-04
description: Create blank word document in Java and learn how to set shadow color,
  blur, and offset for shapes – quick tutorial.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: en
og_description: Create blank word document in Java and learn how to set shadow color,
  blur, and offset for shapes. Follow this step‑by‑step tutorial.
og_title: Create blank word with shadow in Java – Full guide
tags:
- Aspose.Words
- Java
- Document Automation
title: Create blank word with shadow in Java – Full guide
url: /java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Create blank word with shadow in Java – Full guide

Ever needed to **create blank word** files from code and make them look a bit fancier? You're not the only one. In many reporting or template‑generation projects, the first thing you do is spin up an empty Word document, then sprinkle in a shape with a shadow to give it that polished feel.  

In this tutorial we’ll walk through exactly that—how to create a blank Word document using Aspose.Words for Java, **how to add shadow** to a shape, and the nitty‑gritty of **set shadow color**, **how to set blur**, and **how to set offset**. By the end you’ll have a ready‑to‑use `.docx` file that showcases a rectangle with a nicely blurred, semi‑transparent red shadow.

## What you’ll need

- **Aspose.Words for Java** (any recent version; the code works with 23.9+)
- JDK 8 or newer
- An IDE or simple text editor plus a terminal
- Basic Java knowledge—nothing fancy, just the ability to run a `main` method

No extra Maven or Gradle config is required for the demo; just drop the Aspose JAR on your classpath and you’re good to go.

---

![create blank word document with shadow example](image-placeholder.png){: .center alt="create blank word document with shadow example"}

## Create blank word – Initializing the Document

The first step is to spin up a brand‑new, empty Word file. Think of it as a fresh canvas where you can later draw shapes, tables, or text.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why this matters:** `Document` represents the whole `.docx` package. By creating it with the default constructor you’re effectively **create blank word** – there’s no content, no sections, just the file structure ready for you to fill.

## How to add shadow to a shape

Now that we have a clean document, let’s insert a rectangle that will host our shadow. This is where the visual magic begins.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Pro tip:** The `insertShape` call automatically adds the shape to the current paragraph, so you don’t need to manage positioning manually unless you want absolute placement.

## Set shadow color – making the shadow stand out

A shadow without color is just a grey blur, which can look flat. By setting the shadow’s color you can match branding or simply make it pop.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **What’s happening:** `ShadowFormat` controls every visual aspect of the shadow. Enabling `setVisible(true)` turns the effect on, and `setColor` lets you pick any `java.awt.Color`. In our example we chose red to demonstrate **set shadow color** clearly.

## How to set blur for a subtle effect

A crisp, hard‑edged shadow can look harsh. Adding blur softens the edges, giving a more natural look.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Why blur matters:** The `setBlur` value is measured in points. A value of `5.0` creates a gentle diffusion; increase it for a cloudier shadow, decrease for a sharper outline.

## How to set offset – positioning the shadow

Offsets determine where the shadow lands relative to the shape. Think of them as X‑ and Y‑shifts.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Offset explained:** Positive X moves the shadow right, positive Y moves it down. Play with negative numbers if you want the shadow to appear on the opposite side.

## Fine‑tuning transparency

If you want the shadow to be less dominant, adjust its transparency. This step isn’t a keyword requirement but rounds out the visual control.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Saving the document – see the result

Finally, write the document to disk. You’ll end up with a `.docx` you can open in Word, LibreOffice, or any viewer that supports the format.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **What you should see:** Open `ShadowShape.docx`. A single page will show a 150 × 80 pt rectangle with a red, slightly blurred shadow shifted 8 pt down and right. The shadow is 30 % transparent, so the rectangle remains clearly visible.

---

## Common questions and edge cases

### What if I need a different shape?

Replace `ShapeType.RECTANGLE` with any other enum value (`ELLIPSE`, `CLOUD`, `CALLOUT`, etc.). The shadow settings work identically across shapes.

### Can I apply the same shadow to multiple shapes without repeating code?

Absolutely. Create a helper method:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Then call `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` for any shape.

### Does this work with older Aspose versions?

The `ShadowFormat` API has been stable since version 19.8, so you should be fine with most recent releases. If you’re on a very old build, check the Javadoc for `ShadowFormat` to verify method names.

### How to export to PDF while keeping the shadow?

Just call `document.save("output.pdf");` after the shape is created. Aspose.Words renders shadows correctly in PDF, preserving blur and transparency.

---

## Recap – create blank word with a custom shadow

We started by **create blank word** using `new Document()`, then inserted a rectangle, **set shadow color**, learned **how to add shadow**, tweaked **how to set blur**, and finally adjusted **how to set offset** to position it just right. The complete, runnable code lives in the snippet above, and the resulting file demonstrates the effect clearly.

---

## What’s next?

- **Experiment with other shadow properties** like `ShadowFormat.setStyle(ShadowStyle.OUTER)` for different visual styles.
- **Combine multiple shapes** each with its own shadow to build complex diagrams.
- **Add text inside the shape** using `builder.insertHtml("<b>Hello</b>")` before inserting the shape, then apply the same shadow logic.
- **Explore other formatting options** such as line style, fill color, or gradient fills—Aspose.Words offers a rich API for all of these.

Feel free to tweak the blur radius, offsets, or colors until the shadow feels just right for your document’s design language. Happy coding, and may your generated Word files always look a little more polished!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}