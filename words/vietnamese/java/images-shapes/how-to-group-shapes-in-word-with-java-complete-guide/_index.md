---
category: general
date: 2026-10-16
description: Học cách nhóm các hình dạng trong Word bằng Java. Hướng dẫn này cho thấy
  cách thêm hình chữ nhật, thiết lập kích thước và chiều đo của hình, và lưu tài liệu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: vi
lastmod: 2026-10-16
og_description: Nhóm các hình dạng trong Word bằng Java. Thêm hình chữ nhật, đặt kích
  thước và chiều đo của hình, và tạo tài liệu chuyên nghiệp một cách lập trình.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Nhóm các hình dạng trong Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Cách nhóm các hình dạng trong Word bằng Java – hướng dẫn đầy đủ
url: /vi/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Word bằng Java – hướng dẫn đầy đủ

Nếu bạn cần **group shapes in Word** một cách lập trình, hướng dẫn này cung cấp cho bạn một giải pháp sẵn sàng chạy. Bạn sẽ thấy cách **add rectangle shape**, điều chỉnh kích thước, đặt shape dimensions, và cuối cùng lưu một tệp DOCX chứa một hình chữ nhật đã nhóm và một hình bầu dục.

Việc nhóm các hình dạng trong Word hữu ích cho việc xây dựng các sơ đồ phức tạp, tạo các thành phần đồ họa có thể tái sử dụng, hoặc đơn giản là giữ các đối tượng liên quan cùng nhau khi tài liệu được chỉnh sửa sau này. Đoạn mã sử dụng thư viện Aspose.Words for Java, hoạt động với bất kỳ JDK hiện đại nào và không yêu cầu cài đặt Microsoft Word.

## Yêu cầu trước

| Requirement | Reason |
|-------------|--------|
| Java 17 (or later) | Thư viện nhắm tới các môi trường Java hiện đại. |
| Aspose.Words for Java (latest version) | Cung cấp các lớp `Document`, `DocumentBuilder`, `GroupShape` và `Shape` được sử dụng trong ví dụ. |
| An IDE or build tool (Maven/Gradle) | Để biên dịch và chạy mẫu. |
| Basic knowledge of Java syntax | Cần thiết để hiểu luồng mã. |

Thêm phụ thuộc Aspose.Words vào dự án của bạn. Đối với Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Hoặc đối với Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Tổng quan về giải pháp

Hướng dẫn tuân theo một mẫu **problem → solution → explanation** rõ ràng:

1. **Create a new Word document** và lấy một `DocumentBuilder`.  
2. **Insert a `GroupShape` container** sẽ chứa nhiều hình.  
3. **Add a rectangle**, đặt chiều rộng/chiều cao (bước **set shape size**), và gắn nó vào nhóm.  
4. **Add an ellipse**, đặt vị trí bên trong cùng một nhóm, và cũng đặt kích thước của nó.  
5. **Save** tài liệu vào đĩa.  

Mỗi bước đều bao gồm **why** phía sau đoạn mã, giúp bạn hiểu API làm gì và cách bạn có thể điều chỉnh cho các kịch bản khác.

## Bước 1: Tạo tài liệu và DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Why this matters:** `Document` đại diện cho toàn bộ tệp DOCX, trong khi `DocumentBuilder` là một công cụ hỗ trợ cho phép bạn chèn nội dung mà không cần xử lý quản lý node mức thấp. Tạo chúng trước sẽ cung cấp cho bạn một canvas sạch cho tất cả các thao tác hình dạng tiếp theo.

## Bước 2: Chèn một GroupShape container

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Một `GroupShape` hoạt động giống như một **folder** cho các đối tượng vẽ. Khi bạn di chuyển, xoay hoặc xóa nhóm, tất cả các hình con sẽ tự động theo. Đây là cốt lõi của **group shapes in word**.

## Bước 3: Thêm một hình chữ nhật – mã hình chữ nhật

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – Hàm khởi tạo `Shape` nhận `ShapeType.RECTANGLE`, cho phép Aspose.Words vẽ một đường viền hình chữ nhật.  
- **set shape size** – `setWidth` và `setHeight` xác định **shape dimensions** bằng điểm (1 pt = 1/72 in). Đây là cách phổ biến nhất để kiểm soát kích thước hiển thị.  
- **Why we use `appendChild`** – Nó gắn hình chữ nhật vào `GroupShape` để nó di chuyển cùng với nhóm.

