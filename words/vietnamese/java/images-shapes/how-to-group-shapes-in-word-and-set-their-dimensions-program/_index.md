---
category: general
date: 2026-11-25
description: Cách nhóm các hình dạng trong Word bằng Java và cách đặt kích thước hình
  dạng trong tệp DOCX bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: vi
lastmod: 2026-11-25
og_description: Cách nhóm các hình dạng trong Word bằng Aspose.Words Java API và thiết
  lập nhanh kích thước hình. Theo dõi giải pháp đầy đủ từng bước.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Cách nhóm các hình dạng trong Word và đặt kích thước của chúng – Hướng dẫn
  Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Cách nhóm các hình trong Word và thiết lập kích thước của chúng bằng lập trình
url: /vi/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Word và đặt kích thước của chúng bằng chương trình

Nếu bạn cần **cách nhóm các hình dạng trong Word** và kiểm soát kích thước chính xác của chúng, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, có thể chạy được. Sử dụng Aspose.Words for Java, bạn có thể tạo một hình chữ nhật, một hình ellipse, thêm chúng vào một `GroupShape`, và sau đó **cách đặt kích thước hình dạng** như chiều rộng và chiều cao trong một tệp DOCX duy nhất.

Bạn sẽ học cách:

* Tạo một tài liệu Word mới từ đầu.  
* Chèn một `GroupShape` (API mới trong phiên bản 24.9).  
* Thêm một hình chữ nhật và một hình ellipse vào nhóm.  
* **Đặt kích thước hình dạng trong Word** một cách chính xác bằng `setWidth` và `setHeight`.  
* Lưu tài liệu vào đĩa.

Không cần công cụ bên ngoài—chỉ cần Java 17+, Maven và thư viện Aspose.Words for Java.

## Yêu cầu trước

* Java Development Kit 17 hoặc mới hơn.  
* Maven (hoặc Gradle) để quản lý phụ thuộc.  
* Aspose.Words for Java 24.9 hoặc sau (API `GroupShape` được giới thiệu trong 24.9).  
* Kiến thức cơ bản về cú pháp Java và các khái niệm hướng đối tượng.

Nếu bạn chưa thêm Aspose.Words vào dự án của mình, hãy bao gồm phụ thuộc Maven sau:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Bước 1: Tạo tài liệu mới và một DocumentBuilder

