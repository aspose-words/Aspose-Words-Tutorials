---
category: general
date: 2026-07-16
description: cách chèn nhóm hình dạng trong Java bằng Aspose.Words – thêm hình chữ
  nhật, đặt kích thước cho hình dạng, và tạo hình chữ nhật và vòng tròn màu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: vi
lastmod: 2026-07-16
og_description: 'cách chèn nhóm hình dạng trong Java: hướng dẫn thực hành để thêm
  hình chữ nhật, thiết lập kích thước hình dạng và tạo hình chữ nhật và vòng tròn
  màu sắc với Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Chèn Nhóm Hình trong Java – Hướng Dẫn Đầy Đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Cách chèn nhóm hình trong Java – Hướng dẫn đầy đủ
url: /vi/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cách chèn nhóm hình trong Java – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi **cách chèn nhóm hình** trong một tài liệu Word bằng Java chưa? Bạn không phải là người duy nhất. Dù bạn đang xây dựng một trình tạo báo cáo hay một công cụ tạo tờ rơi động, việc nhóm các hình giúp bố cục của bạn gọn gàng và mã nguồn dễ quản lý.

Trong hướng dẫn này, chúng ta sẽ đi qua các bước chính xác để **thêm hình chữ nhật**, **đặt kích thước hình**, và **tạo hình chữ nhật màu** và **tạo hình tròn màu** bằng thư viện Aspose.Words. Khi kết thúc, bạn sẽ có một chương trình có thể chạy được tạo ra một tệp .docx với một hình chữ nhật màu xanh và một hình tròn màu đỏ được bọc gọn trong một nhóm.

## Yêu cầu trước

- Java 17 (hoặc bất kỳ JDK mới nào) đã được cài đặt và cấu hình.
- Maven hoặc Gradle để quản lý các phụ thuộc.
- Aspose.Words for Java 23.9 hoặc mới hơn – bạn có thể tải nó từ Maven Central.
- Kiến thức cơ bản về cú pháp Java – không cần gì phức tạp.

Nếu bạn thiếu bất kỳ mục nào trong số này, hãy tải JDK từ trang của Oracle và thêm phụ thuộc Aspose.Words vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Bây giờ nền tảng đã sẵn sàng, hãy bắt tay vào thực hành.

## cách chèn nhóm hình – Tổng quan

Ý tưởng cốt lõi rất đơn giản: tạo một `Document`, mở một `DocumentBuilder`, chèn một **nhóm hình**, sau đó đưa các hình riêng lẻ (một hình chữ nhật và một hình tròn) vào trong nhóm đó. Nhóm hoạt động như một container, vì vậy việc di chuyển nó sau này sẽ làm dịch chuyển mọi thứ bên trong – lý tưởng cho các bố cục phức tạp.

Dưới đây là đoạn mã đầy đủ, sẵn sàng để chạy. Bạn có thể sao chép và dán nó vào một lớp Java mới có tên `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Mẹo chuyên nghiệp:** Các giá trị `setLeft` và `setTop` là tương đối so với gốc của nhóm, không phải trang. Điều này giúp việc di chuyển lại toàn bộ nhóm trở nên dễ dàng hơn sau này.

### Điều gì vừa xảy ra?

1. **Document & Builder** – Chúng tôi tạo một tệp Word trống và một `DocumentBuilder` cho phép chúng ta chèn nội dung.
2. **Group Shape** – `builder.insertGroupShape()` tạo một container. Hãy nghĩ nó như một thư mục cho các đối tượng vẽ.
3. **Blue Rectangle** – Chúng tôi khởi tạo một `Shape` loại `RECTANGLE`, đặt kích thước, vị trí và tô màu xanh – đây là bước **tạo hình chữ nhật màu**.
4. **Red Circle** – Cùng mẫu, nhưng sử dụng `ELLIPSE` để tạo một vòng tròn hoàn hảo, sau đó tô màu đỏ – đây là phần **tạo hình tròn màu**.
5. **Saving** – Cuối cùng chúng tôi lưu mọi thứ vào `GroupShapeDemo.docx`.

Chạy chương trình (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) và mở tệp kết quả. Bạn sẽ thấy một hình chữ nhật màu xanh ở bên trái và một hình tròn màu đỏ ở bên phải, cả hai đều được khóa trong một hộp nhóm duy nhất.

## Thêm hình chữ nhật

Nếu bạn chỉ cần một hình chữ nhật mà không cần nhóm, bạn có thể bỏ qua lời gọi `insertGroupShape()` và thêm hình chữ nhật trực tiếp vào phần thân của tài liệu. Tuy nhiên, việc nhóm cung cấp cho bạn khả năng di chuyển, xoay hoặc xóa nhiều hình cùng lúc.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Chú ý cách chúng tôi đã sử dụng logic **thêm hình chữ nhật** ở đây. Hình chữ nhật xuất hiện trên trang như một đối tượng độc lập. Trong hầu hết các trường hợp thực tế, bạn sẽ muốn sử dụng nhóm, vì nó giữ nguyên vị trí tương đối.

## Đặt kích thước hình

Khi bạn thấy các phương thức như `setWidth` và `setHeight`, hãy nhớ chúng nhận **điểm** (1/72 inch). Nếu bạn muốn dùng milimet, hãy chuyển đổi trước:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Đoạn mã này minh họa **đặt kích thước hình** với việc chuyển đổi đơn vị – rất hữu ích khi các thông số thiết kế của bạn đến từ một bản mô phỏng UI sử dụng đơn vị mét.

## Tạo hình chữ nhật màu

Việc tô màu cho một hình rất đơn giản, chỉ cần gọi `getFill().setForeColor()`. Bạn có thể truyền bất kỳ `java.awt.Color` nào. Muốn gradient? Sử dụng `setForeColor` cho màu bắt đầu và `setBackColor` cho màu kết thúc.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Đó là cách nhanh để **tạo hình chữ nhật màu** với độ phủ gradient thay vì màu đồng nhất.

## Tạo hình tròn màu

Các vòng tròn chỉ là các hình ellipse có chiều rộng và chiều cao bằng nhau. Logic màu tương tự áp dụng:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Nếu bạn cần độ phủ trong suốt, hãy đặt kênh alpha:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Bây giờ bạn đã thành thạo kỹ thuật **tạo hình tròn màu**.

## Lưu tài liệu

Aspose.Words cho phép bạn xuất ra nhiều định dạng: DOCX, PDF, HTML, PNG, tùy bạn. Đối với demo này, chúng tôi sử dụng DOCX vì nó giữ nguyên các hình vector một cách hoàn hảo.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Chỉ cần thay đổi `SaveFormat` là bạn có thể tạo phiên bản PDF của cùng một tác phẩm đã nhóm.

## Những lỗi thường gặp & Cách tránh

- **Quên thêm hình vào nhóm?** Hình sẽ xuất hiện trên trang nhưng sẽ không di chuyển cùng nhóm. Luôn gọi `group.appendChild(yourShape)`.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Tạo hình chữ nhật trong Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}