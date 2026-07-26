---
date: '2026-07-26'
description: 了解如何使用 Aspose.Words for Java 管理 Word 文件中的批註。透過清晰的程式碼範例，學會新增、列印、刪除及將批註標記為已完成。
keywords:
- Aspose.Words Java
- comment management in Word documents
- managing comments with Aspose.Words
lastmod: '2026-07-26'
og_description: 了解如何使用 Aspose.Words for Java 管理 Word 文件中的批註。透過清晰的程式碼範例，學會新增、列印、刪除及將批註標記為已完成。
og_image_alt: 'Developer guide: Managing Word comments with Aspose.Words Java'
og_title: 如何使用 Aspose.Words for Java 管理 Word 文件中的批註
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Learn how to manage comments in Word documents using Aspose.Words for
    Java. Add, print, delete, and mark comments as done with clear code examples.
  headline: How to Manage Comments in Word Docs with Aspose.Words Java
  type: TechArticle
- questions:
  - answer: A free trial works for evaluation, but a valid license is required for
      production to remove evaluation limits.
    question: Can I use Aspose.Words without a license in production?
  - answer: Yes—load the document with a `LoadOptions` object that includes the password.
    question: Does Aspose.Words support password‑protected Word files?
  - answer: The library can manage tens of thousands of comments; performance depends
      on available memory and document size.
    question: What is the maximum number of comments Aspose.Words can handle?
  - answer: By default, Aspose.Words records comment dates in UTC, ensuring consistent
      cross‑time‑zone reporting.
    question: Are comment timestamps always stored in UTC?
  - answer: Call `document.getComments().remove(comment)`; this removes the comment
      and all its replies in one operation.
    question: How do I delete an entire comment thread?
  type: FAQPage
tags:
- how to manage comments
- add comment java
- print word comments
- delete word comment
- java document comments
title: 如何使用 Aspose.Words for Java 管理 Word 文件中的批註
url: /zh-hant/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/products-backtop-button >}}

# 如何使用 Aspose.Words Java 管理 Word 文件中的批註

以程式方式管理批註一直是依賴 Word 進行協作的團隊的痛點。在本指南中，您將學習如何使用 Aspose.Words for Java 高效地 **管理批註**——新增、列印、刪除以及標記為已解決，全部不需開啟 Word 本身。完成後，您將擁有一套完整的工具箱，以自動化文件審閱流程。

## 快速答案
- **第一步是什麼？** 將您的 Word 檔案載入 `Document` 物件。  
- **我可以為批註新增回覆嗎？** 可以——使用 `Comment.getReplies().add()` 方法。  
- **如何列出所有批註？** 迭代 `Document.getComments()`，並列印每個批註的文字。  
- **是否可以將批註標記為完成？** 設定 `Comment.setDone(true)` 旗標。  
- **如何取得批註的時間戳記？** 呼叫 `Comment.getDateTime()`，它會回傳 UTC 的 `DateTime` 物件。

## 什麼是 Word 文件中的批註管理？
批註管理是指在 Word 檔案內以程式方式建立、取得、修改與移除批註物件。它可實現自動化審閱工作流程、稽核追蹤產生，並與問題追蹤系統整合，免除在 Microsoft Word 中手動編輯的需求。

## 為何使用 Aspose.Words for Java 來管理批註？
Aspose.Words 支援 **35+ 種檔案格式**，且可處理最多 **2,000 頁** 的文件，同時將記憶體使用量控制在 150 MB 以下。其純 Java 引擎可在任何平台上運行，無需 Microsoft Word，為您提供確定性的效能以及對批註中作者、時間戳記與解決狀態等中繼資料的完整控制。

## 前置條件
- 已安裝 Java Development Kit (JDK) 17 或更新版本。  
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE。  
- 用於相依管理的 Maven 或 Gradle。  

### 設定 Aspose.Words for Java
Aspose.Words 以單一 JAR 檔提供。將符合您建置系統的相依性加入。

**Maven:**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```  

**Gradle:**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```  

