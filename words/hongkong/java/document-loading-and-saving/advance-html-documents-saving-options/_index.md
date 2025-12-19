---
date: 2025-12-19
description: 學習如何使用 Aspose.Words Java 匯出 HTML，涵蓋將 Word 儲存為 HTML 的進階選項，以及高效地將 Word
  轉換為 HTML。
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words Java 匯出 HTML：進階選項
url: /zh-hant/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words Java 匯出 HTML：進階選項

在本教學中，您將學會 **如何匯出 HTML**，將 Word 文件透過 Aspose.Words for Java 轉換成 HTML。無論是要 **將 Word 另存為 HTML** 以進行網站發佈，或是 **將 Word 轉換為 HTML** 以供後續處理，進階儲存選項都能讓您對輸出結果進行細緻的控制。我們將逐一說明每個選項的使用時機，並展示這些設定在實務情境中如何發揮作用。

## 快速解答
- **HTML 匯出的主要類別是什麼？** `HtmlSaveOptions`  
- **可以直接在 HTML 中嵌入字型嗎？** 可以，將 `exportFontsAsBase64` 設為 `true`。  
- **如何保留 Word 專屬的往返資訊？** 啟用 `exportRoundtripInformation`。  
- **哪種格式最適合向量圖形？** 使用 `convertMetafilesToSvg` 產生 SVG 輸出。  
- **是否能避免 CSS 類別名稱衝突？** 可以，使用 `addCssClassNamePrefix`。

## 1. 介紹
Aspose.Words for Java 是一套功能強大的 API，讓開發者能以程式方式操作 Word 文件。本指南聚焦於進階的 HTML 文件儲存選項，協助您依照特定的網站或整合需求，客製化轉換流程。

## 2. 匯出往返資訊
保留往返資訊可讓您在將 HTML 重新轉回 Word 時，不會遺失版面或格式細節。

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### 使用時機
- 需要可逆的轉換流程（HTML → Word → HTML）時。  
- 於協同編輯情境下，必須保留原始 Word 結構時。

## 3. 匯出字型為 Base64
將字型直接嵌入 HTML，可消除外部字型依賴，確保在各瀏覽器中的視覺一致性。

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### 專業小技巧
當目標環境對外部資源存取受限（例如電子報）時，建議使用此選項。

## 4. 匯出資源
控制 CSS 與字型資源的輸出方式，並可為這些資產指定自訂資料夾或 URL 別名。

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### 為什麼重要
將 CSS 分離為外部檔案可減少 HTML 大小，且可透過快取提升頁面載入速度。

## 5. 將 Metafile 轉換為 EMF 或 WMF
Metafile（如 EMF/WMF）會被轉換為瀏覽器能可靠呈現的格式。

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### 使用情境
當目標瀏覽器支援這些向量格式且您需要無損縮放時，請選擇 EMF/WMF。

## 6. 將 Metafile 轉換為 SVG
SVG 提供最佳的可伸縮性，且在現代瀏覽器中廣受支援。

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### 好處
SVG 檔案輕量且保持文件的解析度獨立性，非常適合響應式網頁設計。

## 7. 新增 CSS 類別名稱前綴
透過為所有產生的 CSS 類別名稱加上前綴，避免樣式衝突。

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### 實用建議
在將 HTML 嵌入既有頁面時，使用唯一的前綴（例如您的專案名稱），以防止 CSS 衝突。

## 8. 匯出 MHTML 資源的 CID URL
以 MHTML 格式儲存時，可使用 Content‑ID URL 匯出資源，提升電子郵件相容性。

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### 使用時機
適用於產生單一、完整的 HTML 檔案，並可直接作為電子郵件附件。

## 9. 解析字型名稱
確保 HTML 參照正確的字型族，提升跨平台的一致性。

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### 為什麼有幫助
若原始文件使用的字型在客戶端機器上未安裝，此選項會自動替換為網頁安全字型。

## 10. 將文字輸入表單欄位匯出為純文字
將表單欄位以純文字方式呈現，而非互動式的 HTML 輸入元件。

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### 使用情境
需要將表單以唯讀方式保存以供歸檔或列印時。

## 常見問題與除錯
| 問題 | 常見原因 | 解決方法 |
|------|----------|----------|
| 輸出中缺少字型 | 未啟用 `exportFontsAsBase64` | 設定 `setExportFontsAsBase64(true)` |
| 嵌入後 CSS 損壞 | 使用 `EXTERNAL` 卻未提供 CSS 檔案 | 確認 CSS 檔案已部署於指定的 `resourceFolderAlias` |
| HTML 檔案過大 | 大量圖片以 Base64 方式嵌入 | 改為使用外部圖片資源，透過 `setExportFontResources(true)` 並設定 `resourceFolder` |
| SVG 在舊版瀏覽器無法顯示 | 瀏覽器不支援 SVG | 同時匯出為 EMF/WMF，提供 PNG 替代方案 |

## 常見問答

**Q: 我可以同時將字型嵌入為 Base64 且保留外部 CSS 嗎？**  
A: 可以。將 `exportFontsAsBase64(true)` 設為 `true`，同時使用 `CssStyleSheetType.EXTERNAL` 以分離樣式規則。

**Q: 如何將已存在的 HTML 轉回 Word 文件？**  
A: 使用 `Document doc = new Document("input.html");` 讀取 HTML，然後 `doc.save("output.docx");`。在首次匯出時啟用 `exportRoundtripInformation` 即可保留往返資訊。

**Q: 使用 SVG 轉換會不會影響效能？**  
A: 轉換大型 Metafile 為 SVG 可能會增加處理時間，但最終產生的 HTML 較小，且在瀏覽器中的渲染速度通常較快。

**Q: 這些選項在 Aspose.Words for .NET 也適用嗎？**  
A: 相同概念亦存在於 .NET API 中，雖然方法名稱可能略有差異（例如 `HtmlSaveOptions` 在兩平台皆共用）。

**Q: 哪個選項最適合製作適用於電子郵件的 HTML？**  
A: 使用 `SaveFormat.MHTML` 搭配 `exportCidUrlsForMhtmlResources`，即可將所有資源直接嵌入郵件內容。

---

**最後更新：** 2025-12-19  
**測試環境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}