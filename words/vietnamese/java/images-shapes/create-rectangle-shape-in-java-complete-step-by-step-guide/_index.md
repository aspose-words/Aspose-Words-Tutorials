---
category: general
date: 2026-07-03
description: Tạo hình chữ nhật trong Java và học cách thêm bóng cho hình, áp dụng
  hiệu ứng bóng, đặt độ trong suốt cho hình, và tạo tài liệu trống nhanh chóng.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: vi
og_description: Tạo hình chữ nhật trong Java với bóng, độ trong suốt và tài liệu trống.
  Hãy theo hướng dẫn này để thành thạo việc xử lý hình dạng.
og_title: Tạo hình chữ nhật trong Java – Hướng dẫn lập trình đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Tạo hình chữ nhật trong Java – Hướng dẫn chi tiết từng bước
url: /vi/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong Java – Hướng dẫn chi tiết từng bước

Bạn đã bao giờ tự hỏi làm thế nào **tạo hình chữ nhật** trong tài liệu Word bằng Java chưa? Bạn không phải là người duy nhất—các nhà phát triển thường cần một cách nhanh chóng để thêm đồ họa hình học, sau đó tạo bóng nhẹ để bố cục trông chuyên nghiệp hơn. Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình: từ việc **tạo tài liệu trống** đến **thêm bóng vào hình**, **áp dụng hiệu ứng bóng**, và thậm chí **đặt độ trong suốt cho hình** để có vẻ ngoài chuyên nghiệp.

Đoạn mã dưới đây là một ví dụ hoàn chỉnh có thể sao chép‑dán vào dự án của bạn. Không cần tài liệu bên ngoài—chỉ cần làm theo các bước, hiểu “tại sao”, và bạn sẽ tạo ra các hình chữ nhật có bóng trong vài giây.

## Những gì bạn sẽ học

- Cách **tạo hình chữ nhật** một cách lập trình với Aspose.Words for Java.
- Các lời gọi chính xác để **thêm bóng vào hình** và cấu hình các thuộc tính hiển thị.
- Các cách **áp dụng hiệu ứng bóng** và điều chỉnh các tham số như độ dịch, bán kính mờ, và màu sắc.
- Kỹ thuật **đặt độ trong suốt cho hình** để có vẻ ngoài tinh tế hơn.
- Cách **tạo tài liệu trống**, chèn hình và lưu kết quả.

> **Mẹo chuyên nghiệp:** Tất cả các hành động này được thực hiện trên một thể hiện `Document` duy nhất, có nghĩa là bạn có thể xâu chuỗi chúng lại mà không lo về việc I/O file trung gian.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

- Java 17 (hoặc bất kỳ JDK hiện đại nào) được cài đặt.
- Thư viện Aspose.Words for Java được thêm vào dự án (coordinates Maven: `com.aspose:aspose-words:23.12`).
- Một IDE Java hoặc trình soạn thảo văn bản đơn giản—không cần gì phức tạp, chỉ cần nơi để biên dịch và chạy.

Nếu bạn thiếu bất kỳ thứ nào trong số này, hãy tải JDK từ Oracle và thêm phụ thuộc Aspose qua Maven hoặc Gradle. Khi đã xong, bạn đã sẵn sàng.

## Bước 1: **Tạo tài liệu trống** – nền cho mọi thứ

Điều đầu tiên bạn cần là một đối tượng `Document` rỗng. Hãy nghĩ nó như một tờ giấy trắng; nếu không có nó, bạn sẽ không có nơi để đặt hình chữ nhật.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Tại sao phải bắt đầu với tài liệu trống? Bởi vì mọi hình đều tồn tại trong một `Section`, và một `Document` mới tạo sẵn có một section mặc định với body sẵn sàng nhận các node. Bỏ qua bước này sẽ buộc bạn phải tự tạo các section sau này, làm tăng độ phức tạp không cần thiết.

## Bước 2: **Tạo hình chữ nhật** và xác định kích thước

Bây giờ chúng ta đã có nền, hãy **tạo hình chữ nhật**. Lớp `Shape` nhận tham chiếu tài liệu và một `ShapeType`. Ở đây chúng ta chọn `RECTANGLE` và đặt chiều rộng/chiều cao bằng điểm (1 pt ≈ 1/72 inch).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Tại sao lại đặt `WrapType.INLINE`? Việc bao bọc dạng inline khiến hình hành xử như một ký tự trong đoạn văn, đảm bảo nó di chuyển cùng văn bản xung quanh. Nếu bạn cần hành vi nổi, hãy chuyển sang `WrapType.SQUARE` hoặc `WrapType.TOP_BOTTOM`.

## Bước 3: **Áp dụng hiệu ứng bóng** – tạo độ sâu cho hình chữ nhật

Một hình chữ nhật phẳng trông… thật phẳng. Thêm bóng sẽ làm nó nổi bật. Chúng ta sẽ **áp dụng hiệu ứng bóng** bằng cách tạo một thể hiện `ShadowEffect`, sau đó tinh chỉnh các thuộc tính hiển thị.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Hãy phân tích một chút:

- **Color** – `Color.getGray(0.5)` tạo màu xám 50 %, trung tính và phù hợp với hầu hết nền.
- **OffsetX/Y** – Giá trị dương đẩy bóng sang phải và xuống; giá trị âm sẽ di chuyển sang trái/lên.
- **BlurRadius** – Giá trị lớn hơn tạo bóng mềm hơn, lan tỏa hơn.
- **Transparency** – Giá trị từ `0` (đục) tới `1` (hoàn toàn trong suốt). Ở đây chúng ta chọn `0.3` để có hiệu ứng nhẹ nhàng.

