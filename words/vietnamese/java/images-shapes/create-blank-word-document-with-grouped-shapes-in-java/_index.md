---
category: general
date: 2026-08-07
description: Tạo tài liệu Word trống với các hình dạng được nhóm trong Java bằng Aspose.Words.
  Tìm hiểu cách nhóm hình dạng, thiết lập kích thước hình dạng và thêm các hình dạng
  vào Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: vi
lastmod: 2026-08-07
og_description: Tạo tài liệu Word trống với các hình dạng được nhóm trong Java. Hãy
  làm theo hướng dẫn này để đặt kích thước hình dạng, thêm hình dạng vào Word và thành
  thạo cách nhóm hình dạng.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Tạo tài liệu Word trống với các hình dạng được nhóm – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Tạo tài liệu Word trống với các hình dạng được nhóm trong Java
url: /vi/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống với các hình dạng được nhóm trong Java

Nếu bạn cần **tạo tài liệu Word trống** chứa một số hình dạng được sắp xếp như một đơn vị duy nhất, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được, minh họa **cách nhóm hình dạng** các đối tượng, điều chỉnh kích thước của chúng, và **thêm hình dạng vào Word** bằng Aspose.Words for Java.

Hướng dẫn sẽ đi qua từng bước—từ thiết lập dự án đến lưu tệp .docx cuối cùng—để bạn có thể sao chép mã trực tiếp vào ứng dụng của mình. Không cần tham chiếu bên ngoài, và giải pháp hoạt động với Aspose.Words 23.9 hoặc mới hơn.

## Yêu cầu trước

* Java 17 (hoặc bất kỳ JDK nào được hỗ trợ)
* Maven hoặc Gradle để quản lý phụ thuộc
* Giấy phép Aspose.Words for Java (hoặc khóa đánh giá tạm thời)
* Tệp ảnh mẫu (ví dụ, `sample.jpg`) được đặt trong một thư mục đã biết

Nếu bất kỳ mục nào trong số này còn thiếu, hãy cài đặt chúng trước; phần còn lại của hướng dẫn giả định môi trường đã sẵn sàng.

## Bước 1: Thêm Aspose.Words vào dự án của bạn

Thêm phụ thuộc Aspose.Words vào `pom.xml` (Maven) hoặc `build.gradle` (Gradle). Thư viện này cung cấp các lớp `Document`, `DocumentBuilder`, `GroupShape` và `Shape` được sử dụng sau này.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Tại sao điều này quan trọng:** Nếu không có thư viện, không có API xử lý Word nào khả dụng, và bạn không thể **tạo tài liệu Word trống** một cách lập trình.

## Bước 2: Tạo tài liệu Word trống

Hành động cụ thể đầu tiên là khởi tạo một đối tượng `Document`, đại diện cho một **tài liệu Word trống** trong bộ nhớ.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* tạo một **tài liệu Word trống** với các cài đặt mặc định (trang A4, lề mặc định). `DocumentBuilder` đi kèm cho phép bạn chèn nội dung tại vị trí con trỏ hiện tại.

## Bước 3: Chèn một group shape (cách nhóm hình dạng)

Một *group shape* hoạt động như một container cho các hình dạng khác. Trong bước này bạn sẽ học **cách nhóm hình dạng** sao cho chúng di chuyển cùng nhau.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Phương thức `insertGroupShape` đặt container tại vị trí con trỏ của builder. Việc nhóm là cần thiết khi bạn muốn xử lý nhiều bản vẽ như một thực thể duy nhất—đây là cốt lõi của chức năng **group shapes word**.

## Bước 4: Tạo hình chữ nhật và đặt kích thước

Bây giờ thêm một hình chữ nhật vào nhóm. Điều này minh họa **đặt kích thước hình dạng**, cần thiết cho bố cục chính xác.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Tại sao phải đặt kích thước?* Gọi rõ ràng `setWidth` và `setHeight` đảm bảo rằng hình chữ nhật xuất hiện đúng như mong muốn, bất kể kiểu dáng hình dạng mặc định của tài liệu.

