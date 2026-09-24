---
category: general
date: 2026-09-24
description: Tìm hiểu cách tạo tài liệu Word trống trong Java và nhóm các hình dạng
  như hình chữ nhật và đường thẳng bằng Aspose.Words. Bao gồm mã từng bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: vi
lastmod: 2026-09-24
og_description: Tạo một tài liệu Word trống trong Java và học cách nhóm các hình dạng,
  thêm một hình chữ nhật và đặt kích thước hình dạng bằng Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Tạo tài liệu Word trống và nhóm các hình dạng trong Java – hướng dẫn từng
  bước
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cách tạo tài liệu Word trống và nhóm các hình dạng trong Java
url: /vi/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống và nhóm các hình dạng trong Java

Nếu bạn cần **tạo một tài liệu Word trống** và sau đó sắp xếp nhiều đối tượng vẽ, hướng dẫn này sẽ cho bạn biết chính xác cách thực hiện. Sử dụng Aspose.Words for Java, bạn có thể chèn một group shape, thêm một rectangle shape, vẽ một đường line, và kiểm soát kích thước cũng như vị trí của mỗi hình dạng — tất cả trong một chương trình có thể chạy được.

Bạn sẽ đi qua từng bước, từ khởi tạo tài liệu đến lưu file `.docx` cuối cùng. Khi kết thúc, bạn sẽ hiểu **cách nhóm các hình dạng**, **thêm rectangle shape**, và **đặt kích thước hình dạng** để các file Word của bạn trông đúng như mong muốn.

## Yêu cầu trước

- Java 17 hoặc mới hơn (mã sẽ biên dịch với bất kỳ JDK hiện đại nào)
- Thư viện Aspose.Words for Java (tải về từ [Aspose website](https://products.aspose.com/words/java))
- Một IDE hoặc công cụ xây dựng (Maven/Gradle) có thể thêm file JAR của Aspose.Words vào classpath
- Kiến thức cơ bản về cú pháp Java

> **Mẹo chuyên nghiệp:** Sử dụng Maven để quản lý phụ thuộc; thêm `com.aspose:aspose-words:23.12` (hoặc phiên bản mới nhất) vào `pom.xml` của bạn.

## Bước 1: Tạo tài liệu Word trống

Nhiệm vụ đầu tiên là **tạo một tài liệu Word trống**. Điều này cung cấp cho bạn một canvas sạch sẽ để bạn có thể chèn các hình dạng sau này.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Tại sao điều này quan trọng:* Đối tượng `Document` đại diện cho toàn bộ file `.docx`. Bắt đầu với một tài liệu trống đảm bảo không có định dạng ẩn can thiệp vào các hình dạng bạn sẽ thêm.

## Bước 2: Chèn một group shape – container cho nhiều đối tượng

**Group shape** hoạt động như một container cho phép bạn di chuyển, thay đổi kích thước hoặc xoay nhiều hình dạng cùng một lúc. Đây là cốt lõi của **cách nhóm các hình dạng** trong Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Giải thích:* Phương thức `insertGroupShape` tạo một đối tượng `GroupShape` và đặt nó tại vị trí con trỏ hiện tại. Tất cả các hình dạng tiếp theo mà bạn `appendChild` vào nhóm này sẽ được xem như một đơn vị duy nhất.

## Bước 3: Thêm rectangle shape và đặt kích thước của nó

Bây giờ chúng ta **thêm rectangle shape** vào nhóm và **đặt kích thước hình dạng** một cách chính xác.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Tại sao bạn cần đặt kích thước hình dạng:* Chiều rộng và chiều cao kiểm soát cách rectangle hiển thị trên trang. Các phương thức `setLeft` và `setTop` định vị rectangle so với gốc của nhóm, cung cấp cho bạn kiểm soát bố cục pixel‑perfect.

## Bước 4: Thêm line shape và cấu hình kích thước của nó

Một line là một đối tượng vẽ phổ biến khác. Chúng ta sẽ áp dụng logic **thêm rectangle shape** cho line, cho thấy các nguyên tắc định kích thước tương tự áp dụng.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Điểm chính:* Mặc dù line không có chiều cao, bạn vẫn sử dụng `setWidth` để xác định độ dài của nó. Việc định vị (`setLeft`, `setTop`) tuân theo cùng hệ tọa độ như các hình dạng khác.

## Bước 5: Lưu tài liệu với các hình dạng đã nhóm

Cuối cùng, lưu các thay đổi bằng cách lưu tài liệu. Điều này tạo ra một file `.docx` mà bạn có thể mở trong Microsoft Word để kiểm tra kết quả.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Kết quả mong đợi:** Mở `GroupShapeDemo.docx` sẽ hiển thị một trang trống chứa một rectangle và line đã được nhóm. Khi chọn bất kỳ hình dạng nào, toàn bộ nhóm sẽ được chọn, cho phép bạn di chuyển chúng cùng nhau.

## Các câu hỏi thường gặp và xử lý các trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| *Tôi có thể thêm nhiều hơn hai hình dạng vào nhóm không?* | Có. Gọi `group.appendChild(yourShape)` cho mỗi hình dạng bổ sung. |
| *Nếu tôi cần một đơn vị khác (ví dụ: centimet) cho kích thước thì sao?* | Aspose.Words sử dụng đơn vị point (1 point = 1/72 inch). Chuyển đổi bằng cách dùng `Points = centimeters * 28.3465`. |
| *Nhóm có giữ nguyên bố cục khi tài liệu được mở trên máy khác không?* | Chắc chắn. Tất cả dữ liệu kích thước và vị trí được lưu trong file `.docx`, giúp bố cục di động. |
| *Làm sao để tách nhóm các hình dạng sau này?* | Lấy đối tượng `GroupShape`, sau đó lặp qua `group.getChildNodes(NodeType.SHAPE, true)` và di chuyển mỗi child ra khỏi nhóm. |
| *Nếu tôi cần xoay toàn bộ nhóm thì sao?* | Sử dụng `group.setRotationAngle(double angleInDegrees)` trước khi lưu. |

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào IDE của mình. Nó bao gồm tất cả các import cần thiết và chú thích.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Chạy chương trình, mở `GroupShapeDemo.docx` trong Microsoft Word, và bạn sẽ thấy các hình dạng đã nhóm chính xác như mô tả.

## Kết luận

Bây giờ bạn đã biết cách **tạo một tài liệu Word trống**, **nhóm các hình dạng trong Word**, **thêm rectangle shape**, và **đặt kích thước hình dạng** bằng Aspose.Words for Java. Bằng cách đặt các hình dạng vào bên trong một `GroupShape`, bạn có được kiểm soát hoàn toàn về vị trí, tỷ lệ và xoay chung — lý tưởng cho sơ đồ, lưu đồ, hoặc đồ họa tùy chỉnh được nhúng trong các báo cáo tự động.

**Bước tiếp theo:**  
- Khám phá **cách nhóm các hình dạng** với các đối tượng phức tạp hơn như hình ảnh hoặc text box.  
- Thử nghiệm `setRotationAngle` để xoay toàn bộ nhóm.  
- Kết hợp kỹ thuật này với mail‑merge để tạo các tài liệu cá nhân hoá có bao gồm đồ họa thương hiệu.

Bạn có thể tự do điều chỉnh mã cho các dự án của mình, và chia sẻ kết quả trong phần bình luận!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo rectangle shape trong Word bằng Java – Hướng dẫn đầy đủ](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Tạo tài liệu Word Java – Thêm rectangle shape với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}