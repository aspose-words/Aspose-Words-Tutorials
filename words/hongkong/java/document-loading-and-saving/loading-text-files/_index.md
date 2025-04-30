---
"description": "釋放 Aspose.Words for Java 的強大功能。學習載入文字文件、管理清單、處理空格和控製文字方向。"
"linktitle": "使用以下方式載入文字文件"
"second_title": "Aspose.Words Java文件處理API"
"title": "使用 Aspose.Words for Java 載入文字文件"
"url": "/zh-hant/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for Java 載入文字文件


## 使用 Aspose.Words for Java 載入文字檔的簡介

在本指南中，我們將探討如何使用 Aspose.Words for Java 載入文字檔案並將其作為 Word 文件進行操作。我們將涵蓋檢測清單、處理空格和控製文字方向等各個方面。

## 步驟 1：檢測列表

要載入文字文件並偵測列表，您可以按照以下步驟操作：

```java
// 建立一個字串形式的純文字文檔，其中某些部分可以解釋為列表。
// 載入後，Aspose.Words 將始終偵測前三個列表，
// 並且在載入後會為它們建立 List 物件。
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
// 第四個列表，列表編號和列表項目內容之間有空格，
// 只有當 LoadOptions 物件中的「DetectNumberingWithWhitespaces」設定為 true 時才會被偵測為列表，
// 以避免以數字開頭的段落被錯誤地檢測為清單。
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// 使用 LoadOptions 作為參數載入文件並驗證結果。
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

此程式碼示範如何載入具有各種清單格式的文字文件並使用 `DetectNumberingWithWhitespaces` 選項來正確檢測清單。

## 第 2 步：處理空間選項

若要在載入文字文件時控制前導空格和尾隨空格，可以使用以下程式碼：

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

在此範例中，我們載入文字文件並使用以下方法修剪前導和尾隨空格 `TxtLeadingSpacesOptions.TRIM` 和 `TxtTrailingSpacesOptions。TRIM`.

## 步驟3：控製文字方向

若要在載入文字文件時指定文字方向，可以使用以下程式碼：

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

此程式碼將文件方向設定為自動檢測（`DocumentDirection.AUTO`) 並載入包含希伯來文本的文本文檔。您可以根據需要調整文件方向。

## 使用 Aspose.Words for Java 載入文字檔案的完整原始碼

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// 建立一個字串形式的純文字文檔，其中某些部分可以解釋為列表。
	// 載入後，Aspose.Words 將始終偵測前三個列表，
	// 並且在載入後會為它們建立 List 物件。
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
	// 第四個列表，列表編號和列表項目內容之間有空格，
	// 只有當 LoadOptions 物件中的「DetectNumberingWithWhitespaces」設定為 true 時才會被偵測為列表，
	// 以避免以數字開頭的段落被錯誤地檢測為清單。
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// 使用 LoadOptions 作為參數載入文件並驗證結果。
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

## 結論

在本指南中，我們探討如何使用 Aspose.Words for Java 載入文字檔案、偵測清單、處理空格以及控製文字方向。這些技術可讓您在 Java 應用程式中有效地操作文字文件。

## 常見問題解答

### 什麼是 Aspose.Words for Java？

Aspose.Words for Java 是一個強大的文件處理庫，可讓開發人員在 Java 應用程式中以程式設計方式建立、操作和轉換 Word 文件。它提供了處理文字、表格、圖像和其他文件元素的廣泛功能。

### 如何開始使用 Aspose.Words for Java？

若要開始使用 Aspose.Words for Java，請依照下列步驟操作：
1. 下載並安裝 Aspose.Words for Java 函式庫。
2. 請參閱以下文檔 [Aspose.Words for Java API參考](https://reference.aspose.com/words/java/) 了解詳細資訊和範例。
3. 探索範例程式碼和教學課程以了解如何有效地使用該程式庫。

### 如何使用 Aspose.Words for Java 載入文字文件？

要使用 Aspose.Words for Java 載入文字文檔，您可以使用 `TxtLoadOptions` 類和 `Document` 班級。確保根據需要指定適當的選項來處理空間和文字方向。請參閱本文中的逐步指南以取得詳細範例。

### 我可以將載入的文字文檔轉換為其他格式嗎？

是的，Aspose.Words for Java 可讓您將載入的文字文件轉換為各種格式，包括 DOCX、PDF 等。您可以使用 `Document` 類別來執行轉換。查看文件以了解具體的轉換範例。

### 如何處理載入的文字文檔中的空格？

您可以使用以下方式控制載入的文字文件中前導空格和尾隨空格的處理方式 `TxtLoadOptions`。選項如下 `TxtLeadingSpacesOptions` 和 `TxtTrailingSpacesOptions` 允許您根據需要修剪或保留空間。請參閱本指南中的「處理空間選項」部分以取得範例。

### Aspose.Words for Java 中的文字方向有何意義？

對於包含混合腳本或語言（例如希伯來語或阿拉伯語）的文檔，文字方向至關重要。 Aspose.Words for Java 提供了指定文字方向的選項，確保這些語言的文字正確呈現和格式化。本指南中的「控製文字方向」部分示範如何設定文字方向。

### 在哪裡可以找到更多有關 Aspose.Words for Java 的資源和支援？

如需更多資源、文件和支持，請訪問 [Aspose.Words for Java 文檔](https://reference.aspose.com/words/java/)。您也可以參與 Aspose.Words 社群論壇或聯絡 Aspose 支援以取得特定問題或諮詢的協助。

### Aspose.Words for Java 適合商業專案嗎？

是的，Aspose.Words for Java 適用於個人和商業專案。它提供許可選項以適應各種使用場景。請務必查看 Aspose 網站上的授權條款和定價，以便為您的專案選擇合適的授權。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}