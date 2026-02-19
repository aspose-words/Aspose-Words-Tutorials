---
title: Create document with watermark using Aspose.Words for Java
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
description: Learn how to create document with watermark using Aspose.Words for Java and add image watermark java for professional-looking documents.
weight: 15
url: /java/document-conversion-and-export/using-watermarks-to-documents/
date: 2026-02-19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Create document with watermark using Aspose.Words for Java

In this tutorial you'll **create document with watermark** using the Aspose.Words for Java API. Watermarks—whether text or images—help you label a file as confidential, draft, or approved, and they can be applied programmatically to any Word document. We'll walk through setting up the library, adding both text and image watermarks, customizing their appearance, and even removing them when they’re no longer needed.

## Quick Answers
- **What does a watermark do?** It overlays text or an image on each page to convey status or branding.  
- **Which library adds watermarks in Java?** Aspose.Words for Java provides built‑in watermark support.  
- **Can I add an image watermark?** Yes—use the `Shape` class and the `add image watermark java` approach.  
- **Is the watermark semi‑transparent?** You can control opacity via `setSemitransparent` for text watermarks.  
- **Do I need a license?** A free trial works for testing; a commercial license is required for production.

## What is a watermark and why use it?

A watermark is a faint overlay—textual or graphical—added to every page of a document. It’s commonly used to indicate **confidentiality**, **draft status**, or **branding** without altering the underlying content. Adding watermarks programmatically ensures consistency across large batches of files and saves time compared with manual editing.

## Setting up Aspose.Words for Java

Before we start adding watermarks, make sure the library is ready in your project:

1. Download Aspose.Words for Java from [here](https://releases.aspose.com/words/java/).  
2. Add the downloaded JAR (or Maven/Gradle dependency) to your project's classpath.  
3. Import the required classes in your Java source file:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Now that the library is set up, let’s dive into the actual watermark code.

## How to add a text watermark

Text watermarks are ideal for labeling a document as “CONFIDENTIAL” or “DRAFT”. The following snippet shows a clean way to **create document with watermark** using `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### Customizing the text watermark
- **Font family & size** – change `setFontFamily` and `setFontSize`.  
- **Color** – use any `java.awt.Color`.  
- **Layout** – choose `HORIZONTAL`, `DIAGONAL`, etc.  
- **Transparency** – toggle `setSemitransparent(true)` for a lighter look.

## How to add an image watermark (add image watermark java)

Image watermarks are perfect for logos or custom graphics. Below is the **add image watermark java** example that inserts a PNG into the center of each page.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Tips for image watermarks
- **Resize** using `setWidth` / `setHeight` to fit the page.  
- **Position** can be centered or aligned to any margin using `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparency** can be applied by adjusting the image’s alpha channel before loading.

## How to remove watermarks

When a document no longer needs a watermark, you can delete it programmatically. The code below iterates through all shapes and removes any that contain “Watermark” in their name.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Common pitfalls and troubleshooting

- **Missing watermark after saving** – ensure you call `doc.save()` after setting the watermark.  
- **Image not appearing** – verify the image path is correct and the file is a supported format (PNG, JPEG, BMP).  
- **Transparency not applied** – `setSemitransparent(true)` only works for text watermarks; for images, edit the PNG’s alpha channel.  
- **Multiple sections** – if your document has several sections, add the watermark to each section’s body or use `doc.getWatermark().setText(...)` which applies globally.

## Frequently Asked Questions

**Q: How can I change the font of a text watermark?**  
A: Modify the `setFontFamily` property in `TextWatermarkOptions`, e.g., `options.setFontFamily("Times New Roman");`.

**Q: Can I add multiple watermarks to a single document?**  
A: Yes. Create multiple `Shape` objects (for images) or call `doc.getWatermark().setText(...)` with different options for each watermark.

**Q: Is it possible to rotate a watermark?**  
A: For image watermarks, set the rotation on the `Shape` object with `watermark.setRotation(angle)`. For text watermarks, use the `setLayout` property (e.g., `WatermarkLayout.DIAGONAL`).

**Q: How can I make a watermark semi‑transparent?**  
A: Set `options.setSemitransparent(true)` in `TextWatermarkOptions`. For images, adjust the image’s opacity before loading.

**Q: Can I add watermarks to specific sections of a document?**  
A: Yes. Iterate through `doc.getSections()` and add the watermark only to the desired sections.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-02-19  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose