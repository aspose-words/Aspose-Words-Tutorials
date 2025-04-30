---
title: Cloning and Combining Documents in Aspose.Words for Java
linktitle: Cloning and Combining Documents
second_title: Aspose.Words Java Document Processing API
description: Learn how to clone and combine documents in Aspose.Words for Java. Step-by-step guide with source code examples.
weight: 27
url: /java/document-manipulation/cloning-and-combining-documents/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cloning and Combining Documents in Aspose.Words for Java


## Introduction to Cloning and Combining Documents in Aspose.Words for Java

In this tutorial, we will explore how to clone and combine documents using Aspose.Words for Java. We'll cover various scenarios, including cloning a document, inserting documents at replace points, bookmarks, and during mail merge operations.

## Step 1: Cloning a Document

To clone a document in Aspose.Words for Java, you can use the `deepClone()` method. Here's a simple example:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

This code will create a deep clone of the original document and save it as a new file.

## Step 2: Inserting Documents at Replace Points

You can insert documents at specific replace points in another document. Here's how you can do it:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

In this example, we use a `FindReplaceOptions` object to specify a callback handler for the replacement. The `InsertDocumentAtReplaceHandler` class handles the insertion logic.

## Step 3: Inserting Documents at Bookmarks

To insert a document at a specific bookmark in another document, you can use the following code:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Here, we find the bookmark by name and use the `insertDocument` method to insert the content of the `subDoc` document at the bookmark location.

## Step 4: Inserting Documents During Mail Merge

You can insert documents during a mail merge operation in Aspose.Words for Java. Here's how:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

In this example, we set a field merging callback using the `InsertDocumentAtMailMergeHandler` class to handle the insertion of the document specified by the "Document_1" field.

## Conclusion

Cloning and combining documents in Aspose.Words for Java can be accomplished using various techniques. Whether you need to clone a document, insert content at replace points, bookmarks, or during mail merge, Aspose.Words provides powerful features to manipulate documents seamlessly.

## FAQ's

### How do I clone a document in Aspose.Words for Java?

You can clone a document in Aspose.Words for Java using the `deepClone()` method. Here's an example:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### How can I insert a document at a bookmark?

To insert a document at a bookmark in Aspose.Words for Java, you can find the bookmark by name and then use the `insertDocument` method to insert the content. Here's an example:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### How do I insert documents during mail merge in Aspose.Words for Java?

You can insert documents during mail merge in Aspose.Words for Java by setting a field merging callback and specifying the document to be inserted. Here's an example:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

In this example, the `InsertDocumentAtMailMergeHandler` class handles the insertion logic for the "DocumentField" during mail merge.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}
