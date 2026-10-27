---
category: general
date: 2026-10-23
description: Tìm hiểu cách chèn hình ảnh vào markdown khi chuyển đổi tệp DOCX, sử
  dụng Base64 cho các đồ họa nhỏ và tệp ngoại vi cho các hình ảnh lớn hơn.
draft: false
keywords:
- how to embed images
- embed images in markdown
- convert docx to markdown
- extract images from docx
- embed images as base64
lastmod: 2026-10-23
og_description: Tìm hiểu cách chèn hình ảnh vào markdown khi chuyển đổi tệp DOCX,
  sử dụng Base64 cho các đồ họa nhỏ và tệp ngoại vi cho các hình ảnh lớn hơn. Hướng
  dẫn này trình bày các bước chính xác với Aspose.Words for Java.
og_image_alt: Screenshot of markdown output with embedded Base64 images generated
  by Aspose.Words for Java
og_title: Cách chèn hình ảnh vào markdown – Hướng dẫn chuyển đổi DOCX bằng Java
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to embed images in markdown when converting a DOCX file,
    using Base64 for tiny graphics and external files for larger pictures.
  headline: How to embed images in markdown when converting docx
  type: TechArticle
- questions:
  - answer: Yes. The same API works in any Java environment, including servlet containers
      and Spring Boot applications. Just stream the `output.md` back to the client
      after conversion.
    question: Can I use this approach in a web service that generates Markdown on
      the fly?
  - answer: A valid Aspose.Words license is required for production deployments. A
      free evaluation license is available for testing and development.
    question: Is a commercial license required for production use?
  - answer: Load the document with `new Document("file.docx", new LoadOptions("password"))`.
      The same conversion pipeline then applies.
    question: How do I handle password‑protected DOCX files?
  - answer: Convert the SVG to PNG or JPEG first, then let the callback treat it as
      any other image. Aspose.Words does not natively render SVG inside Markdown.
    question: What if I need to embed SVG images?
  - answer: Yes. Aspose.Words for Java is platform‑agnostic and runs wherever a compatible
      JDK is available.
    question: Does this work on Windows, macOS, and Linux?
  type: FAQPage
tags:
- Aspose.Words
- Java
- markdown
- image embedding
- docx conversion
- developer guide
title: Cách chèn hình ảnh vào markdown khi chuyển đổi docx
url: /vi/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhúng hình ảnh trong markdown khi chuyển đổi docx

Bạn đã bao giờ tự hỏi **cách nhúng hình ảnh** trong một tệp Markdown xuất phát từ tài liệu Word chưa? Bạn không phải là người duy nhất. Hầu hết các nhà phát triển gặp khó khăn khi quá trình chuyển đổi bỏ mất hình ảnh hoặc lưu chúng theo cách làm hỏng bố cục cuối cùng.  

Trong hướng dẫn này, chúng tôi sẽ trình bày một ví dụ hoàn chỉnh, sẵn sàng chạy, cho thấy **cách nhúng hình ảnh** dưới dạng URI dữ liệu Base64 cho các đồ họa nhỏ, trong khi các tài nguyên lớn hơn được ghi vào một thư mục phụ. Trong quá trình này, chúng tôi cũng sẽ đề cập đến **convert docx to markdown**, đề cập tới **how to convert docx** với Aspose.Words, và giải thích sự khác biệt giữa việc nhúng hình ảnh dưới dạng Base64 và xuất chúng thành các tệp riêng biệt.  

> **Mẹo:** Nếu bạn chỉ cần một bằng chứng khái niệm nhanh, đoạn mã dưới đây hoạt động ngay lập tức với một phụ thuộc Maven duy nhất.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc chuyển đổi?** Aspose.Words for Java thực hiện chuyển đổi DOCX → Markdown và trích xuất hình ảnh.
- **Các hình ảnh nhỏ được lưu như thế nào?** Chúng được nhúng dưới dạng URI dữ liệu Base64 trực tiếp trong tệp Markdown.
- **Các hình ảnh lớn được lưu ở đâu?** Các ảnh lớn hơn được lưu vào thư mục `markdown_resources` bên cạnh tệp Markdown.
- **Có cần cài đặt Microsoft Word không?** Không, Aspose.Words hoạt động hoàn toàn độc lập với Microsoft Office.
- **Yêu cầu phiên bản Java nào?** Java 17 hoặc bất kỳ bản LTS nào sau này.

