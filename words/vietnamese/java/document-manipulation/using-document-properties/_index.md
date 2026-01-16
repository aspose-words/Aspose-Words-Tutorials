---
date: 2026-01-16
description: Tìm hiểu cách chuyển đổi inch sang điểm, đọc siêu dữ liệu tài liệu bằng
  Java, thêm thuộc tính tùy chỉnh bằng Java và đặt lề trang bằng Java với Aspose.Words
  cho Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Chuyển đổi inch sang điểm – Sử dụng thuộc tính tài liệu trong Aspose.Words
  cho Java
url: /vi/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chuyển Đổi Inch Sang Điểm – Sử Dụng Thuộc Tính Tài Liệu trong Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ khám phá cách **chuyển đổi inch sang điểm** khi thiết lập lề trang, đọc siêu dữ liệu tài liệu bằng Java, thêm thuộc tính tùy chỉnh bằng Java, và làm việc với các thuộc tính tài liệu tích hợp sẵn bằng Aspose.Words cho Java. Dù bạn đang tạo báo cáo, hoá đơn hay tài liệu pháp lý, việc thành thạo các kỹ thuật này sẽ cho phép bạn kiểm soát chi tiết cả về giao diện và siêu dữ liệu của các tệp Word.

## Trả Lời Nhanh
- **Làm sao để chuyển đổi inch sang điểm?** Sử dụng `ConvertUtil.inchToPoint(value)` từ Aspose.Words.  
- **Có thể đọc siêu dữ liệu tài liệu bằng Java không?** Có – gọi `doc.getBuiltInDocumentProperties()` hoặc `doc.getCustomDocumentProperties()`.  
- **Làm sao để thêm thuộc tính tùy chỉnh trong Java?** Dùng `doc.getCustomDocumentProperties().add(name, value)`.  
- **Phương thức nào thiết lập lề trang bằng điểm?** `PageSetup.setTopMargin`, `setBottomMargin`, v.v., chấp nhận giá trị tính bằng điểm.  
- **Liên kết tới một bookmark có được hỗ trợ không?** Có – dùng `addLinkToContent` trên bộ sưu tập thuộc tính tùy chỉnh.

## Giới Thiệu về Thuộc Tính Tài Liệu

Thuộc tính tài liệu là một phần quan trọng của bất kỳ tệp Word nào. Chúng lưu trữ thông tin như tiêu đề, tác giả, chủ đề, từ khóa và bất kỳ siêu dữ liệu tùy chỉnh nào bạn cần cho quá trình xử lý tiếp theo. Trong Aspose.Words cho Java, bạn có thể thao tác cả thuộc tính tích hợp sẵn và thuộc tính tùy chỉnh, đồng thời kiểm soát các chi tiết bố cục như lề bằng cách chuyển đổi đơn vị đo (ví dụ, **chuyển đổi inch sang điểm**).

## “Chuyển Đổi Inch Sang Điểm” là gì?

Trong Word, các đo lường bố cục được biểu thị bằng điểm (1 điểm = 1/72 inch). Chuyển đổi inch sang điểm cho phép bạn định nghĩa lề, thụt lề và khoảng cách bằng các đơn vị imperial quen thuộc, trong khi API làm việc nội bộ bằng điểm.

## Tại sao quản lý siêu dữ liệu tài liệu bằng Java?

Nhúng siêu dữ liệu giúp việc tìm kiếm, phân loại và tự động hoá quy trình trở nên dễ dàng hơn. Ví dụ, bạn có thể gắn thẻ một hợp đồng bằng cờ “Authorized” hoặc lưu trữ số phiên bản để theo dõi kiểm toán. Đọc và ghi thông tin này một cách lập trình đảm bảo tính nhất quán trong các lô tài liệu lớn.

## Yêu Cầu Trước
- Java 17+ (hoặc JDK tương thích)  
- Thư viện Aspose.Words cho Java đã được thêm vào dự án (Maven/Gradle)  
- Một tệp mẫu `.docx` (ví dụ, `Properties.docx`) đặt trong thư mục có thể truy cập

## Hướng Dẫn Từng Bước

### Đánh Giá Các Thuộc Tính Tài Liệu Tích Hợp Sẵn
Dưới đây là một đoạn kiểm tra đơn giản mở tài liệu và in ra tất cả các thuộc tính tích hợp sẵn như Title, Author và Keywords.

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

> **Mẹo chuyên nghiệp:** Sử dụng đoạn mã này để xác nhận rằng siêu dữ liệu của bạn đã được ghi đúng trong các bước trước.

### Thêm Thuộc Tính Tài Liệu Tùy Chỉnh (add custom properties java)
Thuộc tính tùy chỉnh cho phép bạn lưu trữ bất kỳ kiểu dữ liệu nào bạn cần—boolean, string, date, number, v.v.

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

> **Tại sao điều này quan trọng:** Thêm một cờ như **Authorized** có thể kích hoạt các quy trình phê duyệt downstream mà không cần thay đổi nội dung tài liệu.

