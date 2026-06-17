---
date: '2026-06-17'
description: 了解如何使用 Aspose.Words 在 Java 中新增註解，並在有效管理回覆、刪除與時間戳記的同時，高效列印 Word 文件的註解。
keywords:
- how to add comment java
- print word document comments
- Aspose.Words comment management
- Java Word API
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Learn how to add comment java with Aspose.Words, and print word document
    comments efficiently while managing replies, removal, and timestamps.
  headline: 'How to Add Comment Java: Aspose.Words Comment Management Guide'
  type: TechArticle
- description: Learn how to add comment java with Aspose.Words, and print word document
    comments efficiently while managing replies, removal, and timestamps.
  name: 'How to Add Comment Java: Aspose.Words Comment Management Guide'
  steps:
  - name: Initialize the Document Object
    text: The `Document` class is Aspose.Words' top‑level object that represents a
      single Word file in memory.
  - name: Create and Add a Comment
    text: '`Comment` represents a single comment node attached to a run of text.'
  - name: Add a Reply to the Comment
    text: '`Comment.getReplies()` returns a collection that you can populate with
      additional `Comment` objects.'
  - name: Load the Document
    text: The `Document` class loads the file and parses its comment tree.
  - name: Retrieve and Print Comments
    text: '`CommentCollection` provides indexed access to each top‑level comment.'
  - name: Initialize and Add Comments with Replies
    text: '`DocumentBuilder` helps you insert comments and replies in a single pass.'
  - name: Remove Replies
    text: '`Comment.getReplies().clear()` removes every reply attached to the comment.'
  - name: Create a Document and Add a Comment
    text: '`DocumentBuilder` inserts the initial comment that we will later resolve.'
  - name: Mark the Comment as Done
    text: '`comment.setDone(true)` updates the comment’s status to resolved.'
  - name: Create a Document with a Timestamped Comment
    text: When you add a comment, Aspose.Words automatically records the UTC timestamp.
  type: HowTo
- questions:
  - answer: Aspose.Words for Java is a fully managed API that lets you create, edit,
      convert, and render Word documents without Microsoft Word installed.
    question: What is Aspose.Words for Java?
  - answer: Add the Maven or Gradle dependency shown in the “Setting Up Aspose.Words
      for Java” section, then refresh your project.
    question: How do I install Aspose.Words for my project?
  - answer: Yes, a temporary trial license works for evaluation, but it adds evaluation
      watermarks and limits some features.
    question: Can I use Aspose.Words without a license?
  - answer: Forgetting to call `document.save()` after modifications, or attempting
      to access a comment that has been removed, can cause `NullPointerException`s.
    question: What are common pitfalls when managing comments?
  - answer: Use the `Revision` API together with comment timestamps to build a change‑log
      that spans many files.
    question: How do I track changes across multiple documents?
  type: FAQPage
title: 如何在 Java 中新增註解：Aspose.Words 註解管理指南
url: /zh-hant/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Java 中新增評論：Aspose.Words 評論管理指南

## 介紹
在 Word 文件中以程式方式管理評論可能具有挑戰性，尤其是當您需要在協作環境中 **how to add comment java** 時。本教學將一步步示範如何新增、列印、移除以及標記評論為完成，並取得 UTC 時間戳記以進行精確追蹤。完成後，您將能熟練處理 Aspose.Words for Java 中所有常見的評論相關情境。

**您將學習：**
- 輕鬆新增評論與回覆
- 列印所有頂層評論及其回覆
- 移除評論回覆或將評論標記為完成
- 取得評論的 UTC 日期與時間以進行精確追蹤

準備好提升文件自動化工作流程了嗎？讓我們先確認前置條件。

