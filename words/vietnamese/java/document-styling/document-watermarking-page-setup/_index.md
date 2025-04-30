---
"description": "Tìm hiểu cách áp dụng hình mờ và thiết lập cấu hình trang bằng Aspose.Words cho Java. Hướng dẫn toàn diện với mã nguồn."
"linktitle": "Đóng dấu bản quyền tài liệu và thiết lập trang"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Đóng dấu bản quyền tài liệu và thiết lập trang"
"url": "/vi/java/document-styling/document-watermarking-page-setup/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Đóng dấu bản quyền tài liệu và thiết lập trang

## Giới thiệu

Trong lĩnh vực xử lý tài liệu, Aspose.Words for Java là một công cụ mạnh mẽ, cho phép các nhà phát triển kiểm soát mọi khía cạnh của quá trình xử lý tài liệu. Trong hướng dẫn toàn diện này, chúng ta sẽ đi sâu vào sự phức tạp của việc đóng dấu bản quyền tài liệu và thiết lập trang bằng Aspose.Words for Java. Cho dù bạn là một nhà phát triển dày dạn kinh nghiệm hay chỉ mới bước vào thế giới xử lý tài liệu Java, hướng dẫn từng bước này sẽ trang bị cho bạn kiến thức và mã nguồn bạn cần.

## Đóng dấu tài liệu

### Thêm hình mờ

Thêm hình mờ vào tài liệu có thể rất quan trọng đối với việc xây dựng thương hiệu hoặc bảo mật nội dung của bạn. Aspose.Words for Java giúp bạn thực hiện nhiệm vụ này một cách đơn giản. Sau đây là cách thực hiện:

```java
// Tải tài liệu
Document doc = new Document("document.docx");

// Tạo hình mờ
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// Vị trí hình mờ
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// Chèn hình mờ
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Lưu tài liệu
doc.save("document_with_watermark.docx");
```

### Tùy chỉnh hình mờ

Bạn có thể tùy chỉnh thêm hình mờ bằng cách điều chỉnh phông chữ, kích thước, màu sắc và xoay. Tính linh hoạt này đảm bảo hình mờ của bạn phù hợp với phong cách của tài liệu một cách liền mạch.

## Thiết lập trang

### Kích thước và hướng trang

Thiết lập trang là then chốt trong việc định dạng tài liệu. Aspose.Words for Java cung cấp khả năng kiểm soát hoàn toàn kích thước và hướng trang:

```java
// Tải tài liệu
Document doc = new Document("document.docx");

// Đặt kích thước trang thành A4
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// Thay đổi hướng trang thành ngang
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// Lưu tài liệu đã sửa đổi
doc.save("formatted_document.docx");
```

### Lề và Đánh số trang

Kiểm soát chính xác lề và đánh số trang là điều cần thiết cho các tài liệu chuyên nghiệp. Thực hiện điều này với Aspose.Words for Java:

```java
// Tải tài liệu
Document doc = new Document("document.docx");

// Đặt lề
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// Bật đánh số trang
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// Lưu tài liệu đã định dạng
doc.save("formatted_document.docx");
```

## Câu hỏi thường gặp

### Làm thế nào để xóa hình mờ khỏi tài liệu?

Để xóa hình mờ khỏi tài liệu, bạn có thể lặp lại các hình dạng của tài liệu và xóa những hình dạng đại diện cho hình mờ. Sau đây là một đoạn trích:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### Tôi có thể thêm nhiều hình mờ vào một tài liệu không?

Có, bạn có thể thêm nhiều hình mờ vào tài liệu bằng cách tạo thêm các đối tượng Hình dạng và định vị chúng khi cần.

### Làm thế nào để thay đổi kích thước trang thành khổ legal khi định hướng ngang?

Để đặt kích thước trang theo chiều ngang, hãy sửa đổi chiều rộng và chiều cao của trang như sau:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### Phông chữ mặc định cho hình mờ là gì?

Phông chữ mặc định cho hình mờ là Calibri với cỡ chữ là 36.

### Làm thế nào để thêm số trang bắt đầu từ một trang cụ thể?

Bạn có thể thực hiện điều này bằng cách thiết lập số trang bắt đầu trong tài liệu của mình như sau:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### Làm thế nào để căn giữa văn bản ở đầu trang hoặc chân trang?

Bạn có thể căn giữa văn bản ở phần đầu trang hoặc phần chân trang bằng cách sử dụng phương thức setAlignment trên đối tượng Paragraph trong phần đầu trang hoặc phần chân trang.

## Phần kết luận

Trong hướng dẫn mở rộng này, chúng tôi đã khám phá nghệ thuật đóng dấu bản quyền tài liệu và thiết lập trang bằng Aspose.Words for Java. Được trang bị các đoạn mã nguồn và thông tin chi tiết được cung cấp, giờ đây bạn sở hữu các công cụ để thao tác và định dạng tài liệu của mình một cách tinh tế. Aspose.Words for Java cho phép bạn tạo các tài liệu chuyên nghiệp, có thương hiệu phù hợp với thông số kỹ thuật chính xác của bạn.

Thành thạo thao tác tài liệu là một kỹ năng có giá trị đối với các nhà phát triển và Aspose.Words for Java là người bạn đồng hành đáng tin cậy của bạn trong hành trình này. Hãy bắt đầu tạo các tài liệu tuyệt đẹp ngay hôm nay!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}