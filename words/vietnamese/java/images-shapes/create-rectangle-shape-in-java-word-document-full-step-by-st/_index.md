---
category: general
date: 2026-05-26
description: Tạo hình chữ nhật trong tài liệu Word bằng Java và áp dụng hiệu ứng đổ
  bóng. Tìm hiểu cách thêm bóng cho hình, đặt khoảng cách bóng và lưu tệp.
draft: false
keywords:
- create rectangle shape
- apply shadow effect
- create word document java
- add shape shadow
- set shadow distance
language: vi
og_description: Tạo hình chữ nhật trong tài liệu Word bằng Java, áp dụng hiệu ứng
  bóng, thêm bóng cho hình và đặt khoảng cách bóng bằng Aspose.Words.
og_title: Tạo hình chữ nhật trong tài liệu Word bằng Java – Hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  headline: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in a Java Word document and apply shadow effect.
    Learn how to add shape shadow, set shadow distance, and save the file.
  name: Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide
  steps:
  - name: “Can I use a different shape?”
    text: Absolutely. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`, `ShapeType.LINE`,
      or any other supported enum. The rest of the shadow code stays the same.
  - name: “What if I need multiple shadows?”
    text: Aspose.Words only supports a single shadow per shape. To simulate multiple
      shadows, duplicate the shape, offset each copy, and adjust the transparency.
  - name: “Is the shadow visible in LibreOffice?”
    text: Yes—Aspose.Words writes standard OOXML, which LibreOffice interprets correctly.
      The shadow may look slightly different due to rendering engines, but the effect
      persists.
  - name: “How do I change the shadow color to match my brand?”
    text: Just swap `java.awt.Color.GRAY` with any `java.awt.Color` you prefer, such
      as `new java.awt.Color(0, 120, 215)` for a corporate blue.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word Automation
title: Tạo hình chữ nhật trong tài liệu Word bằng Java – Hướng dẫn chi tiết từng bước
url: /vi/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong tài liệu Word Java – Hướng dẫn chi tiết từng bước

Bạn đã bao giờ cần **create rectangle shape** trong một tài liệu Word Java nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn này khi tạo báo cáo hoặc hoá đơn một cách tự động. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách **create rectangle shape**, áp dụng một bóng đổ mịn, và tinh chỉnh khoảng cách bóng sao cho kết quả trông chuyên nghiệp.

Chúng ta sẽ sử dụng Aspose.Words for Java, một thư viện mạnh mẽ cho phép bạn thao tác các tệp Word mà không cần cài đặt Microsoft Office. Khi kết thúc hướng dẫn này, bạn sẽ có thể tạo các dự án **create word document java** có khả năng **add shape shadow**, **apply shadow effect**, và **set shadow distance** chỉ với vài dòng mã.

---

## Những gì bạn sẽ xây dựng

- Một tệp `.docx` mới chứa một hình chữ nhật màu xanh lơ.
- Một bóng đổ thực tế, mờ, có góc và bán trong suốt.
- Kiểm soát đầy đủ khoảng cách bóng so với hình.
- Một lớp Java sẵn sàng chạy mà bạn có thể đưa vào bất kỳ dự án Maven hoặc Gradle nào.

Không cần công cụ bên ngoài, không có bước UI thủ công—chỉ cần mã thuần.

---

## Yêu cầu trước

- Java 8 hoặc mới hơn (mã hoạt động trên Java 11, Java 17, v.v.).
- Thư viện Aspose.Words for Java (có sẵn qua Maven Central).
- Một IDE hoặc trình soạn thảo văn bản bạn thích (IntelliJ IDEA, Eclipse, VS Code…).
- Kiến thức cơ bản về cú pháp Java.

Nếu bạn chưa từng thêm phụ thuộc Maven, đây là đoạn mã nhanh:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

Bây giờ, chúng ta cùng bắt đầu.

---

## Bước 1: Tạo hình chữ nhật trong tài liệu Word

Điều đầu tiên chúng ta cần là một tài liệu trống và một `DocumentBuilder`. Hãy nghĩ về builder như một cây bút viết vào tài liệu. Khi đã có, chúng ta có thể **create rectangle shape** chỉ bằng một lời gọi phương thức.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape of 150x80 points.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Make the shape visible by filling it with cyan.
        rectangleShape.setFillColor(java.awt.Color.CYAN);
```

