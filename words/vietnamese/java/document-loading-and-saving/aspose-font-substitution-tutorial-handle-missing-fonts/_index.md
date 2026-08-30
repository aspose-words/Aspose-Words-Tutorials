---
category: general
date: 2026-05-04
description: Hướng dẫn thay thế phông chữ Aspose cho thấy cách xử lý các phông chữ
  thiếu trong Java bằng các callback cảnh báo và LoadOptions để tải tài liệu một cách
  đáng tin cậy.
draft: false
keywords:
- aspose font substitution tutorial
- handle missing fonts
- Aspose.Words font warning callback
- Java LoadOptions warning handling
- missing font detection Aspose
language: vi
og_description: Hướng dẫn thay thế phông chữ của Aspose giải thích cách xử lý các
  phông chữ thiếu trong Java, ghi lại các sự kiện thay thế và giữ cho tài liệu của
  bạn luôn hiển thị đúng.
og_title: Hướng dẫn Thay thế Phông chữ Aspose – Xử lý Phông chữ Thiếu
tags:
- Aspose.Words
- Java
- Font Management
title: Hướng dẫn Thay thế Phông chữ Aspose – Xử lý Phông chữ thiếu
url: /vi/java/document-loading-and-saving/aspose-font-substitution-tutorial-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hướng dẫn Thay thế Phông chữ Aspose – Xử lý Phông chữ Thiếu

Bạn đã bao giờ cần một **hướng dẫn thay thế phông chữ Aspose** vì một tệp DOCX bạn tải lên đột nhiên hiển thị sai? Bạn không phải là người duy nhất—các phông chữ thiếu là nguồn gây lỗi tinh vi có thể biến một báo cáo được định dạng hoàn hảo thành một mớ hỗn độn. Tin tốt là Aspose.Words cung cấp cho bạn một cách sạch sẽ để **handle missing fonts** trước khi chúng phá vỡ bố cục của bạn.

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ Java hoàn chỉnh, sẵn sàng chạy, ghi lại các cảnh báo thay thế phông chữ, giải thích tại sao mỗi phần lại quan trọng, và cho bạn thấy cách xác minh kết quả. Khi kết thúc, bạn sẽ biết chính xác cách giữ cho tài liệu của mình luôn sắc nét ngay cả khi các kiểu chữ gốc không có trên máy.

## Những gì bạn sẽ học

- Cách đăng ký một `IWarningCallback` tùy chỉnh để lắng nghe các sự kiện `FONT_SUBSTITUTION`.  
- Tại sao việc sử dụng `LoadOptions` là cách tiếp cận được khuyến nghị cho việc xử lý phông chữ đáng tin cậy.  
- Các cách kiểm tra giải pháp với một tài liệu cố ý bị lỗi.  
- Những bẫy thường gặp (ví dụ: quên thiết lập callback) và cách khắc phục nhanh.  

**Yêu cầu trước**: Java 8+ đã được cài đặt, giấy phép Aspose.Words for Java hợp lệ (hoặc bản đánh giá miễn phí), và một IDE cơ bản như IntelliJ hoặc Eclipse. Không cần thư viện bên ngoài nào khác.

---

