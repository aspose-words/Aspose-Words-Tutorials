---
category: general
date: 2026-08-01
description: Nhóm các hình dạng trong Word bằng Java sử dụng Aspose.Words. Tìm hiểu
  cách nhóm các hình dạng và chèn hình chữ nhật nhanh chóng với ví dụ mã đầy đủ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: vi
lastmod: 2026-08-01
og_description: Nhóm các hình dạng trong Word bằng Java. Hướng dẫn này chỉ cách nhóm
  các hình dạng, chèn hình chữ nhật và lưu tệp DOCX bằng Aspose.Words.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Nhóm các hình dạng trong Word bằng Java – Hướng dẫn lập trình chi tiết
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Nhóm các hình dạng trong Word bằng Java – Hướng dẫn chi tiết từng bước
url: /vi/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nhóm các hình dạng trong Word bằng Java – Hướng dẫn chi tiết từng bước

Nếu bạn cần **nhóm các hình dạng trong Word** bằng Java, hướng dẫn này sẽ giúp bạn. Cho dù bạn đang xây dựng một công cụ tạo báo cáo hay một engine mẫu động, việc nhóm các hình dạng giúp tài liệu của bạn trông chuyên nghiệp và giữ các đồ họa liên quan cùng nhau.

Trong vài phút tới, bạn sẽ thấy chính xác **cách nhóm các hình dạng** và **chèn hình chữ nhật** bằng Aspose.Words, cùng một vài mẹo thực tế giúp bạn tránh các lỗi thường gặp. Sẵn sàng biến những hình chữ nhật và hình bầu dục rải rác thành một nhóm gọn gàng? Hãy bắt đầu.

## Nội dung hướng dẫn này

* Các yêu cầu tối thiểu (Java 17+, Aspose.Words 24.10 hoặc mới hơn).  
* Một chương trình Java hoàn chỉnh, có thể chạy được, tạo tài liệu Word, chèn một hình chữ nhật và một hình bầu dục, nhóm chúng, ẩn nhóm nếu muốn, và lưu file.  
* Lý do mỗi lời gọi API quan trọng, không chỉ là chức năng của chúng.  
* Xử lý các trường hợp biên cho các phiên bản Aspose.Words cũ hơn và việc nhóm hơn hai hình dạng.  
* Kết quả mong đợi và cách nhanh chóng để xác minh kết quả.

Khi kết thúc, bạn sẽ có thể chèn đoạn mã này vào bất kỳ dự án Java nào và bắt đầu nhóm các hình dạng trong Word mà không cần tìm kiếm qua các tài liệu rải rác.

---

## Yêu cầu trước

| Requirement | Why it matters |
|-------------|----------------|
| **Java 17+** | Các tính năng ngôn ngữ hiện đại và hiệu năng tốt hơn. |
| **Aspose.Words for Java 24.10+** | `setHidden` method được sử dụng sau này chỉ tồn tại từ phiên bản này trở lên. |
| **A Maven or Gradle build** | Giúp quản lý phụ thuộc trở nên dễ dàng. |
| **An IDE (IntelliJ, Eclipse, VS Code)** | Hữu ích cho việc kiểm thử nhanh, nhưng bất kỳ trình soạn thảo văn bản nào cũng được. |

Thêm phụ thuộc Aspose.Words Maven vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Nếu bạn thích Gradle, tương đương là:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Bước 1: Tạo tài liệu mới và Builder

Đầu tiên chúng ta tạo một `Document` trống và một `DocumentBuilder`. Builder là công cụ chính cho phép chúng ta chèn hình dạng, văn bản và nhiều hơn nữa.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Tại sao lại thực hiện bước này?*  
`Document` đại diện cho toàn bộ tệp DOCX, trong khi `DocumentBuilder` cung cấp một API dựa trên con trỏ tiện lợi. Nếu không có builder, bạn sẽ phải thao tác thủ công với các bộ sưu tập node cấp thấp—điều này dễ gây lỗi.

---

## Bước 2: Chèn hình chữ nhật (và một hình bầu dục)

Bây giờ chúng ta thêm hai hình dạng cơ bản mà muốn nhóm. Lưu ý lời gọi **insert rectangle shape** — đây chính là từ khóa phụ mà bạn đang tìm.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Một vài điều cần lưu ý:

* Chiều rộng (`100`) và chiều cao (`50`) được đo bằng điểm (1 pt ≈ 1/72 in). Điều chỉnh chúng cho phù hợp với bố cục của bạn.  
* Hình chữ nhật được vẽ trước, vì vậy nó nằm phía sau hình bầu dục theo mặc định. Nếu bạn cần thứ tự ngược lại, hãy chèn hình bầu dục trước.  
* Cả hai hình đều kế thừa định dạng hiện tại của builder (màu, kiểu đường). Bạn có thể tùy chỉnh chúng trước khi nhóm nếu muốn.

---

## Bước 3: Cách nhóm các hình dạng với Aspose.Words