> **Tại sao điều này quan trọng:** Phương thức `insertShape` không chỉ tạo hình học mà còn thêm hình vào bộ sưu tập nội bộ của tài liệu, vì vậy bạn có thể ngay lập tức bắt đầu định dạng nó.

---

## Bước 2: Áp dụng hiệu ứng bóng cho hình

Bây giờ hình chữ nhật đã có trên trang, chúng ta sẽ **apply shadow effect**. Bóng đổ tạo độ sâu, khiến hình cảm giác như được nâng lên khỏi trang—một cải tiến UI tinh tế có thể tăng khả năng đọc trong báo cáo.

```java
        // Retrieve the shadow format object.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();

        // Enable the shadow and configure its appearance.
        shadowFormat.setVisible(true);          // Turn the shadow on.
        shadowFormat.setBlur(5.0);              // Soft blur radius.
        shadowFormat.setAngle(45.0);            // Direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Shadow color.
        shadowFormat.setTransparency(0.3);     // 30% transparent.
```

> **Mẹo chuyên nghiệp:** Độ mờ `5.0` trông tự nhiên cho hầu hết các tài liệu hiển thị trên màn hình. Nếu bạn in, có thể muốn giảm giá trị một chút để tránh hiện tượng mờ nhạt.

---

## Bước 3: Đặt khoảng cách bóng – Tinh chỉnh vị trí

Bóng không chỉ liên quan đến độ mờ; chúng còn cần độ dịch chuyển phù hợp. Đây là nơi chúng ta **set shadow distance**. Khoảng cách `7.0` điểm tạo ra một độ dịch chuyển vừa phải, đủ để nhận thấy nhưng không quá mạnh.

```java
        // Define how far the shadow sits from the shape.
        shadowFormat.setDistance(7.0); // Distance in points.
```

> **Nếu bạn cần độ dịch chuyển lớn hơn?** Tăng giá trị; giảm nó để có vẻ gọn hơn. Hãy nhớ, khoảng cách hoạt động cùng với góc để định vị bóng đúng cách.

---

## Bước 4: Lưu tài liệu – Lưu lại công việc của bạn

Cuối cùng, chúng ta ghi tài liệu ra đĩa. Thay đổi đường dẫn tới vị trí bạn muốn lưu tệp.

```java
        // Save the document with the rectangle and its shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

Chạy lớp sẽ tạo ra một tệp `shadow.docx` mà khi mở trong Microsoft Word hoặc LibreOffice, sẽ hiển thị một hình chữ nhật màu xanh lơ với bóng xám mềm, góc 45° và dịch chuyển 7 điểm.

---

## Ví dụ làm việc đầy đủ

Dưới đây là mã hoàn chỉnh, sẵn sàng sao chép‑dán. Nó bao gồm tất cả các import, chú thích và lời gọi `save` cuối cùng.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape of the desired size.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
        // Step 3: Apply a fill color to make the shape visible.
        rectangleShape.setFillColor(java.awt.Color.CYAN);

        // Step 4: Configure the shape's shadow effect.
        ShadowFormat shadowFormat = rectangleShape.getShadowFormat();
        shadowFormat.setVisible(true);          // Enable the shadow.
        shadowFormat.setBlur(5.0);              // Set the blur radius.
        shadowFormat.setDistance(7.0);          // Define how far the shadow is from the shape.
        shadowFormat.setAngle(45.0);            // Set the direction of the shadow.
        shadowFormat.setColor(java.awt.Color.GRAY); // Choose the shadow color.
        shadowFormat.setTransparency(0.3);      // Make the shadow partially transparent.

        // Step 5: Save the document with the shaped shadow.
        doc.save("YOUR_DIRECTORY/shadow.docx");
    }
}
```

