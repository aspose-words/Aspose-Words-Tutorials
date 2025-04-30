---
"description": "学习如何在 Aspose.Words for Java 中克隆和合并文档。循序渐进的指南，包含源代码示例。"
"linktitle": "克隆和合并文档"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中克隆和合并文档"
"url": "/zh/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中克隆和合并文档


## Aspose.Words for Java 中克隆和合并文档的简介

在本教程中，我们将探索如何使用 Aspose.Words for Java 克隆和合并文档。我们将涵盖各种场景，包括克隆文档、在替换点插入文档、添加书签以及在邮件合并操作期间插入文档。

## 步骤 1：克隆文档

要在 Aspose.Words for Java 中克隆文档，您可以使用 `deepClone()` 方法。这里有一个简单的例子：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

此代码将创建原始文档的深度克隆并将其保存为新文件。

## 步骤 2：在替换点插入文档

您可以在文档中的特定替换点插入另一个文档。操作方法如下：

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

在这个例子中，我们使用 `FindReplaceOptions` 对象来指定替换的回调处理程序。 `InsertDocumentAtReplaceHandler` 类处理插入逻辑。

## 步骤 3：在书签处插入文档

要将一个文档插入另一个文档中的特定书签，可以使用以下代码：

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

在这里，我们按名称查找书签并使用 `insertDocument` 方法插入内容 `subDoc` 文档中的书签位置。

## 步骤4：在邮件合并期间插入文档

您可以在 Aspose.Words for Java 的邮件合并操作期间插入文档。操作方法如下：

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

在此示例中，我们使用 `InsertDocumentAtMailMergeHandler` 类来处理“Document_1”字段指定的文档的插入。

## 结论

在 Aspose.Words for Java 中，可以使用多种技术来克隆和合并文档。无论您需要克隆文档、在替换点、书签处插入内容，还是在邮件合并期间插入内容，Aspose.Words 都提供强大的功能，让您无缝地操作文档。

## 常见问题解答

### 如何在 Aspose.Words for Java 中克隆文档？

您可以使用 Aspose.Words for Java 克隆文档 `deepClone()` 方法。以下是一个例子：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### 如何在书签处插入文档？

要在 Aspose.Words for Java 中的书签处插入文档，您可以按名称找到书签，然后使用 `insertDocument` 方法插入内容。以下是示例：

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### 如何在 Aspose.Words for Java 邮件合并期间插入文档？

您可以在 Aspose.Words for Java 的邮件合并过程中插入文档，只需设置字段合并回调并指定要插入的文档即可。以下是示例：

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

在此示例中， `InsertDocumentAtMailMergeHandler` 该类处理邮件合并期间“DocumentField”的插入逻辑。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}