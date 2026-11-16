---
category: general
date: 2026-11-15
description: Tạo hình chữ nhật trong Word bằng Java và học cách thêm hình vào Word,
  đặt kích thước hình và lưu tài liệu Word một cách hiệu quả.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: vi
lastmod: 2026-11-15
og_description: Tạo hình chữ nhật trong tài liệu Word bằng Java. Học cách thêm hình
  vào Word, đặt kích thước hình và lưu tài liệu Word trong vài phút.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Tạo hình chữ nhật trong Word bằng Java – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Tạo hình chữ nhật trong tài liệu Word bằng Java
url: /vi/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong tài liệu Word bằng Java

Nếu bạn cần **tạo hình chữ nhật** bên trong một tệp Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng Java. Bạn sẽ thấy cách **thêm hình vào Word**, kiểm soát **đặt kích thước hình**, và cuối cùng **lưu tài liệu Word** mà không rời khỏi IDE.

Trong các phần sau, bạn sẽ nhận được một ví dụ hoàn chỉnh, có thể chạy được, giải thích từng dòng code, và các mẹo tránh những lỗi thường gặp như vấn đề kích thước và tính tương thích của tài liệu. Không cần tham chiếu bên ngoài—chỉ cần thư viện Aspose.Words for Java.

## Những gì bạn sẽ học

* Cách khởi tạo một `Document` và một `DocumentBuilder`.
* Cách chèn một **group shape** và đặt hình chữ nhật bên trong nó.
* Cách **định nghĩa kích thước hình** bằng `setWidth` và `setHeight`.
* Cách **lưu tài liệu Word** ở định dạng `.docx`.
* Xử lý các trường hợp đặc biệt cho các kích thước trang và cài đặt DPI khác nhau.

### Yêu cầu trước

* Java 17 hoặc mới hơn (code cũng biên dịch được với Java 8).
* Aspose.Words for Java 23.10 hoặc mới hơn – bạn có thể tải từ Maven Central.
* Kiến thức cơ bản về cú pháp Java và các khái niệm hướng đối tượng.

> **Pro tip:** Nếu bạn dự định thêm nhiều hình dạng sau này (ví dụ: vòng tròn hoặc hộp văn bản), hãy giữ chúng trong cùng một `GroupShape`. Điều này giúp việc di chuyển, xoay hoặc định dạng toàn bộ bộ sưu tập trở nên dễ dàng hơn rất nhiều.

## Bước 1: Khởi tạo tài liệu và builder

Bước đầu tiên là tạo một tệp Word trống và một `DocumentBuilder` cho phép bạn ghi nội dung.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Lý do quan trọng:* `Document` đại diện cho toàn bộ tệp, trong khi `DocumentBuilder` cung cấp các phương thức cấp cao để chèn văn bản, bảng và **hình**. Nếu không có builder, bạn sẽ phải thao tác trực tiếp với các node cấp thấp.

## Bước 2: Chèn một group shape để chứa nhiều hình

Một **group shape** hoạt động như một container; bạn có thể thêm nhiều hình và sau này xử lý chúng như một đối tượng duy nhất (ví dụ: di chuyển hoặc xoay cùng nhau).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Tại sao nên dùng group shape?* Nếu sau này bạn muốn thêm mũi tên, vòng tròn, hoặc nhãn quanh hình chữ nhật, group sẽ giữ mọi thứ luôn căn chỉnh. Nó cũng đơn giản hoá quy trình **add shapes to Word** vì bạn chỉ cần một lời gọi `appendChild` cho mỗi hình mới.

## Bước 3: Tạo hình chữ nhật

Bây giờ chúng ta tạo hình chữ nhật thực tế sẽ nằm trong group. Hàm khởi tạo `Shape` cần `Document` sở hữu và loại hình bạn muốn.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Tại sao lại là hình chữ nhật?* `ShapeType.RECTANGLE` là primitive phổ biến nhất để làm nổi bật các phần, tạo placeholder, hoặc vẽ các mô hình UI đơn giản ngay trong Word.

## Bước 4: Định nghĩa kích thước của hình chữ nhật

Đặt kích thước là nơi **set shape dimensions** trở nên quan trọng. Bạn có thể sử dụng bất kỳ đơn vị đo nào mà Aspose.Words hỗ trợ; mặc định là điểm (1 pt = 1/72 inch).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Lưu ý:** Nếu bạn muốn dùng milimet, gọi `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` trong đó `1.39 in ≈ 35 mm`. Điều này minh họa tính linh hoạt của **define shape size**.

## Bước 5: Thêm hình chữ nhật vào group shape

