---
category: general
date: 2025-12-08
description: Thêm bóng cho hình dạng nhanh chóng với Aspose.Words. Tìm hiểu cách tạo
  tài liệu Word bằng Aspose, cách thêm bóng cho hình dạng và áp dụng độ trong suốt
  của bóng trong C#.
draft: false
keywords:
- add shadow to shape
- create word document using aspose
- how to add shape shadow
- apply shadow transparency
language: vi
og_description: Thêm bóng cho hình dạng trong tệp Word bằng Aspose.Words. Hướng dẫn
  từng bước này cho thấy cách tạo tài liệu, thêm hình dạng và áp dụng độ trong suốt
  của bóng.
og_title: Thêm bóng cho hình dạng – Hướng dẫn Aspose.Words C#
tags:
- Aspose.Words
- C#
- Word Automation
title: Thêm bóng cho hình dạng trong tài liệu Word – Hướng dẫn đầy đủ Aspose.Words
url: /vietnamese/net/images-and-shapes/add-shadow-to-shape-in-a-word-document-complete-aspose-words/
---

{{< layout-start >}}

{{< layout-start >}}

# Thêm Bóng Đổ cho Hình – Hướng Dẫn Toàn Diện Aspose.Words

Bạn đã bao giờ cần **thêm bóng đổ cho hình** trong một tệp Word nhưng không chắc nên sử dụng API nào không? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi lần đầu cố gắng tạo bóng đổ cho một hình chữ nhật hoặc bất kỳ phần tử vẽ nào, đặc biệt khi họ làm việc với Aspose.Words cho .NET.

Trong tutorial này, chúng ta sẽ đi qua mọi thứ bạn cần biết: từ **tạo tài liệu Word bằng Aspose** đến việc cấu hình bóng, điều chỉnh độ mờ, khoảng cách, góc, và thậm chí **áp dụng độ trong suốt cho bóng**. Khi kết thúc, bạn sẽ có một chương trình C# sẵn sàng chạy, tạo ra tệp `.docx` với một hình chữ nhật được tô bóng đẹp mắt—không cần can thiệp thủ công trong Word.

---

## Những Điều Bạn Sẽ Học

- Cách thiết lập dự án Aspose.Words trong Visual Studio.  
- Các bước chính để **tạo tài liệu Word bằng Aspose** và chèn một hình.  
- **Cách thêm bóng cho hình** với kiểm soát đầy đủ về độ mờ, khoảng cách, góc và độ trong suốt.  
- Mẹo khắc phục các vấn đề thường gặp (ví dụ: thiếu giấy phép, đơn vị không đúng).  
- Một mẫu mã hoàn chỉnh, sao chép‑dán mà bạn có thể chạy ngay hôm nay.

> **Yêu cầu trước:** .NET 6+ (hoặc .NET Framework 4.7.2+), một giấy phép Aspose.Words hợp lệ (hoặc bản dùng thử miễn phí), và kiến thức cơ bản về C#.

---

## Bước 1 – Thiết Lập Dự Án và Thêm Aspose.Words

Đầu tiên, mở Visual Studio, tạo một **Console App (.NET Core)** mới, và thêm gói NuGet Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Nếu bạn có tệp giấy phép (`Aspose.Words.lic`), sao chép nó vào thư mục gốc của dự án và tải nó khi khởi động. Điều này sẽ loại bỏ dấu watermark xuất hiện trong chế độ đánh giá miễn phí.

```csharp
// Load the license (optional but recommended)
var license = new Aspose.Words.License();
license.SetLicense("Aspose.Words.lic");
```

---

## Bước 2 – Tạo Tài Liệu Trống Mới

Bây giờ chúng ta thực sự **tạo tài liệu Word bằng Aspose**. Đối tượng này sẽ làm nền cho hình của chúng ta.

```csharp
// Step 2: Initialize a new blank document
Document doc = new Document();   // Represents an empty .docx file
```

Lớp `Document` là điểm khởi đầu cho mọi thứ khác—đoạn văn, phần, và dĩ nhiên, các đối tượng vẽ.

