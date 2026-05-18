---
date: '2026-05-18'
description: 了解如何使用 Aspose.Words for Java 管理 Word 文件中的批註。可在 Java 中新增批註、列印 Word 批註、刪除
  Word 批註，以及高效地新增批註回覆。
keywords:
- how to manage comments
- add comment java
- print word comments
- java document comments
- delete word comment
- add comment reply
schemas:
- author: Aspose
  dateModified: '2026-05-18'
  description: Learn how to manage comments in Word documents with Aspose.Words for
    Java. Add comment java, print word comments, delete word comment, and add comment
    reply efficiently.
  headline: How to Manage Comments in Word Documents Using Aspose.Words for Java
  type: TechArticle
- questions:
  - answer: Yes, with a valid license; a free trial is available for evaluation.
    question: Can I use Aspose.Words for Java in a commercial application?
  - answer: Yes, provide the password when loading the document via `LoadOptions`.
    question: Does the library work with password‑protected Word files?
  - answer: Aspose.Words for Java supports JDK 8 through JDK 21, covering both legacy
      and modern environments.
    question: Which Java versions are supported?
  - answer: Use `LoadOptions.setLoadFormat(LoadFormat.DOCX)` and enable `LoadOptions.setMemoryOptimization(true)`
      to reduce memory footprint.
    question: How do I handle documents larger than 200 MB?
  - answer: Iterate `doc.getComments()` and write each comment’s properties to a CSV
      using standard Java I/O.
    question: Is there a way to export comments to a CSV file?
  type: FAQPage
title: 如何使用 Aspose.Words for Java 管理 Word 文件中的批註
url: /zh-hant/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 管理 Word 文件中的評論

以程式方式管理評論有時像在迷宮中穿梭，特別是當您需要新增回覆、刪除不需要的註解，或追蹤每則評論的時間時。本教學將向您展示如何使用 Aspose.Words for Java 高效地**管理評論**，涵蓋從新增評論到取得其 UTC 時間戳的全部內容。

## 快速解答
- **如何在 Java 中新增評論？** 使用 `Document` → `Comment` 物件，並在 `CommentRangeStart` 上呼叫 `appendChild`。
- **我可以列印 Word 檔案中的所有評論嗎？** 迭代 `doc.getComments()`，輸出每則評論的文字與作者。
- **有沒有方法可以刪除評論？** 從文件的評論集合中移除該評論節點。
- **如何為評論新增回覆？** 建立 `Comment` 物件，設定其 `ParentComment` 屬性，然後加入文件中。
- **如何取得評論的時間戳記？** 存取 `Comment.getDateTime()`，它會回傳 UTC 的 `java.time` 值。

## 什麼是 Word 文件中的評論管理？
評論管理是指在 Word 檔案中以程式方式建立、取得、修改與移除評論物件。它可實現自動化的審閱工作流程，無需手動編輯，讓開發人員能以程式方式新增、回覆、解決及擷取評論，從而簡化團隊間的協作與稽核流程。

## 為何使用 Aspose.Words for Java 來管理評論？
Aspose.Words 支援 **35 種以上的輸入與輸出格式**，且能在標準伺服器硬體上於 **3 秒內處理 500 頁文件**，且不需安裝 Microsoft Word。其豐富的 API 讓您能細緻地控制評論物件、時間戳記與回覆層級。

## 前置條件
- 已安裝 Java Development Kit (JDK) 8 或更新版本。
- 具備 Java 語法與物件導向概念的基本認識。
- 使用如 IntelliJ IDEA 或 Eclipse 等 IDE 以便於專案管理。
- 有效的 Aspose.Words for Java 授權（試用版或正式版）。

