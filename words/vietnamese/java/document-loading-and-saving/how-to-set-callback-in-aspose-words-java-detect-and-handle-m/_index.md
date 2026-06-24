---
category: general
date: 2026-06-20
description: Cách thiết lập callback trong Aspose.Words Java để phát hiện phông chữ
  thiếu và tùy chỉnh quá trình tải tài liệu. Tìm hiểu cách xử lý cảnh báo thay thế
  phông chữ từng bước.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: vi
og_description: Cách thiết lập callback trong Aspose.Words Java để phát hiện phông
  chữ thiếu, xử lý thay thế và tùy chỉnh việc tải tài liệu. Hướng dẫn đầy đủ kèm mã.
og_title: cách thiết lập callback – Phát hiện phông chữ thiếu trong Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Cách thiết lập callback trong Aspose.Words Java – Phát hiện và Xử lý phông
  chữ thiếu
url: /vi/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cách thiết lập callback trong Aspose.Words Java – Phát hiện và Xử lý Phông chữ Thiếu

Bạn đã bao giờ tự hỏi **cách thiết lập callback** trong Aspose.Words Java để có thể phát hiện phông chữ thiếu trước khi chúng làm hỏng PDF hoặc DOCX của bạn chưa? Bạn không phải là người duy nhất. Cảnh báo phông chữ thiếu có thể âm thầm làm hỏng bố cục, và nếu không có một callback cảnh báo thích hợp, bạn có thể không nhận ra cho đến khi tài liệu cuối cùng trông sai lệch.  

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy mà **phát hiện phông chữ thiếu**, **xử lý phông chữ thiếu** một cách nhẹ nhàng, và chỉ cho bạn cách **tùy chỉnh việc tải tài liệu** bằng một callback cảnh báo. Khi kết thúc, bạn sẽ có một lớp Java độc lập mà bạn có thể chèn vào bất kỳ dự án nào—không cần tìm kiếm tài liệu bổ sung.

## Những gì bạn cần

- Java 8 hoặc mới hơn (mã cũng hoạt động với Java 11+).  
- Thư viện Aspose.Words for Java (phiên bản 23.9 trở lên).  
- Một tệp DOCX tham chiếu tới phông chữ bạn chưa cài đặt (ví dụ: phông chữ doanh nghiệp tùy chỉnh).  

Nếu bạn chưa thêm Aspose.Words vào dự án Maven của mình, chỉ cần bao gồm:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Thế là xong—không cần plugin bổ sung, không có phụ thuộc native.

---

## Bước 1: Hiểu cơ chế WarningCallback

**warning callback** là cách Aspose.Words thông báo cho bạn khi có điều gì đó bất ngờ xảy ra trong quá trình tải hoặc lưu tài liệu. Bằng cách triển khai `IWarningCallback` bạn sẽ có toàn quyền kiểm soát những gì được ghi log, bỏ qua, hoặc thậm chí chuyển thành ngoại lệ.

> **Tại sao điều này quan trọng:**  
> Khi một phông chữ bị thiếu, Aspose sẽ thay thế bằng một phông chữ dự phòng. Kết quả hiển thị có thể khác biệt đáng kể, đặc biệt đối với các PDF có thương hiệu mạnh. Bằng cách bắt `WarningType.FONT_SUBSTITUTION`, bạn có thể ghi lại tên phông chữ chính xác, quyết định có nên dừng lại hay không, hoặc thay thế bằng phông chữ tùy chỉnh của riêng bạn một cách lập trình.

---

## Bước 2: Tạo một thể hiện LoadOptions

`LoadOptions` là điểm vào để tùy chỉnh việc tải tài liệu. Bạn sẽ gắn callback vào đối tượng này trước khi thực sự tải tệp.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Ở thời điểm này, `loadOptions` chỉ là một container trống—chưa có gì xảy ra. Phép màu thực sự bắt đầu khi chúng ta gắn callback vào.

---

## Bước 3: Triển khai và gắn Callback

Dưới đây là một lớp ẩn danh gọn gàng triển khai `IWarningCallback`. Nó sẽ in một dòng thân thiện ra console mỗi khi xảy ra việc thay thế phông chữ.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Mẹo chuyên nghiệp:** Nếu bạn muốn **xử lý phông chữ thiếu** bằng cách cung cấp một phông chữ thay thế, bạn cũng có thể thiết lập `FontSettings` trên `LoadOptions` và ánh xạ các phông chữ thiếu tới một phông chữ dự phòng đã biết.

---

## Bước 4: Tải tài liệu với các tùy chọn tùy chỉnh của bạn