## 快速回答
- **如何在 Java 中新增評論？** 使用 `DocumentBuilder` 插入 `Comment` 物件，然後呼叫 `Comment.getReplies().add(...)` 以新增回覆。  
- **我可以列印所有評論嗎？** 迭代 `doc.getComments()` 並輸出每則評論的文字與作者。  
- **有沒有方法將評論標記為已解決？** 設定 `Comment.setDone(true)` 以將其標記為完成。  
- **如何取得評論的時間戳記？** 取用 `Comment.getDateTime()`，它會回傳 UTC 的 `java.util.Date`。  
- **我需要授權才能使用這些功能嗎？** 是的，有效的 Aspose.Words 授權可解鎖完整的評論管理功能。

## 什麼是 how to add comment java？
**how to add comment java** 指的是使用 Aspose.Words API for Java 以程式方式在 Word 文件中插入評論的過程。此功能可在無需手動編輯的情況下實現自動化審閱工作流程。透過 API，您可以在程式碼中完全建立、回覆與管理評論，從而與文件處理管線及版本控制系統無縫整合。

## 為何使用 Aspose.Words 進行評論管理？
Aspose.Words 支援 **35+** 種輸入與輸出格式——包括 DOCX、PDF、HTML 與 ODT，且能在一般伺服器硬體上於 **3 秒** 內處理 **500 頁** 的文件。其評論 API 完全在記憶體中運作，無需安裝 Microsoft Word。

## 前置條件
- 已安裝 Java Development Kit (JDK) 8 或更新版本
- 具備 Java 語法與物件導向概念的基本認識
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE
- 取得 Aspose.Words for Java 授權（試用版可用於評估）

### 設定 Aspose.Words for Java
Aspose.Words 透過 Maven Central 與 NuGet 發佈。請加入符合您建置系統的相依性。

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

