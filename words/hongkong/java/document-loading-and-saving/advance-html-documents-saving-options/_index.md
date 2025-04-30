---
"description": "在本教程中，我們介紹了使用 Aspose.Words for Java 的各種進階 HTML 文件保存選項。這些選項使您能夠創建高品質的 HTML"
"linktitle": "使用以下方式儲存 HTML 文件"
"second_title": "Aspose.Words Java文件處理API"
"title": "使用 Aspose.Words Java 的高階 HTML 文件儲存選項"
"url": "/zh-hant/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words Java 的高階 HTML 文件儲存選項


在本教學中，我們將探索 Aspose.Words for Java 提供的進階 HTML 文件保存選項。 Aspose.Words 是一個用於處理 Word 文件的強大的 Java API，它提供了廣泛的文件操作和轉換功能。

## 1. 簡介
Aspose.Words for Java 可讓您以程式設計方式處理 Word 文件。在本教學中，我們將重點介紹進階 HTML 文件保存選項，這些選項可讓您控制 Word 文件轉換為 HTML 的方式。

## 2. 匯出往返訊息
這 `exportRoundtripInformation` 方法可讓您將 Word 文件匯出為 HTML，同時保留往返資訊。當您想要將 HTML 轉換回 Word 格式而不遺失任何特定於文件的詳細資訊時，此資訊非常有用。

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. 將字體匯出為 Base64
隨著 `exportFontsAsBase64` 方法，您可以將文件中使用的字體匯出為 HTML 中的 Base64 編碼資料。這可確保 HTML 表示保留與原始 Word 文件相同的字體樣式。

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. 導出資源
這 `exportResources` 方法可讓您指定 CSS 樣式表的類型並匯出字體資源。您也可以在 HTML 中設定資源資料夾和資源的別名。

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources”);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

## 5. 將圖元檔轉換為 EMF 或 WMF
這 `convertMetafilesToEmfOrWmf` 此方法可讓您將文件中的元檔案轉換為 EMF 或 WMF 格式，確保相容性和 HTML 中的流暢渲染。

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"紅點\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. 將圖元檔轉換為 SVG
使用 `convertMetafilesToSvg` 將元檔案轉換為 SVG 格式的方法。此格式非常適合在 HTML 文件中顯示向量圖形。

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

## 7. 新增 CSS 類別名稱前綴
隨著 `addCssClassNamePrefix` 方法，您可以在匯出的 HTML 中為 CSS 類別名稱加上前綴。這有助於防止與現有樣式發生衝突。

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. 匯出 MHTML 資源的 CID URL
這 `exportCidUrlsForMhtmlResources` 方法用於將文件儲存為 MHTML 格式。它允許導出資源的 Content-ID URL。

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

## 9. 解析字體名稱
這 `resolveFontNames` 方法有助於在以 HTML 格式儲存文件時解析字體名稱，確保在不同平台上保持一致的渲染。

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

## 10. 將文字輸入表單欄位匯出為文字
這 `exportTextInputFormFieldAsText` 方法將表單欄位匯出為 HTML 中的純文本，使其易於閱讀和編輯。

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// 指定的資料夾必須存在並且應該為空。
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// 設定一個選項將表單欄位匯出為純文本，而不是 HTML 輸入元素。
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## 結論
在本教程中，我們探索了 Aspose.Words for Java 提供的高級 HTML 文件保存選項。這些選項可讓您對轉換過程進行細粒度的控制，從而允許您建立與原始 Word 文件非常相似的 HTML 文件。

## 常見問題解答
以下是有關使用 Aspose.Words for Java 和 HTML 文件保存選項的一些常見問題：

### 問題 1：如何使用 Aspose.Words for Java 將 HTML 轉換回 Word 格式？
要將 HTML 轉換回 Word 格式，您可以使用 Aspose.Words API 的 `load` 方法載入HTML文檔，然後將其儲存為Word格式。

### 問題2：匯出為HTML時我可以自訂CSS樣式嗎？
是的，您可以透過修改 HTML 中使用的樣式表或使用 `addCssClassNamePrefix` 方法為 CSS 類別名稱加上前綴。

### Q3：有沒有辦法優化 HTML 輸出以便在網頁上顯示？
是的，您可以透過設定選項（例如將字體匯出為 Base64 以及將元檔案轉換為 SVG）來優化 HTML 輸出以供網頁顯示。

### Q4：將複雜的 Word 文件轉換為 HTML 時有什麼限制嗎？
雖然 Aspose.Words for Java 提供了強大的轉換功能，但佈局複雜的複雜 Word 文件可能需要額外的後處理才能實現所需的 HTML 輸出。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}