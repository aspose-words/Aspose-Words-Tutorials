---
"description": "了解如何使用 Aspose.Words for Java 建立動態目錄。透過逐步指導和原始碼範例掌握 TOC 生成。"
"linktitle": "目錄生成"
"second_title": "Aspose.Words Java文件處理API"
"title": "目錄生成"
"url": "/zh-hant/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 目錄生成

## 介紹

您是否曾為在 Word 文件中建立動態且具有專業外觀的目錄 (TOC) 而苦惱過？別再猶豫了！使用 Aspose.Words for Java，您可以自動化整個過程，節省時間並確保準確性。無論您是要建立綜合報告還是學術論文，本教學都將指導您使用 Java 以程式設計方式產生目錄。準備好了嗎？讓我們開始吧！

## 先決條件

在開始編碼之前，請確保您具備以下條件：

1. Java 開發工具包 (JDK)：安裝在您的系統上。您可以從下載 [Oracle 網站](https://www。oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Java 函式庫：從下載最新版本 [發布頁面](https://releases。aspose.com/words/java/).
3. 整合開發環境 (IDE)：例如 IntelliJ IDEA、Eclipse 或 NetBeans。
4. Aspose 臨時許可證：為避免評估限制，請取得 [臨時執照](https://purchase。aspose.com/temporary-license/).

## 導入包

為了有效地使用 Aspose.Words for Java，請確保匯入所需的類別。以下是導入內容：

```java
import com.aspose.words.*;
```

請依照下列步驟在 Word 文件中產生動態目錄。

## 步驟 1：初始化 Document 和 DocumentBuilder

第一步是建立一個新文件並使用 `DocumentBuilder` 類別來操作它。


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`：代表Word文檔。
- `DocumentBuilder`：允許輕鬆操作文件的輔助類別。

## 第 2 步：插入目錄

現在，讓我們將目錄插入文件的開頭。


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`：插入目錄字段。參數指定：
  - `\o "1-3"`：包括 1 至 3 級標題。
  - `\h`：使條目成為超連結。
  - `\z`：抑制網頁文件的頁碼。
  - `\u`：保留超連結的樣式。
- `insertBreak`：在目錄後面加入分頁符號。

## 步驟 3：新增標題以填滿目錄

要填滿目錄，您需要新增具有標題樣式的段落。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`：將段落樣式設定為特定的標題層級（例如， `HEADING_1`， `HEADING_2`）。
- `writeln`：使用指定的樣式為文件新增文字。

## 步驟 4：新增嵌套標題

為了展示目錄級別，請包含嵌套標題。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- 新增更深層的標題以顯示目錄中的層次結構。

## 步驟 5：更新目錄字段

必須更新 TOC 欄位以顯示最新標題。


```java
doc.updateFields();
```

- `updateFields`：刷新文件中的所有字段，確保目錄反映添加的標題。

## 步驟6：儲存文檔

最後，將文件儲存為您想要的格式。


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`：將文檔匯出至 `.docx` 文件。您可以指定其他格式，例如 `.pdf` 或者 `.txt` 如果需要的話。

## 結論

恭喜！您已成功使用 Aspose.Words for Java 在 Word 文件中建立動態目錄。只需幾行程式碼，您就可以自動完成原本需要花費數小時的任務。那麼，下一步是什麼？嘗試使用不同的標題樣式和格式來根據特定需求自訂目錄。

## 常見問題解答

### 我可以進一步自訂 TOC 格式嗎？
絕對地！您可以調整目錄參數，例如包含頁碼、對齊文字或使用自訂標題樣式。

### Aspose.Words for Java 是否必須取得授權？
是的，需要許可證才能使用全部功能。你可以從 [臨時執照](https://purchase。aspose.com/temporary-license/).

### 我可以為現有文件產生目錄嗎？
是的！將文件裝入 `Document` 物件並按照相同的步驟插入和更新目錄。

### 這對於 PDF 導出有用嗎？
是的，如果您將文件儲存為 `.pdf` 格式。

### 在哪裡可以找到更多文件？
查看 [Aspose.Words for Java 文檔](https://reference.aspose.com/words/java/) 了解更多範例和詳細資訊。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}