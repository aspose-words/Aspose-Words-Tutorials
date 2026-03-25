---
date: '2026-03-25'
description: Tìm hiểu cách tạo bookmark và tạo PDF có bookmark bằng Aspose.Words for
  Java. Hướng dẫn chi tiết này bao gồm việc lồng bookmark, cấp độ đề mục và xuất PDF.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Cách tạo dấu trang trong PDF bằng Aspose.Words cho Java
url: /vi/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Các Cấp Độ Đánh Dấu (Bookmark) Trong PDF Sử Dụng Aspose.Words Java

## Giới thiệu
Nếu bạn cần **cách tạo bookmark** giúp PDF của bạn dễ dàng điều hướng, bạn đã đến đúng nơi. Trong hướng dẫn này, chúng ta sẽ đi qua cách cài đặt Aspose.Words cho Java, tạo các bookmark lồng nhau, gán cấp độ outline, và cuối cùng **tạo PDF với bookmark** trông chuyên nghiệp và thân thiện với người dùng. Khi hoàn thành, bạn sẽ có một mẫu có thể tái sử dụng trong bất kỳ dự án Java nào.

**Bạn sẽ học được**
- Cài đặt và cấp phép Aspose.Words cho Java  
- Tạo bookmark lồng nhau trong tài liệu Word  
- Cấu hình cấp độ outline cho bookmark để điều hướng theo cấp bậc  
- Lưu tài liệu dưới dạng PDF với các bookmark được cấu trúc đúng  

### Câu trả lời nhanh
- **Lớp chính để xây dựng tài liệu là gì?** `DocumentBuilder`  
- **Tôi có thể lồng bookmark không?** Có, chỉ cần bắt đầu một bookmark mới trước khi kết thúc bookmark cha.  
- **Làm sao để đặt cấp độ outline?** Sử dụng `PdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels()`.  
- **Có cần giấy phép để xuất PDF không?** Bản dùng thử hoạt động, nhưng giấy phép sẽ loại bỏ các giới hạn đánh giá.  
- **Cụm từ khóa mục tiêu của hướng dẫn này là gì?** *cách tạo bookmark*  

## “cách tạo bookmark” trong Aspose.Words là gì?
Bookmark là các vị trí có tên bên trong tài liệu Word, trở thành các mục có thể nhấp được trong khung outline của PDF. Chúng cho phép người đọc nhảy trực tiếp tới các phần, bảng hoặc hình mà không cần cuộn.

## Tại sao phải tạo PDF với bookmark?
Nhúng bookmark trong quá trình tạo PDF giúp bạn tránh bước xử lý hậu kỳ, cải thiện khả năng truy cập, và mang lại cho các tài liệu pháp lý hoặc kỹ thuật một cấu trúc sạch sẽ, có thể tìm kiếm được.

## Yêu cầu trước
- **Thư viện và phụ thuộc**: Aspose.Words cho Java (phiên bản 25.3 hoặc mới hơn).  
- **Môi trường**: JDK 8 hoặc mới hơn, IntelliJ IDEA/Eclipse, và Maven hoặc Gradle.  
- **Kiến thức**: Java cơ bản, tệp cấu hình Maven/Gradle, và hiểu biết cơ bản về PDF.

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

### Cách nhận giấy phép
Aspose.Words là sản phẩm thương mại, nhưng bạn có thể bắt đầu với bản dùng thử miễn phí để khám phá các tính năng. Thực hiện các bước sau:

