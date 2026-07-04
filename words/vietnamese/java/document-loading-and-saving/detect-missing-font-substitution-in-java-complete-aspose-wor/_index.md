---
category: general
date: 2026-06-05
description: Phát hiện việc thay thế phông chữ bị thiếu trong Java bằng Aspose.Words.
  Tìm hiểu cách cấu hình LoadOptions, FontSettings và các callback cảnh báo để xử
  lý tài liệu một cách đáng tin cậy.
draft: false
keywords:
- detect missing font substitution
- Java Aspose.Words
- LoadOptions configuration
- FontSettings warning callback
- document loading Java
language: vi
og_description: Phát hiện việc thay thế phông chữ bị thiếu trong Java với Aspose.Words.
  Hướng dẫn này trình bày chi tiết cách thiết lập LoadOptions, FontSettings và một
  callback cảnh báo để bắt các phông chữ bị thiếu.
og_title: phát hiện việc thay thế phông chữ bị thiếu trong Java – Hướng dẫn đầy đủ
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  headline: detect missing font substitution in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: detect missing font substitution in Java using Aspose.Words. Learn
    how to configure LoadOptions, FontSettings, and warning callbacks for reliable
    document processing.
  name: detect missing font substitution in Java – Complete Aspose.Words Guide
  steps:
  - name: 4.1 Quick verification
    text: Run the program from your IDE or via `java -cp .;aspose-words-23.12.jar
      MissingFontDetector`. If the document references a font you don’t have, you’ll
      see the warning message printed. If the console stays silent, either the font
      exists on your machine or the document doesn’t request any missing font
  - name: 4.2 Logging instead of `System.out`
    text: 'In production code you probably want a logger:'
  - name: 4.3 Handling other warning types
    text: 'The callback receives *all* warnings, not just font issues. If you’d like
      to keep an eye on other problems (e.g., `UNKNOWN_STYLE`), add extra `if` branches.
      Here’s a quick example:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font handling
title: Phát hiện việc thay thế phông chữ bị thiếu trong Java – Hướng dẫn đầy đủ Aspose.Words
url: /vi/java/document-loading-and-saving/detect-missing-font-substitution-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# phát hiện việc thay thế phông chữ bị thiếu trong Java – Hướng dẫn đầy đủ Aspose.Words

Bạn đã bao giờ tự hỏi cách **phát hiện việc thay thế phông chữ bị thiếu** khi tải một tài liệu Word trong Java chưa? Bạn không phải là người duy nhất. Các phông chữ thiếu có thể âm thầm làm hỏng các tệp PDF hoặc các trang đã render, và việc phát hiện chúng sớm sẽ tiết kiệm hàng giờ gỡ lỗi. Trong hướng dẫn này, chúng tôi sẽ đi qua một giải pháp thực tế không chỉ tải tài liệu mà còn thông báo cho bạn ngay khi có một lần thay thế phông chữ xảy ra.

Chúng tôi sẽ bao phủ mọi thứ từ việc tạo `LoadOptions` đến việc gắn một `WarningCallback` in ra thông báo rõ ràng mỗi khi Aspose.Words thay thế một phông chữ bị thiếu. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng cho bất kỳ tệp `.docx` nào, và bạn sẽ hiểu *tại sao* mỗi phần lại quan trọng. Không cần thư viện phụ trợ, chỉ cần Java thuần và Aspose.Words.

## Những gì bạn sẽ học

- Cách cấu hình **LoadOptions** để sử dụng **FontSettings** tùy chỉnh.  
- Cách triển khai một **IWarningCallback** để bắt các cảnh báo `FONT_SUBSTITUTION`.  
- Cách tải tài liệu trong khi giám sát an toàn các phông chữ bị thiếu.  
- Đầu ra console dự kiến và cách điều chỉnh mã cho các framework logging.  

**Prerequisites**: Java 8+ đã được cài đặt, Aspose.Words for Java (v23.12 hoặc mới hơn) có trong classpath, và một tệp mẫu `.docx` tham chiếu tới một phông chữ bạn không có trên máy. Đó là tất cả—không cần công cụ xây dựng phụ trợ.

---