#### 取得授權
Aspose.Words 為商業產品，但您可以先使用免費試用版或臨時授權以取得完整功能。請前往 [purchase page](https://purchase.aspose.com/buy) 了解授權方案。

## 如何新增帶回覆的批註？
Document 代表載入記憶體中的 Word 檔案。  
Comment 是儲存單一批註資料的物件。

**直接回答（40‑70 字）：**  
建立 `Document` 實例，呼叫 `document.getComments().add(author, initials, text, date)` 以新增頂層批註，然後使用 `comment.getReplies().add(replyAuthor, replyInitials, replyText, replyDate)` 來附加回覆。API 會自動將回覆連結至其父批註，並在文件儲存時同時保留兩者。

### 步驟 1：初始化 Document 物件
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

### 步驟 2：建立並新增批註
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

### 步驟 3：為批註新增回覆
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## 如何列印所有批註及其回覆？
Document 提供對 Word 檔案中完整批註集合的存取。

**直接回答（40‑70 字）：**  
迭代 `document.getComments()`；對每個批註列印其作者、文字與時間戳記。接著遍歷 `comment.getReplies()`，輸出每則回覆的詳細資訊。此巢狀遍歷可在不載入其他文件部份的情況下，完整呈現討論層級。

### 步驟 1：載入 Document
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

### 步驟 2：取得並列印批註
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

## 如何移除批註回覆？
Comment.getReplies() 會回傳可變動的回覆物件集合。

**直接回答（40‑70 字）：**  
找到目標批註，對特定回覆呼叫 `comment.getReplies().remove(reply)`，或使用 `comment.getReplies().clear()` 以清除所有回覆。移除後儲存文件，批註層級將相應更新。

### 步驟 1：初始化並新增帶回覆的批註
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

### 步驟 2：移除回覆
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

## 如何將批註標記為完成？
Comment 代表單一批註節點，並包含「完成」旗標。

**直接回答（40‑70 字）：**  
在目標批註物件上設定 `Comment.setDone(true)` 屬性。儲存後，該批註在 Word 中會顯示「Done」勾選，表示問題已解決。之後可透過 `comment.isDone()` 來篩選已解決與未解決的批註。

### 步驟 1：建立 Document 並新增批註
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

### 步驟 2：將批註標記為完成
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

## 如何從批註取得 UTC 日期與時間？
Comment 將其建立日期儲存為 UTC 時間戳記。

**直接回答（40‑70 字）：**  
建立批註時，將 UTC 的 `java.util.Date`（或 `java.time.OffsetDateTime`）傳入建構子。之後使用 `comment.getDateTime()` 取得，該方法回傳儲存的 UTC 時間戳記。此值可格式化或存入資料庫，以進行精確的變更追蹤。

### 步驟 1：建立帶時間戳記的 Document 批註
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

### 步驟 2：儲存並取得 UTC 日期
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 實務應用
了解並運用這些批註管理功能，可大幅提升工作流程：

- **協同編輯：** 團隊可自動插入審閱註解與回覆，減少手動工作。  
- **文件審閱自動化：** 產生所有批註的摘要報告，以供合規稽核使用。  
- **回饋管理：** 將批註時間戳記儲存於集中式資料庫，以追蹤回應時間。

## 效能考量
處理大型合約或手冊時，請留意以下建議：

- 以批次方式處理批註，而非一次載入整個批註樹至記憶體。  
- 重複使用單一 `Document` 實例執行多項操作，以減少 GC 壓力。  
- 升級至最新的 Aspose.Words 版本，以獲得內部記憶體最佳化修補程式的效益。

## 結論
您現在已了解如何使用 Aspose.Words for Java **管理 Word 文件中的批註**——從新增與回覆、列印、刪除、標記為完成，到擷取 UTC 時間戳記。將這些模式套用於構建穩健的文件審閱流程、整合內容管理系統，或開發自訂稽核工具。

**下一步：**  
- 嘗試條件式批註篩選（例如，只顯示未解決的批註）。  
- 將批註資料與外部問題追蹤 API 結合，實現端對端工作流程自動化。

## 常見問題

**Q: 我可以在生產環境中未授權使用 Aspose.Words 嗎？**  
A: 免費試用版可用於評估，但在生產環境中必須擁有有效授權才能移除評估限制。

**Q: Aspose.Words 支援受密碼保護的 Word 檔案嗎？**  
A: 支援——使用包含密碼的 `LoadOptions` 物件載入文件。

**Q: Aspose.Words 能處理的批註最大數量是多少？**  
A: 此函式庫可管理數萬筆批註；效能取決於可用記憶體與文件大小。

**Q: 批註的時間戳記是否始終以 UTC 儲存？**  
A: 預設情況下，Aspose.Words 會以 UTC 記錄批註日期，確保跨時區報告的一致性。

**Q: 如何刪除整個批註串？**  
A: 呼叫 `document.getComments().remove(comment)`；此操作會一次移除該批註及其所有回覆。

---

**最後更新：** 2026-07-26  
**測試版本：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

## 相關教學

- [精通 Aspose.Words for Java：如何在 Word 文件中插入與管理書籤](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [使用 Aspose.Words Java 追蹤 Word 文件變更：文件修訂完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [使用 Aspose.Words Java 管理 Word 超連結：完整指南](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-wrap-class >}}