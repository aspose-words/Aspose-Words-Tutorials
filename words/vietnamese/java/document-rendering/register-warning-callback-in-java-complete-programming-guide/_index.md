---
category: general
date: 2026-05-23
description: Đăng ký callback cảnh báo trong Java để phát hiện phông chữ thiếu và
  xử lý việc thay thế phông chữ. Học từng bước với một ví dụ đầy đủ.
draft: false
keywords:
- register warning callback
- detect missing fonts
- Java font handling
- Aspose.Words warning callback
- font substitution detection
language: vi
og_description: Đăng ký callback cảnh báo trong Java để phát hiện phông chữ thiếu.
  Hướng dẫn này trình bày giải pháp hoàn chỉnh kèm mã nguồn, giải thích và các thực
  tiễn tốt nhất.
og_title: Đăng ký Callback Cảnh báo trong Java – Hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Register warning callback in Java to detect missing fonts and handle
    font substitutions. Learn step‑by‑step with a full example.
  headline: Register Warning Callback in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- FontSettings
- DocumentProcessing
title: Đăng ký Callback Cảnh báo trong Java – Hướng dẫn Lập trình Toàn diện
url: /vi/java/document-rendering/register-warning-callback-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đăng ký Callback Cảnh báo trong Java – Hướng dẫn Lập trình Toàn diện

Bạn đã bao giờ cần **đăng ký callback cảnh báo** trong Java nhưng không chắc cách bắt các vấn đề phông chữ bị thiếu? Bạn không cô đơn. Khi tài liệu phụ thuộc vào các phông chữ tùy chỉnh, việc thay thế phông chữ âm thầm có thể làm hỏng bố cục, và cách duy nhất đáng tin cậy để phát hiện chúng là lắng nghe các cảnh báo. Trong hướng dẫn này, chúng ta sẽ đi qua một giải pháp thực tế không chỉ **đăng ký callback cảnh báo** mà còn **phát hiện phông chữ thiếu** trước khi chúng âm thầm phá vỡ đầu ra của bạn.

Thực tế là—Aspose.Words for Java cung cấp một API sạch sẽ cho việc quản lý phông chữ, nhưng nhiều nhà phát triển bỏ qua bước callback cảnh báo và cuối cùng có các PDF không giống gì file Word gốc. Khi kết thúc tutorial, bạn sẽ có một đoạn mã sẵn sàng chạy, hiểu vì sao mỗi dòng quan trọng, và biết cách mở rộng cách tiếp cận cho các kịch bản phức tạp hơn.

## Bạn sẽ học được gì

Trong vài phần tiếp theo, chúng ta sẽ đề cập tới:

* Cách tạo `LoadOptions` và bật xử lý phông chữ tùy chỉnh.  
* Cách **đăng ký callback cảnh báo** để bắt các sự kiện `FONT_SUBSTITUTION`.  
* Cách **phát hiện phông chữ thiếu** và ghi lại thông tin hữu ích để gỡ lỗi.  
* Một ví dụ Java hoàn chỉnh, có thể chạy được mà bạn có thể dán vào IDE ngay hôm nay.

Không cần thư viện bên ngoài nào ngoài Aspose.Words, và mã hoạt động với Java 8+ và Aspose.Words 23.9 (hoặc mới hơn). Nếu bạn đã có một dự án tải các file `.docx`, bạn chỉ cần thêm một vài dòng—không cần tái cấu trúc lớn.

## Yêu cầu trước

* Java Development Kit (JDK) 8 trở lên.  
* Aspose.Words for Java (tải từ trang chính thức hoặc thêm dependency Maven).  
* Quyền truy cập vào thư mục chứa tài liệu Word bạn muốn tải.  
* Kiến thức cơ bản về lambda Java hoặc lớp ẩn danh (chúng ta sẽ dùng lớp ẩn danh để rõ ràng).

Nếu bất kỳ mục nào trên đây còn lạ, đừng hoảng—mỗi bước đều được giải thích bằng tiếng Anh đơn giản, và các chú thích trong mã sẽ lấp đầy khoảng trống.

---

## Bước 1: Tạo Load Options và Bật Xử lý Phông chữ Tùy chỉnh

