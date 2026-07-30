---
date: 2025-12-27
description: 學習如何使用 Aspose.Words for Java 將頁面儲存為 JPEG，並從 Word 文件中提取圖像。包括設定圖像亮度、解析度以及建立多頁
  TIFF 的技巧。
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words for Java 將頁面儲存為 JPEG 並從文件中提取圖像
url: /zh-hant/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 將頁面另存為 JPEG 並從 Aspose.Words for Java 文件中提取圖像

在本教學中，您將了解如何使用 Aspose.Words for Java 從 Word 文件 **save page as jpeg** 並 **extract images from Word**。我們將逐步說明實務情境，例如設定圖像亮度、在 Java 中調整圖像解析度，以及建立多頁 TIFF。每個步驟都包含可直接執行的程式碼片段，您可以複製、貼上，即時看到結果。

## 快速回答
- **我可以將單一頁面另存為 JPEG 嗎？** 可以 – 使用 `ImageSaveOptions` 並搭配 `setPageSet(new PageSet(pageIndex))`。
- **如何調整圖像亮度？** 呼叫 `options.setImageBrightness(floatValue)`（範圍 0‑1）。
- **如果需要多頁 TIFF 該怎麼做？** 設定涵蓋所需頁面的 `PageSet`，並選擇 TIFF 壓縮方式。
- **如何控制圖像解析度？** 使用 `setResolution(floatDpi)` 或 `setHorizontalResolution(floatDpi)`。
- **正式環境需要授權嗎？** 非試用版使用時必須擁有有效的 Aspose.Words 授權。

## 什麼是「save page as jpeg」？
將頁面另存為 JPEG 是指將 Word 文件的單一頁面轉換為點陣圖檔案（JPEG）。此功能適用於產生預覽圖、縮圖，或在 PDF 無法實用的網頁中嵌入文件頁面。

## 為什麼要從 Word 文件中提取圖像？
許多業務流程需要從 DOCX 檔案中提取原始圖形（標誌、圖表、照片）以供再利用、存檔或分析。Aspose.Words 可輕鬆將每張圖像以原始格式抽取，且不會失真。

## 前置條件
- 已安裝 Java Development Kit（JDK 8 或更新版本）。
- 已將 Aspose.Words for Java 程式庫加入專案。可從 [here](https://releases.aspose.com/words/java/) 下載。
- 一個範例 Word 文件（例如 `Rendering.docx`）放置於已知目錄中。

## 步驟 1：將圖像另存為帶閾值控制的 TIFF（建立多頁 TIFF）
若要產生高對比度的灰階 TIFF，可控制二值化閾值。當您需要可列印的黑白文件版本時，此功能相當便利。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## 步驟 2：將特定頁面另存為多頁 TIFF
若只需包含部分頁面的 TIFF（例如第 1‑2 頁），請設定 `PageSet`。此範例示範 **create multipage tiff**。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 步驟 3：將圖像另存為 1 BPP 索引 PNG
當需要極輕量的黑白 PNG（每像素 1 位元）時，可相應設定像素格式。此方式適用於低頻寬情境下嵌入簡易圖形。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 步驟 4：將頁面另存為 JPEG 並自訂（設定圖像亮度與解析度）
此處我們 **save page as jpeg**，同時調整亮度、對比度與解析度——非常適合製作縮圖或網頁預覽。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 步驟 5：使用頁面保存回呼（進階自訂）
回呼可讓您動態重新命名每個輸出檔案，適用於一次匯出多頁時的需求。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## 完整範例程式碼（所有情境）
以下是一個單一類別，包含上述所有示範方法。您可以分別執行各個測試。

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## 常見問題與解決方案
- **「Unable to locate the document file」** – 請確認檔案路徑使用正確的分隔符（`/` 或 `\\`）符合您的作業系統。
- **圖像顯示為空白** – 請確保已設定適當的 `ImageColorMode`（例如 TIFF 使用 `GRAYSCALE`）。
- **大型文件發生記憶體不足錯誤** – 透過調整 `PageSet` 範圍，以批次方式處理頁面。
- **JPEG 品質不佳** – 使用 `setHorizontalResolution` 或 `setResolution` 提高解析度。

## 常見問答

**Q: 如何在使用 Aspose.Words for Java 保存時變更圖像格式？**  
A: 在 `ImageSaveOptions` 中設定所需格式。若要保存為 PNG，只需實例化 `ImageSaveOptions` 並指定 `SaveFormat.PNG` 即可。

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: 我可以自訂 TIFF 圖像的壓縮設定嗎？**  
A: 可以。使用 `setTiffCompression` 來選擇壓縮演算法，例如 `CCITT_3`。

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: 如何將文件的特定頁面另存為單獨的圖像？**  
A: 使用 `setPageSet` 方法並傳入單一頁面索引。

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: 在保存 JPEG 圖像時，如何套用自訂設定？**  
A: 透過 `ImageSaveOptions` 調整亮度、對比度與解析度等屬性。

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: 如何使用回呼自訂圖像保存？**  
A: 實作 `IPageSavingCallback` 並使用 `setPageSavingCallback` 指定它。

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## 結論
現在您已擁有完整的工具箱，可用於 **saving page as jpeg**、提取圖像、控制圖像亮度、在 Java 中設定圖像解析度，以及使用 Aspose.Words for Java 建立多頁 TIFF 檔案。請嘗試不同的 `ImageSaveOptions` 設定以符合專案需求，並探索更廣泛的 Aspose.Words API，以獲得更多文件操作功能。

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}