## Bước 4: **Thêm bóng vào hình** – gắn hiệu ứng

Tạo hiệu ứng chưa đủ; chúng ta phải **thêm bóng vào hình** bằng cách gán đối tượng `ShadowEffect` cho hình chữ nhật.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Ở phía sau, lời gọi này cập nhật markup OpenXML nền (`<w:shdw>`) mà Word dùng để vẽ bóng. Nếu bạn mở file `.docx` đã lưu, sẽ thấy một phần tử `<w:effect>` được điền đầy các tham số chúng ta đã thiết lập.

## Bước 5: **Đặt độ trong suốt cho hình** – tùy chọn nhưng thường hữu ích

Đôi khi bạn muốn hình chữ nhật tự nó bán trong suốt, để văn bản nền vẫn có thể nhìn thấy. Lớp `Shape` cung cấp `setFillColor` và `setFillTransparency`. Dưới đây là một ví dụ nhanh làm cho hình chữ nhật trong suốt 40 %:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Tại sao lại làm như vậy? Hãy tưởng tượng một watermark hoặc một chú thích nổi bật, nơi nội dung nền phải vẫn đọc được. Điều chỉnh giá trị trong suốt cho phù hợp với ngôn ngữ thiết kế của bạn.

## Bước 6: Chèn hình vào tài liệu

Chúng ta đã xây dựng hình chữ nhật, thêm bóng và (tùy chọn) đặt độ trong suốt. Bước cuối cùng là **thêm hình vào section đầu tiên của tài liệu**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Việc gắn hình vào body sẽ đặt nó ở cuối đoạn văn đầu tiên. Nếu bạn cần vị trí chèn cụ thể, hãy lấy `Paragraph` mục tiêu và dùng `insertBefore` hoặc `insertAfter`.

## Bước 7: Lưu tài liệu – xem kết quả

Tất cả công việc trên culminates trong một lời gọi `save` duy nhất. Chọn đường dẫn phù hợp với môi trường của bạn.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Mở file `ShadowShape.docx` kết quả trong Microsoft Word hoặc LibreOffice, và bạn sẽ thấy một hình chữ nhật sắc nét với bóng xám nhẹ, hơi trong suốt nếu bạn đã thực hiện bước tùy chọn. Các thuộc tính hiển thị khớp với những gì chúng ta đã định nghĩa bằng mã.

---

![tạo hình chữ nhật có bóng trong tài liệu Word](https://example.com/images/rectangle-shadow.png "tạo hình chữ nhật có bóng")

*Văn bản thay thế ảnh:* **tạo hình chữ nhật có bóng** – biểu diễn trực quan của kết quả cuối cùng.

## Câu hỏi thường gặp & Các trường hợp đặc biệt

### Nếu tôi muốn màu bóng khác?

Chỉ cần thay đổi lời gọi `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Nhớ rằng bóng quá sáng có thể trông không chuyên nghiệp; các tông màu nhẹ thường là lựa chọn tốt nhất.

### Tôi có thể áp dụng cùng một bóng cho nhiều hình không?

Có. Tạo một thể hiện `ShadowEffect`, cấu hình nó, rồi tái sử dụng:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Chỉ cần tránh thay đổi `ShadowEffect` sau khi đã gắn vào các hình khác, trừ khi bạn muốn cập nhật chúng đồng thời.

### Làm sao để thay đổi độ mờ của bóng một cách động?

Tạo một thanh trượt UI ánh xạ tới `setBlurRadius`. Giá trị từ `2` tới `12` là phổ biến; số lớn hơn sẽ tạo “ánh sáng” hơn là bóng sắc nét.

### Nếu tôi cần hình nổi thay vì inline thì sao?

Thay đổi kiểu bao bọc:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Các hình nổi cho bạn tự do bố trí hơn nhưng đòi hỏi logic vị trí bổ sung.

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là chương trình đầy đủ, sẵn sàng sao chép‑dán, bao gồm tất cả các bước chúng ta đã thảo luận. Chạy nó như một ứng dụng Java thông thường.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Kết quả mong đợi:** Khi mở `ShadowShape.docx`, bạn sẽ thấy một hình chữ nhật trắng, kích thước 200 × 100 pt, nằm ở giữa đoạn văn đầu tiên, với bóng xám trung bình dịch 5 pt, mờ bán kính 8, và 30 % trong suốt. Hình chữ nhật tự nó có độ trong suốt 40 %, cho phép bất kỳ văn bản nào phía dưới cũng có thể lộ ra.

## Kết luận

Chúng ta vừa **tạo hình chữ nhật** từ đầu, **thêm bóng vào hình**, **áp dụng hiệu ứng bóng**, và thậm chí **đặt độ trong suốt cho hình**—tất cả trong khi **tạo tài liệu trống** làm nền tảng. Cách tiếp cận này đơn giản, dựa trên API mượt mà của Aspose.Words, và có thể mở rộng sang hình tròn, ngôi sao, hoặc đa giác tùy chỉnh.

Bạn sẽ làm gì tiếp theo? Hãy thử thay `ShapeType.RECTANGLE` bằng `ShapeType.OVAL` để tạo các vòng tròn có bóng, hoặc thử nghiệm với các màu gradient cho


## Bạn nên học gì tiếp theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong bài viết này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ cùng các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}