---
category: general
date: 2026-09-11
description: Nhóm các hình dạng trong Word và thêm một hình chữ nhật bằng Aspose.Words
  cho Java. Tìm hiểu cách đặt kích thước hình dạng, nhóm các đối tượng và lưu tài
  liệu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: vi
lastmod: 2026-09-11
og_description: Nhóm các hình dạng trong Word và thêm một hình chữ nhật bằng cách
  sử dụng Aspose.Words cho Java. Hướng dẫn này cho thấy cách đặt kích thước hình dạng,
  nhóm các hình dạng và xuất tài liệu.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Nhóm các hình dạng trong Word – thêm hình chữ nhật với Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Nhóm các hình dạng trong Word và thêm một hình chữ nhật bằng Aspose.Words
url: /vi/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nhóm các hình dạng trong Word và thêm hình chữ nhật với Aspose.Words

Nếu bạn cần **group shapes in Word** trong khi lập trình thêm một hình chữ nhật, hướng dẫn này cung cấp cho bạn một giải pháp hoàn chỉnh, sẵn sàng chạy. Bạn sẽ thấy chính xác cách chèn một group shape, thêm một rectangle shape, đặt kích thước hình dạng, và cuối cùng lưu tài liệu để có thể xem kết quả ngay lập tức.

Làm việc với tài liệu Word thường đồng nghĩa với việc sắp xếp nhiều đối tượng—hình ảnh, biểu đồ, hoặc các hình dạng hình học đơn giản—into a single logical unit. Nhóm các đối tượng này giúp việc di chuyển, xoay hoặc định dạng chúng cùng nhau trở nên dễ dàng hơn. Trong tutorial này, chúng ta cũng sẽ đề cập đến **how to add rectangle** shapes và **set shape size** để kiểm soát bố cục một cách hoàn hảo.

## Những gì bạn sẽ học

* Cách tạo một tài liệu Word mới bằng Aspose.Words for Java.  
* **How to group shapes** để chúng hoạt động như một đối tượng duy nhất.  
* **Add rectangle shape** vào một nhóm và chèn một hình ảnh vào cùng nhóm.  
* **Set shape size** cho cả hình chữ nhật và hình ảnh.  
* Lưu tài liệu và mở nó trong Microsoft Word để xác minh kết quả.

### Yêu cầu trước

* Java 17 hoặc phiên bản mới hơn đã được cài đặt.  
* Maven hoặc Gradle để quản lý các phụ thuộc.  
* Giấy phép Aspose.Words for Java hợp lệ (hoặc khóa đánh giá miễn phí).  
* Một tệp hình ảnh (`sample.png`) được đặt trong một thư mục đã biết (thay `YOUR_DIRECTORY` bằng đường dẫn thực tế của bạn).

---

## Cách nhóm các hình dạng trong Word bằng Aspose.Words

Bước đầu tiên là tạo một `Document` và một `DocumentBuilder`. Builder cung cấp cho bạn một API tiện lợi để chèn các hình dạng, văn bản và các yếu tố khác.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Why this matters:** `DocumentBuilder` làm việc trực tiếp với đối tượng `Document` nền tảng, cho phép bạn chèn các hình dạng mà không cần xử lý thủ công các bộ sưu tập node cấp thấp.

### Thêm một group shape

Một group shape là một container có thể chứa các shape khác. Hãy nghĩ nó như một thư mục cho các đối tượng vẽ.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Phương thức `insertGroupShape()` tạo một node `GroupShape` và trả về nó để bạn có thể thêm các shape con sau này.  

---

## Thêm một rectangle shape vào nhóm

Bây giờ chúng ta sẽ **add rectangle shape** vào nhóm đã tạo trước đó. Hình chữ nhật sẽ đóng vai trò là nền hoặc viền cho hình ảnh.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tip:** Đặt `FillColor` và `StrokeColor` làm cho rectangle hiển thị trong tài liệu cuối cùng. Nếu bạn bỏ qua các thuộc tính này, shape có thể xuất hiện trong suốt.

### Cách thêm rectangle

