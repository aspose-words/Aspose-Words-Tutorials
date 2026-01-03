---
date: 2026-01-03
description: Tìm hiểu cách điều chỉnh số trang khi chèn mục lục bằng Aspose.Words
  cho Java. Tùy chỉnh kiểu mục lục và tạo tài liệu một cách dễ dàng.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Điều chỉnh số trang & Tạo mục lục với Aspose.Words cho Java
url: /vi/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Điều chỉnh số trang & Tạo mục lục trong Aspose.Words cho Java

Trong hướng dẫn này, bạn sẽ khám phá cách **điều chỉnh số trang** và **chèn mục lục** (TOC) bằng Aspose.Words cho Java. Một mục lục được cấu trúc tốt giúp tài liệu dài dễ dàng điều hướng, và việc tinh chỉnh căn chỉnh số trang mang lại trải nghiệm chuyên nghiệp cho người đọc. Chúng ta sẽ đi qua việc tạo tài liệu, tùy chỉnh kiểu mục lục, và điều chỉnh các tab stop sao cho số trang hiển thị đúng vị trí mong muốn.

## Trả lời nhanh
- **“Điều chỉnh số trang” có nghĩa là gì?** Thay đổi các tab stop căn chỉnh số trang trong mục lục.  
- **Tôi có thể chèn mục lục tự động không?** Có – sử dụng lớp `FieldToc`.  
- **Có cần giấy phép để chạy mã không?** Bản dùng thử miễn phí đủ cho việc phát triển; giấy phép bắt buộc khi triển khai thực tế.  
- **Phiên bản Aspose nào được hỗ trợ?** Các ví dụ hoạt động với bản phát hành mới nhất của Aspose.Words cho Java.  
- **Có thể tùy chỉnh kiểu mục lục không?** Chắc chắn – bạn có thể thay đổi phông chữ, độ đậm, và nhiều hơn nữa.

## Mục lục là gì trong Aspose.Words?
Mục lục là một trường (field) quét tài liệu để tìm các kiểu tiêu đề (ví dụ: Heading 1, Heading 2) và tạo danh sách các mục cùng số trang. Aspose.Words cho phép bạn chèn trường này bằng lập trình và kiểm soát toàn bộ giao diện của nó.

## Tại sao cần điều chỉnh số trang trong mục lục?
Việc điều chỉnh các tab stop cho phép bạn kiểm soát chính xác vị trí hiển thị số trang, điều này quan trọng để:

- Duy trì bố cục cột sạch sẽ, căn chỉnh đồng đều.  
- Tuân thủ các hướng dẫn phong cách của công ty.  
- Cải thiện khả năng đọc trên tài liệu in và điện tử.

## Yêu cầu trước
- Aspose.Words cho Java đã được thêm vào dự án của bạn (Maven/Gradle).  
- Có kiến thức cơ bản về cú pháp Java.  

## Hướng dẫn từng bước

### Bước 1: Tạo tài liệu mới
Đầu tiên, khởi tạo một đối tượng `Document` trống sẽ chứa nội dung và mục lục của bạn.

```java
Document doc = new Document();
```

### Bước 2: Tùy chỉnh kiểu mục lục
Bạn có thể thay đổi giao diện của mỗi cấp độ mục lục. Trong ví dụ này, chúng ta làm cho các mục cấp một in đậm, một yêu cầu định dạng phổ biến.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### Bước 3: Thêm nội dung vào tài liệu
Chèn các tiêu đề (ví dụ: `Heading1`, `Heading2`) và các đoạn văn thông thường. Trường mục lục sẽ tự động nhận diện các tiêu đề này. *(Mã được bỏ qua để ngắn gọn – trọng tâm là tạo mục lục.)*

### Bước 4: Chèn trường mục lục
Đặt mục lục vào vị trí mong muốn — thường là ở đầu tài liệu.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### Bước 5: Lưu tài liệu
Ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ như DOCX, PDF hoặc HTML.

```java
doc.save("your_output_path_here");
```

## Tùy chỉnh Tab Stop trong mục lục (Điều chỉnh số trang)
Nếu tab stop mặc định không căn chỉnh số trang như bạn muốn, bạn có thể duyệt qua tất cả các đoạn mục lục và thay đổi vị trí tab.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Bây giờ các mục trong mục lục sẽ hiển thị số trang chính xác ở vị trí bạn chỉ định, mang lại vẻ ngoài chuyên nghiệp cho tài liệu.

## Các vấn đề thường gặp & Mẹo
- **Tiêu đề không xuất hiện trong mục lục:** Đảm bảo các tiêu đề của bạn sử dụng kiểu tích hợp (`Heading1`, `Heading2`, …) hoặc ánh xạ các kiểu tùy chỉnh tới các cấp độ mục lục.  
- **Tab stop không được áp dụng:** Kiểm tra đoạn văn thực sự thuộc kiểu mục lục (`TOC_1`‑`TOC_9`).  
- **Hiệu năng trên tài liệu lớn:** Gọi `doc.updateFields()` sau khi chèn mục lục để cập nhật các mục trong một lần duyệt.

## Câu hỏi thường gặp

**H: Làm sao thay đổi định dạng của các mục trong mục lục?**  
Đ: Sử dụng `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` trong đó *X* là cấp độ (1‑9) và chỉnh sửa phông chữ, màu sắc hoặc thiết lập đoạn văn.

**H: Làm sao thêm nhiều cấp độ vào mục lục?**  
Đ: Điều chỉnh tùy chọn `\o "1-3"` của `FieldToc` (ví dụ) để bao gồm các cấp độ tiêu đề bổ sung, sau đó cập nhật các kiểu `TOC_X` tương ứng.

**H: Có thể thay đổi vị trí tab stop cho các mục mục lục cụ thể không?**  
Đ: Có – duyệt qua các đoạn như trong phần “Tùy chỉnh Tab Stop” và thay đổi từng tab stop riêng lẻ.

**H: Có thể tạo mục lục trong file PDF không?**  
Đ: Chắc chắn. Lưu tài liệu dưới dạng PDF (`doc.save("output.pdf")`) sau khi tạo mục lục; trường sẽ được render tự động.

**H: Có cần gọi `updateFields()` thủ công không?**  
Đ: Khi chèn `FieldToc`, Aspose.Words sẽ cập nhật nó khi lưu, nhưng gọi `doc.updateFields()` sẽ cho kết quả ngay lập tức, hữu ích việc gỡ lỗi.

## Kết luận
Bạn đã học cách **điều chỉnh số trang**, **chèn mục lục**, và **tùy chỉnh kiểu mục lục** bằng Aspose.Words cho Java. Những kỹ thuật này giúp bạn tạo ra các tài liệu sạch sẽ, dễ dàng điều hướng và có định dạng chuyên nghiệp, đáp ứng mọi tiêu chuẩn xuất bản.

---  

**Cập nhật lần cuối:** 2026-01-03  
**Đã kiểm tra với:** Aspose.Words cho Java (bản phát hành mới nhất)  
**Tác giả:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}