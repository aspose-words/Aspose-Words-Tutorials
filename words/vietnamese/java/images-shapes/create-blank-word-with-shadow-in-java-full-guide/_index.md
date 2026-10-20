---
category: general
date: 2026-05-04
description: Tạo tài liệu Word trống trong Java và học cách thiết lập màu bóng, độ
  mờ và độ dịch chuyển cho các hình dạng – hướng dẫn nhanh.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: vi
og_description: Tạo tài liệu Word trống trong Java và học cách đặt màu bóng, độ mờ
  và độ dịch chuyển cho các hình dạng. Hãy làm theo hướng dẫn từng bước này.
og_title: Tạo từ trống có bóng trong Java – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- Java
- Document Automation
title: Tạo từ trống có bóng trong Java – Hướng dẫn đầy đủ
url: /vi/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống có bóng trong Java – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **tạo tài liệu Word trống** từ mã và muốn chúng trông hơi sang trọng hơn chưa? Bạn không phải là người duy nhất. Trong nhiều dự án báo cáo hoặc tạo mẫu, việc đầu tiên bạn làm là khởi tạo một tài liệu Word rỗng, sau đó thêm một hình dạng có bóng để tạo cảm giác hoàn thiện.  

Trong hướng dẫn này, chúng ta sẽ đi qua từng bước—cách tạo tài liệu Word trống bằng Aspose.Words for Java, **cách thêm bóng** vào một hình dạng, và các chi tiết như **đặt màu bóng**, **cách đặt độ mờ**, và **cách đặt độ dịch chuyển**. Khi hoàn thành, bạn sẽ có một tệp `.docx` sẵn sàng sử dụng, hiển thị một hình chữ nhật với bóng màu đỏ bán trong suốt, được làm mờ nhẹ.

## Những gì bạn cần

- **Aspose.Words for Java** (bất kỳ phiên bản mới nào; mã hoạt động với 23.9+)
- JDK 8 trở lên
- Một IDE hoặc trình soạn thảo văn bản đơn giản cộng với terminal
- Kiến thức cơ bản về Java—không cần gì phức tạp, chỉ cần có khả năng chạy một phương thức `main`

Không cần cấu hình Maven hay Gradle nào thêm cho bản demo; chỉ cần đưa file JAR của Aspose vào classpath và bạn đã sẵn sàng.

---

![create blank word document with shadow example](image-placeholder.png){: .center alt="ví dụ tài liệu Word trống có bóng"}

## Tạo tài liệu Word trống – Khởi tạo Document

Bước đầu tiên là tạo một tệp Word mới, hoàn toàn trống. Hãy nghĩ đây là một bức tranh trắng, nơi bạn có thể vẽ các hình dạng, bảng hoặc văn bản sau này.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Tại sao điều này quan trọng:** `Document` đại diện cho toàn bộ gói `.docx`. Khi tạo nó bằng constructor mặc định, bạn thực sự **tạo tài liệu Word trống** – không có nội dung, không có phần, chỉ có cấu trúc tệp sẵn sàng để bạn lấp đầy.

## Cách thêm bóng vào một hình dạng

Bây giờ chúng ta đã có tài liệu sạch, hãy chèn một hình chữ nhật sẽ chứa bóng của chúng ta. Đây là nơi phép thuật hình ảnh bắt đầu.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Mẹo chuyên nghiệp:** Lệnh `insertShape` tự động thêm hình vào đoạn hiện tại, vì vậy bạn không cần quản lý vị trí thủ công trừ khi muốn đặt vị trí tuyệt đối.

## Đặt màu bóng – làm bóng nổi bật hơn

Một bóng không màu chỉ là một vùng mờ xám, có thể trông phẳng. Bằng cách đặt màu cho bóng, bạn có thể phù hợp với thương hiệu hoặc chỉ đơn giản là làm nó nổi bật.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **Điều đang xảy ra:** `ShadowFormat` kiểm soát mọi khía cạnh hình ảnh của bóng. Bật `setVisible(true)` kích hoạt hiệu ứng, và `setColor` cho phép bạn chọn bất kỳ `java.awt.Color` nào. Trong ví dụ, chúng tôi chọn màu đỏ để minh họa **đặt màu bóng** một cách rõ ràng.

## Cách đặt độ mờ để tạo hiệu ứng nhẹ nhàng

