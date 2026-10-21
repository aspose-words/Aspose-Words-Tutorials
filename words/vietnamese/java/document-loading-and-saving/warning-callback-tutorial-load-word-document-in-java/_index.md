---
category: general
date: 2026-03-25
description: Hướng dẫn callback cảnh báo khi tải tài liệu Word trong Java và xử lý
  phông chữ thiếu. Tìm hiểu cách tải tài liệu Word bằng Java với callback cảnh báo
  tùy chỉnh.
draft: false
keywords:
- warning callback tutorial
- load word document java
- handle missing fonts
language: vi
og_description: Hướng dẫn callback cảnh báo cho thấy cách tải tài liệu Word trong
  Java đồng thời xử lý các phông chữ thiếu bằng một callback cảnh báo tùy chỉnh.
og_title: Hướng dẫn callback cảnh báo – Tải tài liệu Word trong Java
tags:
- java
- aspose-words
- document-processing
title: Hướng dẫn callback cảnh báo – Tải tài liệu Word trong Java
url: /vi/java/document-loading-and-saving/warning-callback-tutorial-load-word-document-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hướng dẫn callback cảnh báo – Tải tài liệu Word trong Java

Bạn đã bao giờ cố gắng tải một tệp **.docx** trong Java mà chỉ thấy một cảnh báo mơ hồ về việc thiếu phông chữ chưa? Bạn không phải là người duy nhất. Trong **hướng dẫn callback cảnh báo** này, chúng tôi sẽ hướng dẫn qua một ví dụ hoàn chỉnh, sẵn sàng chạy mà không chỉ tải tài liệu Word mà còn bắt các cảnh báo thay thế phông chữ để bạn có thể phản hồi chúng một cách lập trình.

Nếu bạn đang tự hỏi cách **load word document java** một cách hiệu quả trong khi vẫn theo dõi các cảnh báo *handle missing fonts*, bạn đang ở đúng chỗ. Khi kết thúc hướng dẫn này, bạn sẽ có một mẫu có thể tái sử dụng cho bất kỳ dự án Java nào sử dụng Aspose.Words (hoặc thư viện tương tự) và bạn sẽ hiểu tại sao một callback cảnh báo là cách sạch nhất để luôn nắm bắt các vấn đề về phông chữ.

---

## Những gì bạn sẽ học

- Mã chính xác cần thiết để cấu hình một warning callback trong Java.  
- Cách callback phân biệt các cảnh báo thay thế phông chữ với các loại tin nhắn khác.  
- Các cách ghi log, ẩn hoặc thậm chí thay thế phông chữ thiếu ngay trong quá trình chạy.  
- Mẹo khắc phục các lỗi thường gặp khi tải tài liệu Word có tham chiếu tới các phông chữ không có sẵn.

### Yêu cầu trước

- Java 17 (hoặc mới hơn) đã được cài đặt trên máy của bạn.  
- Công cụ xây dựng như Maven hoặc Gradle (chúng tôi sẽ đưa ví dụ Maven).  
- Thư viện Aspose.Words for Java (bản dùng thử miễn phí đủ cho việc thử nghiệm).  
- Một tệp mẫu **input.docx** sử dụng phông chữ mà bạn không có cài đặt (để kích hoạt cảnh báo).

> **Pro tip:** Nếu bạn chưa có Aspose.Words, hãy thêm phụ thuộc được hiển thị bên dưới và để Maven tải về cho bạn—không cần thao tác thủ công với các file JAR.

---

## Bước 1: Thiết lập dự án và nhập các lớp cần thiết

Đầu tiên, chúng ta cần các tọa độ Maven đúng. Thêm đoạn này vào `pom.xml` của bạn:

```xml
<!-- Maven dependency for Aspose.Words -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Bây giờ tạo một lớp Java mới, ví dụ `WordLoader.java`, và nhập các kiểu cần thiết:

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import com.aspose.words.WarningType;
```

