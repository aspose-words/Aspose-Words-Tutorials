---
category: general
date: 2026-11-22
description: Thêm hình chữ nhật vào tài liệu Word bằng Java, đặt kích thước hình,
  nhóm nhiều hình lại với nhau và thêm hình vào nhóm một cách hiệu quả.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: vi
lastmod: 2026-11-22
og_description: Thêm hình chữ nhật vào tài liệu Word bằng Java, sau đó đặt kích thước
  hình, nhóm nhiều hình lại với nhau và thêm hình vào nhóm trong một quy trình duy
  nhất.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Thêm hình chữ nhật và nhóm các hình trong Java – hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Thêm hình chữ nhật và nhóm các hình trong Java
url: /vi/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm hình chữ nhật và nhóm các hình trong Java

Nếu bạn cần **thêm hình chữ nhật** vào tài liệu Word bằng Java, hướng dẫn này sẽ đưa bạn qua các bước chi tiết. Bạn cũng sẽ học cách **đặt kích thước hình**, **nhóm nhiều hình**, và **đính kèm hình vào nhóm** mà không rời khỏi IDE.

Làm việc với đồ họa vector bên trong tệp DOCX thường cảm giác như phải quản lý nhiều API riêng lẻ. Khi kết thúc tutorial này, bạn sẽ có một chương trình tự chứa duy nhất tạo ra một hình chữ nhật, một hình ellipse và bất kỳ hình bổ sung nào bạn cần, sau đó nhóm chúng lại để di chuyển như một đối tượng duy nhất. Không cần công cụ bên ngoài nào ngoài Aspose.Words for Java.

## Yêu cầu trước

Trước khi bắt đầu, hãy đảm bảo bạn có:

* Java 17 hoặc mới hơn đã được cài đặt.
* Maven 3.8+ (hoặc Gradle) để quản lý các phụ thuộc.
* Giấy phép Aspose.Words for Java hợp lệ (phiên bản dùng thử hoạt động cho việc thử nghiệm).
* Một IDE như IntelliJ IDEA hoặc VS Code, mặc dù bất kỳ trình soạn thảo văn bản nào cũng được.

Các yêu cầu này cho phép mã biên dịch và chạy trên bất kỳ môi trường phát triển hiện đại nào.

## Bước 1: Thiết lập dự án Maven

Tạo một dự án Maven mới hoặc thêm phụ thuộc Aspose.Words vào `pom.xml` hiện có:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Phụ thuộc này sẽ kéo vào tất cả các lớp cần thiết cho việc thao tác tài liệu, bao gồm `Document`, `DocumentBuilder`, `Shape` và `GroupShape`. Maven sẽ tự động tải các JAR khi bạn chạy `mvn compile`.

## Bước 2: Tải tài liệu và tạo DocumentBuilder

`DocumentBuilder` cung cấp API dạng fluent để chèn nội dung. Tải một tệp DOCX hiện có hoặc bắt đầu từ tài liệu trống:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Tạo builder sớm giúp bạn có một con trỏ được đặt ở đầu tài liệu, sẵn sàng cho việc chèn hình.

## Thêm hình chữ nhật vào tài liệu Word

### Bước 3: Chèn hình chữ nhật

Hình chữ nhật là phần tử trực quan đầu tiên chúng ta muốn đặt vào tài liệu. Bằng cách sử dụng constructor `Shape` với `ShapeType.RECTANGLE`, bạn sẽ nhận được một đối tượng có thể chỉnh sửa hoàn toàn.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Việc thêm hình chữ nhật tại thời điểm này không ảnh hưởng đến bố cục cho đến khi kích thước của nó được xác định và nó được đính kèm vào một container.

### Đặt kích thước và kích thước hình

#### Bước 4: Xác định chiều rộng và chiều cao

