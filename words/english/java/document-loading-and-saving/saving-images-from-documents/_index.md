---
title: "How to Save Page as JPEG and Extract Images from Documents with Aspose.Words for Java"
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
description: Learn how to save page as jpeg and extract images from Word documents using Aspose.Words for Java. Includes tips for setting image brightness, resolution, and creating multipage TIFF.
weight: 17
url: /java/document-loading-and-saving/saving-images-from-documents/
date: 2025-12-27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Save page as JPEG and Extract Images from Documents in Aspose.Words for Java

In this tutorial you’ll discover how to **save page as jpeg** from a Word document and how to **extract images from Word** files using Aspose.Words for Java. We’ll walk through real‑world scenarios such as setting image brightness, adjusting image resolution in Java, and creating a multipage TIFF. Each step includes ready‑to‑run code snippets so you can copy, paste, and see results instantly.

## Quick Answers
- **Can I save a single page as JPEG?** Yes – use `ImageSaveOptions` with `setPageSet(new PageSet(pageIndex))`.
- **How do I change image brightness?** Call `options.setImageBrightness(floatValue)` (0‑1 range).
- **What if I need a multipage TIFF?** Set a `PageSet` covering the desired pages and choose a TIFF compression method.
- **How can I control image resolution?** Use `setResolution(floatDpi)` or `setHorizontalResolution(floatDpi)`.
- **Do I need a license for production?** A valid Aspose.Words license is required for non‑trial use.

## What is “save page as jpeg”?
Saving a page as JPEG means converting a single page of a Word document into a raster image file (JPEG). This is useful for preview generation, thumbnail creation, or embedding document pages in web pages where PDF rendering isn’t practical.

## Why extract images from Word documents?
Many business workflows require pulling out the original graphics (logos, diagrams, photos) from a DOCX file for reuse, archiving, or analysis. Aspose.Words makes it straightforward to extract each image in its native format without losing quality.

## Prerequisites
- Java Development Kit (JDK 8 or later) installed.
- Aspose.Words for Java library added to your project. Download it from [here](https://releases.aspose.com/words/java/).
- A sample Word document (e.g., `Rendering.docx`) placed in a known directory.

## Step 1: Save Images as TIFF with Threshold Control (Create Multipage TIFF)
To generate a high‑contrast, grayscale TIFF you can control the binarization threshold. This is handy when you need a printable, black‑and‑white version of your document.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Step 2: Save a Specific Page as Multipage TIFF
If you need a TIFF that contains only a subset of pages (e.g., pages 1‑2), configure a `PageSet`. This demonstrates **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Step 3: Save Images as 1 BPP Indexed PNG
When you need ultra‑lightweight black‑and‑white PNGs (1 bit per pixel), set the pixel format accordingly. This is useful for embedding simple graphics in low‑bandwidth scenarios.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Step 4: Save a Page as JPEG with Customization (Set Image Brightness & Resolution)
Here we **save page as jpeg** while adjusting brightness, contrast, and resolution—perfect for creating thumbnails or web‑ready previews.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Step 5: Using a Page‑Saving Callback (Advanced Customization)
A callback lets you rename each output file dynamically, which is useful when exporting many pages at once.

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

## Complete Source Code for All Scenarios
Below is a single class that contains every method demonstrated above. You can run each test individually.

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

## Common Issues and Solutions
- **“Unable to locate the document file”** – Verify the file path uses the correct separator (`/` or `\\`) for your OS.
- **Images appear blank** – Ensure you set an appropriate `ImageColorMode` (e.g., `GRAYSCALE` for TIFF).
- **Out‑of‑memory errors on large documents** – Process pages in batches by adjusting the `PageSet` range.
- **JPEG quality looks poor** – Increase the resolution with `setHorizontalResolution` or `setResolution`.

## Frequently Asked Questions

**Q: How do I change the image format when saving with Aspose.Words for Java?**  
A: Set the desired format in `ImageSaveOptions`. For PNG, you can simply instantiate `ImageSaveOptions` and assign `SaveFormat.PNG` if needed.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Can I customize the compression settings for TIFF images?**  
A: Yes. Use `setTiffCompression` to choose a compression algorithm such as `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: How can I save a specific page from a document as a separate image?**  
A: Use the `setPageSet` method with a single page index.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: How do I apply custom settings to JPEG images when saving?**  
A: Adjust properties like brightness, contrast, and resolution via `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: How can I use a callback for customizing image saving?**  
A: Implement `IPageSavingCallback` and assign it with `setPageSavingCallback`.

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

## Conclusion
You now have a complete toolbox for **saving page as jpeg**, extracting images, controlling image brightness, setting image resolution in Java, and creating multipage TIFF files with Aspose.Words for Java. Experiment with different `ImageSaveOptions` settings to fit your project's needs, and explore the broader Aspose.Words API for even more document manipulation capabilities.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}