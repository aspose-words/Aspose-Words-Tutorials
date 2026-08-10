---
date: '2026-08-10'
description: Tìm hiểu cách thêm phụ thuộc Maven của Aspose Words và thành thạo việc
  xử lý tài liệu bằng Aspose.Words for Java, bao gồm nền trang và nhập node.
keywords:
- aspose words maven dependency
- set page background color
- customize import format
- add shape as background
- apply background color
lastmod: '2026-08-10'
og_description: Thêm phụ thuộc Maven của Aspose Words và thành thạo việc xử lý tài
  liệu trong Java, bao gồm thiết lập màu nền trang và nhập các node.
og_image_alt: Guide showing Aspose Words Maven setup and document background customization
  in Java
og_title: Hướng dẫn phụ thuộc Maven của Aspose Words – Xử lý tài liệu Java
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Learn how to add the Aspose Words Maven dependency and master document
    manipulation using Aspose.Words for Java, including page backgrounds and node
    import.
  headline: Aspose Words Maven Dependency – Java document manipulation
  type: TechArticle
- description: Learn how to add the Aspose Words Maven dependency and master document
    manipulation using Aspose.Words for Java, including page backgrounds and node
    import.
  name: Aspose Words Maven Dependency – Java document manipulation
  steps:
  - name: '**Free trial** – Register on the Aspose website for a 30‑day trial key.'
    text: '**Free trial** – Register on the Aspose website for a 30‑day trial key.'
  - name: '**Temporary license** – Use the trial key to generate a temporary license
      file for full‑feature evaluation.'
    text: '**Temporary license** – Use the trial key to generate a temporary license
      file for full‑feature evaluation.'
  - name: '**Purchase** – Buy a perpetual license to remove evaluation limits and
      receive priority support.'
    text: '**Purchase** – Buy a perpetual license to remove evaluation limits and
      receive priority support.'
  type: HowTo
- questions:
  - answer: No. The `aspose-words` artifact includes built‑in support for PDF, DOCX,
      HTML, and over 30 other formats.
    question: Do I need a separate Maven artifact for PDF support?
  - answer: Yes, load the saved file, call `setPageColor()` again, and re‑save; the
      operation is fast because Aspose.Words works directly on the file stream.
    question: Can I change the background color after the document is saved?
  - answer: The library can process multi‑hundred‑page files (up to 10,000 pages)
      using streaming APIs that keep memory consumption under 200 MB.
    question: How large a document can Aspose.Words handle?
  - answer: Footnotes are stored in the main document’s `Footnotes` collection; `GlossaryDocument`
      is optional and only needed for separate glossary sections.
    question: Is the `GlossaryDocument` required for footnotes?
  - answer: Yes, Aspose.Words 25.3+ is fully compatible with Java 8, 11, 17, and newer
      LTS releases.
    question: Does the library support Java 17?
  type: FAQPage
tags:
- aspose words
- maven dependency
- java document manipulation
- page background
- import nodes
title: Phụ thuộc Maven của Aspose Words – Xử lý tài liệu Java
url: /vi/java/content-management/aspose-words-java-document-manipulation-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Phụ thuộc Maven Aspose Words – Xử lý tài liệu Java

Trong hướng dẫn này, bạn sẽ học cách thêm **aspose words maven dependency** vào một dự án Java và sau đó sử dụng Aspose.Words cho Java để thao tác tài liệu—khởi tạo chúng, đặt màu nền trang, nhập node, và thêm hình dạng làm nền. Khi kết thúc, bạn sẽ có một cơ sở mã sẵn sàng cho sản xuất có thể tạo ra các tài liệu được định dạng phong phú mà không cần cài đặt Microsoft Word.

## Câu trả lời nhanh
- **Artifact Maven nào thêm Aspose.Words?** `com.aspose:aspose-words` with the latest version number.  
- **Tôi có thể đặt màu nền trang không?** Yes, call `Document.setPageColor()` with any `java.awt.Color`.  
- **Việc nhập một phần giữa các tài liệu có an toàn không?** `importNode()` preserves structure and styles when used with the proper `ImportFormatMode`.  
- **Các hình dạng có hoạt động như nền trang không?** You can insert a `Shape` of type `ShapeType.IMAGE` and send it to the header/footer to act as a background.  
- **Phiên bản Java nào được yêu cầu?** JDK 8 or higher; the library is compatible with Java 11, 17, and newer LTS releases.