## Cách nhúng hình ảnh là gì?
`how to embed images` đề cập đến kỹ thuật chèn dữ liệu hình ảnh trực tiếp vào tài liệu Markdown, hoặc dưới dạng URI dữ liệu được mã hoá Base64 hoặc dưới dạng liên kết tương đối tới một tệp bên ngoài. Cách tiếp cận này cho phép bạn giữ một tệp Markdown duy nhất, di động cho các đồ họa nhỏ trong khi vẫn hỗ trợ các tài nguyên độ phân giải cao qua các tệp riêng.

## Tại sao nên nhúng hình ảnh trong markdown?
Việc nhúng hình ảnh dưới dạng Base64 giảm số yêu cầu HTTP cho các biểu tượng và đồ họa nhỏ, có thể cải thiện tốc độ tải trang lên tới 30 % trên các mạng có độ trễ thấp. Đồng thời, việc giữ các ảnh lớn ở bên ngoài ngăn tệp Markdown phình to quá 5 MB, bảo vệ hiệu năng của trình soạn thảo và các diff trong hệ thống kiểm soát phiên bản.

## Yêu cầu trước
- **Java 17** (hoặc bất kỳ JDK mới nào). API tập trung vào Java, nhưng các khái niệm có thể áp dụng cho các ngôn ngữ khác.
- **Aspose.Words for Java** – một thư viện thương mại hỗ trợ chuyển đổi DOCX → Markdown.
- Một **tệp DOCX mẫu** chứa hỗn hợp các biểu tượng nhỏ và ảnh lớn hơn.
- Một thư mục có thể ghi được, nơi tệp Markdown và các tài nguyên của nó sẽ được lưu.

Không cần framework bổ sung, không cần script bên ngoài. Chỉ cần Java thuần và Aspose.Words.

## Những gì bạn cần để thêm Aspose.Words vào dự án của mình (convert docx to markdown)
Nếu bạn đang sử dụng Maven, chèn đoạn mã sau vào `pom.xml` của bạn. Tự do thay thế phiên bản bằng bản phát hành mới nhất tại thời điểm đọc.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Tại sao điều này quan trọng:** Aspose.Words thực hiện công việc nặng nề trong việc phân tích cấu trúc DOCX, trích xuất hình ảnh và tạo ra cú pháp Markdown. Cố gắng tự viết trình phân tích của mình sẽ là một lỗ sâu mà bạn có lẽ không cần phải đi vào.

## Lớp Document hoạt động như thế nào?
`Document` là đối tượng cốt lõi của Aspose.Words đại diện cho một tệp Word duy nhất trong bộ nhớ. Nó cung cấp các phương thức để tải, sửa đổi và lưu tài liệu ở nhiều định dạng.
Nó bao bọc toàn bộ cấu trúc tài liệu, bao gồm các phần, đoạn văn, bảng và tài nguyên nhúng, cho phép bạn thao tác nội dung một cách lập trình mà không cần xử lý XML bên dưới.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

## Cách quyết định giữa Base64 và tệp bên ngoài với callback
Callback tài nguyên là một triển khai của `IResourceSavingCallback` cho phép bạn chặn mỗi hình ảnh trong quá trình chuyển đổi.
Đây là phần cốt lõi của **cách nhúng hình ảnh** một cách chính xác. Callback cung cấp một điểm hook cho mỗi tài nguyên (hình ảnh, kiểu, v.v.) mà bộ chuyển đổi muốn ghi. Bằng cách kiểm tra kích thước hình ảnh, bạn có thể quyết định nhúng nó dưới dạng URI dữ liệu hoặc lưu nó thành tệp bên ngoài, giúp cân bằng hiệu năng và kích thước tệp.

