---
category: general
date: 2026-08-23
description: Tạo tài liệu Word trống bằng Aspose.Words cho Java, học cách nhóm các
  hình dạng, tô màu hình chữ nhật và lưu tài liệu dưới dạng docx trong vài phút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: vi
lastmod: 2026-08-23
og_description: Tạo tài liệu Word trống bằng Aspose.Words cho Java, sau đó xem cách
  nhóm các hình dạng, tô màu hình chữ nhật và lưu tài liệu dưới dạng docx một cách
  hiệu quả.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Tạo tài liệu Word trống và nhóm các hình dạng trong Java – hướng dẫn từng
  bước
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Tạo tài liệu Word trống và nhóm các hình dạng trong Java
url: /vi/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống và nhóm các hình dạng trong Java

Nếu bạn cần **tạo tài liệu Word trống** một cách lập trình, Aspose.Words for Java giúp việc này trở nên đơn giản. Hướng dẫn này sẽ chỉ cho bạn cách **tạo tài liệu Word trống**, chèn **nhóm các hình dạng trong Word**, áp dụng **hình chữ nhật màu**, và cuối cùng **lưu tài liệu dưới dạng docx**. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ dự án Java nào.

Bạn sẽ học:

* Phụ thuộc Maven/Gradle cần thiết cho Aspose.Words.
* Cách khởi tạo một tài liệu trống và một `DocumentBuilder`.
* Các bước cụ thể **cách nhóm các hình dạng** bên trong một `GroupShape`.
* Cách đặt màu nền cho các hình chữ nhật.
* Thực hành tốt nhất cho **lưu tài liệu dưới dạng docx** và cách tìm file đầu ra.

Không yêu cầu kinh nghiệm trước với Aspose.Words, nhưng bạn nên quen với phát triển Java cơ bản và đã cài đặt JDK 8 hoặc mới hơn.

---

## Yêu cầu trước

| Yêu cầu | Phiên bản / Chi tiết |
|-------------|-------------------|
| Java Development Kit | 8 hoặc cao hơn |
| Công cụ xây dựng | Maven 3+ hoặc Gradle 6+ |
| Aspose.Words for Java | 23.12 hoặc mới hơn (phiên bản mới nhất tại thời điểm viết) |
| IDE (tùy chọn) | IntelliJ IDEA, Eclipse, VS Code, hoặc bất kỳ trình chỉnh sửa Java‑compatible nào |

---

## Bước 1: Thêm Aspose.Words vào dự án của bạn

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Mẹo:** Nếu bạn đang sử dụng proxy công ty, hãy cấu hình Maven/Gradle để tải gói từ kho Aspose như mô tả trong tài liệu chính thức.

---

## Bước 2: **Tạo tài liệu Word trống** bằng một builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Constructor `Document` tạo một container `.docx` rỗng trong bộ nhớ. `DocumentBuilder` cung cấp API dạng fluent để thêm nội dung, bao gồm các hình dạng.

---

## Bước 3: Chèn một **nhóm các hình dạng trong Word** container

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

`GroupShape` hoạt động như một mini‑canvas. Tất cả các hình dạng được thêm vào sẽ di chuyển cùng nhau, chính là **cách nhóm các hình dạng** để duy trì tính nhất quán bố cục.

---

## Bước 4: Thêm **hình chữ nhật màu** đầu tiên (đỏ)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

Hằng số `ShapeType.RECTANGLE` tạo một hình chữ nhật đơn giản. Bằng cách gọi `getFill().setForeColor(...)` bạn kiểm soát **hình chữ nhật màu**. Bạn có thể thay `java.awt.Color.RED` bằng bất kỳ hằng số `java.awt.Color` nào khác hoặc giá trị RGB tùy chỉnh.

---

## Bước 5: Thêm **hình chữ nhật màu** thứ hai (xanh lá) và định vị nó

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Việc đặt `setLeft` (hoặc `setTop`) di chuyển hình dạng tương đối so với góc trên‑trái của **nhóm các hình dạng trong Word** container. Điều này minh họa **cách nhóm các hình dạng** với vị trí chính xác.

