---
category: general
date: 2026-08-14
description: Nhóm các hình dạng trong Word bằng Java sử dụng Aspose.Words. Tìm hiểu
  cách tạo hình chữ nhật, đặt kích thước hình và nhóm nhiều hình dạng trong một tài
  liệu Word trống.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: vi
lastmod: 2026-08-14
og_description: Nhóm các hình dạng trong Word bằng Aspose.Words cho Java. Tạo một
  tài liệu Word trống, tạo hình chữ nhật, đặt kích thước hình, và nhóm nhiều hình
  dạng trong vài phút.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Nhóm các hình dạng trong Word – Ví dụ Java cho nhà phát triển
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Nhóm các hình dạng trong Word – hướng dẫn lập trình toàn diện
url: /vi/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nhóm các hình dạng trong Word – hướng dẫn lập trình đầy đủ

Nếu bạn cần **group shapes in Word**, hướng dẫn này sẽ dẫn bạn qua toàn bộ quá trình với Java và Aspose.Words. Bạn sẽ học cách **build blank Word document**, **create rectangle shape**, **set shape dimensions**, và cuối cùng **group multiple shapes** để chúng hoạt động như một đối tượng duy nhất.

Làm việc với các shape trong tệp Word thường giống như vẽ trên một canvas mà không có cọ vẽ. Khi kết thúc hướng dẫn này, bạn sẽ có một đoạn mã có thể tái sử dụng mà bạn có thể chèn vào bất kỳ dự án Java nào, dù bạn đang tạo báo cáo, hoá đơn, hay mẫu tùy chỉnh.

## Những gì bạn cần

- Java 8 hoặc mới hơn
- Aspose.Words for Java (phiên bản mới nhất, ví dụ: 24.9)
- Một IDE như IntelliJ IDEA hoặc Eclipse
- Kiến thức cơ bản về lập trình hướng đối tượng

Tất cả các yêu cầu này đều miễn phí để cài đặt, và đoạn mã dưới đây biên dịch được với một phụ thuộc Maven duy nhất:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Bước 1: Tạo tài liệu Word trống và khởi tạo builder

Điều đầu tiên bạn phải làm là **build a blank Word document**. Điều này cung cấp cho bạn một canvas sạch sẽ để bạn có thể chèn các shape sau này.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` đại diện cho toàn bộ tệp *.docx*, trong khi `DocumentBuilder` là công cụ hỗ trợ chèn đoạn văn, bảng và shape. Khởi tạo cả hai đối tượng là nền tảng cho bất kỳ nhiệm vụ tự động hóa Word nào.

## Bước 2: Chèn một container group shape

Một **group shape** hoạt động như một thư mục có thể chứa các shape khác. Đầu tiên chúng ta tạo container với kích thước cố định 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Phương thức `insertGroupShape` trả về một đối tượng `GroupShape`. Tất cả các shape tiếp theo mà bạn muốn xử lý như một đơn vị duy nhất phải được thêm vào đối tượng này.

## Bước 3: Tạo các hình chữ nhật và đặt kích thước shape

Bây giờ chúng ta **create rectangle shape** các đối tượng, cấu hình kích thước của chúng và đặt vị trí bên trong group. Bước này cũng minh họa cách **set shape dimensions** một cách chính xác.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Cả hai hình chữ nhật đều có cùng kích thước, nhưng thuộc tính `left` của chúng khác nhau, vì vậy chúng xuất hiện cạnh nhau. Bạn có thể thay đổi `setTop` và `setLeft` để sắp xếp bất kỳ bố cục nào bạn cần.

## Bước 4: Lưu tài liệu chứa các hình chữ nhật đã được nhóm

Sau khi các shape nằm trong group, bạn chỉ cần lưu `Document`. Tệp kết quả sẽ hiển thị hai hình chữ nhật di chuyển cùng nhau khi được chọn.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Chạy chương trình sẽ tạo `GroupShape.docx` trong thư mục làm việc. Mở nó trong Microsoft Word, chọn một hình chữ nhật, và bạn sẽ nhận thấy toàn bộ group di chuyển như một đơn vị—đúng như mục đích của **group shapes in Word**.

![Group shapes in Word example](group-shapes.png){alt="Group shapes in Word example"}

*Hình: Hai hình chữ nhật được nhóm lại trong một tài liệu Word.*

## Mẹo chuyên nghiệp: Tái sử dụng cùng một group shape

Nếu bạn cần thêm nhiều shape sau này (ví dụ: vòng tròn, hộp văn bản), hãy giữ một tham chiếu tới `groupShape` và tiếp tục gọi `appendChild`. Điều này tránh việc tạo lại container và đảm bảo tất cả các thành viên luôn đồng bộ.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Các trường hợp đặc biệt và câu hỏi thường gặp

- **What if the shapes overlap?** Overlap được phép; Word sẽ hiển thị chúng theo thứ tự chúng được thêm vào. Sử dụng `setZOrder` nếu bạn cần sắp xếp chồng rõ ràng.
- **Can I group shapes across different pages?** Không. `GroupShape` bị giới hạn trong một trang duy nhất vì hệ tọa độ của nó tương đối với trang.
- **Do grouped shapes inherit formatting?** Mỗi child giữ định dạng riêng của mình (màu nền, kiểu đường). Để áp dụng một kiểu đồng nhất, hãy lặp qua `groupShape.getChildNodes()` và đặt các thuộc tính bằng mã.

## Mã nguồn đầy đủ để tham khảo

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Chạy chương trình sẽ tạo ra một tệp DOCX trong đó hai hình chữ nhật được **grouped**. Khi chọn bất kỳ hình chữ nhật nào, cả hai sẽ di chuyển, xác nhận rằng bạn đã **grouped multiple shapes** thành công.

## Kết luận

Bây giờ bạn đã biết cách **group shapes in Word** bằng Java, từ **building a blank Word document** đến **creating rectangle shape**, **setting shape dimensions**, và cuối cùng **grouping multiple shapes** thành một đối tượng di chuyển duy nhất. Mẫu này có thể mở rộng cho bất kỳ số lượng shape nào và có thể kết hợp với văn bản, hình ảnh hoặc biểu đồ để tạo ra các tài liệu phong phú, lập trình được.

### Tiếp theo là gì?

- Khám phá **group multiple shapes** với các loại khác nhau (ellipse, mũi tên, hộp văn bản).
- Áp dụng màu nền hoặc viền bằng cách gọi `shape.getFillColor()` và `shape.getLine().setColor()`.
- Chèn group shape vào ô bảng để tạo báo cáo có cấu trúc.
- Kết hợp cách tiếp cận này với mail‑merge để tạo hợp đồng cá nhân hoá có bao gồm đồ họa thương hiệu.

Hãy tự do thử nghiệm, điều chỉnh kích thước, hoặc nhúng nội dung bổ sung. Khi bạn thành thạo việc nhóm, các script tự động hóa Word của bạn sẽ trở nên linh hoạt và dễ bảo trì hơn rất nhiều. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Sử dụng Document Shapes trong Aspose.Words cho Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Tạo tài liệu Word Java – Thêm Rectangle Shape với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}