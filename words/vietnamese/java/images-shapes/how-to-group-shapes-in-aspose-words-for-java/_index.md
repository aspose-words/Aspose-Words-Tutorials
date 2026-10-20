---
category: general
date: 2026-10-20
description: Cách nhóm các hình dạng trong Aspose.Words cho Java – học cách chèn hình
  chữ nhật, nhóm chúng và lưu tài liệu trong một hướng dẫn duy nhất.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: vi
lastmod: 2026-10-20
og_description: Cách nhóm các hình dạng trong Aspose.Words cho Java. Hướng dẫn này
  cho thấy cách chèn hình chữ nhật, nhóm chúng và xuất kết quả.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Cách nhóm các hình dạng trong Aspose.Words cho Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Cách nhóm các hình dạng trong Aspose.Words cho Java
url: /vi/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Aspose.Words cho Java

Nếu bạn cần **cách nhóm các hình dạng** trong một tài liệu Word bằng Aspose.Words cho Java, hướng dẫn này sẽ cho bạn quy trình hoàn chỉnh. Bạn sẽ học cách **chèn hình chữ nhật**, thêm một hình chữ nhật thứ hai, nhóm hai hình lại với nhau, và cuối cùng lưu tệp—tất cả với mã rõ ràng, có thể chạy được.

Nhóm các hình dạng hữu ích khi bạn muốn di chuyển, xoay hoặc định dạng nhiều bản vẽ như một đơn vị duy nhất. Dù bạn đang xây dựng mẫu báo cáo, sơ đồ, hay tờ rơi tùy chỉnh, việc thành thạo nhóm hình dạng sẽ tiết kiệm thời gian và giữ cho bố cục nhất quán.

Trong tutorial này bạn sẽ:

* Tạo một `Document` mới và một `DocumentBuilder`.
* **Cách chèn hình chữ nhật** với kích thước chính xác.
* Nhóm các hình chữ nhật vào một `GroupShape`.
* Lưu tài liệu và xác minh kết quả.

> **Yêu cầu trước** – Bạn phải có Aspose.Words cho Java (v23.12 hoặc mới hơn) được thêm vào dự án của mình. Người dùng Maven có thể bao gồm phụ thuộc như dưới đây.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Những gì bạn cần

| Mục | Lý do |
|------|--------|
| Java 17+ | Các tính năng ngôn ngữ hiện đại và hiệu năng tốt hơn |
| Aspose.Words for Java | Cung cấp các API `DocumentBuilder`, `Shape`, và `GroupShape` |
| Một IDE (IntelliJ IDEA, Eclipse, VS Code, v.v.) | Để biên dịch và chạy ví dụ |
| Quyền ghi vào một thư mục | Tài liệu sẽ được lưu vào đĩa |

---

## Cách chèn hình chữ nhật

Bước đầu tiên là tạo một `Document` và một `DocumentBuilder`. Builder cung cấp các phương thức như `insertShape` để đặt các đối tượng vẽ.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Tại sao điều này quan trọng** – Sử dụng `insertShape` là cách chuẩn **cách chèn hình chữ nhật** trong Aspose.Words. Nó tự động thêm hình vào đoạn hiện tại của tài liệu, vì vậy bạn không cần quản lý OpenXML mức thấp.

---

## Điều chỉnh vị trí hình chữ nhật (tùy chọn)

Nếu hình chữ nhật thứ hai cần vị trí tùy chỉnh so với hình đầu tiên, bạn có thể sửa đổi các thuộc tính `left` và `top` của nó. Bước này là tùy chọn nhưng thường cần cho bố cục sơ đồ chính xác.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Mẹo chuyên nghiệp:** Tất cả các đo lường đều tính bằng điểm (1 pt ≈ 1/72 in). Sử dụng `convertPointsToPixels` nếu bạn cần giá trị pixel cho các phép tính dựa trên giao diện người dùng.

---

## Cách nhóm các hình dạng