Đặt kích thước của hình quyết định cách nó hiển thị trên trang. Giá trị chiều rộng và chiều cao được đo bằng điểm (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Bạn có thể điều chỉnh các số này để phù hợp với yêu cầu thiết kế của mình. Các phương thức tương tự áp dụng cho bất kỳ đối tượng `Shape` nào, vì vậy bạn có thể tái sử dụng chúng cho vòng tròn, mũi tên hoặc các bản vẽ tùy chỉnh.

#### Bước 5: Chèn hình chữ nhật vào tài liệu

Bây giờ hình chữ nhật đã có kích thước, hãy đặt nó trên trang. Phương thức `insertShape` của `DocumentBuilder` thêm hình vào vị trí con trỏ hiện tại.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

Ở giai đoạn này, hình chữ nhật xuất hiện riêng lẻ trên trang. Các bước tiếp theo sẽ cho thấy cách kết hợp nó với các hình khác.

## Nhóm nhiều hình lại với nhau

Nhóm các hình cho phép bạn di chuyển, xoay hoặc thay đổi kích thước chúng như một đơn vị duy nhất. Điều này đặc biệt hữu ích khi tạo các sơ đồ phức tạp.

### Bước 6: Tạo container nhóm hình

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Lệnh `insertGroupShape` thêm một container trống vào tài liệu. Bất kỳ hình nào được đính kèm vào container này sẽ trở thành một phần của nhóm.

### Đính kèm hình vào nhóm

#### Bước 7: Thêm hình chữ nhật vào nhóm

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Việc đính kèm di chuyển hình chữ nhật từ thân tài liệu vào bộ sưu tập nội bộ của nhóm. Hình chữ nhật giờ đây tuân theo các biến đổi của nhóm.

#### Bước 8: Thêm một hình ellipse để minh họa

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Hình ellipse chia sẻ cùng không gian tọa độ với hình chữ nhật, vì vậy bạn có thể căn chỉnh chúng một cách trực quan bằng cách điều chỉnh thuộc tính `setLeft` và `setTop` nếu cần.

### Bước 9: Lưu tài liệu

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Chạy chương trình sẽ tạo ra `output.docx`. Mở tệp trong Microsoft Word hoặc LibreOffice; bạn sẽ thấy một hình chữ nhật và một hình ellipse được nhóm lại với nhau. Khi chọn bất kỳ hình nào, toàn bộ nhóm sẽ được đánh dấu, xác nhận rằng **đính kèm hình vào nhóm** đã thành công.

![Ví dụ thêm hình chữ nhật trong Java](image.png){alt="Ví dụ thêm hình chữ nhật trong Java"}

*Ảnh chụp màn hình cho thấy hình chữ nhật và hình bầu dục nằm trong một nhóm duy nhất, sẵn sàng để thao tác chung.*

## Tại sao cách tiếp cận này quan trọng

* **Nguồn duy nhất** – Tất cả thuộc tính hình được đặt trước khi nhóm được tạo, ngăn ngừa các lỗi bố cục.
* **Tái sử dụng** – Các phương thức `setWidth`/`setHeight` hoạt động cho bất kỳ hình nào, vì vậy bạn có thể mở rộng ví dụ này thành mũi tên, ngôi sao hoặc SVG tùy chỉnh.
* **Hiệu năng** – Nhóm giảm số lượng đối tượng vẽ mà bộ render Word phải xử lý, cải thiện tốc độ mở cho các tài liệu lớn.
* **Dễ bảo trì** – Bằng cách giữ logic tạo hình và nhóm cùng nhau, các nhà phát triển trong tương lai có thể sửa đổi kích thước hoặc thêm hình mới mà không phải tìm kiếm trong mã không liên quan.

## Các biến thể phổ biến và trường hợp góc cạnh

| Kịch bản | Điều chỉnh |
|----------|------------|
| **Đơn vị khác nhau** | Sử dụng chuyển đổi `PointsToPixels` hoặc đặt `Shape.setWrapType(WrapType.INLINE)` để đặt vị trí nội tuyến. |
| **Xoay nhóm** | Gọi `groupShape.setRotation(45);` để xoay tất cả các hình con 45°. |
| **Thêm văn bản vào hình** | Sử dụng `Shape.setText("Label");` sau khi đã đặt kích thước. |
| **Kích thước động** | Lấy kích thước trang qua `doc.getFirstSection().getPageSetup().getPageWidth()` và tính kích thước hình theo tỷ lệ. |

Những biến thể này minh họa cách mẫu cốt lõi—**thêm hình chữ nhật**, **đặt kích thước hình**, **nhóm nhiều hình**, **đính kèm hình vào nhóm**—có thể thích ứng với nhiều yêu cầu thực tế.

## Kết luận

Bây giờ bạn đã biết cách **thêm hình chữ nhật** vào tài liệu Word bằng Java, **đặt kích thước hình**, **nhóm nhiều hình**, và **đính kèm hình vào nhóm** một cách sạch sẽ và dễ bảo trì. Ví dụ hoàn chỉnh biên dịch thành một lớp có thể chạy độc lập, và tệp DOCX kết quả thể hiện đầu ra mong đợi.

Từ đây bạn có thể khám phá:

* Thêm nhãn văn bản hoặc siêu liên kết vào mỗi hình.
* Lồng nhóm để xây dựng các sơ đồ phân cấp.
* Xuất tài liệu ra PDF trong khi giữ nguyên các nhóm hình.

Hãy tự do thử nghiệm với các kích thước, màu sắc và các loại hình bổ sung khác nhau. Thành thạo việc thao tác hình mở ra cánh cửa cho việc tạo báo cáo tự động, sơ đồ động và trải nghiệm tài liệu phong phú—tất cả trực tiếp từ mã Java.

## Bạn nên học gì tiếp theo?

Các tutorial sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn hình chữ nhật trong Java – Nhóm và Định vị Hình](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Cách tạo và chèn hình ellipse và hình chữ nhật bên trong một nhóm hình trong tài liệu Word bằng Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Tạo hình chữ nhật trong tài liệu Word bằng Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}