Trước khi chúng ta có thể lắng nghe các cảnh báo liên quan đến phông chữ, chúng ta cần một thể hiện `LoadOptions` để nói với Aspose.Words sử dụng `FontSettings` của riêng mình. Hãy nghĩ `LoadOptions` như “túi cài đặt” bạn đưa cho bộ tải tài liệu.

```java
// Step 1: Create load options and enable custom font handling
LoadOptions loadOptions = new LoadOptions();               // Holds loading configuration
loadOptions.setFontSettings(new FontSettings());           // Attach a fresh FontSettings object
```

**Tại sao điều này quan trọng:**  
`FontSettings` là cổng vào mọi thứ thư viện làm với phông chữ—đường dẫn tìm kiếm, quy tắc thay thế, và quan trọng nhất, callback cảnh báo. Bằng cách tạo một đối tượng `FontSettings` riêng, bạn có toàn quyền kiểm soát cách xử lý phông chữ thiếu thay vì dựa vào giá trị mặc định của thư viện.

> **Mẹo chuyên nghiệp:** Nếu ứng dụng của bạn đã cung cấp một `FontSettings` chung (ví dụ, cho việc chuyển đổi PDF), hãy tái sử dụng nó ở đây để giữ cho việc phân giải phông chữ nhất quán trong toàn bộ pipeline.

---

## Bước 2: Đăng ký Callback Cảnh báo để Phát hiện Phông chữ Thiếu

Bây giờ là phần cốt lõi của tutorial: chúng ta **đăng ký callback cảnh báo** trên `FontSettings` vừa tạo. Callback nhận một đối tượng `WarningInfo` cho mỗi cảnh báo được phát sinh trong quá trình tải tài liệu.

```java
// Step 2: Register a warning callback to be notified of font substitutions
loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter only font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // This is where we **detect missing fonts**
            System.out.println("Substituted: " + info.getDescription());
        }
    }
});
```

**Giải thích logic:**

* `setWarningCallback` gắn listener tùy chỉnh của chúng ta.  
* Trong `warning(WarningInfo info)`, chúng ta kiểm tra `info.getWarningType()`.  
* Khi kiểu bằng `WarningType.FONT_SUBSTITUTION`, thư viện đang thông báo rằng không tìm thấy phông chữ gốc và phải thay thế bằng một phông khác.  
* `info.getDescription()` chứa thông điệp dễ đọc như *“Font 'MyCustomFont' not found, substituted with 'Arial'.”*  

Bằng cách in ra mô tả đó, chúng ta **phát hiện phông chữ thiếu** ngay trong giai đoạn tải, cho phép bạn ghi log, cảnh báo, hoặc thậm chí hủy thao tác nếu việc thay thế không chấp nhận được.

> **Tại sao không chỉ bắt ngoại lệ?**  
> Phông chữ thiếu hiếm khi ném ngoại lệ; chúng phát ra cảnh báo thay vào đó. Nếu không có callback, những cảnh báo ấy sẽ biến mất vào hư không, và bạn sẽ không bao giờ biết độ trung thực hình ảnh của tài liệu đã bị ảnh hưởng.

### Tùy chọn: Sử dụng Lambda (Java 8+)

Nếu bạn thích cú pháp ngắn gọn hơn, cùng một callback có thể được biểu diễn bằng lambda:

```java
loadOptions.getFontSettings().setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        System.out.println("Substituted: " + info.getDescription());
    }
});
```

Cả hai cách đều đạt cùng mục tiêu—chọn phong cách phù hợp với codebase của bạn.

---

## Bước 3: Tải Tài liệu với Các Tuỳ chọn Đã Cấu hình

Với callback đã sẵn sàng, bước cuối cùng là tải tài liệu. Hàm khởi tạo `Document` nhận đường dẫn và `LoadOptions` mà chúng ta đã chuẩn bị.