## Bước 5: Chèn hình ảnh và thêm vào nhóm

Thêm một hình ảnh cho thấy một trường hợp sử dụng phổ biến khác của **thêm hình dạng vào Word**. Hình ảnh sẽ trở thành một phần của cùng một nhóm, di chuyển cùng với hình chữ nhật.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Nếu tệp ảnh bị thiếu, Aspose.Words sẽ ném ra một ngoại lệ. Một mẹo thực tế là kiểm tra đường dẫn trước:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Bước 6: Lưu tài liệu chứa các hình dạng đã nhóm

Cuối cùng, lưu **tài liệu Word trống** (bây giờ đã có một group shape) vào đĩa.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Khi bạn mở `GroupShapeDemo.docx` trong Microsoft Word, sẽ thấy một đối tượng nhóm duy nhất chứa một hình chữ nhật và một hình ảnh. Việc chọn bất kỳ phần nào của nhóm cũng di chuyển toàn bộ container, xác nhận rằng các hình dạng đã **được nhóm** đúng cách.

### Kết quả mong đợi

* Một tệp có tên `GroupShapeDemo.docx` trong thư mục đã chỉ định.
* Khi mở tệp, sẽ hiển thị một container 300 × 200‑point với:
  * Một hình chữ nhật 100 × 50‑point được đặt tại (20, 20).
  * Một hình ảnh được đặt tại (150, 30) trong cùng container.

## Các trường hợp đặc biệt và biến thể

| Situation | How to handle it |
|-----------|-----------------|
| **Kích thước trang khác** | Gọi `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` trước khi chèn nhóm. |
| **Nhiều nhóm** | Lặp lại các bước 3‑5 với một thể hiện `GroupShape` mới; mỗi nhóm có thể được đặt vị trí độc lập. |
| **Xoay hình dạng** | Sử dụng `shape.setRotationAngle(45.0);` để xoay một hình chữ nhật hoặc hình ảnh trước khi thêm vào nhóm. |
| **Hình dạng không phải ảnh** | Tạo các đối tượng `Shape` loại `ShapeType.ELLIPSE`, `ShapeType.LINE`, v.v., và thêm chúng giống như hình chữ nhật. |
| **Hình ảnh lớn** | Thu phóng hình ảnh bằng `picture.setWidth(80.0); picture.setHeight(60.0);` để giữ nhóm trong giới hạn ban đầu. |

## Mẹo thực tế từ kinh nghiệm

* **Pro tip:** Đặt `RelativeHorizontalPosition` và `RelativeVerticalPosition` của nhóm thành `RelativeHorizontalPosition.PAGE` và `RelativeVerticalPosition.PAGE` nếu bạn muốn nhóm được neo vào trang thay vì vào con trỏ.
* **Watch out for:** Thêm một hình dạng vượt quá kích thước của nhóm; hình dạng sẽ bị cắt trong Word. Điều chỉnh kích thước nhóm bằng `group.setWidth()` và `group.setHeight()` cho phù hợp.
* **Performance note:** Nếu bạn tạo nhiều tài liệu trong một vòng lặp, hãy tái sử dụng một thể hiện `DocumentBuilder` duy nhất và gọi `doc.clone()` để giảm chi phí tạo đối tượng.

## Kết luận

Bạn hiện đã biết cách **tạo tài liệu Word trống** chứa một bộ sưu tập các hình dạng đã được nhóm bằng Aspose.Words for Java. Hướng dẫn đã bao quát quy trình đầy đủ: thiết lập thư viện, tạo tài liệu, chèn nhóm, **đặt kích thước hình dạng**, **thêm hình dạng vào Word**, và lưu kết quả.

Từ đây bạn có thể khám phá các tính năng nâng cao hơn như nhóm biểu đồ, áp dụng kiểu cho từng hình dạng riêng lẻ, hoặc xuất tài liệu ra PDF. Mỗi chủ đề này đều dựa trên các nguyên tắc đã được trình bày trong hướng dẫn này.

---

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Chèn hình dạng trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}