---

## Bước 3 – Chèn Hình Chữ Nhật

Với tài liệu đã sẵn sàng, chúng ta có thể thêm một hình. Ở đây chúng ta chọn một hình chữ nhật đơn giản, nhưng logic tương tự áp dụng cho vòng tròn, đường thẳng, hoặc đa giác tùy chỉnh.

```csharp
// Step 3: Create a rectangular shape that will hold the shadow
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 150,   // Width in points (1 point = 1/72 inch)
    Height = 100    // Height in points
};
```

> **Tại sao lại là hình?** Trong Aspose.Words, một đối tượng `Shape` có thể chứa văn bản, hình ảnh, hoặc chỉ đơn giản là một yếu tố trang trí. Thêm bóng cho một hình dễ dàng hơn rất nhiều so với việc thao tác khung ảnh.

---

## Bước 4 – Cấu Hình Bóng Đổ (Thêm Bóng Đổ cho Hình)

Đây là phần cốt lõi của tutorial—**cách thêm bóng cho hình** và tinh chỉnh ngoại hình của nó. Thuộc tính `ShadowFormat` cho bạn toàn quyền kiểm soát.

```csharp
// Step 4: Enable the shadow and configure its appearance
rectangle.ShadowFormat.Visible       = true;   // Turn the shadow on
rectangle.ShadowFormat.Blur          = 5.0;    // Blur radius – higher = softer edges
rectangle.ShadowFormat.Distance      = 3.0;    // Offset distance from the shape
rectangle.ShadowFormat.Angle         = 45;     // Direction in degrees (0 = right, 90 = down)
rectangle.ShadowFormat.Transparency  = 0.3;    // 30 % transparent – this is how we **apply shadow transparency**
```

### Mô Tả Mỗi Thuộc Tính

| Thuộc tính | Hiệu ứng | Giá trị Điển Hình |
|------------|----------|-------------------|
| **Visible** | Bật/tắt bóng. | `true` / `false` |
| **Blur** | Làm mềm các cạnh bóng. | `0` (cứng) đến `10` (rất mềm) |
| **Distance** | Đẩy bóng ra xa hình. | `1`–`5` points là phổ biến |
| **Angle** | Điều khiển hướng offset. | `0`–`360` độ |
| **Transparency** | Làm bóng trong suốt một phần. | `0` (đục) đến `1` (vô hình) |

> **Trường hợp đặc biệt:** Nếu bạn đặt `Transparency` thành `1`, bóng sẽ biến mất hoàn toàn—hữu ích khi muốn bật/tắt bóng bằng chương trình.

---

## Bước 5 – Thêm Hình Vào Tài Liệu

Bây giờ chúng ta gắn hình vào đoạn văn đầu tiên của phần thân tài liệu. Aspose sẽ tự động tạo một đoạn văn nếu chưa có.

```csharp
// Step 5: Append the shape to the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);
```

Nếu tài liệu của bạn đã có nội dung, bạn có thể chèn hình vào bất kỳ node nào bằng `InsertAfter` hoặc `InsertBefore`.

---

## Bước 6 – Lưu Tài Liệu

Cuối cùng, ghi tệp ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.pdf`, `.odt`, …), nhưng trong tutorial này chúng ta sẽ dùng định dạng Word gốc.

```csharp
// Step 6: Save the document with the shadowed shape
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Mở `ShadowedShape.docx` vừa tạo trong Microsoft Word, và bạn sẽ thấy một hình chữ nhật với bóng mềm, góc 45 độ, trong suốt 30 %—đúng như chúng ta đã cấu hình.

---

## Ví Dụ Hoàn Chỉnh

