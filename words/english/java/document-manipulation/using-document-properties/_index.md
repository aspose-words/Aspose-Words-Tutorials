---
title: "Convert Inches to Points – Using Document Properties in Aspose.Words for Java"
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
description: "Learn how to convert inches to points, read document metadata Java, add custom properties Java, and set page margins Java with Aspose.Words for Java."
weight: 32
url: /java/document-manipulation/using-document-properties/
date: 2026-01-16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Convert Inches to Points – Using Document Properties in Aspose.Words for Java

In this tutorial you’ll discover how to **convert inches to points** when setting page margins, read document metadata Java, add custom properties Java, and work with built‑in document properties using Aspose.Words for Java. Whether you’re generating reports, invoices, or legal documents, mastering these techniques gives you fine‑grained control over the appearance and metadata of your Word files.

## Quick Answers
- **How do I convert inches to points?** Use `ConvertUtil.inchToPoint(value)` from Aspose.Words.
- **Can I read document metadata in Java?** Yes – call `doc.getBuiltInDocumentProperties()` or `doc.getCustomDocumentProperties()`.
- **How do I add a custom property in Java?** Use `doc.getCustomDocumentProperties().add(name, value)`.
- **What method sets page margins in points?** `PageSetup.setTopMargin`, `setBottomMargin`, etc., accept point values.
- **Is linking to a bookmark supported?** Yes – use `addLinkToContent` on the custom properties collection.

## Introduction to Document Properties

Document properties are a vital part of any Word file. They store information such as title, author, subject, keywords, and any custom metadata you need for downstream processing. In Aspose.Words for Java you can manipulate both built‑in and custom document properties, and you can also control layout details like margins by converting measurement units (e.g., **convert inches to points**).

## What is “convert inches to points”?

In Word, layout measurements are expressed in points (1 point = 1/72 of an inch). Converting inches to points lets you define margins, indents, and spacing using familiar imperial units while the API works with points internally.

## Why manage document metadata in Java?

Embedding metadata makes it easier to search, categorize, and automate workflows. For example, you might tag a contract with an “Authorized” flag or store a revision number for audit trails. Reading and writing this information programmatically ensures consistency across large document batches.

## Prerequisites
- Java 17+ (or compatible JDK)
- Aspose.Words for Java library added to your project (Maven/Gradle)
- A sample `.docx` file (e.g., `Properties.docx`) placed in an accessible directory

## Step‑by‑Step Guide

### Enumerating Built‑in Document Properties
Below is a simple test that opens a document and prints all built‑in properties such as Title, Author, and Keywords.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Pro tip:** Use this snippet to verify that your metadata was correctly written during earlier steps.

### Adding Custom Document Properties (add custom properties java)
Custom properties let you store any data type you need—boolean, string, date, number, etc.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Why this matters:** Adding a flag like **Authorized** can drive downstream approval workflows without altering the document content.

### Removing a Custom Property
If a property is no longer needed, you can delete it cleanly.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Configuring a Link to Content (bookmark linking)
You can create a bookmark and then add a custom property that points to that bookmark, enabling dynamic cross‑references.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Converting Between Measurement Units (set page margins java)
Here’s where the primary keyword shines. We set margins in inches, then **convert inches to points** using `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Note:** `ConvertUtil` also provides `pointToInch`, `mmToPoint`, etc., for flexible layout handling.

### Using Control Characters (read document metadata java)
Control characters help you clean up text streams. This example replaces a carriage‑return (`\r`) with the Windows line‑break sequence (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Common Issues & Solutions
| Issue | Cause | Fix |
|-------|-------|-----|
| Margins look wrong after conversion | Using wrong unit (e.g., cm instead of inches) | Verify you call `ConvertUtil.inchToPoint` for inch values |
| Custom property not appearing | Property added after saving the document | Call `doc.save(...)` after adding properties |
| Bookmark link broken | Bookmark name typo | Ensure the bookmark name matches exactly in `addLinkToContent` |

## FAQ's

### How do I access built-in document properties?

To access built-in document properties in Aspose.Words for Java, you can use the `getBuiltInDocumentProperties` method on the `Document` object. This method returns a collection of built‑in properties that you can iterate through.

### Can I add custom document properties to a document?

Yes, you can add custom document properties to a document using the `CustomDocumentProperties` collection. You can define custom properties with various data types, including strings, booleans, dates, and numeric values.

### How can I remove a specific custom document property?

To remove a specific custom document property, you can use the `remove` method on the `CustomDocumentProperties` collection, passing the name of the property you want to remove as a parameter.

### What is the purpose of linking to content within a document?

Linking to content within a document allows you to create dynamic references to specific parts of the document. This can be useful for creating interactive documents or cross‑references between sections.

### How can I convert between different measurement units in Aspose.Words for Java?

You can convert between different measurement units in Aspose.Words for Java by using the `ConvertUtil` class. It provides methods to convert units such as inches to points, points to centimeters, and more.

## Frequently Asked Questions

**Q: How do I read document metadata Java without loading the whole file?**  
A: Use `DocumentInfo` to retrieve core properties without fully loading the document content.

**Q: Can I set page margins Java programmatically for existing documents?**  
A: Yes—open the document, modify `PageSetup` margins (convert inches to points if needed), and save.

**Q: Is it possible to export custom properties to PDF metadata?**  
A: When saving to PDF, Aspose.Words automatically maps custom document properties to PDF custom metadata.

**Q: Do control characters affect PDF conversion?**  
A: They are preserved during conversion; however, you may want to normalize line endings for consistency.

**Q: Which Aspose.Words version is required for `ConvertUtil`?**  
A: `ConvertUtil` has been available since Aspose.Words 16.5; any recent version supports it.

## Conclusion

By mastering **convert inches to points**, reading document metadata Java, and adding custom properties Java, you gain full control over both the visual layout and the hidden data of your Word files. These capabilities empower you to build automated document pipelines, enforce compliance, and create richly formatted reports—all with Aspose.Words for Java.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}