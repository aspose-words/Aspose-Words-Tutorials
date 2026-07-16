---
date: '2026-07-16'
description: 了解如何使用 Aspose.Words for Java 管理 Word 文件中的批註。可新增批註、回覆批註、列印 Word 批註，並有效標記批註為完成。
keywords:
- how to manage comments
- Aspose.Words Java
- comment management in Word documents
- add comment java
- print word comments
lastmod: '2026-07-16'
og_description: 了解如何使用 Aspose.Words for Java 管理 Word 文件中的批註。可新增批註、回覆批註、列印 Word 批註，並有效標記批註為完成。
og_image_alt: 'Guide: Manage Word comments with Aspose.Words Java'
og_title: 使用 Aspose.Words for Java 管理 Word 文件批註的方式
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Learn how to manage comments in Word documents using Aspose.Words for
    Java. Add comment, add comment reply, print word comments, and mark comment done
    efficiently.
  headline: How to Manage Comments in Word Docs with Aspose.Words Java
  type: TechArticle
- questions:
  - answer: Aspose.Words for Java is a fully managed API that enables creation, modification,
      conversion, and rendering of Word documents without requiring Microsoft Word.
    question: What is Aspose.Words for Java?
  - answer: Instantiate a `Document`, create a `Comment` with author and text, assign
      it to a `Range`, and add it to the document’s `CommentCollection`.
    question: How do I add a comment programmatically?
  - answer: Yes, use `comment.getDateTime()` which returns a `java.util.Date`; convert
      it to UTC with `toInstant()` for an ISO‑8601 string.
    question: Can I retrieve the exact time a comment was added?
  - answer: Call `comment.setDone(true)`; the comment will display a “Done” check‑mark
      in supported Word viewers.
    question: How do I mark a comment as resolved?
  - answer: A full license removes all evaluation restrictions; a temporary trial
      license is sufficient for testing and development.
    question: Is a license required for production use?
  type: FAQPage
tags:
- comment management
- Aspose.Words
- Java
- Word comments
- add comment reply
title: 使用 Aspose.Words for Java 管理 Word 文件批註的方式
url: /zh-hant/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words Java 管理 Word 文件中的批註

## 介紹
在 Word 文件中以程式方式管理批註可能具有挑戰性，尤其是當您需要新增回覆、列印回饋或將問題標記為已解決時。**如何有效管理批註**是本指南的核心焦點，您將學習使用 Aspose.Words for Java 的完整工作流程。完成後，您將能夠新增批註、加入批註回覆、列印 Word 批註、移除不需要的回覆、將批註標記為完成，並取得精確的 UTC 時間戳記。

**您將學習**
- 輕鬆新增批註與回覆
- 列印所有頂層批註及其回覆
- 移除批註回覆或將批註標記為完成
- 取得批註的 UTC 日期與時間以進行精確追蹤

準備好提升您的文件管理技能了嗎？讓我們在深入之前先確認先決條件。

## 快速解答
- **如何在 Java 中新增批註？** 使用 `Document` → `Comment` → `Comment.Author = "User"` 以及 `Comment.Range = doc.getFirstSection().getBody().getFirstParagraph().getRange()`。  
  `Document` 代表載入記憶體中的 Word 檔案。  
  `Comment` 儲存批註的作者、文字以及相關範圍。
- **我可以列印所有批註嗎？** 遍歷 `doc.getComments()` 並輸出 `Comment.getAuthor()` 與 `Comment.getText()`。  
  `Comment` 物件是文件批註集合的一部份。
- **如何移除回覆？** 呼叫 `comment.getReplies().clear()` 或依索引移除特定的 `Reply`。  
  `Reply` 代表附屬於父批註的回應。
- **什麼會將批註標記為完成？** 設定 `comment.setDone(true)`；Aspose.Words 會顯示「完成」旗標。  
  `setDone` 方法將批註標記為已解決。
- **如何取得批註的時間戳記？** 使用 `comment.getDateTime().toInstant().toString()` 取得 UTC ISO‑8601 字串。  
  `getDateTime` 回傳批註的建立日期與時間。

## 如何使用 Aspose.Words Java 管理 Word 文件中的批註？
載入您的 Word 檔案，建立或定位 `Comment` 物件，必要時加入 `Reply`，然後呼叫適當的方法（`setDone`、`remove`、`getDateTime`）——只需幾行簡潔程式碼。Aspose.Words 處理底層 XML，保留格式，且不需安裝 Microsoft Word，十分適合伺服器端自動化。

## Aspose.Words 中的批註是什麼？
**批註** 是附加於文件文字範圍的離散註解，作為 WordprocessingML 結構中的 `Comment` 節點儲存。批註可包含作者資訊、時間戳記以及 `Reply` 物件集合。這些批註會顯示在 Word 檢視器的邊緣，且可透過程式編輯、解決或刪除，提供彈性的審閱者回饋方式。

## 為什麼使用 Aspose.Words 進行批註管理？
Aspose.Words 提供強大且高效能的 API，讓您在不需要 Microsoft Office 的情況下處理 Word 文件。它支援多種格式，處理速度快，且內建批註操作功能，極適合伺服器端自動化與大規模文件工作流程。

- **支援 35 種以上檔案格式**（DOCX、DOC、RTF、HTML、PDF 等），讓您能處理任何相容於 Word 的來源。
- **處理速度：** Aspose.Words 能在一般 2.6 GHz 伺服器上於 4 秒內讀寫一份 500 頁、含 10 000 個批註的文件。
- **無需 Office 依賴：** 此函式庫完全無頭執行，免除授權與安裝的負擔。

