---
category: general
date: 2026-03-30
description: Tìm hiểu cách đặt bóng cho một hình dạng trong Word bằng C#. Hướng dẫn
  này cũng chỉ cách thêm bóng cho hình dạng, điều chỉnh độ trong suốt của hình dạng
  và thêm bóng cho hình chữ nhật.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: vi
og_description: Cách đặt bóng cho hình dạng trong Word bằng C#? Hãy làm theo hướng
  dẫn từng bước này để thêm bóng cho hình dạng, điều chỉnh độ trong suốt của hình
  dạng và thêm bóng cho hình chữ nhật.
og_title: Cách Đặt Bóng Cho Hình Dạng Word – Hướng Dẫn C#
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Cách Đặt Bóng cho Hình Dạng trong Word – Hướng Dẫn C#
url: /vi/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Bóng Đổ cho Hình Dạng Word – Hướng Dẫn C#

Bạn đã bao giờ tự hỏi **cách đặt bóng đổ** cho một hình dạng trong tài liệu Word mà không cần thao tác giao diện người dùng chưa? Bạn không phải là người duy nhất. Trong nhiều báo cáo hoặc bản thuyết trình marketing, một bóng đổ nhẹ nhàng làm cho hình chữ nhật nổi bật, và thực hiện nó bằng lập trình giúp tiết kiệm hàng giờ.

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy, không chỉ cho thấy **cách đặt bóng đổ**, mà còn bao gồm **add shape shadow**, **adjust shape transparency**, và thậm chí **add rectangle shadow** cho những hộp chú thích cổ điển. Khi kết thúc, bạn sẽ có một tệp Word (`output.docx`) trông chuyên nghiệp, và bạn sẽ hiểu tại sao mỗi thuộc tính lại quan trọng.

## Yêu Cầu Trước

- .NET 6+ (hoặc .NET Framework 4.7.2) với trình biên dịch C#
- Gói NuGet Aspose.Words cho .NET (`Install-Package Aspose.Words`)
- Kiến thức cơ bản về C# và mô hình đối tượng của Word

Không cần thư viện bổ sung—tất cả đều nằm trong Aspose.Words.

---

## Cách Đặt Bóng Đổ cho Hình Dạng Word trong C#

Dưới đây là tệp nguồn hoàn chỉnh. Lưu nó dưới tên `Program.cs` và chạy từ IDE của bạn hoặc `dotnet run`. Đoạn mã tải một tệp `.docx` hiện có, tìm hình dạng đầu tiên (mặc định là hình chữ nhật), bật bóng đổ, điều chỉnh một vài tham số hiển thị, và lưu kết quả.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Bạn sẽ thấy** – Hình chữ nhật bây giờ có một bóng đổ màu đen với độ trong suốt 30 %, dịch 5 pt sang phải và xuống dưới, với độ mờ nhẹ. Mở `output.docx` trong Word để kiểm tra.

## Điều Chỉnh Độ Trong Suốt của Hình Dạng – Tại Sao Điều Này Quan Trọng

Độ trong suốt không chỉ là một công tắc thẩm mỹ; nó ảnh hưởng đến khả năng đọc. Giá trị 0.0 làm cho bóng đổ hoàn toàn không trong suốt, trong khi 1.0 ẩn nó hoàn toàn. Trong đoạn mã trên, chúng tôi đã sử dụng `0.3` để đạt được hiệu ứng nhẹ nhàng phù hợp với cả nền sáng và tối. Hãy thoải mái thử nghiệm:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Hãy nhớ, **adjust shape transparency** cũng có thể được áp dụng cho màu nền của hình dạng nếu bạn cần một hình chữ nhật bán trong suốt.

## Thêm Bóng Đổ cho Hình Dạng vào Các Đối Tượng Khác

Mã chúng tôi sử dụng nhắm mục tiêu vào đối tượng `Shape`, nhưng các thuộc tính `ShadowFormat` tương tự cũng tồn tại trên các đối tượng **Image**, **Chart**, và thậm chí **TextBox**. Dưới đây là một mẫu nhanh bạn có thể sao chép‑dán:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Vì vậy, dù bạn đang **add shape shadow** cho một logo hay một biểu tượng trang trí, cách tiếp cận vẫn giống nhau.

