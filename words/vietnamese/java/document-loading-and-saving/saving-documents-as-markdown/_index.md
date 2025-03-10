---
title: Lưu tài liệu dưới dạng Markdown trong Aspose.Words cho Java
linktitle: Lưu tài liệu dưới dạng Markdown
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu cách chuyển đổi tài liệu Word sang Markdown bằng Aspose.Words for Java. Hướng dẫn từng bước này bao gồm căn chỉnh bảng, xử lý hình ảnh và nhiều hơn nữa.
weight: 18
url: /vi/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tài liệu dưới dạng Markdown trong Aspose.Words cho Java


## Giới thiệu về cách lưu tài liệu dưới dạng Markdown trong Aspose.Words cho Java

Trong hướng dẫn từng bước này, chúng tôi sẽ trình bày cách lưu tài liệu dưới dạng Markdown bằng Aspose.Words for Java. Markdown là ngôn ngữ đánh dấu nhẹ thường được sử dụng để định dạng tài liệu văn bản. Với Aspose.Words for Java, bạn có thể dễ dàng chuyển đổi tài liệu Word của mình sang định dạng Markdown. Chúng tôi sẽ đề cập đến các khía cạnh khác nhau của việc lưu tệp Markdown, bao gồm căn chỉnh nội dung bảng và xử lý hình ảnh.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn có đủ các điều kiện tiên quyết sau:

- Bộ công cụ phát triển Java (JDK) được cài đặt trên hệ thống của bạn.
-  Aspose.Words cho thư viện Java. Bạn có thể tải xuống từ[đây](https://releases.aspose.com/words/java/).

## Bước 1: Tạo một tài liệu Word

Hãy bắt đầu bằng cách tạo một tài liệu Word mà sau này chúng ta sẽ chuyển đổi sang định dạng Markdown. Bạn có thể tùy chỉnh tài liệu này theo yêu cầu của mình.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Chèn một bảng có hai ô
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Lưu tài liệu dưới dạng Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 Trong ví dụ này, chúng ta tạo một bảng đơn giản với hai ô và thiết lập căn chỉnh các đoạn văn trong các ô này. Sau đó, chúng ta lưu tài liệu dưới dạng Markdown bằng cách sử dụng`MarkdownSaveOptions`.

## Bước 2: Tùy chỉnh Căn chỉnh Nội dung Bảng

Aspose.Words for Java cho phép bạn tùy chỉnh căn chỉnh nội dung bảng khi lưu dưới dạng Markdown. Bạn có thể căn chỉnh nội dung bảng sang trái, phải, giữa hoặc để tự động xác định dựa trên đoạn văn đầu tiên trong mỗi cột bảng.

Sau đây là cách tùy chỉnh căn chỉnh nội dung bảng:

```java
// Đặt căn chỉnh nội dung bảng sang trái
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Đặt căn chỉnh nội dung bảng sang phải
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Đặt căn chỉnh nội dung bảng thành chính giữa
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Đặt căn chỉnh nội dung bảng thành tự động (xác định bởi đoạn đầu tiên)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Bằng cách thay đổi`TableContentAlignment` thuộc tính, bạn có thể kiểm soát cách căn chỉnh nội dung bên trong bảng khi chuyển đổi sang Markdown.

## Bước 3: Xử lý hình ảnh

 Để bao gồm hình ảnh trong tài liệu Markdown của bạn, bạn cần chỉ định thư mục chứa hình ảnh. Aspose.Words for Java cho phép bạn đặt thư mục hình ảnh trong`MarkdownSaveOptions`.

Sau đây là cách thiết lập thư mục hình ảnh và lưu tài liệu có hình ảnh:

```java
// Tải một tài liệu có chứa hình ảnh
Document doc = new Document("document_with_images.docx");

// Đặt đường dẫn thư mục hình ảnh
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Lưu tài liệu có hình ảnh
doc.save("document_with_images.md", saveOptions);
```

 Hãy chắc chắn thay thế`"document_with_images.docx"` với đường dẫn đến tài liệu Word của bạn có chứa hình ảnh và`"images_folder/"` với đường dẫn thực tế đến thư mục lưu trữ hình ảnh của bạn.

## Mã nguồn đầy đủ để lưu tài liệu dưới dạng Markdown trong Aspose.Words cho Java

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
	// Làm cho tất cả các đoạn văn bên trong bảng được căn chỉnh.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Trong trường hợp này, việc căn chỉnh sẽ được thực hiện từ đoạn văn đầu tiên trong cột bảng tương ứng.
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

## Phần kết luận

Trong hướng dẫn này, chúng tôi đã khám phá cách lưu tài liệu dưới dạng Markdown bằng Aspose.Words for Java. Chúng tôi đã đề cập đến việc tạo tài liệu Word, tùy chỉnh căn chỉnh nội dung bảng và xử lý hình ảnh trong tệp Markdown. Bây giờ bạn có thể chuyển đổi hiệu quả tài liệu Word của mình sang định dạng Markdown, giúp chúng phù hợp với nhiều nền tảng xuất bản và nhu cầu lập tài liệu khác nhau.

## Câu hỏi thường gặp

### Làm thế nào để cài đặt Aspose.Words cho Java?

 Aspose.Words for Java có thể được cài đặt bằng cách đưa thư viện vào dự án Java của bạn. Bạn có thể tải xuống thư viện từ[đây](https://releases.aspose.com/words/java/) và làm theo hướng dẫn cài đặt được cung cấp trong tài liệu.

### Tôi có thể chuyển đổi các tài liệu Word phức tạp có bảng và hình ảnh sang Markdown không?

Có, Aspose.Words for Java hỗ trợ chuyển đổi các tài liệu Word phức tạp có bảng, hình ảnh và nhiều thành phần định dạng khác nhau sang Markdown. Bạn có thể tùy chỉnh đầu ra Markdown theo độ phức tạp của tài liệu.

### Tôi có thể xử lý hình ảnh trong tệp Markdown như thế nào?

 Để bao gồm hình ảnh trong các tệp Markdown, hãy đặt đường dẫn thư mục hình ảnh bằng cách sử dụng`setImagesFolder`phương pháp trong`MarkdownSaveOptions`. Đảm bảo rằng các tệp hình ảnh được lưu trữ trong thư mục đã chỉ định và Aspose.Words for Java sẽ xử lý các tham chiếu hình ảnh cho phù hợp.

### Có phiên bản dùng thử của Aspose.Words cho Java không?

Có, bạn có thể tải phiên bản dùng thử của Aspose.Words for Java từ trang web Aspose. Phiên bản dùng thử cho phép bạn đánh giá khả năng của thư viện trước khi mua giấy phép.

### Tôi có thể tìm thêm ví dụ và tài liệu ở đâu?

 Để biết thêm ví dụ, tài liệu và thông tin chi tiết về Aspose.Words cho Java, vui lòng truy cập[tài liệu](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
