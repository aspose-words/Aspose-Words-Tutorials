---
date: 2025-12-27
description: 学习如何使用 Aspose.Words for Java 将页面保存为 JPEG 并从 Word 文档中提取图像。包括设置图像亮度、分辨率以及创建多页
  TIFF 的技巧。
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: 使用 Aspose.Words for Java 将页面保存为 JPEG 并从文档中提取图像
url: /zh/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 将页面保存为 JPEG 并从 Aspose.Words for Java 文档中提取图像

在本教程中，您将了解如何使用 Aspose.Words for Java **save page as jpeg** 从 Word 文档中保存页面为 JPEG，以及如何 **extract images from Word** 文件中提取图像。我们将演示真实场景，例如设置图像亮度、在 Java 中调整图像分辨率以及创建多页 TIFF。每一步都包含可直接运行的代码片段，您可以复制、粘贴并立即看到结果。

## 快速回答
- **我可以将单页保存为 JPEG 吗？** 可以 – 使用 `ImageSaveOptions` 并调用 `setPageSet(new PageSet(pageIndex))`。
- **如何更改图像亮度？** 调用 `options.setImageBrightness(floatValue)`（取值范围 0‑1）。
- **如果需要多页 TIFF 呢？** 设置覆盖所需页面的 `PageSet` 并选择 TIFF 压缩方式。
- **如何控制图像分辨率？** 使用 `setResolution(floatDpi)` 或 `setHorizontalResolution(floatDpi)`。
- **生产环境需要许可证吗？** 非试用使用时必须拥有有效的 Aspose.Words 许可证。

## 什么是 “save page as jpeg”？
将页面保存为 JPEG 指的是将 Word 文档的单个页面转换为栅格图像文件（JPEG）。这在生成预览图、缩略图或在网页中嵌入文档页面（PDF 渲染不方便时）非常有用。

## 为什么要从 Word 文档中提取图像？
许多业务流程需要从 DOCX 文件中提取原始图形（徽标、图表、照片）以便重新使用、归档或分析。Aspose.Words 能够直接以原始格式提取每张图像，且不会损失质量。

## 前置条件
- 已安装 Java Development Kit（JDK 8 或更高）。
- 项目中已添加 Aspose.Words for Java 库。可从 [here](https://releases.aspose.com/words/java/) 下载。
- 将示例 Word 文档（例如 `Rendering.docx`）放置在已知目录下。

## 步骤 1：将图像保存为带阈值控制的 TIFF（创建多页 TIFF）
要生成高对比度的灰度 TIFF，可以控制二值化阈值。当需要可打印的黑白版文档时，这非常实用。

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
如果只需要包含部分页面（例如第 1‑2 页）的 TIFF，可配置 `PageSet`。此示例演示 **create multipage tiff**。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 步骤 3：将图像保存为 1 BPP 索引 PNG
当需要超轻量的黑白 PNG（每像素 1 位）时，设置相应的像素格式即可。这在低带宽场景下嵌入简单图形时非常有用。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 步骤 4：将页面保存为 JPEG 并自定义（设置图像亮度和分辨率）
此处 **save page as jpeg** 的同时调整亮度、对比度和分辨率——非常适合生成缩略图或网页就绪的预览图。

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 步骤 5：使用页面保存回调（高级自定义）
回调可以在导出多页时动态重命名每个输出文件。

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

## 所有场景的完整源代码
下面是一个包含上述所有方法的单一类。您可以单独运行每个测试。

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

## 常见问题及解决方案
- **“Unable to locate the document file”** – 请确认文件路径使用了适合您操作系统的分隔符（`/` 或 `\\`）。
- **图像显示为空白** – 请确保为 TIFF 设置了合适的 `ImageColorMode`（例如 `GRAYSCALE`）。
- **大文档出现内存不足** – 通过调整 `PageSet` 范围分批处理页面。
- **JPEG 质量差** – 使用 `setHorizontalResolution` 或 `setResolution` 提高分辨率。

## 常见问答

**问：如何在使用 Aspose.Words for Java 保存时更改图像格式？**  
答：在 `ImageSaveOptions` 中设置所需格式。对于 PNG，只需实例化 `ImageSaveOptions` 并将 `SaveFormat.PNG` 赋给它。

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**问：我可以自定义 TIFF 图像的压缩设置吗？**  
答：可以。使用 `setTiffCompression` 选择压缩算法，例如 `CCITT_3`。

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**问：如何将文档的特定页面保存为单独的图像？**  
答：使用 `setPageSet` 方法并传入单页索引。

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**问：保存 JPEG 图像时如何应用自定义设置？**  
答：通过 `ImageSaveOptions` 调整亮度、对比度和分辨率等属性。

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**问：如何使用回调来自定义图像保存？**  
答：实现 `IPageSavingCallback` 并通过 `setPageSavingCallback` 进行设置。

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

## 结论
现在，您已经拥有了一整套工具，可用于 **save page as jpeg**、提取图像、控制图像亮度、在 Java 中设置图像分辨率，以及使用 Aspose.Words for Java 创建多页 TIFF 文件。请尝试不同的 `ImageSaveOptions` 设置，以满足项目需求，并进一步探索 Aspose.Words API，获取更多文档处理功能。

---

**最后更新：** 2025-12-27  
**测试环境：** Aspose.Words for Java 24.12（撰写时的最新版本）  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}