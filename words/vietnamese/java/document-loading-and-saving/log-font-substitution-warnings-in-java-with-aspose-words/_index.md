---
category: general
date: 2026-06-17
description: Ghi lại cảnh báo thay thế phông chữ trong Java bằng Aspose.Words – phát
  hiện các phông chữ thiếu khi tải tài liệu và giữ cho đầu ra của bạn nhất quán.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: vi
og_description: Ghi lại cảnh báo thay thế phông chữ trong Java với Aspose.Words. Tìm
  hiểu cách bắt các thông báo thiếu phông chữ khi tải tài liệu và giữ PDF của bạn
  luôn nguyên vẹn.
og_title: Ghi lại các cảnh báo thay thế phông chữ trong Java – Hướng dẫn toàn diện
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Ghi lại các cảnh báo thay thế phông chữ trong Java với Aspose.Words
url: /vi/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ghi lại Cảnh báo Thay thế Phông chữ trong Java – Hướng dẫn đầy đủ

Bạn đã bao giờ thắc mắc cách **ghi lại cảnh báo thay thế phông chữ** khi một tài liệu Word kéo một phông chữ mà bạn không có trên máy chủ chưa? Bạn không phải là người duy nhất bối rối vì các phông chữ thiếu bị thay thế một cách im lặng. Tin tốt là gì? Aspose.Words for Java cung cấp cho bạn một cách sạch sẽ để bắt những lần thay thế ngay khi tài liệu được tải.

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ thực tế cho thấy cách đăng ký một callback cảnh báo, lọc các cảnh báo thay thế phông chữ, và ghi chúng ra console (hoặc bất kỳ logger nào bạn muốn). Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng để chèn vào bất kỳ dự án Java nào sử dụng **Aspose.Words Java**.

## Những gì bạn sẽ học

- Cách cấu hình **LoadOptions** để bắt các cảnh báo.
- Cách triển khai **IWarningCallback** chỉ phản hồi các sự kiện **font substitution**.
- Cách tải tài liệu một cách an toàn đồng thời giữ một bản ghi kiểm tra rõ ràng về các phông chữ thiếu.
- Mẹo mở rộng giải pháp sang log dựa trên tệp hoặc hệ thống giám sát.

### Yêu cầu trước

- Java 8 hoặc mới hơn (mã cũng hoạt động với Java 11+).
- Thư viện Aspose.Words for Java (phiên bản 23.10 hoặc mới hơn được khuyến nghị).
- Một tệp mẫu `.docx` tham chiếu đến phông chữ không được cài đặt trên máy của bạn (ví dụ, `MissingFont.docx`).

Không cần bất kỳ framework bổ sung nào—chỉ cần Java thuần và các file Aspose.JAR.

---

## Bước 1: Cấu hình LoadOptions cho Aspose.Words Java

Trước khi bạn có thể chặn bất kỳ cảnh báo nào, bạn cần một thể hiện **LoadOptions**. Đối tượng này cho Aspose.Words biết cách hoạt động khi phân tích tệp đến.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Tại sao bước này lại quan trọng? Nếu không có đối tượng `LoadOptions`, thư viện sẽ im lặng thay thế các phông chữ thiếu và bạn sẽ không thấy dấu vết nào. Bằng cách tạo rõ ràng một đối tượng, bạn mở ra cánh cửa cho một **warning callback** tùy chỉnh có thể ghi lại chính xác những gì bạn quan tâm.

> **Mẹo chuyên nghiệp:** Nếu bạn đang tải nhiều tài liệu trong một batch, hãy tái sử dụng một thể hiện `LoadOptions` duy nhất để tránh việc tạo đối tượng không cần thiết.

## Bước 2: Triển khai Warning Callback cho Font Substitution

