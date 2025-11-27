---
date: '2025-11-27'
description: Tìm hiểu cách tạo dấu trang, tạo PDF có dấu trang và chuyển đổi Word
  sang PDF trong Java bằng Aspose.Words. Hướng dẫn này bao gồm dấu trang lồng nhau
  và mức độ đề mục.
keywords:
- Aspose.Words Java PDF bookmarks
- nested bookmarks in PDFs
- bookmark outline levels
language: vi
title: Cách tạo dấu trang và thiết lập cấp độ đề mục trong PDF bằng Aspose.Words Java
url: /java/content-management/aspose-words-java-pdf-bookmark-outline-levels/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cách Tạo Bookmark và Đặt Cấp Độ Đề Cương trong PDF Sử Dụng Aspose.Words Java

## Giới thiệu
Nếu bạn từng gặp khó khăn khi **cách tạo bookmark** sao cho được tổ chức khi chuyển đổi tài liệu Word sang PDF, bạn đang ở đúng nơi. Trong hướng dẫn này, chúng tôi sẽ trình bày quy trình đầy đủ để tạo PDF có bookmark, lồng chúng và gán cấp độ đề cương để PDF cuối cùng dễ dàng điều hướng. Khi hoàn thành, bạn sẽ có thể **chuyển đổi Word PDF Java**‑style với một cấu trúc bookmark sạch sẽ hoạt động trên mọi trình xem PDF.

### Bạn sẽ học được
- Cài đặt Aspose.Words cho Java trong môi trường phát triển của bạn.  
- **Cách tạo bookmark** bằng chương trình và lồng chúng.  
- Cấu hình cấp độ đề cương của bookmark để tạo PDF với bookmark phản ánh cấu trúc tài liệu.  
- Lưu tệp Word dưới dạng PDF trong khi giữ nguyên cấu trúc bookmark.

## Câu trả lời nhanh
- **Lớp chính để xây dựng tài liệu là gì?** `DocumentBuilder`.  
- **Tùy chọn nào kiểm soát cấu trúc bookmark?** `BookmarksOutlineLevelCollection` trong `PdfSaveOptions`.  
- **Tôi có thể sử dụng Maven hoặc Gradle không?** Có – cả hai đều được hiển thị bên dưới.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; giấy phép vĩnh viễn cần cho môi trường sản xuất.  
- **Cách tiếp cận này có phù hợp với tài liệu lớn không?** Có, nhưng nên cân nhắc các kỹ thuật tối ưu bộ nhớ (ví dụ: loại bỏ tài nguyên không dùng).

### Yêu cầu trước
- **Thư viện và phụ thuộc** – Aspose.Words cho Java (phiên bản 25.3 trở lên).  
- **Môi trường** – JDK 8 trở lên, và một IDE như IntelliJ IDEA hoặc Eclipse.  
- **Kiến thức cơ bản** – Những nền tảng lập trình Java và quen thuộc với Maven hoặc Gradle.

## Cài đặt Aspose.Words
Để bắt đầu, bao gồm các phụ thuộc cần thiết trong dự án của bạn. Dưới đây là cách bạn có thể thêm Aspose.Words bằng Maven hoặc Gradle:

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
Aspose.Words là một thư viện thương mại, nhưng bạn có thể bắt đầu với bản dùng thử miễn phí:

