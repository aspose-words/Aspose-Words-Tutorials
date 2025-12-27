---
date: 2025-12-27
description: 學習如何設定方向、載入 txt 檔案、修剪空格，並使用 Aspose.Words for Java 將 txt 轉換為 docx。
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 設定文字方向並載入文字檔
url: /zh-hant/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何設定方向並載入文字檔案（使用 Aspose.Words for Java）

## 使用 Aspose.Words for Java 載入文字檔案的簡介

在本指南中，您將了解 **如何設定方向** 於載入純文字文件時的操作，並看到使用 Aspose.Words for Java **載入 txt**、**修剪空格**、以及 **將 txt 轉換為 docx** 的實用方法。無論您是建立文件轉換服務，或需要對清單偵測進行細緻控制，本教學都會以清晰說明與可直接執行的程式碼，逐步帶您完成每個步驟。

## 快速解答
- **如何為已載入的 TXT 檔案設定文字方向？** 使用 `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` 或指定 `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`。
- **Aspose.Words 能否偵測純文字中的編號清單？** 可以 – 在 `TxtLoadOptions` 中啟用 `DetectNumberingWithWhitespaces`。
- **如何修剪前置與後置空格？** 設定 `TxtLeadingSpacesOptions.TRIM` 與 `TxtTrailingSpacesOptions.TRIM`。
- **是否能以一行程式碼將 TXT 檔案轉換為 DOCX？** 使用 `TxtLoadOptions` 載入 TXT，然後呼叫 `Document.save("output.docx")`。
- **需要哪個 Java 版本？** Java 8 以上即可滿足 Aspose.Words 24.x 的需求。

## 什麼是 Aspose.Words 中的「設定方向」？

當文字檔案包含從右至左的文字（例如希伯來文或阿拉伯文）時，函式庫必須知道閱讀順序。`DocumentDirection` 列舉讓您 **手動設定方向**，或讓 Aspose 自動偵測，以確保正確的版面配置與雙向文字格式化。

## 為何使用 Aspose.Words 載入 TXT 檔案？

- **精確的清單偵測** – 處理編號、項目符號以及以空白分隔的清單。  
- **細緻的空格處理** – 修剪或保留前置/後置空格。  
- **自動文字方向偵測** – 適用於多語言文件。  
- **一步完成轉換** – 載入 `.txt` 後即可儲存為 `.docx`、`.pdf` 或任何支援的格式。

## 先決條件
- Java 8 或更新版本。  
- Aspose.Words for Java 函式庫（將 Maven/Gradle 依賴或 JAR 加入專案）。  
- 具備 Java I/O 串流的基本知識。

## 逐步指南

### 步驟 1：偵測清單（如何載入 txt）

為了載入文字文件並自動偵測清單，建立 `TxtLoadOptions` 實例並啟用清單偵測。以下程式碼展示了多種清單樣式，並啟用了支援空白的編號方式。

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Pro tip:** 若您只需要基本的清單偵測，可省略空白選項 – Aspose 仍會辨識標準的 `1.` 與 `1)` 形式。

### 步驟 2：處理空格選項（如何修剪空格）

前置與後置空格常會造成格式錯亂。使用 `TxtLeadingSpacesOptions` 與 `TxtTrailingSpacesOptions` 來控制此行為。

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

> **Why it matters:** 修剪空格可防止產生的 DOCX 出現不必要的縮排，使文件看起來乾淨，且無需手動後處理。

### 步驟 3：控制文字方向（如何設定方向）

對於從右至左的語言，請在載入前先設定文件方向。以下範例載入希伯來文文字檔，並印出 bidi 標誌以確認方向。

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

> **Common pitfall:** 忘記設定 `DocumentDirection` 會導致阿拉伯文/希伯來文文字顯示錯亂，字元順序顛倒。

### 完整的載入文字檔案範例程式碼（使用 Aspose.Words for Java）

以下提供完整、可直接執行的來源碼，結合清單偵測、空格處理與方向控制。您可以將其複製貼上至單一類別，分別執行三個測試方法。

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## 常見問題與解決方案
| Issue | Cause | Fix |
|-------|-------|-----|
| Lists not detected | `DetectNumberingWithWhitespaces` left `false` for whitespace‑delimited lists | Enable `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Extra indentation after loading | Leading spaces were preserved | Set `TxtLeadingSpacesOptions.TRIM` |
| Hebrew text appears reversed | Document direction not set or set to `LEFT_TO_RIGHT` | Use `DocumentDirection.AUTO` or `RIGHT_TO_LEFT` |
| Output DOCX is empty | Input stream was not reset before second load | Re‑create `ByteArrayInputStream` for each load call |

## 常見問答

### Q: 什麼是 Aspose.Words for Java？
**A:** Aspose.Words for Java 是一套功能強大的文件處理函式庫，讓開發人員能在 Java 應用程式中以程式方式建立、操作與轉換 Word 文件。它支援從簡單的文字載入到複雜的格式設定與轉換等廣泛功能。

### Q: 如何開始使用 Aspose.Words for Java？
**A:** 1. 下載並安裝 Aspose.Words for Java 函式庫。2. 參考 [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) 取得詳細說明與範例。3. 探索範例程式碼與教學，以熟悉函式庫的使用方式。

### Q: 如何使用 Aspose.Words for Java 載入文字文件？
**A:** 使用 `TxtLoadOptions` 類別搭配 `Document` 建構子。可依需求設定清單偵測、空格處理或文字方向，詳情請參考上述逐步說明。

### Q: 是否可以將已載入的文字文件轉換為其他格式？
**A:** 可以。將 TXT 檔載入為 `Document` 物件後，呼叫 `doc.save("output.pdf")`、`doc.save("output.docx")` 或任何其他支援的格式即可。

### Q: 如何處理載入文字文件中的空格？
**A:** 透過 `TxtLeadingSpacesOptions` 與 `TxtTrailingSpacesOptions` 控制前置與後置空格。將其設定為 `TRIM` 可移除不必要的空白，若需保留原始間距則設定為 `PRESERVE`。

### Q: 文字方向在 Aspose.Words for Java 中有何重要性？
**A:** 文字方向確保從右至左腳本（如希伯來文、阿拉伯文）正確顯示。設定 `DocumentDirection` 後，雙向文字即可在最終文件中正確排版。

### Q: 哪裡可以找到更多 Aspose.Words for Java 的資源與支援？
**A:** 前往 [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) 取得 API 參考、程式碼範例與詳細指南。您亦可加入 Aspose 社群論壇或直接聯繫 Aspose 支援團隊取得協助。

### Q: Aspose.Words for Java 適合商業專案嗎？
**A:** 適用。它提供個人與商業授權方案，您可依需求選擇合適的授權類型。請於 Aspose 官方網站查閱授權條款，以決定最適合您專案的方案。

## 結論
您現在已擁有完整的工具箱，可在使用 Aspose.Words for Java 將純文字轉換為豐富的 Word 文件時，**載入 txt 檔案**、**偵測清單**、**修剪空格**，以及 **設定方向**。將這些模式套用於自動化文件工作流程、提升多語言支援，並確保每次輸出皆乾淨、專業。

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}