---
category: general
date: 2026-07-29
description: Tạo tài liệu Word trong Java bằng Aspose.Words. Học cách chèn hình chữ
  nhật, nhóm các hình trong Word và lưu tài liệu dưới dạng docx nhanh chóng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
- add shapes to word
language: vi
lastmod: 2026-07-29
og_description: Tạo tài liệu Word trong Java bằng Aspose.Words. Chèn hình chữ nhật,
  nhóm các hình trong Word và lưu tài liệu dưới dạng docx trong vài phút.
og_image_alt: Screenshot showing how to create word document with grouped shapes using
  Java
og_title: Tạo tài liệu Word với các hình dạng – Hướng dẫn Java Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  headline: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Create word document in Java using Aspose.Words. Learn to insert rectangle
    shape, group shapes in Word, and save document as docx quickly.
  name: Create Word Document with Shapes in Java – Complete Aspose.Words Guide
  steps:
  - name: '## Create Word Document with Shapes Using Aspose.Words'
    text: The first thing you need is an empty Word file to work with. Aspose.Words
      makes this a one‑liner.
  - name: '## Insert Rectangle Shape and Other Shapes'
    text: Now we’ll add a blue rectangle and a green ellipse. The rectangle demonstrates
      the **insert rectangle shape** keyword, while the ellipse shows that you can
      mix shape types freely.
  - name: '## Group Shapes in Word for Easy Manipulation'
    text: Having two separate objects is fine, but often you want to move them together.
      That’s where **group shapes in word** shines.
  - name: '## Save Document as DOCX and Verify Output'
    text: Finally, we persist the file. This step fulfills the **save document as
      docx** requirement.
  - name: '## Full Working Example and Common Pitfalls'
    text: Below is the complete, ready‑to‑run Java class. Copy‑paste it into your
      project, adjust the output folder, and hit *Run*.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Tạo tài liệu Word với các hình dạng trong Java – Hướng dẫn đầy đủ Aspose.Words
url: /vi/java/images-shapes/create-word-document-with-shapes-in-java-complete-aspose-wor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word với các hình dạng trong Java – Hướng dẫn đầy đủ Aspose.Words

Bạn đã bao giờ tự hỏi làm thế nào để **create word document** một cách lập trình và thêm vào các đồ họa tùy chỉnh? Bạn không phải là người duy nhất. Dù bạn cần tạo báo cáo với các phần được làm nổi bật hay thiết kế một tờ rơi nhanh chóng, việc nắm vững cách xử lý hình dạng trong Word có thể tiết kiệm cho bạn hàng giờ công việc thủ công.

Trong hướng dẫn này, chúng ta sẽ đi qua các bước chính xác để **create word document** bằng Aspose.Words cho Java, **insert rectangle shape**, **group shapes in Word**, và cuối cùng **save document as docx**. Khi kết thúc, bạn sẽ có một ví dụ có thể chạy được hoàn toàn mà bạn có thể đưa vào bất kỳ dự án nào.

## Những gì bạn sẽ nhận được

- Một tệp Word mới được tạo hoàn toàn từ mã Java.  
- Hai hình dạng riêng biệt (một hình chữ nhật và một hình bầu dục) được thêm vào trang.  
- Các hình dạng đó được gộp lại với API **group shapes in word**, khiến chúng hoạt động như một đối tượng duy nhất.  
- Tệp được lưu trên đĩa dưới dạng `.docx` tiêu chuẩn, mở trong Microsoft Word mà không gặp vấn đề.  

Không có công cụ bên ngoài, không có các thủ thuật XML rắc rối—chỉ cần Java gõ kiểu sạch sẽ và Aspose.Words.

---

## Yêu cầu trước

Trước khi chúng ta bắt đầu, hãy chắc chắn rằng bạn có:

1. **Java Development Kit (JDK) 8 hoặc mới hơn** – mã nhắm tới Java 8+.  
2. **Aspose.Words for Java** JAR (bạn có thể tải phiên bản mới nhất từ Maven Central repository).  
3. Một IDE vừa phải (IntelliJ IDEA, Eclipse, hoặc thậm chí một trình soạn thảo văn bản đơn giản).  

Nếu bạn đã có những thứ này, tuyệt vời—hãy bắt đầu.

