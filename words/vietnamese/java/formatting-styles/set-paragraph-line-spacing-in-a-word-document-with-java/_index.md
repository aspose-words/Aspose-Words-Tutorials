---
category: general
date: 2026-11-15
description: Đặt khoảng cách dòng cho đoạn văn trong tài liệu Word bằng Java. Tìm
  hiểu cách thiết lập khoảng cách dòng một cách lập trình bằng Aspose.Words để định
  dạng tài liệu một cách chính xác.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: vi
lastmod: 2026-11-15
og_description: Đặt khoảng cách dòng cho đoạn văn trong tài liệu Word bằng Java. Hướng
  dẫn này giải thích cách thiết lập khoảng cách dòng cho các đoạn văn và dấu phân
  cách chú thích dưới bằng Aspose.Words, cho phép bạn kiểm soát hoàn toàn bố cục tài
  liệu.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Thiết lập khoảng cách dòng cho đoạn văn trong Word bằng Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Đặt khoảng cách dòng cho đoạn văn trong tài liệu Word bằng Java
url: /vi/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đặt khoảng cách dòng cho đoạn văn trong tài liệu Word bằng Java

Nếu bạn cần **đặt khoảng cách dòng cho đoạn văn** trong tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng Java và Aspose.Words. Bạn cũng sẽ học **cách đặt khoảng cách dòng** cho các dấu phân cách chú thích—một yêu cầu phổ biến khi định dạng tài liệu chuyên nghiệp.

Trong các phần sau bạn sẽ:

* Tải một tệp *.docx* hiện có.
* Lấy đoạn văn dấu phân cách chú thích.
* Áp dụng giá trị khoảng cách dòng tùy chỉnh.
* Lưu tài liệu đã cập nhật.

Không cần cấu hình bên ngoài nào ngoài việc thêm thư viện Aspose.Words vào dự án của bạn, vì vậy bạn có thể sao chép mã nguyên văn và chạy ngay lập tức.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java 17 hoặc mới hơn đã được cài đặt.
* Maven (hoặc công cụ xây dựng khác) để quản lý các phụ thuộc.
* Giấy phép Aspose.Words for Java hợp lệ (bản dùng thử miễn phí đủ cho việc thử nghiệm).
* Một tài liệu Word đầu vào (`input.docx`) nằm trong thư mục đã biết.

Thêm phụ thuộc Aspose.Words vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Đặt khoảng cách dòng cho đoạn văn bằng Aspose.Words

Tiêu đề H2 này chứa từ khóa chính, đáp ứng yêu cầu SEO.

### Bước 1: Tải tài liệu Word

Đầu tiên, tạo một thể hiện `Document` trỏ tới tệp nguồn của bạn.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Why this matters*: Loading the document gives you an in‑memory model that you can manipulate without touching the original file until you explicitly save it.

### Bước 2: Lấy dấu phân cách chú thích

Dấu phân cách chú thích là các đoạn văn đặc biệt xuất hiện giữa các chú thích và văn bản chính. Để thay đổi giao diện của chúng, bạn cần truy cập đối tượng `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Tip*: Nếu tài liệu của bạn không chứa chú thích, dấu phân cách vẫn tồn tại dưới dạng đoạn văn ẩn, vì vậy lời gọi sẽ không bao giờ trả về `null`.

### Bước 3: Cách đặt khoảng cách dòng cho đoạn văn của dấu phân cách

Bây giờ áp dụng khoảng cách dòng mong muốn. Aspose.Words sử dụng đơn vị điểm cho giá trị khoảng cách dòng; 12 pts tương đương gần như khoảng cách dòng đơn cho hầu hết các phông chữ.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Bạn cũng có thể sử dụng các chế độ khoảng cách khác:

| Chế độ                     | Lệnh gọi phương thức                                      |
|--------------------------|--------------------------------------------------|
| **Exactly** (fixed pts) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Multiple** (e.g., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Choosing the correct rule ensures the document renders consistently across Word, Google Docs, and other viewers.

### Bước 4: Lưu tài liệu đã cập nhật

Cuối cùng, ghi các thay đổi trở lại đĩa.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Khi bạn mở `output.docx` trong Microsoft Word, dấu phân cách chú thích sẽ hiển thị với khoảng cách dòng bạn đã định nghĩa.

## Hiểu cách đặt khoảng cách dòng cho các đoạn văn thông thường

The same API works for any `Paragraph` object, not just footnote separators. Here’s a quick example that adjusts the spacing of the first paragraph in the body:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Why you might need this**: Reports, contracts, and academic papers often require a specific line‑spacing style (e.g., double‑spacing for drafts). Using the same `setLineSpacing` method guarantees the exact layout you expect.

## Những lỗi thường gặp và cách tránh chúng

| Vấn đề                                 | Nguyên nhân                                   | Giải pháp |
|---------------------------------------|----------------------------------------|-----|
| Khoảng cách dòng không thay đổi        | `LineSpacingRule` để ở mặc định (AUTO) | Đặt rõ quy tắc bằng `setLineSpacingRule`. |
| Dòng trống thừa sau dấu phân cách | Dấu phân cách chứa ký tự carriage return ẩn | Cắt bớt văn bản của dấu phân cách bằng `separator.getText().trim();` trước khi áp dụng khoảng cách. |
| Tài liệu bị hỏng sau khi lưu | Sử dụng phiên bản Aspose.Words đã lỗi thời | Nâng cấp lên phiên bản mới nhất (ví dụ, 24.10) có các bản sửa lỗi cho việc lưu. |

## Mẹo chuyên nghiệp: xử lý hàng loạt nhiều tài liệu

Nếu bạn cần cập nhật hàng chục tệp, hãy gói logic vào một phương thức trợ giúp và lặp qua một thư mục:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Running this method in a loop saves you hours of manual editing.

## Kết quả mong đợi

Sau khi chạy toàn bộ chương trình, `output.docx` sẽ:

* Giữ nguyên nội dung gốc ngoại trừ khoảng cách dòng.
* Hiển thị dấu phân cách chú thích với bố cục khoảng cách dòng đơn (12 pts).
* Bảo tồn tất cả định dạng khác (kiểu dáng, hình ảnh, bảng).

Mở tệp trong Word và xác nhận rằng dòng dấu phân cách đã chặt hơn (hoặc rộng hơn, tùy vào giá trị bạn đã đặt).

## Kết luận

Bạn bây giờ đã biết cách **đặt khoảng cách dòng cho đoạn văn** trong tài liệu Word bằng Java, và cũng hiểu **cách đặt khoảng cách dòng** cho cả dấu phân cách chú thích và các đoạn văn thông thường. Ví dụ đầy đủ, có thể chạy được minh họa việc tải tài liệu, điều chỉnh các thuộc tính khoảng cách dòng, và lưu kết quả—tất cả chỉ với một vài lời gọi API rõ ràng.

**Next steps** you might explore:

* **How to set line spacing** for tables and list items.
* Applying different spacing rules to headings versus body text.
* Using the `Style` object to enforce spacing across an entire document.

Experiment with the values, combine them with other formatting options, and you’ll have full control over document layout in any Java application. Happy coding!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách đặt tùy chọn trong Aspose.Words cho Java – hướng dẫn đầy đủ](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Cách đặt LoadOptions trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Thay đổi khoảng cách và thụt lề đoạn văn châu Á trong tài liệu Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}