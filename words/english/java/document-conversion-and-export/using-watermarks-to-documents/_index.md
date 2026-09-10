---
title: How to Add Watermark to Documents Using Aspose.Words for Java
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
description: Learn how to add watermark to documents with Aspose.Words for Java, including image watermark example, change watermark color, set watermark transparency, and remove watermark document.
weight: 15
url: /java/document-conversion-and-export/using-watermarks-to-documents/
date: 2025-12-18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# How to Add Watermark to Documents Using Aspose.Words for Java

## Introduction to Adding Watermarks to Documents in Aspose.Words for Java

In this tutorial you’ll learn **how to add watermark** to Word documents with Aspose.Words for Java. Watermarks are a quick way to label a file as confidential, draft, or approved, and they can be text‑based or image‑based. We’ll walk through setting up the library, creating text and image watermarks, customizing their appearance (including changing watermark color and setting watermark transparency), and even removing a watermark document when it’s no longer needed.

## Quick Answers
- **What is a watermark?** A semi‑transparent overlay (text or image) that appears behind the main document content.  
- **Can I add multiple watermarks?** Yes – create several `Shape` objects and add each to the desired sections.  
- **How do I change watermark color?** Adjust the `Color` property in `TextWatermarkOptions`.  
- **Is there an image watermark example?** See the “Adding Image Watermarks” section below.  
- **Do I need a license to remove a watermark?** A valid Aspose.Words license is required for production use.

## Setting up Aspose.Words for Java

Before we start adding watermarks to documents, we need to set up Aspose.Words for Java. Follow these steps to get started:

1. Download Aspose.Words for Java from [here](https://releases.aspose.com/words/java/).  
2. Add the Aspose.Words for Java library to your Java project.  
3. Import the necessary classes in your Java code.

Now that we have the library set up, let’s dive into the actual watermark creation.

## Adding Text Watermarks

Text watermarks are a common choice when you want to add textual information to your documents. Here's how you can add a text watermark using Aspose.Words for Java:

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

**Why this matters:** By tweaking `setFontFamily`, `setFontSize`, and `setColor` you can **change watermark color** to match your branding, and `setSemitransparent(true)` lets you **set watermark transparency** for a subtle effect.

## Adding Image Watermarks

In addition to text watermarks, you can also add image watermarks to your documents. Below is an **image watermark example** that demonstrates how to embed a PNG logo or stamp:

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

You can repeat this block with different images or positions to **add multiple watermarks** to a single file.

## Customizing Watermarks

You can customize watermarks by adjusting their appearance and position. For text watermarks, you can change the font, size, color, and layout. For image watermarks, you can modify size, rotation, and alignment as demonstrated in the previous examples.

## Removing Watermarks

If you need to **remove watermark document** content, the following code iterates through all shapes and deletes those identified as watermarks:

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

## Common Use Cases & Tips

- **Confidential drafts:** Apply a semi‑transparent text watermark like “CONFIDENTIAL”.  
- **Branding:** Use an image watermark that contains your company logo.  
- **Section‑specific watermarks:** Loop through `doc.getSections()` and add a watermark only to the sections you choose.  
- **Performance tip:** Reuse the same `TextWatermarkOptions` instance when applying the same watermark to many documents.

## Frequently Asked Questions

### How can I change the font of a text watermark?

To change the font of a text watermark, modify the `setFontFamily` property in the `TextWatermarkOptions`. For example:

```java
options.setFontFamily("Times New Roman");
```

### Can I add multiple watermarks to a single document?

Yes, you can add multiple watermarks to a document by creating multiple `Shape` objects with different settings and adding them to the document.

### Is it possible to rotate a watermark?

Yes, you can rotate a watermark by setting the `setRotation` property in the `Shape` object. Positive values rotate the watermark clockwise, and negative values rotate it counter‑clockwise.

### How can I make a watermark semi‑transparent?

To make a watermark semi‑transparent, set the `setSemitransparent` property to `true` in the `TextWatermarkOptions`.

### Can I add watermarks to specific sections of a document?

Yes, you can add watermarks to specific sections of a document by iterating through the sections and adding the watermark to the desired sections.

---

**Last Updated:** 2025-12-18  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}