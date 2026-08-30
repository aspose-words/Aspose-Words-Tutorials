---
category: general
date: 2026-06-24
description: Cách xử lý cảnh báo khi xử lý các tệp Word trong Java. Tìm hiểu cách
  bắt phông chữ, in thông báo phông chữ và xử lý các phông chữ thiếu một cách mượt
  mà.
draft: false
keywords:
- how to handle warnings
- how to capture fonts
- print font messages
- handle missing fonts
language: vi
og_description: cách xử lý cảnh báo trong Aspose.Words cho Java. Hướng dẫn này cho
  thấy cách bắt phông chữ, in thông báo phông chữ và quản lý các phông chữ thiếu một
  cách hiệu quả.
og_title: cách xử lý cảnh báo trong Aspose.Words – Hướng dẫn Java đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  headline: how to handle warnings in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: how to handle warnings when processing Word files in Java. Learn how
    to capture fonts, print font messages, and handle missing fonts smoothly.
  name: how to handle warnings in Aspose.Words for Java – Full Guide
  steps:
  - name: The document actually references a missing font.
    text: The document actually references a missing font.
  - name: The path to `input.docx` is correct.
    text: The path to `input.docx` is correct.
  - name: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
    text: You’re using a recent version of Aspose.Words (older builds sometimes suppress
      certain warnings).
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Cách xử lý cảnh báo trong Aspose.Words cho Java – Hướng dẫn đầy đủ
url: /vi/java/document-rendering/how-to-handle-warnings-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cách xử lý cảnh báo trong Aspose.Words for Java – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi **cách xử lý cảnh báo** xuất hiện khi tải tài liệu Word bằng Aspose.Words chưa? Có thể bạn đã thấy những thông báo khó hiểu về thiếu phông chữ và nghĩ, “Tuyệt, file PDF của tôi lệch—bây giờ sao?” Bạn không phải là người duy nhất. Trong nhiều dự án thực tế, các cảnh báo thay thế phông chữ là những thủ phạm im lặng làm hỏng độ chính xác bố cục.

Trong tutorial này, chúng ta sẽ đi qua một giải pháp thực tiễn: đăng ký callback cảnh báo, phát hiện các cảnh báo liên quan đến phông chữ, và **in ra thông báo phông chữ** để bạn có thể quyết định nhúng phông thay thế hoặc cung cấp file phông tùy chỉnh. Khi kết thúc, bạn sẽ biết **cách bắt phông chữ**, **xử lý phông chữ thiếu** một cách nhẹ nhàng, và giữ cho quy trình chuyển đổi tài liệu của bạn luôn ổn định.

## Những gì bạn sẽ học

- Mục đích của callback cảnh báo trong Aspose.Words.
- Cách phát hiện và lọc các cảnh báo *thay thế phông chữ*.
- Các cách ghi log hoặc hiển thị **in ra thông báo phông chữ** để debug.
- Các chiến lược **xử lý phông chữ thiếu** trong môi trường production.
- Một ví dụ Java hoàn chỉnh, sẵn sàng chạy mà bạn có thể đưa vào bất kỳ dự án Maven hoặc Gradle nào.

### Yêu cầu trước

- Java 8 hoặc mới hơn (mã cũng hoạt động với JDK 11).
- Thư viện Aspose.Words for Java (tải từ trang Aspose hoặc thêm dependency Maven/Gradle).
- Một file mẫu `input.docx` tham chiếu tới một phông chữ bạn không có sẵn trên máy (hoàn hảo để thử callback).

---

## Bước 1: Thiết lập dự án và nhập Aspose.Words

