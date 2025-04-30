---
title: Using Document Properties in Aspose.Words for Java
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
description: Optimize document management with Aspose.Words for Java. Learn to work with document properties, add custom metadata, and more in this comprehensive tutorial.
weight: 32
url: /java/document-manipulation/using-document-properties/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Using Document Properties in Aspose.Words for Java


## Introduction to Document Properties

Document properties are a vital part of any document. They provide additional information about the document itself, such as its title, author, subject, keywords, and more. In Aspose.Words for Java, you can manipulate both built-in and custom document properties.

## Enumerating Document Properties

### Built-in Properties

To retrieve and work with built-in document properties, you can use the following code snippet:

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

This code will display the document's name and built-in properties, including properties like "Title," "Author," and "Keywords."

### Custom Properties

To work with custom document properties, you can use the following code snippet:

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

This code snippet demonstrates how to add custom document properties, including a boolean value, a string, a date, a revision number, and a numeric value.

## Removing Document Properties

To remove specific document properties, you can use the following code:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

This code removes the custom property "Authorized Date" from the document.

## Configuring Link to Content

In some cases, you may want to create links within your document. Here's how you can do it:

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

This code snippet demonstrates how to create a bookmark in your document and add a custom document property that links to that bookmark.

## Converting Between Measurement Units

In Aspose.Words for Java, you can convert measurement units easily. Here's an example of how to do it:

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

This code snippet sets various margins and distances in inches by converting them to points.

## Using Control Characters

Control characters can be useful when dealing with text. Here's how to replace a control character in your text:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

In this example, we replace the carriage return (`\r`) with a carriage return followed by a line feed (`\r\n`).

## Conclusion

Document properties play a significant role in managing and organizing your documents effectively in Aspose.Words for Java. Whether it's working with built-in properties, custom properties, or using control characters, you have a range of tools at your disposal to enhance your document management capabilities.

## FAQ's

### How do I access built-in document properties?

To access built-in document properties in Aspose.Words for Java, you can use the `getBuiltInDocumentProperties` method on the `Document` object. This method returns a collection of built-in properties that you can iterate through.

### Can I add custom document properties to a document?

Yes, you can add custom document properties to a document using the `CustomDocumentProperties` collection. You can define custom properties with various data types, including strings, booleans, dates, and numeric values.

### How can I remove a specific custom document property?

To remove a specific custom document property, you can use the `remove` method on the `CustomDocumentProperties` collection, passing the name of the property you want to remove as a parameter.

### What is the purpose of linking to content within a document?

Linking to content within a document allows you to create dynamic references to specific parts of the document. This can be useful for creating interactive documents or cross-references between sections.

### How can I convert between different measurement units in Aspose.Words for Java?

You can convert between different measurement units in Aspose.Words for Java by using the `ConvertUtil` class. It provides methods to convert units such as inches to points, points to centimeters, and more.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
