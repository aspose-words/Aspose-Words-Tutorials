---
category: general
date: 2026-04-28
description: Tạo tài liệu PDF UA bằng Aspose.Words cho Java. Tìm hiểu cách tải docx
  với chế độ khôi phục, xuất các phương trình sang LaTeX, lưu markdown từ Word và
  khôi phục các phông chữ bị thiếu.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: vi
og_description: Tạo tài liệu PDF UA với Aspose.Words cho Java. Hướng dẫn chi tiết
  từng bước bao gồm tải khôi phục, xuất LaTeX, lưu Markdown và khôi phục phông chữ
  thiếu.
og_title: Tạo tài liệu PDF UA – Hướng dẫn Java toàn diện
tags:
- Aspose.Words
- Java
- PDF/UA
title: Tạo tài liệu PDF UA bằng Aspose.Words – Hướng dẫn Java đầy đủ
url: /vi/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Tài liệu PDF UA – Hướng dẫn Java đầy đủ

Cần **tạo tài liệu PDF UA** từ một tệp Word trong khi xử lý nội dung bị hỏng? Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn cách tải DOCX với chế độ khôi phục, xuất phương trình sang LaTeX, lưu Markdown từ Word và truy xuất các phông chữ bị thiếu — tất cả đều sử dụng Aspose.Words cho Java.  

Nếu bạn từng nhìn chằm chằm vào một tệp .docx bị hỏng và tự hỏi tại sao PDF của bạn không thể truy cập được, bạn đang ở đúng nơi. Khi kết thúc, bạn sẽ có một tệp PDF/UA 1 hoàn toàn tuân thủ, một phiên bản Markdown chứa các phương trình LaTeX, và một danh sách rõ ràng các việc thay thế phông chữ đã xảy ra trong quá trình tải.

## Những gì bạn cần

- **Aspose.Words for Java** (phiên bản mới nhất tính đến năm 2026) – thêm phụ thuộc Maven/Gradle hoặc JAR vào classpath của bạn.  
- Java 17 hoặc mới hơn (API sử dụng streams, vì vậy nên dùng JDK mới nhất).  
- Một mẫu `input.docx` có thể chứa các phần bị hỏng, phương trình Office Math và các hình dạng nổi.  

Không cần thư viện bổ sung nào; mọi thứ đều nằm trong Aspose.Words.

---

## Bước 1 – Tải DOCX với Chế độ Khôi phục  

Khi một tài liệu bị hỏng một phần, bộ tải mặc định sẽ ném ra ngoại lệ. Bằng cách bật chế độ khôi phục, bạn yêu cầu Aspose.Words tiếp tục xử lý và hiển thị các cảnh báo thay vì dừng lại.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Tại sao điều này quan trọng:* Chế độ khôi phục ngăn toàn bộ quy trình của bạn bị gián đoạn vì một đoạn văn lỗi. Nó cũng sẽ điền vào `doc.getWarnings()` để bạn có thể sau này **truy xuất các phông chữ bị thiếu** và các vấn đề khác.

---

## Bước 2 – Xuất Phương trình sang LaTeX trong Tệp Markdown  

Hầu hết các nhà phát triển yêu thích Markdown cho tài liệu, nhưng các phương trình tích hợp sẵn trong Word rất khó sao chép. Aspose.Words có thể dịch chúng trực tiếp sang LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Mẹo chuyên nghiệp:* Callback đảm bảo mọi hình ảnh được trích xuất đều được lưu vào thư mục `imgs/`. Điều này giống như cách GitHub hiển thị Markdown – sạch sẽ và di động.

---

## Bước 3 – Tạo Tài liệu PDF / UA với Gắn thẻ Đúng  

Tuân thủ PDF/UA (Universal Accessibility) là bắt buộc đối với nhiều dự án khu vực công. Các tùy chọn sau giúp Aspose.Words gắn thẻ các hình dạng nổi một cách chính xác và đặt cờ tuân thủ PDF/UA.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Bạn sẽ thấy:* Khi mở `output.pdf` trong Adobe Acrobat Pro, sẽ hiển thị “PDF/UA‑1 compliant” trong thuộc tính tài liệu. Tất cả các hình dạng nổi (hộp văn bản, hình ảnh) sẽ có các thẻ phù hợp cho trình đọc màn hình.

