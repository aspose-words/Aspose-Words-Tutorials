---
date: '2026-01-27'
description: 學習如何在 Java 中新增註解，並使用 Aspose.Words for Java 在 Word 文件中新增與移除註解。輕鬆管理、列印、刪除及為註解加上時間戳記。
keywords:
- Aspose.Words Java
- comment management in Word documents
- managing comments with Aspose.Words
title: 使用 Aspose.Words 在 Java 中新增註解 – 註解管理大師
url: /zh-hant/java/annotations-comments/aspose-words-java-comment-management-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Java：精通 Word 文件中的評論管理

## 介紹
如果您需要以程式方式 **add comment java**，並完整掌控評論的生命週期，您來對地方了。無論是建立協作審閱工具，或是自動化文件工作流程，管理評論──新增、回覆、移除以及追蹤時間戳記──都可能是痛點。在本教學中，我們將使用 Aspose.Words for Java 示範每一項必要操作，讓您能自信地 **add remove word comments**、列印評論、標記為已完成，並擷取 UTC 時間戳記。

**您將學習**
- 只需一行程式碼即可新增評論與回覆  
- 如何列印所有頂層評論及其巢狀回覆  
- 如何移除單一回覆或完整清除評論串  
- 如何將評論標記為已完成（已解決）  
- 如何取得評論建立的精確 UTC 日期與時間  

準備好了嗎？在深入程式碼之前，先確保您的環境已正確設定。

## 前置條件
在開始之前，請確保您已具備以下條件：

- 已安裝 Java Development Kit (JDK) 8 或以上版本  
- 具備 Java 語法與物件導向程式設計的基本知識  
- 使用 IntelliJ IDEA 或 Eclipse 等 IDE 以便於專案管理  

### 設定 Aspose.Words for Java
Aspose.Words 是功能強大的函式庫，可讓您以多種格式操作 Word 文件。將符合您建置系統的相依性加入專案：

**Maven**  
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### 取得授權
Aspose.Words 為商業產品，但您可先使用免費試用版，或申請臨時授權以取得完整功能。請前往 [purchase page](https://purchase.aspose.com/buy) 了解授權選項。

## 快速問答
- **可以在沒有授權的情況下 add comment java 嗎？** 可以，試用版可用，但會加上評估水印。  
- **哪個方法可新增回覆？** `comment.addReply(author, initials, date, text)`。  
- **如何將評論標記為已完成？** 呼叫 `comment.setDone(true)`。  
- **是否提供 UTC 時間戳記？** 使用 `comment.getDateTimeUtc()`。  
- **測試使用的版本為何？** Aspose.Words 25.3 (Java)。

## 實作指南
以下各節將逐步說明每項功能，並提供實務技巧。

### 功能 1：新增評論與回覆
#### 概觀
新增評論與回覆是協作編輯的基礎。您將學會如何建立評論、將其附加至段落，並再加入巢狀回覆。

#### 實作步驟
**步驟 1：** 初始化 Document 物件  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
```

**步驟 2：** 建立並加入評論  
```java
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("My comment.");
documentBuilder.getCurrentParagraph().appendChild(comment);
```

**步驟 3：** 為評論新增回覆  
```java
comment.addReply("Joe Bloggs", "J.B.", new Date(), "New reply");
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentWithReply.docx");
```

### 功能 2：列印所有評論
#### 概觀
在審閱大型文件時，同時列印所有頂層評論與其回覆可節省時間。此程式碼示範如何載入文件並遍歷評論層級。

#### 實作步驟
**步驟 1：** 載入文件  
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

### 功能 3：移除評論回覆
#### 概觀
有時評論串會變得雜訊太多。此範例說明如何刪除單一回覆或清除整個回覆清單。

#### 實作步驟
**步驟 1：** 初始化並加入含回覆的評論  
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

### 功能 4：將評論標記為已完成
#### 概觀
將評論標記為「已完成」表示問題已解決。此旗標可在 UI 層面過濾已完成的回饋。

#### 實作步驟
**步驟 1：** 建立文件並加入評論  
```java
Document document = new Document();
DocumentBuilder documentBuilder = new DocumentBuilder(document);
documentBuilder.writeln("Hello world!");
Comment comment = new Comment(document, "John Doe", "J.D.", new Date());
comment.setText("Fix the spelling error!");
```

**步驟 2：** 將評論標記為已完成  
```java
document.getFirstSection().getBody().getFirstParagraph().appendChild(comment);
document.getFirstSection().getBody().getFirstParagraph().getRuns().get(0).setText("Hello world!");
comment.setDone(true);
document.save(YOUR_DOCUMENT_DIRECTORY + "/CommentDone.docx");
```

### 功能 5：從評論取得 UTC 日期與時間
#### 概觀
精確的時間戳記對於稽核追蹤至關重要。Aspose.Words 以 UTC 儲存建立時間，您可以取得並比較該時間。

#### 實作步驟
**步驟 1：** 建立帶有時間戳記的評論文件  
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
了解這些 API 可大幅提升文件導向解決方案的效能：

- **協作編輯：** 讓多位審閱者直接在檔案中留下回饋、回覆並解決問題。  
- **文件審查流程：** 自動擷取評論以供報告或合規檢查。  
- **稽核追蹤：** 為法律或法規需求儲存 UTC 時間戳記。  

這些程式碼片段可整合至內容管理平台、自動化報告產生器或自訂的文字處理工具等大型系統。

## 效能考量
處理大型 Word 檔（數百頁、數千條評論）時，請留意以下建議：

- 以批次方式處理評論，避免一次將全部載入記憶體。  
- 在執行多項操作時，重複使用同一個 `Document` 實例。  
- 升級至最新的 Aspose.Words 版本，以獲得效能優化與錯誤修正。

## 常見問題與解決方案
| 問題 | 為何會發生 | 解決方式 |
|------|------------|----------|
| **`NullPointerException` 在存取回覆時拋出** | 該評論沒有回覆（`getReplies()` 回傳空集合）。 | 在存取元素前，先確認 `comment.getReplies().getCount() > 0`。 |
| **儲存後評論未出現** | 文件被儲存至不同資料夾或被覆寫。 | 確認 `YOUR_DOCUMENT_DIRECTORY` 指向正確位置且具寫入權限。 |
| **UTC 時間戳記與本地時間不一致** | `Date` 使用系統區域設定；`getDateTimeUtc()` 會轉換為 UTC。 | 使用 `new Date()` 建立時間，並依賴 `getDateTimeUtc()` 取得一致的儲存時間。 |

## FAQ 區段
1. **什麼是 Aspose.Words for Java？**  
   - 它是一套程式庫，可讓開發者以程式方式操作各種格式的 Word 文件。  

2. **如何在我的專案中安裝 Aspose.Words？**  
   - 將前述的 Maven 或 Gradle 相依性加入專案檔案即可。  

3. **可以在沒有授權的情況下使用 Aspose.Words 嗎？**  
   - 可以，但會有評估水印與功能限制。  

4. **管理評論時常見的問題有哪些？**  
   - 確保正確載入文件、處理回覆的 null 參考，並驗證評論層級結構。  

5. **如何追蹤多個文件的變更？**  
   - 在應用程式中實作版本控制邏輯，或使用 Aspose.Words 內建的修訂追蹤功能。  

---

**最後更新：** 2026-01-27  
**測試版本：** Aspose.Words 25.3 for Java  
**作者：** Aspose  

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}