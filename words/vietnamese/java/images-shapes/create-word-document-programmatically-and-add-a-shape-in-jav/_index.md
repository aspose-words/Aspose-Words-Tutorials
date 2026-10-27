---
category: general
date: 2026-10-26
description: Học cách tạo tài liệu Word bằng lập trình, thêm hình dạng và ẩn đối tượng
  trong Word bằng Aspose.Words cho Java – hướng dẫn chi tiết từng bước.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: vi
lastmod: 2026-10-26
og_description: Tạo tài liệu Word bằng lập trình, học cách thêm hình dạng và ẩn đối
  tượng trong Word với Aspose.Words cho Java. Ví dụ đầy đủ, có thể chạy được.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Tạo tài liệu Word bằng lập trình – thêm và ẩn các hình dạng trong Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Tạo tài liệu Word bằng lập trình và thêm hình dạng trong Java
url: /vi/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình và thêm hình dạng trong Java

Nếu bạn cần **tạo tài liệu Word bằng chương trình**, hướng dẫn này sẽ chỉ cho bạn cách thực hiện, thêm một hình dạng, và sau đó ẩn đối tượng trong Word. Dù bạn đang xây dựng một trình tạo báo cáo hay một hệ thống hợp đồng tự động, bạn sẽ có một giải pháp hoàn chỉnh, sẵn sàng chạy chỉ trong vài phút.

Bạn sẽ học cách:

* Khởi tạo tài liệu Word với Aspose.Words for Java.  
* Chèn một hình ellipse (hoặc bất kỳ hình nào khác) bằng kỹ thuật **how to add shape**.  
* Ẩn hình đó để nó không bao giờ xuất hiện khi mở file, trả lời câu hỏi **how to hide shape**.  

Không cần công cụ bên ngoài nào ngoài thư viện Aspose.Words, và mã hoạt động với Java 17 trở lên.

## Các điều kiện tiên quyết

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Java Development Kit (JDK) 17 hoặc mới hơn đã được cài đặt.  
* Maven hoặc Gradle để quản lý phụ thuộc (ví dụ sử dụng Maven).  
* Giấy phép Aspose.Words for Java hợp lệ (bản đánh giá miễn phí đủ cho việc thử nghiệm).  

Nếu bạn mới với Aspose.Words, hãy tham khảo hướng dẫn Getting Started chính thức, nhưng bạn không cần đọc nó để làm theo tutorial này.

## Phụ thuộc Maven