#### 授權取得
Aspose.Words 為商業函式庫，但您可以先使用免費試用版或申請臨時授權以取得完整功能。前往[購買頁面](https://purchase.aspose.com/buy)了解授權方案。

## 實作指南
本節將針對每項評論管理功能提供清晰、可執行的步驟說明。

### 如何新增評論 java？
`Document` 類別代表一個載入記憶體的 Word 檔案。  
`DocumentBuilder` 類別提供在文件內容中導覽與編輯的方法。  
`Comment` 類別代表附加於 Word 文件文字範圍的評論節點。

**直接答案：**  
建立 `Document` 物件，使用 `DocumentBuilder` 定位游標，呼叫 `builder.insertComment("Author", "Initial comment")`，然後使用 `comment.getReplies().add(new Comment("Reply author", "Reply text"))` 新增回覆。這樣即可在幾行程式碼內建立完整的評論串。

#### 步驟 1：初始化 Document 物件
`Document` 類別是 Aspose.Words 的頂層物件，代表記憶體中的單一 Word 檔案。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```

#### 步驟 2：建立並新增評論
`Comment` 代表附加於文字串的單一評論節點。  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

#### 步驟 3：為評論新增回覆
`Comment.getReplies()` 會回傳一個集合，您可以在其中加入其他 `Comment` 物件作為回覆。  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

### 如何列印 Word 文件評論？
`Document` 類別保存 Word 檔案的內容與結構，包括其評論。  
`CommentCollection` 類別提供對文件中每個頂層評論的索引存取。

**直接答案：**  
迭代 `doc.getComments()`，輸出每則評論的作者、文字與時間戳記，然後遍歷 `comment.getReplies()` 以顯示回覆細節。如此即可取得文件中所有回饋的完整可讀快照。

#### 步驟 1：載入文件
`Document` 類別載入檔案並解析其評論樹。  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```

#### 步驟 2：取得並列印評論
`CommentCollection` 提供對每個頂層評論的索引存取。  
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

### 如何移除評論回覆？
`Comment` 類別代表評論及其相關回覆。

**直接答案：**  
呼叫 `comment.getReplies().clear()` 以刪除所有回覆，或使用 `comment.getReplies().removeAt(index)` 針對單一回覆。修改後，儲存文件以持續變更。

#### 步驟 1：初始化並新增含回覆的評論
`DocumentBuilder` 可協助您一次性插入評論與回覆。  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```

#### 步驟 2：移除回覆
`Comment.getReplies().clear()` 會移除附加於該評論的所有回覆。  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

### 如何將評論標記為完成？
`Comment` 類別包含 `setDone` 方法，可將評論標記為已解決。

**直接答案：**  
在目標 `Comment` 物件上呼叫 `comment.setDone(true)`。此旗標會儲存在 Word 檔案中，並在 Microsoft Word 中顯示為「完成」勾選標記。

#### 步驟 1：建立文件並新增評論
`DocumentBuilder` 插入我們稍後將解決的初始評論。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```

#### 步驟 2：將評論標記為完成
`comment.setDone(true)` 會將評論狀態更新為已解決。  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

### 如何從評論取得 UTC 日期與時間？
`Comment.getDateTime()` 方法回傳一個 `java.util.Date` 物件，代表評論在 UTC 時間的建立時間。

**直接答案：**  
取用 `comment.getDateTime()`，它會回傳 UTC 時間的 `java.util.Date`。您可以使用 `SimpleDateFormat` 並設定 `UTC` 時區來格式化顯示或記錄。

#### 步驟 1：建立帶時間戳記的評論文件
當您新增評論時，Aspose.Words 會自動記錄 UTC 時間戳記。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

#### 步驟 2：儲存並取得 UTC 日期
`comment.getDateTime()` 提供評論建立的確切時間。  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```

## 實務應用
了解並運用這些功能可在多種情境下顯著提升文件管理效能：

- **協同編輯：** 團隊可直接在文件內留下結構化回饋，您的自動化程式可程式化地彙總或解決評論。  
- **文件審閱管線：** 自動化 QA 流程可在發佈前標記未解決的評論。  
- **稽核追蹤：** UTC 時間戳記提供可靠的稽核日誌，適用於受規範限制的產業。

這些功能可順利整合至內容管理系統、CI/CD 管線或自訂審閱工具。

## 效能考量
處理含大量評論的巨型 Word 檔案（數百頁）時，請留意以下建議：

- 分批處理評論，以避免一次載入整個評論樹至記憶體。  
- 若需在保留原始檔的同時操作副本，請使用 `Document.clone()`。  
- 升級至最新的 Aspose.Words 版本，以獲得記憶體最佳化與多執行緒處理的提升。

## 結論
您現在已擁有完整的 **how to add comment java** 工具組，能以 Aspose.Words 管理完整的評論生命週期。精通這些 API 後，您可自動化審閱流程、強化合規性，並打造更智慧的文件處理解決方案。

## 後續步驟
- 嘗試依作者或日期篩選評論。  
- 將評論管理與 Aspose.Words 其他功能（如郵件合併或文件轉換）結合。  
- 探索 Aspose.Words API 參考文件，以了解自訂評論樣式等進階情境。

## 常見問題

**問：什麼是 Aspose.Words for Java？**  
A: Aspose.Words for Java 是一套完整管理的 API，讓您在未安裝 Microsoft Word 的情況下建立、編輯、轉換與呈現 Word 文件。

**問：如何在我的專案中安裝 Aspose.Words？**  
A: 在「設定 Aspose.Words for Java」章節中加入所示的 Maven 或 Gradle 相依性，然後重新整理您的專案。

**問：我可以在沒有授權的情況下使用 Aspose.Words 嗎？**  
A: 可以，臨時試用授權可用於評估，但會加入評估浮水印並限制部分功能。

**問：管理評論時常見的陷阱是什麼？**  
A: 在修改後忘記呼叫 `document.save()`，或嘗試存取已被移除的評論，都可能導致 `NullPointerException`。

**問：如何追蹤多個文件的變更？**  
A: 結合 `Revision` API 與評論時間戳記，即可建立跨多個檔案的變更日誌。

---

**最後更新：** 2026-06-17  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< blocks/products/products-backtop-button >}}

## 相關教學

- [使用 Aspose.Words Java 於 Word 中管理超連結：完整指南](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)
- [使用 Aspose.Words Java 追蹤 Word 文件變更：文件修訂完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [Aspose.Words Java：Word 文件處理完整指南](/words/java/document-operations/aspose-words-java-master-word-processing/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}