```java
// Step 3: Load the document using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Điều gì xảy ra phía sau?**  
Trong lời gọi này, Aspose.Words phân tích file `.docx`, phân giải mỗi phông chữ được tham chiếu, và kích hoạt callback cảnh báo của chúng ta cho bất kỳ phông chữ nào bị thiếu. Nếu mọi thứ có mặt, bạn sẽ không thấy bất kỳ đầu ra nào trên console; ngược lại, bạn sẽ nhận được các dòng như:

```
Substituted: Font 'OpenSans-Regular' not found, substituted with 'Times New Roman'.
Substituted: Font 'CustomIconFont' not found, substituted with 'Arial'.
```

Đầu ra đó là bằng chứng cụ thể rằng chúng ta **đã đăng ký callback cảnh báo** thành công và **đang phát hiện phông chữ thiếu**.

---

## Ví dụ Hoạt động Đầy đủ

Dưới đây là chương trình Java tự chứa, hoàn chỉnh mà bạn có thể sao chép‑dán vào file `Main.java` và chạy. Đảm bảo JAR Aspose.Words đã có trong classpath.

```java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions and enable custom font handling
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setFontSettings(new FontSettings());

            // 2️⃣ Register warning callback to detect missing fonts
            loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("Substituted: " + info.getDescription());
                    }
                }
            });

            // 3️⃣ Load the document using the configured options
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // Optional: Save as PDF to verify visual fidelity
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Kết quả mong đợi** (khi phông chữ bị thiếu):

```
Substituted: Font 'MyCustomFont' not found, substituted with 'Arial'.
Document loaded and saved successfully.
```

Nếu tất cả phông chữ đều có, bạn sẽ chỉ thấy thông điệp thành công.

---

## Xử lý Các Trường hợp Cạnh và Những Cạm bẫy Thường gặp

| Tình huống | Điều cần chú ý | Giải pháp đề xuất |
|-----------|-------------------|---------------|
| **Nhiều phông chữ thiếu** | Callback có thể được gọi nhiều lần, làm rối log. | Gom lại các thông điệp hoặc ghi vào file để phân tích sau. |
| **Ảnh hưởng tới hiệu năng** | Ghi log quá mức có thể làm chậm tải hàng loạt lớn. | Lọc cảnh báo theo mức độ nghiêm trọng hoặc tắt output console trong môi trường production. |
| **Thư mục phông chữ tùy chỉnh** | `FontSettings` mặc định chỉ dùng phông hệ thống. | Gọi `fontSettings.setFontsFolder("path/to/custom/fonts", true);` trước khi đăng ký callback. |
| **Thay thế âm thầm** | Một số phông có thể được thay thế mà không có cảnh báo nếu chúng được coi là tương tự. | Đặt `fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());` và tinh chỉnh quy tắc thay thế. |

Bằng cách dự đoán các kịch bản này, bạn sẽ giữ cho ứng dụng vững chắc và log có ý nghĩa.

---

## Mở rộng Giải pháp

Bây giờ bạn đã biết cách **đăng ký callback cảnh báo** và **phát hiện phông chữ thiếu**, bạn có thể muốn:

* **Hủy tải** khi một phông chữ quan trọng bị thiếu (ném ngoại lệ trong callback).  
* **Thu thập tên phông chữ thiếu** vào một `Set<String>` để tạo báo cáo tổng hợp sau khi tài liệu được tải.  
* **Tích hợp với hệ thống giám sát** (ví dụ, gửi cảnh báo tới Slack hoặc Azure Monitor).  

Tất cả các mở rộng này đều dựa trên cùng một mẫu callback mà chúng ta đã trình bày.

---

## Kết luận

Chúng ta đã đi qua một ví dụ hoàn chỉnh, sẵn sàng cho môi trường production, cho thấy cách **đăng ký callback cảnh báo** trong Java, giúp **phát hiện phông chữ thiếu** ngay khi tài liệu được tải. Những điểm chính cần nhớ là:

* Tạo `LoadOptions` với `FontSettings` tùy chỉnh.  
* Gắn một `IWarningCallback` lọc các cảnh báo `FONT_SUBSTITUTION`.  
* Tải tài liệu bằng các tuỳ chọn đó và phản hồi lại bất kỳ sự kiện phông chữ thiếu nào.

Với kiến thức này, bạn có thể bảo vệ các pipeline xử lý tài liệu, đảm bảo độ trung thực hình ảnh, và cung cấp chẩn đoán rõ ràng cho người dùng cuối.

Sẵn sàng cho bước tiếp theo? Hãy thử thêm thư mục phông chữ, thử nghiệm các chính sách thay thế khác nhau, hoặc kết nối callback với framework logging hiện có. Khả năng mở rộng chỉ bị giới hạn bởi thư viện phông chữ bạn quản lý.

Chúc lập trình vui vẻ, và mong các PDF của bạn luôn hiển thị đúng như mong đợi!

## Các Tutorial Liên quan

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}