Thêm phụ thuộc sau vào `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Mẹo chuyên nghiệp:** Giữ phiên bản luôn cập nhật; các bản phát hành mới hơn chứa các bản sửa lỗi cho việc xử lý hình dạng.

## Bước 1: Tạo tài liệu Word bằng chương trình – khởi tạo tài liệu

Điều đầu tiên bạn làm khi **tạo tài liệu Word bằng chương trình** là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ file .docx trong bộ nhớ.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Tại sao bước này quan trọng*: Lớp `Document` là điểm vào cho mọi thao tác xử lý Word. Nếu không có nó, bạn không thể thêm trang, đoạn văn hay hình dạng.

## Bước 2: How to add shape – chèn một ellipse

Bây giờ chúng ta giải quyết phần **how to add shape** của tutorial. Aspose.Words hỗ trợ nhiều loại hình dạng (Ellipse, Rectangle, TextBox, v.v.). Dưới đây chúng ta chèn một ellipse có chiều rộng và chiều cao là 50 điểm.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

Phương thức `insertShape` trả về một đối tượng `Shape` mà bạn có thể tùy chỉnh thêm — màu, kiểu đường viền, xoay, và hơn thế nữa. Các tọa độ được đo bằng điểm (1/72 inch).

*Tại sao bạn có thể muốn thêm một hình dạng*: Hình dạng hữu ích cho watermark, yếu tố trang trí, hoặc placeholder mà bạn sẽ ẩn hoặc thay thế sau này.

## Bước 3: How to hide shape – làm cho đối tượng không hiển thị trong Word

Để trả lời câu hỏi **how to hide shape**, chỉ cần đặt thuộc tính `Hidden` của hình dạng thành `true`. Điều này báo cho Word xử lý hình dạng như một đối tượng ẩn, vì vậy nó sẽ không bao giờ được hiển thị trong chế độ xem tài liệu hay khi in.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Nếu bạn cần **ẩn đối tượng trong Word** cho một người dùng hoặc điều kiện cụ thể, bạn có thể chuyển đổi thuộc tính này tại thời gian chạy dựa trên logic nghiệp vụ của mình.

> **Lưu ý:** Các hình dạng ẩn vẫn là một phần của cấu trúc XML tài liệu. Chúng có thể được hiển thị lại sau bằng cách gọi `setHidden(false)`.

## Bước 4: Lưu tài liệu

Sau khi thêm và ẩn hình dạng, ghi tài liệu ra đĩa.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Khi bạn mở `HiddenShapeDemo.docx` trong Microsoft Word, sẽ thấy một trang trống vì ellipse đã bị ẩn. Tài liệu vẫn hoạt động như bất kỳ file Word bình thường nào.

## Ví dụ hoàn chỉnh hoạt động

Kết hợp tất cả các phần lại, đây là chương trình đầy đủ, có thể chạy được:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Kết quả mong đợi**

```
Document created successfully.
```

Mở `HiddenShapeDemo.docx` sẽ hiển thị một trang rỗng; ellipse ẩn không được vẽ, xác nhận rằng thao tác **hide object in Word** đã thành công.

## Các trường hợp đặc biệt và biến thể

| Tình huống | Cần thay đổi gì | Lý do |
|-----------|----------------|------|
| Ẩn một hình chữ nhật thay vì ellipse | Sử dụng `ShapeType.RECTANGLE` trong `insertShape` | Placeholder trực quan khác |
| Ẩn nhiều hình dạng cùng lúc | Duyệt `doc.getChildNodes(NodeType.SHAPE, true)` và đặt `setHidden(true)` | Hữu ích cho xử lý hàng loạt |
| Hiển thị hình dạng chỉ trong chế độ in | Đặt `shape.setVisible(false)` và `shape.setPrint(true)` | Word phân biệt giữa hiển thị trên màn hình và khi in |
| Sử dụng đơn vị đo khác | Gọi `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Phù hợp với yêu cầu bố cục của bạn |

## Những lỗi thường gặp

* **Quên gọi `setHidden(true)`** – hình dạng sẽ xuất hiện bình thường.  
* **Lưu tài liệu trước khi ẩn hình dạng** – thứ tự quan trọng; ẩn trước, sau đó lưu.  
* **Sử dụng phiên bản Aspose.Words cũ** – các bản phát hành cũ có thể thiếu API `setHidden`.  

Luôn kiểm tra file tạo ra trên phiên bản Microsoft Word mục tiêu để đảm bảo trạng thái ẩn hoạt động như mong đợi.

## Kết luận

Trong hướng dẫn này, bạn đã học cách **tạo tài liệu Word bằng chương trình**, **thêm hình dạng**, và **ẩn đối tượng trong Word** bằng Aspose.Words for Java. Ví dụ hoàn chỉnh minh họa các bước chính xác, từ khởi tạo tài liệu đến lưu file mà hình dạng không bao giờ xuất hiện.  

Từ đây, bạn có thể:

* Thử nghiệm các loại hình dạng khác (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Kết hợp các hình dạng ẩn với bookmark để tạo mẫu động.  
* Khám phá các thuộc tính `setVisible` và `setPrint` để kiểm soát chi tiết hơn việc hiển thị đối tượng.

Chúc bạn lập trình vui vẻ và tận hưởng việc tự động hoá tài liệu Word!

## Bạn Nên Học Gì Tiếp Theo?


Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create blank word document with Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}