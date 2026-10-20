---
category: general
date: 2026-03-19
description: Tìm hiểu cách đặt bóng cho hình dạng một cách nhanh chóng, thêm bóng
  vào hình, thay đổi độ trong suốt, làm mờ bóng và thiết lập khoảng cách bằng Aspose.Words
  for Java.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- how to change transparency
- how to blur shadow
- how to set distance
language: vi
og_description: Nắm vững cách đặt bóng cho một hình dạng trong Aspose.Words. Hướng
  dẫn này chỉ cách thêm bóng vào hình dạng, thay đổi độ trong suốt, làm mờ bóng và
  thiết lập khoảng cách.
og_title: Cách Đặt Bóng cho Hình Dạng – Hướng Dẫn Java Từng Bước
tags:
- Aspose.Words
- Java
- ShapeShadow
title: Cách Đặt Bóng Cho Hình Dạng trong Aspose.Words – Hướng Dẫn Đầy Đủ
url: /vi/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Bóng Đổ cho Hình Dạng trong Aspose.Words – Hướng Dẫn Toàn Diện

Bạn đã bao giờ tự hỏi **cách đặt bóng** cho một hình dạng mà không phải lục lọi qua vô vàn tài liệu API chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi cần một bóng đổ nhẹ nhàng cho sơ đồ, logo hoặc chú thích trong tài liệu Word. Tin tốt là gì? Với Aspose.Words for Java, việc này cực kỳ đơn giản và bạn có thể thực hiện chỉ trong vài dòng mã.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình: **thêm bóng cho hình dạng**, điều chỉnh **độ trong suốt**, áp dụng **làm mờ**, và tinh chỉnh **khoảng cách** và góc. Khi kết thúc, bạn sẽ có một hình dạng được định dạng hoàn chỉnh, trông chuyên nghiệp, và hiểu được lý do mỗi thuộc tính quan trọng như thế nào.

---

## Yêu Cầu Trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

- Java 8 hoặc mới hơn đã được cài đặt.  
- Aspose.Words for Java (phiên bản mới nhất; tại thời điểm viết là v24.10).  
- Một tệp `.docx` đơn giản chứa ít nhất một hình dạng (ví dụ: hình chữ nhật hoặc ảnh) trong tệp `input.docx`.  
- IDE yêu thích của bạn (IntelliJ IDEA, Eclipse, VS Code… bất kỳ đều được).

Không cần thư viện bổ sung—Aspose.Words đã bao gồm mọi thứ bạn cần.

---

## Cách Đặt Bóng Đổ cho Hình Dạng – Các Bước Thực Hiện

Dưới đây chúng tôi chia giải pháp thành các bước nhỏ gọn. Mỗi bước bao gồm một đoạn mã ngắn, giải thích **tại sao** chúng ta thực hiện, và một mẹo hữu ích.

### 1. Tải tài liệu nguồn

Đầu tiên chúng ta cần một đối tượng `Document` trỏ tới tệp trên đĩa. Hãy nghĩ nó như việc mở một tệp Word trong bộ nhớ.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*​Tại sao điều này quan trọng:* Nếu không có tài liệu đã tải, bạn sẽ không có gì để chỉnh sửa. Lớp `Document` là điểm khởi đầu cho mọi thao tác Aspose.Words.

> **Mẹo chuyên nghiệp:** Sử dụng đường dẫn tuyệt đối trong quá trình phát triển để tránh những bất ngờ “file not found”.

### 2. Thêm bóng đổ cho hình dạng – lấy hình dạng đầu tiên

Bây giờ chúng ta xác định hình dạng muốn định dạng. Bộ chọn `NodeType.SHAPE` duyệt cây node và trả về `Shape` đầu tiên nó gặp.

```java
        // Step 2: Retrieve the first shape in the document
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
```

*​Tại sao điều này quan trọng:* Hình dạng có thể là ảnh, bản vẽ hoặc SmartArt. Lấy đúng node đảm bảo chúng ta không vô tình chỉnh sửa một đoạn văn hay bảng.

> **Cảnh báo:** Nếu tài liệu của bạn không có hình dạng nào, `firstShape` sẽ là `null` và các dòng tiếp theo sẽ ném ra `NullPointerException`. Luôn kiểm tra `null` trong mã sản xuất.

### 3. Cách Thay Đổi Độ Trong Suốt của Bóng Đổ

Bóng đổ hoàn toàn đục nhìn nặng nề. Thiết lập thuộc tính `transparency` cho phép bạn giảm độ đậm thành một lớp mỏng nhẹ.

```java
        // Step 3: Obtain the shadow formatting object for the shape
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Step 4: Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);
```

*​Tại sao điều này quan trọng:* Độ trong suốt kiểm soát mức độ nội dung nền hiển thị qua bóng. Giá trị `0.0` là màu đen đặc; `0.3` tạo hiệu ứng nhẹ, trong suốt.

> **Sai lầm thường gặp:** Quên gọi `setTransparency` sẽ để mặc định (đầy đủ đục), khiến bóng trông quá gắt.

### 4. Cách Làm Mờ Bóng Đổ

Làm mờ làm mềm các cạnh, khiến bóng trông tự nhiên hơn, đặc biệt trên màn hình độ phân giải cao.