## Bước 1: Thiết lập dự án và thêm Aspose.Words

Trước khi chúng ta bắt đầu viết mã, hãy chắc chắn rằng Aspose.Words đã sẵn sàng. Nếu bạn dùng Maven, thêm phụ thuộc sau vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Nếu bạn thích Gradle, tương đương là:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

Khi thư viện đã có trong classpath, bạn đã sẵn sàng để **phát hiện việc thay thế phông chữ bị thiếu** chỉ bằng một lời gọi phương thức duy nhất.

---

## Bước 2: Tạo LoadOptions và gắn FontSettings

Trái tim của giải pháp nằm ở việc chuẩn bị một thể hiện `LoadOptions` biết cách giám sát các vấn đề về phông chữ. Dưới đây là mã được chia nhỏ từng dòng.

```java
import com.aspose.words.*;

public class MissingFontDetector {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Prepare load options – this object controls how the document is read.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Create FontSettings – it holds font‑related configuration.
        FontSettings fontSettings = new FontSettings();

        // 3️⃣ Register a warning callback that will be invoked on font substitution.
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about FONT_SUBSTITUTION warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // 4️⃣ Attach the FontSettings to the LoadOptions.
        loadOptions.setFontSettings(fontSettings);
```

**Tại sao điều này quan trọng**: `LoadOptions` chỉ cho Aspose.Words *cách* diễn giải tệp đầu vào. Bằng cách cắm vào một `FontSettings` được tùy chỉnh, chúng ta cung cấp cho bộ tải một hook (`IWarningCallback`) sẽ kích hoạt **đúng khi một phông chữ bị thiếu được thay thế**. Nếu không có callback này, Aspose.Words sẽ thay thế phông chữ một cách âm thầm và bạn sẽ không bao giờ biết.

---

## Bước 3: Tải tài liệu với các tùy chọn đã cấu hình

Bây giờ hệ thống cảnh báo đã sẵn sàng, việc tải tài liệu trở nên đơn giản.

```java
        // 5️⃣ Load the document using the prepared options.
        // Replace the path with the location of your test file.
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Optional: do something with the document (e.g., save as PDF).
        // doc.save("output.pdf");
    }
}
```

Khi lệnh `new Document(...)` chạy, Aspose.Words sẽ đọc tệp, kiểm tra từng tham chiếu phông chữ và nếu không tìm thấy phông chữ tương ứng trên hệ thống, nó sẽ kích hoạt phương thức `warning` mà chúng ta đã định nghĩa trước đó. Console sẽ ngay lập tức hiển thị một dòng như:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Dòng đó là đầu ra **phát hiện việc thay thế phông chữ bị thiếu** mà bạn đang tìm kiếm.

---

## Bước 4: Xác minh kết quả và tinh chỉnh Callback (Nâng cao)

### 4.1 Kiểm tra nhanh

Chạy chương trình từ IDE hoặc qua `java -cp .;aspose-words-23.12.jar MissingFontDetector`. Nếu tài liệu tham chiếu một phông chữ bạn không có, bạn sẽ thấy thông báo cảnh báo được in ra. Nếu console im lặng, hoặc là phông chữ đã tồn tại trên máy, hoặc tài liệu không yêu cầu bất kỳ phông chữ nào bị thiếu.

### 4.2 Ghi log thay vì `System.out`

Trong mã production, bạn có thể muốn dùng một logger:

```java
import java.util.logging.Logger;

private static final Logger logger = Logger.getLogger(MissingFontDetector.class.getName());

fontSettings.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        logger.warning("Font substitution: " + info.getMessage());
    }
});
```

Thay đổi nhỏ này giúp cơ chế **phát hiện việc thay thế phông chữ bị thiếu** hoạt động tốt hơn với các pipeline logging hiện có.

### 4.3 Xử lý các loại cảnh báo khác

Callback nhận *tất cả* các cảnh báo, không chỉ vấn đề phông chữ. Nếu bạn muốn theo dõi các vấn đề khác (ví dụ, `UNKNOWN_STYLE`), hãy thêm các nhánh `if` bổ sung. Dưới đây là một ví dụ nhanh:

