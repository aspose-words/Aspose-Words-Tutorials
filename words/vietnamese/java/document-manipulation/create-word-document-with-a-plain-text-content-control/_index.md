---
category: general
date: 2026-10-04
description: Tạo tài liệu Word bằng Java có bao gồm một điều khiển nội dung văn bản
  thuần và một trình giữ chỗ. Tìm hiểu cách thêm trình giữ chỗ vào thẻ và cách chèn
  sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: vi
lastmod: 2026-10-04
og_description: Tạo tài liệu Word với một điều khiển nội dung văn bản thuần và một
  trình giữ chỗ. Hướng dẫn này cho thấy cách thêm trình giữ chỗ vào thẻ và cách chèn
  sdt bằng Aspose.Words cho Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Tạo tài liệu Word với kiểm soát nội dung – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Tạo tài liệu Word với điều khiển nội dung văn bản thuần
url: /vi/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word với một plain text content control

Nếu bạn cần **tạo tài liệu Word** chứa một vùng người dùng có thể chỉnh sửa, plain text content control là cách tiếp cận đáng tin cậy nhất. Hướng dẫn này chỉ ra cách chèn Structured Document Tag (SDT), đặt placeholder, và lưu kết quả dưới dạng **docx với placeholder**. Bạn sẽ thấy một ví dụ Java đầy đủ, có thể chạy được, hoạt động với Aspose.Words for Java 23.8.

Bài viết bao gồm mọi tiền đề cần thiết, giải thích lý do mỗi lời gọi API quan trọng, và cung cấp các mẹo xử lý các trường hợp đặc biệt như placeholder đa ngôn ngữ hoặc các thẻ lồng nhau. Khi hoàn thành, bạn có thể tạo một tệp Word yêu cầu người dùng “Enter text…” ngay trong tài liệu.

## Tiền đề

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* Java 17 (hoặc mới hơn) đã được cài đặt và cấu hình trong PATH.  
* Maven 3.8+ để quản lý phụ thuộc.  
* Giấy phép Aspose.Words for Java (phiên bản dùng thử cũng đủ cho việc thử nghiệm).  
* Một IDE phát triển (IntelliJ IDEA, Eclipse, hoặc VS Code).

Thêm Aspose.Words vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Tạo tài liệu Word với một plain text content control

Quy trình chính bao gồm bốn bước logic. Mỗi bước được gói trong một phương thức có tên rõ ràng để bạn có thể tái sử dụng trong các dự án lớn hơn.

### Bước 1: Khởi tạo tài liệu và builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Tại sao lại quan trọng:** `Document` đại diện cho tệp Word trong bộ nhớ. `DocumentBuilder` là API dạng fluent cho phép bạn chèn đoạn văn, bảng và SDT. Bắt đầu với một tài liệu trống đảm bảo placeholder xuất hiện ngay đầu tài liệu, rất hữu ích cho các mẫu.

### Bước 2: Chèn một plain‑text Structured Document Tag (SDT)

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Tại sao lại quan trọng:** `StructuredDocumentTagType.PLAIN_TEXT` tạo một content control chỉ chấp nhận ký tự thuần, ngăn ngừa việc định dạng nhầm. Lệnh `setPlaceholderName` điền văn bản gợi ý màu xám mà người dùng sẽ thấy trước khi nhập — đây là thao tác **add placeholder to tag** giúp tài liệu giống như một biểu mẫu.

### Bước 3: Thêm nội dung thường sau SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Tại sao lại quan trọng:** Thêm nội dung sau control xác nhận rằng SDT không chiếm toàn bộ luồng tài liệu. Nó cũng minh họa cách kết hợp các thẻ có cấu trúc với các đoạn văn thông thường, một yêu cầu phổ biến khi xây dựng mẫu.

### Bước 4: Lưu tệp kết quả

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Tại sao lại quan trọng:** Phương thức `save` ghi mô hình trong bộ nhớ ra một tệp **docx với placeholder** thực tế. Tệp đã tạo có thể mở bằng Microsoft Word, LibreOffice, hoặc bất kỳ thư viện nào hỗ trợ định dạng OpenXML.

## Toàn bộ mã nguồn

Kết hợp các phần lại với nhau sẽ cho bạn một chương trình tự chứa, có thể biên dịch và chạy:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Kết quả mong đợi

Chạy chương trình sẽ tạo ra `SdtDemo.docx`. Mở tệp trong Word sẽ hiển thị:

* Một placeholder màu xám “Enter text…” bên trong một plain‑text content control có nhãn **MyTag**.  
* Dòng **After SDT** ngay dưới control.

Placeholder sẽ biến mất ngay khi người dùng gõ, giữ nguyên định dạng gốc.

## Các biến thể phổ biến và trường hợp đặc biệt

| Scenario | Recommended change |
|----------|--------------------|
| **Multilingual placeholder** | Sử dụng ký tự Unicode trong `setPlaceholderName`, ví dụ: `sdt.setPlaceholderName("Введите текст…");`. |
| **Nested content controls** | Chèn một SDT thứ hai bên trong SDT đầu tiên bằng cách gọi `builder.moveTo(sdt.getParagraph());` trước khi thực hiện `insertStructuredDocumentTag` lần thứ hai. |
| **Read‑only control** | Gọi `sdt.setLockContentControl(true);` để ngăn người dùng xóa thẻ. |
| **Rich‑text thay vì plain text** | Thay thế `StructuredDocumentTagType.PLAIN_TEXT` bằng `StructuredDocumentTagType.RICH_TEXT`. |
| **Saving to a stream** | Dùng `doc.save(OutputStream, SaveFormat.DOCX);` khi cần gửi tệp qua HTTP. |

## Mẹo chuyên nghiệp

* **Reuse tag IDs** – Nếu bạn tạo nhiều tài liệu từ cùng một mẫu, giữ tên thẻ (`"MyTag"`) nhất quán để các quy trình xử lý phía sau (ví dụ, mail‑merge) có thể tìm thấy nó một cách đáng tin cậy.  
* **Performance** – Đối với các mẫu lớn, tạo một `DocumentBuilder` duy nhất và tái sử dụng; chèn nhiều SDT trong vòng lặp nhanh hơn so với việc tạo lại builder mỗi lần.  
* **Testing** – Sau khi tạo DOCX, kiểm tra chương trình rằng placeholder tồn tại bằng `doc.getRange().getStructuredDocumentTags().getCount()`.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word** chứa một **plain text content control** với placeholder tùy chỉnh, hiệu quả tạo ra một **docx với placeholder** sẵn sàng cho người dùng nhập liệu. Ví dụ minh họa toàn bộ chu trình từ khởi tạo tài liệu, **cách chèn sdt**, **thêm placeholder vào thẻ**, chèn nội dung thường, và cuối cùng lưu tệp.

### Các bước tiếp theo

* Khám phá **cách chèn sdt** vào bảng để tạo bố cục dạng biểu mẫu.  
* Kết hợp kỹ thuật này với việc **gộp docx với placeholder** để xây dựng các trình tạo báo cáo tự động.  
* Thử nghiệm các loại control khác (`RICH_TEXT`, `CHECKBOX`) để tạo các biểu mẫu Word phong phú hơn.

Hãy tự do điều chỉnh mã cho công cụ mẫu của bạn và chia sẻ kết quả trong phần bình luận!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ, kèm theo giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}