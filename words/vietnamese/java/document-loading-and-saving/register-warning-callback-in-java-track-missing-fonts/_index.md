---
category: general
date: 2026-05-30
description: Đăng ký callback cảnh báo trong Java để theo dõi các phông chữ thiếu
  và tùy chỉnh việc tải tài liệu với Aspose.Words. Tìm hiểu giải pháp đầy đủ từng
  bước.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: vi
og_description: Đăng ký callback cảnh báo trong Java để theo dõi phông chữ thiếu và
  tùy chỉnh quá trình tải tài liệu. Hướng dẫn đầy đủ kèm mã và giải thích.
og_title: Đăng ký callback cảnh báo trong Java – Theo dõi phông chữ bị thiếu
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Đăng ký callback cảnh báo trong Java – Theo dõi phông chữ thiếu
url: /vi/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đăng ký callback cảnh báo trong Java – Theo dõi phông chữ thiếu

Bạn đã bao giờ tự hỏi làm thế nào để **theo dõi phông chữ thiếu** khi tải một tài liệu Word bằng Aspose.Words for Java chưa? Có thể bạn đã thấy những sự thay thế phông chữ im lặng và tự hỏi, “Điều gì đã xảy ra với bố cục của tôi?” Tin tốt là bạn không cần phải đoán. Bằng cách **đăng ký một callback cảnh báo**, bạn có thể ghi lại mọi sự kiện thay thế phông chữ ngay khi tài liệu được đọc, và bạn cũng có thể **tùy chỉnh việc tải tài liệu** để phù hợp với quy trình của mình.

> **Bạn sẽ nhận được:**  
> • Một chương trình Java hoàn chỉnh sử dụng Aspose.Words  
> • Giải thích chi tiết từng dòng code  
> • Mẹo xử lý các trường hợp đặc biệt như tệp được mã hóa hoặc lô lớn  
> • Một kiểm tra nhanh bạn có thể chạy trên bất kỳ tệp `.docx` nào

## Các yêu cầu trước

- **Java 17** (hoặc bất kỳ JDK nào mới) đã được cài đặt và `JAVA_HOME` được thiết lập.  
- **Aspose.Words for Java** JAR trên classpath của bạn. Bạn có thể tải phiên bản mới nhất từ kho Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Một tài liệu Word mẫu (`input.docx`) mà bạn nghi ngờ chứa các phông chữ không được cài trên máy của bạn.  
- Một IDE hoặc công cụ xây dựng dòng lệnh (Maven/Gradle) mà bạn quen thuộc.

Đó là tất cả. Không cần phông chữ bổ sung, không cần dịch vụ bổ sung—chỉ cần Java thuần và Aspose.Words.

## Tại sao phải đăng ký callback cảnh báo?

Hãy nghĩ về **callback cảnh báo** như một camera an ninh cho quá trình tải tài liệu của bạn. Khi Aspose.Words gặp một glyph thiếu, nó không ném ra ngoại lệ; nó lặng lẽ thay thế bằng một phông chữ dự phòng. Sự thay thế im lặng này có thể làm hỏng bố cục, đặc biệt trong các PDF hoặc hoá đơn quan trọng về thương hiệu. Bằng cách đăng ký một callback, bạn:

1. **Nhận thông tin theo thời gian thực** – mọi cảnh báo `FONT_SUBSTITUTION` được gửi ngay lập tức.  
2. **Ghi log hoặc phản hồi** – bạn có thể ghi log vào tệp, đưa ra cảnh báo, hoặc thậm chí thay thế phông chữ bằng chương trình.  
3. **Duy trì đầu ra sạch sẽ** – biết được phông chữ nào thiếu giúp bạn sửa tài liệu nguồn trước khi xuất bản.

Nói ngắn gọn, callback biến một vấn đề ẩn thành vấn đề hiển thị, làm cho quy trình tài liệu của bạn đáng tin cậy hơn nhiều.

## Bước 1 – Tạo `LoadOptions` để tùy chỉnh cách tải tài liệu

Điều đầu tiên chúng ta làm là khởi tạo `LoadOptions`. Đối tượng này là cổng vào cho mọi tùy chỉnh thời gian tải mà bạn có thể cần, từ xử lý mật khẩu đến tính năng **đăng ký callback cảnh báo** của chúng ta.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Tại sao không chỉ gọi `new Document("file.docx")`? Bởi vì nếu không có `LoadOptions` bạn sẽ mất cơ hội can thiệp vào các sự kiện tải. `LoadOptions` là nơi duy nhất Aspose.Words cho phép bạn **tùy chỉnh việc tải tài liệu**.

## Bước 2 – Đăng ký callback cảnh báo để theo dõi phông chữ thiếu

Bây giờ là phần trọng tâm: chúng ta **đăng ký một callback cảnh báo** thực hiện giao diện `IWarningCallback`. Trong phương thức `warning` chúng ta lọc ra `WarningType.FONT_SUBSTITUTION` và in ra một thông báo hữu ích.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Một vài lưu ý:

- **Tại sao lại là `IWarningCallback`?** Đó là giao diện mà Aspose.Words sử dụng cho tất cả các loại cảnh báo, cung cấp cho bạn một điểm vào duy nhất cho nhiều vấn đề có thể xảy ra.  
- **Lọc là rất quan trọng** – nếu không có kiểm tra `if` bạn sẽ thấy các cảnh báo về hình ảnh thiếu, tính năng đã lỗi thời, v.v., làm lộn xộn log của bạn.  
- **An toàn đa luồng** – callback chạy trên cùng một luồng tải tài liệu, vì vậy bạn có thể an toàn cập nhật các cấu trúc chia sẻ nếu cần tổng hợp kết quả sau này.

