---
"description": "Tối ưu hóa quản lý tài liệu với Aspose.Words for Java. Tìm hiểu cách làm việc với các thuộc tính tài liệu, thêm siêu dữ liệu tùy chỉnh và nhiều hơn nữa trong hướng dẫn toàn diện này."
"linktitle": "Sử dụng Thuộc tính Tài liệu"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Sử dụng Thuộc tính Tài liệu trong Aspose.Words cho Java"
"url": "/vi/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sử dụng Thuộc tính Tài liệu trong Aspose.Words cho Java


## Giới thiệu về Thuộc tính Tài liệu

Thuộc tính tài liệu là một phần quan trọng của bất kỳ tài liệu nào. Chúng cung cấp thông tin bổ sung về chính tài liệu, chẳng hạn như tiêu đề, tác giả, chủ đề, từ khóa, v.v. Trong Aspose.Words for Java, bạn có thể thao tác cả thuộc tính tài liệu tích hợp và tùy chỉnh.

## Liệt kê các thuộc tính của tài liệu

### Thuộc tính tích hợp

Để truy xuất và làm việc với các thuộc tính tài liệu tích hợp, bạn có thể sử dụng đoạn mã sau:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Mã này sẽ hiển thị tên tài liệu và các thuộc tính tích hợp, bao gồm các thuộc tính như "Tiêu đề", "Tác giả" và "Từ khóa".

### Thuộc tính tùy chỉnh

Để làm việc với các thuộc tính tài liệu tùy chỉnh, bạn có thể sử dụng đoạn mã sau:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Đoạn mã này trình bày cách thêm các thuộc tính tùy chỉnh của tài liệu, bao gồm giá trị boolean, chuỗi, ngày, số bản sửa đổi và giá trị số.

## Xóa Thuộc tính Tài liệu

Để xóa các thuộc tính cụ thể của tài liệu, bạn có thể sử dụng đoạn mã sau:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Mã này xóa thuộc tính tùy chỉnh "Ngày được ủy quyền" khỏi tài liệu.

## Cấu hình liên kết đến nội dung

Trong một số trường hợp, bạn có thể muốn tạo liên kết trong tài liệu của mình. Sau đây là cách bạn có thể thực hiện:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Thêm thuộc tính liên kết đến nội dung.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Đoạn mã này trình bày cách tạo dấu trang trong tài liệu của bạn và thêm thuộc tính tài liệu tùy chỉnh liên kết đến dấu trang đó.

## Chuyển đổi giữa các đơn vị đo lường

Trong Aspose.Words for Java, bạn có thể dễ dàng chuyển đổi đơn vị đo lường. Sau đây là ví dụ về cách thực hiện:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Đặt lề theo inch.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Đoạn mã này thiết lập nhiều lề và khoảng cách khác nhau tính bằng inch bằng cách chuyển đổi chúng thành điểm.

## Sử dụng các ký tự điều khiển

Các ký tự điều khiển có thể hữu ích khi xử lý văn bản. Sau đây là cách thay thế một ký tự điều khiển trong văn bản của bạn:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Thay thế ký tự điều khiển "\r" bằng "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Trong ví dụ này, chúng ta thay thế ký tự trả về (`\r`) với một dấu trả về dòng tiếp theo là một dấu xuống dòng (`\r\n`).

## Phần kết luận

Thuộc tính tài liệu đóng vai trò quan trọng trong việc quản lý và sắp xếp tài liệu của bạn một cách hiệu quả trong Aspose.Words for Java. Cho dù làm việc với các thuộc tính tích hợp, thuộc tính tùy chỉnh hay sử dụng các ký tự điều khiển, bạn đều có nhiều công cụ để nâng cao khả năng quản lý tài liệu của mình.

## Câu hỏi thường gặp

### Làm thế nào để truy cập vào các thuộc tính tích hợp của tài liệu?

Để truy cập các thuộc tính tài liệu tích hợp trong Aspose.Words cho Java, bạn có thể sử dụng `getBuiltInDocumentProperties` phương pháp trên `Document` đối tượng. Phương pháp này trả về một tập hợp các thuộc tính tích hợp mà bạn có thể lặp lại.

### Tôi có thể thêm thuộc tính tùy chỉnh vào tài liệu không?

Có, bạn có thể thêm các thuộc tính tài liệu tùy chỉnh vào tài liệu bằng cách sử dụng `CustomDocumentProperties` bộ sưu tập. Bạn có thể xác định các thuộc tính tùy chỉnh với nhiều kiểu dữ liệu khác nhau, bao gồm chuỗi, giá trị boolean, ngày tháng và giá trị số.

### Làm thế nào để tôi có thể xóa một thuộc tính tùy chỉnh cụ thể của tài liệu?

Để xóa một thuộc tính tài liệu tùy chỉnh cụ thể, bạn có thể sử dụng `remove` phương pháp trên `CustomDocumentProperties` bộ sưu tập, truyền tên thuộc tính bạn muốn xóa dưới dạng tham số.

### Mục đích của việc liên kết đến nội dung trong tài liệu là gì?

Liên kết đến nội dung trong tài liệu cho phép bạn tạo tham chiếu động đến các phần cụ thể của tài liệu. Điều này có thể hữu ích khi tạo tài liệu tương tác hoặc tham chiếu chéo giữa các phần.

### Làm thế nào tôi có thể chuyển đổi giữa các đơn vị đo lường khác nhau trong Aspose.Words cho Java?

Bạn có thể chuyển đổi giữa các đơn vị đo lường khác nhau trong Aspose.Words cho Java bằng cách sử dụng `ConvertUtil` lớp. Nó cung cấp các phương pháp để chuyển đổi các đơn vị như inch sang point, point sang cm, v.v.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}