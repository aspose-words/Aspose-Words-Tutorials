---
category: general
date: 2025-12-29
description: Tạo hình chữ nhật trong tài liệu Word bằng Aspose.Words C#. Tìm hiểu
  cách đặt độ trong suốt cho hình, đặt màu bóng và lưu tài liệu Word một cách dễ dàng.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: vi
og_description: Tạo hình chữ nhật trong tài liệu Word bằng Aspose.Words C#. Hướng
  dẫn này chỉ cách đặt độ trong suốt cho hình, đặt màu bóng và lưu tài liệu Word.
og_title: Tạo hình chữ nhật trong Word – Hướng dẫn đầy đủ Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Tạo hình chữ nhật trong Word bằng Aspose.Words – Hướng dẫn từng bước
url: /vi/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong Word – Hướng dẫn đầy đủ Aspose.Words

Bạn đã bao giờ cần **tạo hình chữ nhật** trong tài liệu Word nhưng không biết bắt đầu từ đâu? Bạn không đơn độc; nhiều nhà phát triển gặp khó khăn này khi tự động hoá báo cáo hoặc hoá đơn. Trong hướng dẫn này, chúng tôi sẽ đi qua các bước chính xác để tạo hình chữ nhật, đặt độ trong suốt cho hình, đặt màu bóng, và cuối cùng **lưu tài liệu Word** bằng Aspose.Words cho .NET.  

Chúng tôi sẽ bao phủ mọi thứ từ đối tượng tài liệu ban đầu đến tệp `.docx` cuối cùng trên đĩa, vì vậy sau khi đọc xong, bạn sẽ có thể **tạo tài liệu Word** một cách lập trình mà không phải đoán mò. Không có tham chiếu bên ngoài, chỉ có một giải pháp tự chứa mà bạn có thể sao chép‑dán vào dự án của mình.

## Yêu cầu trước

- .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.7+)
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Kiến thức cơ bản về cú pháp C#
- Một IDE mà bạn thích (Visual Studio, Rider, VS Code, v.v.)

> **Mẹo chuyên nghiệp:** Nếu bạn đang dùng bản dùng thử miễn phí của Aspose.Words, thư viện sẽ thêm một watermark vào tệp đầu ra. Đối với môi trường production, bạn sẽ cần một giấy phép hợp lệ.

## Bước 1: Khởi tạo Document và Builder

Điều đầu tiên chúng ta làm là tạo một tài liệu Word mới, trống và một `DocumentBuilder` cho phép chúng ta chèn nội dung. Hãy tưởng tượng builder như một cây bút ảo vẽ lên trang.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Tại sao lại quan trọng:** Nếu không có `DocumentBuilder`, bạn sẽ phải thao tác trực tiếp với cây node cấp thấp, điều này dễ gây lỗi và khó đọc hơn.

## Bước 2: Tạo hình chữ nhật

Bây giờ chúng ta thực sự **tạo hình chữ nhật**. Phương thức `InsertShape` nhận một enum `ShapeType`, chiều rộng và chiều cao (đơn vị điểm). Đối tượng `Shape` trả về cho phép chúng ta điều chỉnh các thuộc tính hiển thị sau này.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Tại thời điểm này, hình chữ nhật là một hộp đen đặc được neo vào đoạn văn hiện tại. Bạn có thể di chuyển, thay đổi kích thước, hoặc thậm chí xoay nó sau này nếu cần.

![tạo hình chữ nhật có bóng](/images/rectangle-shadow.png "Tài liệu Word hiển thị một hình chữ nhật với bóng màu xám")

*Văn bản thay thế ảnh: tạo hình chữ nhật có bóng trong tài liệu Word*

## Bước 3: Đặt độ trong suốt cho hình