Việc gắn hình chữ nhật vào group đã tạo trước sẽ làm nó xuất hiện trong tài liệu.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

Ở thời điểm này, hình chữ nhật được đặt ở góc trên‑trái của group. Bạn có thể di chuyển sau này bằng `rectangle.setLeft(...)` và `rectangle.setTop(...)` nếu cần vị trí chính xác.

## Bước 6: (Tùy chọn) Lưu tài liệu để xem kết quả

Cuối cùng, ghi tài liệu ra đĩa. Đây là bước **save Word document** tạo ra một tệp `.docx` mà bạn có thể mở bằng Microsoft Word, LibreOffice, hoặc Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Chạy chương trình sẽ tạo ra `RectangleShapeDemo.docx` chứa một hình chữ nhật duy nhất bên trong một group shape. Mở tệp sẽ thấy một hình chữ nhật trắng đơn giản—có kích thước chính xác như bạn đã định nghĩa.

### Kết quả mong đợi

* Một tệp Word có tên `RectangleShapeDemo.docx`.
* Trong đoạn văn đầu tiên, một group shape chứa hình chữ nhật 100 pt × 50 pt.
* Không có văn bản nào được thêm, vì vậy hình chữ nhật xuất hiện trên một trang trống.

## Các biến thể thường gặp và trường hợp đặc biệt

| Tình huống | Cách điều chỉnh code |
|-----------|-----------------------|
| **Kích thước trang khác** (ví dụ: A4) | Gọi `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` trước khi chèn hình. |
| **DPI cao hơn cho in** | Nhân chiều rộng/chiều cao với hệ số DPI mong muốn, ví dụ `rectangle.setWidth(200 * 2);` cho độ phân giải gấp đôi. |
| **Thêm nhãn văn bản bên trong hình chữ nhật** | Tạo một `Shape` loại `TEXT_BOX`, đặt `setWidth`/`setHeight` khớp với hình chữ nhật, rồi thêm vào cùng `GroupShape`. |
| **Xoay hình chữ nhật** | Dùng `rectangle.setRotationAngle(45);` để xoay 45 độ theo chiều kim đồng hồ. |
| **Lưu dưới dạng PDF thay vì DOCX** | Thay `document.save("output.docx");` bằng `document.save("output.pdf");` – API giống nhau, vẫn giữ được hình chữ nhật. |

## Những mẹo chuyên nghiệp để triển khai vững chắc

1. **Tái sử dụng builder** – sau khi chèn group shape, bạn có thể tiếp tục thêm đoạn văn hoặc bảng mà không cần tạo một instance builder mới.
2. **Giải phóng tài nguyên** – mặc dù garbage collector của Java xử lý hầu hết các đối tượng, việc gọi `document.close();` một cách rõ ràng (nếu dùng stream) giúp tránh rò rỉ handle file.
3. **Kiểm tra kích thước** – trước khi gọi `setWidth`/`setHeight`, đảm bảo giá trị là dương; giá trị âm sẽ ném `IllegalArgumentException`.
4. **Tương thích phiên bản** – code hoạt động với Aspose.Words 23.x trở lên. Các phiên bản cũ hơn có thể yêu cầu `Shape.setSize(width, height)` thay vì các setter riêng.

## Ví dụ đầy đủ, có thể chạy được

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Xác minh kết quả:** Mở `output/RectangleShapeDemo.docx` trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật có kích thước đã chỉ định, nằm ở giữa phía trên của trang đầu. Nếu hình quá nhỏ, hãy điều chỉnh các giá trị truyền vào `setWidth` và `setHeight`.

## Kết luận

Bây giờ bạn đã biết cách **tạo hình chữ nhật** trong tệp Word bằng Java, cách **thêm hình vào Word** thông qua `GroupShape`, cách **đặt kích thước hình** và **định nghĩa kích thước hình**, và cuối cùng cách **lưu tài liệu Word** để chia sẻ. Mẫu này cũng áp dụng cho các loại hình khác, cho phép bạn xây dựng các sơ đồ phức tạp một cách lập trình.

### Tiếp theo bạn nên làm gì?

* Khám phá **add shapes to Word** bằng cách chèn vòng tròn, mũi tên, hoặc hộp văn bản.
* Kết hợp nhiều hình vào một `GroupShape` duy nhất và áp dụng các biến đổi (xoay, lật).
* Tạo báo cáo nhúng biểu đồ dưới dạng hình, sau đó **save Word document** dưới dạng PDF để chia sẻ.

Hãy tự do thử nghiệm với kích thước, màu sắc và vị trí để phù hợp với kịch bản của bạn. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã nguồn hoàn chỉnh và các giải thích chi tiết từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}