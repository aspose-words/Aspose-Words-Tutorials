---
title: Finding and Replacing Text in Aspose.Words for Java
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
description: Learn how to find and replace text in Word documents with Aspose.Words for Java. Step-by-step guide with code examples. Enhance your Java document manipulation skills.
weight: 15
url: /java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Finding and Replacing Text in Aspose.Words for Java


## Introduction to Finding and Replacing Text in Aspose.Words for Java

Aspose.Words for Java is a powerful Java API that allows you to work with Word documents programmatically. One of the common tasks when dealing with Word documents is finding and replacing text. Whether you need to update placeholders in templates or perform more complex text manipulations, Aspose.Words for Java can help you achieve your goals efficiently.

## Prerequisites

Before we dive into the details of finding and replacing text, make sure you have the following prerequisites in place:

- Java Development Environment
- Aspose.Words for Java library
- A sample Word document to work with

You can download the Aspose.Words for Java library from [here](https://releases.aspose.com/words/java/).

## Finding and Replacing Simple Text

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

In this example, we load a Word document, create a `DocumentBuilder`, and use the `replace` method to find and replace "old-text" with "new-text" within the document.

## Using Regular Expressions

Regular expressions provide powerful pattern matching capabilities for text search and replacement. Aspose.Words for Java supports regular expressions for more advanced find and replace operations.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

In this example, we use a regular expression pattern to find and replace text within the document.

## Ignoring Text Inside Fields

You can configure Aspose.Words to ignore text inside fields when performing find and replace operations.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

This is useful when you want to exclude text inside fields, such as merge fields, from being replaced.

## Ignoring Text Inside Delete Revisions

You can configure Aspose.Words to ignore text inside delete revisions during find and replace operations.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

This allows you to exclude text that has been marked for deletion in tracked changes from being replaced.

## Ignoring Text Inside Insert Revisions

You can configure Aspose.Words to ignore text inside insert revisions during find and replace operations.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

This allows you to exclude text that has been marked as inserted in tracked changes from being replaced.

## Replacing Text with HTML

You can use Aspose.Words for Java to replace text with HTML content.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

In this example, we use a custom `ReplaceWithHtmlEvaluator` to replace text with HTML content.

## Replacing Text in Headers and Footers

You can find and replace text within headers and footers of your Word document.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

This allows you to perform text replacements specifically in headers and footers.

## Showing Changes for Header and Footer Orders

You can use Aspose.Words to show changes for header and footer orders in your document.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

This allows you to visualize changes related to header and footer orders in your document.

## Replacing Text with Fields

You can replace text with fields using Aspose.Words for Java.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

In this example, we replace text with fields and specify the field type (e.g., `FieldType.FIELD_MERGE_FIELD`).

## Replacing with an Evaluator

You can use a custom evaluator to determine the replacement text dynamically.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

In this example, we use a custom evaluator (`MyReplaceEvaluator`) to replace text.

## Replacing with Regex

Aspose.Words for Java allows you to replace text using regular expressions.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

In this example, we use a regular expression pattern to find and replace text within the document.

## Recognizing and Substitutions Within Replacement Patterns

You can recognize and make substitutions within replacement patterns using Aspose.Words for Java.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

This allows you to perform substitutions within the replacement patterns for more advanced replacements.

## Replacing with a String

You can replace text with a simple string using Aspose.Words for Java.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

In this example, we replace "text-to-replace" with "new-string" within the document.

## Using Legacy Order

You can use legacy order when performing find and replace operations.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

This allows you to use legacy order for find and replace operations.

## Replacing Text in a Table

You can find and replace text within tables in your Word document.

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

This allows you to perform text replacements specifically within tables.

## Conclusion

Aspose.Words for Java provides comprehensive capabilities for finding and replacing text within Word documents. Whether you need to perform simple text replacements or more advanced operations using regular expressions, field manipulations, or custom evaluators, Aspose.Words for Java has you covered. Make sure to explore the extensive documentation and examples provided by Aspose to harness the full potential of this powerful Java library.

## FAQ's

### How do I download Aspose.Words for Java?

You can download Aspose.Words for Java from the website by visiting [this link](https://releases.aspose.com/words/java/).

### Can I use regular expressions for text replacement?

Yes, you can use regular expressions for text replacement in Aspose.Words for Java. This allows you to perform more advanced and flexible find and replace operations.

### How can I ignore text inside fields during replacement?

To ignore text inside fields during replacement, you can set the `IgnoreFields` property of the `FindReplaceOptions` to `true`. This ensures that text within fields, such as merge fields, is excluded from the replacement.

### Can I replace text inside headers and footers?

Yes, you can replace text inside headers and footers of your Word document. Simply access the appropriate header or footer and use the `replace` method with the desired `FindReplaceOptions`.

### What is the UseLegacyOrder option for?

The `UseLegacyOrder` option in `FindReplaceOptions` allows you to use legacy order when performing find and replace operations. This can be useful in certain scenarios where legacy order behavior is desired.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
