---
category: general
date: 2026-07-03
description: Xuất các đối tượng nổi thành nội tuyến khi chuyển đổi Word sang PDF nội
  tuyến. Tìm hiểu cách thiết lập các tùy chọn PDF và lưu Word dưới dạng PDF trong
  Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: vi
og_description: Xuất các hình dạng nổi dưới dạng nội dòng khi bạn chuyển đổi tài liệu
  Word sang PDF. Hướng dẫn này cho thấy cách thiết lập các tùy chọn PDF và lưu Word
  dưới dạng PDF.
og_title: Xuất các hình dạng nổi trong dòng – Hướng dẫn chuyển đổi PDF bằng Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Xuất hình dạng nổi nội tuyến – Hướng dẫn toàn diện về chuyển đổi PDF
url: /vi/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xuất các hình dạng nổi trong dòng – Hướng dẫn đầy đủ về chuyển đổi PDF

Bạn đã bao giờ cần **xuất các hình dạng nổi trong dòng** khi chuyển đổi tài liệu Word sang PDF chưa? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp phải vấn đề này khi các biểu đồ hoặc biểu tượng của họ bất ngờ chuyển sang các lớp riêng biệt. Tin tốt là một tùy chọn PDF duy nhất có thể giữ các hình dạng này gọn gàng bên trong thẻ `<span>`, bảo toàn bố cục chính xác như bạn thấy trong Word.

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn **cách đặt các tùy chọn PDF** trong Java, cho bạn đoạn mã chính xác để **lưu Word dưới dạng tùy chọn PDF**, và giải thích tại sao bạn có thể muốn **chuyển đổi Word sang PDF trong dòng** thay vì xuất mặc định ở mức khối. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy mà bạn có thể chèn vào bất kỳ dự án Maven hoặc Gradle nào.

## Những gì bạn sẽ học

- Sự khác biệt giữa xuất `<span>` trong dòng và `<div>` khối cho các hình dạng nổi.  
- Cách cấu hình `PdfSaveOptions` để buộc hiển thị trong dòng.  
- Mã từng bước tải một tệp `.docx`, áp dụng tùy chọn, và ghi ra PDF.  
- Những cạm bẫy thường gặp (phông chữ thiếu, hình dạng không được hỗ trợ) và cách tránh chúng.  
- Mẹo kiểm tra đầu ra và mở rộng cách tiếp cận này cho các thành phần tài liệu khác.

**Điều kiện tiên quyết** – bạn sẽ cần Java 8 hoặc mới hơn, thư viện Aspose.Words for Java (hoặc bất kỳ API nào có lớp `PdfSaveOptions` tương tự), và một tệp Word mẫu có các hình dạng nổi (hướng dẫn này sử dụng `FloatingShapes.docx`). Không cần công cụ bên ngoài nào khác.

---

## Bước 1: Tải tài liệu Word nguồn

Điều đầu tiên bạn làm là mở file `.docx` muốn chuyển đổi. Điều này khá đơn giản, nhưng hãy chắc chắn rằng đường dẫn là tuyệt đối hoặc được giải quyết đúng từ classpath của bạn.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Lý do quan trọng:*  
Nếu tài liệu không được tải đúng, quá trình chuyển đổi PDF tiếp theo sẽ ném ra `FileNotFoundException`. Việc sử dụng `Document` đảm bảo mô hình đối tượng nội bộ được khởi tạo đầy đủ, bao gồm mọi hình dạng nổi hiện trên trang.

---

## Bước 2: Tạo PDF Save Options và Đặt Hình dạng Nổi thành Inline

Đây là nơi phép thuật xảy ra. Mặc định Aspose.Words xuất các hình dạng nổi dưới dạng phần tử `<div>` mức khối, có thể phá vỡ luồng trong các PDF dựa trên HTML. Đặt `setExportFloatingShapesAsInlineTag(true)` sẽ yêu cầu engine bọc mỗi hình dạng trong một thẻ `<span>` inline thay vì.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Lý do quan trọng:*  
- **Độ chính xác bố cục** – Thẻ inline giữ hình dạng căn chỉnh với văn bản xung quanh, tránh các khoảng trống không mong muốn.  
- **Khả năng tìm kiếm** – Các phần tử inline có khả năng được các trình đọc PDF lập chỉ mục đúng hơn.  
- **Kiểm soát kiểu dáng** – Bạn có thể nhắm mục tiêu tới `<span>` bằng CSS nếu sau này chuyển PDF lại thành HTML.

> **Mẹo chuyên nghiệp:** Nếu bạn cần hành vi khối cũ cho một tài liệu cụ thể, chỉ cần truyền `false` hoặc bỏ qua lời gọi này.

---

## Bước 3: Lưu tài liệu dưới dạng PDF bằng các tùy chọn đã cấu hình

Bây giờ bạn kết hợp `Document` đã tải với `PdfSaveOptions` và ghi file ra. Dòng lệnh duy nhất này thực hiện phần việc nặng.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Lý do quan trọng:*  
Phương thức `save` tôn trọng mọi cờ bạn đã đặt trên `pdfOptions`. Bỏ qua việc truyền các tùy chọn sẽ quay lại xuất khối mặc định, làm mất mục đích **xuất các hình dạng nổi trong dòng**.

---

## Ví dụ Hoạt động Đầy đủ

