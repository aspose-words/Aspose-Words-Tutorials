---
"description": "透過我們全面的逐步指南了解如何使用 Aspose.Words for Java 儲存文件中的圖像。自訂格式、壓縮等。"
"linktitle": "儲存文件中的影像"
"second_title": "Aspose.Words Java文件處理API"
"title": "在 Aspose.Words for Java 中儲存文件中的圖片"
"url": "/zh-hant/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中儲存文件中的圖片


## Aspose.Words for Java 文件中圖像保存簡介

在本教學中，我們將探討如何使用 Aspose.Words for Java 儲存文件中的圖像。我們將介紹圖像保存的各種場景和自訂選項。本指南提供了帶有原始程式碼範例的逐步說明。

## 先決條件

在開始之前，請確保已將 Aspose.Words for Java 程式庫整合到您的專案中。您可以從下載 [這裡](https://releases。aspose.com/words/java/).

## 步驟 1：使用閾值控制將影像儲存為 TIFF

若要將影像儲存為具有閾值控制的 TIFF 格式，請按照下列步驟操作：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## 步驟 2：將特定頁面儲存為多頁 TIFF

若要將特定頁面儲存為多頁 TIFF，請使用下列程式碼：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 步驟3：將影像儲存為1 BPP索引PNG

若要將影像儲存為 1 BPP 索引 PNG，請依照下列步驟操作：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 步驟 4：將頁面儲存為自訂 JPEG

若要將特定頁面儲存為具有自訂選項的 JPEG，請使用下列程式碼：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 步驟5：使用頁面儲存回調

您可以使用回調來自訂頁面儲存。以下是一個例子：

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

## 使用 Aspose.Words for Java 從文件保存影像的完整原始碼

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
	// 將“PageSet”設定為“0”以僅轉換文件的第一頁。
	options.setPageSet(new PageSet(0));
	// 改變影像的亮度和對比度。
	// 兩者的尺度均為 0-1，預設為 0.5。
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// 更改水平分辨率。
	// 這些屬性的預設值為 96.0，解析度為 96dpi。
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

## 結論

您已經了解如何使用 Aspose.Words for Java 儲存文件中的圖片。這些範例示範了影像保存的各種自訂選項，包括格式、壓縮和回調使用。利用 Aspose.Words for Java 的強大功能探索更多可能性。

## 常見問題解答

### 使用 Aspose.Words for Java 儲存時如何變更影像格式？

您可以透過在 `ImageSaveOptions`。例如，要儲存為 PNG，請使用 `SaveFormat.PNG` 如程式碼所示：

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### 我可以自訂 TIFF 影像的壓縮設定嗎？

是的，您可以自訂 TIFF 影像壓縮設定。例如，要將壓縮方法設為 CCITT_3，請使用以下程式碼：

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### 如何將文件中的特定頁面儲存為單獨的圖像？

若要將特定頁面儲存為圖像，請使用 `setPageSet` 方法 `ImageSaveOptions`。例如，若要僅儲存第一頁，請設定 `PageSet` 到 `new PageSet(0)`。

```java
saveOptions.setPageSet(new PageSet(0)); // 將第一頁儲存為圖像
```

### 如何在儲存時將自訂設定套用至 JPEG 影像？

您可以使用以下方式將自訂設定套用至 JPEG 影像 `ImageSaveOptions`。調整亮度、對比度和解析度等屬性。例如，若要將亮度變更為 0.3 並將對比度變更為 0.7，請使用下列程式碼：

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### 如何使用回調來自訂圖像保存？

若要使用回調自訂圖像儲存，請設定 `PageSav在gCallback` in `ImageSaveOptions`。創建一個實現 `IPageSavingCallback` 介面並覆蓋 `pageSaving` 方法。

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

然後，創建一個實現 `IPageSavingCallback` 介面並自訂檔案名稱和位置 `pageSaving` 方法。

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}