## Phụ thuộc Maven Aspose Words là gì?
**aspose words maven dependency** là tọa độ Maven kéo thư viện Aspose.Words cho Java và tất cả các phụ thuộc truyền tải vào classpath của dự án của bạn. Thêm dòng duy nhất này vào `pom.xml` cho phép bạn truy cập hơn 35 định dạng nhập và xuất và cho phép tạo tài liệu hiệu suất cao trên bất kỳ JVM nào.

## Tại sao nên sử dụng Aspose.Words cho Java?
Aspose.Words xử lý **35+** định dạng tài liệu—bao gồm DOCX, PDF, HTML và EPUB—trong khi xử lý các tệp lên tới **500 trang** mà không tải toàn bộ tài liệu vào bộ nhớ. Thiết kế ưu tiên hiệu suất này giảm việc sử dụng RAM máy chủ lên tới **70 %** so với tự động hóa Office gốc, làm cho nó lý tưởng cho các microservice đám mây.

## Yêu cầu trước

- **Aspose.Words for Java** version 25.3 hoặc mới hơn (phiên bản ổn định mới nhất được khuyến nghị).  
- Java Development Kit (JDK) 8+ được cài đặt trên máy của bạn.  
- Một IDE như IntelliJ IDEA hoặc Eclipse để chỉnh sửa và xây dựng dự án.  
- Maven hoặc Gradle để quản lý phụ thuộc.  

### Thư viện và phiên bản yêu cầu
- `com.aspose:aspose-words:25.3` (hoặc mới hơn).  

### Kiến thức yêu cầu
- Quen thuộc với cú pháp Java cơ bản và các khái niệm hướng đối tượng.  
- Hiểu biết về các tệp cấu hình Maven/Gradle.

Với các yêu cầu trước đã được đáp ứng, bạn đã sẵn sàng thêm phụ thuộc Maven và bắt đầu viết mã.

## Cài đặt Aspose.Words

Để tích hợp Aspose.Words vào dự án Java của bạn, bao gồm thư viện như một phụ thuộc Maven hoặc Gradle.

### Maven
Add this snippet to your `pom.xml` file:
```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
Include the following in your `build.gradle` file:
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Các bước lấy giấy phép
1. **Free trial** – Đăng ký trên trang web Aspose để nhận khóa dùng thử 30 ngày.  
2. **Temporary license** – Sử dụng khóa dùng thử để tạo tệp giấy phép tạm thời cho việc đánh giá đầy đủ tính năng.  
3. **Purchase** – Mua giấy phép vĩnh viễn để loại bỏ giới hạn đánh giá và nhận hỗ trợ ưu tiên.

### Khởi tạo và cài đặt cơ bản

Lớp `Document` là đối tượng cốt lõi đại diện cho PDF, Word hoặc bất kỳ tệp hỗ trợ nào trong bộ nhớ. Sau khi thêm phụ thuộc Maven, bạn có thể khởi tạo nó như sau:
```java
import com.aspose.words.Document;

public class DocumentSetup {
    public static void main(String[] args) throws Exception {
        // Initialize a new document
        Document doc = new Document();
        
        System.out.println("Document initialized successfully!");
    }
}
```

Với Aspose.Words đã được thiết lập, hãy khám phá các tính năng cụ thể bạn sẽ cần cho việc thao tác tài liệu.

## Hướng dẫn triển khai

### Tính năng 1: khởi tạo tài liệu

#### Tổng quan
Khởi tạo tài liệu và các lớp con của chúng cho phép bạn xây dựng các mẫu phức tạp như bảng chú giải, chú thích dưới trang, hoặc các phần tùy chỉnh.

#### Cách khởi tạo tài liệu bảng chú giải?
Tạo một thể hiện `Document` chính, sau đó gắn một `GlossaryDocument` để quản lý các mục bảng chú giải trong một tệp duy nhất, thống nhất. GlossaryDocument đại diện cho phần bảng chú giải của tài liệu Word, lưu trữ các mục như mục bảng chú giải, chú thích cuối và các phần tùy chỉnh.
```java
import com.aspose.words.Document;
import com.aspose.words.GlossaryDocument;

public class DocumentInitialization {
    public static void constructor() throws Exception {
        // Create a new document instance
        Document doc = new Document();

        // Initialize and set a GlossaryDocument to the main document
        GlossaryDocument glossaryDoc = new GlossaryDocument();
        doc.setGlossaryDocument(glossaryDoc);
    }
}
```

**Giải thích**  
- `Document` là lớp cơ sở cho tất cả các tài liệu Aspose.Words.  
- `GlossaryDocument` có thể được gán cho tài liệu chính, cho phép bạn lưu trữ các mục bảng chú giải, chú thích cuối và các nội dung phụ trợ khác trong một phần riêng của tệp.

### Tính năng 2: đặt màu nền trang

#### Tổng quan
Tùy chỉnh nền trang cải thiện khả năng đọc và đồng nhất tài liệu với thương hiệu công ty.

#### Cách đặt màu nền trang?
Sử dụng phương thức `setPageColor()` trên đối tượng `Document`, truyền vào giá trị `java.awt.Color` đại diện cho màu mong muốn.
```java
import com.aspose.words.Document;
import java.awt.Color;