Các import này cho phép chúng ta truy cập `LoadOptions`, giao diện `IWarningCallback`, và đối tượng `WarningInfo` để biết *điều gì* đã sai.

---

## Bước 2: Định nghĩa Warning Callback – Trái tim của hướng dẫn

**warning callback tutorial** dựa vào việc chặn các sự kiện thay thế phông chữ. Dưới đây là một triển khai ngắn gọn nhưng đầy đủ chức năng:

```java
// Step 2: Create a warning callback that prints font substitution messages
class FontSubstitutionCallback implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("⚠️ Font substituted: " + info.getDescription());
        }
    }
}
```

**Tại sao điều này quan trọng:**  
- `IWarningCallback` được gọi *mỗi* khi Aspose.Words gặp một tình huống đáng chú ý.  
- Bằng cách kiểm tra `info.getWarningType()`, chúng ta lọc bỏ các cảnh báo không liên quan (như tính năng đã lỗi thời) và chỉ tập trung vào kịch bản **handle missing fonts**.  
- Ghi mô tả giúp bạn biết tên phông chữ gốc và phông thay thế đã được dùng, điều này rất quan trọng cho các kiểm tra bố cục sau này.

---

## Bước 3: Gắn Callback vào LoadOptions

Bây giờ chúng ta gắn callback vào một thể hiện `LoadOptions`. Đây là điểm mà quy trình **load word document java** nhận thức được trình xử lý tùy chỉnh của chúng ta.

```java
// Step 3: Prepare LoadOptions with the custom warning callback
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontSubstitutionCallback());
```

Bạn cũng có thể đặt các tùy chọn khác ở đây—như `setPassword` cho các tệp được mã hóa hoặc `setLoadFormat` nếu cần buộc một định dạng cụ thể. Callback hoạt động độc lập với các cài đặt đó.

---

## Bước 4: Tải tài liệu và quan sát Callback hoạt động

Với mọi thứ đã được gắn, việc tải tài liệu chỉ cần một dòng lệnh:

```java
// Step 4: Load the .docx file using the configured LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Khi tệp tham chiếu tới một phông chữ thiếu, bạn sẽ thấy đầu ra tương tự như:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Nếu các phông chữ của tài liệu đều có sẵn, callback sẽ im lặng—đúng như mong đợi khi **handling missing fonts** một cách khéo léo.

---

## Bước 5: Xác minh kết quả và xử lý hậu kỳ tùy chọn

Sau khi tải, bạn có thể muốn xác nhận tài liệu có thể sử dụng được, chẳng hạn bằng cách chuyển đổi sang PDF hoặc trích xuất văn bản thuần:

```java
// Optional: Save as PDF to verify visual fidelity
document.save("output.pdf");

// Or extract plain text to a console for quick inspection
System.out.println(document.getText());
```

Cả hai hành động này sẽ tôn trọng việc thay thế đã xảy ra trước đó, vì vậy bạn có thể thấy ảnh hưởng thực tế của phông chữ thiếu lên kết quả cuối cùng.

---

## Các trường hợp đặc biệt & Những lỗi thường gặp

| Tình huống | Điều gì xảy ra | Cách xử lý |
|-----------|----------------|------------|
| **Nhiều phông chữ thiếu** | Callback được kích hoạt một lần cho mỗi phông chữ thiếu. | Giữ callback nhẹ nhàng; tránh thực hiện I/O nặng trong `warning()`. |
| **Thư mục phông chữ tùy chỉnh** | Aspose.Words vẫn báo cáo thay thế nếu phông không nằm trong đường tìm kiếm mặc định. | Dùng `loadOptions.setFontSettings(FontSettings.getDefaultInstance())` và thêm thư mục phông của bạn qua `FontSettings.getDefaultInstance().setFontsFolder("path", true)`. |
| **Ứng dụng yêu cầu hiệu năng cao** | Ghi log quá mức có thể làm chậm quá trình xử lý hàng loạt. | Chuyển sang logger mức `WARN` và tắt việc in ra console trong môi trường production. |
| **Cảnh báo không liên quan tới phông** | Callback nhận được nhiều loại cảnh báo (ví dụ `DEPRECATED_FEATURE`). | Lọc bằng `WarningType` như đã minh họa; bạn cũng có thể thu thập các cảnh báo khác để làm báo cáo chẩn đoán. |

---

## Ví dụ đầy đủ hoạt động

Dưới đây là chương trình tự chứa đầy đủ mà bạn có thể sao chép‑dán vào IDE. Nó bao gồm tất cả các import, lớp callback, và một phương thức `main` đơn giản.

```java
import com.aspose.words.*;

