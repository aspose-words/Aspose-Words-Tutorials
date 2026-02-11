---
category: general
date: 2026-02-10
description: Cách xử lý phông chữ trong Java bằng Aspose.Words. Tìm hiểu cảnh báo
  thay thế phông chữ, các callback của LoadOptions và cách xử lý phông chữ thiếu trong
  một vài bước.
draft: false
keywords:
- how to handle fonts
- font substitution warnings
- Aspose.Words Java
- LoadOptions warning callback
- MissingFont.docx handling
language: vi
og_description: Cách xử lý phông chữ trong Java với Aspose.Words. Hướng dẫn này cho
  bạn thấy cách thực hiện thay thế phông chữ từng bước, các callback cảnh báo và quản
  lý phông chữ thiếu.
og_title: Cách Xử Lý Phông Chữ trong Java – Hướng Dẫn Đầy Đủ Aspose.Words
tags:
- Java
- Aspose.Words
- Document Processing
title: Cách Xử Lý Phông Chữ trong Java với Aspose.Words – Hướng Dẫn Toàn Diện
url: /vi/java/document-rendering/how-to-handle-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Xử Lý Phông Chữ trong Java – Hướng Dẫn Toàn Diện

Bạn đã bao giờ tự hỏi **cách xử lý phông chữ** khi một tài liệu Word tham chiếu tới một kiểu chữ mà không được cài đặt trên máy chủ của bạn chưa? Đó là một tình huống khiến nhiều nhà phát triển gặp khó khăn, đặc biệt khi bạn tự động tạo hoặc chuyển đổi tài liệu bằng Aspose.Words. Tin tốt là gì? Bạn có thể bắt mọi sự kiện thay thế phông chữ và phản hồi lại—không cần đoán mò.

Trong tutorial này chúng ta sẽ đi qua một ví dụ thực tế cho thấy **cách xử lý phông chữ** bằng Aspose.Words for Java. Chúng ta sẽ gắn một warning callback, lọc ra chỉ các cảnh báo thay thế phông chữ, và in ra một thông báo thân thiện cho mỗi phông chữ bị thiếu. Khi kết thúc, bạn sẽ hiểu tại sao điều này quan trọng, cách triển khai nó một cách sạch sẽ, và những gì sẽ xảy ra khi mã chạy.

> **Bạn sẽ nhận được:** một lớp Java hoàn chỉnh, sẵn sàng chạy, giải thích từng dòng code, mẹo cho môi trường production, và cách nhanh chóng kiểm tra kết quả.

---

## Yêu Cầu Trước

Trước khi bắt đầu, hãy chắc chắn bạn có:

- **Java 8** (hoặc mới hơn) đã được cài đặt trên máy của bạn.  
- **Aspose.Words for Java** JAR (phiên bản mới nhất tính đến 2026‑02, ví dụ `aspose-words-23.11.jar`).  
- Một tài liệu mẫu (`MissingFont.docx`) tham chiếu tới một phông chữ bạn chưa cài đặt.  
- Môi trường phát triển (IntelliJ IDEA, Eclipse, hoặc thậm chí một trình soạn thảo văn bản đơn giản + dòng lệnh).

Không cần bất kỳ framework bổ sung nào—chỉ cần Java thuần và JAR Aspose.Words.

![Diagram showing how to handle fonts in Java with Aspose.Words](https://example.com/handle-fonts-diagram.png "how to handle fonts diagram")
*Image alt text: how to handle fonts diagram*

---

## Bước 1 – Thiết Lập Warning Callback (cốt lõi của **cách xử lý phông chữ**)

Khi Aspose.Words tải một tài liệu, nó sẽ tạo ra một loạt các đối tượng `WarningInfo` cho bất kỳ điều gì không hoàn hảo. Bằng cách gắn một `IWarningCallback`, bạn có thể chặn những cảnh báo này ngay trong thời gian thực.

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions and register a warning callback.
        LoadOptions loadOptions = new LoadOptions();

        // The callback will be invoked for every warning Aspose.Words emits.
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 2️⃣ Filter for FONT_SUBSTITUTION warnings only.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
                // Other warning types are ignored – you could log them here if you wish.
            }
        });
```

**Tại sao điều này quan trọng:**  
Nếu bạn bỏ qua callback, Aspose.Words sẽ âm thầm thay thế các phông chữ thiếu bằng phông mặc định, và bạn sẽ không bao giờ biết phông nào đã bị thiếu. Khi xử lý cảnh báo, bạn có được cái nhìn rõ ràng và có thể quyết định nhúng phông dự phòng, ghi log vấn đề, hoặc thậm chí hủy thao tác.

---

## Bước 2 – Tải Tài Liệu Bằng `LoadOptions` Đã Cấu Hình

Bây giờ callback đã sẵn sàng, chúng ta chỉ cần tải tài liệu. Đối tượng `LoadOptions` mà chúng ta tạo ở trên sẽ được truyền trực tiếp vào hàm khởi tạo `Document`.

```java
        // 3️⃣ Load a document that may contain missing fonts.
        // Replace the path with the actual location of your test file.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // At this point the warning callback runs automatically.
        // Any font substitution will be printed to the console.
