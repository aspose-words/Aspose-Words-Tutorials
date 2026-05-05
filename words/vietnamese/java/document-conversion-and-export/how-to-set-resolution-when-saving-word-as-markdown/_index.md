---
category: general
date: 2026-05-04
description: Cách đặt độ phân giải cho việc xuất Markdown từ Word. Tìm hiểu độ phân
  giải hình ảnh trong markdown, cách xuất phương trình và lưu Word dưới dạng markdown
  trong Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: vi
og_description: Cách đặt độ phân giải cho việc xuất Markdown từ Word. Hướng dẫn này
  cho thấy độ phân giải hình ảnh trong markdown, xuất phương trình và lưu Word dưới
  dạng markdown.
og_title: Cách Đặt Độ Phân Giải Khi Lưu Word Thành Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Cách đặt độ phân giải khi lưu Word dưới dạng Markdown
url: /vi/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Độ Phân Giải Khi Lưu Word thành Markdown

Bạn đã bao giờ tự hỏi **cách đặt độ phân giải** cho các hình ảnh xuất hiện trong tệp Markdown được tạo từ tài liệu Word chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi các hình ảnh toán học được raster hoá mặc định trông mờ, đặc biệt trên màn hình có DPI cao.  

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn chi tiết các bước để kiểm soát *markdown image resolution* đồng thời chỉ ra **cách xuất phương trình** dưới dạng LaTeX, và cuối cùng là **cách lưu Word thành markdown** bằng Aspose.Words for Java. Khi kết thúc, bạn sẽ có một tệp Markdown sắc nét, sẵn sàng cho sản xuất, hiển thị phương trình một cách sạch sẽ và hình ảnh với chất lượng bạn cần.

## Yêu cầu trước

- Java 17 (hoặc bất kỳ JDK gần đây nào)  
- Aspose.Words for Java 23.6 trở lên – bạn có thể tải từ Maven Central  
- Một tài liệu Word (`.docx`) chứa các đối tượng OfficeMath (phương trình) và có thể có hình ảnh raster  
- Kiến thức cơ bản về Maven/Gradle và một IDE (IntelliJ IDEA, Eclipse, VS Code, v.v.)

Không cần thư viện bổ sung; mọi thứ khác đều được Aspose.Words xử lý.

---

## Cách Đặt Độ Phân Giải cho Xuất Markdown

> **Mẹo chuyên nghiệp:** Độ phân giải bạn chọn ảnh hưởng trực tiếp đến kích thước tệp của các hình ảnh được tạo. Giá trị **300 dpi** là sự cân bằng tốt cho hầu hết các trình xem Markdown trên web.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

Lệnh `setImageResolution(int dpi)` là trung tâm của **cách đặt độ phân giải**. Nó chỉ định cho Aspose.Words raster hoá bất kỳ hình ảnh dự phòng nào (ví dụ, khi một phương trình không thể biểu diễn bằng LaTeX thuần) với số điểm trên inch được chỉ định. Nếu bạn bỏ qua dòng này, thư viện sẽ sử dụng mặc định 220 dpi, có thể trông mờ trên màn hình retina.

### Tại sao nên sử dụng LaTeX cho các phương trình?

Khi bạn xuất phương trình dưới dạng LaTeX (`OfficeMathExportMode.LATEX`), Markdown tạo ra chứa mã LaTeX thô được bao quanh bởi `$…$` hoặc `$$…$$`. Hầu hết các trình render Markdown hiện đại (GitHub, GitLab, MkDocs với MathJax) sẽ hiển thị chúng dưới dạng đồ họa vector sắc nét, có thể mở rộng—không lo lắng về độ phân giải. Cài đặt độ phân giải chỉ quan trọng đối với **markdown image resolution** của bất kỳ hình ảnh raster dự phòng nào, chẳng hạn như biểu đồ nhúng hoặc ảnh không được hỗ trợ nguyên bản trong Markdown.

---

## Cách Sử Dụng Độ Phân Giải Hình Ảnh Markdown Một Cách Hiệu Quả

Nếu bạn cần nhúng các hình ảnh thông thường (ví dụ, ảnh chụp màn hình) vào tệp Word của mình, chúng sẽ được Aspose.Words chuyển đổi sang PNG. Phương thức `setImageResolution` tương tự được áp dụng, đảm bảo các PNG này kế thừa DPI bạn chỉ định. Dưới đây là danh sách kiểm tra nhanh:

1. **Chọn DPI phù hợp với nền tảng mục tiêu của bạn** – 72 dpi cho web cổ điển, 150 dpi cho màn hình tiêu chuẩn, 300 dpi cho PDF chất lượng in.  
2. **Kiểm tra đầu ra** – mở tệp `.md` đã tạo trong trình xem yêu thích và phóng to để xác nhận độ sắc nét.  
3. **Xem xét kích thước tệp** – DPI cao hơn tạo ra PNG lớn hơn; nếu băng thông là mối quan tâm, thử nghiệm với 200 dpi và so sánh.