Đây là phần cốt lõi của hướng dẫn—**cách nhóm các hình dạng**. API `insertGroupShape` nhận một mảng các hình đã tồn tại và trả về một `Shape` mới đại diện cho nhóm.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Tại sao lại dùng nhóm?  

* Một nhóm di chuyển như một đơn vị duy nhất, giữ nguyên vị trí tương đối.  
* Bạn có thể áp dụng các biến đổi (xoay, thu phóng) cho toàn bộ tập hợp bằng một lời gọi.  
* Nhóm giúp việc chỉnh sửa sau này đơn giản hơn—có thể tách nhóm nếu cần chỉnh sửa từng phần tử.

---

## Bước 4 (Tùy chọn): Ẩn nhóm khỏi chế độ xem tài liệu

Nếu bạn không muốn nhóm hiển thị khi người dùng mở tài liệu trong Word, bạn có thể ẩn nó. Bước này là tùy chọn nhưng hữu ích cho đồ họa nền hoặc watermark.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**Nếu bạn đang dùng phiên bản Aspose.Words cũ hơn?**  
Phương thức `setHidden` sẽ không biên dịch được. Trong trường hợp đó, bạn có thể đạt được hiệu quả tương tự bằng cách đặt `WrapType` của shape thành `NONE` và di chuyển nó phía sau lớp văn bản:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

Cách này hơi dài hơn, nhưng vẫn giữ nhóm ra khỏi tầm nhìn của người đọc.

---

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Thay đổi đường dẫn tới vị trí bạn muốn lưu file.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

Khi bạn mở `GroupShapeResult.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật và một hình bầu dục được nhóm gọn gàng. Nếu bạn đặt `setHidden(true)`, nhóm sẽ không hiển thị trong trình soạn thảo nhưng vẫn tồn tại trong file (hữu ích cho việc xử lý chương trình sau này).

---

## Ví dụ hoàn chỉnh hoạt động

Kết hợp tất cả lại, đây là lớp Java hoàn chỉnh, tự chứa mà bạn có thể sao chép‑dán vào dự án của mình:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Kết quả mong đợi:** Một file có tên `GroupShapeResult.docx` chứa một nhóm duy nhất giữ một hình chữ nhật màu xanh và một hình bầu dục viền đỏ (màu mặc định). Nếu bạn mở tài liệu, chọn nhóm, và nhấp chuột phải → **Group → Ungroup**, bạn sẽ thấy hai hình dạng gốc xuất hiện lại.

---

## Câu hỏi thường gặp & Trường hợp đặc biệt

### 1. Tôi có thể nhóm hơn hai hình dạng không?

Chắc chắn. Chỉ cần truyền một mảng lớn hơn vào `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

API mở rộng tuyến tính; giới hạn duy nhất là bộ nhớ cho các nhóm cực lớn.

### 2. Nếu tôi cần thay đổi vị trí của nhóm sau khi tạo thì sao?

Sử dụng các phương thức `setLeft` và `setTop` của nhóm, giống như bất kỳ shape nào khác:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Vì nhóm hoạt động như một shape duy nhất, tất cả các shape con sẽ di chuyển cùng nhau.

### 3. Làm sao để áp dụng viền hoặc màu nền cho toàn bộ nhóm?

Nhóm tự nó có thể có định dạng, nhưng không ảnh hưởng trực tiếp tới các shape con. Nếu bạn muốn một viền chung, hãy bao bọc các shape trong một hình chữ nhật trước, sau đó nhóm tất cả. Hoặc, lặp qua từng shape con và đặt cùng một `fillColor` hoặc `strokeWeight`.

### 4. `setHidden(true)` có ảnh hưởng tới việc in không?

Các shape ẩn **không** được in mặc định trong Word, điều này có thể hữu ích cho watermark hoặc dấu hiệu mẫu. Nếu bạn cần shape được in nhưng vẫn ẩn trên màn hình, bạn sẽ phải dùng cách khác (ví dụ, đặt độ trong suốt thành 0%).

---

## Mẹo chuyên nghiệp từ thực tiễn

* **Đặt tên cho các shape** – `groupShape.setName("HeaderGraphics");` giúp việc gỡ lỗi dễ dàng hơn khi bạn sau này truy xuất shape theo tên.  
* **Tái sử dụng builder** – Sau khi chèn một nhóm, con trỏ của builder vẫn ở vị trí nhóm được đặt, vì vậy bạn có thể tiếp tục thêm đoạn văn ngay sau nhóm mà không cần đặt lại vị trí.  
* **Bảo vệ phiên bản** – Nếu bạn phát hành một thư viện có thể chạy trên các phiên bản Aspose.Words cũ hơn, hãy bao bọc lời gọi `setHidden` trong khối try‑catch cho `NoSuchMethodError` và quay lại cách `WrapType.NONE` đã trình bày ở trên.  
* **Mẹo hiệu năng** – Khi tạo hàng ngàn

---

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có ví dụ mã hoàn chỉnh, kèm giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rendering Shapes in Aspose.Words for Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}