1. **Bản dùng thử** – Tải xuống từ [trang phát hành Aspose](https://releases.aspose.com/words/java/).  
2. **Giấy phép tạm thời** – Đăng ký tại [trang giấy phép tạm thời](https://purchase.aspose.com/temporary-license/) nếu bạn cần khóa ngắn hạn.  
3. **Giấy phép đầy đủ** – Mua qua [cổng mua hàng Aspose](https://purchase.aspose.com/buy) cho mục đích sản xuất.

Sau khi có tệp giấy phép, tải nó khi khởi động ứng dụng để mở khóa tất cả các tính năng.

## Cách tạo bookmark trong PDF với Aspose.Words Java
Dưới đây chúng tôi chia triển khai thành các bước rõ ràng, có số thứ tự. Mỗi bước bao gồm một giải thích ngắn gọn và sau đó là khối mã gốc (không thay đổi).

### Bước 1: Khởi tạo Document và DocumentBuilder
Chúng tôi bắt đầu với một thể hiện `Document` mới và một `DocumentBuilder` cho phép chèn nội dung và bookmark.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Bước 2: Chèn bookmark đầu tiên (Parent)
```java
builder.startBookmark("Bookmark 1");
builder.writeln("Text inside Bookmark 1.");
```

### Bước 3: Lồng một bookmark con bên trong bookmark cha
```java
builder.startBookmark("Bookmark 2");
builder.writeln("Text inside Bookmark 1 and 2.");
builder.endBookmark("Bookmark 2"); // End the nested bookmark
```

### Bước 4: Đóng bookmark cha
```java
builder.endBookmark("Bookmark 1");
```

### Bước 5: Thêm bookmark thứ ba độc lập
```java
builder.startBookmark("Bookmark 3");
builder.writeln("Text inside Bookmark 3.");
builder.endBookmark("Bookmark 3");
```

## Cấu hình cấp độ đề cương cho bookmark
Sau khi các bookmark đã được tạo, chúng tôi chỉ định cho Aspose.Words cách các bookmark này sẽ hiển thị trong đề cương của PDF (bảng điều hướng bên trái).

### Bước 6: Chuẩn bị PdfSaveOptions
```java
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
BookmarksOutlineLevelCollection outlineLevels = pdfSaveOptions.getOutlineOptions().getBookmarksOutlineLevels();
```

### Bước 7: Gán mức độ phân cấp
```java
outlineLevels.add("Bookmark 1", 1);
outlineLevels.add("Bookmark 2", 2); // Nested under Bookmark 1
outlineLevels.add("Bookmark 3", 3);
```

### Bước 8: Lưu tài liệu dưới dạng PDF
```java
doc.save(getArtifactsDir() + "BookmarksOutlineLevelCollection.BookmarkLevels.pdf", pdfSaveOptions);
```

## Tại sao nên dùng cách này để tạo PDF có bookmark?
- **Điều hướng chuyên nghiệp** – Độc giả có thể nhảy trực tiếp tới các phần, cải thiện tính sử dụng cho các báo cáo lớn hoặc hợp đồng pháp lý.  
- **Kiểm soát toàn diện** – Bạn quyết định cấu trúc, không phải trình xem PDF.  
- **Đa nền tảng** – Hoạt động giống nhau trên Windows, Linux và macOS vì nó thuần Java.  

## Các vấn đề thường gặp và giải pháp
| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|---|---|---|
| Bookmark bị thiếu trong PDF | `startBookmark` không có `endBookmark` tương ứng | Kiểm tra mỗi `startBookmark` đều có `endBookmark` tương ứng. |
| Cấu trúc sai | Cấp độ đề cương được gán không đúng thứ tự | Đảm bảo bookmark cha có số cấp độ thấp hơn bookmark con. |
| Giấy phép chưa được áp dụng | Tệp giấy phép chưa được tải trước khi tạo tài liệu | Tải giấy phép ngay khi khởi động ứng dụng (`License license = new License(); license.setLicense("Aspose.Words.lic");`). |

## Ứng dụng thực tế
1. **Tài liệu pháp lý** – Dễ dàng điều hướng các điều khoản, phụ lục và phụ lục phụ.  
2. **Báo cáo tài chính** – Nhảy giữa các phần như Báo cáo thu nhập, Bảng cân đối kế toán và Ghi chú.  
3. **Tài liệu học trực tuyến** – Cung cấp mục lục phản ánh cấu trúc đề cương PDF.  

## Cân nhắc về hiệu năng
- **Quản lý bộ nhớ** – Đối với các tệp Word rất lớn, cân nhắc gọi `doc.cleanup()` trước khi lưu.  
- **Tối ưu tài nguyên** – Loại bỏ hình ảnh hoặc kiểu không dùng để giảm kích thước PDF.  

## Câu hỏi thường gặp

**Q: Làm thế nào để cài đặt Aspose.Words cho Java?**  
A: Thêm phụ thuộc Maven hoặc Gradle như đã trình bày ở trên, sau đó đặt tệp giấy phép vào classpath và tải nó khi chạy.

**Q: Tôi có thể tạo bookmark mà không đặt cấp độ đề cương không?**  
A: Có, nhưng trình xem PDF sẽ hiển thị chúng dưới dạng danh sách phẳng, có thể gây khó khăn khi điều hướng tài liệu phức tạp.

**Q: Có giới hạn độ sâu của việc lồng bookmark không?**  
A: Về mặt kỹ thuật không, nhưng hầu hết các trình xem PDF hỗ trợ tối đa 9 cấp độ một cách thoải mái. Hãy giữ cấu trúc hợp lý cho người đọc.

**Q: Aspose xử lý các tệp Word rất lớn như thế nào?**  
A: Thư viện truyền dữ liệu dưới dạng luồng và cung cấp các phương thức như `Document.optimizeResources()` để giảm lượng bộ nhớ tiêu thụ.

**Q: Tôi có thể chỉnh sửa bookmark sau khi PDF đã được tạo không?**  
A: Hoàn toàn có thể – bạn có thể dùng Aspose.PDF cho Java để thêm, xóa hoặc đổi tên bookmark trong một PDF đã tồn tại.

## Tài nguyên
- [Tài liệu Aspose.Words](https://reference.aspose.com/words/java/)  
- [Tải xuống bản phát hành mới nhất](https://releases.aspose.com/words/java/)  
- [Mua giấy phép](https://purchase.aspose.com/buy)  
- [Bản dùng thử miễn phí](https://releases.aspose.com/words/java/)  
- [Đăng ký giấy phép tạm thời](https://purchase.aspose.com/temporary-license/)  
- [Diễn đàn hỗ trợ Aspose](https://forum.aspose.com/c/words/10)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2025-11-27  
**Tested With:** Aspose.Words 25.3 for Java  
**Author:** Aspose