---
title: 在 Aspose.Words for Java 中儲存文件中的圖片
linktitle: 儲存文件中的影像
second_title: Aspose.Words Java 文件處理 API
description: 透過我們全面的逐步指南，了解如何使用 Aspose.Words for Java 儲存文件中的圖像。自訂格式、壓縮等。
weight: 17
url: /zh-hant/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中儲存文件中的圖片


## 在 Aspose.Words for Java 中儲存文件中的圖片簡介

在本教學中，我們將探討如何使用 Aspose.Words for Java 儲存文件中的圖像。我們將介紹圖像保存的各種場景和自訂選項。本指南提供了帶有原始程式碼範例的逐步說明。

## 先決條件

在開始之前，請確保您已將 Aspose.Words for Java 程式庫整合到您的專案中。您可以從以下位置下載：[這裡](https://releases.aspose.com/words/java/).

## 第 1 步：使用閾值控制將影像儲存為 TIFF

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

## 步驟 3：將影像儲存為 1 BPP 索引 PNG

若要將映像儲存為 1 BPP 索引 PNG，請依照下列步驟操作：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 步驟 4：透過自訂將頁面另存為 JPEG

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

您可以使用回呼來自訂頁面儲存。這是一個例子：

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

## 在 Aspose.Words for Java 中保存文件影像的完整原始碼

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
	//將“PageSet”設定為“0”以僅轉換文件的第一頁。
	options.setPageSet(new PageSet(0));
	//更改影像的亮度和對比度。
	//兩者的評分範圍均為 0-1，預設值為 0.5。
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	//更改水平分辨率。
	//對於 96dpi 的分辨率，這些屬性的預設值為 96.0。
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

您已經學習如何使用 Aspose.Words for Java 儲存文件中的影像。這些範例示範了影像保存的各種自訂選項，包括格式、壓縮和回調使用。利用 Aspose.Words for Java 的強大功能探索更多可能性。

## 常見問題解答

### 使用 Aspose.Words for Java 儲存時如何變更影像格式？

您可以透過在中指定所需的格式來變更影像格式`ImageSaveOptions`。例如，若要另存為 PNG，請使用`SaveFormat.PNG`如程式碼所示：

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### 我可以自訂 TIFF 影像的壓縮設定嗎？

是的，您可以自訂 TIFF 影像壓縮設定。例如，要將壓縮方法設定為CCITT_3，請使用以下程式碼：

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### 如何將文件中的特定頁面儲存為單獨的影像？

若要將特定頁面另存為圖像，請使用`setPageSet`中的方法`ImageSaveOptions`。例如，若要僅儲存第一頁，請設定`PageSet`到`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); //將第一頁儲存為圖像
```

### 儲存時如何將自訂設定套用至 JPEG 影像？

您可以使用以下命令將自訂設定套用至 JPEG 影像`ImageSaveOptions`。調整亮度、對比度和解析度等屬性。例如，若要將亮度變更為 0.3，對比度變更為 0.7，請使用下列程式碼：

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### 如何使用回調來自訂圖像保存？

若要使用回調來自訂圖像儲存，請設定`PageSavingCallback`在`ImageSaveOptions`。創建一個類別來實現`IPageSavingCallback`介面並覆蓋`pageSaving`方法。

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

然後，建立一個類別來實現`IPageSavingCallback`介面並自訂檔案名稱和位置`pageSaving`方法。

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