## Cách Thêm Bóng Đổ cho Bất Kỳ Hình Dạng nào – Các Trường Hợp Cạnh

1. **Shape without a bounding box** – Một số hình dạng Word (như các nét vẽ tự do) không hỗ trợ bóng đổ. Cố gắng đặt `ShadowFormat.Visible` sẽ thất bại một cách im lặng. Kiểm tra `shape.IsShadowSupported` nếu bạn cần an toàn.  
2. **Older Word versions** – Các thuộc tính bóng đổ tương ứng với tính năng của Word 2007+. Nếu bạn phải hỗ trợ Word 2003, bóng đổ sẽ bị bỏ qua khi tệp được mở.  
3. **Multiple shadows** – Aspose.Words hiện chỉ hỗ trợ một bóng đổ cho mỗi hình dạng. Nếu bạn cần hiệu ứng lớp đôi, hãy sao chép hình dạng, dịch chuyển nó, và áp dụng các cài đặt bóng đổ khác nhau.

## Thêm Bóng Đổ cho Hình Chữ Nhật – Trường Hợp Thực Tế

Hãy tưởng tượng bạn đang tạo báo cáo quý và mỗi tiêu đề phần là một hình chữ nhật màu. Thêm **add rectangle shadow** sẽ mang lại cho trang một vẻ “thẻ‑bìa”. Các bước giống hệt ví dụ cơ bản; chỉ cần chắc chắn rằng hình dạng bạn nhắm tới thực sự là một hình chữ nhật (`shape.ShapeType == ShapeType.Rectangle`). Nếu bạn cần tạo hình chữ nhật từ đầu, xem đoạn mã dưới đây:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Chạy toàn bộ chương trình với phần bổ sung này sẽ cho bạn một hình chữ nhật mới đã có hiệu ứng **add rectangle shadow** mong muốn.

---

![Word shape with shadow](placeholder-image.png){alt="cách đặt bóng đổ cho một hình dạng trong Word"}

*Hình: Hình chữ nhật sau khi áp dụng các cài đặt bóng đổ.*

## Tóm Tắt Nhanh (Bảng Điểm Nhanh)

- **Load** tài liệu bằng `new Document(path)`.  
- **Locate** hình dạng qua `doc.GetChild(NodeType.Shape, index, true)`.  
- **Enable** bóng đổ: `shape.ShadowFormat.Visible = true;`.  
- **Set color** với bất kỳ `System.Drawing.Color` nào.  
- **Adjust transparency** (`0.0–1.0`) để kiểm soát độ mờ.  
- **OffsetX / OffsetY** di chuyển bóng đổ theo chiều ngang/dọc (điểm).  
- **BlurRadius** làm mềm cạnh — giá trị cao hơn = bóng đổ mờ hơn.  
- **Save** tệp và mở trong Word để xem kết quả.

## Bạn Có Thể Thử Gì Tiếp Theo?

- **Dynamic colors** – Lấy màu bóng đổ từ một chủ đề hoặc đầu vào của người dùng.  
- **Conditional shadows** – Áp dụng bóng đổ chỉ khi chiều rộng của hình dạng vượt quá một ngưỡng.  
- **Batch processing** – Duyệt qua tất cả các hình dạng trong tài liệu và **add shape shadow** tự động.  

Nếu bạn đã theo dõi, bây giờ bạn đã biết **cách đặt bóng đổ**, cách **adjust shape transparency**, và cách **add rectangle shadow** để có vẻ chuyên nghiệp. Hãy thoải mái thử nghiệm, phá vỡ và sau đó sửa lại—lập trình là người thầy tốt nhất.

*Chúc lập trình vui vẻ! Nếu hướng dẫn này đã giúp bạn, hãy để lại bình luận hoặc chia sẻ các mẹo bóng đổ của bạn. Càng học hỏi lẫn nhau, tài liệu Word của chúng ta càng đẹp mắt.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}