---
"description": "Tìm hiểu cách thêm hình mờ vào tài liệu trong Aspose.Words cho Java. Tùy chỉnh hình mờ văn bản và hình ảnh cho tài liệu trông chuyên nghiệp."
"linktitle": "Sử dụng hình mờ cho tài liệu"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Sử dụng Watermark cho Tài liệu trong Aspose.Words cho Java"
"url": "/vi/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Watermark cho Tài liệu trong Aspose.Words cho Java


## Giới thiệu về cách thêm hình mờ vào tài liệu trong Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách thêm hình mờ vào tài liệu bằng cách sử dụng Aspose.Words for Java API. Hình mờ là một cách hữu ích để dán nhãn tài liệu bằng văn bản hoặc đồ họa để chỉ ra trạng thái, tính bảo mật hoặc thông tin liên quan khác. Chúng tôi sẽ đề cập đến cả hình mờ văn bản và hình ảnh trong hướng dẫn này.

## Thiết lập Aspose.Words cho Java

Trước khi bắt đầu thêm hình mờ vào tài liệu, chúng ta cần thiết lập Aspose.Words cho Java. Thực hiện theo các bước sau để bắt đầu:

1. Tải xuống Aspose.Words cho Java từ [đây](https://releases.aspose.com/words/java/).
2. Thêm thư viện Aspose.Words cho Java vào dự án Java của bạn.
3. Nhập các lớp cần thiết vào mã Java của bạn.

Bây giờ chúng ta đã thiết lập xong thư viện, hãy tiến hành thêm hình mờ.

## Thêm hình mờ văn bản

Hình mờ văn bản là lựa chọn phổ biến khi bạn muốn thêm thông tin văn bản vào tài liệu của mình. Sau đây là cách bạn có thể thêm hình mờ văn bản bằng Aspose.Words for Java:

```java
// Tạo một phiên bản Tài liệu
Document doc = new Document("Document.docx");

// Định nghĩa TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Đặt văn bản hình mờ và các tùy chọn
doc.getWatermark().setText("Test", options);

// Lưu tài liệu có hình mờ
doc.save("DocumentWithWatermark.docx");
```

## Thêm hình mờ cho hình ảnh

Ngoài hình mờ văn bản, bạn cũng có thể thêm hình mờ hình ảnh vào tài liệu của mình. Sau đây là cách thêm hình mờ hình ảnh:

```java
// Tạo một phiên bản Tài liệu
Document doc = new Document("Document.docx");

// Tải hình ảnh cho hình mờ
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Đặt kích thước và vị trí hình mờ
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Thêm hình mờ vào tài liệu
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Lưu tài liệu có hình mờ
doc.save("DocumentWithImageWatermark.docx");
```

## Tùy chỉnh hình mờ

Bạn có thể tùy chỉnh hình mờ bằng cách điều chỉnh giao diện và vị trí của chúng. Đối với hình mờ văn bản, bạn có thể thay đổi phông chữ, kích thước, màu sắc và bố cục. Đối với hình mờ hình ảnh, bạn có thể sửa đổi kích thước và vị trí của chúng như đã trình bày trong các ví dụ trước.

## Xóa hình mờ

Để xóa hình mờ khỏi tài liệu, bạn có thể sử dụng mã sau:

```java
// Tạo một phiên bản Tài liệu
Document doc = new Document("DocumentWithWatermark.docx");

// Xóa hình mờ
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Lưu tài liệu mà không có hình mờ
doc.save("DocumentWithoutWatermark.docx");
```


## Phần kết luận

Trong hướng dẫn này, chúng ta đã học cách thêm hình mờ vào tài liệu bằng Aspose.Words for Java. Cho dù bạn cần thêm hình mờ văn bản hay hình ảnh, Aspose.Words đều cung cấp các công cụ để tùy chỉnh và quản lý chúng một cách hiệu quả. Bạn cũng có thể xóa hình mờ khi không còn cần thiết nữa, đảm bảo tài liệu của bạn sạch sẽ và chuyên nghiệp.

## Câu hỏi thường gặp

### Làm thế nào để thay đổi phông chữ của hình mờ văn bản?

Để thay đổi phông chữ của hình mờ văn bản, hãy sửa đổi `setFontFamily` tài sản trong `TextWatermarkOptions`. Ví dụ:

```java
options.setFontFamily("Times New Roman");
```

### Tôi có thể thêm nhiều hình mờ vào một tài liệu không?

Có, bạn có thể thêm nhiều hình mờ vào một tài liệu bằng cách tạo nhiều `Shape` các đối tượng có thiết lập khác nhau và thêm chúng vào tài liệu.

### Có thể xoay hình mờ được không?

Có, bạn có thể xoay hình mờ bằng cách thiết lập `setRotation` tài sản trong `Shape` đối tượng. Giá trị dương sẽ xoay hình mờ theo chiều kim đồng hồ, giá trị âm sẽ xoay ngược chiều kim đồng hồ.

### Làm thế nào để tạo hình mờ bán trong suốt?

Để làm cho hình mờ trong suốt một nửa, hãy đặt `setSemitransparent` tài sản để `true` trong `TextWatermarkOptions`.

### Tôi có thể thêm hình mờ vào các phần cụ thể của tài liệu không?

Có, bạn có thể thêm hình mờ vào các phần cụ thể của tài liệu bằng cách lặp lại các phần và thêm hình mờ vào các phần mong muốn.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}