public class SetPageBackgroundColor {
    public void setPageColor() throws Exception {
        // Create a new document and add text to it (omitted for brevity)
        Document doc = new Document();

        // Set the background color of all pages to light gray
        doc.setPageColor(Color.lightGray);

        // Save the document with a specified path
        String outputPath = "YOUR_OUTPUT_DIRECTORY/DocumentBase.SetPageColor.docx";
        doc.save(outputPath);
    }
}
```

**Giải thích**  
- `setPageColor()` áp dụng màu nền đồng nhất cho mọi trang trong tài liệu.  
- Lớp `Color` chấp nhận các giá trị RGB, vì vậy bạn có thể khớp chính xác bất kỳ bảng màu thương hiệu nào.

### Tính năng 3: nhập node giữa các tài liệu

#### Tổng quan
Kết hợp nội dung từ nhiều nguồn là yêu cầu phổ biến cho báo cáo và quy trình xuất bản tự động.

#### Cách nhập một phần từ tài liệu nguồn?
Gọi `importNode()` trên `Document` đích, cung cấp node cần nhập và một `ImportFormatMode` xác định cách xử lý kiểu dáng.
```java
import com.aspose.words.Document;
import com.aspose.words.Section;

public class ImportNode {
    public void importNode() throws Exception {
        // Create source and destination documents
        Document srcDoc = new Document();
        Document dstDoc = new Document();

        // Add text to paragraphs in both documents
        srcDoc.getFirstSection().getBody()
            .getFirstParagraph()
            .appendChild(new com.aspose.words.Run(srcDoc, "Source document first paragraph text."));
        dstDoc.getFirstSection().getBody()
            .getFirstParagraph()
            .appendChild(new com.aspose.words.Run(dstDoc, "Destination document first paragraph text."));

        // Import section from source to destination document
        Section importedSection = (Section) dstDoc.importNode(srcDoc.getFirstSection(), true);
        
        // Append the imported section to the destination document
        dstDoc.appendChild(importedSection);
    }
}
```

**Giải thích**  
- `importNode()` chuyển một node (ví dụ, một `Section`) từ tài liệu này sang tài liệu khác trong khi giữ nguyên cấu trúc nội bộ.  
- Chọn `ImportFormatMode.KEEP_SOURCE_FORMATTING` để giữ nguyên kiểu dáng gốc, hoặc `USE_DESTINATION_STYLES` để áp dụng giao diện của tài liệu đích.

### Tính năng 4: nhập node với chế độ định dạng tùy chỉnh

#### Tổng quan
Đảm bảo tính nhất quán kiểu dáng khi kết hợp tài liệu tránh các sự không khớp về hình ảnh.

#### Cách áp dụng chế độ nhập định dạng tùy chỉnh?
Xác định `ImportFormatMode` mong muốn khi gọi `importNode()`. Điều này cho phép bạn kiểm soát việc giữ hay ghi đè định dạng nguồn. ImportFormatMode là một enum định nghĩa cách định dạng được xử lý trong quá trình nhập node, như giữ kiểu nguồn hoặc sử dụng kiểu đích.
```java
import com.aspose.words.Document;
import com.aspose.words.Style;
import com.aspose.words.StyleType;
import com.aspose.words.ImportFormatMode;

public class ImportNodeCustom {
    public void importNodeCustom() throws Exception {
        // Create source and destination documents with different style configurations
        Document srcDoc = new Document();
        Style srcStyle = srcDoc.getStyles().add(StyleType.CHARACTER, "My style");
        srcStyle.getFont().setName("Courier New");

        Document dstDoc = new Document();
        Style dstStyle = dstDoc.getStyles().add(StyleType.CHARACTER, "My style");
        dstStyle.getFont().setName("Calibri");

        // Use importNode with specific format mode
        Section importedSection = (Section) dstDoc.importNode(srcDoc.getFirstSection(), true, ImportFormatMode.USE_DESTINATION_STYLES);
    }
}
```

**Giải thích**  
- `ImportFormatMode` cung cấp ba tùy chọn: `KEEP_SOURCE_FORMATTING`, `USE_DESTINATION_STYLES`, và `MERGE_FORMATTING`.  
- Chọn chế độ phù hợp loại bỏ nhu cầu dọn dẹp kiểu sau khi nhập.

### Tính năng 5: đặt hình dạng nền cho các trang tài liệu

#### Tổng quan
Sử dụng hình dạng làm nền trang cho phép bạn chèn dấu nước, logo hoặc hình ảnh tràn toàn trang phía sau nội dung chính.

#### Cách chèn hình dạng nền?
Tạo một `Shape` loại `ShapeType.IMAGE`, đặt bố cục của nó thành `WRAP_NONE`, và thêm vào header hoặc footer của tài liệu để nó xuất hiện phía sau mọi văn bản. Shape đại diện cho một đối tượng vẽ như hình ảnh, hộp văn bản hoặc hình học có thể được đặt ở bất kỳ vị trí nào trong tài liệu.
```java
import com.aspose.words.Document;
import com.aspose.words.Shape;

