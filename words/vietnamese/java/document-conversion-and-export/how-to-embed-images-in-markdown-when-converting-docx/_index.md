---
category: general
date: 2026-01-11
description: Tìm hiểu cách nhúng hình ảnh vào Markdown khi chuyển đổi tệp DOCX, sử
  dụng Base64 cho các hình ảnh nhỏ và lưu các tài nguyên lớn riêng biệt.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- how to convert docx
- embed images as base64
- export word document markdown
language: vi
og_description: Tìm hiểu cách nhúng hình ảnh trong Markdown khi chuyển đổi tệp DOCX,
  sử dụng Base64 cho các hình ảnh nhỏ và lưu các tài nguyên lớn riêng biệt.
og_title: Cách chèn hình ảnh vào Markdown khi chuyển đổi DOCX
tags:
- Aspose.Words
- Java
- Markdown
- Image Embedding
title: Cách chèn hình ảnh vào Markdown khi chuyển đổi DOCX
url: /vi/java/document-conversion-and-export/how-to-embed-images-in-markdown-when-converting-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Nhúng Hình Ảnh vào Markdown Khi Chuyển Đổi DOCX

Bạn đã bao giờ tự hỏi **cách nhúng hình ảnh** vào một tệp Markdown xuất phát từ tài liệu Word chưa? Bạn không phải là người duy nhất. Hầu hết các nhà phát triển gặp khó khăn khi quá trình chuyển đổi bỏ mất hình ảnh hoặc lưu chúng theo cách làm hỏng bố cục cuối cùng.  

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy, cho thấy **cách nhúng hình ảnh** dưới dạng Base64 data URI cho các đồ họa nhỏ, trong khi các tài nguyên lớn hơn sẽ được ghi vào một thư mục phụ. Trong quá trình này, chúng tôi cũng sẽ đề cập đến **convert docx to markdown**, nói về **how to convert docx** với Aspose.Words, và giải thích sự khác biệt giữa việc nhúng hình ảnh dưới dạng Base64 và xuất chúng ra các tệp riêng biệt.  

> **Pro tip:** Nếu bạn chỉ cần một bằng chứng khái niệm nhanh, đoạn mã dưới đây hoạt động ngay lập tức với một phụ thuộc Maven duy nhất.

---

## Những Gì Bạn Cần

- **Java 17** (hoặc bất kỳ JDK hiện đại nào) – API tập trung vào Java, nhưng các khái niệm có thể áp dụng cho các ngôn ngữ khác.  
- **Aspose.Words for Java** – thư viện thương mại hỗ trợ chuyển đổi DOCX → Markdown.  
- Một **sample DOCX** chứa hỗn hợp các biểu tượng nhỏ và ảnh lớn hơn.  
- Một thư mục nơi bạn muốn lưu Markdown và các tài nguyên của nó.  

Không cần framework bổ sung, không cần script bên ngoài. Chỉ cần Java thuần và Aspose.Words.

---

## Bước 1 – Thêm Aspose.Words vào Dự Án của Bạn (convert docx to markdown)

Nếu bạn đang sử dụng Maven, chèn đoạn mã sau vào `pom.xml` của bạn. Tự do thay thế phiên bản bằng bản phát hành mới nhất tại thời điểm đọc.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for newer versions -->
</dependency>
```

> **Why this matters:** Aspose.Words xử lý phần nặng của việc phân tích cấu trúc DOCX, trích xuất hình ảnh và tạo ra cú pháp Markdown. Cố gắng tự viết trình phân tích của mình sẽ là một lỗ sâu mà bạn có lẽ không cần phải đi vào.

---

## Bước 2 – Load the Source DOCX Document

Đầu tiên, chỉ định API tới tệp Word bạn muốn chuyển đổi. Hàm khởi tạo `Document` thực hiện toàn bộ công việc — không cần phân tích XML thủ công.

```java
import com.aspose.words.*;

