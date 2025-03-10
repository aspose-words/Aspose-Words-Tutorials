---
title: 在 Aspose.Words for Java 中連接和附加文檔
linktitle: 加入和附加文檔
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 輕鬆加入和追加文件。保留格式、管理頁首頁尾等。
weight: 30
url: /zh-hant/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中連接和附加文檔


## Aspose.Words for Java 中連接和附加文件簡介

在本教學中，我們將探討如何使用 Aspose.Words for Java 函式庫加入和附加文件。您將學習如何無縫合併多個文檔，同時保留格式和結構。

## 先決條件

在開始之前，請確保您的 Java 專案中已設定 Aspose.Words for Java API。

## 文件連線選項

### 簡單追加

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### 新增導入格式選項

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### 附加到空白文檔

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### 附加頁碼轉換

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); //轉換 NUMPAGES 字段
dstDoc.updatePageLayout(); //更新頁面佈局以獲得正確的編號
```

## 處理不同的頁面設置

附加具有不同頁面設定的文檔時：

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
//確保頁面設定設定與目標文件匹配
```

## 連接不同樣式的文檔

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## 聰明的風格行為

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## 使用 DocumentBuilder 插入文檔

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## 保留源編號

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## 處理文字框

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## 管理頁首和頁尾

### 連結頁首和頁尾

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### 取消頁首和頁尾的鏈接

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## 結論

Aspose.Words for Java 提供了靈活且強大的工具來連接和附加文檔，無論您需要維護格式、處理不同的頁面設定還是管理頁首和頁尾。嘗試使用這些技術來滿足您的特定文件處理需求。

## 常見問題解答

### 如何無縫拼接不同樣式的文件？

若要加入不同樣式的文檔，請使用`ImportFormatMode.USE_DESTINATION_STYLES`追加時。

### 附加文件時可以保留頁碼嗎？

是的，您可以使用以下命令保留頁碼`convertNumPageFieldsToPageRef`方法並更新頁面佈局。

### 什麼是聰明風格行為？

智慧型樣式行為有助於在附加文件時保持一致的樣式。與它一起使用`ImportFormatOptions`為了更好的結果。

### 附加文件時如何處理文字方塊？

放`importFormatOptions.setIgnoreTextBoxes(false)`在附加過程中包含文字方塊。

### 如果我想在文件之間連結/取消連結頁首和頁尾怎麼辦？

您可以將頁首和頁尾連結到`linkToPrevious(true)`或取消它們的鏈接`linkToPrevious(false)`根據需要。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
