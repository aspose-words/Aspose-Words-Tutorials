---
date: 2026-01-11
description: Tìm hiểu cách hiển thị/ẩn dấu trang và tạo dấu trang Java bằng Aspose.Words
  for Java để điều hướng và thao tác tài liệu hiệu quả.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Hiển thị và ẩn dấu trang với Aspose.Words cho Java
url: /vi/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hiển thị và Ẩn Dấu trang với Aspose.Words cho Java

## Giới thiệu về việc sử dụng Dấu trang trong Aspose.Words cho Java

Dấu trang là một tính năng mạnh mẽ trong Aspose.Words cho Java cho phép bạn **create bookmark java**, điều hướng đến nội dung cụ thể, và thậm chí **show hide bookmarks** khi bạn cần tạo các phiên bản tài liệu khác nhau. Trong hướng dẫn từng bước này, chúng tôi sẽ trình bày cách tạo, truy cập, cập nhật, sao chép và chuyển đổi trạng thái hiển thị của dấu trang, giúp bạn kiểm soát hoàn toàn việc thao tác tài liệu.

## Câu trả lời nhanh
- **What is the primary purpose of bookmarks?** Đánh dấu và sau đó truy xuất các phần cụ thể của tài liệu.  
- **Can I hide bookmark markers in the final output?** Có—sử dụng API show/hide để chuyển đổi hiển thị của chúng.  
- **How do I create a bookmark inside a table cell?** Bắt đầu và kết thúc dấu trang bằng `DocumentBuilder` khi con trỏ nằm trong ô bảng.  
- **Is it possible to copy bookmarked text to another document?** Chắc chắn—sử dụng `NodeImporter` để giữ nguyên định dạng.  
- **What version of Aspose.Words is required?** Bất kỳ phiên bản gần đây nào; mã hoạt động với bản dựng mới nhất năm 2026.

## Tính năng “show hide bookmarks” là gì?

Tính năng **show hide bookmarks** cho phép bạn hiển thị hoặc ẩn các dấu phân cách của dấu trang một cách lập trình trong tài liệu đã lưu. Điều này hữu ích khi bạn muốn tạo ra đầu ra sạch sẽ cho người dùng cuối đồng thời vẫn giữ lại dữ liệu dấu trang cho việc xử lý nội bộ.

## Tại sao nên sử dụng dấu trang trong tự động hoá tài liệu Java?

- **Efficient navigation** – Nhảy trực tiếp đến các phần mà không cần quét toàn bộ tệp.  
- **Dynamic content generation** – Chèn, thay thế hoặc xóa văn bản liên kết với dấu trang.  
- **Conditional visibility** – Hiển thị hoặc ẩn các dấu trang dựa trên sở thích người dùng hoặc định dạng đầu ra.  
- **Reusability** – Sao chép các đoạn có dấu trang giữa các tài liệu trong khi giữ nguyên kiểu dáng.

## Yêu cầu trước
- Java Development Kit (JDK) 8 hoặc cao hơn.  
- Thư viện Aspose.Words cho Java được thêm vào dự án của bạn (Maven/Gradle hoặc JAR).  
- Kiến thức cơ bản về các lớp `Document` và `DocumentBuilder`.

## Hướng dẫn từng bước

### Bước 1: Tạo Dấu trang (create bookmark java)

Để thêm một dấu trang, bạn bắt đầu nó, viết nội dung, sau đó kết thúc. Ví dụ này tạo một dấu trang đơn giản có tên **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Bước 2: Truy cập Dấu trang (access bookmarks java)

Dấu trang có thể được truy xuất bằng chỉ mục bắt đầu từ 0 hoặc bằng tên. Đoạn mã dưới đây minh họa cả hai cách tiếp cận.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Bước 3: Cập nhật Dữ liệu Dấu trang (update bookmark text)

Bạn có thể đổi tên dấu trang hoặc thay thế nội dung văn bản của nó. Điều này hữu ích khi tài liệu gốc thay đổi.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Bước 4: Làm việc với Văn bản có Dấu trang (copy bookmarked text)

Sao chép một đoạn có dấu trang sang tài liệu khác trong khi giữ nguyên định dạng gốc là rất đơn giản với `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Bước 5: Hiển thị và Ẩn Dấu trang (show hide bookmarks)

Đoạn mã sau minh họa cách ẩn các dấu của dấu trang trong tệp đã lưu. Truyền `false` để ẩn, `true` để hiển thị.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Bước 6: Gỡ rối Dấu trang trên Hàng (bookmark table cell)

Khi dấu trang bao phủ nhiều hàng của bảng, chúng có thể bị rối. Các phương thức tiện ích dưới đây sẽ gỡ rối chúng và cho phép bạn xóa một hàng cụ thể bằng dấu trang của nó.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Các vấn đề thường gặp và giải pháp

| Issue | Solution |
|-------|----------|
| **Bookmark not found** | Xác minh tên dấu trang khớp chính xác (phân biệt chữ hoa/thường) và tài liệu đã được lưu sau khi tạo. |
| **Copied text loses formatting** | Sử dụng `ImportFormatMode.KEEP_SOURCE_FORMATTING` cùng với `NodeImporter` như đã minh họa ở Bước 4. |
| **Show/hide does not affect output** | Đảm bảo bạn gọi `showHideBookmarkedContent` **trước** khi lưu tài liệu. |
| **Bookmark inside a table cell is ignored** | Đặt các lời gọi start/end khi con trỏ builder nằm trong ô mục tiêu. |

## Câu hỏi thường gặp

**Q: How do I create a bookmark in a table cell?**  
A: Sử dụng `DocumentBuilder` để di chuyển con trỏ vào ô mong muốn, sau đó gọi `startBookmark` và `endBookmark` quanh nội dung ô.

**Q: Can I copy a bookmark to another document?**  
A: Có—sử dụng lớp `NodeImporter` (xem Bước 4) để nhập node có dấu trang trong khi giữ nguyên định dạng gốc.

**Q: How can I delete a row by its bookmark?**  
A: Đầu tiên xác định hàng chứa dấu trang, sau đó gọi `remove` trên node hàng (như đã minh họa trong Bước 6).

**Q: What are some common use cases for bookmarks?**  
A: Tạo mục lục, trích xuất các phần cụ thể cho báo cáo, và tự động lắp ráp tài liệu dựa trên lựa chọn của người dùng.

**Q: Where can I find more information about Aspose.Words for Java?**  
A: Để xem tài liệu chi tiết và tải xuống, truy cập [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

---

**Cập nhật lần cuối:** 2026-01-11  
**Kiểm thử với:** Aspose.Words cho Java 24.11 (2026)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}