public class MarkdownResourceCallback {
    public static void main(String[] args) throws Exception {
        // Step 2: Load the source DOCX document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Lưu ý phần chú thích giải thích *tại sao* dòng này quan trọng: nếu không có một thể hiện `Document` thì không có gì để chuyển đổi.

---

## Bước 3 – Prepare MarkdownSaveOptions with a Resource‑Saving Callback

Đây là phần cốt lõi của **cách nhúng hình ảnh** một cách chính xác. Callback cung cấp một điểm gắn cho mỗi tài nguyên (hình ảnh, kiểu dáng, v.v.) mà bộ chuyển đổi muốn ghi.

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

- **Control:** Bạn quyết định hình ảnh sẽ trở thành chuỗi Base64 nội tuyến hay một tệp riêng.  
- **Performance:** Các biểu tượng nhỏ sẽ trở thành một phần của Markdown, loại bỏ các yêu cầu HTTP thêm.  
- **Portability:** Các ảnh lớn hơn sẽ ở dạng tệp ngoại vi, giữ cho kích thước Markdown ở mức hợp lý.

---

## Bước 4 – Save the Document as Markdown

Cuối cùng, yêu cầu Aspose.Words ghi tệp Markdown bằng các tùy chọn chúng ta vừa cấu hình.

```java
        // Step 5: Save the document as Markdown using the configured options
        doc.save("YOUR_DIRECTORY/output.md", saveOptions);
    }
}
```

Chạy chương trình sẽ tạo ra hai thứ:

1. `output.md` – bản đại diện Markdown của DOCX gốc của bạn.  
2. Thư mục `markdown_resources` chứa bất kỳ hình ảnh lớn nào không được nhúng.

---

## Full Working Example (All Steps in One Place)

Dưới đây là tệp nguồn hoàn chỉnh, sẵn sàng sao chép‑dán vào IDE của bạn. Thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế trên máy của bạn.

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

**Expected output:** Mở `output.md` trong bất kỳ trình xem Markdown nào. Các biểu tượng nhỏ sẽ xuất hiện nội tuyến, ví dụ:

```markdown
![Embedded Icon](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
```

Các ảnh lớn hơn sẽ được tham chiếu như:

```markdown
![Photo](markdown_resources/photo1.jpg)
```

Đó chính là những gì bạn cần để **nhúng hình ảnh** đồng thời vẫn giữ kích thước tệp ở mức quản lý được.

---

## Các Câu Hỏi Thường Gặp & Trường Hợp Cạnh

### Nếu một hình ảnh là JPEG thay vì PNG thì sao?

Callback ở trên luôn thêm tiền tố URI là `image/png`. Đối với JPEG, bạn có thể kiểm tra vài byte đầu của `args.getData()` hoặc sử dụng `args.getFileName()` để suy ra MIME type đúng:

```java
String mime = args.getFileName().toLowerCase().endsWith(".jpg") ||
              args.getFileName().toLowerCase().endsWith(".jpeg")
              ? "image/jpeg" : "image/png";
args.setUri("data:" + mime + ";base64," + base64);
```

### Tôi có thể thay đổi ngưỡng kích thước không?

Chắc chắn rồi. Giới hạn `10_000` byte chỉ là một ví dụ. Nếu bạn có ngân sách băng thông rộng rãi, có thể tăng lên 50 KB hoặc hơn. Ngược lại, giảm nó nếu bạn cần các tệp Markdown siêu nhẹ.

### Điều này có hoạt động với bảng hoặc các đối tượng Word khác không?

Có. Aspose.Words tự động chuyển đổi bảng, danh sách và thậm chí chú thích cuối trang sang Markdown. Callback tài nguyên chỉ can thiệp vào hình ảnh, vì vậy bạn không cần mã bổ sung cho các yếu tố khác.

### Còn các tên tệp không phải ASCII thì sao?

API mã hoá an toàn các tên tệp Unicode khi ghi vào thư mục `markdown_resources`. Chỉ cần đảm bảo hệ thống tệp của bạn hỗ trợ UTF‑8 (hầu hết các OS hiện đại đều hỗ trợ).

---

## Pro Tips for a Smooth Conversion

- **Keep the output folder clean.** Chỉ chạy `Files.createDirectories` một lần cho mỗi lần chuyển đổi, hoặc xóa thư mục trước mỗi lần chạy nếu bạn muốn bắt đầu mới.  
- **Validate the Markdown.** Các công cụ như `markdownlint` có thể phát hiện ký tự lạ do chuỗi Base64 bị hỏng.  
- **Version lock Aspose.Words.** Một phiên bản cụ thể đảm bảo mã của bạn vẫn hoạt động ngay cả khi bản phát hành lớn thay đổi hành vi mặc định.  
- **Use a .gitignore** entry for `markdown_resources/

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}