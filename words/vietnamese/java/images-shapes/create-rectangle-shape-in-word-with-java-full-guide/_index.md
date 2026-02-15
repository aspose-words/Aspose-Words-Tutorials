---
category: general
date: 2026-02-15
description: Tạo hình chữ nhật trong tài liệu Word bằng Java. Tìm hiểu cách thêm bóng
  cho hình dạng, lưu tài liệu Word và thêm hình chữ nhật bằng Aspose.Words.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: vi
og_description: Tạo hình chữ nhật trong tệp Word bằng Java. Hướng dẫn này chỉ cách
  thêm bóng cho hình dạng, lưu tài liệu Word và thêm hình chữ nhật từng bước.
og_title: Tạo hình chữ nhật – Hướng dẫn Aspose.Words cho Java
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

Bạn đã bao giờ cần **create rectangle shape** trong một tệp Word nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn này khi tự động hoá báo cáo hoặc hoá đơn. Tin tốt là gì? Với Aspose.Words for Java, bạn có thể tạo một hình chữ nhật, thêm bóng đẹp, và lưu tài liệu Word chỉ trong vài dòng mã.

Trong tutorial này, chúng ta sẽ đi qua mọi thứ bạn cần: từ khởi tạo một tài liệu trống, cấu hình bóng, đến cuối cùng lưu tệp. Khi kết thúc, bạn sẽ biết **how to shadow shape** các đối tượng, cách **add shape shadow**, và cách **add rectangle shape** vào bất kỳ tài liệu Word nào bạn tạo. Không cần tài liệu bên ngoài—chỉ cần mã chạy được.

## Yêu cầu trước

- Java 8 hoặc mới hơn (API cũng hoạt động với Java 11+).  
- Thư viện Aspose.Words for Java (phiên bản 23.9 hoặc mới hơn).  
- Một IDE như IntelliJ IDEA hoặc Eclipse—bất kỳ cái nào cũng được.  
- Kiến thức cơ bản về cú pháp Java.

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng Maven, thêm phụ thuộc Aspose.Words vào `pom.xml` của bạn và để IDE xử lý phần còn lại.

---

## Bước 1: Khởi tạo tài liệu mới – Cách **create rectangle shape**  

Đầu tiên: bạn cần một canvas sạch. Trong Aspose.Words, canvas đó là một đối tượng `Document`.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

Lớp `Document` đại diện cho toàn bộ tệp .docx. Hãy nghĩ nó như một cuốn sổ mà sau này bạn sẽ **add rectangle shape** và bóng của nó.

## Bước 2: Xây dựng hình chữ nhật – **Add rectangle shape**  

Bây giờ chúng ta thực sự tạo hình chữ nhật. Chúng ta sẽ đặt kích thước, bố cục và màu nền của nó.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Tại sao lại `INLINE` wrap? Bởi vì chúng ta muốn hình dạng hoạt động như một đoạn văn—hoàn hảo cho các báo cáo đơn giản. Bạn có thể đổi thành `TOPBOTTOM` nếu cần văn bản bao quanh hình sau này.

## Bước 3: Áp dụng bóng – **How to shadow shape**  

Một hình chữ nhật phẳng trông hơi nhạt. Thêm bóng giúp nó có chiều sâu và làm tài liệu trông chuyên nghiệp hơn. Đây là nơi chúng ta trả lời “**how to shadow shape**” trong thực tế.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Mỗi thuộc tính thực hiện một chức năng cụ thể:

- `setVisible(true)` bật bóng.  
- `setColor` chọn màu xám đậm cho hiệu ứng nhẹ nhàng.  
- `setBlurRadius` kiểm soát độ mềm của các cạnh.  
- `setOffsetX/Y` di chuyển bóng sang phải và xuống, mô phỏng nguồn sáng.  
- `setTransparency` làm bóng hơi trong suốt, để hình vẫn là trung tâm.

