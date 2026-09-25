---
category: general
date: 2026-02-10
description: Tạo hình chữ nhật trong tài liệu Word bằng Aspose.Words cho Java. Tìm
  hiểu cách đặt màu bóng, cách thêm bóng, và tạo tài liệu Word một cách lập trình.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: vi
og_description: Tạo hình chữ nhật trong tài liệu Word bằng Aspose.Words cho Java.
  Thực hiện theo hướng dẫn từng bước này để đặt màu bóng, thêm bóng và tạo tài liệu
  Word.
og_title: Tạo hình chữ nhật trong Word bằng Java – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- Java
- Document Automation
title: Tạo hình chữ nhật trong Word bằng Java – Hướng dẫn đầy đủ
url: /vi/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong Word bằng Java – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **tạo hình chữ nhật** trong một tài liệu Word nhưng không biết bắt đầu từ đâu? Bạn không đơn độc—nhiều nhà phát triển gặp khó khăn này khi lần đầu tiên cố gắng vẽ đồ họa một cách lập trình trong Word. Tin tốt là gì? Với Aspose.Words for Java, bạn có thể chèn một hình chữ nhật vào trang, thêm bóng đẹp mắt và lưu tệp trong vài giây. Trong hướng dẫn này, chúng tôi sẽ trình bày chi tiết **cách thêm bóng**, **đặt màu bóng**, và **tạo tài liệu Word** từ đầu.  

Chúng tôi sẽ bao phủ mọi thứ bạn cần: các thư viện bắt buộc, từng dòng mã, lý do tại sao một số cài đặt quan trọng, và một vài mẹo mà bạn có thể không tìm thấy trong tài liệu chính thức. Khi hoàn thành, bạn sẽ có một ví dụ sẵn sàng chạy tạo hình chữ nhật với bóng xám nhẹ, được lưu dưới tên *Shadow.docx*.

## Các yêu cầu trước – Những gì bạn cần trước khi bắt đầu

Trước khi chúng ta đi vào mã, hãy chắc chắn rằng bạn đã có những thứ sau:

| Yêu cầu | Lý do |
|-------------|--------|
| Java Development Kit (JDK) 8 hoặc mới hơn | Aspose.Words chạy trên bất kỳ JDK hiện đại nào. |
| Maven hoặc Gradle (tùy chọn) | Giúp đơn giản việc thêm phụ thuộc Aspose.Words. |
| Giấy phép Aspose.Words for Java (hoặc bản dùng thử miễn phí) | Thư viện là thương mại; bản dùng thử phù hợp cho việc thử nghiệm. |
| Một IDE (IntelliJ IDEA, Eclipse, VS Code, v.v.) | Giúp bạn chạy và gỡ lỗi ví dụ nhanh chóng. |

Nếu bạn đã có một dự án Java, chỉ cần thêm tọa độ Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Không cần cài đặt phức tạp hơn—chỉ một phương thức `public static void main` đơn giản là đủ.