Mã trên minh họa **how to add rectangle** bằng cách tạo một instance `Shape` với `ShapeType.RECTANGLE` và sau đó thêm nó vào `GroupShape`. Mẫu này hoạt động cho bất kỳ loại shape nào khác (ví dụ: `ELLIPSE`, `POLYLINE`).  

---

## Đặt kích thước shape cho rectangle và hình ảnh

Việc đặt kích thước phù hợp đảm bảo rằng rectangle và hình ảnh căn chỉnh chính xác. Ở đây chúng ta cũng **set shape size** cho hình ảnh sẽ chèn tiếp theo.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Cả rectangle và picture bây giờ có cùng kích thước (100 × 50 points). Vì chúng thuộc cùng một nhóm, việc di chuyển hoặc xoay nhóm sẽ ảnh hưởng đến cả hai shape cùng nhau.

> **Why match sizes?** Căn chỉnh các kích thước đảm bảo rằng hình ảnh nằm gọn trong rectangle, tạo ra hiệu ứng “hình ảnh trong khung” sạch sẽ.

---

## Lưu tài liệu và xem kết quả

Cuối cùng, chúng ta ghi tài liệu ra đĩa. Mở tệp trong Microsoft Word sẽ hiển thị các shape đã nhóm như một đối tượng có thể chọn duy nhất.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Khi bạn mở `output.docx`, bạn sẽ thấy một rectangle với hình ảnh bên trong. Nhấp vào shape sẽ chọn cả rectangle và picture vì chúng đã **grouped**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Image alt text:* *group shapes in word example* – một tài liệu Word hiển thị một rectangle và hình ảnh đã được **grouped**.

---

## Các câu hỏi thường gặp và xử lý trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Nếu tôi cần kích thước khác cho hình ảnh thì sao?** | Điều chỉnh `picture.setWidth()` và `picture.setHeight()` sau khi chèn. Rectangle có thể giữ kích thước gốc, hoặc bạn cũng có thể thay đổi kích thước để khớp. |
| **Tôi có thể thêm nhiều shape vào cùng một nhóm không?** | Có. Gọi `group.appendChild(newShape)` cho bất kỳ đối tượng `Shape` bổ sung nào. |
| **Làm thế nào để xoay toàn bộ nhóm?** | Sử dụng `group.setRotationAngle(double angleInRadians)`. Việc xoay sẽ áp dụng cho mọi shape con. |
| **Nếu tệp hình ảnh bị thiếu thì sao?** | `insertImage` ném ra `FileNotFoundException`. Bao gói lời gọi trong khối try‑catch và cung cấp một shape placeholder dự phòng. |
| **Có thể tách nhóm sau này không?** | Gọi `group.removeAllChildren()` để tách các phần tử con, sau đó chèn chúng lại vào tài liệu từng cái một. |

---

## Kết luận

Bây giờ bạn có một ví dụ hoàn chỉnh, có thể chạy được, cho thấy **how to group shapes in Word**, **add rectangle shape**, **set shape size**, và **save** tài liệu bằng Aspose.Words for Java. Bằng cách nhóm rectangle và picture, bạn có thể di chuyển, thay đổi kích thước hoặc xoay chúng như một đơn vị duy nhất—đúng như những gì nhiều kịch bản tự động hoá tài liệu yêu cầu.

Từ đây bạn có thể khám phá:

* Thêm các hộp văn bản vào cùng một nhóm (`how to add rectangle`‑style text).  
* Áp dụng các mẫu fill hoặc gradient khác nhau (`set shape size` kết hợp với styling).  
* Sử dụng kỹ thuật tương tự để nhóm biểu đồ, bảng hoặc SmartArt (`how to group shapes` trên các loại đối tượng khác).  

Hãy tự do thử nghiệm với các loại shape khác, màu sắc và tùy chọn bố cục. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với hướng dẫn từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word Java – Thêm hình chữ nhật với hiệu ứng bóng](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cách tạo trường biểu mẫu và thêm nội dung bằng DocumentBuilder trong Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cách chuyển Word sang PDF bằng Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}