```java
        // Step 3: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Step 4: Decide how to handle each image
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    // Small image – embed as Base64
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger image – write to a folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        // Normalize path for Markdown (use forward slashes)
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });
```

### Tại sao lại cần callback?
- **Kiểm soát:** Bạn quyết định hình ảnh sẽ trở thành chuỗi Base64 nội tuyến hay một tệp riêng.
- **Hiệu năng:** Các biểu tượng nhỏ trở thành một phần của Markdown, loại bỏ các yêu cầu HTTP bổ sung.
- **Tính di động:** Các ảnh lớn hơn vẫn ở dạng tệp bên ngoài, giữ kích thước Markdown ở mức hợp lý.

## Cách lưu tài liệu dưới dạng markdown
SaveOptions là một đối tượng cấu hình kiểm soát cách Aspose.Words ghi đầu ra, bao gồm định dạng, mã hoá và xử lý tài nguyên.
Cuối cùng, chỉ định cho Aspose.Words ghi tệp Markdown bằng các tùy chọn chúng ta vừa cấu hình. Đối tượng `SaveOptions` cho phép bạn chỉ định thư mục đầu ra, callback tài nguyên và các tùy chọn định dạng khác, đảm bảo Markdown được tạo phù hợp với quy ước dự án của bạn. Bạn cũng có thể bật hoặc tắt việc tạo mục lục và kiểm soát cách chú thích được hiển thị.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Chạy chương trình sẽ tạo ra hai thứ:

1. `output.md` – bản đại diện Markdown của DOCX gốc của bạn.  
2. Một thư mục `markdown_resources` chứa bất kỳ hình ảnh lớn nào không được nhúng.

## Ví dụ hoàn chỉnh (tất cả các bước trong một nơi)

Dưới đây là tệp nguồn đầy đủ, sẵn sàng sao chép‑dán vào IDE của bạn. Thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế trên máy của bạn.

