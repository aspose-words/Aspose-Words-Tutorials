---
category: general
date: 2026-06-30
description: Cấu hình LoadOptions cho cảnh báo trong Aspose.Words Java. Tìm hiểu cách
  thiết lập callback cảnh báo cho việc thay thế phông chữ và các cảnh báo khác của
  load‑options.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: vi
og_description: Cấu hình LoadOptions để nhận cảnh báo trong Aspose.Words Java. Hướng
  dẫn này chỉ cách bắt các cảnh báo thay thế phông chữ bằng callback cảnh báo.
og_title: Cấu hình LoadOptions cho Cảnh báo – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Cấu hình LoadOptions cho Cảnh báo – Hướng dẫn Java toàn diện
url: /vi/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cấu hình LoadOptions cho Cảnh báo – Hướng dẫn Java đầy đủ

Bạn đã bao giờ cần **cấu hình LoadOptions cho cảnh báo** khi mở tài liệu Word bằng Aspose.Words for Java chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp rắc rối khi một phông chữ thiếu bị thay thế một cách im lặng, khiến PDF cuối cùng trông không đúng thương hiệu. Tin tốt? Bằng cách gắn một **callback cảnh báo Java** vào `LoadOptions` của bạn, bạn có thể bắt mọi cảnh báo thay thế phông chữ ngay khi nó xảy ra.

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ thực tế không chỉ cho thấy cách thiết lập callback mà còn giải thích *tại sao* mỗi phần lại quan trọng. Khi kết thúc, bạn sẽ có thể **xử lý cảnh báo phông chữ**, ghi chúng lại, hoặc thậm chí thay thế phông chữ ngay lập tức—không cần đoán mò.

## Những gì bạn sẽ nhận được

- Một chương trình Java có thể chạy đầy đủ và in ra mọi cảnh báo thay thế phông chữ.
- Hiểu cơ chế **Aspose.Words font substitution**.
- Mẹo để tùy chỉnh việc xử lý cảnh báo cho các dự án lớn hơn.
- Kiến thức về **document loading options** và thời điểm cần điều chỉnh chúng.

> **Yêu cầu trước:** Java 8+ và thư viện Aspose.Words for Java (phiên bản 23.9 trở lên). Không cần bất kỳ phụ thuộc bên ngoài nào khác.

---

## Bước 1: Cấu hình LoadOptions cho Cảnh báo

Điều đầu tiên bạn cần là một thể hiện `LoadOptions` biết rằng nó nên báo cáo cảnh báo. Hãy nghĩ về `LoadOptions` như một bộ công cụ bạn đưa cho Aspose.Words trước khi nó mở tệp.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Tại sao điều này quan trọng:**  
`LoadOptions` kiểm soát cách thư viện đọc tài liệu. Bằng cách gán một `IWarningCallback`, bạn yêu cầu Aspose.Words gọi mã của bạn mỗi khi nó gặp điều gì đáng chú ý—như một phông chữ thiếu. Nếu không có điều này, thư viện sẽ thay thế phông chữ một cách im lặng và bạn sẽ không bao giờ biết.

> **Mẹo chuyên nghiệp:** Nếu bạn muốn bắt *tất cả* cảnh báo, bỏ qua câu lệnh `if`. Hiện tại chúng ta tập trung vào các vấn đề phông chữ vì chúng là nguồn gây bất ngờ về bố cục phổ biến nhất.

---

## Bước 2: Tải tài liệu bằng các tùy chọn đã cấu hình

Bây giờ callback đã sẵn sàng, tải tệp `.docx` của bạn (hoặc bất kỳ định dạng nào được hỗ trợ) bằng cùng một `LoadOptions`. Đây là nơi **document loading options** thực sự có tác dụng.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Bên trong:**  
Khi Aspose.Words phân tích `input.docx`, nó sẽ quét các bảng phông chữ. Nếu một phông chữ được tham chiếu trong tài liệu không được cài đặt trên máy chủ, engine sẽ phát sinh cảnh báo `FONT_SUBSTITUTION`, ngay lập tức kích hoạt callback mà chúng ta đã định nghĩa trước đó.

---

## Bước 3: Lưu tài liệu – Các cảnh báo đã được in ra

Lưu tài liệu là một thao tác đơn giản, nhưng đây là thời điểm bạn có thể xác minh rằng callback đã được kích hoạt đúng cách. Tất cả các cảnh báo được in ra trong bước tải, vì vậy thao tác lưu chỉ là một bước dọn dẹp.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Kết quả dự kiến trên console:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Nếu bạn không thấy gì, có thể tài liệu chỉ sử dụng các phông chữ đã được cài đặt, hoặc callback chưa được gắn đúng—hãy kiểm tra lại Bước 1.

---

## Bước 4: Mở rộng Callback để **Xử lý Cảnh báo Phông chữ** một cách Trơn tru

In ra console là ổn cho các bản demo, nhưng mã sản xuất thường cần xử lý phong phú hơn: ghi log vào tệp, gửi cảnh báo, hoặc thậm chí thay đổi phông chữ bằng chương trình.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Tại sao bạn nên làm điều này:**  
Một tệp log cung cấp thông tin hậu kiểm, đặc biệt khi xử lý hàng loạt tài liệu. Khối thay thế tùy chọn cho thấy cách **cấu hình LoadOptions cho cảnh báo** *và* can thiệp để thực thi chính sách phông chữ của công ty.

