---
category: general
date: 2026-11-22
description: Tìm hiểu cách thêm hình dạng vào Word bằng Aspose.Words cho Java – chèn
  một hình chữ nhật và ẩn nó bằng cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: vi
lastmod: 2026-11-22
og_description: Thêm hình dạng vào Word bằng Aspose.Words cho Java. Hướng dẫn này
  cho thấy cách chèn một hình chữ nhật, ẩn hình dạng và lưu tài liệu.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Thêm hình dạng vào Word với Aspose.Words – Hướng dẫn Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Cách thêm hình dạng vào tài liệu Word bằng Aspose.Words cho Java
url: /vi/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm hình dạng vào tài liệu Word bằng Aspose.Words cho Java

Nếu bạn cần **thêm hình dạng vào tài liệu Word** một cách lập trình, Aspose.Words cho Java giúp thực hiện việc này một cách đơn giản. Trong hướng dẫn này, bạn sẽ học **cách chèn hình dạng**, kiểm soát khả năng hiển thị của nó, và **cách ẩn hình dạng** sao cho tệp cuối cùng trông đúng như mong muốn.

Bạn sẽ đi qua một ví dụ hoàn chỉnh, có thể chạy được, tải một tệp `.docx` hiện có, chèn một hình chữ nhật, ẩn nó, và lưu kết quả. Không cần script bên ngoài hay các bước thủ công, và tutorial bao gồm các biến thể phổ biến như tạo tài liệu mới từ đầu hoặc ẩn hình dạng chỉ khi in.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* Java 17 (hoặc mới hơn) đã được cài đặt – các phiên bản cũ hơn vẫn hoạt động nhưng LTS mới nhất mang lại hiệu năng tốt hơn.  
* Maven 3.8+ để quản lý phụ thuộc.  
* Giấy phép Aspose.Words cho Java hợp lệ (bản dùng thử miễn phí đủ cho việc học).  
* Một IDE hoặc trình soạn thảo văn bản mà bạn thích (ví dụ: IntelliJ IDEA, VS Code).

## Bước 1: Thêm Aspose.Words vào dự án Maven của bạn

