---
category: general
date: 2026-06-27
description: Tìm hiểu cách bắt các cảnh báo thay thế phông chữ trong Java bằng Aspose.Words.
  Hướng dẫn từng bước này cũng đề cập đến các callback cảnh báo và cách sử dụng LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: vi
og_description: Ghi lại cảnh báo thay thế phông chữ trong Java với Aspose.Words. Thực
  hiện theo hướng dẫn này để thiết lập callback cảnh báo, sử dụng LoadOptions và xử
  lý các phông chữ bị thiếu.
og_title: Ghi lại các cảnh báo thay thế phông chữ trong Java – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Ghi lại Cảnh báo Thay thế Phông chữ trong Java với Aspose.Words – Hướng dẫn
  đầy đủ
url: /vi/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ghi lại Cảnh báo Thay thế Phông chữ trong Java với Aspose.Words – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **ghi lại các cảnh báo thay thế phông chữ** khi tải một tệp DOCX sử dụng các phông chữ hiếm? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế—như các công cụ tạo báo cáo tự động hoặc bộ chuyển đổi tài liệu hàng loạt—các phông chữ thiếu sẽ gây ra việc thay thế im lặng, có thể làm hỏng độ chính xác của bố cục.  

May mắn là Aspose.Words cung cấp cho bạn một cách sạch sẽ để lắng nghe các cảnh báo đó. Trong hướng dẫn này chúng ta sẽ đi qua việc cấu hình **LoadOptions**, gắn một **Aspose.Words warning callback**, và in mỗi thông báo *thay thế phông chữ* ra console. Khi kết thúc, bạn sẽ biết chính xác khi nào một phông chữ đã được thay thế và cách phản hồi một cách lập trình.

> **Bạn sẽ nhận được:** một đoạn mã Java có thể chạy đầy đủ, giải thích *tại sao* mỗi phần lại quan trọng, và mẹo xử lý các trường hợp đặc biệt như thư mục phông chữ tùy chỉnh.

## Yêu cầu trước & Những gì bạn cần

- Java 8 hoặc mới hơn đã được cài đặt (mã cũng hoạt động với Java 11+).
- JAR Aspose.Words for Java mới nhất (tải từ trang chính thức hoặc Maven Central).
- Một tệp DOCX tham chiếu đến các phông chữ không được cài trên máy của bạn (ví dụ, một *font‑rich.docx* bạn có thể tìm trong bộ demo của Aspose).
- Một IDE tốt (IntelliJ IDEA, Eclipse, hoặc thậm chí VS Code với các extension Java).

Không cần thư viện bên ngoài nào ngoài Aspose.Words, và ví dụ chạy trong một phương thức `main` đơn giản.

## Bước 1: Thiết lập LoadOptions – Điểm vào cho việc tải tùy chỉnh

`LoadOptions` là túi cấu hình của Aspose.Words cho biết thư viện *cách* đọc một tài liệu. Mặc định nó sẽ thay thế âm thầm các phông chữ thiếu, nhưng bạn có thể thay đổi hành vi này bằng một callback cảnh báo.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Tại sao điều này quan trọng:** Nếu không có `LoadOptions`, tài liệu sẽ được tải một cách yên lặng và bạn sẽ mất khả năng nhìn thấy các phông chữ bị thiếu. Khi tạo một thể hiện, bạn sẽ có một hook cho hệ thống cảnh báo.

## Bước 2: Định nghĩa Warning Callback để *Ghi lại Cảnh báo Thay thế Phông chữ*

