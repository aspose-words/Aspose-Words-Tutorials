---
date: '2026-03-15'
description: Tìm hiểu cách thêm dấu trang PDF và thiết lập mức độ đề mục bằng Aspose.Words
  cho Java, nâng cao khả năng điều hướng và độ dễ đọc của PDF.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Thêm dấu trang PDF và cấp độ đề mục với Aspose.Words Java
url: /vi/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Thêm dấu trang PDF và mức độ đề mục với Aspose.Words Java

## Giới thiệu
Trong tutorial này bạn sẽ học **cách thêm dấu trang PDF** và cấu hình mức độ đề mục của chúng bằng **Aspose.Words for Java**. Các dấu trang được tổ chức hợp lý giúp việc duyệt các tệp PDF lớn trở nên dễ dàng, dù bạn đang làm việc với hợp đồng pháp lý, báo cáo chi tiết, hay tài liệu e‑learning.

**Bạn sẽ học được**
- Cài đặt và sử dụng **Aspose.Words for Java**
- **Tạo dấu trang lồng nhau** trong tài liệu Word
- **Cách đặt mức độ đề mục** cho dấu trang để có cấu trúc cây sạch sẽ
- **Lưu tài liệu dưới dạng PDF** với cây dấu trang có cấu trúc

Hãy chắc chắn rằng bạn đã chuẩn bị đầy đủ trước khi bắt đầu.

### Yêu cầu trước
Trước khi bắt đầu, hãy xác nhận bạn đã có:
- **Thư viện và phụ thuộc**: Aspose.Words for Java (phiên bản 25.3 trở lên).  
- **Cài đặt môi trường**: JDK đã được cài đặt và một IDE như IntelliJ IDEA hoặc Eclipse.  
- **Kiến thức nền**: Kỹ năng lập trình Java cơ bản và quen thuộc với Maven hoặc Gradle.

## Câu trả lời nhanh
- **Mục tiêu chính là gì?** Thêm dấu trang PDF và định nghĩa mức độ đề mục.  
- **Thư viện nào được yêu cầu?** Aspose.Words for Java (v25.3+).  
- **Có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; giấy phép thương mại cần cho môi trường sản xuất.  
- **Có thể tạo PDF với dấu trang trong một bước không?** Có — cấu hình `PdfSaveOptions` và gọi `doc.save`.  
- **Có hỗ trợ tạo dấu trang lồng nhau không?** Hoàn toàn có, bạn có thể tạo bao nhiêu mức độ lồng nhau tùy ý.

## Cài đặt Aspose.Words
Để bắt đầu, thêm các phụ thuộc cần thiết vào dự án của bạn. Dưới đây là cách thực hiện với Maven và Gradle:

**Maven:**
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Nhận giấy phép
Aspose.Words là sản phẩm thương mại, nhưng bạn có thể bắt đầu với bản dùng thử miễn phí để khám phá các tính năng.

