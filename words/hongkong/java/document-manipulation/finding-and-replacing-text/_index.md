---
title: 在 Aspose.Words for Java 中尋找和取代文本
linktitle: 尋找和取代文本
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 尋找和取代 Word 文件中的文字。帶有程式碼範例的分步指南。提升您的 Java 文件操作技能。
weight: 15
url: /zh-hant/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中尋找和取代文本


## 在 Aspose.Words for Java 中尋找和取代文字簡介

Aspose.Words for Java 是一個功能強大的 Java API，可讓您以程式設計方式處理 Word 文件。處理 Word 文件時的常見任務之一是尋找和取代文字。無論您需要更新範本中的佔位符還是執行更複雜的文字操作，Aspose.Words for Java 都可以幫助您有效率地實現目標。

## 先決條件

在我們深入了解尋找和取代文字的詳細資訊之前，請確保您具備以下先決條件：

- Java開發環境
- Aspose.Words for Java 函式庫
- 可供使用的範例 Word 文檔

您可以從以下位置下載 Aspose.Words for Java 程式庫：[這裡](https://releases.aspose.com/words/java/).

## 尋找並取代簡單文字

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立文檔產生器
DocumentBuilder builder = new DocumentBuilder(doc);

//尋找並取代文本
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

//儲存修改後的文檔
doc.save("modified-document.docx");
```

在這個例子中，我們載入一個Word文檔，建立一個`DocumentBuilder`，並使用`replace`方法在文件中尋找並用“新文字”取代“舊文字”。

## 使用正規表示式

正規表示式為文字搜尋和取代提供了強大的模式匹配功能。 Aspose.Words for Java 支援正規表示式以進行更進階的查找和取代操作。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立文檔產生器
DocumentBuilder builder = new DocumentBuilder(doc);

//使用正規表示式尋找和取代文本
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

//儲存修改後的文檔
doc.save("modified-document.docx");
```

在此範例中，我們使用正規表示式模式來尋找和取代文件中的文字。

## 忽略字段內的文本

您可以將 Aspose.Words 配置為在執行尋找和取代操作時忽略欄位內的文字。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立 FindReplaceOptions 實例並將 IgnoreFields 設為 true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

//替換文字時使用選項
doc.getRange().replace("text-to-replace", "new-text", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

當您想要排除欄位（例如合併欄位）內的文字被替換時，這非常有用。

## 忽略刪除修訂內的文本

您可以設定 Aspose.Words 在尋找和取代操作期間忽略刪除修訂內的文字。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立 FindReplaceOptions 實例並將 IgnoreDeleted 設為 true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

//替換文字時使用選項
doc.getRange().replace("text-to-replace", "new-text", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

這允許您排除追蹤變更中已標記為刪除的文本，使其不被替換。

## 忽略插入修訂內的文本

您可以設定 Aspose.Words 在尋找和取代操作期間忽略插入修訂內的文字。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立 FindReplaceOptions 實例並將 IgnoreInserted 設為 true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

//替換文字時使用選項
doc.getRange().replace("text-to-replace", "new-text", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

這允許您排除已標記為插入追蹤變更的文字被替換。

## 用 HTML 取代文字

您可以使用 Aspose.Words for Java 將文字替換為 HTML 內容。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//使用自訂替換回呼建立 FindReplaceOptions 實例
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

//替換文字時使用選項
doc.getRange().replace("text-to-replace", "new-html-content", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

在這個例子中，我們使用自訂的`ReplaceWithHtmlEvaluator`用 HTML 內容取代文字。

## 替換頁首和頁尾中的文本

您可以尋找並取代 Word 文件的頁首和頁尾中的文字。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//取得頁首和頁尾的集合
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

//選擇要取代文字的頁首或頁尾類型（例如，HeaderFooterType.FOOTER_PRIMARY）
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

//建立一個 FindReplaceOptions 實例並將其應用於頁尾範圍
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

這允許您專門在頁首和頁尾中執行文字替換。

## 顯示頁首和頁尾訂單的更改

您可以使用 Aspose.Words 顯示文件中頁首和頁尾順序的變更。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//取得第一部分
Section firstPageSection = doc.getFirstSection();

//建立 FindReplaceOptions 實例並將其套用至文件範圍
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

//取代影響頁首和頁尾順序的文本
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

這使您可以視覺化與文件中頁首和頁尾順序相關的變更。

## 用字段替換文本

您可以使用 Aspose.Words for Java 將文字替換為欄位。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立 FindReplaceOptions 實例並為欄位設定自訂替換回調
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

//替換文字時使用選項
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

在此範例中，我們用欄位替換文字並指定欄位類型（例如，`FieldType.FIELD_MERGE_FIELD`）。

## 用評估器替換

您可以使用自訂求值器來動態確定替換文字。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立 FindReplaceOptions 實例並設定自訂替換回調
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

//替換文字時使用選項
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

在此範例中，我們使用自訂評估器（`MyReplaceEvaluator`) 來替換文字。

## 用正規表示式替換

Aspose.Words for Java 可讓您使用正規表示式取代文字。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//使用正規表示式尋找和取代文本
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

//儲存修改後的文檔
doc.save("modified-document.docx");
```

在此範例中，我們使用正規表示式模式來尋找和取代文件中的文字。

## 識別替換模式中的替換

您可以使用 Aspose.Words for Java 在替換模式中識別並進行替換。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立一個 FindReplaceOptions 實例，並將 UseSubstitutions 設為 true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

//用模式取代文字時使用選項
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

這允許您在替換模式內執行替換以實現更高級的替換。

## 用字串替換

您可以使用 Aspose.Words for Java 將文字替換為簡單的字串。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//用字串替換文本
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

//儲存修改後的文檔
doc.save("modified-document.docx");
```

在此範例中，我們在文件中將“text-to-replace”替換為“new-string”。

## 使用舊訂單

執行尋找和取代操作時可以使用舊順序。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//建立 FindReplaceOptions 實例並將 UseLegacyOrder 設為 true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

//替換文字時使用選項
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

//儲存修改後的文檔
doc.save("modified-document.docx");
```

這允許您使用舊順序進行查找和替換操作。

## 替換表格中的文本

您可以在 Word 文件的表格中尋找和取代文字。

```java
//載入文檔
Document doc = new Document("your-document.docx");

//取得特定的表格（例如第一個表格）
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//使用 FindReplaceOptions 替換表中的文字
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

//儲存修改後的文檔
doc.save("modified-document.docx");
```

這允許您專門在表格內執行文字替換。

## 結論

Aspose.Words for Java 提供了在 Word 文件中尋找和取代文字的全面功能。無論您需要使用正規表示式、欄位操作或自訂求值器執行簡單的文字替換還是更進階的操作，Aspose.Words for Java 都能滿足您的需求。請務必探索 Aspose 提供的大量文件和範例，以充分利用這個強大的 Java 庫的潛力。

## 常見問題解答

### 如何下載 Java 版 Aspose.Words？

您可以透過造訪網站下載 Aspose.Words for Java[這個連結](https://releases.aspose.com/words/java/).

### 我可以使用正規表示式進行文字替換嗎？

是的，您可以在 Aspose.Words for Java 中使用正規表示式進行文字替換。這使您可以執行更高級、更靈活的查找和替換操作。

### 如何在替換過程中忽略欄位內的文字？

若要在替換期間忽略欄位內的文本，您可以設定`IgnoreFields`的財產`FindReplaceOptions`到`true`。這可確保欄位內的文字（例如合併欄位）不會被取代。

### 我可以替換頁首和頁尾內的文字嗎？

是的，您可以取代 Word 文件的頁首和頁尾內的文字。只需存取適當的頁首或頁尾並使用`replace`方法與所需的`FindReplaceOptions`.

### UseLegacyOrder 選項的用途是什麼？

這`UseLegacyOrder`選項中`FindReplaceOptions`允許您在執行尋找和取代操作時使用舊順序。這在某些需要遺留訂單行為的場景中非常有用。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