Đoạn mã này **đăng ký callback cảnh báo**, và từ thời điểm này trở đi mọi sự kiện phông chữ thiếu sẽ được in ra `stdout`. Đây là cốt lõi của **theo dõi phông chữ thiếu**.

## Bước 3 – Tải tài liệu bằng `LoadOptions` đã cấu hình

Với callback đã sẵn sàng, chúng ta cuối cùng tải tệp. Nếu tài liệu tham chiếu một phông chữ mà bạn không có, callback sẽ được kích hoạt trước khi đối tượng `Document` được tạo hoàn toàn.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế trên máy của bạn. Hàm khởi tạo `Document` đọc tệp, áp dụng bất kỳ mật khẩu nào (nếu bạn đã đặt trong `loadOptions`), và kích hoạt callback cảnh báo cho mỗi phông chữ thiếu. Bạn sẽ thấy đầu ra như sau:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Dòng này chứng minh bạn đã **theo dõi phông chữ thiếu** thành công.

## Bước 4 – Tiếp tục xử lý tài liệu (tùy chọn)

Ở giai đoạn này bạn có thể thao tác tài liệu theo bất kỳ cách nào—thay thế văn bản, chèn hình ảnh, hoặc thậm chí thay đổi phông chữ đã được thay thế bằng chương trình. Callback đã cung cấp cho bạn danh sách các phông chữ gây vấn đề, vì vậy bạn có thể, ví dụ, nhúng một phông chữ dự phòng:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Bạn có thể bỏ qua khối này nếu chỉ cần **theo dõi phông chữ thiếu**. Điều quan trọng là bạn đã có thông tin cần thiết để đưa ra quyết định sáng suốt.

## Bước 5 – Lưu tài liệu đã xử lý

Cuối cùng, lưu lại tài liệu. Bạn có thể ghi đè lên bản gốc, lưu vào vị trí mới, hoặc xuất ra PDF—tất cả mà không mất dữ liệu cảnh báo bạn đã thu thập trước đó.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Chạy toàn bộ lớp sẽ tạo ra đầu ra console cho mỗi phông chữ thiếu và một tệp mới có tên `processed.docx` trong cùng thư mục.

## Ví dụ làm việc hoàn chỉnh

Dưới đây là lớp Java đầy đủ mà bạn có thể sao chép‑dán vào IDE. Nó bao gồm mọi thứ chúng ta đã thảo luận, cộng thêm một hàm `main` nhỏ.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Kết quả mong đợi

Khi bạn chạy chương trình với một tài liệu sử dụng phông chữ không được cài trên hệ thống, bạn sẽ thấy thứ gì đó như:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Nếu tài liệu **không có phông chữ thiếu**, console sẽ im lặng cho đến dòng cuối cùng “Document saved successfully.” — chính xác những gì bạn mong đợi từ một **đăng ký callback cảnh báo** hoạt động tốt.

## Mẹo chuyên nghiệp & Những cạm bẫy thường gặp

- **Nhiều callback?** Aspose.Words chỉ cho phép một trình xử lý cảnh báo. Nếu bạn cần ghi log cả vào tệp và console, hãy triển khai một callback tổng hợp để chuyển cảnh báo tới nhiều đích.  
- **Lô lớn** – khi xử lý hàng trăm tệp, hãy cân nhắc tái sử dụng một thể hiện `LoadOptions` duy nhất; tạo mới cho mỗi tệp sẽ gây tốn tài nguyên không cần thiết.  
- **Tài liệu được mã hóa** – đặt mật khẩu trên `LoadOptions` trước khi tải, nếu không bạn sẽ nhận được `IncorrectPasswordException` trước khi callback được kích hoạt.  
- **Hiệu năng** – callback chạy đồng bộ. Nếu bạn ghi log tới dịch vụ từ xa, hãy đệm các tin nhắn và flush chúng sau khi tải hoàn tất để tránh tắc nghẽn I/O.  
- **Thay thế phông chữ** – bạn cũng có thể cung cấp một bộ sưu tập `FontSource` tùy chỉnh nếu có các phông chữ độc quyền mà bạn muốn Aspose.Words xem xét trước khi quay lại phông chữ hệ thống.

## Kết luận

Bạn vừa học cách **đăng ký callback cảnh báo** trong Java, hiệu quả **theo dõi phông chữ thiếu**, và **tùy chỉnh việc tải tài liệu** với Aspose.Words. Giải pháp tự chứa, chạy bằng một phương thức `main` duy nhất, và cung cấp cho bạn khả năng quan sát ngay lập tức mọi sự thay thế phông chữ mà nếu không sẽ bị bỏ qua.

Bước tiếp theo? Hãy mở rộng callback để ghi cảnh báo vào tệp CSV cho mục đích kiểm toán, hoặc kết hợp nó với bộ xử lý lô tự động nhúng các phông chữ thiếu. Bạn cũng có thể khám phá các loại cảnh báo khác như `IMAGE_SUBSTITUTION` hoặc `DEPRECATED_FEATURE`—cùng một mẫu áp dụng.

Happy coding, and may your documents always render exactly as you intended!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")

## Bạn nên học gì tiếp theo?

- [Callback Cảnh báo trong Tài liệu Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Tùy chỉnh Màu Chủ đề & Phông chữ trong Aspose.Words Java: Hướng dẫn toàn diện](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Theo dõi Thay đổi trong Tài liệu Word bằng Aspose.Words Java: Hướng dẫn đầy đủ về Phiên bản Tài liệu](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}