Thêm phụ thuộc sau vào file `pom.xml`. Điều này sẽ kéo phiên bản ổn định mới nhất (tính đến tháng 11 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Mẹo:** Sử dụng thẻ `<scope>provided</scope>` nếu bạn dự định đóng gói JAR cùng với logic cấp phép của riêng mình.

## Thêm hình dạng vào Word – khởi tạo tài liệu

Bước chức năng đầu tiên là lấy một đối tượng `Document`. Bạn có thể tải một tệp hiện có hoặc tạo một tệp mới.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Tại sao điều này quan trọng*: Lớp `Document` là điểm vào cho mọi thao tác với Word. Tải một tệp hiện có giữ nguyên các kiểu, header và footer, trong khi tài liệu mới cho bạn một “bảng trắng”.

## Cách chèn hình dạng vào tài liệu Word

Tiếp theo, tạo một `DocumentBuilder` để chỉnh sửa nội dung tài liệu. Builder cung cấp các phương thức để chèn văn bản, bảng và **hình dạng**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

Lệnh `insertShape` trả về một đối tượng `Shape` mà bạn có thể cấu hình thêm (màu, viền, văn bản, v.v.). Kích thước được biểu thị bằng điểm (1 pt = 1/72 in).

*Tại sao bạn có thể muốn dùng hình chữ nhật*: Hình chữ nhật là container phổ biến cho chú thích, watermark hoặc placeholder. Bạn có thể thay `ShapeType.RECTANGLE` bằng `ShapeType.ELLIPSE`, `ShapeType.LINE`, v.v., để đáp ứng nhu cầu hình ảnh khác nhau.

## Cách ẩn hình dạng trong Word

Đôi khi bạn cần một hình dạng tồn tại để tính toán bố cục nhưng không muốn nó xuất hiện trong bản render cuối cùng. Aspose.Words cung cấp phương thức `setHidden(true)` để thực hiện điều này.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Cờ ẩn hoạt động giống như tùy chọn **Hidden** trong Microsoft Word: hình dạng bị loại bỏ khỏi bố cục hiển thị nhưng vẫn tham gia vào mô hình đối tượng của tài liệu. Điều này hữu ích cho:

* Lưu trữ siêu dữ liệu hoặc marker mà ứng dụng của bạn sẽ đọc sau này.  
* Tạo placeholder và loại bỏ chúng ngay trước khi xuất bản.  
* Kiểm soát khả năng hiển thị cho các định dạng đầu ra khác nhau (ví dụ: ẩn trong HTML nhưng giữ lại trong PDF).

> **Lưu ý:** Hình dạng ẩn vẫn được xuất ra PDF theo mặc định. Nếu bạn muốn chúng cũng bị loại bỏ khi tạo PDF, hãy đặt `rectangle.getWrapType() = WrapType.NONE` và điều chỉnh thuộc tính `Hidden` cho phù hợp.

## Bước 4: Lưu tài liệu đã chỉnh sửa

Cuối cùng, ghi các thay đổi vào một tệp mới.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Khi bạn mở `output.docx` trong Microsoft Word, hình chữ nhật sẽ không hiển thị, nhưng nó vẫn là một phần của cây tài liệu. Bạn có thể xác nhận sự tồn tại của nó bằng cách tải lại tệp và kiểm tra `Shape.isHidden()`.

### Kết quả mong đợi

* Tệp `output.docx` mở ra mà không có bất kỳ hình dạng nào hiển thị.  
* Nếu bạn kiểm tra tài liệu bằng Aspose.Words (ví dụ: `doc.getChildNodes(NodeType.SHAPE, true).size()`), số lượng hình dạng sẽ là **1**, xác nhận rằng hình dạng tồn tại nhưng đã bị ẩn.

## Các biến thể nâng cao và trường hợp góc cạnh

### 1. Tạo hình dạng trong tài liệu mới

Nếu bạn bắt đầu từ đầu, thay dòng tải bằng:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Định vị hình dạng một cách chính xác

Mặc định, `insertShape` đặt hình dạng tại vị trí con trỏ hiện tại. Để định vị tuyệt đối:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Kiểm soát khả năng hiển thị theo định dạng đầu ra

Nếu bạn muốn hình dạng hiển thị trong giao diện Word nhưng ẩn khi xuất ra PDF, hãy dùng `Shape.setWrapType(WrapType.NONE)` cùng với `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Thêm văn bản vào bên trong hình dạng

Một hình chữ nhật có thể chứa một khung văn bản:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Bạn có thể ẩn khung văn bản này bằng cùng một lời gọi `setHidden(true)`.

## Những lỗi thường gặp và cách tránh

| Triệu chứng | Nguyên nhân | Cách khắc phục |
|------------|-------------|----------------|
| Hình dạng vẫn xuất hiện dù đã gọi `setHidden(true)` | Tài liệu đã được lưu trước khi đặt cờ ẩn. | Đảm bảo gọi `setHidden(true)` **trước** khi thực hiện `doc.save()`. |
| Kích thước hình dạng bị biến dạng | Nhầm lẫn giữa điểm và pixel trên màn hình DPI cao. | Sử dụng điểm (72 pt = 1 in) để có kích thước nhất quán trên mọi nền tảng. |
| Hình dạng ẩn vẫn in ra | Một số máy in bỏ qua cờ ẩn. | Đặt `Shape.setWrapType(WrapType.NONE)` và đồng thời xóa `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Kết luận

Bây giờ bạn đã biết cách **thêm hình dạng vào tài liệu Word** bằng Aspose.Words cho Java, **cách chèn hình dạng**, và **cách ẩn hình dạng** sao cho nó không hiển thị với người dùng cuối nhưng vẫn là một phần của cấu trúc tài liệu. Ví dụ hoàn chỉnh ở trên tải một tệp, chèn một hình chữ nhật, ẩn nó, và lưu lại, bao quát cả các trường hợp sử dụng điển hình và một số trường hợp góc cạnh.

Từ đây, bạn có thể khám phá các chủ đề liên quan như **cách chèn hình dạng** với màu nền tùy chỉnh, **cách ẩn hình dạng trong Word** cho việc in có điều kiện, hoặc tự động xử lý hàng loạt tài liệu bằng Aspose.Words. Thử nghiệm với các giá trị `ShapeType` khác nhau, các tùy chọn định vị, và các cờ hiển thị để phù hợp với quy trình làm việc của bạn.

Chúc bạn lập trình vui vẻ và tận hưởng sự linh hoạt mà việc thao tác Word bằng lập trình mang lại cho các ứng dụng Java của mình!

## Bạn Nên Học Gì Tiếp Theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã nguồn hoàn chỉnh cùng các giải thích chi tiết từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}