Aspose.Words cung cấp giao diện `IWarningCallback`. Việc triển khai nó cho phép bạn quyết định hành động khi engine phát sinh một `WarningInfo`. Trong trường hợp của chúng ta, chúng ta chỉ muốn phản hồi `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Một vài điểm cần lưu ý:

1. **Filtering** – Câu lệnh `if` đảm bảo chúng ta bỏ qua các cảnh báo không liên quan (như vấn đề bố cục) và giữ log gọn gàng.
2. **Thread safety** – Callback chạy trên cùng một luồng tải tài liệu, vì vậy bạn không cần đồng bộ thêm cho việc xuất ra console đơn giản. Nếu bạn ghi vào một logger chung, hãy chắc chắn nó an toàn với đa luồng.
3. **Extensibility** – Muốn ghi vào file? Thay `System.out.println` bằng `java.util.logging.Logger` hoặc một framework logging của bên thứ ba.

## Bước 3: Tải tài liệu bằng các tùy chọn đã cấu hình

Bây giờ callback đã sẵn sàng, hãy tải tệp Word của bạn. Ngay khi Aspose.Words phân tích tài liệu, bất kỳ phông chữ nào thiếu sẽ kích hoạt callback đã định nghĩa ở trên.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Nếu tệp nguồn tham chiếu một phông chữ chưa được cài đặt, bạn sẽ thấy đầu ra tương tự như:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Dòng đó là **log font substitution warnings** mà bạn đang tìm kiếm. Bây giờ bạn có thể hành động dựa trên nó—có thể cảnh báo người dùng, chuyển sang stylesheet dự phòng, hoặc chỉ đơn giản lưu lại bản ghi để tuân thủ.

## Bước 4: Tiếp tục xử lý bình thường

Sau khi tải, tài liệu hoạt động giống như bất kỳ đối tượng `Document` nào khác. Bạn có thể tự do kiểm tra các section, trích xuất văn bản, hoặc chuyển đổi sang PDF. Việc ghi log cảnh báo diễn ra tự động trong bước tải, vì vậy bạn không cần thêm mã.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

Console bây giờ sẽ hiển thị cả cảnh báo thay thế phông chữ (nếu có) **và** số lượng section, xác nhận rằng tài liệu hoạt động đầy đủ.

## Mẹo nâng cao & Trường hợp đặc biệt

### Ghi log vào file thay vì console

Nếu bạn muốn một log kéo dài, thay thế lời gọi `System.out.println` bằng một `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Hãy nhớ xử lý `IOException` một cách thích hợp trong mã production.

### Ghi nhận nhiều tài liệu trong vòng lặp

Khi xử lý một thư mục các tài liệu, bạn có thể tái sử dụng cùng một callback:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Vì callback được gắn vào `loadOptions`, mỗi vòng lặp sẽ tự động ghi lại bất kỳ sự kiện thay thế phông chữ nào.

### Xử lý phông chữ nhúng

Aspose.Words có thể nhúng các phông chữ thiếu nếu bạn bật tính năng này:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Ngay cả khi bật nhúng, callback cảnh báo vẫn được kích hoạt, cung cấp cho bạn khả năng nhìn thấy những gì đã được thay thế.

## Ví dụ Hoạt động đầy đủ

Dưới đây là chương trình hoàn chỉnh, sẵn sàng chạy. Sao chép nó vào một lớp có tên `FontSubstitutionDiagnostics.java`, điều chỉnh đường dẫn tệp và thực thi.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Kết quả mong đợi** (giả sử tài liệu nguồn tham chiếu một phông chữ thiếu):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Cả console và `font_substitution_log.txt` sẽ chứa cảnh báo, cung cấp cho bạn một bản ghi kiểm tra đáng tin cậy.

## Kết luận

Chúng tôi vừa cho bạn thấy cách **ghi lại cảnh báo thay thế phông chữ** trong Java bằng Aspose.Words. Bằng cách cấu hình `LoadOptions`, kết nối một `IWarningCallback`, và tải tài liệu, bạn sẽ có đầy đủ khả năng quan sát bất kỳ sự kiện phông chữ thiếu nào mà nếu không sẽ không được phát hiện. Từ đây bạn có thể:

- Chuyển các cảnh báo tới dịch vụ logging trung tâm.
- Kích hoạt cảnh báo cho các pipeline kiểm soát chất lượng.
- Kết hợp kỹ thuật này với các chiến lược **document loading** khác, như chuyển đổi PDF hoặc mail‑merge.

Hãy thoải mái thử nghiệm—thay logger console bằng SLF4J, thêm dấu thời gian, hoặc thậm chí đẩy cảnh báo lên bảng điều khiển giám sát. Mẫu cốt lõi vẫn giữ nguyên, và giờ bạn có nền tảng vững chắc cho việc xử lý phông chữ mạnh mẽ trong bất kỳ quy trình công việc tài liệu dựa trên Java nào.

Có cách tiếp cận nào bạn muốn chia sẻ? Có thể bạn đã tích hợp điều này với Spring Boot hoặc một cloud function. Hãy để lại bình luận bên dưới, và chúng ta cùng tiếp tục thảo luận. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Ghi lại Cảnh báo Thay thế Phông chữ trong Java với Aspose.Words – Hướng dẫn đầy đủ](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Sử dụng Document Options và Settings trong Aspose.Words cho Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Bật Cảnh báo Thay thế Phông chữ trong Aspose.Words – Hướng dẫn đầy đủ](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}