public class WordLoader {
    // Custom warning callback – only cares about font substitution
    static class FontSubstitutionCallback implements IWarningCallback {
        @Override
        public void warning(WarningInfo info) {
            if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                System.out.println("⚠️ Font substituted: " + info.getDescription());
            }
        }
    }

    public static void main(String[] args) {
        try {
            // 1️⃣ Prepare LoadOptions with our callback
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setWarningCallback(new FontSubstitutionCallback());

            // 2️⃣ Load the document – this triggers the callback if needed
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // 3️⃣ Optional verification – save as PDF and print text
            doc.save("output.pdf");                     // visual check
            System.out.println("--- Extracted Text ---");
            System.out.println(doc.getText());          // quick sanity check
        } catch (Exception e) {
            // In real apps, use proper logging instead of printStackTrace
            e.printStackTrace();
        }
    }
}
```

**Đầu ra console dự kiến** (khi phát hiện phông chữ thiếu):

```
⚠️ Font substituted: Font 'Times New Roman' was not found. Substituted with 'Liberation Serif'.
--- Extracted Text ---
[Document text appears here...]
```

Nếu không có phông chữ nào thiếu, bạn sẽ chỉ thấy tiêu đề văn bản đã trích xuất.

---

## Tổng quan hình ảnh

![sơ đồ tutorial callback cảnh báo cho thấy luồng từ LoadOptions → IWarningCallback → đầu ra console](/images/warning-callback-tutorial.png "sơ đồ tutorial callback cảnh báo")

*Biểu đồ minh họa cách warning callback chặn các sự kiện thay thế phông chữ trong quá trình tải tài liệu.*

---

## Tóm tắt & Các bước tiếp theo

Chúng ta vừa hoàn thành một **warning callback tutorial** cho thấy cách **load word document java** một cách khéo léo đồng thời **handle missing fonts**. Những điểm chính cần ghi nhớ là:

1. Triển khai `IWarningCallback` và lọc `WarningType.FONT_SUBstitution`.  
2. Gắn callback vào `LoadOptions` trước khi tải tài liệu.  
3. Xác minh kết quả bằng cách lưu hoặc trích xuất văn bản, và tùy chọn tinh chỉnh đường tìm kiếm phông chữ.

Từ đây bạn có thể khám phá:

- **Thay thế phông chữ tùy chỉnh**: Thay thế phông chữ thiếu bằng một phông chữ bạn chọn một cách lập trình.  
- **Xử lý hàng loạt**: Duyệt qua một thư mục các tài liệu, thu thập tất cả cảnh báo thay thế vào báo cáo CSV.  
- **Tích hợp với framework logging**: Đưa các cảnh báo vào Log4j hoặc SLF4J để chẩn đoán ở mức production.

Hãy thử các ý tưởng này, và bạn sẽ nhanh chóng thấy sức mạnh của một warning callback được đặt đúng chỗ trong các pipeline tài liệu thực tế.

---

### Có câu hỏi?

Bạn có thể để lại bình luận bên dưới hoặc nhắn tin cho tôi trên GitHub. Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng phông chữ mong muốn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}