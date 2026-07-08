---
category: general
date: 2026-07-03
description: Đăng ký callback cảnh báo trong Java để phát hiện phông chữ thiếu khi
  xử lý tài liệu Word. Tìm hiểu cách xử lý cảnh báo của Aspose.Words và phát hiện
  việc thay thế phông chữ.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: vi
og_description: Đăng ký callback cảnh báo trong Java để phát hiện phông chữ thiếu.
  Hướng dẫn này cho thấy cách bắt các cảnh báo thay thế phông chữ bằng Aspose.Words.
og_title: Đăng ký callback cảnh báo trong Java – Phát hiện phông chữ thiếu
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Đăng ký callback cảnh báo trong Java – Phát hiện font thiếu một cách dễ dàng
url: /vi/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đăng ký callback cảnh báo trong Java – Dễ dàng phát hiện phông chữ thiếu

Bạn đã bao giờ tự hỏi làm thế nào để **đăng ký callback cảnh báo** để có thể **phát hiện phông chữ thiếu** khi chuyển đổi hoặc chỉnh sửa tài liệu Word chưa? Bạn không phải là người duy nhất. Các phông chữ thiếu có thể làm hỏng bố cục một cách im lặng, biến một báo cáo gọn gàng thành một mớ hỗn độn, và hầu hết các nhà phát triển thậm chí không nhận ra cho đến khi file PDF cuối cùng trông không đúng.  

Trong hướng dẫn này chúng ta sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy, cho bạn thấy chính xác cách gắn vào hệ thống cảnh báo của Aspose.Words for Java, bắt các cảnh báo thay thế phông chữ phiền phức, và ghi lại chúng hoặc phản hồi theo cách bạn cần. Không có các lối tắt mơ hồ “xem tài liệu”—chỉ có mã thuần, sao chép‑dán và lý do đằng sau mỗi dòng.

## Các điều kiện tiên quyết

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* **Java 17** (hoặc bất kỳ JDK hiện đại nào) đã được cài đặt và `JAVA_HOME` đã được thiết lập.  
* **Aspose.Words for Java** JAR (tải về từ trang chính thức hoặc lấy qua Maven).  
* Một tệp `.docx` mẫu tham chiếu tới một phông chữ **không** được cài đặt trên máy của bạn—điều này sẽ kích hoạt cảnh báo.  
* IDE yêu thích của bạn hoặc một trình soạn thảo văn bản đơn giản và các công cụ xây dựng dòng lệnh.

Đó là tất cả. Không cần framework bổ sung, không cần dịch vụ bên ngoài. Sẵn sàng chưa? Hãy bắt đầu.

## Bước 1: Thiết lập dự án và thêm Aspose.Words

