---
date: 2025-12-27
description: Tìm hiểu cách lưu trang dưới dạng JPEG và trích xuất hình ảnh từ tài
  liệu Word bằng Aspose.Words cho Java. Bao gồm các mẹo về việc thiết lập độ sáng,
  độ phân giải của hình ảnh và tạo TIFF đa trang.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Cách lưu trang dưới dạng JPEG và trích xuất hình ảnh từ tài liệu bằng Aspose.Words
  cho Java
url: /vi/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Lưu trang dưới dạng JPEG và Trích xuất Hình ảnh từ Tài liệu trong Aspose.Words cho Java

Trong tutorial này, bạn sẽ khám phá cách **save page as jpeg** từ một tài liệu Word và cách **extract images from Word** bằng Aspose.Words cho Java. Chúng tôi sẽ hướng dẫn qua các kịch bản thực tế như thiết lập độ sáng hình ảnh, điều chỉnh độ phân giải hình ảnh trong Java, và tạo TIFF đa trang. Mỗi bước đều bao gồm các đoạn mã sẵn sàng chạy để bạn có thể sao chép, dán và xem kết quả ngay lập tức.

## Trả lời nhanh
- **Tôi có thể lưu một trang duy nhất dưới dạng JPEG không?** Có – sử dụng `ImageSaveOptions` với `setPageSet(new PageSet(pageIndex))`.
- **Làm thế nào để thay đổi độ sáng hình ảnh?** Gọi `options.setImageBrightness(floatValue)` (phạm vi 0‑1).
- **Nếu tôi cần một TIFF đa trang thì sao?** Đặt một `PageSet` bao phủ các trang mong muốn và chọn phương pháp nén TIFF.
- **Làm sao kiểm soát độ phân giải hình ảnh?** Sử dụng `setResolution(floatDpi)` hoặc `setHorizontalResolution(floatDpi)`.
- **Có cần giấy phép cho môi trường production không?** Cần một giấy phép Aspose.Words hợp lệ cho việc sử dụng không phải bản dùng thử.

## “save page as jpeg” là gì?
Lưu một trang dưới dạng JPEG có nghĩa là chuyển đổi một trang duy nhất của tài liệu Word thành một tệp ảnh raster (JPEG). Điều này hữu ích cho việc tạo preview, tạo thumbnail, hoặc nhúng các trang tài liệu vào trang web khi việc hiển thị PDF không thực tế.

## Tại sao cần trích xuất hình ảnh từ tài liệu Word?
Nhiều quy trình kinh doanh yêu cầu lấy ra các đồ họa gốc (logo, sơ đồ, ảnh) từ tệp DOCX để tái sử dụng, lưu trữ, hoặc phân tích. Aspose.Words giúp trích xuất mỗi hình ảnh ở định dạng gốc mà không làm mất chất lượng.

## Yêu cầu trước
- Java Development Kit (JDK 8 trở lên) đã được cài đặt.
- Thư viện Aspose.Words cho Java đã được thêm vào dự án. Tải về từ [here](https://releases.aspose.com/words/java/).
- Một tài liệu Word mẫu (ví dụ: `Rendering.docx`) được đặt trong thư mục đã biết.

## Bước 1: Lưu hình ảnh dưới dạng TIFF với kiểm soát ngưỡng (Tạo TIFF đa trang)
Để tạo một TIFF độ tương phản cao, thang xám, bạn có thể kiểm soát ngưỡng nhị phân. Điều này hữu ích khi cần một phiên bản in đen‑trắng của tài liệu.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Bước 2: Lưu một trang cụ thể dưới dạng TIFF đa trang
Nếu bạn cần một TIFF chỉ chứa một tập hợp các trang (ví dụ: trang 1‑2), hãy cấu hình một `PageSet`. Điều này minh họa **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Bước 3: Lưu hình ảnh dưới dạng PNG Indexed 1 BPP
Khi bạn cần PNG đen‑trắng siêu nhẹ (1 bit mỗi pixel), hãy đặt định dạng pixel cho phù hợp. Thích hợp cho việc nhúng đồ họa đơn giản trong các kịch bản băng thông thấp.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Bước 4: Lưu một trang dưới dạng JPEG với tùy chỉnh (Đặt độ sáng & độ phân giải ảnh)
Ở đây chúng ta **save page as jpeg** đồng thời điều chỉnh độ sáng, độ tương phản và độ phân giải — hoàn hảo để tạo thumbnail hoặc preview chuẩn web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Bước 5: Sử dụng Callback khi lưu trang (Tùy chỉnh nâng cao)
Callback cho phép bạn đổi tên mỗi tệp đầu ra một cách động, hữu ích khi xuất nhiều trang cùng lúc.

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

## Mã nguồn hoàn chỉnh cho tất cả các kịch bản
Dưới đây là một lớp duy nhất chứa mọi phương thức đã trình bày ở trên. Bạn có thể chạy từng test riêng lẻ.

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

## Các vấn đề thường gặp và giải pháp
- **“Unable to locate the document file”** – Kiểm tra lại đường dẫn tệp, đảm bảo sử dụng dấu phân cách đúng (`/` hoặc `\\`) cho hệ điều hành của bạn.
- **Hình ảnh xuất ra trống** – Đảm bảo bạn đã đặt `ImageColorMode` phù hợp (ví dụ: `GRAYSCALE` cho TIFF).
- **Lỗi out‑of‑memory trên tài liệu lớn** – Xử lý các trang theo lô bằng cách điều chỉnh phạm vi `PageSet`.
- **Chất lượng JPEG kém** – Tăng độ phân giải bằng `setHorizontalResolution` hoặc `setResolution`.

## Câu hỏi thường gặp

**Q: Làm thế nào để thay đổi định dạng ảnh khi lưu bằng Aspose.Words cho Java?**  
A: Đặt định dạng mong muốn trong `ImageSaveOptions`. Đối với PNG, bạn chỉ cần khởi tạo `ImageSaveOptions` và gán `SaveFormat.PNG` nếu cần.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Tôi có thể tùy chỉnh cài đặt nén cho ảnh TIFF không?**  
A: Có. Sử dụng `setTiffCompression` để chọn thuật toán nén như `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Làm sao tôi có thể lưu một trang cụ thể từ tài liệu dưới dạng ảnh riêng?**  
A: Dùng phương thức `setPageSet` với một chỉ số trang duy nhất.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Làm thế nào để áp dụng các cài đặt tùy chỉnh cho ảnh JPEG khi lưu?**  
A: Điều chỉnh các thuộc tính như độ sáng, độ tương phản và độ phân giải qua `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Làm sao tôi có thể sử dụng callback để tùy chỉnh việc lưu ảnh?**  
A: Triển khai `IPageSavingCallback` và gán nó bằng `setPageSavingCallback`.

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

## Kết luận
Bạn đã có một bộ công cụ hoàn chỉnh để **save page as jpeg**, trích xuất hình ảnh, kiểm soát độ sáng ảnh, thiết lập độ phân giải ảnh trong Java, và tạo các tệp TIFF đa trang với Aspose.Words cho Java. Hãy thử nghiệm các cài đặt `ImageSaveOptions` khác nhau để phù hợp với nhu cầu dự án của bạn, và khám phá thêm API Aspose.Words để thực hiện các thao tác xử lý tài liệu phong phú hơn.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}