Độ trong suốt là mức “thấy qua” của phần nền hình. Aspose.Words sử dụng thuộc tính `Transparency` có giá trị từ `0.0` (đục) đến `1.0` (hoàn toàn trong suốt). Ở đây chúng ta **đặt độ trong suốt cho hình** ở mức 40 % để văn bản phía dưới vẫn đọc được```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Trường hợp đặc biệt:** Nếu bạn cần một hình hoàn toàn vô hình nhưng vẫn muốn bóng xuất hiện, hãy đặt `Transparency` thành `1.0` và cho hình một độ rộng viền khác 0.

## Bước 4: Cấu hình bóng

Một bóng mờ nhẹ sẽ tạo độ sâu. Chúng ta sẽ **đặt màu bóng** thành màu xám trung bình, điều chỉnh bán kính mờ và dịch chuyển nó một vài điểm cả theo chiều ngang và chiều dọc.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Tại sao lại quan trọng:** Một bóng quá sắc nét hoặc quá tối có thể trông giống như lỗi in. Điều chỉnh `Blur` và `Transparency` cho đến khi cảm giác tự nhiên.

## Bước 5: Lưu tài liệu Word

Cuối cùng chúng ta **lưu tài liệu Word** vào đĩa. Phương thức `Save` tự động xác định định dạng tệp dựa trên phần mở rộng; `.docx` là định dạng OpenXML hiện đại.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Nếu thư mục không tồn tại, Aspose.Words sẽ ném ra một `ArgumentException`. Hãy chắc chắn đường dẫn hợp lệ hoặc tạo thư mục trước.

## Ví dụ làm việc đầy đủ

Dưới đây là chương trình hoàn chỉnh, sẵn sàng chạy, kết hợp tất cả các bước lại với nhau. Sao chép đoạn này vào một dự án console mới và nhấn **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Kết quả mong đợi

Mở `ShadowRectangle.docx` trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật màu xám nhạt với bóng mềm, hơi lệch, cả hai đều được hiển thị ở mức 40 % trong suốt. Hình nằm trên một trang trống, sẵn sàng cho nội dung bổ sung.

## Câu hỏi thường gặp & Biến thể

**Nếu tôi cần một hình dạng khác?**  
Thay `ShapeType.Rectangle` bằng bất kỳ giá trị enum nào khác (`Ellipse`, `Triangle`, `Star`, v.v.). Phần còn lại của mã vẫn giữ nguyên.

**Tôi có thể thay đổi màu viền không?**  
Có — dùng `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` và tùy chọn đặt `rectangleShape.StrokeWeight = 1.5;`.

**Làm sao đặt hình ở vị trí cụ thể trên trang?**  
Đặt `rectangleShape.WrapType = WrapType.None;` rồi điều chỉnh các thuộc tính `rectangleShape.Left` và `rectangleShape.Top` (giá trị tính bằng điểm).

**Có thể chèn văn bản bên trong hình chữ nhật không?**  
Chắc chắn. Sau khi tạo hình, bạn có thể gọi `rectangleShape.AppendChild(new Paragraph(document))` và sau đó thêm một `Run` chứa văn bản của bạn. Nhớ đặt các thuộc tính `rectangleShape.TextBox` nếu muốn định dạng phong phú hơn.

## Mẹo chuyên nghiệp & Cạm bẫy

- **Cấp giấy phép sớm:** Nếu bạn qu áp dụng giấy phép, Aspose.Words sẽ chèn một watermark trên trang đầu, gây nhầm lẫn trong quá trình thử nghiệm.
- **Mẹo hiệu năng:** Khi tạo nhiều tài liệu trong một vòng lặp, hãy tái sử dụng một đối tượng `Document` duy nhất và gọi `document.RemoveAllChildren();` sau mỗi lần lưu để tránh áp lực GC quá mức.
- **Hiển thị bóng:** Trên màn hình độ phân giải thấp, bóng nhẹ có thể không nhìn thấy. Tăng `Blur` hoặc `OffsetX/Y` để debug, sau đó giảm lại cho môi trường production.

## Bước tiếp theo

Bây giờ bạn đã biết cách **tạo hình chữ nhật**, **đặt độ trong suốt cho hình**, **đặt màu bóng**, và **lưu tài liệu Word**, hãy cân nhắc mở rộng tutorial:

- Thêm nhiều hình và nhóm chúng lại.
- Chèn hình chữ nhật vào ô bảng để tạo bố cục báo cáo.
- Kết hợp hình với `DocumentBuilder.InsertHtml` để phủ nội dung HTML‑styled.
- Khám phá các hiệu ứng hình ảnh khác như `Glow` hoặc `Reflection` để tạo tài liệu giống UI phong phú hơn.

Thử nghiệm, phá vỡ, rồi tinh chỉnh — việc tạo tài liệu lập trình là một sân chơi nơi thiết kế trực quan gặp gỡ code.

---

*Chúc lập trình vui vẻ! Nếu bạn gặp bất kỳ khó khăn nào, hãy để lại bình luận bên dưới và chúng tôi sẽ cùng bạn khắc phục.*  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}