Kết hợp tất cả lại, đây là một chương trình gọn gàng mà bạn có thể biên dịch và chạy ngay. Thay `YOUR_DIRECTORY` bằng đường dẫn thực tế trên máy của bạn.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Kết quả mong đợi** – Sau khi chạy chương trình, mở `FloatingShapes.pdf`. Bạn sẽ thấy các hình dạng nằm sát văn bản, không có khoảng trắng thừa, và biểu diễn HTML (nếu bạn kiểm tra cấu trúc nội bộ của PDF) sẽ chứa các thẻ `<span>` quanh mỗi hình dạng.

![Xuất các hình dạng nổi trong dòng ví dụ](https://example.com/export-inline.png "Ảnh chụp màn hình cho thấy các hình dạng nổi được hiển thị trong dòng trong PDF")

*Văn bản thay thế ảnh:* **xuất các hình dạng nổi trong dòng** ảnh chụp màn hình PDF với các hình dạng inline.

---

## Câu hỏi Thường gặp & Trường hợp Cạnh

### 1. “Nếu tài liệu của tôi chứa SmartArt phức tạp thì sao?”

SmartArt được xử lý như một đối tượng vẽ. Cờ inline hoạt động với hầu hết các hình dạng vector, nhưng SmartArt rất phức tạp có thể vẫn được xuất dưới dạng hình ảnh. Trong những trường hợp đó, hãy cân nhắc làm phẳng SmartArt trong Word trước khi chuyển đổi, hoặc sử dụng `pdfOptions.setExportSmartArtAsImage(true)` để buộc xuất dưới dạng hình ảnh.

### 2. “Tôi có thể kết hợp xuất inline và block trong cùng một tài liệu không?”

Thật không may, API áp dụng cài đặt này trên toàn bộ tài liệu. Nếu bạn cần hành vi hỗn hợp, hãy chia tài liệu thành các phần, xuất mỗi phần riêng biệt với các tùy chọn khác nhau, sau đó hợp nhất các PDF bằng `PdfMerger`.

### 3. “Điều này có ảnh hưởng tới việc nhúng phông chữ không?”

Không. Việc nhúng phông chữ được điều khiển bởi `pdfOptions.setEmbedFullFonts(true)` (mặc định). Bạn có thể bật hoặc tắt nó mà không ảnh hưởng tới cờ hình dạng inline.

### 4. “Làm sao tôi kiểm tra rằng các hình dạng thực sự là `<span>`?”

Mở PDF kết quả trong công cụ như **PDF.js** hoặc **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Bạn sẽ thấy hình dạng được bọc trong một phần tử `<span>` trong XML nền. Nếu bạn thấy `<div>`, tùy chọn chưa được áp dụng.

---

## Mở rộng Cách Tiếp Cận – Các Tùy chọn Liên quan

Khi bạn đã ở đây, có thể bạn cũng muốn khám phá các tùy chỉnh chuyển đổi PDF khác:

| Tùy chọn | Chức năng | Trường hợp sử dụng điển hình |
|----------|-----------|------------------------------|
| `setCompressImages(true)` | Giảm kích thước ảnh | Tải xuống nhanh hơn |
| `setUseHighQualityRendering(true)` | Cải thiện việc render vector | PDF chuẩn in |
| `setExportDocumentStructure(true)` | Thêm thẻ cấu trúc cho khả năng truy cập | Tuân thủ WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Đặt định dạng một cách rõ ràng (hiếm khi cần) | Quy trình đa định dạng |

Các cài đặt này kết hợp tốt với các kịch bản **chuyển đổi word sang pdf inline** nơi bạn cần cả độ chính xác bố cục và hiệu suất.

---

## Kiểm thử Quá trình Chuyển đổi

1. **Kiểm tra trực quan** – Mở PDF trong hai trình xem (Chrome và Adobe Reader) để đảm bảo các hình dạng thẳng hàng.  
2. **So sánh tự động** – Sử dụng thư viện như `pdfbox` để trích xuất XML và khẳng định sự hiện diện của thẻ `<span>`.  
3. **Đánh giá hiệu năng** – Đo thời gian thực hiện có và không có `setCompressImages` để thấy sự đánh đổi.

Một ví dụ JUnit nhanh:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Kết luận

Bạn đã có một giải pháp toàn diện, đầu‑từ‑đầu‑đến cho **xuất các hình dạng nổi trong dòng** khi **chuyển đổi Word sang PDF trong dòng**. Bằng cách cấu hình `PdfSaveOptions` bạn kiểm soát thẻ HTML được dùng cho mỗi hình dạng, giữ cho PDF của bạn gọn gàng và có thể tìm kiếm. Hãy nhớ kiểm tra đầu ra, điều chỉnh các tùy chọn liên quan như nén ảnh, và xử lý các trường hợp đặc biệt như SmartArt phức tạp.

Sẵn sàng cho bước tiếp theo? Hãy thử áp dụng kỹ thuật tương tự để **xuất các bảng nổi trong dòng** hoặc thử nghiệm PDF có kiểu CSS bằng `HtmlSaveOptions` của Aspose. Mẫu lặp lại—tải, cấu hình, lưu—áp dụng cho hầu hết các kịch bản chuyển đổi tài liệu sang PDF.

Có thêm câu hỏi về **cách đặt pdf options** hoặc cần trợ giúp với **save word as pdf options** cho thư viện khác? Để lại bình luận, và chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}