---

## Triển khai từng bước

Dưới đây chúng tôi chia quy trình thành các bước nhỏ. Mỗi bước bao gồm một đoạn mã, một giải thích ngắn, và một mẹo mà bạn có thể không tìm thấy trong tài liệu chính thức.

### ## Tạo tài liệu Word với các hình dạng bằng Aspose.Words

Điều đầu tiên bạn cần là một tệp Word trống để làm việc. Aspose.Words làm cho việc này chỉ cần một dòng lệnh.

```java
// Step 1: Initialise a blank document and a DocumentBuilder
Document doc = new Document();                 // Represents the Word file
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:**  
`Document` là container cho mọi thứ—văn bản, bảng, hình ảnh và hình dạng. `DocumentBuilder` là trợ lý thân thiện cho phép bạn thêm nội dung mà không phải đấu tranh với các đối tượng cấp thấp. Hãy nghĩ nó như một cây bút viết trực tiếp lên trang.

> **Mẹo chuyên nghiệp:** Nếu bạn dự định bắt đầu với một mẫu (ví dụ, tiêu đề công ty), thay thế `new Document()` bằng `new Document("template.docx")`.

### ## Chèn hình chữ nhật và các hình dạng khác

Bây giờ chúng ta sẽ thêm một hình chữ nhật màu xanh và một hình bầu dục màu xanh lá. Hình chữ nhật minh họa từ khóa **insert rectangle shape**, trong khi hình bầu dục cho thấy bạn có thể tự do kết hợp các loại hình dạng.

```java
// Step 2: Insert a rectangle shape (100x50 points) and set its appearance
Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
rect.setLeft(50);                               // X‑coordinate in points
rect.setTop(50);                                // Y‑coordinate in points
rect.getFill().setColor(java.awt.Color.BLUE);  // Fill color

// Step 3: Insert an ellipse shape (80x80 points) and configure it
Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
ellipse.setLeft(180);
ellipse.setTop(30);
ellipse.getFill().setColor(java.awt.Color.GREEN);
```

**Điều gì đang diễn ra bên trong?**  
Mỗi lần gọi `insertShape` tạo một đối tượng `Shape` và tự động thêm nó vào đoạn hiện tại. Các phương thức `setLeft`/`setTop` định vị hình dạng tương đối với lề trang, đo bằng điểm (1 pt = 1/72 in). Bằng cách điều chỉnh các số này, bạn có thể đặt hình dạng ở bất kỳ vị trí nào bạn muốn.

> **Câu hỏi thường gặp:** *Tôi có thể thêm một hình ảnh thay vì màu nền không?*  
> Chắc chắn—chỉ cần thay thế màu nền bằng một hình ảnh bằng cách sử dụng `shape.getFill().setImage("path/to/image.png")`.

### ## Nhóm các hình dạng trong Word để dễ thao tác

Có hai đối tượng riêng biệt là ổn, nhưng thường bạn muốn di chuyển chúng cùng nhau. Đó là nơi **group shapes in word** tỏa sáng.

```java
// Step 4: Create a GroupShape container and add the two shapes
GroupShape group = builder.insertGroupShape(); // Starts an empty group
group.appendChild(rect);
group.appendChild(ellipse);