Một bóng sắc nét, có cạnh cứng có thể trông gắt gao. Thêm độ mờ làm mềm các cạnh, tạo cảm giác tự nhiên hơn.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Tại sao độ mờ quan trọng:** Giá trị `setBlur` được đo bằng điểm. Giá trị `5.0` tạo ra một sự lan tỏa nhẹ; tăng lên để bóng mờ hơn, giảm xuống để có viền sắc nét hơn.

## Cách đặt độ dịch chuyển – định vị bóng

Độ dịch chuyển xác định vị trí bóng so với hình dạng. Hãy nghĩ chúng như các dịch chuyển theo trục X và Y.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Giải thích độ dịch chuyển:** Giá trị X dương di chuyển bóng sang phải, giá trị Y dương di chuyển bóng xuống. Thử nghiệm với số âm nếu bạn muốn bóng xuất hiện ở phía đối diện.

## Tinh chỉnh độ trong suốt

Nếu bạn muốn bóng ít chiếm ưu thế hơn, hãy điều chỉnh độ trong suốt. Bước này không phải là yêu cầu bắt buộc nhưng giúp hoàn thiện kiểm soát hình ảnh.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Lưu tài liệu – xem kết quả

Cuối cùng, ghi tài liệu ra đĩa. Bạn sẽ có một tệp `.docx` có thể mở bằng Word, LibreOffice, hoặc bất kỳ trình xem nào hỗ trợ định dạng này.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **Bạn sẽ thấy gì:** Mở `ShadowShape.docx`. Một trang duy nhất sẽ hiển thị một hình chữ nhật 150 × 80 pt với bóng màu đỏ, hơi mờ, dịch chuyển 8 pt xuống và sang phải. Bóng có độ trong suốt 30 %, vì vậy hình chữ nhật vẫn rõ ràng.

---

## Các câu hỏi thường gặp và trường hợp đặc biệt

### Nếu tôi cần một hình dạng khác thì sao?

Thay `ShapeType.RECTANGLE` bằng bất kỳ giá trị enum nào khác (`ELLIPSE`, `CLOUD`, `CALLOUT`, v.v.). Các cài đặt bóng hoạt động giống nhau cho mọi hình dạng.

### Tôi có thể áp dụng cùng một bóng cho nhiều hình dạng mà không lặp lại mã không?

Chắc chắn rồi. Tạo một phương thức trợ giúp:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Sau đó gọi `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` cho bất kỳ hình dạng nào.

### Điều này có hoạt động với các phiên bản Aspose cũ không?

API `ShadowFormat` đã ổn định từ phiên bản 19.8, vì vậy bạn sẽ ổn với hầu hết các bản phát hành gần đây. Nếu bạn đang dùng một bản rất cũ, hãy kiểm tra Javadoc của `ShadowFormat` để xác nhận tên phương thức.

### Cách xuất ra PDF mà vẫn giữ bóng?

Chỉ cần gọi `document.save("output.pdf");` sau khi tạo hình dạng. Aspose.Words render bóng đúng trong PDF, giữ nguyên độ mờ và độ trong suốt.

---

## Tóm tắt – tạo tài liệu Word trống với bóng tùy chỉnh

Chúng ta bắt đầu bằng **tạo tài liệu Word trống** bằng `new Document()`, sau đó chèn một hình chữ nhật, **đặt màu bóng**, học **cách thêm bóng**, tinh chỉnh **cách đặt độ mờ**, và cuối cùng điều chỉnh **cách đặt độ dịch chuyển** để đặt vị trí chính xác. Mã hoàn chỉnh, có thể chạy được nằm trong các đoạn trên, và tệp kết quả minh họa hiệu ứng một cách rõ ràng.

---

## Tiếp theo?

- **Thử nghiệm các thuộc tính bóng khác** như `ShadowFormat.setStyle(ShadowStyle.OUTER)` để có các phong cách hình ảnh khác.
- **Kết hợp nhiều hình dạng** mỗi cái có bóng riêng để xây dựng các sơ đồ phức tạp.
- **Thêm văn bản vào bên trong hình** bằng `builder.insertHtml("<b>Hello</b>")` trước khi chèn hình, sau đó áp dụng cùng logic bóng.
- **Khám phá các tùy chọn định dạng khác** như kiểu đường viền, màu nền, hoặc gradient—Aspose.Words cung cấp API phong phú cho tất cả những điều này.

Hãy tự do điều chỉnh bán kính mờ, độ dịch chuyển hoặc màu sắc cho đến khi bóng cảm thấy hoàn hảo với ngôn ngữ thiết kế của tài liệu. Chúc bạn lập trình vui vẻ, và hy vọng các tệp Word bạn tạo ra luôn trông tinh tế hơn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}