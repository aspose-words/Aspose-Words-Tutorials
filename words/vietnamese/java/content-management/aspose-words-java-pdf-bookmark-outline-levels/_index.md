---
date: '2026-03-20'
description: Tìm hiểu cách tạo dấu trang lồng nhau và tạo PDF có dấu trang bằng Aspose.Words
  cho Java, cải thiện khả năng đọc và điều hướng.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
title: Tạo các dấu trang lồng nhau trong PDF bằng Aspose.Words Java
url: /vi/java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Bookmark Lồng Nhau trong PDF với Aspose.Words Java

## Giới thiệu
Nếu bạn từng gặp khó khăn trong việc giữ cho các bookmark PDF được sắp xếp sau khi chuyển đổi tài liệu Word, bạn không phải là người duy nhất. Trong hướng dẫn này, bạn sẽ **tạo bookmark lồng nhau** và học cách **tạo PDF với bookmark** dễ dàng điều hướng. Chúng tôi sẽ hướng dẫn cách thiết lập Aspose.Words, xây dựng cấu trúc bookmark, gán mức outline, và cuối cùng xuất ra một PDF sạch sẽ.

**Bạn sẽ học được**
- Cách thiết lập Aspose.Words cho Java
- Cách **tạo bookmark lồng nhau** trong tài liệu Word
- Cách cấu hình mức outline cho bookmark để điều hướng PDF rõ ràng
- Cách **tạo PDF với bookmark** phản ánh cấu trúc bạn đã định nghĩa

### Câu trả lời nhanh
- **Lớp chính để xây dựng tài liệu là gì?** `DocumentBuilder`
- **Phương thức nào thêm một bookmark?** `startBookmark(String name)`
- **Làm thế nào để đặt mức outline cho một bookmark?** `outlineLevels.add(name, level)`
- **Tôi có cần giấy phép cho môi trường production không?** Có, giấy phép mua sẽ mở khóa đầy đủ tính năng.
- **Tôi có thể sử dụng với Maven hoặc Gradle không?** Chắc chắn – cả hai đều được hỗ trợ.

### Yêu cầu trước
Trước khi bắt đầu, hãy chắc chắn rằng bạn có:
- **Aspose.Words cho Java** (phiên bản 25.3 trở lên).
- Một JDK đã cài đặt và một IDE như IntelliJ IDEA hoặc Eclipse.
- Kiến thức cơ bản về Java và quen thuộc với Maven hoặc Gradle.

## “Tạo bookmark lồng nhau” là gì?
Tạo bookmark lồng nhau có nghĩa là đặt một bookmark bên trong một bookmark khác, tạo thành cấu trúc cha‑con. Khi tài liệu được lưu dưới dạng PDF, các mối quan hệ này xuất hiện dưới dạng các mục có thể thu gọn trong bảng bookmark của PDF, giúp việc khám phá tài liệu lớn trở nên dễ dàng hơn.

## Tại sao nên sử dụng mức outline khi tạo PDF với bookmark?
Mức outline xác định cấu trúc hiển thị của các bookmark trong trình xem PDF. Một bookmark mức‑1 xuất hiện như mục cấp cao nhất, mức‑2 như mục con, và cứ tiếp tục như vậy. Các mức outline đúng cách biến danh sách bookmark phẳng thành một mục lục có cấu trúc, đặc biệt hữu ích cho hợp đồng pháp lý, báo cáo kỹ thuật và sách điện tử.

## Cài đặt Aspose.Words
Thêm thư viện vào dự án của bạn bằng Maven hoặc Gradle.

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
Aspose.Words là sản phẩm thương mại, nhưng bạn có thể bắt đầu với bản dùng thử miễn phí.

