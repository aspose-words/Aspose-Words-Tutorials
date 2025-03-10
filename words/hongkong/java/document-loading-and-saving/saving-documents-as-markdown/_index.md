---
title: 在 Aspose.Words for Java 中將文件儲存為 Markdown
linktitle: 將文件另存為 Markdown
second_title: Aspose.Words Java 文件處理 API
description: 了解如何使用 Aspose.Words for Java 將 Word 文件轉換為 Markdown。本逐步指南涵蓋表格對齊、影像處理等內容。
weight: 18
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中將文件儲存為 Markdown


## 在 Aspose.Words for Java 中將文件儲存為 Markdown 簡介

在本逐步指南中，我們將示範如何使用 Aspose.Words for Java 將文件儲存為 Markdown。 Markdown 是一種輕量級標記語言，通常用於格式化文字文件。使用 Aspose.Words for Java，您可以輕鬆地將 Word 文件轉換為 Markdown 格式。我們將介紹保存 Markdown 文件的不同方面，包括表格內容對齊和處理圖像。

## 先決條件

在開始之前，請確保您具備以下先決條件：

- 您的系統上安裝了 Java 開發工具包 (JDK)。
-  Aspose.Words for Java 函式庫。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/).

## 第 1 步：建立 Word 文檔

我們首先建立一個 Word 文檔，稍後將其轉換為 Markdown 格式。您可以根據您的要求自訂此文件。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//插入包含兩個儲存格的表格
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

//將文件另存為 Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

在此範例中，我們建立一個包含兩個儲存格的簡單表格，並設定這些儲存格內段落的對齊方式。然後，我們使用以下命令將文件另存為 Markdown`MarkdownSaveOptions`.

## 第 2 步：自訂表格內容對齊方式

Aspose.Words for Java 讓您在另存為 Markdown 時自訂表格內容的對齊方式。您可以將表格內容左對齊、右對齊、居中對齊，或根據每個表格列中的第一個段落自動決定。

以下是自訂表格內容對齊方式的方法：

```java
//設定表格內容左對齊
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

//設定表格內容右對齊
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

//設定表格內容居中對齊
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//將表格內容對齊設定為自動（由第一段決定）
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

透過改變`TableContentAlignment`屬性，您可以控制轉換為 Markdown 時表格內內容的對齊方式。

## 第 3 步：處理影像

要在 Markdown 文件中包含映像，您需要指定映像所在的資料夾。 Aspose.Words for Java 允許您將圖像資料夾設定在`MarkdownSaveOptions`.

以下是如何設定圖像資料夾並保存帶有圖像的文件：

```java
//載入包含映像的文檔
Document doc = new Document("document_with_images.docx");

//設定圖片資料夾路徑
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

//儲存帶有影像的文檔
doc.save("document_with_images.md", saveOptions);
```

確保更換`"document_with_images.docx"`包含圖像的 Word 文件的路徑和`"images_folder/"`與儲存影像的資料夾的實際路徑。

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
	//使表格內的所有段落對齊。
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	//在這種情況下，對齊方式將從對應表列的第一段中取得。
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

在本指南中，我們探討如何使用 Aspose.Words for Java 將文件儲存為 Markdown。我們介紹了 Word 文件的建立、自訂表格內容對齊以及處理 Markdown 文件中的圖像。現在您可以有效地將 Word 文件轉換為 Markdown 格式，使其適合各種發布平台和文件需求。

## 常見問題解答

### 如何安裝 Aspose.Words for Java？

可以透過將程式庫包含在 Java 專案中來安裝 Aspose.Words for Java。您可以從以下位置下載該程式庫[這裡](https://releases.aspose.com/words/java/)並按照文件中提供的安裝說明進行操作。

### 我可以將包含表格和圖片的複雜 Word 文件轉換為 Markdown 嗎？

是的，Aspose.Words for Java 支援將包含表格、圖片和各種格式元素的複雜 Word 文件轉換為 Markdown。您可以根據文件的複雜度自訂 Markdown 輸出。

### 如何處理 Markdown 文件中的圖片？

若要在 Markdown 檔案中包含映像，請使用下列命令設定映像資料夾路徑`setImagesFolder`中的方法`MarkdownSaveOptions`。確保圖像檔案儲存在指定的資料夾中，Aspose.Words for Java 將相應地處理圖像引用。

### 是否有 Aspose.Words for Java 的試用版？

是的，您可以從 Aspose 網站取得 Aspose.Words for Java 的試用版。試用版可讓您在購買許可證之前評估庫的功能。

### 在哪裡可以找到更多範例和文件？

有關 Aspose.Words for Java 的更多範例、文件和詳細信息，請訪問[文件](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
