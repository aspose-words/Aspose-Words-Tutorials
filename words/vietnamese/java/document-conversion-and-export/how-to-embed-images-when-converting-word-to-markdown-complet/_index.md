---
category: general
date: 2026-02-28
description: Tìm hiểu cách nhúng hình ảnh khi chuyển đổi tài liệu sang markdown. Xuất
  markdown có hình ảnh và nhận các hình ảnh nội tuyến trong markdown bằng Java.
draft: false
keywords:
- how to embed images
- convert doc to markdown
- convert word to markdown
- export markdown with images
- inline images in markdown
language: vi
og_description: Khám phá cách nhúng hình ảnh khi chuyển đổi tài liệu Word sang Markdown.
  Hướng dẫn này chỉ cho bạn cách xuất Markdown có hình ảnh và giữ chúng ở dạng nội
  tuyến.
og_title: Cách chèn hình ảnh khi chuyển đổi Word sang Markdown
tags:
- markdown
- java
- Aspose.Words
- image handling
title: Cách Nhúng Hình Ảnh Khi Chuyển Đổi Word Sang Markdown – Hướng Dẫn Toàn Diện
url: /vi/java/document-conversion-and-export/how-to-embed-images-when-converting-word-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Nhúng Hình Ảnh Khi Chuyển Đổi Word Sang Markdown – Hướng Dẫn Toàn Diện

Bạn đã bao giờ tự hỏi **cách nhúng hình ảnh** trong một tệp Markdown mà bạn tạo từ tài liệu Word chưa? Có thể bạn đã thử xuất nhanh, nhưng chỉ nhận được một loạt các tệp hình ảnh rời rạc và các liên kết bị hỏng. Đó là một vấn đề phổ biến—đặc biệt khi bạn cần một tệp `.md` duy nhất, di động mà bạn có thể đưa vào một static‑site generator hoặc README trên GitHub.

Tin tốt? Bạn có thể yêu cầu trình xuất nhúng mỗi hình ảnh dưới dạng chuỗi Base64, vì vậy Markdown tạo ra sẽ tự chứa toàn bộ nội dung. Trong hướng dẫn này, chúng tôi sẽ đi qua từng bước cụ thể, cho bạn xem toàn bộ mã Java, và giải thích lý do mỗi phần quan trọng. Khi kết thúc, bạn sẽ có thể **chuyển đổi doc sang markdown** với hình ảnh được nhúng, và cũng sẽ biết cách điều chỉnh quy trình cho các kịch bản khác như “xuất markdown với hình ảnh” hoặc “nhúng hình ảnh trong markdown”.

## Những Điều Bạn Sẽ Học

- Các thư viện cần thiết và cấu hình dự án tối thiểu.  
- Cách cấu hình `MarkdownSaveOptions` để hình ảnh trở thành Base64 data URIs.  
- Tại sao việc sử dụng `ResourceSavingCallback` là cách sạch nhất để kiểm soát việc xử lý hình ảnh.  
- Cách xác minh rằng tệp Markdown thực sự chứa các hình ảnh được nhúng.  
- Mẹo cho các trường hợp đặc biệt (hình ảnh lớn, các loại MIME khác nhau, và các cân nhắc về hiệu năng).

Bạn không cần kinh nghiệm trước với Aspose.Words; chỉ cần nền tảng Java cơ bản là đủ.

## Yêu Cầu Trước

Trước khi chúng ta bắt đầu với mã, hãy chắc chắn rằng bạn đã có:

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** (or any recent JDK) | API Aspose.Words for Java nhắm tới Java 8+, nhưng việc sử dụng JDK mới nhất sẽ cung cấp các tiện ích `Base64` tích hợp. |
| **Aspose.Words for Java** (latest version) | Thư viện này cung cấp `MarkdownSaveOptions` và cơ sở hạ tầng callback mà chúng ta sẽ sử dụng. |
| **A Word document** (`.docx`) that contains at least one image | Chúng ta cần một thứ gì đó để chuyển đổi; ví dụ giả định một tệp có tên `sample.docx`. |
| **An IDE or text editor** (IntelliJ, VS Code, etc.) | Để biên dịch và chạy mẫu nhanh chóng. |