1. **Bản dùng thử**: Tải xuống từ [trang phát hành của Aspose](https://releases.aspose.com/words/java/) để kiểm tra đầy đủ khả năng.  
2. **Giấy phép tạm thời**: Đăng ký giấy phép tạm thời tại [trang giấy phép tạm thời của Aspose](https://purchase.aspose.com/temporary-license/) nếu cần.  
3. **Mua giấy phép**: Đối với việc sử dụng lâu dài, mua giấy phép từ [cổng mua hàng của Aspose](https://purchase.aspose.com/buy).

Sau khi có tệp giấy phép, khởi tạo nó trong dự án để mở khóa tất cả tính năng của Aspose.Words.

## Hướng dẫn triển khai
Chúng ta sẽ chia triển khai thành hai phần logic: tạo bookmark lồng nhau và cấu hình cấp độ outline cho chúng.

### Cách tạo bookmark trong tài liệu Word
**Tổng quan** – Phần này trình bày đoạn mã chính xác bạn cần để **cách tạo bookmark** mà sau này có thể xuất ra dạng PDF có cấu trúc cấp bậc.

#### Bước 1: Khởi tạo Document và Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Đối tượng `Document` đại diện cho tệp Word, trong khi `DocumentBuilder` cho phép bạn chèn văn bản, hình ảnh và bookmark.

#### Bước 2: Chèn bookmark lồng nhau
Bắt đầu với một bookmark chính:
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Bây giờ lồng một bookmark khác bên trong bookmark đầu tiên:
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Đóng bookmark ngoài cùng:
```java
builder.endBookmark("Bookmark 1");
```

#### Bước 3: Thêm các bookmark độc lập khác
Bạn có thể tiếp tục thêm bao nhiêu bookmark tùy thích. Ví dụ, một bookmark thứ ba riêng biệt:
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

### Cách tạo PDF với bookmark và cấp độ outline
**Tổng quan** – Sau khi các bookmark đã tồn tại trong tài liệu Word, chúng ta cấu hình cấu trúc cấp bậc trước khi lưu dưới dạng PDF.

#### Bước 1: Thiết lập PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Các tùy chọn này chỉ cho Aspose.Words cách chuyển đổi bookmark Word thành các mục outline trong PDF.

#### Bước 2: Gán cấp độ outline
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```
Số nguyên xác định độ sâu – `1` là cấp độ cao nhất, `2` là cấp con, và tiếp tục như vậy.

#### Bước 3: Lưu tài liệu dưới dạng PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
PDF kết quả sẽ hiển thị một khung bookmark gọn gàng phản ánh cấu trúc bạn đã định nghĩa.

### Mẹo khắc phục sự cố
- **Bookmark bị thiếu** – Kiểm tra lại rằng mỗi `startBookmark` đều có `endBookmark` tương ứng.  
- **Cấp độ không đúng** – Đảm bảo các số cấp độ tương ứng với quan hệ cha‑con mong muốn.  
- **Vấn đề giấy phép** – Nếu thấy dấu watermark đánh giá, chắc chắn tệp giấy phép đã được tải đúng trước bất kỳ thao tác nào trên tài liệu.

## Ứng dụng thực tế
Dưới đây là các kịch bản thường gặp mà **cách tạo bookmark** và **tạo PDF với bookmark** đặc biệt hữu ích:

1. **Hợp đồng pháp lý** – Nhảy nhanh tới các điều khoản, định nghĩa hoặc phụ lục.  
2. **Báo cáo tài chính** – Điều hướng giữa các phần, bảng và biểu đồ mà không cần cuộn.  
3. **Tài liệu e‑Learning** – Cung cấp mục lục có thể nhấp cho các chương và tiểu chương.  

## Các lưu ý về hiệu năng
- **Kích thước tài liệu** – Loại bỏ các kiểu hoặc hình ảnh không dùng trước khi lưu để giữ PDF nhẹ.  
- **Quản lý bộ nhớ** – Đối với tệp rất lớn, cân nhắc gọi `doc.updatePageLayout()` sau các chỉnh sửa lớn để giải phóng tài nguyên.

## Kết luận
Bạn đã có một phương pháp hoàn chỉnh, sẵn sàng sản xuất để **cách tạo bookmark**, gán cấp độ outline, và **tạo PDF với bookmark** bằng Aspose.Words cho Java. Áp dụng mẫu này vào quy trình tài liệu của bạn để cung cấp các PDF được định dạng đẹp, dễ dàng điều hướng mỗi lần.

**Bước tiếp theo**: Thử thêm biểu tượng tùy chỉnh cho bookmark, hoặc kết hợp cách này với Aspose.PDF để thực hiện các tác vụ hậu xử lý như thêm chữ ký số.

## Phần Câu hỏi Thường gặp
1. **Làm sao cài đặt Aspose.Words cho Java?**  
   - Thêm nó như một phụ thuộc qua Maven hoặc Gradle, sau đó thiết lập tệp giấy phép.  
2. **Có thể sử dụng bookmark mà không có cấp độ outline không?**  
   - Có, nhưng việc sử dụng cấp độ outline sẽ cải thiện khả năng điều hướng trong PDF.  
3. **Giới hạn về độ sâu lồng bookmark là bao nhiêu?**  
   - Không có giới hạn nghiêm ngặt, nhưng hãy giữ cấu trúc hợp lý cho người dùng cuối.  
4. **Aspose xử lý tài liệu lớn như thế nào?**  
   - Nó quản lý tài nguyên hiệu quả, mặc dù vẫn nên tối ưu cho các tệp rất lớn.  
5. **Có thể chỉnh sửa bookmark sau khi lưu PDF không?**  
   - Có, bạn có thể dùng Aspose.PDF cho Java để chỉnh sửa bookmark sau khi chuyển đổi.

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

**Cập nhật lần cuối:** 2026-03-25  
**Được kiểm tra với:** Aspose.Words 25.3 cho Java  
**Tác giả:** Aspose