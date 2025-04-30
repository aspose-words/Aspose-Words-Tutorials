---
"description": "Tìm hiểu cách tạo Mục lục động bằng Aspose.Words cho Java. Làm chủ việc tạo Mục lục với hướng dẫn từng bước và ví dụ về mã nguồn."
"linktitle": "Mục lục Thế hệ"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Mục lục Thế hệ"
"url": "/vi/java/table-processing/table-contents-generation/"
"weight": 14
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mục lục Thế hệ

## Giới thiệu

Bạn đã bao giờ gặp khó khăn khi tạo Mục lục (TOC) động và chuyên nghiệp trong tài liệu Word của mình chưa? Không cần tìm đâu xa! Với Aspose.Words for Java, bạn có thể tự động hóa toàn bộ quy trình, tiết kiệm thời gian và đảm bảo độ chính xác. Cho dù bạn đang xây dựng một báo cáo toàn diện hay một bài báo học thuật, hướng dẫn này sẽ hướng dẫn bạn cách tạo Mục lục theo chương trình với Java. Sẵn sàng để bắt đầu chưa? Hãy bắt đầu thôi!

## Điều kiện tiên quyết

Trước khi bắt đầu viết mã, hãy đảm bảo bạn có những điều sau:

1. Java Development Kit (JDK): Đã cài đặt trên hệ thống của bạn. Bạn có thể tải xuống từ [Trang web của Oracle](https://www.oracle.com/java/technologies/javase-downloads.html).
2. Aspose.Words cho Thư viện Java: Tải xuống phiên bản mới nhất từ [trang phát hành](https://releases.aspose.com/words/java/).
3. Môi trường phát triển tích hợp (IDE): Chẳng hạn như IntelliJ IDEA, Eclipse hoặc NetBeans.
4. Giấy phép tạm thời Aspose: Để tránh những hạn chế về đánh giá, hãy lấy [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).

## Nhập gói

Để sử dụng Aspose.Words for Java hiệu quả, hãy đảm bảo bạn nhập các lớp cần thiết. Sau đây là các lớp nhập:

```java
import com.aspose.words.*;
```

Thực hiện theo các bước sau để tạo mục lục động trong tài liệu Word của bạn.

## Bước 1: Khởi tạo Document và DocumentBuilder

Bước đầu tiên là tạo một tài liệu mới và sử dụng `DocumentBuilder` lớp để thao tác nó.


```java
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

- `Document`: Biểu thị tài liệu Word.
- `DocumentBuilder`: Một lớp trợ giúp cho phép thao tác tài liệu dễ dàng.

## Bước 2: Chèn Mục lục

Bây giờ, chúng ta hãy chèn Mục lục vào đầu tài liệu.


```java
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");
builder.insertBreak(BreakType.PAGE_BREAK);
```

- `insertTableOfContents`: Chèn một trường TOC. Các tham số chỉ định:
  - `\o "1-3"`: Bao gồm các tiêu đề từ cấp độ 1 đến 3.
  - `\h`: Tạo siêu liên kết cho mục nhập.
  - `\z`: Bỏ số trang cho các tài liệu web.
  - `\u`: Giữ nguyên kiểu cho siêu liên kết.
- `insertBreak`: Thêm ngắt trang sau mục lục.

## Bước 3: Thêm Tiêu đề để Điền vào Mục lục

Để điền mục lục, bạn cần thêm các đoạn văn có kiểu tiêu đề.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 1");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_2);
builder.writeln("Heading 1.1");
builder.writeln("Heading 1.2");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Heading 2");
```

- `setStyleIdentifier`: Đặt kiểu đoạn văn thành một mức tiêu đề cụ thể (ví dụ: `HEADING_1`, `HEADING_2`).
- `writeln`Thêm văn bản vào tài liệu theo kiểu đã chỉ định.

## Bước 4: Thêm Tiêu đề lồng nhau

Để thể hiện mức độ mục lục, hãy bao gồm các tiêu đề lồng nhau.


```java
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_3);
builder.writeln("Heading 3.1.1");
builder.writeln("Heading 3.1.2");
builder.writeln("Heading 3.1.3");

builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_4);
builder.writeln("Heading 3.1.3.1");
builder.writeln("Heading 3.1.3.2");
```

- Thêm tiêu đề ở mức độ sâu hơn để hiển thị thứ bậc trong Mục lục.

## Bước 5: Cập nhật các trường mục lục

Trường TOC phải được cập nhật để hiển thị các tiêu đề mới nhất.


```java
doc.updateFields();
```

- `updateFields`: Làm mới tất cả các trường trong tài liệu, đảm bảo mục lục phản ánh các tiêu đề đã thêm.

## Bước 6: Lưu tài liệu

Cuối cùng, lưu tài liệu theo định dạng mong muốn.


```java
doc.save(dataDir + "DocumentBuilder.InsertToc.docx");
```

- `save`: Xuất tài liệu sang `.docx` tập tin. Bạn có thể chỉ định các định dạng khác như `.pdf` hoặc `.txt` nếu cần.

## Phần kết luận

Xin chúc mừng! Bạn đã tạo thành công Mục lục động trong tài liệu Word bằng Aspose.Words for Java. Chỉ với một vài dòng mã, bạn đã tự động hóa một tác vụ mà nếu không thì có thể mất hàng giờ. Vậy, tiếp theo là gì? Hãy thử nghiệm với các kiểu tiêu đề và định dạng khác nhau để điều chỉnh Mục lục của bạn theo nhu cầu cụ thể.

## Câu hỏi thường gặp

### Tôi có thể tùy chỉnh thêm định dạng mục lục không?
Chắc chắn rồi! Bạn có thể điều chỉnh các thông số mục lục như bao gồm số trang, căn chỉnh văn bản hoặc sử dụng kiểu tiêu đề tùy chỉnh.

### Có bắt buộc phải có giấy phép cho Aspose.Words dành cho Java không?
Có, cần có giấy phép để có đầy đủ chức năng. Bạn có thể bắt đầu bằng [giấy phép tạm thời](https://purchase.aspose.com/temporary-license/).

### Tôi có thể tạo mục lục cho một tài liệu hiện có không?
Vâng! Tải tài liệu vào một `Document` đối tượng và làm theo các bước tương tự để chèn và cập nhật Mục lục.

### Cách này có áp dụng được với file xuất PDF không?
Có, TOC sẽ xuất hiện trong PDF nếu bạn lưu tài liệu ở định dạng `.pdf` định dạng.

### Tôi có thể tìm thêm tài liệu ở đâu?
Kiểm tra các [Tài liệu Aspose.Words cho Java](https://reference.aspose.com/words/java/) để biết thêm ví dụ và thông tin chi tiết.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}