```

**Bạn có thể mong đợi gì:**  
Khi `MissingFont.docx` tham chiếu, ví dụ, *Comic Sans MS* nhưng máy chủ chỉ có *Arial*, callback sẽ in ra một thông báo như sau:

```
Substituted font: Font 'Comic Sans MS' was substituted with 'Arial'.
```

Nếu tài liệu tải lên mà không có phông chữ nào bị thiếu, sẽ không có gì được in—đúng như bạn muốn khi **cách xử lý phông chữ** một cách suôn sẻ.

---

## Bước 3 – (Tùy Chọn) Kiểm Tra Bảng Phông Chữ Của Tài Liệu

Đôi khi bạn cần kiểm tra các phông chữ thực tế mà tài liệu sử dụng sau khi tải. Aspose.Words làm việc này rất dễ dàng.

```java
        // Optional: List all fonts the document thinks it has.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Khi nào nên dùng:**  
Nếu bạn đang xây dựng một bộ xử lý batch phải báo cáo các phông chữ thiếu trước khi xuất PDF, việc in ra bảng phông chữ sẽ cung cấp một bước kiểm tra cuối cùng.

---

## Ví Dụ Đầy Đủ, Có Thể Chạy Ngay

Kết hợp tất cả lại, đây là lớp hoàn chỉnh bạn có thể sao chép‑dán vào `FontSubstitutionDemo.java` và chạy:

```java
import com.aspose.words.*;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1 – Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Handle only font‑substitution warnings.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Substituted font: " + info.getDescription());
                }
            }
        });

        // Step 2 – Load the document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // Step 3 – (Optional) List the fonts the document finally uses.
        FontInfoCollection fonts = document.getFontInfos();
        System.out.println("\n--- Fonts used in the document ---");
        for (FontInfo font : fonts) {
            System.out.println(font.getFullName());
        }
    }
}
```

**Chạy mã:**  

```bash
javac -cp "aspose-words-23.11.jar" FontSubstitutionDemo.java
java -cp ".:aspose-words-23.11.jar" FontSubstitutionDemo
```

Bạn sẽ thấy các thông báo thay thế phông chữ, tiếp theo là danh sách phông chữ cuối cùng.

---

## Các Câu Hỏi Thường Gặp & Trường Hợp Cạnh

### Nếu tôi muốn tự thay thế phông chữ thì sao?

Callback chỉ thông báo *phông nào* đã bị thay thế. Nếu bạn muốn ép buộc một phông dự phòng cụ thể, bạn có thể sử dụng `FontSettings`:

```java
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings() {{
    getTableSubstitution().addSubstitutes("MissingFont", "Arial");
}});
loadOptions.setFontSettings(fontSettings);
```

Bây giờ mọi lần xuất hiện “MissingFont” sẽ được thay bằng “Arial” trước khi tài liệu được tải.

### Điều này có hoạt động khi lưu ra PDF không?

Chắc chắn rồi. Callback tương tự sẽ được kích hoạt trong `document.save("out.pdf")` nếu bộ render PDF cũng cần thay thế phông. Chỉ cần giữ nguyên `LoadOptions` hoặc gắn một callback mới cho `PdfSaveOptions`.

### Nó hoạt động như thế nào trong môi trường đa luồng?

`LoadOptions` **không** an toàn với đa luồng, vì vậy hãy tạo một thể hiện mới cho mỗi luồng. Callback tự nó có thể không có trạng thái (như ví dụ) hoặc bạn có thể tiêm một logger có khả năng nhận biết luồng.

### Nếu phông chữ thiếu là phông chữ doanh nghiệp tùy chỉnh thì sao?

Bạn thường sẽ nhúng phông đó vào thư mục phông của máy chủ và chỉ định cho Aspose.Words bằng `FontSettings.setFontsFolder("path/to/fonts", true)`. Khi đó callback sẽ ngừng kích hoạt cho phông đó vì nó không còn bị thiếu nữa.

---

## Mẹo Chuyên Gia Cho Xử Lý Phông Chữ Sẵn Sàng cho Production

- **Ghi log, không chỉ `System.out.println`** – sử dụng framework logging thích hợp (SLF4J, Log4j) để có thể thu thập cảnh báo trong hệ thống giám sát.  
- **Cache việc tra cứu phông** – nếu bạn xử lý hàng ngàn tài liệu, tránh việc quét lại thư mục phông của hệ điều hành liên tục. Tải phông một lần vào một đối tượng `FontSettings` và tái sử dụng.  
- **Fail fast khi phông chữ quan trọng bị thiếu** – bạn có thể ném ngoại lệ trong callback nếu một phông chữ cụ thể là bắt buộc cho tuân thủ thương hiệu.  
- **Kiểm thử với đa dạng tài liệu** – bao gồm PDF, DOCX và DOC; mỗi định dạng có thể kích hoạt các loại cảnh báo khác nhau.  

---

## Kết Luận

Chúng ta đã bao quát **cách xử lý phông chữ** trong Java bằng Aspose.Words từ đầu đến cuối:

1. Gắn một `IWarningCallback` để bắt các cảnh báo thay thế phông.  
2. Tải tài liệu với `LoadOptions` để callback tự động chạy.  
3. (Tùy chọn) Kiểm tra danh sách phông cuối cùng để xác nhận kết quả.  

Bằng cách làm theo các bước này, bạn sẽ có được cái nhìn toàn diện về các phông chữ bị thiếu, có thể thực thi chính sách phông công ty, và tránh những thay thế âm thầm có thể làm hỏng giao diện PDF hoặc Word được tạo ra.

Sẵn sàng cho thử thách tiếp theo? Hãy thử thay đổi callback để ghi lại *tất cả* cảnh báo, khám phá `FontSettings` cho các quy tắc thay thế tùy chỉnh, hoặc tích hợp logic này vào một microservice Spring‑Boot xử lý tài liệu trực tiếp.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng kiểu chữ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}