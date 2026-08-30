---
category: general
date: 2026-08-07
description: Cách chỉnh sửa chú thích trong Java với Aspose.Words – thêm dấu gạch
  tùy chỉnh, thay đổi đường chú thích và thiết lập căn chỉnh đoạn văn cho tài liệu
  hoàn thiện.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: vi
lastmod: 2026-08-07
og_description: Cách chỉnh sửa chú thích trong Java với Aspose.Words. Tìm hiểu cách
  thêm dấu gạch tùy chỉnh, thay đổi dòng chú thích và thiết lập căn chỉnh đoạn văn
  chỉ trong vài bước.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Cách chỉnh sửa chú thích trong Java – thêm dấu gạch ngang, thay đổi dòng,
  đặt căn chỉnh
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Cách chỉnh sửa chú thích trong Java với Aspose.Words
url: /vi/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách chỉnh sửa footnote trong Java với Aspose.Words

Nếu bạn cần **cách chỉnh sửa footnote** trong một tài liệu Word bằng Java, hướng dẫn này sẽ trình bày quy trình hoàn chỉnh. Bạn sẽ học cách thêm dấu gạch tùy chỉnh, thay đổi dòng footnote, và đặt căn chỉnh đoạn văn để dấu phân cách footnote trông chuyên nghiệp.

Việc chỉnh sửa footnote là yêu cầu phổ biến khi chuẩn bị hợp đồng pháp lý, bài báo học thuật, hoặc brochure marketing. Các bước dưới đây bao phủ mọi thứ bạn cần—từ tải tài liệu đến lưu tệp cuối cùng—mà không cần công cụ bổ sung.

## Yêu cầu trước

* Java 17 hoặc mới hơn đã được cài đặt.  
* Aspose.Words for Java (phiên bản mới nhất) đã được thêm vào classpath của dự án.  
* Một tệp DOCX (`input.docx`) chứa ít nhất một footnote.  

Những mục này đảm bảo mã chạy mà không gặp lỗi runtime.

## Cách chỉnh sửa footnote separator và line

Dấu phân cách footnote là đoạn văn xuất hiện giữa văn bản chính và danh sách footnote. Thay đổi giao diện của nó cải thiện khả năng đọc và phù hợp với thương hiệu công ty.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Tại sao mỗi dòng lại quan trọng

1. **Tải tài liệu** – `new Document(...)` đọc tệp DOCX vào bộ nhớ, cho phép bạn truy cập tất cả các nút của nó.  
2. **Lấy dấu phân cách** – `getFootnoteSeparator()` trả về đoạn văn đặc biệt mà Aspose.Words coi là dòng footnote. Đối tượng này là nơi duy nhất bạn có thể an toàn chỉnh sửa dấu phân cách.  
3. **Đặt căn chỉnh đoạn** – `setAlignment(ParagraphAlignment.CENTER)` thay đổi căn chỉnh của dòng. Từ khóa *set paragraph alignment* được áp dụng trực tiếp lên dấu phân cách, đảm bảo dấu gạch được căn giữa.  
4. **Thêm dấu gạch tùy chỉnh** – Bằng cách xóa các run hiện có và thêm một `Run` mới với ký tự em‑dash (`—`), bạn đạt được hiệu ứng *add custom dash* đồng thời *change footnote line* theo kiểu mong muốn.  
5. **Lưu tài liệu** – `doc.save(...)` ghi các thay đổi trở lại đĩa, tạo ra tệp đầu ra phản ánh mọi sửa đổi.  

## Thêm dấu gạch tùy chỉnh vào footnote separator

Mã trong **Bước 4** minh họa kỹ thuật *add custom dash*. Bạn có thể thay thế em‑dash bằng bất kỳ chuỗi nào, chẳng hạn `"***"` hoặc `"---"`, để phù hợp với ngôn ngữ trực quan của tài liệu.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Việc sử dụng dấu gạch tùy chỉnh đặc biệt hữu ích khi đường mỏng mặc định không đáp ứng các tiêu chuẩn thương hiệu.

## Thay đổi kiểu dòng footnote

Nếu bạn muốn một đường liền thay vì dấu gạch, có thể chèn ký tự vẽ hộp Unicode hoặc một chuỗi gạch dưới lặp lại.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

Bước *change footnote line* hoạt động tương tự bất kể ký tự bạn chọn, vì đoạn văn phân cách chỉ đơn giản hiển thị văn bản mà nó chứa.

## Đặt căn chỉnh đoạn cho footnote separator

Thao tác *set paragraph alignment* không chỉ giới hạn ở căn giữa. Bạn có thể căn trái, phải, hoặc căn đều tùy theo nhu cầu bố cục.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Căn dấu phân cách sang bên phải có thể hữu ích cho các tài liệu sử dụng footnote căn phải, chẳng hạn các ấn phẩm song ngữ.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh tích hợp tất cả các khái niệm—tải tài liệu, chỉnh sửa footnote separator, thêm dấu gạch tùy chỉnh, thay đổi kiểu dòng, và đặt căn chỉnh.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Kết quả mong đợi:** Tệp `output.docx` chứa một dấu em‑dash căn giữa nơi trước đây là đường mỏng. Tất cả các footnote vẫn nguyên vẹn, và bố cục tài liệu phản ánh kiểu dấu phân cách mới.

## Những lỗi thường gặp và cách tránh

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|------------|----------------|
| Không tìm thấy dấu phân cách | Tài liệu không có footnote hoặc sử dụng kiểu footnote tùy chỉnh | Đảm bảo tệp DOCX nguồn chứa ít nhất một footnote trước khi gọi `getFootnoteSeparator()` |
| Dấu gạch tùy chỉnh không hiển thị | Phông chữ không hỗ trợ ký tự đã chọn | Sử dụng ký tự Unicode được hỗ trợ bởi phông chữ mặc định của tài liệu, hoặc nhúng phông chữ tương thích |
| Căn chỉnh không thay đổi | Định dạng đoạn văn bị ghi đè sau trong mã | Áp dụng căn chỉnh **sau** bất kỳ lời gọi định dạng nào khác có thể đặt lại nó |

Việc giải quyết những điểm này ngăn ngừa lỗi runtime và đảm bảo quy trình *cách chỉnh sửa footnote* hoạt động đáng tin cậy.

## Các bước tiếp theo

Bây giờ bạn đã biết **cách chỉnh sửa footnote** các phần tử, có thể khám phá các nhiệm vụ liên quan:

* **Thêm kiểu tham chiếu footnote tùy chỉnh** – sửa đổi các nút `FootnoteReference` để thay đổi số thứ tự hoặc ký hiệu.  
* **Chèn footnote mới bằng lập trình** – sử dụng `DocumentBuilder.insertFootnote()` cho nội dung động.  
* **Áp dụng định dạng có điều kiện** – thay đổi giao diện footnote dựa trên kiểu đoạn văn hoặc độ dài nội dung.  

Mỗi phần mở rộng này dựa trên cùng một API mà bạn đã dùng để *add custom dash*, *change footnote line*, và *set paragraph alignment*.

---

*Chúc lập trình vui vẻ! Nếu hướng dẫn đã giúp bạn thành thạo việc chỉnh sửa footnote, hãy cân nhắc chia sẻ nó với đội ngũ của bạn hoặc đóng góp một pull request để cải thiện ví dụ hơn nữa.*

## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoàn chỉnh, kèm giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Đặt Vị Trí Chú Thích và Ghi Chú Cuối](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words cho Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cách Đặt LoadOptions trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}