1. **Bản dùng thử**: Tải xuống từ [trang phát hành của Aspose](https://releases.aspose.com/words/java/) để thử toàn bộ khả năng.  
2. **Giấy phép tạm thời**: Đăng ký giấy phép tạm thời tại [trang giấy phép tạm thời của Aspose](https://purchase.aspose.com/temporary-license/) nếu bạn cần thời gian đánh giá kéo dài hơn.  
3. **Mua bản quyền**: Đối với việc sử dụng lâu dài, mua giấy phép tại [cổng mua hàng của Aspose](https://purchase.aspose.com/buy).

Sau khi có file giấy phép, khởi tạo nó trong dự án để mở khóa tất cả các tính năng.

## Hướng dẫn triển khai
Chúng tôi sẽ hướng dẫn từng bước, chia nhỏ mỗi phần để dễ hiểu.

### Tạo dấu trang lồng nhau
**Tổng quan**: Học cách **tạo dấu trang lồng nhau** trong tài liệu Word bằng Aspose.Words for Java.

#### Bước 1: Khởi tạo Document và Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Đoạn mã này tạo một tài liệu Word mới và một đối tượng builder cho phép bạn chèn nội dung và dấu trang.

#### Bước 2: Chèn dấu trang lồng nhau
Bắt đầu bằng việc tạo một dấu trang chính:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Bây giờ, chèn một dấu trang khác bên trong nó:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Hoàn thiện dấu trang bên ngoài:
```java
builder.endBookmark("Bookmark 1");
```

#### Bước 3: Thêm dấu trang bổ sung
Bạn có thể tiếp tục thêm dấu trang tùy ý. Ví dụ, một dấu trang thứ ba riêng biệt:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Cấu hình mức độ đề mục cho dấu trang
**Tổng quan**: Sắp xếp các dấu trang bằng cách đặt mức độ đề mục, quyết định thứ tự hiển thị trong các trình xem PDF.

#### Bước 1: Thiết lập PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Các tùy chọn này sẽ được áp dụng khi bạn **lưu tài liệu dưới dạng PDF**.

#### Bước 2: Thêm mức độ đề mục
Gán mức độ cho mỗi dấu trang; số thấp hơn sẽ xuất hiện cao hơn trong cây đề mục:
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

#### Bước 3: Lưu tài liệu
Cuối cùng, tạo PDF với cấu trúc dấu trang đã được cấu hình:
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

### Mẹo khắc phục sự cố
- **Dấu trang bị thiếu**: Kiểm tra mỗi `startBookmark` có một `endBookmark` tương ứng.  
- **Mức độ không đúng**: Kiểm tra lại thứ tự bạn thêm mức độ đề mục; cấu trúc cây dựa trên số mức độ bạn gán.  
- **Tài liệu lớn**: Gọi `doc.removeUnusedResources()` trước khi lưu để giảm kích thước PDF.

## Ứng dụng thực tiễn
Dưới đây là một số tình huống thực tế mà **thêm dấu trang PDF** tỏa sáng:

1. **Tài liệu pháp lý** – Nhảy nhanh tới các điều khoản, phụ lục, hoặc annex.  
2. **Báo cáo tài chính** – Duyệt qua các phần, bảng và biểu đồ.  
3. **Tài liệu e‑Learning** – Cung cấp cho người đọc một mục lục có thể nhấp được.  

## Các cân nhắc về hiệu suất
- **Quản lý bộ nhớ**: Khi xử lý các tệp Word rất lớn, gọi `System.gc()` sau khi lưu để giải phóng bộ nhớ.  
- **Kích thước tài liệu**: Loại bỏ các hình ảnh không cần thiết hoặc văn bản ẩn trước khi tạo dấu trang để giữ PDF cuối cùng nhẹ nhàng.

## Kết luận
Bạn đã có một phương pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **thêm dấu trang PDF**, cấu hình mức độ đề mục, và **tạo PDF với dấu trang** bằng Aspose.Words for Java. Cách tiếp cận này cải thiện đáng kể tính khả dụng của PDF và mang lại trải nghiệm điều hướng chuyên nghiệp cho người dùng cuối.

**Bước tiếp theo**: Hãy thử kết hợp kỹ thuật này với Aspose.PDF cho Java để chỉnh sửa dấu trang sau khi PDF đã được tạo, hoặc tích hợp vào dịch vụ xử lý hàng loạt tự động thêm mục lục cho mọi báo cáo bạn tạo.

## Câu hỏi thường gặp

**Q: Làm thế nào để cài đặt Aspose.Words cho Java?**  
A: Thêm phụ thuộc Maven hoặc Gradle như đã trình bày ở trên, sau đó đặt file giấy phép vào thư mục resources của dự án và khởi tạo nó khi khởi động.

**Q: Tôi có thể sử dụng dấu trang mà không có mức độ đề mục không?**  
A: Có, nhưng nếu không có mức độ đề mục, trình xem PDF sẽ liệt kê tất cả dấu trang ở cùng một cấp độ, khiến việc điều hướng trở nên khó khăn hơn.

**Q: Giới hạn về mức độ lồng nhau của dấu trang là bao nhiêu?**  
A: Kỹ thuật không có giới hạn cứng, nhưng nên giữ cấu trúc hợp lý (3‑5 cấp) để đảm bảo độ đọc dễ dàng.

**Q: Aspose xử lý tài liệu lớn như thế nào?**  
A: Nó truyền dữ liệu theo luồng và cung cấp các phương thức như `Document.optimizeResources()` để giảm mức tiêu thụ bộ nhớ.

**Q: Tôi có thể chỉnh sửa dấu trang sau khi đã lưu PDF không?**  
A: Chắc chắn — sử dụng Aspose.PDF cho Java để chỉnh sửa, sắp xếp lại hoặc xóa dấu trang sau khi tạo.

## Tài nguyên
- [Tài liệu Aspose.Words](https://reference.aspose.com/words/java/)
- [Tải bản phát hành mới nhất](https://releases.aspose.com/words/java/)
- [Mua giấy phép](https://purchase.aspose.com/buy)
- [Bản dùng thử](https://releases.aspose.com/words/java/)
- [Đăng ký giấy phép tạm thời](https://purchase.aspose.com/temporary-license/)
- [Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Cập nhật lần cuối:** 2026-03-15  
**Đã kiểm tra với:** Aspose.Words for Java 25.3  
**Tác giả:** Aspose