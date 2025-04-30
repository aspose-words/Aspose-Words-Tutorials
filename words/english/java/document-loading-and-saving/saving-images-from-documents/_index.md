---
title: Saving Images from Documents in Aspose.Words for Java
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
description: Learn how to save images from documents using Aspose.Words for Java with our comprehensive step-by-step guide. Customize formats, compression, and more.
weight: 17
url: /java/document-loading-and-saving/saving-images-from-documents/
---


{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Saving Images from Documents in Aspose.Words for Java


## Introduction to Saving Images from Documents in Aspose.Words for Java

In this tutorial, we will explore how to save images from documents using Aspose.Words for Java. We will cover various scenarios and customization options for image saving. This guide provides step-by-step instructions with source code examples.

## Prerequisites

Before you begin, ensure you have the Aspose.Words for Java library integrated into your project. You can download it from [here](https://releases.aspose.com/words/java/).

## Step 1: Saving Images as TIFF with Threshold Control

To save images as TIFF format with threshold control, follow these steps:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Step 2: Saving a Specific Page as Multipage TIFF

To save a specific page as a multipage TIFF, use the following code:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Step 3: Saving Images as 1 BPP Indexed PNG

To save images as 1 BPP indexed PNG, follow these steps:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Step 4: Saving a Page as JPEG with Customization

To save a specific page as JPEG with customization options, use this code:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Step 5: Using Page Saving Callback

You can use a callback to customize page saving. Here's an example:

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

## Complete Source Code For Saving Images from Documents in Aspose.Words for Java

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

## Conclusion

You have learned how to save images from documents using Aspose.Words for Java. These examples demonstrate various customization options for image saving, including format, compression, and callback usage. Explore more possibilities with Aspose.Words for Java's powerful capabilities.

## FAQ's

### How do I change the image format when saving with Aspose.Words for Java?

You can change the image format by specifying the desired format in the `ImageSaveOptions`. For example, to save as PNG, use `SaveFormat.PNG` as shown in the code:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Can I customize the compression settings for TIFF images?

Yes, you can customize TIFF image compression settings. For example, to set the compression method to CCITT_3, use the following code:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### How can I save a specific page from a document as a separate image?

To save a specific page as an image, use the `setPageSet` method in `ImageSaveOptions`. For example, to save only the first page, set the `PageSet` to `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

### How do I apply custom settings to JPEG images when saving?

You can apply custom settings to JPEG images using `ImageSaveOptions`. Adjust properties like brightness, contrast, and resolution. For instance, to change brightness to 0.3 and contrast to 0.7, use this code:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### How can I use a callback for customizing image saving?

To use a callback for customizing image saving, set the `PageSavingCallback` in `ImageSaveOptions`. Create a class that implements the `IPageSavingCallback` interface and override the `pageSaving` method.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Then, create a class that implements the `IPageSavingCallback` interface and customize the file name and location in the `pageSaving` method.

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