> **Lưu ý:** Nếu bạn cần bóng màu, chỉ cần truyền một `java.awt.Color` khác vào `setColor`.

## Bước 4: Chèn hình vào tài liệu  

Khi hình chữ nhật và bóng của nó đã sẵn sàng, chúng ta chèn nó vào phần đầu tiên của tài liệu.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Thêm vào body đặt hình ở vị trí mà một đoạn văn mới sẽ xuất hiện. Nếu bạn muốn hình chữ nhật ở vị trí cụ thể, có thể dùng `insertBefore` hoặc thao tác với bộ sưu tập `Paragraph`.

## Bước 5: **Save Word document** – Lưu công việc của bạn  

Bước cuối cùng là ghi tệp ra đĩa. Đây là lúc bạn thực sự **save Word document**.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Thay `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối trên máy của bạn. Sau khi chạy chương trình, mở `ShadowShape.docx` trong Microsoft Word—bạn sẽ thấy một hình chữ nhật màu xám nhạt với bóng tối mềm.

![Sơ đồ hiển thị hình chữ nhật có bóng được tạo bằng Aspose.Words](https://example.com/rectangle-shadow.png "tạo hình chữ nhật với bóng")

---

## Câu hỏi thường gặp & Trường hợp đặc biệt  

### Nếu tôi cần nhiều hình chữ nhật?

Chỉ cần lặp lại **Step 2** và **Step 3** trong một vòng lặp, điều chỉnh `setWidth`, `setHeight`, hoặc `setFillColor` mỗi lần. Hãy nhớ đặt tên biến duy nhất cho mỗi hình hoặc lưu chúng vào một danh sách.

### Có thể xuất ra PDF thay vì DOCX không?

Chắc chắn. Sau khi hình đã được thêm, gọi `document.save("output.pdf")`. Aspose.Words sẽ xử lý việc chuyển đổi, giữ nguyên bóng.

### Còn các phiên bản Word cũ hơn thì sao?

Sử dụng overload `document.save("file.doc", SaveFormat.DOC)`. API sẽ tự động hạ cấp các tính năng, nhưng lưu ý rằng một số kiểu bóng có thể trông hơi khác trong định dạng cũ.

### Làm sao thay đổi hướng bóng?

Điều chỉnh `setOffsetX` và `setOffsetY`. Giá trị X dương di chuyển bóng sang phải, âm sang trái. Giá trị Y dương di chuyển xuống, âm lên. Thử nghiệm các số này để mô phỏng nguồn sáng từ bất kỳ góc nào.

---

## Mẹo khi làm việc với hình dạng  

- **Group shapes**: Nếu bạn cần một nhãn bên cạnh hình chữ nhật, tạo một `GroupShape` và thêm cả hình chữ nhật và một `TextBox`.  
- **Z‑order matters**: Sử dụng `shape.moveToFront()` hoặc `shape.moveToBack()` để kiểm soát hình nào xuất hiện phía trên.  
- **Performance**: Thêm hàng trăm hình có thể chậm. Gom chúng vào một phần duy nhất, sau đó gọi `document.updatePageLayout()` một lần ở cuối.

---

## Tóm tắt  

Chúng ta đã đề cập cách **create rectangle shape** trong tài liệu Word bằng Java, cách **add shape shadow**, và cách **save Word document** với kết quả. Mã hoàn chỉnh, có thể chạy được nằm trong các đoạn trên, và bạn giờ đã hiểu “tại sao” đằng sau mỗi thuộc tính—để có thể điều chỉnh màu, độ mờ và độ dịch chuyển phù hợp với bất kỳ thiết kế nào.

Sẵn sàng cho thử thách tiếp theo? Hãy thử kết hợp hình chữ nhật với biểu đồ, hoặc xuất tệp ra PDF và xem bóng được hiển thị như thế nào. Bạn cũng có thể khám phá **add rectangle shape** trong bảng để có bố cục báo cáo đẹp mắt.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn sắc nét như code của bạn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}