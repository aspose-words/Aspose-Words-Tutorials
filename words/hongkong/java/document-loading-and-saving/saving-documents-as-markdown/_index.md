---
"description": "了解如何使用 Aspose.Words for Java 將 Word 文件轉換為 Markdown。本逐步指南涵蓋表格對齊、影像處理等內容。"
"linktitle": "將文件儲存為 Markdown"
"second_title": "Aspose.Words Java文件處理API"
"title": "在 Aspose.Words for Java 中將文件儲存為 Markdown"
"url": "/zh-hant/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中將文件儲存為 Markdown


## Aspose.Words for Java 中將文件儲存為 Markdown 的簡介

在本逐步指南中，我們將示範如何使用 Aspose.Words for Java 將文件儲存為 Markdown。 Markdown 是一種輕量級標記語言，通常用於格式化文字文件。使用 Aspose.Words for Java，您可以輕鬆地將 Word 文件轉換為 Markdown 格式。我們將介紹保存 Markdown 文件的不同方面，包括表格內容對齊和處理圖像。

## 先決條件

在開始之前，請確保您符合以下先決條件：

- 您的系統上安裝了 Java 開發工具包 (JDK)。
- Java 函式庫的 Aspose.Words。您可以從下載 [這裡](https://releases。aspose.com/words/java/).

## 步驟 1：建立 Word 文件

讓我們先建立一個 Word 文檔，然後將其轉換為 Markdown 格式。您可以根據您的要求自訂此文件。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// 插入包含兩個儲存格的表格
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// 將文件儲存為 Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

在這個範例中，我們建立一個包含兩個儲存格的簡單表格，並設定這些儲存格內段落的對齊方式。然後，我們使用 `MarkdownSaveOptions`。

## 步驟2：自訂表格內容對齊方式

Aspose.Words for Java 可讓您在儲存為 Markdown 時自訂表格內容的對齊方式。您可以將表格內容左對齊、右對齊、居中對齊，或根據每個表格列中的第一個段落自動決定。

自訂表格內容對齊的方法如下：

```java
// 將表格內容對齊方式設定為左對齊
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// 將表格內容對齊方式設定為右對齊
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// 將表格內容對齊方式設定為居中
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// 將表格內容對齊方式設定為自動（由第一段決定）
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

透過改變 `TableContentAlignment` 屬性，您可以控制轉換為 Markdown 時表格內的內容如何對齊。

## 步驟3：處理影像

要在 Markdown 文件中包含映像，您需要指定映像所在的資料夾。 Aspose.Words for Java 允許您在 `MarkdownSaveOptions`。

以下是設定影像資料夾並儲存包含影像的文件的方法：

```java
// 載入包含映像的文檔
Document doc = new Document("document_with_images.docx");

// 設定影像資料夾路徑
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// 儲存包含影像的文檔
doc.save("document_with_images.md", saveOptions);
```

確保更換 `"document_with_images.docx"` 包含圖像的 Word 文件的路徑和 `"images_folder/"` 使用儲存影像的資料夾的實際路徑。

## 在 Aspose.Words for Java 中將文件儲存為 Markdown 的完整原始碼

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// 使表格內的所有段落對齊。
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// 在這種情況下，對齊將取自對應表格列中的第一個段落。
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## 結論

在本指南中，我們探討如何使用 Aspose.Words for Java 將文件儲存為 Markdown。我們介紹如何建立 Word 文件、自訂表格內容對齊以及處理 Markdown 文件中的圖像。現在您可以有效地將 Word 文件轉換為 Markdown 格式，使其適用於各種發布平台和文件需求。

## 常見問題解答

### 如何安裝 Aspose.Words for Java？

可以透過將程式庫包含在 Java 專案中包含來安裝 Aspose.Words for Java。您可以從 [這裡](https://releases.aspose.com/words/java/) 並按照文件中提供的安裝說明進行操作。

### 我可以將包含表格和圖片的複雜 Word 文件轉換為 Markdown 嗎？

是的，Aspose.Words for Java 支援將包含表格、圖片和各種格式元素的複雜 Word 文件轉換為 Markdown。您可以根據文件的複雜度自訂 Markdown 輸出。

### 如何處理 Markdown 文件中的圖片？

要在 Markdown 文件中包含圖像，請使用 `setImagesFolder` 方法 `MarkdownSaveOptions`。確保圖像檔案儲存在指定的資料夾中，Aspose.Words for Java 將相應地處理圖像引用。

### 是否有適用於 Java 的 Aspose.Words 試用版？

是的，您可以從 Aspose 網站取得 Aspose.Words for Java 的試用版。試用版可讓您在購買許可證之前評估該庫的功能。

### 在哪裡可以找到更多範例和文件？

有關 Aspose.Words for Java 的更多範例、文件和詳細信息，請訪問 [文件](https://reference。aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}