Bây giờ callback đã được kết nối, hãy tải tài liệu. Nếu tệp tham chiếu tới một phông chữ bạn không có, bạn sẽ thấy cảnh báo được in ra.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Khi chạy chương trình, console có thể hiển thị:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Dòng này chứng minh bạn đã **phát hiện phông chữ thiếu** thành công và hiện đang ở vị trí để **xử lý phông chữ thiếu** theo cách bạn muốn.

---

## Bước 5: Tùy chọn – Thay thế phông chữ thiếu bằng một phông chữ đã biết

Nếu bạn muốn tự động thay thế bất kỳ phông chữ thiếu nào bằng, ví dụ, `Times New Roman`, bạn có thể thêm một đối tượng `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Bây giờ tài liệu sẽ được tải, và mọi tham chiếu tới `MyCustomFont` sẽ được thay thế một cách im lặng bằng `Times New Roman`. Console vẫn sẽ thông báo những gì đã được thay thế, giúp bạn luôn nắm được tình hình.

---

## Ví dụ Hoạt động đầy đủ

Dưới đây là một lớp Java duy nhất tích hợp tất cả các bước ở trên. Sao chép‑dán vào IDE, điều chỉnh `docPath`, và chạy.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Kết quả mong đợi**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Bạn giờ đã có một cách tái tạo để **phát hiện phông chữ thiếu**, **xử lý phông chữ thiếu**, và **tùy chỉnh việc tải tài liệu**—tất cả nhờ việc học **cách thiết lập callback** một cách chính xác.

---

## Câu hỏi thường gặp

### Nếu tôi muốn chương trình dừng tải khi phát hiện phông chữ thiếu thì sao?

Ném một ngoại lệ bên trong phương thức `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Khối `catch` ở cuối sẽ bắt ngoại lệ này, và bạn có thể quyết định cách ghi log hoặc thông báo cho người dùng.

### Điều này có hoạt động với PDF được tạo từ DOCX không?

Chắc chắn rồi. Callback được kích hoạt trong giai đoạn **loading**, giống hệt cho mọi định dạng đầu ra (`save` sang PDF, DOCX, HTML, v.v.). Miễn là bạn tải tài liệu nguồn bằng cùng một `LoadOptions`, bạn sẽ bắt được các phông chữ thiếu trước khi chúng ảnh hưởng đến PDF cuối cùng.

### Tôi có thể bắt các loại cảnh báo khác (ví dụ: chuyển đổi hình ảnh) không?

Có—`WarningInfo.getWarningType()` có thể so sánh với các enum khác như `WarningType.IMAGE_CONVERSION`. Chỉ cần thêm các nhánh `if` nữa trong callback.

### Có ảnh hưởng đến hiệu năng không?

Rất ít. Callback chạy đồng bộ trong quá trình tải, và các kiểm tra bổ sung nhẹ. Nếu bạn đang tải hàng ngàn tài liệu, có thể muốn tắt cảnh báo trong môi trường production bằng cách đặt `loadOptions.setWarningCallback(null);`.

---

## Tổng quan hình ảnh

![how to set callback example in Aspose.Words Java](https://example.com/images/callback-diagram.png "how to set callback")

*Biểu đồ minh họa luồng: `LoadOptions` → `IWarningCallback` → Tải tài liệu → Xử lý thay thế phông chữ.*

---

## Tổng kết

Chúng ta đã đề cập **cách thiết lập callback** trong Aspose.Words Java, trình bày **phát hiện phông chữ thiếu**, chỉ ra các cách thực tế để **xử lý phông chữ thiếu**, và giải thích cách **tùy chỉnh việc tải tài liệu** bằng `LoadOptions`.  

Với kiến thức này, bạn có thể bảo vệ quy trình tài liệu của mình khỏi các lần thay thế phông chữ im lặng, giữ nguyên thương hiệu, và cung cấp cho người dùng phản hồi rõ ràng khi có sự cố xảy ra.

### Tiếp theo là gì?

- Khám phá **bảng thay thế phông chữ** để ánh xạ hàng loạt các phông chữ thiếu.  
- Kết hợp callback này với **kiểm tra tài liệu** để thực thi các hướng dẫn phong cách.  
- Thử **callback cảnh báo tùy chỉnh** ghi vào tệp log hoặc hệ thống giám sát thay vì `System.out`.  

Hãy tự do thử nghiệm, và cho chúng tôi biết bạn đã tùy chỉnh callback như thế nào cho dự án của mình. Chúc lập trình vui!

---

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}