Bây giờ các hình chữ nhật đã tồn tại, bạn có thể đặt chúng vào trong một `GroupShape`. Việc nhóm khiến hai hình chữ nhật hành xử như một đối tượng duy nhất—di chuyển, xoay hoặc định dạng nhóm sẽ ảnh hưởng đến cả hai hình.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Tại sao việc nhóm hoạt động** – `GroupShape` kế thừa từ `Shape`, vì vậy bạn có thể xử lý nhóm giống như bất kỳ đối tượng vẽ nào khác. Khi bạn gọi `appendChild`, các hình sẽ được loại bỏ khỏi vị trí gốc và trở thành con của nhóm.

---

## Lưu tài liệu chứa các hình đã nhóm

Cuối cùng, ghi tài liệu ra đĩa. Tệp sẽ chứa một `GroupShape` duy nhất với hai hình chữ nhật bên trong.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Kết quả mong đợi

Mở `GroupShape.docx` trong Microsoft Word:

* Bạn sẽ thấy hai hình chữ nhật (màu xanh và màu xanh lá) được đặt cạnh nhau.
* Khi chọn bất kỳ hình chữ nhật nào, toàn bộ nhóm sẽ được chọn—kéo sẽ di chuyển cả hai cùng lúc.
* Nhóm có viền đỏ mỏng, xác nhận rằng các thuộc tính `GroupShape` đã được áp dụng.

Nếu bạn nhấp chuột phải vào nhóm và chọn **Group → Ungroup**, các hình chữ nhật sẽ trở lại dạng độc lập, chứng tỏ thao tác nhóm có thể được đảo ngược.

---

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Cách xử lý |
|-----------|------------------|
| **Nhiều hơn hai hình** | Chèn mỗi hình, sau đó thêm tất cả vào cùng một `GroupShape`. |
| **Các loại hình dạng khác nhau** (ví dụ: ellipse, picture) | Sử dụng `builder.insertShape(ShapeType.ELLIPSE, …)` hoặc `builder.insertImage(...)` trước khi thêm. |
| **Phóng to/thu nhỏ nhóm** | Gọi `group.setWidth(newWidth)` hoặc `group.setHeight(newHeight)`; các con sẽ tỷ lệ theo. |
| **Xoay nhóm** | `group.setRotationAngle(45);` xoay toàn bộ bộ sưu tập quanh trung tâm. |
| **Giữ nguyên vị trí gốc** | Lưu `left`/`top` của mỗi hình trước khi nhóm và khôi phục lại sau khi tách nếu cần. |

---

## Ví dụ đầy đủ, có thể chạy

Dưới đây là lớp Java hoàn chỉnh mà bạn có thể sao chép‑dán vào IDE. Nó bao gồm tất cả các import, xử lý lỗi và chú thích để rõ ràng.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Chạy chương trình, mở `GroupShape.docx` tạo ra, và bạn sẽ thấy các hình chữ nhật đã được nhóm chính xác như mô tả.

---

## Kết luận

Bạn giờ đã biết **cách nhóm các hình dạng** trong Aspose.Words cho Java, từ tạo tài liệu, chèn hình chữ nhật, điều chỉnh vị trí, đến cuối cùng nhóm chúng bằng `GroupShape`. Kỹ thuật này cho phép bạn xử lý nhiều bản vẽ như một thực thể duy nhất, đơn giản hoá việc điều chỉnh bố cục và duy trì tính nhất quán về hình ảnh.

**Bước tiếp theo**

* Khám phá **cách chèn hình chữ nhật** với các mẫu nền hoặc viền khác nhau.
* Kết hợp **chèn hình chữ nhật** với các hộp văn bản để tạo sơ đồ có nhãn.
* Thử nghiệm xoay hoặc thu phóng nhóm để tạo ra các đồ họa phức tạp hơn.

Hãy tự do điều chỉnh mã cho các loại hình dạng khác, nhóm lớn hơn, hoặc các kịch bản tạo tài liệu động. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ, hoạt động với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn hình chữ nhật trong Java – Nhóm và Định vị các hình dạng](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [cách chèn nhóm hình trong Java – Hướng dẫn đầy đủ](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Cách đặt bóng cho hình dạng trong Aspose.Words – Hướng dẫn đầy đủ](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}