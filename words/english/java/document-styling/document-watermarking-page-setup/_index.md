---
title: Document Watermarking and Page Setup
linktitle: Document Watermarking and Page Setup
second_title: Aspose.Words Java Document Processing API
description: Learn how to apply watermarks and set up page configurations with Aspose.Words for Java. A comprehensive guide with source code.
weight: 13
url: /java/document-styling/document-watermarking-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Document Watermarking and Page Setup

## Introduction

In the realm of document manipulation, Aspose.Words for Java stands as a powerful tool, allowing developers to wield control over every aspect of document processing. In this comprehensive guide, we will delve into the intricacies of document watermarking and page setup using Aspose.Words for Java. Whether you are a seasoned developer or just stepping into the world of Java document processing, this step-by-step guide will equip you with the knowledge and source code you need.

## Document Watermarking

### Adding Watermarks

Adding watermarks to documents can be crucial for branding or securing your content. Aspose.Words for Java makes this task straightforward. Here's how:

```java
// Load the document
Document doc = new Document("document.docx");

// Create a watermark
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// Position the watermark
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// Insert the watermark
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document
doc.save("document_with_watermark.docx");
```

### Customizing Watermarks

You can further customize watermarks by adjusting font, size, color, and rotation. This flexibility ensures your watermark matches your document's style seamlessly.

## Page Setup

### Page Size and Orientation

Page setup is pivotal in document formatting. Aspose.Words for Java offers complete control over page size and orientation:

```java
// Load the document
Document doc = new Document("document.docx");

// Set page size to A4
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// Change page orientation to landscape
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// Save the modified document
doc.save("formatted_document.docx");
```

### Margins and Page Numbering

Precise control over margins and page numbering is essential for professional documents. Achieve this with Aspose.Words for Java:

```java
// Load the document
Document doc = new Document("document.docx");

// Set margins
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// Enable page numbering
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// Save the formatted document
doc.save("formatted_document.docx");
```

## FAQs

### How can I remove a watermark from a document?

To remove a watermark from a document, you can iterate through the document's shapes and remove the ones representing watermarks. Here's a snippet:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### Can I add multiple watermarks to a single document?

Yes, you can add multiple watermarks to a document by creating additional Shape objects and positioning them as needed.

### How do I change the page size to legal in landscape orientation?

To set the page size to legal in landscape orientation, modify the page width and height as follows:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### What is the default font for watermarks?

The default font for watermarks is Calibri with a font size of 36.

### How can I add page numbers starting from a specific page?

You can achieve this by setting the starting page number in your document as follows:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### How do I center-align text in the header or footer?

You can center-align text in the header or footer by using the setAlignment method on the Paragraph object within the header or footer.

## Conclusion

In this extensive guide, we've explored the art of document watermarking and page setup using Aspose.Words for Java. Armed with the provided source code snippets and insights, you now possess the tools to manipulate and format your documents with finesse. Aspose.Words for Java empowers you to create professional, branded documents tailored to your exact specifications.

Mastering document manipulation is a valuable skill for developers, and Aspose.Words for Java is your trusted companion in this journey. Start creating stunning documents today!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
