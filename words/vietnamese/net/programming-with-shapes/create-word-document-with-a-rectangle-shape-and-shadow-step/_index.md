---
category: general
date: 2026-03-01
description: Tạo tài liệu Word bằng Aspose.Words và học cách thêm hình chữ nhật, cách
  thêm bóng, cách đặt độ trong suốt và cách tạo hình—tất cả bằng C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: vi
og_description: Tạo tài liệu Word với Aspose.Words trong C#. Tìm hiểu cách thêm hình
  chữ nhật, áp dụng bóng ngoài và thiết lập độ trong suốt chỉ trong vài bước.
og_title: Tạo tài liệu Word với hình chữ nhật và bóng – Hướng dẫn
tags:
- Aspose.Words
- C#
- Document Generation
title: Tạo tài liệu Word với hình chữ nhật và bóng – Hướng dẫn từng bước
url: /vi/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word với hình chữ nhật và bóng – Hướng dẫn từng bước

Bạn đã bao giờ cần **create word document** chứa một hình chữ nhật được tùy chỉnh? Có thể bạn đang xây dựng mẫu báo cáo và muốn một bóng đổ nhẹ để làm nổi bật bố cục. Bạn không phải là người duy nhất—các nhà phát triển thường hỏi, “Làm thế nào để thêm hình chữ nhật và bóng một cách lập trình?” Tin tốt là với Aspose.Words bạn có thể thực hiện trong vài dòng.

Trong tutorial này chúng ta sẽ đi qua toàn bộ quy trình: từ việc khởi tạo một file Word trống, đến việc thêm hình chữ nhật, đến việc cấu hình bóng ngoài với độ trong suốt. Khi kết thúc, bạn sẽ có một file `Shadow.docx` sẵn sàng sử dụng, có thể mở trong Word và thấy hiệu ứng ngay lập tức. Không cần công cụ bên ngoài, không cần XML rắc rối—chỉ cần mã C# sạch sẽ và giải thích rõ ràng.

## Những gì bạn sẽ học

- **How to create shape** objects in a Word document using Aspose.Words.
- **How to add rectangle shape** to a paragraph without messing up existing content.
- **How to add shadow** (outer shadow) and control its color, offset, blur, and transparency.
- **How to set transparency** on the shadow so it looks professional.
- Tips, pitfalls, and variations you might need in real‑world projects.

### Yêu cầu trước

- .NET 6.0 hoặc mới hơn (API cũng hoạt động với .NET Framework 4.6+).
- Aspose.Words for .NET được cài đặt qua NuGet (`Install-Package Aspose.Words`).
- Kiến thức cơ bản về cú pháp C#—không cần gì phức tạp, chỉ các câu lệnh `using` và tạo đối tượng thông thường.

> **Pro tip:** Nếu bạn đang dùng Visual Studio, bật “nullable reference types” để phát hiện sớm các lỗi tham chiếu null tiềm năng.

## Bước 1 – Tạo tài liệu Word trống

Để **create word document** chúng ta bắt đầu với lớp `Document`. Hãy nghĩ nó như một canvas trống; sau này bạn có thể thêm các section, paragraph, table hoặc shape.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Tại sao chúng ta cần một instance `Document` mới? Bởi vì mọi shape, paragraph, hay style đều tồn tại trong mô hình đối tượng tài liệu (DOM). Bắt đầu với một tài liệu sạch sẽ đảm bảo rằng hình chữ nhật bạn thêm sẽ không gây xung đột với nội dung hiện có.

## Bước 2 – Định nghĩa hình chữ nhật