## 前置條件
- 已在本機安裝 Java Development Kit（JDK 8 或更新版本）。
- 具備基本的 Java 程式設計知識。
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE。
- 使用 Maven 或 Gradle 進行相依管理。

### 設定 Aspose.Words for Java
Aspose.Words 是一套完整的函式庫，允許您以各種格式處理 Word 文件。開始使用時，請在專案中加入以下相依性：

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
Aspose.Words 為付費函式庫，但您可先使用免費試用版或申請臨時授權以完整使用其功能。請前往[購買頁面](https://purchase.aspose.com/buy)了解授權選項。

## 實作指南
在本節中，我們將逐一說明使用 Aspose.Words for Java 進行批註管理的各項功能。

### 功能 1：新增批註與回覆
**概述**  
此功能示範如何在 Word 文件中新增批註與回覆，適用於多位審閱者提供回饋的協同編輯情境。

#### 實作步驟
**步驟 1：** 初始化 Document 物件  
`Document` 是代表記憶體中 Word 文件的主要類別。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

**步驟 2：** 建立並新增批註  
`Comment` 儲存作者、日期以及被批註的文字範圍。  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**步驟 3：** 為批註新增回覆  
`Reply` 物件透過 `getReplies()` 集合附加於父 `Comment`。  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

### 功能 2：列印所有批註
**概述**  
此功能列印所有頂層批註及其回覆，讓您能一次性檢視大量回饋。

#### 實作步驟
**步驟 1：** 載入文件  
`Document` 代表您正在處理的 Word 檔案。  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

**步驟 2：** 取得並列印批註  
`Comment` 物件可迭代以提取作者與文字資訊。  
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

### 功能 3：移除批註回覆
**概述**  
移除特定回覆或全部回覆，以保持文件的整潔與組織。

#### 實作步驟
**步驟 1：** 初始化並新增含回覆的批註  
建立 `Comment` 物件並填入 `Reply` 條目。  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

**步驟 2：** 移除回覆  
`Reply` 代表回應；您可以清除或刪除單一項目。  
```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```  

### 功能 4：將批註標記為完成
**概述**  
將批註標記為已解決，以有效追蹤文件中的問題。

#### 實作步驟
**步驟 1：** 建立文件並新增批註  
`Document` 是新批註的容器。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

**步驟 2：** 將批註標記為完成  
`setDone(true)` 將批註標記為已解決。  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```  

### 功能 5：取得批註的 UTC 日期與時間
**概述**  
取得批註加入的精確 UTC 日期與時間，以便精確追蹤。

#### 實作步驟
**步驟 1：** 建立含時間戳記的批註文件  
`Document` 包含將要檢查時間戳記的批註。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```  

**步驟 2：** 儲存並取得 UTC 日期  
`getDateTime()` 回傳批註的建立時間，可轉換為 UTC。  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 實務應用
了解並運用這些功能，可在多種情境下顯著提升文件管理效能：
- **協同編輯：** 透過批註與回覆促進團隊協作。
- **文件審閱：** 透過將問題標記為已解決來簡化審閱流程。
- **回饋管理：** 使用精確的時間戳記追蹤回饋。

## 效能考量
處理大型文件時，請考慮以下最佳化建議：
- 限制一次處理的批註數量。
- 使用高效資料結構（例如 `ArrayList`）儲存與取得批註。
- 定期更新 Aspose.Words，以利用效能提升與錯誤修正。

## 常見問題

**問：什麼是 Aspose.Words for Java？**  
A: Aspose.Words for Java 是一套完整管理的 API，允許在不需要 Microsoft Word 的情況下建立、修改、轉換與呈現 Word 文件。

**問：如何以程式方式新增批註？**  
A: 建立 `Document` 實例，建立帶有作者與文字的 `Comment`，將其指派給 `Range`，再加入文件的 `CommentCollection`。

**問：我可以取得批註的精確加入時間嗎？**  
A: 可以，使用 `comment.getDateTime()` 取得 `java.util.Date`；再以 `toInstant()` 轉換為 UTC 的 ISO‑8601 字串。

**問：如何將批註標記為已解決？**  
A: 呼叫 `comment.setDone(true)`；在支援的 Word 檢視器中，批註會顯示「完成」勾選標記。

**問：正式環境使用是否需要授權？**  
A: 完整授權會移除所有評估限制；臨時試用授權足以用於測試與開發。

## 結論
您現在已掌握如何使用 Aspose.Words for Java 管理 Word 文件中的批註。透過新增批註、加入批註回覆、列印 Word 批註、移除回覆、將批註標記為完成，以及提取 UTC 時間戳記，您可以建構強大且協同的文件工作流程。探索更多 Aspose.Words 功能——如合併列印、表格操作與 PDF 轉換——以進一步擴充自動化能力。

**下一步**
- 嘗試將批註管理與文件版本控制結合。
- 將這些程式碼片段整合至您現有的內容管理或審閱系統。
- 檢視 Aspose.Words API 參考文件，以獲得更深入的客製化選項。

---

**Last Updated:** 2026-07-16  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose

## 相關教學

- [使用 Aspose.Words Java 追蹤 Word 文件變更：文件修訂完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [精通 Aspose.Words for Java：在 Word 文件中插入與管理書籤](/words/java/content-management/aspose-words-java-manage-bookmarks/)
- [使用 Aspose.Words Java 管理 Word 超連結：完整指南](/words/java/content-management/master-hyperlink-management-word-aspose-words-java/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}