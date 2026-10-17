---
category: general
date: 2026-01-11
description: Tạo tài liệu Word bằng Java nhanh chóng bằng cách thêm một hình chữ nhật,
  đặt màu nền và áp dụng bóng cho hình. Học từng bước.
draft: false
keywords:
- create word document java
- add rectangle shape
- apply shadow to shape
- set shape fill color
- how to add shape
language: vi
og_description: Tạo tài liệu Word bằng Java bằng cách chèn một hình chữ nhật, đặt
  màu nền và áp dụng bóng. Hướng dẫn đầy đủ kèm mã.
og_title: Tạo tài liệu Word bằng Java – Thêm hình chữ nhật có bóng
tags:
- Aspose.Words
- Java
- Document Generation
title: Tạo tài liệu Word bằng Java – Thêm hình chữ nhật có hiệu ứng đổ bóng
url: /vi/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng Java – Thêm hình chữ nhật với hiệu ứng bóng

Bạn đã bao giờ cần **tạo word document java** và muốn nó trông chuyên nghiệp hơn chưa? Có thể bạn đang xây dựng một công cụ tạo báo cáo và một trang trống không đủ. Tin tốt là gì? Với Aspose.Words for Java, bạn có thể chèn một hình chữ nhật vào tài liệu, tô màu cho nó, và thậm chí thêm một bóng nhẹ – tất cả chỉ trong vài dòng mã.

Trong tutorial này chúng ta sẽ đi qua từng bước: cách thêm hình chữ nhật, đặt màu nền, và áp dụng bóng cho hình để tệp Word của bạn trông chuyên nghiệp hơn. Khi hoàn thành, bạn sẽ có một ví dụ có thể chạy được để sao chép‑dán vào dự án của mình.

## Những gì bạn cần

- **Java 17** (hoặc bất kỳ JDK nào mới) – mã sử dụng các tính năng chuẩn của ngôn ngữ.  
- **Thư viện Aspose.Words for Java** – phiên bản 23.9 hoặc mới hơn được khuyến nghị.  
- Một IDE hoặc trình soạn thảo văn bản mà bạn thích – IntelliJ IDEA, Eclipse, VS Code… tùy bạn.  
- Một thư mục để lưu file `ShadowShape.docx` được tạo.

Không cần cấu hình phức tạp nào; chỉ cần thêm JAR Aspose.Words vào classpath và bạn đã sẵn sàng.

## Bước 1: Thiết lập dự án và nhập Aspose.Words

Đầu tiên, tạo một dự án Maven (hoặc Gradle) mới và thêm phụ thuộc Aspose.Words. Dưới đây là đoạn `pom.xml` tối thiểu cho Maven:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>23.9</version>
        <classifier>jdk17</classifier>
    </dependency>
</dependencies>
```

Nếu bạn không dùng Maven, chỉ cần đặt file JAR vào thư mục `libs` và thêm vào đường dẫn biên dịch.

> **Pro tip:** Aspose cung cấp giấy phép dùng thử miễn phí mà bạn có thể nhúng bằng `License license = new License(); license.setLicense("Aspose.Words.lic");`. Bỏ qua nó cho các thử nghiệm nhanh; thư viện vẫn hoạt động ở chế độ đánh giá.

## Bước 2: Tạo tài liệu mới và Builder

Bây giờ chúng ta sẽ thực sự **create word document java** các đối tượng. Lớp `Document` đại diện cho toàn bộ file .docx, trong khi `DocumentBuilder` cho phép chúng ta chèn nội dung.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Tại thời điểm này bạn đã có một tài liệu trống sẵn sàng nhận các hình, đoạn văn hoặc bất kỳ nội dung nào bạn cần.

## Bước 3: Chèn hình chữ nhật và đặt màu nền

Thêm một hình rất đơn giản, chỉ cần gọi `insertShape`. Chúng ta sẽ sử dụng kỹ thuật **add rectangle shape**, thuộc từ khóa phụ *add rectangle shape*.

```java
        // Insert a rectangle shape – 200pt wide, 100pt tall
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);

        // Set the fill color to a bright orange
        rectangle.setFillColor(java.awt.Color.ORANGE);
```

Tại sao lại chọn màu cam? Nó nổi bật trên nền trắng, nhưng bạn có thể thay bằng bất kỳ `java.awt.Color` nào bạn muốn. Bước này bao gồm từ khóa phụ *set shape fill color*.

## Bước 4: Cấu hình hiển thị bóng – Áp dụng bóng cho hình

Phần thú vị nhất đã đến: thêm một bóng nhẹ cho hình chữ nhật. API Aspose cung cấp đối tượng `ShadowFormat` để điều khiển mọi khía cạnh của bóng.

```java
        // Get the shadow format object for the shape
        ShadowFormat shadow = rectangle.getShadowFormat();

        // Make the shadow visible
        shadow.setVisible(true);

        // Choose a neutral gray for the shadow color
        shadow.setColor(java.awt.Color.GRAY);

        // Blur radius – larger values produce a softer edge
        shadow.setBlur(5.0);

        // Offset determines how far the shadow is displaced
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);

        // Transparency (0 = opaque, 1 = fully transparent)
        shadow.setTransparency(0.2);

        // Define the shadow style and type
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);

        // Scale controls the overall size of the shadow relative to the shape
        shadow.setScale(1.0);