### Xóa Một Thuộc Tính Tùy Chỉnh
Nếu một thuộc tính không còn cần thiết, bạn có thể xóa nó một cách sạch sẽ.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Cấu Hình Liên Kết tới Nội Dung (bookmark linking)
Bạn có thể tạo một bookmark và sau đó thêm một thuộc tính tùy chỉnh trỏ tới bookmark đó, cho phép tham chiếu chéo động.

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

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Chuyển Đổi Giữa Các Đơn Vị Đo Lường (set page margins java)
Đây là nơi từ khóa chính tỏa sáng. Chúng ta đặt lề bằng inch, sau đó **chuyển đổi inch sang điểm** bằng `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Lưu ý:** `ConvertUtil` còn cung cấp `pointToInch`, `mmToPoint`, v.v., để xử lý bố cục linh hoạt.

### Sử Dụng Ký Tự Điều Khiển (read document metadata java)
Ký tự điều khiển giúp bạn làm sạch luồng văn bản. Ví dụ này thay thế ký tự carriage‑return (`\r`) bằng chuỗi ngắt dòng Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Các Vấn Đề Thường Gặp & Giải Pháp
| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|------------|----------------|
| Lề hiển thị sai sau khi chuyển đổi | Sử dụng sai đơn vị (ví dụ, cm thay vì inch) | Kiểm tra lại việc gọi `ConvertUtil.inchToPoint` cho giá trị inch |
| Thuộc tính tùy chỉnh không xuất hiện | Thuộc tính được thêm sau khi lưu tài liệu | Gọi `doc.save(...)` sau khi thêm thuộc tính |
| Liên kết bookmark bị hỏng | Tên bookmark bị viết sai | Đảm bảo tên bookmark khớp chính xác trong `addLinkToContent` |

## Câu Hỏi Thường Gặp

### Làm sao để truy cập các thuộc tính tài liệu tích hợp sẵn?

Để truy cập các thuộc tính tài liệu tích hợp sẵn trong Aspose.Words cho Java, bạn có thể dùng phương thức `getBuiltInDocumentProperties` trên đối tượng `Document`. Phương thức này trả về một bộ sưu tập các thuộc tính tích hợp sẵn mà bạn có thể duyệt qua.

### Tôi có thể thêm thuộc tính tài liệu tùy chỉnh vào một tài liệu không?

Có, bạn có thể thêm thuộc tính tài liệu tùy chỉnh vào tài liệu bằng cách sử dụng bộ sưu tập `CustomDocumentProperties`. Bạn có thể định nghĩa các thuộc tính tùy chỉnh với nhiều kiểu dữ liệu, bao gồm string, boolean, date và numeric.

### Làm sao để xóa một thuộc tính tài liệu tùy chỉnh cụ thể?

Để xóa một thuộc tính tài liệu tùy chỉnh cụ thể, bạn có thể dùng phương thức `remove` trên bộ sưu tập `CustomDocumentProperties`, truyền vào tên của thuộc tính cần xóa.

### Mục đích của việc liên kết tới nội dung trong tài liệu là gì?

Liên kết tới nội dung trong tài liệu cho phép bạn tạo các tham chiếu động đến các phần cụ thể của tài liệu. Điều này hữu ích cho việc tạo tài liệu tương tác hoặc tham chiếu chéo giữa các mục.

### Làm sao để chuyển đổi giữa các đơn vị đo lường khác nhau trong Aspose.Words cho Java?

Bạn có thể chuyển đổi giữa các đơn vị đo lường trong Aspose.Words cho Java bằng cách sử dụng lớp `ConvertUtil`. Lớp này cung cấp các phương thức để chuyển đổi như inch sang điểm, điểm sang centimet, và nhiều hơn nữa.

## Các Câu Hỏi Thường Đặt

**Q: Làm sao để đọc siêu dữ liệu tài liệu Java mà không tải toàn bộ tệp?**  
A: Sử dụng `DocumentInfo` để lấy các thuộc tính cốt lõi mà không cần tải toàn bộ nội dung tài liệu.

**Q: Tôi có thể thiết lập lề trang Java một cách lập trình cho các tài liệu hiện có không?**  
A: Có—mở tài liệu, sửa đổi lề `PageSetup` (chuyển đổi inch sang điểm nếu cần), và lưu lại.

**Q: Có thể xuất thuộc tính tùy chỉnh sang siêu dữ liệu PDF không?**  
A: Khi lưu dưới dạng PDF, Aspose.Words tự động ánh xạ các thuộc tính tài liệu tùy chỉnh sang siêu dữ liệu tùy chỉnh của PDF.

**Q: Các ký tự điều khiển có ảnh hưởng tới việc chuyển đổi PDF không?**  
A: Chúng được giữ nguyên trong quá trình chuyển đổi; tuy nhiên, bạn có thể muốn chuẩn hoá ký tự ngắt dòng để đồng nhất.

**Q: Phiên bản Aspose.Words nào cần thiết cho `ConvertUtil`?**  
A: `ConvertUtil` đã có từ Aspose.Words 16.5; bất kỳ phiên bản gần đây nào cũng hỗ trợ.

## Kết Luận

Bằng cách thành thạo **chuyển đổi inch sang điểm**, đọc siêu dữ liệu tài liệu Java và thêm thuộc tính tùy chỉnh Java, bạn sẽ có toàn quyền kiểm soát cả bố cục trực quan và dữ liệu ẩn của các tệp Word. Những khả năng này cho phép bạn xây dựng các quy trình tự động hoá tài liệu, thực thi tuân thủ và tạo các báo cáo được định dạng phong phú—tất cả đều nhờ Aspose.Words cho Java.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}