Thêm phụ thuộc Aspose vào `pom.xml` (Maven) hoặc `build.gradle` (Gradle) của bạn. Dưới đây là đoạn mã Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Check the latest version on Maven Central -->
</dependency>
```

Bạn muốn dùng Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Mẹo chuyên nghiệp:** Aspose cung cấp bản dùng thử miễn phí 30 ngày. Lấy một khóa giấy phép tạm thời và đăng ký sớm để tránh các thông báo watermark.

## Bước 1: Tạo Markdown Save Options

Điều đầu tiên chúng ta làm là khởi tạo `MarkdownSaveOptions`. Đối tượng này cho Aspose biết cách chúng ta muốn quá trình chuyển đổi hoạt động—xử lý phông chữ, định dạng danh sách, và quan trọng nhất đối với chúng ta là xử lý hình ảnh.

```csharp
// Step 1: Create Markdown save options
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions();
```

Trong Java, cú pháp giống hệt; chỉ cần thay thế từ khóa `csharp` bằng `java` trong khối mã sau.  
Tại sao điều này quan trọng: nếu không tùy chỉnh các tùy chọn, Aspose sẽ ghi mỗi hình ảnh vào một tệp riêng bên cạnh `.md`. Bằng cách chuẩn bị đối tượng tùy chọn ngay bây giờ, chúng ta tạo một điểm can thiệp để chặn hành vi mặc định đó.

## Bước 2: Chặn Tài Nguyên Hình Ảnh và Mã Hóa Chúng Thành Base64

Aspose kích hoạt một callback mỗi khi nó muốn ghi một tài nguyên (hình ảnh, CSS, v.v.). Bằng cách triển khai `IResourceSavingCallback` chúng ta có thể quyết định làm gì với mỗi tài nguyên. Đoạn mã dưới đây kiểm tra xem tài nguyên có phải là hình ảnh không, xóa tên tệp (để không tạo tệp ngoại vi), mã hóa dữ liệu nhị phân thành Base64, và đặt loại MIME phù hợp.

```java
// Step 2: Embed all images directly as Base64 data
markdownSaveOptions.setResourceSavingCallback(new IResourceSavingCallback() {
    @Override
    public void resourceSaving(ResourceSavingArgs args) {
        // Check if the resource being saved is an image
        if (args.getResourceType() == ResourceType.IMAGE) {
            // Suppress writing an external image file
            args.setResourceFileName(null);
            // Encode the image bytes to a Base64 string
            args.setResourceData(Base64.getEncoder()
                    .encodeToString(args.getResourceData()));
            // Set the appropriate MIME type for the embedded image
            args.setResourceContentType("image/png");
        }
    }
});
```

**Điều gì đang diễn ra bên trong?**

1. **`args.getResourceType()`** – Aspose phân loại mọi blob xuất ra. Chúng ta chỉ quan tâm đến `ResourceType.IMAGE`.  
2. **`args.setResourceFileName(null)`** – Bằng cách đặt tên tệp thành null, chúng ta thông báo cho thư viện *không* ghi tệp vật lý.  
3. **`Base64.getEncoder().encodeToString(...)`** – Mảng byte thô trở thành một chuỗi văn bản có thể an toàn đặt trong một Markdown data URI.  
4. **`args.setResourceContentType("image/png")`** – Điều này đảm bảo thẻ Markdown được tạo ra có dạng `![alt](data:image/png;base64,…)`. Nếu tài liệu nguồn của bạn chứa JPEG, bạn có thể kiểm tra các byte gốc và chọn `"image/jpeg"` thay thế.

> **Tại sao lại dùng Base64?**  
> Các trình xử lý Markdown hiểu data URI sẽ hiển thị hình ảnh trực tiếp, và tệp kết quả vẫn di động—không cần sao chép tài nguyên bổ sung. Điều này đặc biệt hữu ích cho README trên GitHub hoặc các trang tài liệu không cho phép tài nguyên bên ngoài.

## Bước 3: Thực Hiện Việc Chuyển Đổi

Bây giờ các tùy chọn đã sẵn sàng, chỉ cần tải tài liệu Word của bạn và gọi `save`. Đường dẫn bạn cung cấp sẽ là vị trí của tệp Markdown được tạo.

```java
// Step 3: Load the source Word document
Document doc = new Document("sample.docx");

// Step 4: Save the document as a Markdown file using the configured options
doc.save("output/doc.md", markdownSaveOptions);
```

Xong rồi—chỉ hai dòng mã thực hiện chuyển đổi. Các công việc nặng (đọc DOCX, trích xuất hình ảnh, chuyển đổi đoạn văn) đều được Aspose xử lý.

## Bước 4: Xác Minh Kết Quả – Hình Ảnh Nhúng Xuất Hiện

Mở `output/doc.md` trong bất kỳ trình soạn thảo văn bản nào. Bạn sẽ thấy một thứ gì đó như:

```markdown
# Sample Document

Here is an inline image:

![Image 1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...
```

Nếu bạn dán Markdown vào một trình xem hỗ trợ data URI (GitHub, xem trước VS Code, hoặc một static‑site generator), hình ảnh sẽ hiển thị mà không cần tệp bổ sung.

**Kiểm tra nhanh**:  

- **Tìm `data:image/`** – Nếu bạn thấy một vài chuỗi dài, việc nhúng đã thành công.  
- **Đếm các mẫu `![](`** – Chúng nên khớp với số lượng hình ảnh trong tệp Word gốc.

## Xử Lý Các Trường Hợp Đặc Biệt

### Hình Ảnh Lớn

Base64 làm tăng kích thước gốc khoảng **33 %**. Đối với các hình ảnh rất lớn (ví dụ, ảnh độ phân giải cao), tệp Markdown có thể trở nên cồng kềnh. Hãy cân nhắc các chiến lược sau:

| Strategy | When to use |
|----------|--------------|
| **Resize before conversion** – Use `java.awt.Image` to scale down. | Khi tài liệu nguồn chứa các tài nguyên độ phân giải cao không cần kích thước đầy đủ. |
| **Switch to JPEG** – Change `args.setResourceContentType("image/jpeg")`. | Khi ảnh là ảnh chụp, định dạng PNG không cần thiết. |
| **Chunk the document** – Split the Word file into sections and export each separately. | Khi bạn cần giữ tệp Markdown dưới một giới hạn kích thước nhất định (ví dụ, giới hạn 10 MB của GitHub). |

### Hình Ảnh Không Phải PNG

Nếu tài liệu Word của bạn chứa các định dạng hỗn hợp, bạn có thể phát hiện MIME type một cách động:

```java
String mime = args.getResourceContentType(); // returns something like "image/jpeg"
args.setResourceContentType(mime); // keep original type
```

Aspose đã tự điền `ResourceContentType`, vì vậy bạn thường không cần phải hard‑code "image/png".

### Mẹo Về Hiệu Năng

- **Tái sử dụng một thể hiện `Base64.Encoder` duy nhất** nếu bạn đang chuyển đổi nhiều hình ảnh trong một vòng lặp.  
- **Bật `markdownSaveOptions.setExportImagesAsBase64(true)`** (nếu phiên bản API hỗ trợ) để tránh hoàn toàn callback.  
- **Chạy chuyển đổi trong một luồng nền** khi xử lý hàng loạt tài liệu trong môi trường server.

## Ví Dụ Hoàn Chỉnh (Tất Cả Cùng Nhau)

Dưới đây là một chương trình Java sẵn sàng copy‑paste, bao gồm các import, xử lý lỗi, và toàn bộ luồng chúng ta đã thảo luận.

```java
import com.aspose.words.*;
import java.util.Base64;
import java.nio.file.Paths;

public class WordToMarkdownWithEmbeddedImages {
    public static void main(String[] args) {
        try {
            // Load the source DOCX
            Document doc = new Document("sample.docx");

            // Configure Markdown save options
            MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();

            // Embed images as Base64 data URIs
            mdOptions.setResourceSavingCallback(new IResourceSavingCallback() {
                @Override
                public void resourceSaving(ResourceSavingArgs rsArgs) {
                    if (rsArgs.getResourceType() == ResourceType.IMAGE) {
                        // Prevent external file creation
                        rsArgs.setResourceFileName(null);
                        // Encode image bytes to Base64
                        String base64 = Base64.getEncoder()
                                .encodeToString(rsArgs.getResourceData());
                        rsArgs.setResourceData(base64);
                        // Preserve original MIME type (PNG, JPEG, etc.)
                        String mime = rsArgs.getResourceContentType();
                        rsArgs.setResourceContentType(mime);
                    }
                }
            });

            // Define output path (ensure directory exists)
            String outputPath = Paths.get("output", "doc.md").toString();
            doc.save(outputPath, mdOptions);

            System.out.println("Conversion complete! Markdown saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("Error during conversion: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Kết quả mong đợi**: một tệp `doc.md` duy nhất chứa các hình ảnh Base64 nhúng, sẵn sàng cho bất kỳ công cụ nào hỗ trợ Markdown.

## Câu Hỏi Thường Gặp

**Q1: Điều này có hoạt động với các phiên bản cũ hơn của Aspose.Words không?**  
*Thường thì có.* API callback đã ổn định kể từ phiên bản 19. Tuy nhiên, shortcut `setExportImagesAsBase64` xuất hiện trong các bản phát hành sau, vì vậy nếu bạn đang dùng bản cũ hơn, bạn sẽ cần callback rõ ràng như đã trình bày ở trên.

**Q2: Nếu tôi cần xuất ra GitHub Flavored Markdown (GFM) thì sao?**  
`MarkdownSaveOptions` của Aspose đã phát sinh cú pháp tương thích GFM. Bước bổ sung duy nhất là đảm bảo engine render của repository hỗ trợ data URI—GitHub có hỗ trợ.

**Q3: Tôi có thể dùng cách này cho các định dạng khác, như HTML không?**  
Chắc chắn. `ResourceSavingCallback` tương tự hoạt động cho `HtmlSaveOptions`. Chỉ cần thay đổi lớp tùy chọn và giữ lại logic Base64.

## 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}