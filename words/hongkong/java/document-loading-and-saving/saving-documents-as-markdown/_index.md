---
date: 2025-12-22
description: 了解如何使用 Aspose.Words for Java 將 Word 文件轉換為 Markdown，以匯出 Markdown。本分步指南涵蓋表格對齊、圖像處理等內容。
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 匯出 Markdown
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words for Java 匯出 Markdown

## 在 Aspose.Words for Java 中匯出 Markdown 的簡介

## 快速答案
- **保存為 Markdown 的主要類別是什麼？** `MarkdownSaveOptions`
- **圖片能否自動嵌入？** 是 – 透過 `setImagesFolder` 設定圖片資料夾。
- **如何控制表格對齊方式？** 使用 `TableContentAlignment`（LEFT、RIGHT、CENTER、AUTO）。
- **最低需求是什麼？** JDK 8+ 以及 Aspose.Words for Java 程式庫。
- **是否提供試用版？** 有，請從 Aspose 官方網站下載。

## 什麼是「如何匯出 markdown」？
匯出 markdown 指的是將富文字 Word 文件（`.docx`）轉換為純文字 `.md` 檔案，並以 Markdown 語法保留標題、表格與圖片。

## 為什麼使用 Aspose.Words for Java 來轉換含圖片的 docx？
Aspose.Words 能處理複雜版面、內嵌圖片與表格結構，且不會失真。它亦提供對 Markdown 輸出的精細控制，例如表格對齊與圖片資料夾管理。

## 先決條件

- 已在系統上安裝 Java Development Kit（JDK）。
- Aspose.Words for Java 程式庫。您可從 [here](https://releases.aspose.com/words/java/) 下載。

## 步驟 1：建立簡易 Word 文件

首先，我們會建立一個包含表格的小文件。之後可示範 **自訂表格對齊**。

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

在上述程式碼片段中，我們：

1. 建立新的 `Document`。
2. 使用 `DocumentBuilder` 插入一個兩格的表格。
3. 在每個儲存格內套用 **右對齊** 與 **置中** 段落對齊。
4. 使用 `MarkdownSaveOptions` 將檔案儲存為 Markdown。

## 步驟 2：自訂表格內容對齊

Aspose.Words 讓您決定表格儲存格在最終 Markdown 中的呈現方式。您可以強制左、右、置中對齊，或讓程式庫根據每欄第一段落自動判斷。

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

透過切換 `TableContentAlignment` 屬性，即可控制 Markdown 輸出的 **自訂表格對齊**。

## 步驟 3：匯出至 markdown 時處理圖片

當文件內含圖片時，您會希望這些圖片在產生的 `.md` 檔案中正確顯示。請設定 Aspose.Words 輸出擷取圖片的資料夾。

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

將 `"document_with_images.docx"` 替換為您的來源檔案路徑，將 `"images_folder/"` 替換為您希望儲存圖片的目錄。產生的 Markdown 會包含指向此資料夾的圖片連結，讓您能順暢 **在 markdown 中處理圖片**。

## 完整來源程式碼：在 Aspose.Words for Java 中將文件儲存為 Markdown

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## 常見問題與解決方案

| 問題 | 解決方案 |
|-------|----------|
| 圖片未出現在 `.md` 檔案中 | 驗證 `setImagesFolder` 指向可寫入的目錄，且在產生的 Markdown 中正確引用該資料夾。 |
| 表格對齊顯示異常 | 使用 `TableContentAlignment.AUTO` 讓 Aspose.Words 根據每欄第一段落推斷最佳對齊方式。 |
| 輸出檔案為空 | 確保在呼叫 `save` 之前，`Document` 物件實際包含內容。 |

## 常見問答

**Q: 如何安裝 Aspose.Words for Java？**  
A: 可透過在 Java 專案中加入程式庫來安裝 Aspose.Words for Java。您可從 [here](https://releases.aspose.com/words/java/) 下載程式庫，並依照文件中的安裝說明操作。

**Q: 是否能將含表格與圖片的複雜 Word 文件轉換為 Markdown？**  
A: 可以，Aspose.Words for Java 支援將含表格、圖片及各種格式元素的複雜 Word 文件轉換為 Markdown。您可依文件的複雜度自訂 Markdown 輸出。

**Q: 如何在 Markdown 檔案中處理圖片？**  
A: 使用 `MarkdownSaveOptions` 的 `setImagesFolder` 方法設定圖片資料夾路徑。確保圖片檔案儲存在指定的資料夾中，Aspose.Words 會產生相應的 Markdown 圖片連結。

**Q: 是否提供 Aspose.Words for Java 的試用版？**  
A: 有，您可從 Aspose 官方網站取得 Aspose.Words for Java 的試用版。試用版讓您在購買授權前評估程式庫功能。

**Q: 在哪裡可以找到更多範例與文件？**  
A: 如需更多範例、文件與 Aspose.Words for Java 的詳細資訊，請造訪 [documentation](https://reference.aspose.com/words/java/)。

---

**最後更新：** 2025-12-22  
**測試環境：** Aspose.Words for Java 24.12（撰寫時的最新版本）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}