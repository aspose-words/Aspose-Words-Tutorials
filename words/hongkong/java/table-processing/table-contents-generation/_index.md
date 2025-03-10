---
title: 目錄生成
linktitle: 目錄生成
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 建立動態目錄。透過逐步指導和原始碼範例掌握 TOC 生成。
weight: 14
url: /zh-hant/java/table-processing/table-contents-generation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 目錄生成

## 介紹

您是否曾在 Word 文件中建立動態且具有專業外觀的目錄 (TOC) 時遇到困難？別再猶豫了！透過 Aspose.Words for Java，您可以自動化整個流程，從而節省時間並確保準確性。無論您是要建立綜合報告還是學術論文，本教學都將引導您使用 Java 以程式設計方式產生 TOC。準備好潛入了嗎？讓我們開始吧！

## 先決條件

在我們開始編碼之前，請確保您具備以下條件：

1.  Java 開發工具包 (JDK)：安裝在您的系統上。您可以從以下位置下載：[甲骨文網站](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words for Java Library：從以下位置下載最新版本[發布頁面](https://releases.aspose.com/words/java/).
3. 整合開發環境 (IDE)：例如 IntelliJ IDEA、Eclipse 或 NetBeans。
4.  Aspose 臨時許可證：為了避免評估限制，請取得[臨時執照](https://purchase.aspose.com/temporary-license/).

## 導入包

若要有效地使用 Aspose.Words for Java，請確保匯入所需的類別。以下是進口：

```java
import com.aspose.words.*;
```

請依照下列步驟在 Word 文件中產生動態目錄。

## 第 1 步：初始化 Document 和 DocumentBuilder

第一步是建立一個新文件並使用`DocumentBuilder`類別來操縱它。


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`：代表Word文檔。
- `DocumentBuilder`：一個幫助程序類，可以輕鬆操作文件。

## 第 2 步：插入目錄

現在，讓我們在文件的開頭插入目錄。


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`：插入目錄字段。參數指定：
  - `\o "1-3"`：包括 1 至 3 級標題。
  - `\h`：製作條目超連結。
  - `\z`：隱藏 Web 文件的頁碼。
  - `\u`：保留超連結的樣式。
- `insertBreak`：在目錄後面加入分頁符號。

## 步驟 3：新增標題以填滿目錄

要填滿目錄，您需要新增帶有標題樣式的段落。


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier` ：將段落樣式設定為特定標題層級（例如，`HEADING_1`, `HEADING_2`）。
- `writeln`：以指定樣式為文件新增文字。

## 第 4 步：新增嵌套標題

若要示範 TOC 級別，請包含嵌套標題。


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

## 第 5 步：更新目錄字段

必須更新 TOC 欄位才能顯示最新的標題。


```java
doc.updateFields();
```

- `updateFields`：刷新文件中的所有字段，確保目錄反映添加的標題。

## 第 6 步：儲存文檔

最後，將文件儲存為您想要的格式。


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save` ：將文檔匯出到`.docx`文件。您可以指定其他格式，例如`.pdf`或者`.txt`如果需要的話。

## 結論

恭喜！您已使用 Aspose.Words for Java 在 Word 文件中成功建立了動態目錄。只需幾行程式碼，您就可以自動完成一項原本可能需要數小時才能完成的任務。那麼，下一步是什麼？嘗試嘗試不同的標題樣式和格式，以根據特定需求自訂目錄。

## 常見問題解答

### 我可以進一步自訂目錄格式嗎？
絕對地！您可以調整目錄參數，例如包含頁碼、對齊文字或使用自訂標題樣式。

### Aspose.Words for Java 是否強制需要授權？
是的，完整功能需要許可證。您可以從[臨時執照](https://purchase.aspose.com/temporary-license/).

### 我可以為現有文件產生目錄嗎？
是的！將文檔載入到`Document`物件並按照相同的步驟插入和更新 TOC。

### 這適用於 PDF 導出嗎？
是的，如果您將文件保存在 PDF 中，目錄將出現在`.pdf`格式。

### 在哪裡可以找到更多文件？
查看[Aspose.Words for Java 文檔](https://reference.aspose.com/words/java/)了解更多範例和詳細資訊。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
