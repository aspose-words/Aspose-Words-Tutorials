---
category: general
date: 2026-07-06
description: Tạo DocumentConfig trong Java để theo dõi các phông chữ thiếu bằng Aspose.Words
  – hướng dẫn đầy đủ, từng bước cho các nhà phát triển.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: vi
og_description: Tạo DocumentConfig trong Java để theo dõi các phông chữ thiếu với
  Aspose.Words. Tìm hiểu quy trình đầy đủ, từ cài đặt đến xử lý cảnh báo.
og_title: Tạo DocumentConfig trong Java – Theo dõi phông chữ bị thiếu
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Tạo DocumentConfig trong Java – Theo dõi phông chữ thiếu với Aspose.Words
url: /vi/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo DocumentConfig trong Java – Theo dõi các phông chữ thiếu với Aspose.Words

**Create DocumentConfig trong Java** để giám sát các cảnh báo thay thế phông chữ khi tải tài liệu Word. Bạn đã bao giờ tự hỏi tại sao một số ký tự trông lạ sau khi mở một tệp DOCX chưa? Rất có thể phông chữ gốc không có trên máy, và Aspose.Words sẽ tự động thay thế một cách im lặng. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách **theo dõi các phông chữ thiếu** để bạn không bao giờ bị bất ngờ bởi một glyph lạc lõng nữa.

Chúng tôi sẽ hướng dẫn toàn bộ những gì bạn cần: cấu hình Maven/Gradle, đoạn mã tạo một `DocumentConfig`, một `IWarningCallback` tùy chỉnh chỉ lọc các cảnh báo thay thế phông chữ, và cách nhanh chóng ghi lại các tin nhắn đó. Khi kết thúc, bạn sẽ có một ví dụ có thể chạy được, in ra mọi cảnh báo phông chữ thiếu lên console (hoặc tệp, nếu bạn muốn).

---

## Những gì bạn sẽ học

- Tại sao `DocumentConfig` là nơi thích hợp để chặn các sự kiện thay thế phông chữ.  
- Cách **theo dõi các phông chữ thiếu** mà không làm bận mắt log của bạn với các cảnh báo không liên quan.  
- Một chương trình Java hoàn chỉnh, sẵn sàng copy‑paste, minh họa kỹ thuật này.  
- Mẹo mở rộng giải pháp—ví dụ, ghi cảnh báo vào cơ sở dữ liệu hoặc gửi thông báo email.

### Yêu cầu trước

| Yêu cầu | Lý do |
|-------------|--------|
| Java 8 hoặc mới hơn | Aspose.Words for Java hỗ trợ JDK 8+. |
| Thư viện Aspose.Words for Java (phiên bản mới nhất) | Cung cấp `DocumentConfig`, `IWarningCallback`, v.v. |
| Một IDE hoặc công cụ xây dựng (IntelliJ, Eclipse, Maven/Gradle) | Để biên dịch và chạy mẫu. |
| Tệp DOCX tham chiếu đến các phông chữ bạn chưa cài đặt | Để xem cảnh báo hoạt động. |

Nếu bạn đã có dự án, chỉ cần thêm phụ thuộc Aspose và bạn đã sẵn sàng.

---

## Bước 1: Thêm Aspose.Words vào dự án của bạn

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Mẹo:** Phiên bản dùng thử miễn phí hoạt động hoàn hảo cho việc thử nghiệm, nhưng nhớ áp dụng giấy phép cho môi trường production để loại bỏ watermark đánh giá.

---

## Bước 2: Tạo DocumentConfig và Đăng ký Callback Cảnh báo

Trọng tâm của giải pháp nằm trong đoạn mã này. Chúng tôi **tạo một DocumentConfig**, gắn một `IWarningCallback` tùy chỉnh, và chỉ định nó **theo dõi các phông chữ thiếu**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Tại sao cách này hoạt động:** Khi Aspose.Words phân tích một tài liệu, nó phát ra các đối tượng `WarningInfo` cho bất kỳ bất thường nào. Bằng cách cung cấp một callback, bạn chặn các cảnh báo đó *trước* khi chúng biến mất. Điều kiện `if` đảm bảo chúng ta chỉ **theo dõi các phông chữ thiếu**, bỏ qua các cảnh báo khác như thẻ lỗi thời hoặc tính năng không được hỗ trợ.

---

## Bước 3: Chạy ví dụ và quan sát đầu ra