---

## Bước 4 – Điều chỉnh Bóng của Hình dạng (Tùy chọn Định dạng)  

Mặc dù không bắt buộc cho khả năng truy cập, việc điều chỉnh các khía cạnh hình ảnh có thể hữu ích cho các báo cáo nội bộ.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Tại sao lại quan tâm?* Nếu PDF cũng là một tài liệu marketing, một bóng nhẹ sẽ làm bố cục trông tinh tế mà không phá vỡ tính tuân thủ.

---

## Bước 5 – Truy xuất các Phông chữ Bị Thiếu và Các Cảnh báo Khác  

Trong quá trình tải khôi phục, Aspose.Words ghi lại mọi việc thay thế phông chữ. Liệt kê chúng giúp bạn quyết định có nên nhúng phông chữ đúng hay chấp nhận phông chữ thay thế.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Kết quả điển hình* (bảng điều khiển của bạn sẽ hiển thị tương tự):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Nếu bạn thấy các phông chữ quan trọng bị thiếu, hãy cân nhắc cài đặt chúng trên máy chủ hoặc nhúng chúng bằng `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Ví dụ Hoạt động Đầy đủ  

Dưới đây là lớp Java hoàn chỉnh, sẵn sàng chạy. Dán nó vào IDE của bạn, điều chỉnh các đường dẫn và nhấn **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Kết quả mong đợi**

| Output | Description |
|--------|-------------|
| `output.md` | Tệp Markdown nơi mọi phương trình Office Math xuất hiện dưới dạng LaTeX (`$…$`). Các hình ảnh được lưu trong `imgs/`. |
| `output.pdf` | Tài liệu PDF/UA‑1 tuân thủ; mở trong Acrobat để thấy “PDF/UA‑1” dưới File → Properties → Standards. |
| Console | Danh sách các phông chữ bị thiếu, ví dụ: “Missing: Calibri → substituted: Arial”. |

---

## Câu hỏi Thường gặp (FAQ)

**Q: Điều này có hoạt động với các phiên bản Aspose.Words cũ không?**  
A: Các enum `RecoveryMode`, `OfficeMathExportMode.LATEX` và `PdfCompliance.PDF_UA_1` được giới thiệu từ phiên bản 22.8. Nếu bạn đang dùng phiên bản cũ hơn, hãy nâng cấp – các tính năng truy cập không được chuyển lại.

**Q: Nếu tôi cần nhúng các phông chữ gốc thay vì thay thế thì sao?**  
A: Đặt `pdfOptions.setEmbedFullFonts(true)` và đảm bảo các tệp phông chữ có thể truy cập được trên đường dẫn phông chữ của JVM.

**Q: Tôi có thể xuất sang các định dạng markup khác (ví dụ, HTML) mà vẫn giữ các phương trình LaTeX không?**  
A: Có. Sử dụng `HtmlSaveOptions` và đặt `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – cùng một enum hoạt động trên mọi định dạng.

**Q: DOCX của tôi chứa nhiều hình dạng nổi; chúng có được gắn thẻ hết không?**  
A: Với `setExportFloatingShapesAsInlineTag(true)`, Aspose.Words bao mỗi hình dạng nổi trong một thẻ `<Figure>` cho PDF/UA, đáp ứng hầu hết các kiểm tra của trình đọc màn hình.

---

## Tổng kết  

Chúng tôi vừa cho bạn thấy cách **tạo tài liệu PDF UA** từ nguồn Word, đồng thời **tải docx với chế độ khôi phục**, **xuất phương trình sang LaTeX**, **lưu markdown từ Word**, và **truy xuất các phông chữ bị thiếu**. Mã nguồn hoàn toàn độc lập, chạy trên bất kỳ môi trường Java 17+ nào và tạo ra các tài sản sẵn sàng cho cả kiểm toán khả năng truy cập và nhà phát triển

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}