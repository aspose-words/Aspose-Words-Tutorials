---
category: general
date: 2026-10-13
description: Học cách tạo các hình dạng nhóm trong Word bằng Java. Hướng dẫn này chỉ
  cho bạn cách chèn hình nhóm, thêm đường vào nhóm và nhóm nhiều hình dạng trên toàn
  bộ tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: vi
lastmod: 2026-10-13
og_description: Tạo các hình dạng nhóm trong Word bằng Java. Theo dõi hướng dẫn đầy
  đủ này để chèn hình dạng nhóm, thêm đường vào nhóm và nhóm nhiều hình dạng trong
  tài liệu Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Tạo các hình dạng nhóm trong Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Cách tạo các hình dạng nhóm trong tài liệu Word bằng Java
url: /vi/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo các hình dạng được nhóm trong tài liệu Word bằng Java

Nếu bạn cần **tạo các hình dạng được nhóm** trong một tệp Microsoft Word từ Java, hướng dẫn này sẽ đưa bạn qua toàn bộ quy trình. Bạn sẽ thấy cách **chèn group shape**, đặt một hình chữ nhật và một đường thẳng bên trong cùng một container, và cuối cùng lưu tài liệu với các đồ họa đã được nhóm.

Nhóm các hình dạng giúp di chuyển, thay đổi kích thước hoặc định dạng nhiều đối tượng vẽ như một đơn vị duy nhất—rất phù hợp cho sơ đồ, lưu đồ hoặc trang trí tùy chỉnh. Khi kết thúc hướng dẫn, bạn sẽ có thể **add line to group**, **group multiple shapes word** tài liệu, và tái sử dụng kỹ thuật này cho bất kỳ số lượng hình dạng nào.

## Prerequisites

- Java 17 hoặc phiên bản mới hơn đã được cài đặt trên máy phát triển của bạn.  
- Giấy phép Aspose.Words for Java (hoặc bản dùng thử miễn phí).  
- Dự án Maven hoặc Gradle nơi bạn có thể thêm phụ thuộc Aspose.Words:

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Không cần thư viện bổ sung nào khác.

## Step 1: Insert the group shape container

Bước đầu tiên là **insert group shape** vào tài liệu. Container này sẽ chứa mọi hình dạng tiếp theo.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` tạo một đối tượng `Shape` trống loại `GROUPSHAPE`. Hãy nghĩ nó như một canvas trong suốt có thể chứa các đối tượng vẽ khác.

## Step 2: Add a rectangle to the group

Một hình chữ nhật thường được dùng làm nền trực quan cho một nhóm các hình dạng.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Đặt `Left` và `Top` thành `0` sẽ đặt hình chữ nhật ở góc trên‑trái của nhóm. Bạn có thể thay đổi các giá trị này để dịch chuyển hình trong nhóm.

## Step 3: **Add line to group** – create a line shape

Bây giờ chúng ta **add line to group**. Đường thẳng sẽ xuất hiện dưới hình chữ nhật.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

Thuộc tính `Top` di chuyển đường thẳng xuống 60 points dưới hình chữ nhật, tạo một bố cục xếp chồng đơn giản. Bạn cũng có thể đặt `Left` nếu cần dịch chuyển theo chiều ngang.

## Step 4: Save the document with the grouped shapes

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Khi bạn mở `GroupShapeDemo.docx` trong Microsoft Word, sẽ thấy một nhóm duy nhất chứa cả hình chữ nhật và đường thẳng. Việc chọn nhóm cho phép bạn di chuyển cả hai hình cùng lúc, chứng tỏ bạn đã **group multiple shapes word** thành công.

## Full, runnable example

Dưới đây là chương trình hoàn chỉnh với tất cả các import và xử lý lỗi. Sao chép vào IDE, thay `YOUR_DIRECTORY` bằng đường dẫn thư mục tồn tại, và chạy.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Expected output

- Một tệp có tên `GroupShapeDemo.docx` xuất hiện trong thư mục đích.  
- Mở tệp trong Word sẽ hiển thị một đối tượng được nhóm duy nhất, chứa hình chữ nhật ở trên và đường thẳng ở dưới.  
- Kéo nhóm sẽ di chuyển cả hai hình cùng lúc, xác nhận rằng bạn đã **created grouped shapes** thành công.

## Tips and common pitfalls

- **Pro tip:** Nếu bạn cần xoay hoặc định dạng các hình riêng lẻ bên trong nhóm, hãy gọi các setter tương ứng (`setRotation`, `getFill().setForeColor`, v.v.) trước khi thêm chúng vào nhóm. Nhóm sẽ giữ lại các thuộc tính hình ảnh đó.  
- **Watch out for:** Quên đặt thuộc tính `Top` cho đường thẳng có thể gây chồng lấn lên hình chữ nhật, làm cho nhóm trông lộn xộn.  
- **Edge case:** Khi bạn thêm nhiều hơn hai hình, hãy nhớ rằng tọa độ của mỗi child được tính tương đối so với gốc của nhóm (0,0). Hãy lên kế hoạch bố cục cho phù hợp.  
- **Performance note:** Nhóm một số lượng lớn hình (hàng trăm) có thể làm tăng kích thước tệp hơi lên, nhưng nó giúp việc chỉnh sửa sau này trong Word trở nên đơn giản hơn.

## How to **group multiple shapes word** documents programmatically

Mẫu được trình bày ở trên—tạo container nhóm, cấu hình mỗi hình con, và thêm vào—hoạt động cho bất kỳ số lượng hình nào: vòng tròn, ảnh, hộp văn bản, v.v. Chỉ cần lặp lại các bước “tạo hình → đặt thuộc tính → thêm” trước khi gọi `doc.save()`.

Nếu bạn cần **add line to group** sau khi nhóm đã chứa các hình khác, bạn có thể lấy nhóm hiện có bằng:

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Điều này cho thấy bạn có thể sửa đổi một nhóm ở bất kỳ thời điểm nào trong vòng đời tài liệu.

## Conclusion

Bây giờ bạn đã biết cách **create grouped shapes** trong tài liệu Word bằng Java và Aspose.Words. Bằng cách **inserting group shape**, **adding line to group**, và **group multiple shapes word**, bạn có thể xây dựng các bản vẽ phức tạp hoạt động như một đối tượng duy nhất—lý tưởng cho sơ đồ, mẫu, và tạo báo cáo tự động.

Tiếp theo, khám phá các chủ đề liên quan:

- **Applying styles to grouped shapes** – học cách đặt màu nền, viền và hiệu ứng cho tất cả các child cùng một lúc.  
- **Exporting grouped shapes to PDF** – xem cách nhóm vẫn được giữ lại khi bạn chuyển đổi tài liệu.  
- **Animating shapes with VBA** – kết hợp các nhóm được tạo bằng Java với macro Word để tạo tài liệu tương tác.

Hãy thoải mái thử nghiệm với các loại hình dạng, kích thước và vị trí khác nhau. Nhóm các đối tượng mang lại sự linh hoạt để xử lý nhiều đối tượng như một, giúp đơn giản hoá cả mã nguồn và tương tác người dùng. Chúc bạn lập trình vui vẻ!


## What Should You Learn Next?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ với các giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}