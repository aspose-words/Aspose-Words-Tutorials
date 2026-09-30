---
date: 2026-02-24
description: 了解如何使用 Aspose.Words for Java 將 Word 轉換為 Markdown。本指南涵蓋表格對齊、圖片處理，以及如何將文件儲存為
  Markdown。
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 將 Word 轉換為 Markdown
url: /zh-hant/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 將 Word 轉換為 Markdown（使用 Aspose.Words for Java）

## 簡介：使用 Aspose.Words for Java 將 Word 轉換為 Markdown

在本步驟教學中，您將學習 **如何使用功能強大的 Aspose.Words for Java API 將 Word 轉換為 Markdown**。Markdown 是一種輕量級的標記語言，許多開發者與內容平台都依賴它來撰寫乾淨、易讀的文件。完成本指南後，您將能夠將任何 `.docx` 檔案轉換，保留表格、圖片與格式，並匯出為 `.md` 檔，適用於靜態網站產生器、GitHub README 或任何支援 Markdown 的工作流程。

## 快速答覆
- **需要哪個函式庫？** Aspose.Words for Java（`aspose-words.jar`）。
- **可以自訂表格對齊方式嗎？** 可以 – 在 `MarkdownSaveOptions` 中使用 `TableContentAlignment`。
- **圖片如何處理？** 使用 `setImagesFolder()` 設定圖片資料夾；函式庫會產生相對連結。
- **正式環境需要授權嗎？** 商業授權是非試用版的必備條件。
- **相容於 Java 17 嗎？** 相容，函式庫支援 Java 8 及以上版本。

## 什麼是將 Word 轉換為 Markdown？

將 Word 轉換為 Markdown 意指將 Microsoft Word 文件的豐富格式轉換成純文字的 Markdown 語法。此過程會保留標題、清單、表格與圖片參考，同時去除二進位格式，使內容更易於搬移與版本控制。

## 為什麼使用 Aspose.Words for Java 來儲存文件為 Markdown？

* **完整保真** – 表格、圖片與複雜版面皆能完整保留。  
* **細緻控制** – 可自訂表格對齊、圖片路徑等設定。  
* **無外部相依** – 函式庫即開箱即用，無需安裝 Office。  
* **跨平台** – 可在 Windows、Linux 與 macOS 上執行，支援任何 Java 執行環境。

## 前置條件

在開始之前，請確保您已具備：

- 已在系統上安裝 Java Development Kit（JDK）。  
- Aspose.Words for Java 函式庫。您可從 [此處](https://releases.aspose.com/words/java/) 下載。

## 步驟說明

### 步驟 1：建立將要轉換的 Word 文件

首先，我們建立一個包含兩格表格的簡易 Word 文件。此範例說明在稍後 **將文件儲存為 Markdown** 時，表格內段落的對齊方式會被正確保留。

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

### 步驟 2：自訂表格內容對齊方式

Aspose.Words for Java 讓您可以控制產生的 Markdown 中表格儲存格的對齊方式。使用 `TableContentAlignment` 屬性即可 **自訂表格對齊** 為左、右、置中，或讓函式庫根據每欄第一個段落自動決定。

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

透過切換此設定，您可以 **匯出 Word 表格為 Markdown**，並取得下游渲染引擎所需的精確對齊效果。

### 步驟 3：處理轉換過程中的圖片

當來源 Word 文件內含圖片時，必須告訴 Aspose.Words 圖片檔案的輸出位置。`MarkdownSaveOptions` 的 `setImagesFolder` 方法可指定存放圖片資產的資料夾，Markdown 內則會產生相對連結指向這些檔案。

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

將 `"document_with_images.docx"` 替換為您的來源檔案路徑，將 `"images_folder/"` 替換為您希望輸出圖片的資料夾。

### 完整範例程式碼（涵蓋所有情境）

以下提供一個整合範例，示範如何在同一方法中 **自動表格對齊**、**自訂對齊** 以及 **設定圖片資料夾**。此程式碼與原教學相同，直接可使用。

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

| 問題 | 原因 | 解決方式 |
|------|------|----------|
| 圖片顯示為斷裂連結 | 未設定 `setImagesFolder` 或資料夾路徑不正確 | 確認資料夾路徑正確且資料夾具寫入權限 |
| 表格對齊異常 | `TableContentAlignment` 設定錯誤 | 使用 `TableContentAlignment.AUTO` 讓第一段落決定，或明確設定 LEFT/RIGHT/CENTER |
| 輸出檔案為空 | 未將儲存選項傳遞給 `doc.save()` | 確保在 `save` 方法中傳入 `MarkdownSaveOptions` 實例 |
| 不支援的 Word 功能（如 SmartArt） | Markdown 無法表現某些複雜物件 | 先將這些元素轉為圖片再儲存，或簡化來源文件 |

## 常見問答

**Q: 如何安裝 Aspose.Words for Java？**  
A: 只要在 Java 專案中加入函式庫即可。您可從 [此處](https://releases.aspose.com/words/java/) 下載，並依照文件說明完成安裝。

**Q: 能否將包含表格與圖片的複雜 Word 文件轉換為 Markdown？**  
A: 能。Aspose.Words for Java 支援將含表格、圖片與各種格式元素的複雜 Word 文件轉換為 Markdown，且可依文件複雜度自訂輸出內容。

**Q: 如何在 Markdown 檔案中處理圖片？**  
A: 使用 `MarkdownSaveOptions` 的 `setImagesFolder` 方法設定圖片資料夾路徑。確保圖片檔案存放於指定資料夾，Aspose.Words for Java 會自動產生正確的圖片引用。

**Q: 有提供 Aspose.Words for Java 的試用版嗎？**  
A: 有。您可於 Aspose 官方網站取得試用版，試用期間可評估函式庫功能，之後再決定是否購買授權。

**Q: 哪裡可以找到更多範例與文件說明？**  
A: 請造訪 [文件說明](https://reference.aspose.com/words/java/) 取得更多範例、文件與詳細資訊。

## 結論

本指南說明了使用 Aspose.Words for Java **將 Word 轉換為 Markdown** 所需的全部步驟：建立來源文件、**自訂表格對齊**，以及透過正確的資料夾設定處理圖片。掌握這些技巧後，您即可穩定地將 Word 內容匯出為 Markdown，供部落格、文件網站或任何支援 Markdown 的平台使用。

---

**最後更新：** 2026-02-24  
**測試環境：** Aspose.Words for Java 24.12（撰寫時的最新版本）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}