Đặt một tệp DOCX tham chiếu đến phông chữ bạn không có (ví dụ, “Comic Sans MS” trên máy Linux). Thực thi chương trình:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Bạn sẽ thấy một cái gì đó tương tự như:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Mỗi dòng tương ứng với một phông chữ thiếu mà Aspose tự động thay thế. Nếu không có phông chữ nào thiếu, chương trình sẽ im lặng—đúng như bạn muốn để có log sạch sẽ.

---

## Bước 4: Lưu danh sách phông chữ thiếu (Tùy chọn)

In ra console tiện lợi cho demo, nhưng trong dịch vụ thực tế bạn có thể muốn lưu dữ liệu. Dưới đây là cách nhanh để ghi các cảnh báo vào tệp văn bản.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Bây giờ mỗi sự kiện phông chữ thiếu sẽ thêm một dòng vào `missing-fonts.log`. Bạn có thể sau này phân tích tệp này, đưa vào bảng điều khiển giám sát, hoặc thậm chí kích hoạt cảnh báo nếu một phông chữ quan trọng biến mất khỏi máy chủ của bạn.

---

## Bước 5: Những lỗi thường gặp và cách tránh chúng

| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|-------------|--------------------|----------------|
| Không có cảnh báo xuất hiện mặc dù DOCX sử dụng phông chữ không biết | Callback chưa được đăng ký hoặc `setWarningCallback` được gọi sau khi tải tài liệu | Đảm bảo `config.setWarningCallback(...)` được thực thi **trước** khi tạo instance `Document`. |
| Ứng dụng bị crash với `NullPointerException` | `info.getDescription()` trả về `null` cho một số loại cảnh báo hiếm | Kiểm tra null: `String desc = info.getDescription(); if (desc != null) …` |
| Quá nhiều cảnh báo không liên quan tràn ngập console | Callback chỉ lọc `FONT_SUBSTITUTION`? | Kiểm tra lại điều kiện `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Hiệu năng chậm lại khi xử lý lô lớn | Ghi vào tệp đồng bộ cho mỗi cảnh báo | Ghi theo batch hoặc sử dụng `BufferedWriter` để giảm tải I/O. |

---

## Bước 6: Mở rộng giải pháp – Từ Console tới Doanh nghiệp

- **Ghi log vào cơ sở dữ liệu:** Thay thế `FileWriter` bằng một câu lệnh INSERT JDBC; lưu `documentName`, `missingFont`, và `timestamp`.  
- **Cảnh báo email:** Kết nối với JavaMail; gửi bản tóm tắt sau khi xử lý một lô tài liệu.  
- **Logic thay thế tùy chỉnh:** Thay vì để Aspose chọn phông chữ dự phòng, bạn có thể tải bộ sưu tập phông chữ cục bộ qua `FontSettings.setFontsFolder()` và tải lại nếu xảy ra thay thế.

Các mở rộng này giữ nguyên ý tưởng cốt lõi—**tạo documentconfig** và **theo dõi các phông chữ thiếu**—trong khi mở rộng cho nhu cầu production.

---

## Kết luận

Bạn giờ đã có một mẫu vững chắc, sẵn sàng copy‑and‑paste để **tạo DocumentConfig** trong Java và sử dụng nó để **theo dõi các phông chữ thiếu** với Aspose.Words. Cách tiếp cận này nhẹ, chỉ cần vài dòng mã, và cho bạn kiểm soát đầy đủ cách xử lý các cảnh báo thay thế phông chữ. Dù bạn đang xây dựng dịch vụ chuyển đổi tài liệu, công cụ tạo báo cáo tự động, hay công cụ kiểm tra tuân thủ, việc biết chính xác những phông chữ nào thiếu có thể tiết kiệm hàng giờ gỡ lỗi.

Bước tiếp theo? Hãy thử thay đổi đầu ra console thành log JSON có cấu trúc, hoặc tích hợp callback vào microservice Spring Boot xử lý tải lên thời gian thực. Và nếu bạn gặp bất kỳ trường hợp đặc biệt nào—ví dụ, một phông chữ OpenType tùy chỉnh mà Aspose không thể phân tích—hãy để lại bình luận bên dưới; chúng tôi sẽ cùng bạn khắc phục.

Chúc lập trình vui vẻ, và hy vọng các PDF của bạn luôn hiển thị đúng phông chữ mong muốn!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Sử dụng phông chữ trong Aspose.Words cho Java](/words/english/java/using-document-elements/using-fonts/)
- [Tùy chỉnh màu sắc chủ đề & phông chữ trong Aspose.Words Java: Hướng dẫn toàn diện](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Cách tạo tài liệu PDF với Aspose.Words cho Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}