---
category: general
date: 2026-08-20
description: Tìm hiểu cách nhóm các hình dạng, đặt kích thước hình dạng, chèn hình
  ảnh vào tài liệu, thêm hình ảnh vào nhóm và tạo hình chữ nhật với Aspose.Words trong
  Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: vi
lastmod: 2026-08-20
og_description: Cách nhóm các hình dạng trong tài liệu Word bằng Aspose.Words. Hãy
  làm theo hướng dẫn Java từng bước này để thiết lập kích thước hình dạng, chèn ảnh
  vào tài liệu, thêm hình ảnh vào nhóm và tạo hình chữ nhật.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Cách nhóm các hình dạng trong tài liệu Word bằng Aspose.Words – Hướng dẫn
  Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Cách nhóm các hình dạng trong tài liệu Word bằng Aspose.Words
url: /vi/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong tài liệu Word bằng Aspose.Words

Nếu bạn cần **cách nhóm các hình dạng** trong một tệp Word, hướng dẫn này sẽ trình bày giải pháp Java đầy đủ. Bạn sẽ thấy cách **đặt kích thước hình dạng**, **chèn hình ảnh vào tài liệu**, **thêm ảnh vào nhóm**, và **tạo hình chữ nhật** — tất cả đều kèm giải thích rõ ràng và mẫu mã có thể chạy được.

Việc nhóm các hình dạng giúp đơn giản hoá quản lý bố cục, cho phép bạn di chuyển hoặc xoay nhiều đối tượng như một đơn vị duy nhất, và giữ cho tài liệu của bạn gọn gàng. Trong các bước dưới đây, bạn sẽ tạo một nhóm chứa một hình chữ nhật và một bức ảnh, sau đó đặt nhóm này lên trang.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* Java 17 hoặc mới hơn được cài đặt.
* Aspose.Words for Java (phiên bản 23.9 trở lên) đã được thêm vào classpath của dự án.
* Một ảnh JPEG mẫu tại `YOUR_DIRECTORY/sample.jpg` (thay `YOUR_DIRECTORY` bằng đường dẫn thực tế).

Bạn có thể thêm Aspose.Words qua Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Cách nhóm các hình dạng với Aspose.Words

Các phần sau sẽ hướng dẫn từng thao tác cần thiết để **cách nhóm các hình dạng**. Tiêu đề H2 chính chứa từ khóa chính, đáp ứng các quy tắc SEO.

### Bước 1: Tạo tài liệu mới và một `DocumentBuilder`

`Document` đại diện cho tệp Word, trong khi `DocumentBuilder` cung cấp các phương thức tiện lợi để chèn nội dung.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Lý do quan trọng*: Bắt đầu với một `Document` mới đảm bảo rằng nhóm bạn tạo sẽ không gây xung đột với các phần tử đã tồn tại.

### Bước 2: Chèn một hình dạng nhóm sẽ chứa nhiều hình dạng con

Một hình dạng nhóm hoạt động như một container. Kích thước của nó xác định hộp bao cho tất cả các hình dạng con.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Mẹo*: Chiều rộng (`300`) và chiều cao (`200`) được tính bằng điểm (1 pt = 1/72 inch). Điều chỉnh chúng dựa trên kích thước của các hình dạng bạn dự định thêm.

### Bước 3: Tạo một hình chữ nhật, đặt kích thước và thêm vào nhóm

Đặt kích thước chính xác cho một hình dạng là cần thiết khi bạn muốn kiểm soát bố cục một cách chính xác.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Tại sao chúng ta đặt kích thước hình dạng*: Các phương thức `setWidth` và `setHeight` tương ứng với từ khóa phụ **set shape size**, cho phép bạn kiểm soát pixel‑perfect về giao diện của hình chữ nhật.

### Bước 4: Chèn một ảnh, sau đó thêm hình ảnh vào cùng một nhóm

Việc chèn ảnh là phần cốt lõi của yêu cầu **insert image into document**. Đối tượng `Shape` trả về là một hình ảnh có thể được nhóm giống như bất kỳ hình dạng nào khác.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Pro tip*: Nếu bạn cần giữ tỷ lệ khung hình gốc, chỉ đặt một trong hai kích thước (`setWidth` hoặc `setHeight`). Aspose.Words sẽ tự động tỷ lệ kích thước còn lại.

### Bước 5: Đặt vị trí cho toàn bộ nhóm trên trang