Dưới đây là chương trình **đầy đủ, sao chép‑dán ngay** tích hợp tất cả các bước trên. Lưu lại dưới tên `Program.cs` và chạy bằng `dotnet run`.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // OPTIONAL: Load Aspose.Words license (remove if using trial)
        // -------------------------------------------------
        try
        {
            var license = new License();
            license.SetLicense("Aspose.Words.lic");
        }
        catch (Exception ex)
        {
            Console.WriteLine("License not found – running in evaluation mode: " + ex.Message);
        }

        // -------------------------------------------------
        // 1. Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // 2. Insert a rectangle shape
        // -------------------------------------------------
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 150,
            Height = 100
        };

        // -------------------------------------------------
        // 3. Configure the shadow – this is where we **add shadow to shape**
        // -------------------------------------------------
        rectangle.ShadowFormat.Visible      = true;   // Show the shadow
        rectangle.ShadowFormat.Blur         = 5.0;    // Soft edges
        rectangle.ShadowFormat.Distance     = 3.0;    // Offset distance
        rectangle.ShadowFormat.Angle        = 45;     // Direction in degrees
        rectangle.ShadowFormat.Transparency = 0.3;    // 30 % transparent (apply shadow transparency)

        // -------------------------------------------------
        // 4. Add the shape to the document
        // -------------------------------------------------
        doc.FirstSection.Body.FirstParagraph.AppendChild(rectangle);

        // -------------------------------------------------
        // 5. Save the file
        // -------------------------------------------------
        string outFile = Path.Combine(Environment.CurrentDirectory, "ShadowedShape.docx");
        doc.Save(outFile);
        Console.WriteLine($"Document created successfully: {outFile}");
    }
}
```

**Kết quả mong đợi:** Một tệp có tên `ShadowedShape.docx` chứa một hình chữ nhật duy nhất với bóng nhẹ, bán trong suốt, nghiêng 45°.

---

## Biến Thể & Mẹo Nâng Cao

### Thay Đổi Màu Bóng Đổ

Mặc định bóng sẽ kế thừa màu nền của hình, nhưng bạn có thể đặt màu tùy chỉnh:

```csharp
rectangle.ShadowFormat.Color = System.Drawing.Color.Gray;
```

### Nhiều Hình với Bóng Đổ Khác Nhau

Nếu cần nhiều hình, chỉ cần lặp lại các bước tạo và cấu hình. Đừng quên đặt tên duy nhất cho mỗi hình nếu bạn dự định tham chiếu chúng sau này.

### Xuất ra PDF với Bóng Đổ Được Bảo Tồn

Aspose.Words giữ nguyên hiệu ứng bóng khi lưu ra PDF:

```csharp
doc.Save("ShadowedShape.pdf");
```

### Những Cạm Bẫy Thường Gặp

| Triệu chứng | Nguyên Nhân Thường Gặp | Cách Khắc Phục |
|-------------|------------------------|----------------|
| Bóng không hiển thị | `ShadowFormat.Visible` để `false` | Đặt thành `true`. |
| Bóng quá cứng | `Blur` bằng `0` | Tăng `Blur` lên 3–6. |
| Bóng biến mất trong PDF | Dùng phiên bản Aspose.Words cũ (< 22.9) | Nâng cấp lên thư viện mới nhất. |

---

## Kết Luận

Chúng ta đã bao quát **cách thêm bóng đổ cho hình** bằng Aspose.Words, từ khởi tạo tài liệu đến tinh chỉnh độ mờ, khoảng cách, góc và **áp dụng độ trong suốt cho bóng**. Ví dụ đầy đủ minh họa một cách tiếp cận sạch sẽ, sẵn sàng cho môi trường sản xuất mà bạn có thể điều chỉnh cho bất kỳ hình hay bố cục tài liệu nào.

Có câu hỏi về **tạo tài liệu Word bằng Aspose** cho các kịch bản phức tạp hơn—như bảng có bóng hoặc hình động dựa trên dữ liệu? Hãy để lại bình luận bên dưới hoặc xem các tutorial liên quan về xử lý ảnh và định dạng đoạn văn trong Aspose.Words.

Chúc lập trình vui vẻ, và tận hưởng việc mang lại cho tài liệu Word của bạn một lớp hoàn thiện trực quan hơn! 

--- 

![ví dụ thêm bóng đổ cho hình](shadowed_shape.png "add shadow to shape example")

{{< layout-end >}}

{{< layout-end >}}