// Step 5: Reposition the whole group as a single entity
group.setLeft(100);
group.setTop(150);
```

**Tại sao lại nhóm?**  
Khi các hình dạng được nhóm, bất kỳ biến đổi nào—di chuyển, xoay, thay đổi kích thước—sẽ áp dụng cho toàn bộ bộ sưu tập. Điều này phản ánh hành vi bạn nhận được khi thủ công chọn nhiều hình dạng trong giao diện Word và nhấn *Group*. Nó cũng đơn giản hoá mã sau này vì bạn chỉ cần điều chỉnh một đối tượng thay vì nhiều.

> **Trường hợp đặc biệt:** Nếu sau này bạn cần tách nhóm, gọi `group.getParentNode().removeChild(group)` và chèn lại các phần tử con riêng lẻ.

### ## Lưu tài liệu dưới dạng DOCX và kiểm tra kết quả

Cuối cùng, chúng ta lưu tệp. Bước này đáp ứng yêu cầu **save document as docx**.

```java
// Step 6: Write the document to disk as a .docx file
String outputPath = "output/GroupShapeExample.docx";
doc.save(outputPath, SaveFormat.DOCX);
System.out.println("Document saved successfully to " + outputPath);
```

**Bạn sẽ thấy gì:**  
Mở tệp `GroupShapeExample.docx` được tạo trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật màu xanh và một hình bầu dục màu xanh lá, được nhóm gọn gàng. Kéo nhóm này—cả hai hình dạng di chuyển cùng nhau, giống như bạn mong đợi từ giao diện người dùng.

> **Mẹo:** Sử dụng `SaveFormat.PDF` nếu bạn cần phiên bản PDF; cùng một đoạn mã sẽ hoạt động mà không cần thay đổi.

### ## Ví dụ đầy đủ và các lỗi thường gặp

Dưới đây là lớp Java hoàn chỉnh, sẵn sàng chạy. Sao chép và dán nó vào dự án của bạn, điều chỉnh thư mục đầu ra, và nhấn *Run*.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle shape and set its position and fill color
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rect.setLeft(50);
        rect.setTop(50);
        rect.getFill().setColor(java.awt.Color.BLUE);

        // Step 3: Insert a second ellipse shape and configure its position and fill color
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 80, 80);
        ellipse.setLeft(180);
        ellipse.setTop(30);
        ellipse.getFill().setColor(java.awt.Color.GREEN);

        // Step 4: Group the two shapes together using the new GroupShape API
        GroupShape group = builder.insertGroupShape();
        group.appendChild(rect);
        group.appendChild(ellipse);

        // Step 5: Optionally reposition the entire group as a single object
        group.setLeft(100);
        group.setTop(150);

        // Step 6: Save the document containing the grouped shapes
        String outPath = "output/GroupShapeExample.docx";
        doc.save(outPath, SaveFormat.DOCX);
        System.out.println("Document saved successfully to " + outPath);
    }
}
```

#### Các lỗi thường gặp & Cách tránh chúng

| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| **`NullPointerException` trên `builder`** | Quên khởi tạo `DocumentBuilder` sau khi tạo `Document`. | Đảm bảo `new DocumentBuilder(doc)` được thực thi trước khi chèn bất kỳ hình dạng nào. |
| **Hình dạng xuất hiện ngoài trang** | Sử dụng giá trị pixel thay vì điểm, hoặc không tính đến lề. | Nhớ rằng Aspose.Words yêu cầu đơn vị là điểm; 72 pt = 1 in. Điều chỉnh `setLeft`/`setTop` cho phù hợp. |
| **Nhóm biến mất sau khi lưu** | Thêm hình dạng vào nhóm *sau* khi nhóm đã được lưu. | Luôn nhóm trước khi gọi `doc.save()`. |
| **Không tìm thấy tệp khi lưu** | Thư mục đầu ra không tồn tại. | Tạo thư mục bằng chương trình (`new File("output").mkdirs();`) hoặc sử dụng một đường dẫn đã tồn tại. |

---

## Kết luận

Chúng ta vừa **create word document** từ đầu, **add shapes to word**, **insert rectangle shape**, **group shapes in word**, và cuối cùng **save document as docx**—tất cả chỉ với một vài dòng Java. Sức mạnh của Aspose.Words nằm ở mô hình đối tượng rõ ràng; bạn có thể xem tệp Word như một canvas, vẽ lên nó bằng các hình dạng, và sau đó xuất ra bất cứ nơi nào bạn cần.

Cảm thấy phiêu lưu? Hãy thử thay hình chữ nhật bằng một ngôi sao, thêm văn bản bên trong các hình dạng bằng `Shape.getTextBox()`, hoặc thử nghiệm với việc xoay (`shape.setRotationAngle(45)`). API rất phong phú, và các khả năng gần như vô hạn.

Có câu hỏi về các kịch bản nâng cao—như liên kết hình dạng với bookmark hoặc xuất ra PDF với phông chữ nhúng? Để lại bình luận bên dưới, và chúng tôi sẽ cùng nhau khám phá sâu hơn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao phủ các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tạo nhóm hình dạng trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo hình chữ nhật trong Word với Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}