## Bước 4: Thêm một ellipse và đặt vị trí bên trong nhóm

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

Ellipse minh họa **set shape dimensions** vượt ra ngoài một hình chữ nhật đơn giản. Bằng cách gọi `setLeft`, chúng ta kiểm soát độ lệch ngang bên trong nhóm, hữu ích khi sắp xếp nhiều đối tượng.

## Bước 5: Lưu tài liệu

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Khi bạn mở *GroupShapeDemo.docx* trong Microsoft Word, bạn sẽ thấy một hình chữ nhật và một ellipse được khóa cùng nhau trong một nhóm duy nhất. Chọn bất kỳ hình nào sẽ chọn toàn bộ nhóm—đúng như bạn mong đợi khi **group shapes in word**.

## Ví dụ đầy đủ, có thể chạy

Đặt tất cả các phần lại với nhau, đây là tệp nguồn hoàn chỉnh bạn có thể sao chép vào IDE của mình:

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Kết quả mong đợi

- Một tệp có tên **GroupShapeDemo.docx** xuất hiện trong thư mục dự án.  
- Mở tệp trong Word hiển thị hai hình (một hình chữ nhật và một ellipse) được nhóm lại với nhau.  
- Kéo bất kỳ hình nào sẽ di chuyển toàn bộ nhóm, xác nhận rằng **group shapes in word** hoạt động như mong đợi.

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Cần thay đổi gì | Lý do |
|----------|----------------|-----|
| **Different shape types** (e.g., triangle) | Sử dụng `ShapeType.TRIANGLE` hoặc bất kỳ giá trị enum nào khác khi khởi tạo `Shape`. | Cho phép bạn xây dựng các sơ đồ phức tạp hơn. |
| **Setting fill color** | Gọi `shape.getFillColor().setColor(Color.BLUE);` sau khi tạo hình. | Cải thiện ngoại hình mà không ảnh hưởng đến việc nhóm. |
| **Rotating the group** | Sử dụng `groupShape.setRotationAngle(45);` | Xoay tất cả các hình con cùng nhau, hữu ích cho các biểu tượng. |
| **Adding text inside a shape** | `shape.appendChild(new Paragraph(document));` sau đó thêm một `Run` chứa văn bản. | Biến hình thành nhãn hoặc chú thích. |
| **Saving to a stream** | Sử dụng `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Hữu ích cho các dịch vụ web trả về tài liệu trực tiếp. |

### Mẹo chuyên nghiệp

Khi bạn cần **set shape dimensions** dựa trên dữ liệu động (ví dụ, độ dài mã vạch), tính trước chiều rộng/chiều cao bằng điểm:

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

## Kết luận

Bây giờ bạn đã biết cách **group shapes in Word** bằng Java, cách **add rectangle shape**, và cách **set shape size** và **set shape dimensions** với mã ngắn gọn, sẵn sàng cho sản xuất. Bằng cách thực hiện các bước trên, bạn có thể tạo các nhóm đồ họa có thể tái sử dụng, nhúng chúng vào báo cáo tự động, hoặc xây dựng công cụ vẽ sơ đồ tùy chỉnh mà không cần mở Word thủ công.

### Tiếp theo là gì?

- Khám phá các biến thể **add rectangle shape** như góc bo tròn (`ShapeType.RECTANGLE` với `setCornerRadius`).  
- Kết hợp **group shapes in word** với bảng hoặc biểu đồ để tạo tài liệu phong phú hơn.  
- Tìm hiểu API Aspose.Words cho **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) để kiểm soát cách văn bản xung quanh tương tác với đồ họa đã nhóm.  

Hãy tự do thử nghiệm, điều chỉnh **rectangle shape code**, và chia sẻ kết quả của bạn

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tạo hình chữ nhật trong Word bằng Java – Hướng dẫn đầy đủ](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}