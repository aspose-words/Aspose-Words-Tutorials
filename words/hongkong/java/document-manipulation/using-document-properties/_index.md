---
title: 在 Aspose.Words for Java 中使用文件屬性
linktitle: 使用文件屬性
second_title: Aspose.Words Java 文件處理 API
description: 使用 Aspose.Words for Java 最佳化文件管理。在這個綜合教學中學習如何使用文件屬性、新增自訂元資料等。
weight: 32
url: /zh-hant/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中使用文件屬性


## 文件屬性簡介

文檔屬性是任何文件的重要組成部分。它們提供有關文件本身的附加信息，例如標題、作者、主題、關鍵字等。在 Aspose.Words for Java 中，您可以操作內建和自訂文件屬性。

## 枚舉文檔屬性

### 內建屬性

若要檢索和使用內建文件屬性，您可以使用下列程式碼片段：

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

此程式碼將顯示文件的名稱和內建屬性，包括「標題」、「作者」和「關鍵字」等屬性。

### 自訂屬性

若要使用自訂文件屬性，您可以使用以下程式碼片段：

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

此程式碼片段示範如何新增自訂文件屬性，包括布林值、字串、日期、修訂號和數值。

## 刪除文檔屬性

若要刪除特定文檔屬性，可以使用下列程式碼：

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

此程式碼從文件中刪除自訂屬性「授權日期」。

## 配置內容連結

在某些情況下，您可能希望在文件中建立連結。您可以這樣做：

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    //新增連結到內容屬性。
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

此程式碼片段示範如何在文件中建立書籤並新增連結到該書籤的自訂文件屬性。

## 測量單位之間的轉換

在Aspose.Words for Java中，您可以輕鬆轉換測量單位。以下是如何執行此操作的範例：

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    //設定頁邊距（以英吋為單位）。
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

此程式碼片段透過將各種邊距和距離（以英吋為單位）轉換為點來設定它們。

## 使用控製字符

處理文字時控製字元很有用。以下是替換文字中控製字元的方法：

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    //將“\r”控製字元替換為“\r\n”。
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

在此範例中，我們替換回車符 (`\r`），回車後跟換行符（`\r\n`）。

## 結論

文件屬性在 Aspose.Words for Java 中有效管理和組織文件方面發揮著重要作用。無論是使用內建屬性、自訂屬性或使用控製字符，您都可以使用一系列工具來增強文件管理功能。

## 常見問題解答

### 如何存取內建文件屬性？

要存取 Aspose.Words for Java 中的內建文件屬性，您可以使用`getBuiltInDocumentProperties`方法上的`Document`目的。此方法傳回您可以迭代的內建屬性的集合。

### 我可以為文件新增自訂文件屬性嗎？

是的，您可以使用以下命令將自訂文件屬性新增至文件：`CustomDocumentProperties`收藏。您可以使用各種資料類型定義自訂屬性，包括字串、布林值、日期和數值。

### 如何刪除特定的自訂文件屬性？

若要刪除特定的自訂文件屬性，您可以使用`remove`方法上的`CustomDocumentProperties`集合，將要刪除的屬性的名稱作為參數傳遞。

### 連結到文件內容的目的是什麼？

連結到文件中的內容可讓您建立對文件特定部分的動態引用。這對於建立互動式文件或各部分之間的交叉引用非常有用。

### 如何在 Aspose.Words for Java 中的不同測量單位之間進行轉換？

您可以使用 Aspose.Words for Java 在不同的測量單位之間進行轉換`ConvertUtil`班級。它提供了將英吋轉換為點、點轉換為公分等單位的方法。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