![ví dụ tạo hình chữ nhật](https://example.com/rectangle-shadow.png "tạo hình chữ nhật có bóng trong Word")

*Image alt text: ví dụ tạo hình chữ nhật cho thấy một hình chữ nhật màu cyan với bóng xám.*

## Bước 1 – Tạo tài liệu Word mới

Điều đầu tiên chúng ta phải làm là khởi tạo một tài liệu trống. Hãy nghĩ đây như việc mở một file Word mới mà bạn sẽ vẽ lên sau này.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Tại sao phải bắt đầu với một `Document` trống? Bởi vì Aspose.Words coi lớp `Document` là canvas cho mọi thao tác tiếp theo—thêm đoạn văn, bảng hoặc hình dạng. Nếu bỏ qua bước này, bạn sẽ gặp `NullPointerException` ngay khi cố chèn bất kỳ đối tượng nào.

## Bước 2 – Thiết lập DocumentBuilder

`DocumentBuilder` là cây bút thân thiện giúp bạn viết vào `Document`. Đây là cách được khuyến nghị để thêm nội dung vì nó tự động quản lý vị trí con trỏ.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Bạn có thể tự hỏi, “Tại sao không thao tác trực tiếp trên tài liệu?” Câu trả lời: builder ẩn đi các chi tiết mức thấp như quản lý section, giúp mã sạch hơn và ít lỗi hơn.

## Bước 3 – Chèn hình chữ nhật

Bây giờ là phần thú vị—**cách tạo shape**. Chúng ta sẽ chèn một hình chữ nhật kích thước 100 × 50 điểm và tô màu cyan để bạn có thể nhìn thấy nó.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

Một vài lưu ý:

* `ShapeType.RECTANGLE` cho Aspose biết chúng ta muốn một hình chữ nhật; bạn có thể thay bằng `OVAL`, `LINE`, v.v.
* Kích thước được biểu thị bằng điểm (1 pt ≈ 1/72 in). Điều chỉnh chúng cho phù hợp với bố cục của bạn.
* Nếu không có màu nền, hình sẽ vô hình trên trang trắng—do đó chúng ta dùng màu cyan.

## Bước 4 – Thêm bóng và **đặt màu bóng**

Đây là nơi chúng ta trả lời phần **cách thêm bóng** của câu hỏi. Đối tượng `ShadowFormat` điều khiển mọi khía cạnh hình ảnh của bóng, từ màu đến bán kính làm mờ.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Tại sao lại dùng các giá trị này?

* **Visibility** – Nếu không gọi `setVisible(true)` các cài đặt khác sẽ bị bỏ qua.
* **Color** – Màu xám là lựa chọn trung tính, hoạt động tốt trên cả nền sáng và tối. Bạn có thể thay `java.awt.Color.GRAY` bằng bất kỳ `java.awt.Color` nào bạn muốn.
* **Blur radius** – Giá trị `5.0` tạo độ mờ nhẹ; số lớn hơn sẽ làm bóng trở nên lan tỏa hơn.
* **OffsetX/Y** – Độ dịch chuyển làm bóng lệ phải và xuống, mô phỏng nguồn sáng từ góc trên‑trái.
* **Transparency** – Bóng bán trong suốt sẽ hòa hợp tốt hơn với trang, đặc biệt khi in.

Nếu bạn muốn bóng sắc nét hơn, hãy hạ bán kính làm mờ xuống `0` và tăng độ dịch chuyển. Hãy thử nghiệm—bóng là yếu tố trực quan, và cài đặt phù hợp phụ thuộc vào thiết kế tài liệu của bạn.

## Bước 5 – Lưu tài liệu

Cuối cùng, chúng ta ghi lại mọi thứ vào tệp `.docx`. Bạn có thể chọn bất kỳ đường dẫn nào; chỉ cần đảm bảo thư mục tồn tại.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Khi mở *Shadow.docx* trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu cyan với bóng xám nhẹ, lệ sang phải và xuống dưới 4 pts. Đó là quy trình **tạo tài liệu Word** hoàn chỉnh.

### Kết quả mong đợi

| Thành phần | Mô tả |
|------------|------|
| Hình chữ nhật | Màu nền xanh lơ, kích thước 100 × 50 pt |
| Bóng | Màu xám, 30 % trong suốt, độ mờ 5 pt, độ dịch chuyển (4, 4) |
| Tệp | `Shadow.docx` được lưu tại đường dẫn bạn cung cấp |

Nếu hình không xuất hiện, hãy kiểm tra lại màu nền không trùng với màu nền trang và bóng đã được đặt là hiển thị.

## Mẹo chuyên nghiệp & Những lỗi thường gặp

* **Mẹo:** Dùng `rectangle.setStrokeColor(java.awt.Color.BLACK);` nếu bạn muốn viền quanh hình. Điều này giúp hình chữ nhật nổi bật hơn trên trang in.
* **Cẩn thận:** Lưu vào thư mục chỉ đọc sẽ gây ra `IOException`. Chọn vị trí có quyền ghi hoặc điều chỉnh quyền truy cập file.
* **Trường hợp đặc biệt:** Nếu cần nền trong suốt (không màu), gọi `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);`. Hình vẫn sẽ tạo bóng, hữu ích cho các đồ họa kiểu watermark.
* **Lưu ý hiệu năng:** Thêm hàng trăm hình trong vòng lặp có thể tăng sử dụng bộ nhớ. Gọi `document.save` chỉ một lần sau khi đã thêm tất cả các hình.

## Ví dụ hoạt động đầy đủ

Dưới đây là toàn bộ chương trình bạn có thể sao chép‑dán vào một lớp Java tên `ShadowDemo`. Nó biên dịch và chạy ngay (miễn là bạn đã thêm JAR Aspose.Words vào classpath).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Chạy chương trình, mở *Shadow.docx* tạo ra, và bạn sẽ thấy hình chữ nhật cùng bóng đúng như mô tả.

## Nếu bạn cần nhiều hình hơn thì sao?

Bạn có thể tự hỏi, “Có thể **tạo hình chữ nhật** nhiều lần hoặc dùng các hình dạng khác không?” Chắc chắn rồi. Chỉ cần lặp lại đoạn chèn và điều chỉnh tọa độ bằng `builder.moveTo` hoặc `builder.insertParagraph`. Các cài đặt bóng có thể tái sử dụng bằng cách trích xuất chúng vào một phương thức trợ giúp:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Gọi `applyStandardShadow(rectangle);` sau mỗi lần chèn hình để giữ mã của bạn DRY (Don’t Repeat Yourself).

## Các bước tiếp theo – Vượt ra ngoài cơ bản

Bây giờ bạn đã biết **cách thêm bóng**, hãy khám phá các chủ đề liên quan sau:

* **Cách đặt màu bóng** cho các đoạn văn bản – tạo cảm giác nổi bật nhẹ cho tiêu đề.
* **Tạo tài liệu Word** với bảng và hình ảnh – kết hợp hình dạng với nội dung khác.
* **Cách tạo shape** hoạt ảnh bằng tính năng sẵn có của Word

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}