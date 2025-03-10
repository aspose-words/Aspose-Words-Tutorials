---
title: 比較文件的差異
linktitle: 比較文件的差異
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Java 中的 Aspose.Words 比較文件的差異。我們的逐步指南可確保準確的文件管理。
weight: 12
url: /zh-hant/java/document-merging/comparing-documents-for-differences/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 比較文件的差異

## 介紹

有沒有想過如何找出兩個 Word 文件之間的每一個差異？也許您正在修改文件或嘗試尋找協作者所做的變更。手動比較可能很乏味且容易出錯，但使用 Aspose.Words for Java，一切變得輕而易舉！該庫使您能夠輕鬆地自動進行文件比較、突出顯示修訂並合併更改。

## 先決條件

在開始編寫程式碼之前，請確保您已準備好以下內容：  
1. 您的系統上安裝了 Java 開發工具包 (JDK)。  
2.  Aspose.Words for Java 函式庫。你可以[在這裡下載](https://releases.aspose.com/words/java/).  
3. IntelliJ IDEA 或 Eclipse 等開發環境。  
4. 基本熟悉 Java 程式設計。  
5. 有效的 Aspose 許可證。如果您沒有，請取得一個[臨時許可證在這裡](https://purchase.aspose.com/temporary-license/).

## 導入包

要使用Aspose.Words，您需要匯入必要的類別。以下是所需的導入：

```java
import com.aspose.words.*;
import java.util.Date;
```

確保這些套件已正確新增至您的專案依賴項。


在本節中，我們將把該過程分解為簡單的步驟。


## 第 1 步：設定您的文檔

首先，您需要兩個文檔：一個代表原始文檔，另一個代表編輯後的版本。創建它們的方法如下：

```java
Document doc1 = new Document();
DocumentBuilder builder = new DocumentBuilder(doc1);
builder.writeln("This is the original document.");

Document doc2 = new Document();
builder = new DocumentBuilder(doc2);
builder.writeln("This is the edited document.");
```

這將在記憶體中建立兩個具有基本內容的文件。您也可以使用載入現有的 Word 文檔`new Document("path/to/document.docx")`.


## 第 2 步：檢查現有修訂

Word 文件中的修訂代表追蹤的變更。在比較之前，請確保兩個文件都不包含預先存在的修訂：

```java
if (doc1.getRevisions().getCount() == 0 && doc2.getRevisions().getCount() == 0) {
    System.out.println("No revisions found. Proceeding with comparison...");
}
```

如果存在修訂，您可能需要在繼續之前接受或拒絕它們。


## 第 3 步：比較文件

使用`compare`尋找差異的方法。此方法比較目標文件（`doc2`）與來源文件（`doc1`）：

```java
doc1.compare(doc2, "AuthorName", new Date());
```

這裡：
- AuthorName 是進行更改的人的姓名。
- 日期是比較時間戳。


## 第 4 步：流程修訂

比較後，Aspose.Words 將在來源文件中產生修訂（`doc1`）。我們來分析一下這些修改：

```java
for (Revision r : doc1.getRevisions()) {
    System.out.println("Revision type: " + r.getRevisionType());
    System.out.println("Node type: " + r.getParentNode().getNodeType());
    System.out.println("Changed text: " + r.getParentNode().getText());
}
```

此循環提供有關每個修訂的詳細信息，例如更改類型和受影響的文字。


## 第 5 步：接受所有修改

如果您想要來源文件（`doc1`) 來配對目標文件 (`doc2`），接受所有修改：

```java
doc1.getRevisions().acceptAll();
```

本次更新`doc1`以反映所做的所有更改`doc2`.


## 步驟6：儲存更新後的文檔

最後，將更新後的文檔儲存到磁碟：

```java
doc1.save("Document.Compare.docx");
```

若要確認更改，請重新載入文件並驗證沒有剩餘的修訂：

```java
doc1 = new Document("Document.Compare.docx");
if (doc1.getRevisions().getCount() == 0) {
    System.out.println("Documents are now identical.");
}
```


## 第 7 步：驗證文檔相等性

為了確保文件相同，請比較它們的文字：

```java
if (doc1.getText().trim().equals(doc2.getText().trim())) {
    System.out.println("Documents are equal.");
}
```

如果文字匹配，恭喜您 - 您已成功比較並同步文件！


## 結論

有了 Aspose.Words for Java，文件比較不再是苦差事。只需幾行程式碼，您就可以找出差異、處理修訂並確保文件一致性。無論您是管理協作寫作專案還是審核法律文件，此功能都會改變遊戲規則。

## 常見問題解答

### 我可以將文件與圖像和表格進行比較嗎？  
是的，Aspose.Words 支援比較複雜的文檔，包括具有圖像、表格和格式的文檔。

### 我需要許可證才能使用此功能嗎？  
是的，完整功能需要許可證。得到一個[臨時許可證在這裡](https://purchase.aspose.com/temporary-license/).

### 如果存在預先存在的修訂會怎樣？  
您必須在比較文件之前接受或拒絕它們以避免衝突。

### 我可以突出顯示文件中的修訂嗎？  
是的，Aspose.Words 允許您自訂修訂的顯示方式，例如反白顯示變更。

### 其他程式語言是否提供此功能？  
是的，Aspose.Words 支援多種語言，包括 .NET 和 Python。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