Bây giờ chúng ta **how to create shape** một hình chữ nhật. Constructor `Shape` nhận tài liệu sở hữu và kiểu shape. Chúng ta cũng đặt chiều rộng và chiều cao bằng điểm (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Bạn có thể thắc mắc, “Có thể dùng centimet thay vì điểm không?” API chỉ chấp nhận điểm, nhưng bạn có thể chuyển đổi: `points = centimeters * 28.35`. Phép chuyển đổi này rất hữu ích khi bạn căn chỉnh shape theo lề trang.

## Bước 3 – Thêm bóng ngoài và đặt độ trong suốt

Đây là nơi phép thuật xảy ra: **how to add shadow** và **how to set transparency** cho bóng đó. Thuộc tính `ShadowFormat` cho phép bạn kiểm soát hoàn toàn.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Why these settings?**  
- **Transparency** cho phép kết cấu trang nền hiện ra, tránh bóng trông quá nặng.  
- **OffsetX/Y** tạo ảo giác shape được nâng lên khỏi trang.  
- **BlurRadius** làm mềm các cạnh—không có nó, bóng sẽ là một hình chữ nhật cứng, trông không tự nhiên.

Nếu bạn muốn hiệu ứng mạnh hơn, tăng `OffsetX/Y` lên 10 và tăng `BlurRadius` lên 8. Ngược lại, để có dấu hiệu nhẹ nhàng, giữ chúng ở 2 và 2 tương ứng.

## Bước 4 – Chèn hình vào tài liệu

Chúng ta bây giờ **add rectangle shape** vào paragraph đầu tiên của tài liệu. Nếu tài liệu không có nội dung, `FirstParagraph` sẽ được tạo tự động cho bạn.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Nếu bạn muốn shape nằm trong một ô bảng cụ thể hoặc một paragraph sau này? Chỉ cần tìm node đó (`doc.GetChild(NodeType.Paragraph, index, true)`) và gọi `AppendChild` trên nó. Cùng một đối tượng shape có thể được sao chép nếu bạn cần nhiều bản sao.

## Bước 5 – Lưu tài liệu

Cuối cùng, chúng ta **create word document** trên đĩa. Sử dụng đường dẫn phù hợp với môi trường của bạn; ví dụ sử dụng một placeholder.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Khi bạn mở `Shadow.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu xám nhạt với bóng ngoài mềm mại lệch về phía dưới‑phải. Độ trong suốt 30 % của bóng đảm bảo nó không chiếm ưu thế trên trang.

---

![Create word document with a shadowed rectangle shape](image.png "Create word document with a shadowed rectangle")

*Văn bản thay thế hình ảnh: create word document with a shadowed rectangle shape*

## Mã đầy đủ, sẵn sàng chạy

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào một console app. Không thiếu bất kỳ phần nào, không có “xem tài liệu để biết thêm”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Kết quả mong đợi

- Một file có tên **Shadow.docx** xuất hiện trong thư mục đích.
- Khi mở trong Word, sẽ hiển thị một hình chữ nhật (200 × 100 pt) với bóng ngoài màu xám đậm.
- Bóng được lệch 5 pt theo chiều ngang và dọc, có độ mờ và trong suốt 30 %.

## Câu hỏi thường gặp & Trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Can I change the shadow color to match my brand?** | Absolutely—just replace `System.Drawing.Color.DarkGray` with any `Color` you prefer, e.g., `Color.FromArgb(255, 0, 120, 215)` for a blue accent. |
| **What if I need an inner shadow instead of outer?** | Set `ShadowFormat.Style = ShadowStyle.InnerShadow`. The rest of the properties behave the same. |
| **Is transparency supported in older Word versions?** | Yes. Aspose.Words writes the appropriate XML that Word 2007+ understands. Older versions may ignore the transparency value but will still show the shadow. |
| **Can I add multiple shapes with different shadows?** | Sure—just create new `Shape` instances, configure each shadow independently, and append them to the desired nodes. |
| **What about performance for hundreds of shapes?** | Creating many shapes can increase memory usage. Reuse a single `Document` instance and add shapes in a loop; dispose of temporary objects if you run into pressure. |

## Mẹo cho dự án thực tế

- **Batch generation:** Khi tạo báo cáo cho nhiều người dùng, khởi tạo một mẫu `Document` duy nhất và sao chép nó cho mỗi vòng lặp. Thay thế các placeholder trước khi thêm shape.
- **Dynamic sizing:** Sử dụng kích thước trang (`document.FirstSection.PageSetup.PageWidth`) để tính kích thước shape tương đối với trang, đảm bảo bố cục nhất quán trên các kích thước giấy khác nhau.
- **Testing:** Luôn mở file `.docx` đã tạo trong Word sau khi thay đổi các tham số bóng. Phản hồi trực quan nhanh hơn việc đoán số.

## Các bước tiếp theo

Bây giờ bạn đã biết **how to add rectangle shape**, **how to add shadow**, và **how to set transparency**, hãy khám phá thêm:

- Thêm **gradient fills** cho shape (`Shape.FillFormat`).
- Nhúng **pictures** vào shape để tạo hiệu ứng watermark.
- Sử dụng **tables** để căn chỉnh nhiều shape có bóng trong một lưới.
- Xuất cùng một tài liệu sang PDF (`document.Save("output.pdf")`) trong khi vẫn giữ nguyên bóng.

Mỗi mục trên đều dựa trên các khái niệm cốt lõi, vì vậy bạn sẽ cảm thấy thoải mái khi mở rộng mã.

---

### Tóm tắt

Chúng ta bắt đầu bằng **create word document** với Aspose.Words, sau đó **how to create shape** một hình chữ nhật, áp dụng **how to add shadow**, tinh chỉnh **how to set transparency**, và lưu kết quả. Toàn bộ quy trình nằm trong một mẫu ngắn gọn, có thể tái sử dụng và bạn có thể điều chỉnh cho bất kỳ kịch bản tự động hoá nào.

Hãy thoải mái thử nghiệm—thay đổi màu sắc, chơi với offset, hoặc xếp chồng nhiều shape lại với nhau. Khi gặp khó khăn, hãy quay lại các phần trên; chúng được thiết kế như một tài liệu tham khảo nhanh. Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn trông thật chuyên nghiệp!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}