Trước khi bạn có thể **xử lý cảnh báo**, bạn cần một dự án Java đã biết tới Aspose.Words. Nếu bạn dùng Maven, thêm đoạn sau vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest stable version -->
</dependency>
```

Đối với Gradle, tương đương là:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

Khi dependency đã được giải quyết, nhập các lớp cần thiết vào file nguồn Java của bạn:

```java
import com.aspose.words.*;
```

> **Mẹo chuyên nghiệp:** Giữ các thư viện Aspose luôn cập nhật. Các bản phát hành mới thường cải thiện việc xử lý cảnh báo và bổ sung chi tiết `WarningInfo` phong phú hơn.

---

## Bước 2: Tải tài liệu Word và đăng ký Callback Cảnh báo

Bây giờ thư viện đã có trong classpath, chúng ta có thể **cách bắt phông chữ** mà engine thay thế. Điều quan trọng là `Document.setWarningCallback`, chấp nhận bất kỳ triển khai nào của `IWarningCallback`. Dưới đây là một ví dụ ngắn gọn nhưng đầy đủ, in mỗi cảnh báo thay thế phông chữ ra console.

```java
public class FontWarningDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document (replace with your actual path)
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Register the warning callback – this is where we **handle warnings**
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                // Filter only font‑substitution warnings
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 3️⃣ **Print font messages** – you could also log to a file or monitoring system
                    System.out.println("Font substitution detected: " + warningInfo.getDescription());
                }
                // Optional: handle other warning types here
            }
        });

        // Trigger the warning processing by saving or converting the document
        // For demonstration, we’ll just save to PDF (you could save to any format)
        document.save("output.pdf");
    }
}
```

### Tại sao cách này hoạt động

- **`Document.setWarningCallback`** báo cho Aspose.Words gọi code của bạn mỗi khi gặp một tình huống cần cảnh báo.
- **`WarningInfo.getWarningType()`** cho phép chúng ta phân biệt các loại (ví dụ, `FONT_SUBSTITUTION`, `DEPRECATED_FEATURE`). Bằng cách tập trung vào `FONT_SUBSTITUTION` chúng ta **xử lý phông chữ thiếu** mà không làm đầy log.
- Dòng `System.out.println` **in ra thông báo phông chữ** ngay lập tức, rất hữu ích trong quá trình phát triển hoặc khi khắc phục sự cố trong pipeline production.

---

## Bước 3: Kiểm tra Callback với một phông chữ bị thiếu

Để xác nhận callback thực sự **bắt phông chữ**, tạo một file Word sử dụng phông chữ không được cài trên máy của bạn—ví dụ, “Comic Sans MS” trên server Linux chỉ có “DejaVu Sans”. Khi chạy demo, bạn sẽ thấy đầu ra tương tự:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Nếu không thấy bất kỳ thông báo nào, hãy kiểm tra lại:

1. Tài liệu thực sự tham chiếu tới một phông chữ thiếu.
2. Đường dẫn tới `input.docx` là đúng.
3. Bạn đang dùng phiên bản mới của Aspose.Words (các bản cũ đôi khi ẩn một số cảnh báo).

---

## Bước 4: Xử lý nâng cao – Nhúng phông chữ thay thế

In ra cảnh báo là tốt, nhưng trong hệ thống production bạn có thể muốn **xử lý phông chữ thiếu** tự động. Một cách phổ biến là nhúng một phông chữ dự phòng (ví dụ, “Liberation Sans”) trước khi lưu. Dưới đây là cách mở rộng callback để thay thế phông chữ thiếu một cách lập trình:

```java
document.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo warningInfo) {
        if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            String missingFont = warningInfo.getDescription()
                .replaceAll(".*'([^']+)'.*", "$1"); // extract the font name
            System.out.println("Missing font: " + missingFont);

            // Load a fallback font from resources or a known location
            FontSettings fontSettings = document.getFontSettings();
            fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
            }});
        }
    }
});
```

**Điều gì đang diễn ra?**

- Chúng ta phân tích mô tả cảnh báo để lấy tên phông chữ bị thiếu.
- Dùng `FontSettings`, chúng ta chỉ định Aspose.Words thay thế *bất kỳ* lần xuất hiện của phông chữ đó bằng “Liberation Sans”.
- Lần tiếp theo tài liệu được render hoặc lưu, phông dự phòng sẽ được áp dụng một cách im lặng.

> **Cảnh báo:** Sử dụng quá mức việc thay thế tự động có thể che giấu các vấn đề thiết kế thực sự. Tốt nhất là ghi lại việc thay thế (như chúng ta đã **in ra thông báo phông chữ**) và kiểm tra kết quả thủ công trong QA.

---

## Bước 5: Ghi log thay vì in – Chuẩn bị cho môi trường Production

Trong pipeline CI/CD, bạn có thể không muốn xuất ra console. Thay `System.out.println` bằng một logger thích hợp (ví dụ, SLF4J). Dưới đây là một cách nhanh:

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

// ...

private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

// Inside the callback:
logger.warn("Font substitution: {}", warningInfo.getDescription());
```