### 設定 Aspose.Words for Java
Aspose.Words 以 Maven 或 Gradle 套件的形式提供。請加入與您的建置系統相符的相依性。

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
Aspose.Words 為商業套件，但您可先使用免費試用版或申請臨時授權以取得完整功能。請前往[購買頁面](https://purchase.aspose.com/buy)了解授權方案。

## 如何以 Java 方式新增評論？
`Document` 是代表載入記憶體中的 Word 檔案的主要 Aspose.Words 物件。`Comment` 代表可儲存作者、文字與時間戳記資訊的單一評論節點。若要新增頂層評論，請載入或建立 `Document`，以所需的作者與文字實例化 `Comment`，並將其附加至目標位置的 `CommentRangeStart`。此方法僅需幾行程式碼即可插入評論。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```  

## 如何在 Java 中為評論新增回覆？
`Comment` 物件可透過 `ParentComment` 屬性連結形成回覆鏈。將此屬性設定為現有的評論，新的評論即成為該父評論的子項（回覆）。建立子 `Comment`，將其 `ParentComment` 指向原始評論，並插入文件中。這樣回覆會直接嵌套在父評論之下，保留討論層級。  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```  

## 如何列印 Word 評論？
`Document.getComments()` 會回傳 Word 檔案中所有 `Comment` 節點的集合。透過迭代此集合，您可以取得每則評論的作者、文字與時間戳記。載入文件，呼叫 `getComments()`，然後對每個 `Comment` 將其詳細資訊輸出至主控台或日誌。這可快速概覽檔案中嵌入的所有回饋。  
```java
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/Comments.docx");
```  

## 如何刪除 Word 評論？
`Comment.remove()` 會將評論節點從文件樹中分離，實際上即刪除該評論。首先在 `Document.getComments()` 集合中找到目標評論，然後呼叫其 `remove()` 方法。若您選擇清除整個層級，此操作亦會移除所有子回覆，確保評論徹底從檔案中消除。  
```java
Document document = new Document();
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
comment.addReply("Joe Bloggs", "J.B.", new Date(), "Another reply");
```  

## 如何將評論標記為已完成？
`Comment.setDone(boolean)` 可將評論標記為已解決，會在 Word UI 中切換顯示「Done」旗標。建立或找到評論後，呼叫 `setDone(true)` 以表示問題已處理。此旗標協助審閱者快速辨識已完成項目，若需可稍後使用 `setDone(false)` 取消。  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```  

## 如何從評論取得 UTC 日期與時間？
`Comment.getDateTime()` 以 UTC 的 `java.time.OffsetDateTime` 回傳評論的建立時間戳記。載入文件後存取此屬性，即可取得每則評論的精確時間資訊，對稽核追蹤與版本控制相當有用。必要時亦可將其轉換為其他時區。  
```java
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Document doc = new Document(YOUR_DOCUMENT_DIRECTORY + "/CommentUtcDateTime.docx");
Comment currentComment = (Comment) doc.getChild(NodeType.COMMENT, 0, true);
assert currentComment.getDateTimeUtc().toString() == dateTime.toString();
```  

## 實務應用
了解並運用這些評論管理功能，可改變許多實務工作流程：

- **協同編輯：** 團隊可在文件內直接新增、回覆與解決評論。
- **文件審閱流程：** 自動化腳本可擷取所有回饋，產生摘要報告，並將項目標記為已完成。
- **稽核與合規：** UTC 時間戳記提供每則評論的不可變更紀錄，對法規追蹤相當有用。

## 效能考量
處理大型檔案時，請留意以下最佳實踐建議：

- 以批次方式處理評論，而非一次載入整個評論樹至記憶體。
- 僅在需要一次清除所有評論時才使用 `Document.getComments().clear()`。
- 升級至最新的 Aspose.Words 版本，以獲得記憶體最佳化的評論處理效能。

## 常見問題與解決方案
| 問題 | 解決方案 |
|-------|----------|
| **存取評論時的 NullPointerException** | 確保在呼叫 `getComments()` 前已完整載入文件（`Document.load`）。 |
| **回覆未在 Word UI 中顯示** | 正確設定 `ParentComment` 屬性；回覆必須參考已存在的評論。 |
| **時間戳記顯示本地時間而非 UTC** | 使用 `Comment.getDateTime().withOffsetSameInstant(ZoneOffset.UTC)` 以強制使用 UTC。 |

## 常見問答

**Q: 我可以在商業應用程式中使用 Aspose.Words for Java 嗎？**  
A: 可以，需具備有效授權；亦提供免費試用版供評估。

**Q: 此函式庫能處理受密碼保護的 Word 檔案嗎？**  
A: 能，載入文件時透過 `LoadOptions` 提供密碼即可。

**Q: 支援哪些 Java 版本？**  
A: Aspose.Words for Java 支援 JDK 8 至 JDK 21，涵蓋舊版與新版環境。

**Q: 如何處理大於 200 MB 的文件？**  
A: 使用 `LoadOptions.setLoadFormat(LoadFormat.DOCX)` 並啟用 `LoadOptions.setMemoryOptimization(true)` 以降低記憶體占用。

**Q: 有沒有方法將評論匯出為 CSV 檔案？**  
A: 迭代 `doc.getComments()`，並使用標準 Java I/O 將每則評論的屬性寫入 CSV。

---

**最後更新：** 2026-05-18  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

{{< blocks/products/products-backtop-button >}}

## 相關教學

- [使用 Aspose.Words Java 追蹤 Word 文件變更&#58; 文件修訂完整指南](/words/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)
- [精通 Aspose.Words for Java 註解與評論教學](/words/java/annotations-comments/)
- [精通 Aspose.Words for Java&#58; 在 Word 文件中插入與管理書籤](/words/java/content-management/aspose-words-java-manage-bookmarks/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

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

```java
comment.removeReply(comment.getReplies().get(0)); // Remove one reply
comment.removeAllReplies(); // Remove all remaining replies
```

```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
Date dateTime = new Date();
Comment comment = new Comment(document, "John Doe", "J.D.", dateTime);
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```