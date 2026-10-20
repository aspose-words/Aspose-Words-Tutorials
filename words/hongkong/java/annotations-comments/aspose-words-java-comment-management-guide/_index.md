---
date: '2025-11-25'
description: 學習如何使用 Aspose.Words for Java 新增批註，並了解如何刪除批註回覆。輕鬆管理、列印、移除及追蹤批註時間戳記。
keywords:
- Aspose.Words Java
- comment management in Word documents
- managing comments with Aspose.Words
title: 如何使用 Java 在 Aspose.Words 中添加批註
url: /zh-hant/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words 在 Java 中新增評論

在 Word 文件中以程式方式管理評論有時彷彿在迷宮中穿梭，尤其當你需要以乾淨、可重複的方式 **how to add comment java**。在本教學中，我們將逐步說明如何新增評論、回覆、列印、移除、標記為完成，甚至提取 UTC 時間戳——全部使用 Aspose.Words for Java。最後，你也會了解 **how to delete comment replies**，以便在需要時整理文件。

## 快速解答
- **使用的函式庫是什麼？** Aspose.Words for Java  
- **主要任務？** How to add comment java in a Word document  
- **如何刪除評論回覆？** Use the `removeReply` or `removeAllReplies` methods  
- **先決條件？** JDK 8+, Maven or Gradle, and an Aspose.Words license (trial works too)  
- **典型實作時間？** ~15‑20 minutes for a basic comment workflow  

## 什麼是 “how to add comment java”？
在 Java 中新增評論是指建立一個 `Comment` 節點，將其附加到段落，並可選擇性地加入回覆。這是協同文件審閱、自動回饋循環以及內容批准流程的基礎構件。

## 為何使用 Aspose.Words 進行評論管理？
- **完整控制** over comment metadata (author, initials, date)  
- **跨格式支援** – works with DOC, DOCX, ODT, PDF, etc.  
- **無需 Microsoft Office 依賴** – runs on any server‑side JVM  
- **豐富 API** for marking comments as done, deleting replies, and retrieving UTC timestamps  

## 先決條件
- Java Development Kit (JDK) 8 或更新版本  
- Maven 或 Gradle 建置工具  
- IDE，例如 IntelliJ IDEA 或 Eclipse  
- Aspose.Words for Java 程式庫（請參考以下相依性片段）

### 新增 Aspose.Words 相依性
**Maven：**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle：**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 取得授權
Aspose.Words 為商業產品。您可以先使用免費 30 天試用版，或申請臨時授權以進行評估。詳情請造訪 [purchase page](https://purchase.aspose.com/buy)。

## 如何使用 Java 新增評論 – 步驟指南

### 功能 1：新增評論並回覆
**概述** – 示範 **how to add comment java** 的核心模式並附加回覆。

#### 實作步驟
**步驟 1：** 初始化 Document 物件  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```

**步驟 2：** 建立並新增 Comment  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**步驟 3：** 為 Comment 新增回覆  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

### 功能 2：列印所有評論
**概述** – 取得所有頂層評論及其回覆以供檢閱。

#### 實作步驟
**步驟 1：** 載入 Document  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```

**步驟 2：** 取得並列印評論  
```java
NodeCollection<Comment> comments = doc.getChildNodes(NodeType.COMMENT, true);
for (Comment comment : (Iterable<Comment>) comments) {
    if (comment.getAncestor() == null) {
        System.out.println("Top-level comment:");
        System.out.println("\t" + comment.getText().trim() + ", by " + comment.getAuthor());
        for (Comment reply : comment.getReplies()) {
            System.out.println("\t" + reply.getText().trim() + ", by " + reply.getAuthor());
        }
    }
}
```

### 功能 3：在 Java 中刪除評論回覆
**概述** – 示範 **how to delete comment replies**，以保持文件整潔。

#### 實作步驟
**步驟 1：** 初始化並新增帶回覆的評論  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```

**步驟 2：** 移除回覆  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

### 功能 4：將評論標記為完成
**概述** – 將評論標記為已解決，對於追蹤問題狀態很有幫助。

#### 實作步驟
**步驟 1：** 建立 Document 並新增 Comment  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```

**步驟 2：** 將 Comment 標記為完成  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

### 功能 5：從評論取得 UTC 日期與時間
**概述** – 取得評論新增時的精確 UTC 時間戳，適用於稽核日誌。

#### 實作步驟
**步驟 1：** 建立帶有時間戳的 Comment 的 Document  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**步驟 2：** 儲存並取得 UTC 日期  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## 實務應用
- **協同編輯：** 團隊可直接在產生的報告中新增與回覆。  
- **文件審閱工作流程：** 將評論標記為完成，以表示問題已解決。  
- **稽核與合規：** UTC 時間戳提供了回饋輸入時間的不可變紀錄。  

## 效能考量
- 對於非常大的檔案，請批次處理評論以避免記憶體激增。  
- 在執行多項操作時，重複使用同一個 `Document` 實例。  
- 保持 Aspose.Words 為最新版本，以獲得新版本中的效能最佳化。  

## 結論
現在您已了解如何使用 Aspose.Words **how to add comment java**，以及如何 **how to delete comment replies**，並能管理完整的評論生命週期——從建立、解決到時間戳提取。將這些程式碼片段整合至您現有的 Java 服務中，以自動化審閱流程並提升文件治理。

**下一步**
- 嘗試依作者或日期篩選評論。  
- 將評論管理與文件轉換（例如 DOCX → PDF）結合，以建立自動化報告管線。  

## 常見問題

**Q: 我可以在受密碼保護的文件上使用這些 API 嗎？**  
A: 可以。使用包含密碼的適當 `LoadOptions` 來載入文件。

**Q: Aspose.Words 需要安裝 Microsoft Office 嗎？**  
A: 不需要。此函式庫完全獨立，能在任何支援 Java 的平台上運行。

**Q: 若嘗試移除不存在的回覆會發生什麼？**  
A: `removeReply` 方法會拋出 `IllegalArgumentException`。請先檢查集合大小。

**Q: 文件能容納的評論數量有上限嗎？**  
A: 實際上沒有，但數量過大可能影響效能；建議分批處理。

**Q: 如何將評論匯出為 CSV 檔案？**  
A: 迭代評論集合，提取屬性（作者、文字、日期），並使用標準 Java I/O 寫入檔案。

---

**最後更新：** 2025-11-25  
**測試環境：** Aspose.Words for Java 25.3  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}