Lớp `Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cung cấp cách tiện lợi để thêm nội dung.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this step?*  
Creating a fresh `Document` gives you a clean canvas. `DocumentBuilder` is the high‑level helper that lets you insert paragraphs, tables, and, in this case, shapes.

* Tại sao lại thực hiện bước này?  
Tạo một `Document` mới giúp bạn có một nền trắng sạch sẽ. `DocumentBuilder` là công cụ cấp cao cho phép bạn chèn đoạn văn, bảng và, trong trường hợp này, các hình dạng.

## Bước 2: Chèn một GroupShape (API mới trong phiên bản 24.9)

`GroupShape` hoạt động như một container; bất kỳ hình nào bạn thêm vào đều trở thành một phần của cùng một nhóm hiển thị.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Why use `GroupShape`?*  
Grouping shapes simplifies moving, rotating, or applying formatting to multiple objects at once. The API was added in 24.9, so older versions won’t compile this line.

* Tại sao sử dụng `GroupShape`?  
Nhóm các hình dạng giúp đơn giản hoá việc di chuyển, xoay hoặc áp dụng định dạng cho nhiều đối tượng cùng lúc. API này được thêm vào trong 24.9, vì vậy các phiên bản cũ hơn sẽ không biên dịch được dòng này.

## Bước 3: Tạo một hình chữ nhật, đặt kích thước và thêm nó vào nhóm

Ở đây chúng tôi trình bày **cách đặt kích thước hình dạng** cho một hình chữ nhật.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Why set width and height explicitly?*  
Word stores shape size in points. By calling `setWidth` and `setHeight` you control the exact visual footprint, which is essential when you need precise layout or when exporting to PDF.

* Tại sao phải đặt chiều rộng và chiều cao một cách rõ ràng?  
Word lưu kích thước hình dạng bằng điểm. Bằng cách gọi `setWidth` và `setHeight` bạn kiểm soát chính xác diện tích hiển thị, điều này rất quan trọng khi bạn cần bố cục chính xác hoặc khi xuất ra PDF.

## Bước 4: Tạo một hình ellipse, đặt kích thước và thêm nó vào cùng một nhóm

Kỹ thuật **đặt kích thước hình dạng trong Word** tương tự hoạt động cho bất kỳ loại hình nào.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Why add the ellipse to the same `GroupShape`?*  
Both shapes will move together as a unit. This is useful for creating icons, logos, or complex diagrams that must stay aligned.

* Tại sao lại thêm ellipse vào cùng một `GroupShape`?  
Cả hai hình sẽ di chuyển cùng nhau như một đơn vị. Điều này hữu ích khi tạo biểu tượng, logo hoặc các sơ đồ phức tạp cần giữ căn chỉnh.

## Bước 5: Lưu tài liệu với các hình đã nhóm

Cuối cùng, lưu tệp DOCX vào đĩa.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Chạy chương trình này sẽ tạo ra một tệp có tên **GroupShape.docx** chứa một hình chữ nhật và một hình ellipse được nhóm lại với nhau. Khi bạn mở tệp trong Microsoft Word, bạn sẽ thấy hai hình này hoạt động như một đối tượng duy nhất—bạn có thể kéo, thay đổi kích thước hoặc xoay chúng cùng nhau.

### Kết quả mong đợi

* Một tài liệu Word (`GroupShape.docx`) với một trang.  
* Một `GroupShape` chứa một hình chữ nhật 100 × 50 pt và một hình ellipse 80 × 80 pt.  
* Khi chọn bất kỳ hình nào, cả nhóm sẽ được chọn.

## Các câu hỏi thường gặp và trường hợp đặc biệt

### Cách thay đổi vị trí của các hình đã nhóm?

Sau khi tạo `GroupShape`, bạn có thể đặt các thuộc tính `left` và `top` của nó:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Các tọa độ này cũng được đo bằng điểm.

### Nếu tôi cần thêm hơn hai hình thì sao?

`GroupShape` hoạt động giống như bất kỳ nút container nào khác. Gọi `groupShape.appendChild(yourShape)` cho mỗi hình bổ sung. API không giới hạn số lượng con.

### Tôi có thể áp dụng kiểu (màu nền, độ dày đường viền) cho từng hình riêng lẻ không?

Có. Mỗi đối tượng `Shape` cung cấp các thuộc tính định dạng:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Mã này có hoạt động với các phiên bản Aspose.Words cũ hơn không?

Phương thức `insertGroupShape` được giới thiệu trong phiên bản 24.9. Nếu bạn đang dùng phiên bản cũ hơn, bạn sẽ cần tạo một `GroupShape` thủ công qua cây node, điều này phức tạp hơn. Nâng cấp là con đường được khuyến nghị.

## Mẹo chuyên nghiệp

* **Sử dụng điểm để nhất quán** – Đơn vị nội bộ của Word là điểm (1/72 inch). Chuyển đổi từ pixel hoặc centimet có thể dẫn đến kích thước không mong muốn.  
* **Nhóm trước khi định vị** – Định vị `GroupShape` sau khi bạn đã thêm tất cả các con của nó; nếu không bạn có thể cần tính lại các offset.  
* **Tái sử dụng DocumentBuilder** – Bạn có thể chèn nhiều nhóm trong cùng một tài liệu bằng cách di chuyển con trỏ của builder (`builder.moveTo`) trước mỗi lần gọi `insertGroupShape`.

## Kết luận

Bạn giờ đã có một ví dụ hoàn chỉnh, từ đầu đến cuối về **cách nhóm các hình dạng trong Word** và **cách đặt kích thước hình dạng** bằng Aspose.Words for Java. Bài hướng dẫn đã bao gồm việc tạo tài liệu, chèn một `GroupShape`, thêm một hình chữ nhật và một hình ellipse, đặt kích thước chính xác của chúng, và lưu kết quả.  

Từ đây bạn có thể khám phá:

* Thêm các hộp văn bản hoặc hình ảnh vào cùng một nhóm.  
* Tạo hoạt ảnh cho các hình đã nhóm bằng tính năng smart art của Word (qua API).  
* Xuất các hình đã nhóm ra PDF hoặc SVG để sử dụng trên web.

Hãy tự do thử nghiệm với các loại hình dạng, kích thước và vị trí khác nhau—việc nhóm cung cấp cho bạn khả năng kiểm soát mạnh mẽ các bố cục phức tạp trong tài liệu Word.

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}