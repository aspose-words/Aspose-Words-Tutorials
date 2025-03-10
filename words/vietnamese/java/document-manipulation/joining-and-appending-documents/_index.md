---
title: Nối và Thêm Tài liệu trong Aspose.Words cho Java
linktitle: Tham gia và Thêm tài liệu
second_title: API xử lý tài liệu Java Aspose.Words
description: Tìm hiểu cách nối và thêm tài liệu dễ dàng bằng Aspose.Words for Java. Giữ nguyên định dạng, quản lý tiêu đề, chân trang và nhiều hơn nữa.
weight: 30
url: /vi/java/document-manipulation/joining-and-appending-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nối và Thêm Tài liệu trong Aspose.Words cho Java


## Giới thiệu về việc nối và thêm tài liệu trong Aspose.Words cho Java

Trong hướng dẫn này, chúng ta sẽ khám phá cách nối và thêm tài liệu bằng thư viện Aspose.Words cho Java. Bạn sẽ học cách hợp nhất nhiều tài liệu một cách liền mạch trong khi vẫn giữ nguyên định dạng và cấu trúc.

## Điều kiện tiên quyết

Trước khi bắt đầu, hãy đảm bảo bạn đã thiết lập Aspose.Words for Java API trong dự án Java của mình.

## Tùy chọn tham gia tài liệu

### Thêm đơn giản

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Thêm vào với Tùy chọn Định dạng Nhập

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Thêm vào tài liệu trống

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Thêm vào với Chuyển đổi Số trang

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Chuyển đổi các trường NUMPAGES
dstDoc.updatePageLayout(); // Cập nhật bố cục trang để đánh số chính xác
```

## Xử lý các thiết lập trang khác nhau

Khi thêm tài liệu có thiết lập trang khác nhau:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Đảm bảo cài đặt thiết lập trang khớp với tài liệu đích
```

## Nối các tài liệu có nhiều kiểu khác nhau

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Hành vi phong cách thông minh

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Chèn tài liệu bằng DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Giữ lại số nguồn

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Xử lý hộp văn bản

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Quản lý Header và Footer

### Liên kết Header và Footer

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Hủy liên kết Header và Footer

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Phần kết luận

Aspose.Words for Java cung cấp các công cụ linh hoạt và mạnh mẽ để nối và thêm tài liệu, cho dù bạn cần duy trì định dạng, xử lý các thiết lập trang khác nhau hay quản lý tiêu đề và chân trang. Hãy thử nghiệm các kỹ thuật này để đáp ứng nhu cầu xử lý tài liệu cụ thể của bạn.

## Câu hỏi thường gặp

### Làm thế nào tôi có thể ghép các tài liệu có nhiều kiểu khác nhau một cách liền mạch?

 Để nối các tài liệu có nhiều kiểu khác nhau, hãy sử dụng`ImportFormatMode.USE_DESTINATION_STYLES` khi thêm vào.

### Tôi có thể giữ nguyên số trang khi thêm tài liệu không?

 Có, bạn có thể giữ nguyên số trang bằng cách sử dụng`convertNumPageFieldsToPageRef` phương pháp và cập nhật bố cục trang.

### Hành vi phong cách thông minh là gì?

 Hành vi phong cách thông minh giúp duy trì các phong cách nhất quán khi thêm tài liệu. Sử dụng nó với`ImportFormatOptions` để có kết quả tốt hơn.

### Tôi có thể xử lý hộp văn bản khi thêm tài liệu như thế nào?

Bộ`importFormatOptions.setIgnoreTextBoxes(false)` để bao gồm các hộp văn bản trong khi thêm vào.

### Tôi phải làm sao nếu muốn liên kết/hủy liên kết phần đầu trang và phần chân trang giữa các tài liệu?

 Bạn có thể liên kết tiêu đề và chân trang với`linkToPrevious(true)` hoặc hủy liên kết chúng với`linkToPrevious(false)` khi cần thiết.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
