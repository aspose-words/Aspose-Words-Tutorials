---
title: Show Hide Bookmarks with Aspose.Words for Java
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
description: Learn how to show hide bookmarks and create bookmark java using Aspose.Words for Java for efficient document navigation and manipulation.
weight: 17
url: /java/document-manipulation/using-bookmarks/
date: 2026-01-11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Show Hide Bookmarks with Aspose.Words for Java

## Introduction to Using Bookmarks in Aspose.Words for Java

Bookmarks are a powerful feature in Aspose.Words for Java that lets you **create bookmark java**, navigate to specific content, and even **show hide bookmarks** when you need to generate different document versions. In this step‑by‑step guide we’ll walk through creating, accessing, updating, copying, and toggling the visibility of bookmarks, giving you full control over document manipulation.

## Quick Answers
- **What is the primary purpose of bookmarks?** To mark and later retrieve specific parts of a document.  
- **Can I hide bookmark markers in the final output?** Yes—use the show/hide API to toggle their visibility.  
- **How do I create a bookmark inside a table cell?** Start and end the bookmark with `DocumentBuilder` while the cursor is inside the cell.  
- **Is it possible to copy bookmarked text to another document?** Absolutely—use `NodeImporter` to preserve formatting.  
- **What version of Aspose.Words is required?** Any recent release; the code works with the latest 2026 build.

## What is “show hide bookmarks”?

The **show hide bookmarks** feature allows you to programmatically display or conceal bookmark delimiters in the saved document. This is useful when you want to generate clean output for end users while still retaining bookmark data for internal processing.

## Why use bookmarks in Java document automation?

- **Efficient navigation** – Jump directly to sections without scanning the whole file.  
- **Dynamic content generation** – Insert, replace, or remove text tied to a bookmark.  
- **Conditional visibility** – Show or hide bookmark markers based on user preferences or output format.  
- **Reusability** – Copy bookmarked fragments between documents while preserving styles.

## Prerequisites
- Java Development Kit (JDK) 8 or higher.  
- Aspose.Words for Java library added to your project (Maven/Gradle or JAR).  
- Basic familiarity with `Document` and `DocumentBuilder` classes.

## Step‑by‑Step Guide

### Step 1: Create a Bookmark (create bookmark java)

To add a bookmark, you start it, write the content, then end it. This example creates a simple bookmark named **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Step 2: Access Bookmarks (access bookmarks java)

Bookmarks can be retrieved either by their zero‑based index or by name. The code below demonstrates both approaches.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Step 3: Update Bookmark Data (update bookmark text)

You may rename a bookmark or replace its text content. This is handy when the underlying document changes.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Step 4: Work with Bookmarked Text (copy bookmarked text)

Copying a bookmarked fragment to another document while keeping the original formatting is straightforward with `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Step 5: Show and Hide Bookmarks (show hide bookmarks)

The following snippet demonstrates how to hide a bookmark’s markers in the saved file. Pass `false` to hide, `true` to show.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Step 6: Untangle Row Bookmarks (bookmark table cell)

When bookmarks span table rows, they can become tangled. The utility methods below untangle them and allow you to delete a specific row by its bookmark.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Common Issues and Solutions

| Issue | Solution |
|-------|----------|
| **Bookmark not found** | Verify the bookmark name matches exactly (case‑sensitive) and that the document was saved after creation. |
| **Copied text loses formatting** | Use `ImportFormatMode.KEEP_SOURCE_FORMATTING` with `NodeImporter` as shown in Step 4. |
| **Show/hide does not affect output** | Ensure you call `showHideBookmarkedContent` **before** saving the document. |
| **Bookmark inside a table cell is ignored** | Place the start/end calls while the builder cursor is inside the target cell. |

## Frequently Asked Questions

**Q: How do I create a bookmark in a table cell?**  
A: Use `DocumentBuilder` to move the cursor into the desired cell, then call `startBookmark` and `endBookmark` around the cell content.

**Q: Can I copy a bookmark to another document?**  
A: Yes—use the `NodeImporter` class (see Step 4) to import the bookmarked node while preserving its original formatting.

**Q: How can I delete a row by its bookmark?**  
A: First locate the row that contains the bookmark, then call `remove` on the row node (as demonstrated in Step 6).

**Q: What are some common use cases for bookmarks?**  
A: Generating a table of contents, extracting specific sections for reporting, and automating document assembly based on user selections.

**Q: Where can I find more information about Aspose.Words for Java?**  
A: For detailed documentation and downloads, visit [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Last Updated:** 2026-01-11  
**Tested With:** Aspose.Words for Java 24.11 (2026)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}