```

Khối mã này **apply shadow to shape** chính xác như từ khóa phụ gợi ý. Bạn có thể điều chỉnh `blur`, `offsetX/Y`, và `transparency` để phù hợp với phong cách thiết kế. Ví dụ, `offsetX` lớn hơn tạo bóng mạnh hơn, trong khi `transparency` cao hơn làm bóng nhẹ nhàng hơn.

## Bước 5: Lưu tài liệu

Cuối cùng, chúng ta ghi tài liệu ra đĩa. Chọn một thư mục bạn có quyền ghi và đặt tên file rõ ràng.

```java
        // Save the result – adjust the path as needed
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Khi mở `ShadowShape.docx` trong Microsoft Word hoặc LibreOffice, bạn sẽ thấy một hình chữ nhật màu cam sáng với bóng xám mềm mại nằm ngay phía dưới.

![create word document java with rectangle shape](/images/shadow-rectangle.png "create word document java – rectangle with shadow")

*Văn bản alt của hình ảnh bao gồm từ khóa chính, đáp ứng quy tắc SEO.*

## Câu hỏi thường gặp & Các trường hợp đặc biệt

### Nếu tôi cần một hình dạng khác thì sao?

Aspose.Words hỗ trợ hàng chục giá trị `ShapeType` – sao, mũi tên, chú thích, bất kỳ gì bạn muốn. Chỉ cần thay `ShapeType.RECTANGLE` bằng `ShapeType.OVAL` hoặc bất kỳ hằng số enum nào khác. Các bước **how to add shape** vẫn áp dụng.

### Làm sao để thêm hình vào một đoạn văn cụ thể?

Thay vì chèn hình trực tiếp bằng builder, bạn có thể tạo hình trước (`new Shape(document, ShapeType.RECTANGLE)`) rồi thêm vào `Paragraph` bằng `paragraph.appendChild(shape)`. Cách này cho phép kiểm soát bố cục chi tiết hơn.

### Tôi có thể áp dụng màu nền gradient thay vì màu đồng nhất không?

Có! Dùng `rectangle.getFill().setFillType(FillType.GRADIENT)` và định nghĩa một `LinearGradientFill`. API hơi dài hơn một chút, nhưng rất hữu ích cho các thiết kế hiện đại.

### Còn khả năng tương thích với các phiên bản Word cũ thì sao?

Aspose.Words mặc định lưu ở định dạng .docx, được hỗ trợ bởi Word 2007+ và LibreOffice. Nếu bạn cần .doc, gọi `document.save("file.doc", SaveFormat.DOC)`. Việc hiển thị bóng có thể hơi khác nhau, nhưng hình vẫn giữ nguyên.

## Ví dụ hoàn chỉnh (Sẵn sàng sao chép‑dán)

Dưới đây là toàn bộ chương trình, sẵn sàng biên dịch và chạy. Thay `YOUR_DIRECTORY` bằng đường dẫn thực tế trên máy của bạn.

```java
import com.aspose.words.*;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape and set its fill color
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 200, 100);
        rectangle.setFillColor(java.awt.Color.ORANGE);

        // Step 3: Apply shadow to shape
        ShadowFormat shadow = rectangle.getShadowFormat();
        shadow.setVisible(true);
        shadow.setColor(java.awt.Color.GRAY);
        shadow.setBlur(5.0);
        shadow.setOffsetX(4.0);
        shadow.setOffsetY(4.0);
        shadow.setTransparency(0.2);
        shadow.setStyle(ShadowStyle.OUTER);
        shadow.setType(ShadowType.PARALLEL);
        shadow.setScale(1.0);

        // Step 4: Save the document
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Chạy đoạn mã này sẽ tạo một file Word chứa hình chữ nhật màu cam với bóng xám mềm mại — chính xác những gì chúng ta muốn đạt được khi **create word document java** với một hình dạng được định dạng.

## Kết luận

Bạn giờ đã có một công thức toàn diện, từ đầu đến cuối, để **create word document java** mà *adds rectangle shape*, *sets shape fill color*, và *applies shadow to shape*. Cách tiếp cận đơn giản, API mượt mà, và bạn có thể mở rộng vô số cách — thay đổi hình dạng, màu gradient, hoặc thậm chí thêm nhiều bóng cho mỗi hình.

Tiếp theo bạn có thể thử xếp chồng nhiều hình, thử `ShadowStyle.ETCHED` để có cảm giác trực quan khác, hoặc kết hợp với tạo bảng để xây dựng các báo cáo đầy đủ. Các khả năng chỉ bị giới hạn bởi trí tưởng tượng của bạn (và có thể là mức giấy phép Aspose).

Nếu bạn gặp bất kỳ vấn đề nào hoặc có ý tưởng cải tiến, hãy để lại bình luận bên dưới. Chúc bạn lập trình vui vẻ và làm cho các tài liệu Word trở nên sinh động hơn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}