```java
import com.aspose.words.*;
import java.nio.file.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Create Markdown save options and define a resource‑saving callback
        MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
        saveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
            public void resourceSaving(ResourceSavingArgs args) {
                // Small images (<10 KB) become Base64 data URIs
                if (args.getResourceType() == ResourceType.IMAGE && args.getData().length < 10_000) {
                    String base64 = java.util.Base64.getEncoder()
                            .encodeToString(args.getData());
                    args.setUri("data:image/png;base64," + base64);
                    args.setKeepResourceStreamOpen(false);
                } else {
                    // Larger images are written to a dedicated folder
                    Path outPath = Paths.get("markdown_resources", args.getFileName());
                    try {
                        Files.createDirectories(outPath.getParent());
                        Files.write(outPath, args.getData());
                        args.setUri(outPath.toString().replace('\\', '/'));
                    } catch (Exception e) {
                        throw new RuntimeException(e);
                    }
                }
            }
        });

        // Step 3: Save the document as Markdown
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

**Kết quả mong đợi:** Mở `output.md` trong bất kỳ trình xem Markdown nào. Các biểu tượng nhỏ xuất hiện nội tuyến, ví dụ:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

[Biểu tượng nhúng](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)

Các ảnh lớn được tham chiếu như sau:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

[Ảnh](markdown_resources/photo1.jpg)

Đó chính là những gì bạn cần để **nhúng hình ảnh** đồng thời vẫn giữ kích thước tệp ở mức có thể quản lý.

## Các câu hỏi thường gặp & trường hợp đặc biệt

### Nếu hình ảnh là JPEG thay vì PNG thì sao?
Callback ở trên luôn thêm tiền tố `image/png` vào URI. Đối với JPEG, bạn có thể kiểm tra vài byte đầu tiên của `args.getData()` hoặc sử dụng `args.getFileName()` để suy ra loại MIME đúng:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Tôi có thể thay đổi ngưỡng kích thước không?
Chắc chắn. Giới hạn `10_000` byte chỉ là một ví dụ. Nếu bạn có ngân sách băng thông rộng rãi, hãy tăng lên 50 KB hoặc hơn. Ngược lại, giảm nó nếu bạn cần các tệp Markdown siêu nhẹ.

### Điều này có hoạt động với bảng hoặc các đối tượng Word khác không?
Có. Aspose.Words tự động chuyển đổi bảng, danh sách và thậm chí chú thích thành Markdown. Callback tài nguyên chỉ chặn hình ảnh, vì vậy bạn không cần mã bổ sung cho các yếu tố khác.

### Còn các tên tệp không phải ASCII thì sao?
API mã hoá an toàn các tên tệp Unicode khi ghi vào thư mục `markdown_resources`. Chỉ cần đảm bảo hệ thống tệp của bạn hỗ trợ UTF‑8 (hầu hết các hệ điều hành hiện đại đều hỗ trợ).

## Mẹo khắc phục sự cố và những lỗi thường gặp
- **Thiếu hình ảnh sau khi chuyển đổi:** Kiểm tra `args.getData()` trong callback không phải null và thư mục đầu ra có quyền ghi.  
- **Chuỗi Base64 bị hỏng:** Đảm bảo lời gọi `Base64.getEncoder().encodeToString()` nhận được mảng byte đầy đủ; việc cắt ngắn thường xảy ra khi luồng không được đọc hết.  
- **Tệp Markdown lớn:** Nếu `.md` tạo ra vượt quá 5 MB, hãy cân nhắc giảm ngưỡng kích thước hoặc nén các hình ảnh lớn trước khi lưu chúng vào thư mục tài nguyên.  
- **Không tương thích phiên bản:** Aspose.Words 24.9+ hỗ trợ hơn 35 định dạng đầu ra và có thể xử lý DOCX 500 trang trong vòng dưới 4 giây trên máy chủ 2.5 GHz tiêu chuẩn. Khóa phiên bản Maven để tránh hành vi không mong muốn sau khi có bản phát hành lớn.

## Câu hỏi thường gặp

**Q: Tôi có thể sử dụng cách tiếp cận này trong dịch vụ web tạo Markdown nhanh không?**  
A: Có. Cùng một API hoạt động trong bất kỳ môi trường Java nào, bao gồm các container servlet và ứng dụng Spring Boot. Chỉ cần stream `output.md` trở lại client sau khi chuyển đổi.

**Q: Cần giấy phép thương mại để sử dụng trong môi trường production không?**  
A: Cần một giấy phép Aspose.Words hợp lệ cho việc triển khai production. Một giấy phép đánh giá miễn phí có sẵn cho việc thử nghiệm và phát triển.

**Q: Làm thế nào để xử lý các tệp DOCX được bảo vệ bằng mật khẩu?**  
A: Tải tài liệu bằng `new Document("file.docx", new LoadOptions("password"))`. Quy trình chuyển đổi tương tự sẽ được áp dụng.

**Q: Nếu tôi cần nhúng hình ảnh SVG thì sao?**  
A: Đầu tiên chuyển đổi SVG sang PNG hoặc JPEG, sau đó để callback xử lý như bất kỳ hình ảnh nào khác. Aspose.Words không hỗ trợ render SVG trực tiếp trong Markdown.

**Q: Điều này có hoạt động trên Windows, macOS và Linux không?**  
A: Có. Aspose.Words for Java không phụ thuộc vào nền tảng và chạy ở bất kỳ nơi nào có JDK tương thích.

---

**Cập nhật lần cuối:** 2026-10-23  
**Kiểm tra với:** Aspose.Words for Java 24.10  
**Tác giả:** Aspose

## Hướng dẫn liên quan

- [Lưu hình ảnh Word Chuyển đổi Docx sang Markdown với Java](/words/java/document-conversion-and-export/save-word-images-convert-docx-to-markdown-with-java/)
- [Tải hình ảnh lên CDN khi chuyển đổi Docx sang Markdown - Full](/words/java/document-conversion-and-export/upload-images-to-cdn-while-converting-docx-to-markdown-full/)
- [Hướng dẫn Java đầy đủ chuyển đổi Docx sang Markdown](/words/java/document-conversion-and-export/convert-docx-to-markdown-complete-java-guide/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}