![Sơ đồ hướng dẫn thay thế phông chữ Aspose](https://example.com/images/font-substitution-diagram.png "Sơ đồ hướng dẫn thay thế phông chữ Aspose")

## Bước 1 – Định nghĩa Warning Callback để Ghi lại Các Lần Thay Thế  

Điều đầu tiên Aspose.Words làm khi không tìm thấy phông chữ được yêu cầu là kích hoạt một sự kiện `WarningInfo`. Bằng cách triển khai `IWarningCallback` bạn có thể ghi log, hiển thị, hoặc thậm chí hủy quá trình tải nếu muốn.

```java
// Step 1: Create a callback that prints font‑substitution warnings
class FontWarningCollector implements IWarningCallback {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
}
```

**Tại sao điều này quan trọng** – Nếu không có callback, bạn sẽ không bao giờ biết rằng Aspose đã thay thế *Arial* bằng *Liberation Sans* (hoặc bất kỳ phông thay thế nào khác). Sự thay thế im lặng này có thể gây ra dịch chuyển bố cục, đặc biệt trong các bảng hoặc bố cục đa cột.

---

## Bước 2 – Gắn Callback vào `LoadOptions`

`LoadOptions` là trung tâm điều khiển mọi thứ ảnh hưởng đến cách tài liệu được đọc. Khi gắn callback ở đây, bạn đảm bảo **bất kỳ** tài liệu nào được tải bằng các tùy chọn này sẽ kích hoạt logic cảnh báo của bạn.

```java
// Step 2: Wire the callback into LoadOptions
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new FontWarningCollector());
```

**Mẹo** – Nếu bạn dự định tải nhiều tài liệu trong một lô, hãy tái sử dụng cùng một thể hiện `LoadOptions`. Điều này giảm tải tạo đối tượng và giữ cho việc ghi log của bạn nhất quán.

---

## Bước 3 – Tải Tài liệu Có Thể Cần Thay Thế Phông chữ  

Bây giờ chúng ta thực sự đọc một tệp mà chúng ta biết thiếu phông chữ. Thay thế `YOUR_DIRECTORY` bằng thư mục chứa các tệp thử nghiệm của bạn.

```java
// Step 3: Load a document that deliberately references a missing font
String inputPath = "YOUR_DIRECTORY/missing-font.docx";
Document doc = new Document(inputPath, loadOptions);
```

Khi bộ tải gặp một glyph không thể hiển thị, callback từ **Bước 1** sẽ in một thông báo thân thiện ra console. Ví dụ:

```
Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

**Trường hợp đặc biệt** – Nếu tài liệu chứa phông chữ *embedded*, Aspose sẽ sử dụng chúng trước và bỏ qua cảnh báo. Đây là hành vi mong đợi; bạn chỉ thấy cảnh báo cho những phông chữ thực sự thiếu.

---

## Bước 4 – Lưu Tài liệu (Giờ đã có Phông chữ Thay Thế)

Sau khi quá trình tải hoàn tất, Aspose đã tự động thay thế các phông chữ thiếu bên trong. Lưu tài liệu sẽ giữ lại việc thay thế, vì vậy đầu ra sẽ trông giống hệt như những gì bạn thấy trên console.

```java
// Step 4: Persist the document – the fonts are already substituted if needed
String outputPath = "YOUR_DIRECTORY/loaded.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Mở `loaded.docx` trong Word hoặc LibreOffice và bạn sẽ thấy bố cục không thay đổi, mặc dù phông chữ gốc không được cài đặt trên máy của bạn.

---

## Bước 5 – Xác Minh Kết Quả Bằng Chương Trình (Tùy chọn)

Nếu bạn muốn chắc chắn rằng không có sự thay thế bất ngờ nào lọt qua, bạn có thể truy vấn bảng phông chữ của tài liệu sau khi tải.

```java
// Optional: List all fonts actually used in the saved document
for (FontInfo fontInfo : doc.getFontInfos()) {
    System.out.println("Used font: " + fontInfo.getFontName());
}
```

Kết quả nên chứa phông chữ thay thế (ví dụ: *Arial*) thay vì phông chữ bị thiếu. Điều này hữu ích cho các pipeline tự động nơi bạn cần đảm bảo PDF hoặc DOCX cuối cùng đáp ứng yêu cầu thương hiệu.

---

## Mẹo Chuyên Gia & Những Bẫy Thường Gặp

- **Mẹo chuyên gia:** Đặt `loadOptions.setFontSettings(new FontSettings())` nếu bạn cần chỉ định cho Aspose một thư mục phông chữ tùy chỉnh trước khi tải. Điều này giảm số lần thay thế.
- **Cẩn thận với:** Quên gọi `setWarningCallback`. Mã vẫn chạy, nhưng bạn sẽ bỏ lỡ các thông điệp chẩn đoán quan trọng.
- **Lưu ý về hiệu năng:** Tải các tài liệu lớn với nhiều phông chữ thiếu có thể tạo ra rất nhiều cảnh báo. Hãy cân nhắc giảm tần suất xuất hoặc ghi vào file log thay vì `System.out`.
- **Nếu muốn hủy khi có thay thế?** Thay lời gọi `System.out.println` bằng `throw new RuntimeException(info.getDescription())` trong callback. Điều này buộc quá trình tải thất bại, hữu ích cho các kịch bản tuân thủ nghiêm ngặt.

---

## Câu Hỏi Thường Gặp

**Hỏi:** Điều này có hoạt động với các định dạng PDF hoặc hình ảnh không?  
**Đáp:** Callback cảnh báo chỉ áp dụng cho giai đoạn tải của các định dạng xử lý Word (`.docx`, `.doc`, `.rtf`, v.v.). Việc render PDF sử dụng pipeline khác, nhưng bạn vẫn có thể bắt các cảnh báo liên quan đến phông chữ qua `PdfLoadOptions`.

**Hỏi:** Tôi có thể thay thế một phông chữ cụ thể bằng một phông chữ khác mà tôi chọn không?  
**Đáp:** Có. Tạo một đối tượng `FontSettings`, gọi `fontSettings.getSubstitutionSettings().getTableSubstitutes().addSubstitutes("MissingFont", "MyPreferredFont")`, và gán nó cho `loadOptions.setFontSettings(fontSettings)`.

**Hỏi:** Callback có an toàn với đa luồng không?  
**Đáp:** Triển khai mặc định không được đồng bộ hoá. Nếu bạn tải tài liệu song song, hãy đảm bảo callback của bạn xử lý truy cập đồng thời (ví dụ: dùng `ConcurrentLinkedQueue` để ghi log).

---

## Kết Luận

Bạn đã có một **hướng dẫn thay thế phông chữ Aspose** đầy đủ, cho thấy cách **handle missing fonts** một cách khéo léo trong Java. Bằng cách định nghĩa một `IWarningCallback` tùy chỉnh, gắn nó vào `LoadOptions`, và lưu tài liệu, bạn giữ cho đầu ra nhất quán bất kể phông chữ nào được cài đặt trên máy chủ.

Từ đây bạn có thể khám phá:

- Bảng thay thế phông chữ tùy chỉnh cho các thay thế tuân thủ thương hiệu.  
- Tích hợp logger cảnh báo với SLF4J hoặc Log4j cho chẩn đoán cấp sản xuất.  
- Mở rộng callback để thu thập thống kê qua một lô tài liệu.

Hãy thử nghiệm, điều chỉnh các phông chữ thay thế, và để tài liệu của bạn luôn đẹp mắt ngay cả khi các kiểu chữ gốc biến mất. Chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}