Aspose.Words đẩy các sự kiện cảnh báo qua giao diện `IWarningCallback`. Thực thi nó ngay trong mã (hoặc dưới dạng lớp riêng) và lọc cho `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Giải thích:**  
- `info.getWarningType()` cho bạn biết loại cảnh báo.  
- `WarningType.FONT_SUBSTITUTION` là giá trị enum mà chúng ta quan tâm.  
- `info.getDescription()` chứa thông điệp dạng người đọc được, ví dụ, *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Bằng cách in mô tả, bạn **ghi lại các cảnh báo thay thế phông chữ** trong thời gian thực.

## Bước 3: Tải Tài liệu Sử dụng LoadOptions Đã Cấu hình

Bây giờ callback đã sẵn sàng, hãy tải DOCX của bạn. Callback cảnh báo sẽ tự động kích hoạt trong quá trình phân tích.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế tới tệp thử nghiệm của bạn. Khi hàm khởi tạo `Document` chạy, bất kỳ phông chữ nào bị thiếu sẽ kích hoạt callback đã định nghĩa trước, và bạn sẽ thấy các thông báo thay thế trên console.

## Bước 4: Xác minh Tài liệu Đã Tải (Tùy chọn nhưng Hữu ích)

Sau khi tải, bạn có thể muốn xác nhận tính toàn vẹn của tài liệu—số trang, trích xuất văn bản, v.v. Bước này không bắt buộc để ghi lại cảnh báo, nhưng nó giúp bạn thấy ảnh hưởng của các lần thay thế.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Nếu một phông chữ đã được thay thế, bố cục có thể dịch chuyển nhẹ; việc kiểm tra số trang có thể phát hiện những thay đổi này.

## Bước 5: Nâng cao – Xử lý Phông chữ Được Thay Thế Một cách Lập trình

Đôi khi bạn không chỉ muốn ghi log cảnh báo—bạn có thể cần nhúng một phông chữ dự phòng hoặc điều chỉnh kiểu dáng. Dưới đây là một mẫu nhanh bạn có thể áp dụng.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Bằng cách chỉ định cho Aspose.Words một thư mục chứa các phông chữ gốc, bạn có thể *ngăn* việc thay thế hoàn toàn. Nếu thư mục này thiếu, callback vẫn sẽ ghi lại sự kiện, cung cấp cho bạn chiến lược dự phòng.

## Ví dụ Hoàn chỉnh Có Thể Chạy

Kết hợp tất cả lại, đây là chương trình đầy đủ, sẵn sàng chạy:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Kết quả dự kiến trên console** (khi gặp phông chữ thiếu):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Nếu tất cả các phông chữ đều có, callback sẽ im lặng—không có gì được in ra, đúng như mong đợi.

## Những Sai lầm Thường gặp & Mẹo chuyên nghiệp

| Sai lầm | Tại sao lại xảy ra | Cách khắc phục |
|---------|-------------------|----------------|
| **Callback không bao giờ được kích hoạt** | Bạn quên gắn callback vào `LoadOptions` **hoặc** dùng constructor mặc định của `Document` mà không truyền `loadOptions`. | Luôn gọi `loadOptions.setWarningCallback(...)` **và** sử dụng overload `new Document(path, loadOptions)`. |
| **Quá nhiều cảnh báo làm lộn log** | Tài liệu lớn với nhiều phông chữ thiếu tạo ra một cảnh báo cho mỗi lần thay thế. | Lọc thêm bằng cách kiểm tra `info.getDescription()` cho các tên phông chữ cụ thể, hoặc gom các cảnh báo vào danh sách để xử lý sau. |
| **Phông chữ thay thế ảnh hưởng tới bố cục** | Phông chữ dự phòng có thể có metric (kích thước, khoảng cách) khác. | Cung cấp thư mục phông chữ tùy chỉnh (xem Bước 5) hoặc điều chỉnh style của tài liệu sau khi tải. |
| **Chạy trên server không có giao diện** | Phông chữ dự phòng mặc định có thể dựa vào các phông hệ thống không được cài trên server. | Đóng gói các phông chữ cần thiết cùng ứng dụng và chỉ định `FontSettings` tới thư mục đó. |

## Câu hỏi Thường gặp

**Q: Điều này có hoạt động với PDF hoặc các định dạng khác không?**  
A: Có. Callback cảnh báo không phụ thuộc vào định dạng; nó sẽ kích hoạt cho bất kỳ loại tài liệu nào mà Aspose.Words tải (DOC, DOCX, RTF, HTML, v.v.). Điểm khác nhau duy nhất là tập các cảnh báo có thể xuất hiện.

**Q: Tôi có thể ghi lại các loại cảnh báo khác, như cảnh báo *độ phân giải hình ảnh* không?**  
A: Chắc chắn. Trong phương thức `warning`, kiểm tra `info.getWarningType()` cho các giá trị enum khác như `WarningType.IMAGE_RESOLUTION`. Sau đó xử lý chúng theo nhu cầu.

**Q: Nếu tôi cần danh sách các phông chữ đã được thay thế sau khi tài liệu tải xong thì sao?**  
A: Lưu mỗi `info.getDescription()` vào một `List<String>` trong callback. Sau khi tải, bạn sẽ có một bộ sưu tập có thể log, gửi tới dịch vụ giám sát, hoặc dùng để kích hoạt quy trình tải phông chữ.

## Kết luận

Bạn giờ đã biết **cách ghi lại các cảnh báo thay thế phông chữ** trong Java bằng Aspose.Words, tại sao mỗi phần của giải pháp lại quan trọng, và cách mở rộng nó cho các tình huống thực tế. Bằng cách tận dụng `LoadOptions`, một `Aspose.Words warning callback`, và tùy chọn `FontSettings`, bạn sẽ có đầy đủ khả năng quan sát các phông chữ thiếu và giữ cho quy trình chuyển đổi tài liệu của mình luôn đáng tin cậy.

Sẵn sàng cho bước tiếp theo? Hãy thay `System.out.println` bằng một logger như SLF4J, hoặc tích hợp danh sách cảnh báo vào giao diện UI để cảnh báo người dùng trước khi hoàn tất chuyển đổi hàng loạt. Bạn cũng có thể khám phá **Aspose.Words warning callback** cho các loại cảnh báo khác, chẳng hạn *tính năng không được hỗ trợ* hoặc *cảnh báo hình ảnh độ phân giải cao*.  

Chúc bạn lập trình vui vẻ, và hy vọng các file PDF của bạn không bao giờ gặp phải việc thay thế phông chữ bất ngờ nữa! 

![Ảnh chụp màn hình hiển thị đầu ra console của các cảnh báo thay thế phông chữ đã được ghi lại](image-placeholder.png "ghi lại cảnh báo thay thế phông chữ")


## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Bật Cảnh báo Thay thế Phông chữ trong Aspose.Words – Hướng dẫn đầy đủ](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Cách Đặt LoadOptions trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cách Tạo Tài liệu PDF với Aspose.Words cho Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}