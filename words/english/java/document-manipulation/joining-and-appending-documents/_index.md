---
title: Joining and Appending Documents in Aspose.Words for Java
linktitle: Joining and Appending Documents
second_title: Aspose.Words Java Document Processing API
description: Learn how to join and append documents effortlessly using Aspose.Words for Java. Preserve formatting, manage headers footers, and more.
weight: 30
url: /java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Joining and Appending Documents in Aspose.Words for Java


## Introduction to Joining and Appending Documents in Aspose.Words for Java

In this tutorial, we'll explore how to join and append documents using the Aspose.Words for Java library. You'll learn how to seamlessly merge multiple documents while preserving formatting and structure.

## Prerequisites

Before we begin, make sure you have Aspose.Words for Java API set up in your Java project.

## Document Joining Options

### Simple Append

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Append with Import Format Options

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Append to Blank Document

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Append with Page Number Conversion

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convert NUMPAGES fields
dstDoc.updatePageLayout(); // Update page layout for correct numbering
```

## Handling Different Page Setups

When appending documents with different page setups:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Ensure page setup settings match the destination document
```

## Joining Documents with Different Styles

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Smart Style Behavior

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Inserting Documents with DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Keeping Source Numbering

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Handling Text Boxes

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Managing Headers and Footers

### Linking Headers and Footers

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Unlinking Headers and Footers

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Conclusion

Aspose.Words for Java provides flexible and powerful tools for joining and appending documents, whether you need to maintain formatting, handle different page setups, or manage headers and footers. Experiment with these techniques to meet your specific document processing needs.

## FAQ's

### How can I join documents with different styles seamlessly?

To join documents with different styles, use `ImportFormatMode.USE_DESTINATION_STYLES` when appending.

### Can I preserve page numbering when appending documents?

Yes, you can preserve page numbering by using the `convertNumPageFieldsToPageRef` method and updating the page layout.

### What is Smart Style Behavior?

Smart Style Behavior helps maintain consistent styles when appending documents. Use it with `ImportFormatOptions` for better results.

### How can I handle text boxes when appending documents?

Set `importFormatOptions.setIgnoreTextBoxes(false)` to include text boxes during appending.

### What if I want to link/unlink headers and footers between documents?

You can link headers and footers with `linkToPrevious(true)` or unlink them with `linkToPrevious(false)` as needed.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