Nếu bạn dùng Maven, thêm phụ thuộc sau vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Đối với Gradle, đặt đoạn này vào `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Nếu bạn thích cách thủ công, chỉ cần đặt `aspose-words-24.10.jar` vào classpath của bạn.  
**Mẹo chuyên nghiệp:** giữ JAR cạnh thư mục `src`; điều này sẽ đơn giản hoá lệnh `javac` sau này.

## Bước 2: Tải tài liệu có thể chứa phông chữ thiếu

Điều đầu tiên bạn làm là tạo một đối tượng `Document` trỏ tới tệp nguồn. Bước này đơn giản, nhưng cũng là nơi thư viện quét tệp và *có thể* phát hiện các phông chữ thiếu.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Ở đây, `Document` là điểm vào cho mọi thao tác của Aspose.Words. Khi hàm khởi tạo chạy, thư viện sẽ phân tích XML của tài liệu, giải quyết phông chữ, và nếu có phông chữ nào không khả dụng, nó sẽ *đặt vào hàng* một cảnh báo mà chúng ta có thể bắt sau này.

## Bước 3: Đăng ký callback cảnh báo để bắt các cảnh báo thay thế phông chữ

Bây giờ là phần trọng tâm: **đăng ký callback cảnh báo**. Aspose.Words cho phép bạn cắm một triển khai của giao diện `IWarningCallback`. Mỗi khi engine gặp một tình huống đáng chú ý—như một phông chữ thiếu—nó sẽ gọi phương thức `warning` của bạn.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Tại sao điều này quan trọng

* **Tầm nhìn:** Không có callback, việc thay thế diễn ra im lặng, và bạn có thể phát hành tài liệu với giao diện sai.  
* **Tự động hoá:** Trong các pipeline batch, bạn có thể ghi lại mọi sự cố phông chữ thiếu và sau đó đưa danh sách này vào script cài đặt phông chữ.  
* **Tuân thủ:** Một số ngành (ví dụ, pháp lý) yêu cầu bằng chứng rằng các phông chữ gốc đã được sử dụng hoặc đã được thay thế đúng cách.

Lưu ý chúng ta lọc theo `WarningType.FONT_SUBSTITUTION`. Aspose.Words phát ra nhiều loại cảnh báo—tràn bố cục, tính năng lỗi thời, v.v.—nhưng chúng ta chỉ quan tâm tới những cảnh báo cho biết phông chữ đã thiếu. Điều này giữ cho console sạch sẽ và tập trung vào mục tiêu **phát hiện phông chữ thiếu**.

## Bước 4: Lưu tài liệu và để callback được kích hoạt

Khi bạn cuối cùng gọi `save`, engine hoàn tất mọi việc tải lười và kích hoạt callback cảnh báo cho mỗi phông chữ thiếu mà nó phát hiện trong quá trình lưu.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Đầu ra console dự kiến

Giả sử `input.docx` tham chiếu tới phông chữ *“Comic Sans MS”* mà không được cài đặt, bạn sẽ thấy thứ gì đó như:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Nếu tài liệu nguồn chỉ chứa các phông chữ đã được cài đặt, dòng cảnh báo sẽ không xuất hiện—nghĩa là **phát hiện phông chữ thiếu** đã thành công một cách im lặng.

![đầu ra đăng ký callback cảnh báo hiển thị phát hiện phông chữ thiếu](register-warning-callback-output.png)

*Image alt text: đầu ra đăng ký callback cảnh báo hiển thị phát hiện phông chữ thiếu*

## Bước 5: Xử lý các trường hợp đặc biệt và mẹo thực tiễn

### Nhiều phông chữ thiếu

Nếu một tài liệu tham chiếu tới nhiều phông chữ không khả dụng, callback sẽ được kích hoạt một lần cho mỗi phông chữ. Bạn có thể gom các tin nhắn lại thành một danh sách nếu cần báo cáo tổng hợp sau này.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Kiểm soát hành vi thay thế

Đôi khi bạn *có* muốn buộc một phông chữ dự phòng cụ thể. Hãy sử dụng `FontSettings` trước khi tải tài liệu:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Bây giờ callback vẫn sẽ được kích hoạt, nhưng bạn biết chính xác phông chữ nào sẽ được dùng.

### Cân nhắc về hiệu năng

Đăng ký callback cảnh báo chỉ tạo ra một chi phí rất nhỏ—chỉ vài nan giây cho mỗi cảnh báo. Trong các dịch vụ có lưu lượng cao (ví dụ, chuyển đổi hàng ngàn tài liệu mỗi giờ) ảnh hưởng là không đáng kể. Tuy nhiên, nếu bạn xử lý hàng triệu tài liệu, hãy cân nhắc tắt cảnh báo sau khi đã xác nhận bộ phông chữ đã đầy đủ:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Ghi chú đa nền tảng

Callback hoạt động giống hệt trên Windows, macOS và Linux. Điểm khác nhau duy nhất là tập hợp phông chữ có sẵn trên mỗi hệ điều hành. Nếu bạn chạy cùng một công việc trên nhiều agent, có thể sẽ thấy các thông báo thay thế khác nhau. Để giữ kết quả quyết định, hãy cung cấp một **thư mục phông chữ tùy chỉnh** và chỉ định cho Aspose.Words bằng `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Ví dụ đầy đủ, có thể chạy ngay

Dưới đây là toàn bộ lớp Java bạn có thể sao chép‑dán vào `src/main/java/FontWarningDemo.java`. Nó bao gồm tất cả các import, xử lý lỗi, và chú thích cần thiết để chạy ngay lập tức.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Biên dịch và chạy:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Bạn sẽ thấy các dòng cảnh báo (nếu có) tiếp theo là thông báo thành công.

## Kết luận

Bạn vừa học được **cách đăng ký callback cảnh báo** trong Java để **phát hiện phông chữ thiếu** khi làm việc với Aspose.Words. Bằng cách gắn vào hệ thống cảnh báo của thư viện, bạn có được tầm nhìn đầy đủ về các sự kiện thay thế phông chữ, có thể ghi lại chúng để tuân thủ, và thậm chí thay thế phông chữ một cách lập trình nếu cần.  

Từ đây bạn có thể khám phá:

* **Phát hiện phông chữ thiếu** trên một loạt tệp bằng vòng lặp hoặc stream song song.  
* Tích hợp callback với một framework ghi log (SLF4J, Log4j) để có báo cáo mức sản xuất.  
* Sử dụng `FontSettings` để áp dụng bộ phông chữ doanh nghiệp và tránh các fallback không mong muốn.

Hãy thử ngay—đổi tài liệu đầu vào, thử các kịch bản phông chữ thiếu khác nhau, và xem callback hoạt động như thế nào. Nếu gặp bất kỳ vấn đề nào, hãy để lại bình luận bên dưới; chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong bài viết này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Custom Savings](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}