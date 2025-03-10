---
title: 在 Aspose.Words for Java 中複製和合併文檔
linktitle: 克隆和合併文檔
second_title: Aspose.Words Java 文件處理 API
description: 了解如何在 Aspose.Words for Java 中複製和組合文件。帶有原始程式碼範例的分步指南。
weight: 27
url: /zh-hant/java/document-manipulation/cloning-and-combining-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中複製和合併文檔


## Aspose.Words for Java 中複製和組合文件的簡介

在本教程中，我們將探索如何使用 Aspose.Words for Java 複製和組合文件。我們將介紹各種場景，包括複製文件、在替換點插入文件、書籤以及在郵件合併作業期間。

## 第 1 步：克隆文檔

要在 Aspose.Words for Java 中複製文檔，您可以使用`deepClone()`方法。這是一個簡單的例子：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

此程式碼將建立原始文件的深度複製並將其另存為新文件。

## 步驟 2：在替換點插入文檔

您可以在另一個文件中的特定替換點插入文件。您可以這樣做：

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

在這個例子中，我們使用一個`FindReplaceOptions`物件來指定用於替換的回呼處理程序。這`InsertDocumentAtReplaceHandler`類別處理插入邏輯。

## 步驟 3：在書籤處插入文檔

若要將文件插入到另一個文件中的特定書籤處，可以使用下列程式碼：

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

在這裡，我們按名稱查找書籤並使用`insertDocument`方法插入內容`subDoc`書籤位置處的文件。

## 步驟 4：在郵件合併期間插入文檔

您可以在 Aspose.Words for Java 中的郵件合併作業期間插入文件。方法如下：

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

在此範例中，我們使用以下命令設定欄位合併回調`InsertDocumentAtMailMergeHandler`類別來處理由「Document_1」欄位指定的文件的插入。

## 結論

可以使用多種技術來完成 Aspose.Words for Java 中的複製和組合文件。無論您需要複製文件、在替換點、書籤處插入內容，還是在郵件合併過程中，Aspose.Words 都提供了強大的功能來無縫操作文件。

## 常見問題解答

### 如何在 Aspose.Words for Java 中複製文件？

您可以使用 Aspose.Words for Java 複製文檔`deepClone()`方法。這是一個例子：

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### 如何在書籤處插入文件？

要在 Aspose.Words for Java 中的書籤處插入文檔，您可以按名稱找到書籤，然後使用`insertDocument`方法來插入內容。這是一個例子：

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### 如何在 Aspose.Words for Java 中的郵件合併過程中插入文件？

您可以透過設定欄位合併回呼並指定要插入的文檔，在 Aspose.Words for Java 中的郵件合併過程中插入文檔。這是一個例子：

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

在此範例中，`InsertDocumentAtMailMergeHandler`類別處理郵件合併期間「DocumentField」的插入邏輯。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
