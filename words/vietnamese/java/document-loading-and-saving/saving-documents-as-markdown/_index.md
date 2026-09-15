---
date: 2025-12-22
description: Tìm hiểu cách xuất markdown bằng cách chuyển đổi tài liệu Word sang Markdown
  với Aspose.Words for Java. Hướng dẫn từng bước này bao gồm căn chỉnh bảng, xử lý
  hình ảnh và nhiều hơn nữa.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Cách xuất Markdown bằng Aspose.Words cho Java
url: /vi/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách xuất Markdown với Aspose.Words cho Java

## Giới thiệu về việc xuất Markdown trong Aspose.Words cho Java

Trong hướng dẫn từng bước này, **bạn sẽ học cách xuất markdown** từ các tài liệu Word bằng Aspose.Words cho Java. Markdown là một ngôn ngữ đánh dấu nhẹ, phù hợp cho tài liệu, các trình tạo trang tĩnh và nhiều nền tảng xuất bản. Khi kết thúc hướng dẫn này, bạn sẽ có thể **chuyển đổi Word sang markdown**, tùy chỉnh căn chỉnh bảng, và **xử lý hình ảnh trong markdown** một cách dễ dàng.

## Câu trả lời nhanh
- **Lớp chính để lưu dưới dạng Markdown là gì?** `MarkdownSaveOptions`
- **Hình ảnh có thể được nhúng tự động không?** Có – đặt thư mục hình ảnh bằng `setImagesFolder`.
- **Làm sao để kiểm soát căn chỉnh bảng?** Sử dụng `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Yêu cầu tối thiểu là gì?** JDK 8+ và thư viện Aspose.Words cho Java.
- **Có phiên bản dùng thử không?** Có, tải xuống từ trang web Aspose.

## Export markdown là gì?
Xuất markdown có nghĩa là chuyển một tài liệu Word dạng rich‑text (`.docx`) thành một tệp văn bản thuần `.md` giữ lại các tiêu đề, bảng và hình ảnh theo cú pháp Markdown.

## Tại sao nên dùng Aspose.Words cho Java để chuyển đổi docx có hình ảnh?
Aspose.Words xử lý các bố cục phức tạp, hình ảnh nhúng và cấu trúc bảng mà không mất độ chính xác. Nó cũng cung cấp cho bạn khả năng kiểm soát chi tiết đầu ra Markdown, như căn chỉnh bảng và quản lý thư mục hình ảnh.

## Yêu cầu trước
- Java Development Kit (JDK) đã được cài đặt trên hệ thống của bạn.
- Thư viện Aspose.Words cho Java. Bạn có thể tải xuống từ [here](https://releases.aspose.com/words/java/).

## Bước 1: Tạo một tài liệu Word đơn giản
Đầu tiên, chúng ta sẽ tạo một tài liệu nhỏ có chứa một bảng. Điều này sẽ cho phép chúng ta minh họa **tùy chỉnh căn chỉnh bảng** sau này.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Trong đoạn mã trên chúng ta:

1. Tạo một `Document` mới.
2. Sử dụng `DocumentBuilder` để chèn một bảng hai ô.
3. Áp dụng căn chỉnh đoạn văn **phải** và **giữa** trong mỗi ô.
4. Lưu tệp dưới dạng Markdown bằng `MarkdownSaveOptions`.

## Bước 2: Tùy chỉnh căn chỉnh nội dung bảng
Aspose.Words cho phép bạn chỉ định cách các ô bảng được hiển thị trong Markdown cuối cùng. Bạn có thể buộc căn trái, phải, giữa, hoặc để thư viện tự động quyết định dựa trên đoạn văn đầu tiên của mỗi cột.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Bằng cách chuyển đổi thuộc tính `TableContentAlignment`, bạn kiểm soát **tùy chỉnh căn chỉnh bảng** cho đầu ra Markdown.

## Bước 3: Xử lý hình ảnh khi xuất sang markdown
Khi một tài liệu chứa hình ảnh, bạn sẽ muốn các hình ảnh đó hiển thị đúng trong tệp `.md` được tạo. Đặt thư mục mà Aspose.Words sẽ lưu các hình ảnh đã trích xuất.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Thay thế `"document_with_images.docx"` bằng đường dẫn tới tệp nguồn của bạn và `"images_folder/"` bằng vị trí bạn muốn lưu các hình ảnh. Markdown kết quả sẽ chứa các liên kết hình ảnh trỏ tới thư mục này, cho phép bạn **xử lý hình ảnh trong markdown** một cách liền mạch.

## Mã nguồn hoàn chỉnh để lưu tài liệu dưới dạng Markdown trong Aspose.Words cho Java
```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Các vấn đề thường gặp và giải pháp
| Vấn đề | Giải pháp |
|-------|----------|
| Hình ảnh không hiển thị trong tệp `.md` | Kiểm tra rằng `setImagesFolder` trỏ tới một thư mục có thể ghi và thư mục này được tham chiếu đúng trong Markdown được tạo. |
| Căn chỉnh bảng bị lệch | Sử dụng `TableContentAlignment.AUTO` để cho Aspose.Words suy ra căn chỉnh tốt nhất dựa trên đoạn văn đầu tiên của mỗi cột. |
| Tệp đầu ra rỗng | Đảm bảo đối tượng `Document` thực sự chứa nội dung trước khi gọi `save`. |

## Câu hỏi thường gặp
**Q: Làm thế nào để cài đặt Aspose.Words cho Java?**  
**A:** Aspose.Words cho Java có thể được cài đặt bằng cách bao gồm thư viện trong dự án Java của bạn. Bạn có thể tải thư viện từ [here](https://releases.aspose.com/words/java/) và làm theo hướng dẫn cài đặt được cung cấp trong tài liệu.

**Q: Tôi có thể chuyển đổi các tài liệu Word phức tạp có bảng và hình ảnh sang Markdown không?**  
**A:** Có, Aspose.Words cho Java hỗ trợ chuyển đổi các tài liệu Word phức tạp có bảng, hình ảnh và các yếu tố định dạng khác sang Markdown. Bạn có thể tùy chỉnh đầu ra Markdown theo độ phức tạp của tài liệu.

**Q: Làm sao tôi có thể xử lý hình ảnh trong các tệp Markdown?**  
**A:** Đặt đường dẫn thư mục hình ảnh bằng phương thức `setImagesFolder` trong `MarkdownSaveOptions`. Đảm bảo các tệp hình ảnh được lưu trong thư mục đã chỉ định; Aspose.Words sẽ tạo các liên kết hình ảnh Markdown phù hợp.

**Q: Có phiên bản dùng thử của Aspose.Words cho Java không?**  
**A:** Có, bạn có thể nhận phiên bản dùng thử của Aspose.Words cho Java từ trang web Aspose. Phiên bản dùng thử cho phép bạn đánh giá khả năng của thư viện trước khi mua giấy phép.

**Q: Tôi có thể tìm thêm ví dụ và tài liệu ở đâu?**  
**A:** Để xem thêm ví dụ, tài liệu và thông tin chi tiết về Aspose.Words cho Java, vui lòng truy cập [documentation](https://reference.aspose.com/words/java/).

---

**Cập nhật lần cuối:** 2025-12-22  
**Kiểm tra với:** Aspose.Words cho Java 24.12 (phiên bản mới nhất tại thời điểm viết)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}