Bây giờ các cảnh báo của bạn sẽ tích hợp với các công cụ tổng hợp log hiện có (ELK, Splunk, …), giúp **xử lý phông chữ thiếu** dễ dàng hơn trên nhiều job.

---

## Bước 6: Những lỗi thường gặp & Cách tránh

| Vấn đề | Nguyên nhân | Giải pháp |
|--------|-------------|-----------|
| Không có cảnh báo nào xuất hiện | Phông chữ thực tế tồn tại trên hệ thống, hoặc tài liệu sử dụng phông đã nhúng. | Xác minh tài liệu thử nghiệm thực sự tham chiếu tới một phông chữ không có. |
| Callback không được gọi | `setWarningCallback` được gọi **sau** khi tài liệu đã được tải. | Đăng ký callback **trước** bất kỳ thao tác nào có thể gây ra cảnh báo (ví dụ, trước `Document.save`). |
| Nhiều cảnh báo làm ngập log | Tài liệu lớn gây ra nhiều lần thay thế. | Thêm cơ chế throttling hoặc gom nhóm tin nhắn trước khi log. |
| Thay thế không áp dụng | `FontSettings` không được liên kết với đối tượng Document. | Đảm bảo bạn đặt `FontSettings` trên cùng một đối tượng `Document` mà bạn đang lưu. |

---

## Bước 7: Ví dụ đầy đủ, sẵn sàng chạy

Dưới đây là chương trình hoàn chỉnh, có thể sao chép và dán ngay. Bao gồm import, callback, logging và chiến lược phông dự phòng.

```java
import com.aspose.words.*;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class FontWarningDemo {

    private static final Logger logger = LoggerFactory.getLogger(FontWarningDemo.class);

    public static void main(String[] args) throws Exception {
        // Load the document – adjust the path as needed
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Register warning callback to capture and log font substitution warnings
        document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo warningInfo) {
                if (warningInfo.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Extract missing font name (optional, for advanced handling)
                    String missingFont = warningInfo.getDescription()
                        .replaceAll(".*'([^']+)'.*", "$1");

                    // Log the warning – this **prints font messages** in your log files
                    logger.warn("Font substitution detected: {}", warningInfo.getDescription());

                    // OPTIONAL: automatically substitute with a known fallback
                    FontSettings fontSettings = document.getFontSettings();
                    fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
                        getTableSubstitution().addSubstitutes(missingFont, new String[]{"Liberation Sans"});
                    }});
                }
            }
        });

        // Save to PDF (or any other format). This triggers the warning processing.
        document.save("output.pdf");
        logger.info("Document conversion completed. Check logs for any font substitution warnings.");
    }
}
```

**Đầu ra console/log dự kiến** (giả sử “Comic Sans MS” bị thiếu):

```
WARN  FontWarningDemo - Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
INFO  FontWarningDemo - Document conversion completed. Check logs for any font substitution warnings.
```

File `output.pdf` kết quả sẽ sử dụng “Liberation Sans” ở mọi chỗ mà “Comic Sans MS” được tham chiếu, nhờ vào việc thay thế tự động mà chúng ta đã thêm.

---

## Kết luận

Chúng ta vừa khám phá **cách xử lý cảnh báo** trong Aspose.Words for Java từ đầu đến cuối. Bằng cách đăng ký callback cảnh báo, lọc các cảnh báo **thay thế phông chữ**, và **in ra thông báo phông chữ**, bạn có được toàn bộ khả năng quan sát các trường hợp phông chữ thiếu. Thêm một phông dự phòng qua `FontSettings` cho phép bạn **xử lý phông chữ thiếu** mà không cần can thiệp thủ công, trong khi một framework logging phù hợp sẽ biến giải pháp thành sẵn sàng cho production.

Bước tiếp theo? Hãy thử kết hợp cách này với Aspose.PDF để kiểm tra các phông đã nhúng vẫn tồn tại sau khi chuyển đổi, hoặc khám phá các loại cảnh báo khác (ví dụ, `DEPRECATED_FEATURE`) để chuẩn bị cho tương lai. Và nếu bạn tò mò về **cách bắt phông chữ** từ một bucket lưu trữ từ xa


## Bạn nên học gì tiếp theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}