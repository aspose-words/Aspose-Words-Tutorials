---
category: general
date: 2026-03-19
description: Tìm hiểu cách ghi lại các cảnh báo trong Aspose.Words cho Java và phát
  hiện phông chữ thiếu. Hướng dẫn từng bước này cũng chỉ cách xử lý phông chữ thiếu
  một cách nhẹ nhàng.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: vi
og_description: Cách bắt các cảnh báo trong Aspose.Words cho Java, phát hiện phông
  chữ thiếu và xử lý phông chữ thiếu với ví dụ mã đầy đủ.
og_title: Cách bắt cảnh báo – Phát hiện phông chữ thiếu trong Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Cách bắt cảnh báo – Phát hiện phông chữ thiếu trong Aspose.Words
url: /vi/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Ghi Nhận Cảnh Báo – Phát Hiện Phông Chữ Thiếu Trong Aspose.Words

Bạn có bao giờ tự hỏi **cách ghi nhận cảnh báo** khi một tài liệu Word được tải và một số phông chữ không có trên máy tính không? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế, phông chữ thiếu gây ra sự thay đổi bố cục im lặng, và cách duy nhất để biết điều gì đã xảy ra là lắng nghe luồng cảnh báo mà Aspose.Words phát ra.  

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy mà **phát hiện phông chữ thiếu**, cho bạn thấy **cách phát hiện phông chữ thiếu** một cách lập trình, và thậm chí đưa ra một mẹo nhanh về **xử lý phông chữ thiếu** để đầu ra của bạn luôn dự đoán được.

> **Lưu ý nhanh:** Mã này hoạt động với Aspose.Words 23.9 (hoặc mới hơn) và yêu cầu Java 8+.

---

## Những Gì Bạn Cần

- **Aspose.Words for Java** (phụ thuộc Maven/Gradle hoặc JAR trên classpath)  
- Một tệp Word (`input.docx`) tham chiếu tới một phông chữ không được cài đặt trên hệ thống của bạn (ví dụ, “Comic Sans MS”)  
- Một IDE Java hoặc thiết lập dòng lệnh đơn giản `javac`/`java`  

Không cần thư viện nào khác—tất cả những gì còn lại đều nằm trong gói Aspose.Words.

---

## Bước 1 – Thiết Lập LoadOptions Để Ghi Nhận Cảnh Báo  

Để bắt đầu lắng nghe các cảnh báo, bạn phải tạo một thể hiện `LoadOptions`. Đối tượng này chỉ cho bộ tải biết phải theo dõi bất kỳ vấn đề nào nó gặp phải, chẳng hạn như phông chữ thiếu.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Tại sao điều này quan trọng:** Nếu không có `LoadOptions`, bộ tải sẽ im lặng thay thế các phông chữ thiếu bằng phông chữ hệ thống mặc định, và bạn sẽ không bao giờ biết một sự thay thế đã xảy ra. Bật cảnh báo sẽ cho bạn toàn bộ khả năng quan sát.

---

## Bước 2 – Tải Tài Liệu Bằng LoadOptions  

Bây giờ chúng ta thực sự tải tài liệu. `LoadOptions` mà chúng ta vừa tạo được truyền vào hàm khởi tạo, vì vậy bất kỳ cảnh báo nào được tạo ra trong quá trình phân tích sẽ được ghi nhận.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Mẹo chuyên nghiệp:** Nếu bạn đang xử lý nhiều tệp trong một lô, hãy tái sử dụng cùng một thể hiện `LoadOptions` để tránh việc tạo đối tượng không cần thiết.

---

## Bước 3 – Duyệt Qua Các Cảnh Báo Đã Ghi Nhận  