---

## Cách Xuất Phương Trình dưới dạng LaTeX

Dòng `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` chỉ định cho Aspose.Words chuyển đổi mọi đối tượng OfficeMath sang LaTeX. Đây là cách tiếp cận được khuyến nghị vì:

- **Khả năng mở rộng** – LaTeX hiển thị ở bất kỳ kích thước nào mà không mất chất lượng.  
- **Khả năng chỉnh sửa** – Bạn có thể chỉnh sửa LaTeX trực tiếp trong tệp Markdown sau này.  
- **Tính tương thích** – Hầu hết các trình tạo site tĩnh và công cụ tài liệu đã hỗ trợ render LaTeX.

Nếu bạn cần sử dụng lại phương án dự phòng dựa trên hình ảnh, chỉ cần chuyển sang `OfficeMathExportMode.IMAGE`. Trong trường hợp đó, độ phân giải bạn đặt sẽ trở nên quan trọng hơn.

---

## Lưu Word thành Markdown – Ví dụ Toàn Diện Từ Đầu Đến Cuối

Dưới đây là một đoạn mã dự án Maven đầy đủ, có thể chạy, minh họa toàn bộ quy trình, từ khai báo phụ thuộc đến thực thi.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Kết quả mong đợi:** `MathExport.md` sẽ chứa các khối LaTeX cho mỗi phương trình, và bất kỳ hình ảnh nhúng nào sẽ xuất hiện dưới dạng liên kết PNG với DPI là 300. Mở tệp trong trình xem Markdown hỗ trợ MathJax (ví dụ, VS Code với phần mở rộng Markdown Preview Enhanced) và bạn sẽ thấy các phương trình và hình ảnh hoàn toàn sắc nét.

---

## Câu Hỏi Thường Gặp & Các Trường Hợp Đặc Biệt

### Nếu tôi cần DPI khác cho chỉ một hình ảnh thì sao?

Aspose.Words áp dụng DPI toàn cục thông qua `setImageResolution`. Để xử lý DPI riêng cho từng hình ảnh, bạn cần hậu xử lý Markdown đã tạo: thay thế các tệp PNG bằng phiên bản độ phân giải cao hơn và điều chỉnh liên kết hình ảnh thủ công. Không phải là cách lý tưởng, nhưng có thể thực hiện cho một vài trường hợp đặc biệt.

### Điều này có hoạt động trên Linux/macOS không?

Chắc chắn. Thư viện thuần Java, vì vậy cùng một đoạn mã chạy ở bất kỳ nơi nào có JDK. Chỉ cần đảm bảo các đường dẫn tệp sử dụng dấu gạch chéo (/) hoặc `Paths.get(...)` để xử lý độc lập nền tảng.

### Còn đầu ra SVG thì sao?

Nếu bạn thích hình ảnh vector cho biểu đồ, có thể đặt `saveOptions.setExportImagesAsSvg(true);`. SVG bỏ qua DPI, vì vậy vấn đề **markdown image resolution** không còn tồn tại. Tuy nhiên, không phải tất cả trình render Markdown đều xử lý SVG tốt, vì vậy hãy thử nghiệm trên nền tảng mục tiêu trước.

### Tôi có thể nhúng Markdown đã tạo vào trình tạo site tĩnh không?

Có. Đầu ra là tệp `.md` thuần với cú pháp Markdown chuẩn cộng thêm các dấu phân cách LaTeX. Hầu hết các trình tạo (Jekyll, Hugo, MkDocs) sẽ chấp nhận ngay. Chỉ cần nhớ bật MathJax hoặc KaTeX trong cấu hình site của bạn.

---

## Kết Luận

Chúng tôi đã trình bày **cách đặt độ phân giải** cho hình ảnh khi bạn **lưu Word thành markdown**, khám phá các chi tiết của **markdown image resolution**, minh họa **cách xuất phương trình** dưới dạng LaTeX, và đưa ra ví dụ Java đầy đủ. Bằng cách điều chỉnh `setImageResolution` và chọn `OfficeMathExportMode` phù hợp, bạn có được kiểm soát chính xác cả độ trung thực hình ảnh và kích thước tệp.

Sẵn sàng cho bước tiếp theo? Hãy thử kết hợp cách này với Aspose.PDF để chuyển đổi cùng nguồn Word trực tiếp sang PDF, hoặc thử nghiệm `setExportImagesAsSvg(true)` cho đồ họa dựa trên vector. Các kỹ thuật bạn đã học ở đây là nền tảng cho bất kỳ quy trình tài liệu tự động nào.

Nếu bạn thấy hướng dẫn này hữu ích, hãy đánh dấu sao trên GitHub, chia sẻ với đồng nghiệp, hoặc để lại bình luận bên dưới với các mẹo của bạn. Chúc lập trình vui vẻ!  

![Ví dụ cách đặt độ phân giải](resolution.png "Cách đặt độ phân giải khi lưu Word thành Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}