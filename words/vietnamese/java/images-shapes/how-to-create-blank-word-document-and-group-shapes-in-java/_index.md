---
category: general
date: 2026-09-27
description: Tạo một tài liệu Word trống trong Java và nhóm các hình dạng bằng Aspose.Words.
  Học cách đặt kích thước hình dạng, đặt màu nền cho hình dạng và thêm phần tử con
  vào nhóm.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: vi
lastmod: 2026-09-27
og_description: Tạo tài liệu Word trống trong Java bằng Aspose.Words. Hướng dẫn này
  cho thấy cách nhóm các hình dạng trong Word, đặt kích thước hình dạng, đặt màu nền
  cho hình dạng và thêm phần tử con vào nhóm.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Tạo tài liệu Word trống và nhóm các hình dạng trong Java – hướng dẫn từng
  bước
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cách tạo tài liệu Word trống và nhóm các hình dạng trong Java
url: /vi/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống và nhóm các hình dạng trong Java

Nếu bạn cần **create blank word document** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words for Java. Bạn cũng sẽ học cách **group shapes in word**, đặt kích thước cho mỗi hình dạng, áp dụng màu nền, và **append child to group** để các đối tượng hoạt động như một đơn vị duy nhất.

Làm việc với các tệp Word từ mã giúp bạn tránh việc định dạng thủ công và cho phép tự động tạo báo cáo, hợp đồng hoặc brochure marketing. Khi kết thúc hướng dẫn này, bạn sẽ có một chương trình Java có thể chạy được tạo ra tệp `.docx` chứa một hình chữ nhật màu xanh và một hình ảnh, cả hai được nhóm lại với nhau.

## Yêu cầu trước

- Java 17 (hoặc bất kỳ JDK nào mới) đã được cài đặt.
- Maven hoặc Gradle để quản lý các phụ thuộc.
- Giấy phép Aspose.Words for Java (phiên bản dùng thử miễn phí hoạt động cho việc thử nghiệm).
- Một tệp ảnh mẫu (ví dụ, `sample.jpg`) được đặt trong thư mục mà bạn có thể tham chiếu từ mã.

> **Mẹo chuyên nghiệp:** Giữ các tệp ảnh của bạn trong thư mục `resources` và tải chúng bằng `ClassLoader.getResourceAsStream` để tránh các đường dẫn tuyệt đối được mã hoá cứng.

## Bước 1: Tạo tài liệu Word trống và thêm một GroupShape

Bước đầu tiên là khởi tạo một đối tượng `Document` mới, đại diện cho một tệp Word trống, sau đó chèn một `GroupShape`. Nhóm sẽ đóng vai trò là một container cho bất kỳ hình dạng nào bạn thêm sau này.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Tại sao điều này quan trọng:* Một `GroupShape` cho phép bạn di chuyển, xoay hoặc định dạng nhiều hình dạng cùng nhau, điều này rất cần thiết cho các bố cục phức tạp như sơ đồ hoặc watermark.

## Bước 2: Chèn một hình chữ nhật và **set shape size**

Tiếp theo, tạo một hình chữ nhật, xác định kích thước của nó và thêm vào nhóm. Điều này minh họa thao tác **set shape size**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Giải thích:* `setWidth` và `setHeight` kiểm soát kích thước chính xác của hình dạng tính bằng point (1 point = 1/72 inch). Điều chỉnh các giá trị này để phù hợp với yêu cầu bố cục của bạn.

## Bước 3: **Set shape fill color** cho hình chữ nhật

Nền của hình chữ nhật được đặt thành màu xanh bằng `setFillColor`. Bạn có thể sử dụng bất kỳ hằng số `java.awt.Color` nào hoặc tạo màu RGB tùy chỉnh.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Lý do hữu ích:* Màu nền giúp phân biệt các đối tượng một cách trực quan, đặc biệt khi bạn xuất tài liệu sang PDF hoặc in nó.

## Bước 4: Chèn một hình ảnh và **append child to group**

Bây giờ thêm một hình ảnh vào cùng một `GroupShape`. Hình ảnh được chèn bằng `DocumentBuilder.insertImage`, sau đó được thêm vào nhóm để nó di chuyển cùng với hình chữ nhật.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Trường hợp đặc biệt:* Nếu đường dẫn hình ảnh sai, Aspose.Words sẽ ném `FileNotFoundException`. Sử dụng đường dẫn tương đối hoặc tải hình ảnh từ resources để tránh vấn đề này.

## Bước 5: **Save the document with the grouped shapes**

Cuối cùng, ghi tài liệu ra đĩa. Tệp kết quả sẽ chứa hình chữ nhật và hình ảnh được nhóm lại với nhau.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Kết quả mong đợi

- Một tệp có tên `GroupShape.docx` xuất hiện trong thư mục đã chỉ định.
- Mở tệp trong Microsoft Word hiển thị một trang trống với một hình chữ nhật màu xanh và hình ảnh đã chọn, cả hai được chọn như một đối tượng duy nhất (bạn có thể di chuyển hoặc thay đổi kích thước chúng cùng nhau).

![create blank word document with grouped shapes](/images/grouped-shapes.png "create blank word document with grouped shapes")

*Ảnh chụp màn hình trên minh họa các hình dạng đã được nhóm cuối cùng trong tài liệu Word mới tạo.*

## Các biến thể phổ biến và mẹo bổ sung

| Tình huống | Cách xử lý |
|-----------|------------|
| **Multiple images** | Chèn mỗi hình ảnh bằng `builder.insertImage` và gọi `group.appendChild(picture)` cho mỗi hình. |
| **Different shape types** | Sử dụng `ShapeType.OVAL`, `ShapeType.LINE`, v.v., khi tạo đối tượng `Shape`. |
| **Changing group position** | Sau khi thêm tất cả các phần tử con, đặt `group.setLeft(x)` và `group.setTop(y)` để di chuyển toàn bộ nhóm. |
| **Export to PDF** | Gọi `doc.save("output.pdf")` sau khi nhóm; PDF sẽ giữ nguyên việc nhóm. |
| **License enforcement** | Nếu bạn chạy phiên bản dùng thử, sẽ xuất hiện watermark. Cài đặt giấy phép hợp lệ để loại bỏ nó. |

## Kết luận

Bây giờ bạn đã biết cách **create blank word document**, chèn một **GroupShape**, **set shape size**, **set shape fill color**, và **append child to group** bằng Aspose.Words for Java. Mô hình này cho phép bạn xây dựng các bố cục phức tạp, lập trình được, có thể chỉnh sửa sau này trong Word hoặc xuất sang các định dạng khác.

Tiếp theo, khám phá cách **group shapes in word** với các hộp văn bản, thêm siêu liên kết vào các hình dạng, hoặc tự động tạo báo cáo đa trang. Các nguyên tắc giống nhau—chỉ cần tạo thêm các hình dạng, cấu hình thuộc tính của chúng, và thêm chúng vào cùng một nhóm.

Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo hình chữ nhật trong Word bằng Java – Hướng dẫn đầy đủ](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}