Aspose.Words lưu mỗi cảnh báo dưới dạng một đối tượng `WarningInfo`. Chúng ta chỉ quan tâm đến các cảnh báo liên quan đến phông chữ, vì vậy chúng ta lọc ra `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Giải thích:**  
- `document.getWarnings()` trả về danh sách mọi cảnh báo xảy ra trong quá trình tải.  
- `FontSubstitutionWarningInfo` chứa hai dữ liệu quan trọng: **phông chữ yêu cầu** (phông chữ mà DOCX yêu cầu) và **phông chữ thực tế** mà Aspose.Words sử dụng thay thế.  
- Bằng cách in ra cả hai, bạn ngay lập tức thấy phông chữ nào bị thiếu và sự thay thế nào đã diễn ra.

---

## Bước 4 – (Tùy Chọn) Xử Lý Phông Chữ Thiếu Một Cách Lập Trình  

Ghi nhận cảnh báo chỉ là một phần của câu chuyện. Khi bạn biết một phông chữ bị thiếu, bạn có thể muốn **xử lý phông chữ thiếu** bằng cách cung cấp một sự thay thế tùy chỉnh hoặc ghi lại vấn đề để xem xét sau.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Tại sao làm như vậy?**  
- Đảm bảo việc hiển thị nhất quán trên các máy tính.  
- Ngăn ngừa các thay đổi bố cục không mong muốn trong PDF hoặc hình ảnh được tạo sau này.  

Bạn cũng có thể lưu chi tiết cảnh báo vào cơ sở dữ liệu, gửi email cho nhóm nội dung, hoặc thậm chí hủy quá trình nếu một phông chữ quan trọng bị thiếu.

---

## Ví Dụ Hoàn Chỉnh Hoạt Động  

Dưới đây là chương trình đầy đủ, có thể chạy được. Chỉ cần thay thế `YOUR_DIRECTORY/input.docx` bằng đường dẫn tới tệp thử nghiệm của bạn, thêm JAR Aspose.Words vào classpath, và chạy.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Kết quả mong đợi** (khi “Comic Sans MS” bị thiếu):

```
Requested: Comic Sans MS → Substituted: Arial
```

Sau khi mã dự phòng tùy chọn chạy, tệp `output.docx` đã lưu sẽ hiển thị bằng **Arial** ở mọi nơi mà “Comic Sans MS” đã được tham chiếu ban đầu.

---

## Câu Hỏi Thường Gặp & Trường Hợp Cạnh  

| Question | Answer |
|----------|--------|
| *Nếu tài liệu có nhiều phông chữ bị thiếu thì sao?* | Vòng lặp sẽ phát ra một cảnh báo cho mỗi phông chữ. Bạn có thể thu thập chúng vào một `Map<String, String>` để xử lý hàng loạt. |
| *Điều này có hoạt động cho các PDF được tạo từ tài liệu không?* | Chắc chắn. Việc thay thế phông chữ diễn ra trong giai đoạn tải, vì vậy bất kỳ xuất ra nào sau này (PDF, HTML, hình ảnh) sẽ sử dụng các phông chữ đã được giải quyết. |
| *Tôi có thể ẩn các cảnh báo thay vì ghi nhận chúng không?* | Có—đặt `loadOptions.setWarningCallback(null);` nhưng bạn sẽ mất khả năng quan sát các phông chữ thiếu. |
| *Danh sách cảnh báo có bị xóa sau khi lưu không?* | Bộ sưu tập cảnh báo thuộc về đối tượng `Document`. Sau khi bạn gọi `document.save()`, danh sách vẫn không thay đổi trừ khi bạn tạo một `Document` mới. |
| *Còn các phông chữ tùy chỉnh được nhúng trong DOCX thì sao?* | Các phông chữ được nhúng được coi là có sẵn; Aspose.Words sẽ sử dụng chúng ngay cả khi chúng không được cài đặt trên hệ thống máy chủ. |

---

## Mẹo Chuyên Nghiệp Cho Sử Dụng Trong Sản Xuất  

- **Cache FontSettings:** Nếu bạn xử lý hàng trăm tệp, hãy tạo một `FontSettings` duy nhất với các fallback ưa thích và tái sử dụng nó để tránh chi phí dư thừa.  
- **Log Structured Data:** Thay vì `System.out` đơn giản, ghi cảnh báo vào một log JSON—điều này làm cho việc phân tích downstream (ví dụ, “phông chữ thiếu nhiều nhất”) trở nên dễ dàng.  
- **Validate Early:** Thực hiện một “dry‑load” nhanh với `LoadOptions` trước khi xử lý nặng; hủy sớm nếu các phông chữ quan trọng bị thiếu.  
- **Thread Safety:** Các đối tượng `Document` không an toàn với đa luồng. Giữ việc xử lý mỗi tệp trong một luồng riêng hoặc sử dụng `LoadOptions` thread‑local.  

---

## Kết Luận  

Bạn đã biết **cách ghi nhận cảnh báo** trong Aspose.Words cho Java, **phát hiện phông chữ thiếu**, và **xử lý phông chữ thiếu** bằng một chiến lược fallback sạch sẽ. Bằng cách tận dụng `LoadOptions` và duyệt qua `document.getWarnings()`, bạn có được toàn bộ thông tin về các sự kiện thay thế phông chữ, đảm bảo các tài liệu được tạo ra hiển thị chính xác như mong muốn trên mọi môi trường.  

Sẵn sàng cho bước tiếp theo? Hãy thử mở rộng mẫu này để **phát hiện hình ảnh thiếu**, **theo dõi các tính năng không được hỗ trợ**, hoặc thậm chí **tự động nhúng phông chữ thiếu** vào tệp đầu ra. Cách tiếp cận ghi nhận cảnh báo tương tự hoạt động cho nhiều kịch bản xử lý tài liệu khác, làm cho mã của bạn mạnh mẽ và chuẩn bị cho tương lai.  

Chúc lập trình vui vẻ, và mong các tài liệu của bạn luôn hiển thị một cách tuyệt đẹp!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}