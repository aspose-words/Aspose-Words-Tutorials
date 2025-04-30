---
"description": "通过我们全面的分步指南，学习如何使用 Aspose.Words for Java 保存文档中的图像。自定义格式、压缩等等。"
"linktitle": "保存文档中的图像"
"second_title": "Aspose.Words Java文档处理API"
"title": "在 Aspose.Words for Java 中保存文档中的图像"
"url": "/zh/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中保存文档中的图像


## Aspose.Words for Java 文档中图像保存简介

在本教程中，我们将探索如何使用 Aspose.Words for Java 从文档中保存图像。我们将介绍各种图像保存场景和自定义选项。本指南提供分步说明和源代码示例。

## 先决条件

在开始之前，请确保已将 Aspose.Words for Java 库集成到项目中。您可以从以下位置下载： [这里](https://releases。aspose.com/words/java/).

## 步骤 1：使用阈值控制将图像保存为 TIFF

要将图像保存为具有阈值控制的 TIFF 格式，请按照以下步骤操作：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## 步骤 2：将特定页面保存为多页 TIFF

要将特定页面保存为多页 TIFF，请使用以下代码：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 步骤3：将图像保存为1 BPP索引PNG

要将图像保存为 1 BPP 索引 PNG，请按照以下步骤操作：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 步骤 4：将页面保存为自定义 JPEG

要将特定页面保存为具有自定义选项的 JPEG，请使用以下代码：

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 步骤5：使用页面保存回调

您可以使用回调来自定义页面保存。以下是示例：

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

## 使用 Aspose.Words for Java 从文档保存图像的完整源代码

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
	// 将“PageSet”设置为“0”以仅转换文档的第一页。
	options.setPageSet(new PageSet(0));
	// 改变图像的亮度和对比度。
	// 两者的尺度均为 0-1，默认为 0.5。
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// 更改水平分辨率。
	// 这些属性的默认值为 96.0，分辨率为 96dpi。
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

## 结论

您已经学习了如何使用 Aspose.Words for Java 从文档中保存图像。这些示例演示了各种自定义图像保存选项，包括格式、压缩和回调函数的使用。探索 Aspose.Words for Java 强大功能的更多可能性。

## 常见问题解答

### 使用 Aspose.Words for Java 保存时如何更改图像格式？

您可以通过在 `ImageSaveOptions`。例如，要保存为 PNG，请使用 `SaveFormat.PNG` 如代码所示：

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### 我可以自定义 TIFF 图像的压缩设置吗？

是的，您可以自定义 TIFF 图像压缩设置。例如，要将压缩方法设置为 CCITT_3，请使用以下代码：

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### 如何将文档中的特定页面保存为单独的图像？

要将特定页面保存为图像，请使用 `setPageSet` 方法 `ImageSaveOptions`。例如，若要仅保存第一页，请设置 `PageSet` 到 `new PageSet(0)`。

```java
saveOptions.setPageSet(new PageSet(0)); // 将第一页保存为图像
```

### 如何在保存时将自定义设置应用于 JPEG 图像？

您可以使用以下方式将自定义设置应用于 JPEG 图像 `ImageSaveOptions`调整亮度、对比度和分辨率等属性。例如，要将亮度更改为 0.3，对比度更改为 0.7，请使用以下代码：

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### 如何使用回调来自定义图像保存？

要使用回调自定义图像保存，请设置 `PageSav在gCallback` in `ImageSaveOptions`创建一个实现 `IPageSavingCallback` 接口并覆盖 `pageSaving` 方法。

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

然后，创建一个实现 `IPageSavingCallback` 界面并自定义文件名和位置 `pageSaving` 方法。

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