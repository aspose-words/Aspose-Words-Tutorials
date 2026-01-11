---
date: 2026-01-11
description: 學習如何使用 Aspose.Words for Java 顯示/隱藏書籤以及建立書籤，以實現高效的文件導覽與操作。
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 顯示與隱藏書籤
url: /zh-hant/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中顯示/隱藏書籤

## 在 Aspose.Words for Java 中使用書籤的簡介

書籤是 Aspose.Words for Java 中的強大功能，可讓您 **create bookmark java**、導覽至特定內容，甚至在需要產生不同文件版本時 **show hide bookmarks**。在本分步指南中，我們將逐步說明如何建立、存取、更新、複製以及切換書籤的可見性，讓您全面掌控文件操作。

## 快速問答
- **What is the primary purpose of bookmarks?** 標記並稍後檢索文件的特定部分。  
- **Can I hide bookmark markers in the final output?** 是的——使用 show/hide API 來切換其可見性。  
- **How do I create a bookmark inside a table cell?** 在光標位於儲存格內時，使用 `DocumentBuilder` 開始與結束書籤。  
- **Is it possible to copy bookmarked text to another document?** 當然可以——使用 `NodeImporter` 以保留格式。  
- **What version of Aspose.Words is required?** 任何近期版本；此程式碼可在最新 2026 版中運作。

## 什麼是「show hide bookmarks」？

**show hide bookmarks** 功能允許您以程式方式在已儲存的文件中顯示或隱藏書籤分隔符。當您希望為最終使用者產生乾淨的輸出，同時仍保留書籤資料以供內部處理時，這非常有用。

## 為何在 Java 文件自動化中使用書籤？

- **Efficient navigation** – 直接跳至特定章節，無需掃描整個檔案。  
- **Dynamic content generation** – 插入、取代或移除與書籤相關的文字。  
- **Conditional visibility** – 根據使用者偏好或輸出格式顯示或隱藏書籤標記。  
- **Reusability** – 在文件之間複製書籤片段，同時保留樣式。

## 先決條件
- Java Development Kit (JDK) 8 或更高版本。  
- 已將 Aspose.Words for Java 函式庫加入您的專案（Maven/Gradle 或 JAR）。  
- 熟悉 `Document` 與 `DocumentBuilder` 類別的基本用法。

## 分步指南

### 步驟 1：建立書籤 (create bookmark java)

要新增書籤，先啟動書籤、寫入內容，最後結束書籤。本範例建立一個名為 **My Bookmark** 的簡單書籤。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### 步驟 2：存取書籤 (access bookmarks java)

書籤可透過零基索引或名稱取得。以下程式碼示範兩種方式。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### 步驟 3：更新書籤資料 (update bookmark text)

您可以重新命名書籤或取代其文字內容。當底層文件變更時此功能相當便利。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### 步驟 4：處理書籤文字 (copy bookmarked text)

使用 `NodeImporter` 複製書籤片段至另一文件，同時保留原始格式，操作相當簡單。

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### 步驟 5：顯示與隱藏書籤 (show hide bookmarks)

以下程式碼示範如何在儲存的檔案中隱藏書籤標記。傳入 `false` 以隱藏，傳入 `true` 以顯示。

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### 步驟 6：解除列書籤交錯 (bookmark table cell)

當書籤跨越表格列時，可能會交錯。以下實用方法可解除交錯，並允許您依書籤刪除特定列。

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## 常見問題與解決方案

| Issue | Solution |
|-------|----------|
| **Bookmark not found** | 確認書籤名稱完全相符（區分大小寫），且文件在建立後已儲存。 |
| **Copied text loses formatting** | 如 Step 4 所示，使用 `ImportFormatMode.KEEP_SOURCE_FORMATTING` 搭配 `NodeImporter`。 |
| **Show/hide does not affect output** | 確保在儲存文件之前呼叫 `showHideBookmarkedContent` **before**。 |
| **Bookmark inside a table cell is ignored** | 在建構器光標位於目標儲存格內時，呼叫開始/結束方法。 |

## 常見問題

**Q: 如何在表格儲存格中建立書籤？**  
A: 使用 `DocumentBuilder` 將光標移至目標儲存格，然後在儲存格內容前後呼叫 `startBookmark` 與 `endBookmark`。

**Q: 能否將書籤複製到其他文件？**  
A: 可以——使用 `NodeImporter` 類別（參見步驟 4）匯入書籤節點，同時保留其原始格式。

**Q: 如何依書籤刪除列？**  
A: 首先定位包含該書籤的列，然後對該列節點呼叫 `remove`（如步驟 6 所示）。

**Q: 書籤的常見使用情境有哪些？**  
A: 產生目錄、抽取特定章節以供報告，以及根據使用者選擇自動組合文件等。

**Q: 在哪裡可以取得 Aspose.Words for Java 的更多資訊？**  
A: 欲取得詳細文件與下載，請造訪 [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/)。

---

**最後更新：** 2026-01-11  
**測試環境：** Aspose.Words for Java 24.11 (2026)  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}