---
date: 2026-01-16
description: 了解如何將英吋轉換為點、使用 Java 讀取文件元資料、使用 Java 新增自訂屬性，以及使用 Aspose.Words for Java
  設定頁面邊距。
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: 將英吋轉換為點 – 在 Aspose.Words for Java 中使用文件屬性
url: /zh-hant/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 將英吋轉換為點 – 在 Aspose.Words for Java 中使用文件屬性

在本教學中，您將了解如何在設定頁邊距時 **將英吋轉換為點**、在 Java 中讀取文件中繼資料、加入自訂屬性，以及使用 Aspose.Words for Java 處理內建文件屬性。無論是產生報告、發票或法律文件，精通這些技巧都能讓您對 Word 檔案的外觀與中繼資料進行細緻的控制。

## 快速解答
- **如何將英吋轉換為點？** 使用 Aspose.Words 的 `ConvertUtil.inchToPoint(value)`。
- **我可以在 Java 中讀取文件中繼資料嗎？** 可以 – 呼叫 `doc.getBuiltInDocumentProperties()` 或 `doc.getCustomDocumentProperties()`。
- **如何在 Java 中加入自訂屬性？** 使用 `doc.getCustomDocumentProperties().add(name, value)`。
- **哪個方法以點為單位設定頁邊距？** `PageSetup.setTopMargin`、`setBottomMargin` 等接受點值。
- **是否支援連結至書籤？** 支援 – 在自訂屬性集合上使用 `addLinkToContent`。

## 文件屬性簡介

文件屬性是任何 Word 檔案的重要組成部分。它們儲存諸如標題、作者、主旨、關鍵字以及您在後續處理所需的任何自訂中繼資料等資訊。在 Aspose.Words for Java 中，您可以操作內建與自訂文件屬性，亦可透過轉換測量單位（例如 **將英吋轉換為點**）來控制版面細節，如頁邊距。

## 什麼是「將英吋轉換為點」？

在 Word 中，版面測量以點為單位表示（1 點 = 1/72 英吋）。將英吋轉換為點可讓您使用熟悉的英制單位來定義頁邊距、縮排與間距，而 API 在內部則以點為單位運作。

## 為什麼要在 Java 中管理文件中繼資料？

嵌入中繼資料可讓搜尋、分類與自動化工作流程變得更簡單。例如，您可以為合約加上「Authorized」標記，或儲存修訂號碼以作稽核追蹤。以程式方式讀寫這些資訊，可確保大量文件批次的一致性。

## 前置條件
- Java 17+（或相容的 JDK）
- 已在專案中加入 Aspose.Words for Java 套件（Maven/Gradle）
- 一個範例 `.docx` 檔案（例如 `Properties.docx`），放置於可存取的目錄中

## 步驟說明

### 列舉內建文件屬性
以下是一個簡單的測試程式，會開啟文件並列印所有內建屬性，如 Title、Author 與 Keywords。

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

> **小技巧：** 使用此程式碼片段來驗證先前步驟中您的中繼資料是否正確寫入。

### 新增自訂文件屬性（add custom properties java）
自訂屬性讓您儲存任何需要的資料類型——布林值、字串、日期、數字等。

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

> **為什麼重要：** 加入像 **Authorized** 這樣的旗標，可在不更改文件內容的情況下推動後續的批准工作流程。

### 移除自訂屬性
```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### 設定內容連結（書籤連結）
您可以建立書籤，然後新增指向該書籤的自訂屬性，從而實現動態交叉參照。

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

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### 單位轉換（設定頁邊距 java）
這裡正是主要關鍵詞發揮作用的地方。我們先以英吋設定頁邊距，然後使用 `ConvertUtil` **將英吋轉換為點**。

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **注意：** `ConvertUtil` 亦提供 `pointToInch`、`mmToPoint` 等方法，以彈性處理版面配置。

### 使用控制字元（read document metadata java）
控制字元可協助清理文字串流。此範例將回車 (`\r`) 替換為 Windows 換行序列 (`\r\n`)。

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## 常見問題與解決方案
| 問題 | 原因 | 解決方式 |
|------|------|----------|
| 轉換後頁邊距顯示不正確 | 使用了錯誤的單位（例如使用公分而非英吋） | 確認對英吋值呼叫 `ConvertUtil.inchToPoint` |
| 自訂屬性未出現 | 屬性是在儲存文件之後才加入的 | 在加入屬性後呼叫 `doc.save(...)` |
| 書籤連結失效 | 書籤名稱拼寫錯誤 | 確保在 `addLinkToContent` 中的書籤名稱完全相符 |

## 常見問答

### 如何存取內建文件屬性？

要在 Aspose.Words for Java 中存取內建文件屬性，您可以對 `Document` 物件使用 `getBuiltInDocumentProperties` 方法。此方法會回傳內建屬性的集合，您可以遍歷它們。

### 我可以為文件新增自訂文件屬性嗎？

可以，您可以使用 `CustomDocumentProperties` 集合為文件新增自訂文件屬性。您可以定義包含字串、布林值、日期與數值等各種資料類型的自訂屬性。

### 如何移除特定的自訂文件屬性？

若要移除特定的自訂文件屬性，可在 `CustomDocumentProperties` 集合上使用 `remove` 方法，並傳入欲移除的屬性名稱作為參數。

### 在文件內連結內容的目的為何？

在文件內連結內容可讓您建立指向文件特定部分的動態參照。這對於製作互動式文件或章節之間的交叉參照非常有用。

### 如何在 Aspose.Words for Java 中於不同測量單位間轉換？

您可以透過使用 `ConvertUtil` 類別，在 Aspose.Words for Java 中於不同測量單位間進行轉換。它提供將英吋轉換為點、點轉換為公分等方法。

## 常見問題

**Q: 如何在不載入整個檔案的情況下讀取 Java 文件中繼資料？**  
A: 使用 `DocumentInfo` 取得核心屬性，而無需完整載入文件內容。

**Q: 我可以以程式方式在 Java 中為現有文件設定頁邊距嗎？**  
A: 可以——開啟文件後，修改 `PageSetup` 的邊距（如有需要先將英吋轉換為點），最後儲存。

**Q: 能否將自訂屬性匯出為 PDF 中繼資料？**  
A: 在儲存為 PDF 時，Aspose.Words 會自動將自訂文件屬性對映至 PDF 的自訂中繼資料。

**Q: 控制字元會影響 PDF 轉換嗎？**  
A: 轉換過程中會保留它們；但為了保持一致性，您可能需要正規化換行字元。

**Q: `ConvertUtil` 需要哪個版本的 Aspose.Words？**  
A: `ConvertUtil` 從 Aspose.Words 16.5 版起即已提供，任何較新的版本皆支援。

## 結論

透過精通 **將英吋轉換為點**、在 Java 中讀取文件中繼資料以及新增自訂屬性，您即可完整掌控 Word 檔案的視覺版面與隱藏資料。這些功能讓您能構建自動化文件流程、落實合規要求，並製作豐富格式的報告——全部皆使用 Aspose.Words for Java。

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}