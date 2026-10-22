---
category: general
date: 2026-09-21
description: Tạo tài liệu Word bằng cách lập trình sử dụng Java. Tìm hiểu cách nhóm
  các hình dạng trong Word, chèn một hình chữ nhật, đặt kích thước hình dạng và thêm
  các hình dạng vào tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: vi
lastmod: 2026-09-21
og_description: 'Tạo tài liệu Word bằng lập trình Java: hướng dẫn này chỉ cách nhóm
  các hình dạng trong Word, chèn hình chữ nhật, đặt kích thước hình dạng và thêm các
  hình dạng vào tài liệu Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Tạo tài liệu Word bằng lập trình, nhóm các hình dạng trong Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Tạo tài liệu Word bằng lập trình, nhóm các hình dạng trong Java
url: /vi/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình, nhóm các hình dạng trong Java

Nếu bạn cần **tạo tài liệu Word bằng chương trình**, hướng dẫn này sẽ đưa bạn qua một giải pháp hoàn chỉnh. Bạn sẽ thấy cách **nhóm các hình dạng trong Word**, chèn một hình chữ nhật, đặt kích thước của nó, và thêm các hình dạng khác—tất cả đều sử dụng Java và thư viện Aspose.Words for Java.

Bài học bao gồm mọi bước từ thiết lập dự án đến lưu file .docx cuối cùng. Khi hoàn thành, bạn sẽ có thể tạo một tài liệu Word chứa một hình chữ nhật và một hình ảnh được gói trong một nhóm duy nhất, giúp việc di chuyển hoặc thay đổi kích thước chúng cùng nhau trở nên dễ dàng. Không yêu cầu kinh nghiệm trước với Aspose.Words API, nhưng bạn nên có môi trường phát triển Java cơ bản.

## Các yêu cầu trước

* Java Development Kit (JDK) 8 hoặc mới hơn  
* Maven hoặc Gradle để quản lý phụ thuộc  
* Aspose.Words for Java 23.9 (hoặc phiên bản mới nhất) – thư viện miễn phí dùng để đánh giá  
* Một file ảnh (ví dụ, `sample.jpg`) được đặt trong một thư mục đã biết  

Có sẵn các mục này sẽ đảm bảo mã chạy mà không cần cấu hình bổ sung.

## Bước 1: Thiết lập dự án và nhập Aspose.Words

Tạo một dự án Maven (hoặc thêm phụ thuộc vào `pom.xml` hiện có của bạn):

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Nếu bạn thích Gradle, thêm đoạn sau vào `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Sau khi phụ thuộc được giải quyết, nhập các lớp cần thiết trong file nguồn Java của bạn:

```java
import com.aspose.words.*;
import java.io.File;
```

## Bước 2: Tạo tài liệu Word bằng chương trình

Hoạt động đầu tiên trong bất kỳ kịch bản tự động nào là khởi tạo một đối tượng `Document` và một `DocumentBuilder`. Builder giúp đơn giản hoá việc chèn văn bản, ảnh và các hình dạng.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Tại thời điểm này tài liệu chỉ tồn tại trong bộ nhớ. Bạn có thể bắt đầu thêm các hình dạng ngay bây giờ.

## Bước 3: Chèn một hình chữ nhật – cách chèn hình chữ nhật

Một hình chữ nhật là một `Shape` cơ bản với `ShapeType.RECTANGLE`. Bạn kiểm soát kích thước của nó bằng `setWidth`, `setHeight`, và định vị bằng `setTop` và `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Tại sao điều này quan trọng:** Đặt kích thước và vị trí một cách rõ ràng (`set shape size word`) đảm bảo hình chữ nhật xuất hiện đúng nơi bạn mong muốn, bất kể bố cục mặc định của tài liệu.

## Bước 4: Chèn một ảnh – thêm hình dạng vào tài liệu Word

`DocumentBuilder` có thể chèn ảnh trực tiếp từ đường dẫn file. Sau khi chèn, bạn có thể định vị lại hình ảnh giống như bất kỳ hình dạng nào khác.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Cả hình chữ nhật và ảnh bây giờ đều là các hình dạng độc lập trong tài liệu.

## Bước 5: Nhóm các hình dạng – cách nhóm các hình dạng trong Word

Nhóm các hình dạng hữu ích khi bạn muốn di chuyển hoặc thay đổi kích thước chúng như một đơn vị duy nhất. Aspose.Words cung cấp một container `GroupShape` cho mục đích này.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Khi nhóm được lưu, Word sẽ coi hai phần tử con như một đối tượng logic duy nhất. Bạn có thể sau này chọn nhóm và kéo nó, và cả hình chữ nhật lẫn ảnh sẽ di chuyển cùng nhau.

## Bước 6: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Đường dẫn phải có quyền ghi cho quá trình Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Chạy phương thức `main` sẽ tạo ra một file có tên **GroupShapeExample.docx**. Mở nó trong Microsoft Word để thấy một hình chữ nhật và một ảnh được khóa cùng nhau trong một nhóm. Khi chọn nhóm, bạn có thể di chuyển cả hai đối tượng đồng thời, xác nhận việc nhóm đã thành công.

## Kết quả mong đợi

* Một file Word (`GroupShapeExample.docx`) nằm trong thư mục bạn chỉ định.  
* Trong file, một hình chữ nhật (đổ màu xám nhạt) xuất hiện ở góc trên‑trái, và ảnh nằm ngay bên dưới nó.  
* Cả hai đối tượng đều là một phần của một nhóm duy nhất, vì vậy kéo một đối tượng sẽ kéo đối tượng còn lại.

## Các biến thể thường gặp và trường hợp đặc biệt

| Tình huống | Khuyến nghị |
|-----------|-------------|
| **Định dạng ảnh khác nhau** | Aspose.Words hỗ trợ PNG, BMP, GIF và TIFF. Sử dụng phần mở rộng file phù hợp trong `insertImage`. |
| **Kích thước âm** | API sẽ ném `ArgumentException`. Luôn kiểm tra chiều rộng và chiều cao trước khi gọi `setWidth` / `setHeight`. |
| **Tài liệu lớn** | Nhóm nhiều hình dạng có thể làm tăng kích thước file. Xem xét gộp các hình dạng thành một ảnh duy nhất khi hiệu năng quan trọng. |
| **Tương thích phiên bản Word** | GroupShape hoạt động với Word 2007 (`.docx`) và các phiên bản sau. Đối với các file `.doc` cũ hơn, nhóm sẽ bị làm phẳng. |
| **Định vị động** | Sử dụng các phép tính dựa trên kích thước trang (`doc.getFirstSection().getPageSetup().getPageWidth()`) nếu bạn cần vị trí thích ứng. |

**Mẹo chuyên nghiệp:** Sau khi tạo nhóm, bạn có thể thay đổi

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong bài viết này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}