```java
if (info.getWarningType() == WarningType.UNKNOWN_STYLE) {
    logger.info("Unknown style encountered: " + info.getMessage());
}
```

---

## Bước 5: Những lỗi thường gặp và mẹo chuyên nghiệp

| Vấn đề | Nguyên nhân | Cách khắc phục |
|--------|-------------|----------------|
| **Không có cảnh báo nào xuất hiện** | Phông chữ thực tế đã tồn tại trên hệ điều hành, hoặc tài liệu sử dụng fallback mà Aspose.Words coi là “đã tìm thấy”. | Xóa tạm thời phông chữ khỏi hệ thống hoặc dùng một tên phông chữ thực sự không tồn tại trong tài liệu nguồn. |
| **Callback không bao giờ được gọi** | `setWarningCallback` đã được gọi trên một thể hiện `FontSettings` *khác* với thể hiện được gắn vào `LoadOptions`. | Đảm bảo bạn gọi `loadOptions.setFontSettings(fontSettings)` **sau** khi đã cấu hình callback. |
| **Giảm hiệu năng** | Tải nhiều tài liệu lớn với callback có thể tạo thêm overhead. | Cache một thể hiện `FontSettings` duy nhất và tái sử dụng nó cho các lần tải nếu bạn xử lý hàng loạt. |
| **Đa luồng** | `FontSettings` không an toàn với đa luồng theo mặc định. | Tạo một `FontSettings` riêng cho mỗi luồng hoặc đồng bộ hoá truy cập. |

**Mẹo pro**: Nếu bạn đang tạo PDF cho một dịch vụ web, bạn có thể muốn thu thập tất cả các cảnh báo thay thế vào một danh sách và trả về trong phản hồi API, thay vì in ra console.

---

## Ví dụ hoàn chỉnh (Sẵn sàng sao chép‑dán)

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {
        // Prepare load options
        LoadOptions loadOptions = new LoadOptions();

        // Configure font settings with a warning callback
        FontSettings fontSettings = new FontSettings();
        fontSettings.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substitution detected: " + info.getMessage());
                }
            }
        });

        // Attach font settings to load options
        loadOptions.setFontSettings(fontSettings);

        // Path to the document that contains a missing font
        String docPath = "YOUR_DIRECTORY/docWithMissingFont.docx";

        // Load the document – this triggers the callback if needed
        Document doc = new Document(docPath, loadOptions);

        // Optional: save as PDF to verify visual output
        // doc.save("output.pdf");

        System.out.println("Document loaded successfully.");
    }
}
```

**Đầu ra console dự kiến** (giả sử tệp tham chiếu một phông chữ bị thiếu):

```
⚠️ Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
Document loaded successfully.
```

Nếu không có phông chữ nào bị thiếu, bạn sẽ chỉ thấy dòng cuối cùng “Document loaded successfully.”.

---

## Kết luận

Chúng ta vừa chứng minh cách **phát hiện việc thay thế phông chữ bị thiếu** trong Java bằng Aspose.Words. Bằng cách cấu hình `LoadOptions`, tạo một thể hiện `FontSettings`, và gắn một `IWarningCallback`, bạn sẽ có được khả năng quan sát đầy đủ mọi lần thư viện thay thế phông chữ phía sau. Cách tiếp cận này không chỉ ngăn chặn các lỗi render im lặng mà còn cung cấp một điểm nối để ghi log, cảnh báo, hoặc thậm chí tự động nhúng các phông chữ dự phòng.

Từ đây, bạn có thể:

- Mở rộng callback để thu thập các cảnh báo vào danh sách cho phản hồi API.  
- Kết hợp kỹ thuật này với cấu hình **LoadOptions** cho các kịch bản khác (ví dụ, tải tài nguyên tùy chỉnh).  
- Khám phá toàn bộ hệ sinh thái **Java Aspose.Words**: chuyển đổi sang PDF, trích xuất văn bản, hoặc thực hiện mail merge.

Hãy thử, tinh chỉnh logger, và để ứng dụng của bạn lên tiếng khi một phông chữ biến mất. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Bắt lỗi cảnh báo thay thế phông chữ trong Java với Aspose.Words – Hướng dẫn đầy đủ](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Sử dụng Document Options và Settings trong Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}