Sau khi đã thêm tất cả các hình dạng con, bạn có thể di chuyển, xoay hoặc ẩn toàn bộ nhóm. Việc định vị sử dụng khái niệm **add picture to group** một cách gián tiếp, vì nhóm hiện đã chứa ảnh.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Giải thích*: `setLeft` và `setTop` đặt nhóm tương đối với lề trang. Việc xoay nhóm cho thấy tất cả các hình dạng con kế thừa phép biến đổi này.

### Bước 6: Lưu tài liệu

Cuối cùng, ghi tệp ra đĩa. Bạn có thể mở file `.docx` kết quả trong Word để xác nhận việc nhóm.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

Chạy chương trình sẽ tạo **GroupShapesDemo.docx** chứa một hình chữ nhật và một ảnh được gộp lại. Khi chọn bất kỳ hình dạng nào trong Word, hình dạng còn lại cũng sẽ được chọn, xác nhận rằng bạn đã thành công trong việc **cách nhóm các hình dạng**.

---

## Kết quả mong đợi

Khi bạn mở *GroupShapesDemo.docx* trong Microsoft Word:

* Một hình chữ nhật (đổ màu vàng) xuất hiện ở phía trái của nhóm.
* Ảnh bạn cung cấp xuất hiện ở phía phải của hình chữ nhật.
* Cả hai đối tượng di chuyển cùng nhau khi bạn kéo nhóm.
* Nhóm được đặt cách lề trái 50 pt và cách lề trên 100 pt, xoay 15°.

Nếu ảnh không hiển thị, hãy kiểm tra lại đường dẫn tệp trong `insertImage`. Aspose.Words sẽ ném `IOException` khi không tìm thấy tệp.

---

## Các câu hỏi thường gặp và xử lý trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes?** | Yes. Call `groupShape.appendChild(otherShape)` for each additional shape. |
| **What if I need a transparent background for the rectangle?** | Use `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Is grouping supported in older Word formats (e.g., `.doc`)?** | Grouping works for `.docx` and `.doc` but some older viewers may ignore the group metadata. Save as `.docx` for full fidelity. |
| **How do I ungroup later?** | Retrieve the child nodes via `groupShape.getChildNodes(NodeType.ANY, true)` and move them to the document body, then remove the group. |
| **Can I group shapes across different sections?** | No. A `GroupShape` must reside within a single `Story` (usually the main document body). |

---

## Mẹo chuyên nghiệp để xử lý hình dạng một cách vững chắc

* **Sử dụng vị trí tuyệt đối một cách hạn chế** – vị trí tương đối (`builder.moveToDocumentEnd()`) thường tạo bố cục linh hoạt hơn.
* **Cache `DocumentBuilder`** – tạo một builder mới cho mỗi thao tác có thể làm giảm hiệu năng trên tài liệu lớn.
* **Đặt `PictureFillMode`** khi bạn cần ảnh kéo dài hoặc lặp lại bên trong hình dạng: `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Xác thực kích thước ảnh** trước khi chèn để tránh việc co giãn không mong muốn ảnh hưởng tới hộp bao của nhóm.

---

## Các bước tiếp theo

Bây giờ bạn đã biết **cách nhóm các hình dạng**, bạn có thể khám phá:

* **Insert image into document** với các tùy chọn nâng cao như cắt ảnh (`pictureShape.setCropTop(...)`).
* **Set shape size** một cách động dựa trên kích thước trang (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Add picture to group** cùng với các hộp văn bản để tạo đồ họa có chú thích.
* **Create rectangle shape** với góc bo tròn (`rectangleShape.setCornerRadius(5);`).

Những chủ đề này dựa trên cùng một API và giúp bạn tạo các báo cáo Word phức tạp, được tạo lập bằng mã.

---

## Kết luận

Trong hướng dẫn này, bạn đã học **cách nhóm các hình dạng** trong tài liệu Word bằng Aspose.Words for Java. Bằng cách thực hiện sáu bước—tạo tài liệu, chèn nhóm, **tạo hình chữ nhật**, **đặt kích thước hình dạng**, **chèn ảnh vào tài liệu**, **thêm ảnh vào nhóm**, và định vị nhóm—bây giờ bạn đã có một mẫu có thể tái sử dụng cho các kịch bản bố cục phức tạp. Hãy thoải mái thử nghiệm thêm các hình dạng con, các góc xoay khác nhau, hoặc logic nhóm có điều kiện để phù hợp với nhu cầu ứng dụng của bạn.

Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong bài viết này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}