1. **Dùng thử miễn phí** – Tải xuống từ [trang phát hành của Aspose](https://releases.aspose.com/words/java/) để kiểm tra đầy đủ tính năng.  
2. **Giấy phép tạm thời** – Đăng ký tại [trang giấy phép tạm thời của Aspose](https://purchase.aspose.com/temporary-license/) để đánh giá ngắn hạn.  
3. **Mua** – Nhận giấy phép vĩnh viễn từ [cổng mua hàng của Aspose](https://purchase.aspose.com/buy).

Sau khi bạn có file `.lic`, tải nó trong mã của bạn để mở khóa tất cả tính năng.

## Hướng dẫn thực hiện
Dưới đây là hướng dẫn từng bước tạo tài liệu, thêm bookmark lồng nhau, gán mức outline, và lưu kết quả dưới dạng PDF.

### Bước 1: Khởi tạo Document và Builder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```
Điều này tạo một tài liệu Word trống và một đối tượng builder mà bạn sẽ dùng để chèn văn bản và bookmark.

### Bước 2: Tạo Bookmark Đầu tiên (Parent)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```
Lệnh `startBookmark` mở một bookmark mới có tên **Bookmark 1**. Mọi nội dung bạn viết sau lệnh này sẽ thuộc về bookmark đó cho đến khi bạn đóng nó.

### Bước 3: Lồng Bookmark Thứ Hai vào Bookmark Đầu tiên
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```
Vì bookmark này được bắt đầu **sau** bookmark đầu tiên và được đóng **trước** bookmark đầu tiên, nó trở thành con của **Bookmark 1**.

### Bước 4: Đóng Bookmark Parent
```java
builder.endBookmark("Bookmark 1");
```
Bây giờ cấu trúc trông như sau:

- Bookmark 1 (level 1)  
  - Bookmark 2 (level 2)

### Bước 5: Thêm Bookmark Thứ Ba Độc Lập
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```
Bookmark này nằm ở cấp cao nhất, tách biệt khỏi hai bookmark đầu tiên.

### Bước 6: Cấu hình mức Outline cho việc xuất PDF
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```
Đối tượng `PdfSaveOptions` cho phép bạn kiểm soát cách bookmark hiển thị trong PDF cuối cùng.

```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 1);
```
Ở đây chúng tôi gán mức 1 cho các bookmark cấp cao nhất và mức 2 cho bookmark lồng nhau.

### Bước 7: Lưu tài liệu dưới dạng PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```
PDF kết quả sẽ hiển thị một bảng bookmark gọn gàng, có thể thu gọn, phản ánh đúng cấu trúc bạn đã định nghĩa.

## Các vấn đề thường gặp và giải pháp
- **Bookmark bị thiếu** – Mỗi `startBookmark` phải có một `endBookmark` tương ứng. Quên một trong số chúng sẽ khiến bookmark bị bỏ qua trong PDF.  
- **Mức Outline không đúng** – Kiểm tra lại các tên bạn truyền vào `outlineLevels.add`. Lỗi chính tả sẽ khiến mức không được áp dụng.  
- **Tài liệu lớn** – Đối với các tệp rất lớn, gọi `doc.removeMacros()` hoặc xóa các style không dùng trước khi lưu để giữ kích thước PDF hợp lý.

## Ứng dụng thực tiễn
1. **Hợp đồng pháp lý** – Nhảy nhanh giữa các điều khoản và tiểu mục.  
2. **Báo cáo kỹ thuật** – Duyệt qua các phần, bảng và hình ảnh mà không cần cuộn.  
3. **Tài liệu e‑learning** – Cung cấp mục lục có thể nhấp cho sinh viên.

## Mẹo hiệu suất
- Xóa các tài nguyên không dùng (hình ảnh, style) trước khi lưu.  
- Sử dụng API streaming nếu bạn xử lý các PDF lớn hơn 100 MB để giảm mức sử dụng bộ nhớ.

## Kết luận
Bây giờ bạn đã biết cách **tạo bookmark lồng nhau**, gán mức outline, và **tạo PDF với bookmark** vừa chức năng vừa thân thiện với người dùng. Hãy thử nghiệm với các cấu trúc sâu hơn hoặc tích hợp logic này vào quy trình tạo tài liệu của bạn để tự động hoá hơn nữa.

## Câu hỏi thường gặp

**H: Làm thế nào để cài đặt Aspose.Words cho Java?**  
Đ: Thêm phụ thuộc Maven hoặc Gradle như trên, sau đó tải file giấy phép của bạn tại thời gian chạy.

**H: Tôi có thể sử dụng bookmark mà không đặt mức outline không?**  
Đ: Có, nhưng PDF sẽ hiển thị danh sách phẳng, gây khó khăn trong việc điều hướng tài liệu phức tạp.

**H: Có giới hạn độ sâu của việc lồng bookmark không?**  
Đ: Về mặt kỹ thuật không, nhưng nên giữ cấu trúc hợp lý (3‑4 mức) để duy trì khả năng đọc.

**H: Aspose xử lý tài liệu rất lớn như thế nào?**  
Đ: Nó stream nội dung và cung cấp các tiện ích quản lý bộ nhớ; tuy nhiên, bạn vẫn nên loại bỏ các yếu tố không dùng.

**H: Tôi có thể chỉnh sửa bookmark sau khi PDF đã được tạo không?**  
Đ: Chắc chắn – sử dụng Aspose.PDF cho Java để sửa tiêu đề bookmark, đích đến hoặc mức outline sau khi tạo.

## Tài nguyên
- [Aspose.Words Documentation](https://reference.aspose.com/words/java/)
- [Download Latest Releases](https://releases.aspose.com/words/java/)
- [Purchase a License](https://purchase.aspose.com/buy)
- [Free Trial](https://releases.aspose.com/words/java/)
- [Temporary License Application](https://purchase.aspose.com/temporary-license/)
- [Aspose Support Forum](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-03-20  
**Tested With:** Aspose.Words for Java 25.3  
**Author:** Aspose