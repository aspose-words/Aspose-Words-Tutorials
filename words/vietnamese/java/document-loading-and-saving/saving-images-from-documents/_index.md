---
"description": "Tìm hiểu cách lưu hình ảnh từ tài liệu bằng Aspose.Words for Java với hướng dẫn từng bước toàn diện của chúng tôi. Tùy chỉnh định dạng, nén và nhiều hơn nữa."
"linktitle": "Lưu hình ảnh từ tài liệu"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Lưu hình ảnh từ tài liệu trong Aspose.Words cho Java"
"url": "/vi/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lưu hình ảnh từ tài liệu trong Aspose.Words cho Java


## Giới thiệu về Lưu hình ảnh từ tài liệu trong Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách lưu hình ảnh từ tài liệu bằng Aspose.Words for Java. Chúng ta sẽ đề cập đến nhiều tình huống và tùy chọn tùy chỉnh khác nhau để lưu hình ảnh. Hướng dẫn này cung cấp hướng dẫn từng bước với các ví dụ về mã nguồn.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã tích hợp thư viện Aspose.Words for Java vào dự án của mình. Bạn có thể tải xuống từ [đây](https://releases.aspose.com/words/java/).

## Bước 1: Lưu hình ảnh dưới dạng TIFF với Kiểm soát ngưỡng

Để lưu hình ảnh ở định dạng TIFF với ngưỡng kiểm soát, hãy làm theo các bước sau:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Bước 2: Lưu một trang cụ thể dưới dạng TIFF nhiều trang

Để lưu một trang cụ thể dưới dạng TIFF nhiều trang, hãy sử dụng mã sau:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Bước 3: Lưu hình ảnh dưới dạng PNG được lập chỉ mục 1 BPP

Để lưu hình ảnh dưới dạng PNG được lập chỉ mục 1 BPP, hãy làm theo các bước sau:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Bước 4: Lưu trang dưới dạng JPEG với tùy chỉnh

Để lưu một trang cụ thể dưới dạng JPEG với các tùy chọn tùy chỉnh, hãy sử dụng mã này:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Bước 5: Sử dụng Page Saving Callback

Bạn có thể sử dụng lệnh gọi lại để tùy chỉnh việc lưu trang. Sau đây là một ví dụ:

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

## Mã nguồn đầy đủ để lưu hình ảnh từ tài liệu trong Aspose.Words cho Java

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
	// Đặt "PageSet" thành "0" để chỉ chuyển đổi trang đầu tiên của tài liệu.
	options.setPageSet(new PageSet(0));
	// Thay đổi độ sáng và độ tương phản của hình ảnh.
	// Cả hai đều có thang điểm từ 0-1 và mặc định là 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Thay đổi độ phân giải theo chiều ngang.
	// Giá trị mặc định cho các thuộc tính này là 96.0, cho độ phân giải 96dpi.
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

## Phần kết luận

Bạn đã học cách lưu hình ảnh từ tài liệu bằng Aspose.Words for Java. Các ví dụ này minh họa các tùy chọn tùy chỉnh khác nhau để lưu hình ảnh, bao gồm định dạng, nén và sử dụng lệnh gọi lại. Khám phá thêm nhiều khả năng với các khả năng mạnh mẽ của Aspose.Words for Java.

## Câu hỏi thường gặp

### Làm thế nào để thay đổi định dạng hình ảnh khi lưu bằng Aspose.Words cho Java?

Bạn có thể thay đổi định dạng hình ảnh bằng cách chỉ định định dạng mong muốn trong `ImageSaveOptions`. Ví dụ, để lưu dưới dạng PNG, hãy sử dụng `SaveFormat.PNG` như được hiển thị trong mã:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Tôi có thể tùy chỉnh cài đặt nén cho hình ảnh TIFF không?

Có, bạn có thể tùy chỉnh cài đặt nén hình ảnh TIFF. Ví dụ, để đặt phương pháp nén thành CCITT_3, hãy sử dụng mã sau:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Làm thế nào để lưu một trang cụ thể trong tài liệu dưới dạng hình ảnh riêng biệt?

Để lưu một trang cụ thể dưới dạng hình ảnh, hãy sử dụng `setPageSet` phương pháp trong `ImageSaveOptions`. Ví dụ, để chỉ lưu trang đầu tiên, hãy đặt `PageSet` ĐẾN `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Lưu trang đầu tiên dưới dạng hình ảnh
```

### Làm thế nào để áp dụng cài đặt tùy chỉnh cho ảnh JPEG khi lưu?

Bạn có thể áp dụng các thiết lập tùy chỉnh cho hình ảnh JPEG bằng cách sử dụng `ImageSaveOptions`. Điều chỉnh các thuộc tính như độ sáng, độ tương phản và độ phân giải. Ví dụ, để thay đổi độ sáng thành 0,3 và độ tương phản thành 0,7, hãy sử dụng mã này:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Tôi có thể sử dụng lệnh gọi lại để tùy chỉnh việc lưu hình ảnh như thế nào?

Để sử dụng lệnh gọi lại để tùy chỉnh việc lưu hình ảnh, hãy đặt `PageSavTRONGgCallback` in `ImageSaveOptions`. Tạo một lớp thực hiện `IPageSavingCallback` giao diện và ghi đè `pageSaving` phương pháp.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Sau đó, tạo một lớp thực hiện `IPageSavingCallback` giao diện và tùy chỉnh tên tệp và vị trí trong `pageSaving` phương pháp.

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