---

## Nâng cao: Kiểm soát các kịch bản **Aspose.Words Font Substitution** khác

Callback cảnh báo không chỉ giới hạn ở phông chữ thiếu. Bạn cũng có thể bắt:

- **Các ký tự Unicode không được hỗ trợ** (`WarningType.UNSUPPORTED_CHAR`).
- **Các vấn đề script phức tạp** (`WarningType.COMPLEX_SCRIPT`).

Chỉ cần mở rộng câu lệnh `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Điều này làm cho giải pháp của bạn vững chắc cho các tài liệu đa ngôn ngữ, một trường hợp thường gặp trong các ứng dụng toàn cầu.

---

## Ví dụ Hoạt động Đầy đủ

Dưới đây là chương trình hoàn chỉnh, sẵn sàng chạy. Dán nó vào bất kỳ IDE Java nào, thay thế các placeholder `YOUR_DIRECTORY`, và nhấn *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Kết quả Dự kiến

- Console in ra bất kỳ cảnh báo thay thế phông chữ nào.
- `font-warnings.log` chứa danh sách có dấu thời gian (nếu bạn giữ việc ghi log tùy chọn).
- `output.docx` được lưu với các phông chữ đã được thay thế, phù hợp với fallback bạn đã định nghĩa.

---

## Những Cạm Bẫy Thường Gặp & Cách Tránh

| Cạm bẫy | Tại sao lại xảy ra | Cách khắc phục |
|---------|--------------------|----------------|
| **Không có cảnh báo nào xuất hiện** | Callback chưa được gắn, hoặc tài liệu chỉ sử dụng các phông chữ đã được cài đặt. | Xác minh `loadOptions.setWarningCallback(...)` được gọi *trước* khi tải tài liệu. |
| **FileNotFoundException** trên `input.docx` | Đường dẫn sai hoặc tệp không được đóng gói trong dự án. | Sử dụng đường dẫn tuyệt đối hoặc đặt tệp vào thư mục resources của dự án. |
| **Giảm hiệu năng** khi xử lý hàng ngàn tài liệu | Ghi log quá mức lên đĩa cho mỗi cảnh báo. | Bộ đệm log và ghi theo lô, hoặc giới hạn ghi log chỉ cho các cảnh báo quan trọng. |
| **Thay thế phông chữ không mong muốn** mặc dù đã có fallback | Bảng thay thế chưa được áp dụng đủ sớm. | Đặt cài đặt thay thế **trước** khi tải tài liệu, hoặc sử dụng `FontSettings.setSubstitutionSettings` toàn cục. |

---

## Các Bước Tiếp Theo

Bây giờ bạn đã thành thạo **cấu hình LoadOptions cho cảnh báo**, hãy xem xét các chủ đề tiếp theo này:

- **Xử lý hàng loạt**: Lặp qua một thư mục các tài liệu, tổng hợp tất cả cảnh báo phông chữ thành một báo cáo duy nhất.
- **Nhà cung cấp phông chữ tùy chỉnh**: Tải phông chữ từ một chia sẻ mạng hoặc tài nguyên nhúng thay vì hệ điều hành cục bộ.
- **Tích hợp với các framework ghi log** như Log4j để đạt mức độ truy xuất doanh nghiệp.
- Khám phá các **document loading options** khác như phát hiện `LoadFormat` hoặc xử lý `Password` cho các tệp được bảo vệ.

Mỗi mục này dựa trên cùng một mẫu—tạo một đối tượng `LoadOptions`, gắn các callback phù hợp, và để Aspose.Words thực hiện phần công việc nặng.

---

## Kết luận

Chúng tôi đã đi sâu vào cách **cấu hình LoadOptions cho cảnh báo** trong Aspose.Words cho Java, thiết lập một **callback cảnh báo Java**, và sử dụng thông tin đó để **xử lý cảnh báo phông chữ** một cách thông minh. Mã nguồn ngắn gọn, các khái niệm rõ ràng, và bạn giờ đã có nền tảng vững chắc để mở rộng việc xử lý cảnh báo sang các kịch bản khác như ký tự không được hỗ trợ hoặc script phức tạp.

Hãy thử nghiệm, điều chỉnh bảng thay thế để phù hợp với phông chữ thương hiệu của bạn, và xem những việc thay thế phông chữ im lặng biến mất. Chúc lập trình vui vẻ!

--- 

![Sơ đồ minh họa luồng cấu hình LoadOptions cho cảnh báo, tải tài liệu, bắt sự kiện thay thế phông chữ và lưu kết quả](configure-loadoptions-for-warnings-diagram.png "Luồng cấu hình LoadOptions cho cảnh báo")

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn thành thạo các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Ghi lại Cảnh báo Thay thế Phông chữ trong Java với Aspose.Words – Hướng dẫn đầy đủ](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Cách Đặt LoadOptions trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cách Tải tài liệu RTF với Cấu hình RTF Load Options trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}