**Kết quả mong đợi:** Mở `shadow.docx` → bạn sẽ thấy một hình chữ nhật màu xanh lơ nằm ở trung tâm trang đầu, tạo ra một bóng xám nhẹ nhàng hơi dịch chuyển về phía dưới‑phải. Độ mờ và độ trong suốt của bóng làm cho nó trông như ánh sáng tự nhiên.

---

## Câu hỏi thường gặp & Các trường hợp đặc biệt

### “Tôi có thể dùng hình dạng khác không?”

Chắc chắn. Thay `ShapeType.RECTANGLE` bằng `ShapeType.OVAL`, `ShapeType.LINE`, hoặc bất kỳ enum nào khác được hỗ trợ. Phần còn lại của mã bóng vẫn giữ nguyên.

### “Nếu tôi cần nhiều bóng?”

Aspose.Words chỉ hỗ trợ một bóng cho mỗi hình. Để mô phỏng nhiều bóng, sao chép hình, dịch chuyển mỗi bản sao và điều chỉnh độ trong suốt.

### “Bóng có hiển thị trong LibreOffice không?”

Có—Aspose.Words ghi chuẩn OOXML, LibreOffice sẽ diễn giải đúng. Bóng có thể trông hơi khác do các engine render, nhưng hiệu ứng vẫn tồn tại.

### “Làm sao thay đổi màu bóng để phù hợp với thương hiệu của tôi?”

Chỉ cần thay `java.awt.Color.GRAY` bằng bất kỳ `java.awt.Color` nào bạn muốn, chẳng hạn `new java.awt.Color(0, 120, 215)` cho màu xanh doanh nghiệp.

---

## Minh hoạ hình ảnh

![tạo hình chữ nhật trong tài liệu Word Java](https://example.com/images/rectangle-shadow.png)

*Alt text:* **create rectangle shape** minh họa cho một hình chữ nhật màu xanh lơ với bóng đổ màu xám trong tài liệu Word.

---

## Tóm tắt & Các bước tiếp theo

Chúng tôi đã trình bày cách **create rectangle shape**, **apply shadow effect**, **add shape shadow**, và **set shadow distance** bằng Aspose.Words for Java. Mã độc lập, chạy trên bất kỳ JDK hiện đại nào, và tạo ra một tệp `.docx` được hoàn thiện, sẵn sàng phân phối.

Muốn tiến xa hơn? Hãy thử:

- Thêm văn bản vào bên trong hình chữ nhật bằng `builder.moveTo(rectangleShape.getAbsolutePosition())`.
- Tạo một bảng các hình để xây dựng sơ đồ.
- Xuất tài liệu ra PDF (`doc.save("output.pdf", SaveFormat.PDF);`).

---

## Suy nghĩ cuối cùng

Việc thành thạo các nhiệm vụ **create word document java** như tạo hình và tạo bóng giúp bạn có lợi thế lớn khi tự động hoá báo cáo, hợp đồng, hoặc tài liệu marketing. Cách tiếp cận ở đây sạch sẽ, dễ bảo trì, và—quan trọng nhất—dễ điều chỉnh cho bất kỳ phong cách trực quan nào bạn cần.

Hãy chạy thử mã, điều chỉnh độ mờ, góc và khoảng cách, và xem tài liệu của bạn biến đổi từ nhàm chán thành tinh tế. Nếu gặp khó khăn, hãy để lại bình luận bên dưới; tôi sẵn sàng giúp đỡ.

Chúc lập trình vui vẻ!

## Các hướng dẫn liên quan

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tạo PDF từ Word với tạo mã vạch – Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-barcode-generation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}