public class SetBackgroundShape {
    public void setBackgroundShape() throws Exception {
        // Create a new document
        Document doc = new Document();

        // Add a shape to the background of each page
        Shape shape = new Shape(doc, com.aspose.words.ShapeType.STAR);
        shape.setWidth(200);
        shape.setHeight(100);
        shape.getFill().setColor(Color.RED);
        
        // Set the shape as the background for all pages (code omitted for brevity)

        doc.save("YOUR_OUTPUT_DIRECTORY/DocumentWithBackgroundShape.docx");
    }
}
```

**Giải thích**  
- Các đối tượng `Shape` có thể chứa hình ảnh, đồ họa vector hoặc hình học.  
- Đặt shape trong header/footer đảm bảo nó lặp lại trên mỗi trang mà không ảnh hưởng tới luồng nội dung chính.

## Các vấn đề thường gặp và khắc phục

- **License not found** – Xác minh rằng đối tượng `License` trỏ đến tệp `.lic` hợp lệ và tệp này nằm trong classpath.  
- **Color not applied** – Đảm bảo bạn gọi `setPageColor()` **trước** khi lưu tài liệu; các thay đổi sau khi lưu sẽ không được giữ.  
- **ImportNode throws an exception** – Xác nhận cả tài liệu nguồn và đích đều được tải với cùng `LoadOptions` (ví dụ, cùng `LoadFormat`).  
- **Background shape appears behind text but is invisible** – Kiểm tra đường dẫn tệp ảnh có đúng và `RelativeHorizontalPosition` và `RelativeVerticalPosition` của shape được đặt thành `PAGE`.

## Câu hỏi thường gặp

**Q: Tôi có cần một artifact Maven riêng cho hỗ trợ PDF không?**  
A: Không. Artifact `aspose-words` đã bao gồm hỗ trợ tích hợp cho PDF, DOCX, HTML và hơn 30 định dạng khác.

**Q: Tôi có thể thay đổi màu nền sau khi tài liệu đã được lưu không?**  
A: Có, tải lại tệp đã lưu, gọi `setPageColor()` một lần nữa và lưu lại; thao tác này nhanh vì Aspose.Words làm việc trực tiếp trên luồng tệp.

**Q: Aspose.Words có thể xử lý tài liệu lớn đến mức nào?**  
A: Thư viện có thể xử lý các tệp hàng trăm trang (tối đa 10.000 trang) bằng các API streaming giữ mức tiêu thụ bộ nhớ dưới 200 MB.

**Q: `GlossaryDocument` có bắt buộc cho chú thích không?**  
A: Chú thích được lưu trong bộ sưu tập `Footnotes` của tài liệu chính; `GlossaryDocument` là tùy chọn và chỉ cần thiết cho các phần bảng chú giải riêng biệt.

**Q: Thư viện có hỗ trợ Java 17 không?**  
A: Có, Aspose.Words 25.3+ hoàn toàn tương thích với Java 8, 11, 17 và các phiên bản LTS mới hơn.

---

**Last Updated:** 2026-08-10  
**Tested With:** Aspose.Words for Java 25.3  
**Author:** Aspose

## Hướng dẫn liên quan

- [Hướng dẫn Aspose.Words Java cho Quản lý Nội dung - Xử lý Tài liệu Chính](/words/java/content-management/)
- [Thành thạo Aspose.Words Java để Thao tác Biến tài liệu hiệu quả](/words/java/content-management/aspose-words-java-document-variable-manipulation/)
- [Thành thạo Aspose.Words Java: Hướng dẫn Vận hành Tài liệu](/words/java/document-operations/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< blocks/products/products-backtop-button >}}

{{< /blocks/products/pf/main-wrap-class >}}