---

## Bước 6: **Lưu tài liệu dưới dạng docx** và kiểm tra kết quả

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Phương thức `save` tự động ghi file `.docx` vì phần mở rộng file là `.docx`. Nếu bạn cần định dạng khác (ví dụ, PDF), truyền enum `SaveFormat` phù hợp.

> **Mẹo:** Đảm bảo thư mục đích (`output/` trong ví dụ này) tồn tại hoặc tạo nó bằng mã: `new File("output").mkdirs();`.

---

## Mã nguồn đầy đủ để sao chép nhanh

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Kết quả mong đợi:** Mở `GroupShapeDemo.docx` trong Microsoft Word sẽ hiển thị một trang duy nhất chứa hai hình chữ nhật màu (đỏ ở bên trái, xanh lá ở bên phải) di chuyển cùng nhau khi bạn chọn nhóm.

---

## Câu hỏi thường gặp và xử lý các trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| *Tôi có thể thêm hơn hai hình dạng vào cùng một nhóm không?* | Có. Gọi `groupShape.appendChild(yourShape)` cho mỗi hình dạng bổ sung. Nhóm sẽ tự động thay đổi kích thước để vừa với các phần mở rộng xa nhất, hoặc bạn có thể điều chỉnh thủ công chiều rộng/chiều cao. |
| *Nếu tôi cần một loại hình dạng khác (ví dụ, ellipse)?* | Thay `ShapeType.RECTANGLE` bằng `ShapeType.ELLIPSE`. Logic màu nền vẫn áp dụng tương tự. |
| *Có cần giải phóng đối tượng `Document` không?* | Aspose.Words quản lý tài nguyên native nội bộ. Khi JVM kết thúc, tài nguyên sẽ được giải phóng. Đối với ứng dụng chạy lâu, gọi `doc.dispose();` nếu bạn dùng **Aspose.Words for Java (Native)**. |
| *Làm sao thay đổi thứ tự Z‑order để một hình chữ nhật nằm trên?* | Dùng `groupShape.insertAfter(shape, referenceShape);` hoặc `groupShape.insertBefore(shape, referenceShape);` để sắp xếp lại thứ tự các phần tử con trong nhóm. |
| *Có thể nhóm các hình dạng qua các section khác nhau không?* | Không. `GroupShape` phải nằm trong một đoạn văn hoặc container hình dạng duy nhất. Để nhóm qua các section, tạo các nhóm riêng biệt trong mỗi section. |

---

## Kết luận

Bạn đã biết cách **tạo tài liệu Word trống** với Aspose.Words for Java, **nhóm các hình dạng trong Word**, áp dụng kiểu dáng **hình chữ nhật màu**, và **lưu tài liệu dưới dạng docx**. Mô hình này có thể mở rộng cho bố cục phức tạp hơn — chỉ cần thêm các hình dạng, điều chỉnh offset, và tùy chọn đặt văn bản, hình ảnh hoặc liên kết bên trong nhóm.

**Các bước tiếp theo** bạn có thể khám phá:

* Sử dụng **nhóm các hình dạng trong Word** để xây dựng sơ đồ luồng hoặc mô hình UI.
* Thử nghiệm **lưu tài liệu dưới dạng docx** kết hợp với chuyển đổi PDF (`doc.save("out.pdf")`).
* Áp dụng gradient hoặc mẫu cho **hình chữ nhật màu** để có thiết kế trực quan phong phú hơn.
* Kết hợp các hình dạng đã nhóm với bảng hoặc biểu đồ cho các tài liệu báo cáo nâng cao.

Hãy thoải mái chỉnh sửa kích thước, màu sắc, hoặc loại hình dạng để phù hợp với thương hiệu dự án của bạn. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cách lưu tài liệu dưới dạng pdf với Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Sử dụng hình dạng tài liệu trong Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}