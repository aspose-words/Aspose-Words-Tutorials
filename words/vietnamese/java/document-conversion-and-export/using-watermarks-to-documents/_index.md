---
date: 2025-12-18
description: Tìm hiểu cách thêm watermark vào tài liệu bằng Aspose.Words cho Java,
  bao gồm ví dụ watermark hình ảnh, thay đổi màu watermark, thiết lập độ trong suốt
  của watermark và xóa watermark khỏi tài liệu.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Cách Thêm Đánh Dấu Nước vào Tài Liệu bằng Aspose.Words cho Java
url: /vi/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách Thêm Đánh Dấu Nước vào Tài Liệu Sử Dụng Aspose.Words cho Java

## Giới thiệu về việc Thêm Đánh Dấu Nước vào Tài Liệu trong Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ học **cách thêm đánh dấu nước** vào tài liệu Word bằng Aspose.Words cho Java. Đánh dấu nước là cách nhanh chóng để gắn nhãn một tệp là bí mật, bản nháp hoặc đã được phê duyệt, và chúng có thể là dạng văn bản hoặc hình ảnh. Chúng tôi sẽ hướng dẫn cách thiết lập thư viện, tạo đánh dấu nước dạng văn bản và hình ảnh, tùy chỉnh giao diện của chúng (bao gồm thay đổi màu đánh dấu nước và thiết lập độ trong suốt), và thậm chí loại bỏ đánh dấu nước khỏi tài liệu khi không còn cần thiết.

## Trả lời nhanh
- **Đánh dấu nước là gì?** Một lớp phủ bán trong suốt (văn bản hoặc hình ảnh) xuất hiện phía sau nội dung chính của tài liệu.  
- **Tôi có thể thêm nhiều đánh dấu nước không?** Có – tạo nhiều đối tượng `Shape` và thêm từng cái vào các phần mong muốn.  
- **Làm sao để thay đổi màu đánh dấu nước?** Điều chỉnh thuộc tính `Color` trong `TextWatermarkOptions`.  
- **Có ví dụ về đánh dấu nước hình ảnh không?** Xem phần “Thêm Đánh Dấu Nước Hình Ảnh” bên dưới.  
- **Có cần giấy phép để loại bỏ đánh dấu nước không?** Cần có giấy phép Aspose.Words hợp lệ cho việc sử dụng trong môi trường sản xuất.

## Thiết lập Aspose.Words cho Java

Trước khi bắt đầu thêm đánh dấu nước vào tài liệu, chúng ta cần thiết lập Aspose.Words cho Java. Thực hiện các bước sau để bắt đầu:

1. Tải Aspose.Words cho Java từ [đây](https://releases.aspose.com/words/java/).  
2. Thêm thư viện Aspose.Words cho Java vào dự án Java của bạn.  
3. Nhập các lớp cần thiết trong mã Java của bạn.

Bây giờ thư viện đã được thiết lập, chúng ta sẽ đi vào phần tạo đánh dấu nước thực tế.

## Thêm Đánh Dấu Nước Văn Bản

Đánh dấu nước dạng văn bản là lựa chọn phổ biến khi bạn muốn thêm thông tin văn bản vào tài liệu. Dưới đây là cách bạn có thể thêm một đánh dấu nước văn bản bằng Aspose.Words cho Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Tại sao điều này quan trọng:** Bằng cách điều chỉnh `setFontFamily`, `setFontSize`, và `setColor` bạn có thể **thay đổi màu đánh dấu nước** để phù hợp với thương hiệu, và `setSemitransparent(true)` cho phép bạn **đặt độ trong suốt cho đánh dấu nước** để tạo hiệu ứng nhẹ nhàng.

## Thêm Đánh Dấu Nước Hình Ảnh

Ngoài đánh dấu nước văn bản, bạn cũng có thể thêm đánh dấu nước hình ảnh vào tài liệu. Dưới đây là một **ví dụ đánh dấu nước hình ảnh** minh họa cách nhúng logo hoặc con dấu PNG:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Bạn có thể lặp lại khối này với các hình ảnh hoặc vị trí khác nhau để **thêm nhiều đánh dấu nước** vào một tệp duy nhất.

## Tùy Chỉnh Đánh Dấu Nước

Bạn có thể tùy chỉnh đánh dấu nước bằng cách điều chỉnh giao diện và vị trí của chúng. Đối với đánh dấu nước văn bản, bạn có thể thay đổi phông chữ, kích thước, màu sắc và bố cục. Đối với đánh dấu nước hình ảnh, bạn có thể sửa đổi kích thước, góc quay và căn chỉnh như đã trình bày trong các ví dụ trước.

## Loại Bỏ Đánh Dấu Nước

Nếu bạn cần **loại bỏ nội dung đánh dấu nước** khỏi tài liệu, đoạn mã sau sẽ duyệt qua tất cả các shape và xóa những shape được xác định là đánh dấu nước:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Các Trường Hợp Sử Dụng Thông Thường & Mẹo

- **Bản nháp bí mật:** Áp dụng một đánh dấu nước văn bản bán trong suốt như “CONFIDENTIAL”.  
- **Thương hiệu:** Sử dụng một đánh dấu nước hình ảnh chứa logo công ty của bạn.  
- **Đánh dấu nước cho từng phần:** Duyệt qua `doc.getSections()` và thêm đánh dấu nước chỉ vào các phần bạn chọn.  
- **Mẹo hiệu năng:** Tái sử dụng cùng một thể hiện `TextWatermarkOptions` khi áp dụng cùng một đánh dấu nước cho nhiều tài liệu.

## Câu Hỏi Thường Gặp

### Làm sao tôi có thể thay đổi phông chữ của một đánh dấu nước văn bản?

Để thay đổi phông chữ của một đánh dấu nước văn bản, sửa đổi thuộc tính `setFontFamily` trong `TextWatermarkOptions`. Ví dụ:

```java
options.setFontFamily("Times New Roman");
```

### Tôi có thể thêm nhiều đánh dấu nước vào một tài liệu duy nhất không?

Có, bạn có thể thêm nhiều đánh dấu nước vào tài liệu bằng cách tạo nhiều đối tượng `Shape` với các cài đặt khác nhau và thêm chúng vào tài liệu.

### Có thể xoay một đánh dấu nước không?

Có, bạn có thể xoay một đánh dấu nước bằng cách đặt thuộc tính `setRotation` trong đối tượng `Shape`. Giá trị dương sẽ quay đồng hồ, giá trị âm sẽ quay ngược chiều kim đồng hồ.

### Làm sao tôi có thể làm cho một đánh dấu nước bán trong suốt?

Để làm cho một đánh dấu nước bán trong suốt, đặt thuộc tính `setSemitransparent` thành `true` trong `TextWatermarkOptions`.

### Tôi có thể thêm đánh dấu nước vào các phần cụ thể của tài liệu không?

Có, bạn có thể thêm đánh dấu nước vào các phần cụ thể của tài liệu bằng cách duyệt qua các phần và thêm đánh dấu nước vào các phần mong muốn.

---

**Cập nhật lần cuối:** 2025-12-18  
**Kiểm tra với:** Aspose.Words cho Java 24.12  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}