```java
        // Step 5: Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);
```

*​Tại sao điều này quan trọng:* Bán kính làm mờ `0` tạo ra cạnh sắc nét, không thực tế. Tăng bán kính sẽ lan rộng bóng, mô phỏng cách ánh sáng khuếch tán trong thực tế.

> **Kiểm tra nhanh:** Thay đổi `5.0` thành `10.0` và chạy lại—nhận thấy bóng trở nên mềm mại hơn.

### 5. Cách Đặt Khoảng Cách và Góc của Bóng Đổ

Khoảng cách di chuyển bóng ra xa hình dạng, trong khi góc quyết định hướng của nguồn sáng.

```java
        // Step 6: Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Step 7: Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);
```

*​Tại sao điều này quan trọng:* Khoảng cách `0` gắn bóng ngay sau hình dạng, thường trông phẳng. Góc `45°` mô phỏng nguồn sáng từ trên‑trái, một lựa chọn thiết kế phổ biến.

> **Trường hợp đặc biệt:** Góc được đo theo chiều kim đồng hồ từ trục ngang. Góc `180` sẽ lật bóng sang phía đối diện.

### 6. Lưu tài liệu

Cuối cùng, ghi tài liệu đã chỉnh sửa trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc tạo tệp mới.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");
    }
}
```

*​Tại sao điều này quan trọng:* Lưu lại sẽ lưu trữ tất cả các thiết lập bóng mà bạn vừa cấu hình. Mở tệp kết quả trong Word để xem hiệu ứng.

---

## Ví Dụ Hoàn Chỉnh

Kết hợp tất cả lại, đây là chương trình hoàn chỉnh, sẵn sàng chạy:

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the first shape (add null‑check for safety)
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape == null) {
            System.out.println("No shapes found in the document.");
            return;
        }

        // Access the shadow format
        ShadowFormat shadowFormat = firstShape.getShadowFormat();

        // Make the shadow 30 % transparent
        shadowFormat.setTransparency(0.3);

        // Apply a soft blur with a radius of 5 points
        shadowFormat.setBlurRadius(5.0);

        // Set the shadow offset distance to 4 points
        shadowFormat.setDistance(4.0);

        // Define the shadow direction angle (45 degrees)
        shadowFormat.setAngle(45.0);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.out.println("Shadow applied successfully!");
    }
}
```

**Kết quả mong đợi:** Mở `output_with_shadow.docx`. Hình dạng đầu tiên sẽ hiển thị một bóng mềm, trong suốt 30 %, hơi mờ, dịch chuyển 4 pts ở góc 45°. Trông như hình đang nổi lên trên trang.

---

## Câu Hỏi Thường Gặp (FAQ)

### Tôi có thể thêm bóng cho nhiều hình dạng cùng lúc không?

Chắc chắn. Thay thế việc lấy một hình duy nhất bằng một vòng lặp:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node node : shapes) {
    Shape shape = (Shape) node;
    ShadowFormat sf = shape.getShadowFormat();
    // Apply the same settings or vary per shape
}
```

### Nếu tôi muốn bóng có màu thay vì màu đen thì sao?

`ShadowFormat` cũng cung cấp phương thức `setColor(Color)`. Đối với bóng màu xanh đậm:

```java
shadowFormat.setColor(Color.fromArgb(0, 0, 255));
```

### Điều này có hoạt động với ảnh bên trong hình dạng không?

Có. Aspose.Words coi ảnh là đối tượng `Shape` miễn là chúng được chèn dưới dạng “Picture” (không inline). Các thuộc tính bóng giống nhau được áp dụng.

### Bán kính làm mờ được đo bằng điểm hay pixel?

Nó được đo bằng điểm (1 pt = 1/72 in). Điều này giữ cho giao diện nhất quán trên các cài đặt DPI khác nhau.

---

## Kết Luận

Chúng tôi đã trình bày **cách đặt bóng** cho một hình dạng từ đầu đến cuối, minh họa **thêm bóng cho hình dạng**, cho thấy **cách thay đổi độ trong suốt**, giải thích **cách làm mờ bóng**, và cuối cùng chi tiết **cách đặt khoảng cách** và góc. Mã ngắn gọn, khái niệm rõ ràng, và bạn đã có một mẫu có thể tái sử dụng để định dạng bất kỳ hình dạng nào trong Aspose.Words for Java.

Sẵn sàng cho thử thách tiếp theo? Hãy thử kết hợp các thiết lập bóng này với **gradient fills**, hoặc thử nghiệm **nhiều bóng** bằng cách sao chép hình dạng và dịch chuyển mỗi bản sao. Không gì là không thể, và với các công cụ vừa học, bạn sẽ nhanh chóng tạo nên vẻ chuyên nghiệp cho tài liệu.

Nếu bạn thấy hướng dẫn này hữu ích, hãy để lại bình luận, chia sẻ các biến thể của bạn, hoặc khám phá các hướng dẫn khác của chúng tôi về **định dạng hình dạng**, **hiệu ứng văn bản**, và **chuyển đổi tài liệu**. Chúc lập trình vui vẻ! 

![how to set shadow on a shape example](image.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}