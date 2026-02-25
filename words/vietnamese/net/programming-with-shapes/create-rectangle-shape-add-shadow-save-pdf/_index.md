---
category: general
date: 2026-02-24
description: Tạo hình chữ nhật trong C# bằng Aspose.Words, thêm bóng cho hình và lưu
  tài liệu dưới dạng PDF. Học cách thêm bóng và cách lưu PDF trong vài phút.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: vi
og_description: Tạo hình chữ nhật trong C# bằng Aspose.Words, sau đó thêm bóng cho
  hình và lưu tài liệu dưới dạng PDF – hướng dẫn đầy đủ, từng bước một.
og_title: Tạo hình chữ nhật, thêm bóng và lưu PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Tạo hình chữ nhật, thêm bóng và lưu PDF
url: /vi/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật, thêm bóng đổ & lưu PDF

Bạn đã bao giờ cần **tạo hình chữ nhật** trong tài liệu Word nhưng cũng muốn có một bóng đổ đẹp và xuất ra PDF chưa? Bạn không phải là người duy nhất. Trong nhiều dự án báo cáo hoặc tạo hoá đơn, việc tinh chỉnh hình ảnh—như một bóng đổ nhẹ—làm nên sự khác biệt giữa “chỉ là một tệp nữa” và “tài liệu cấp chuyên nghiệp.”  

Trong tutorial này, chúng ta sẽ đi qua từng bước: sử dụng **Aspose.Words for .NET** để tạo hình chữ nhật, thêm bóng đổ cho hình, và cuối cùng **lưu tài liệu dưới dạng PDF**. Khi hoàn thành, bạn sẽ có một ứng dụng console C# sẵn sàng chạy, tạo ra PDF với một hình chữ nhật có bóng đổ, và bạn sẽ hiểu cách điều chỉnh bóng hoặc thay đổi các tùy chọn xuất.

## Những gì bạn cần

- .NET 6 SDK (hoặc bất kỳ phiên bản .NET gần đây nào) – API hoạt động tương tự trên .NET Framework 4.x.  
- Gói NuGet Aspose.Words for .NET (`Aspose.Words`) – cài đặt bằng `dotnet add package Aspose.Words`.  
- Trình soạn thảo mã nguồn – Visual Studio, VS Code, hoặc Rider đều được.  

Không cần bước cấp phép bổ sung cho ví dụ này; chế độ đánh giá miễn phí đã đủ để xem kết quả PDF.

## Bước 1: Thiết lập dự án và nhập namespace

Đầu tiên, hãy tạo một dự án console và đưa vào các lớp cần thiết.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Lý do quan trọng:* `Document` và `DocumentBuilder` cung cấp “canvas”, trong khi `Shape` và `ShadowFormat` cho phép chúng ta vẽ và tạo kiểu cho hình chữ nhật. Nhập chúng ngay từ đầu giúp mã sau này gọn gàng hơn.

## Bước 2: **Tạo hình chữ nhật** với kích thước mong muốn

Bây giờ chúng ta thực sự tạo một tài liệu trống và chèn một hình chữ nhật. Lưu ý phương thức `InsertShape` trả về một đối tượng `Shape` mà chúng ta có thể ngay lập tức tạo kiểu.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Giải thích*: Kích thước được biểu thị bằng điểm (1 pt = 1/72 in). Điều chỉnh các số để phù hợp với bố cục của bạn. Chúng tôi cũng đặt màu nền xanh nhạt cho hình để bóng đổ nổi bật hơn.

## Bước 3: **Thêm bóng đổ cho hình** – tinh chỉnh hiệu ứng

Bóng đổ không chỉ là “bật/tắt”. Bạn có thể kiểm soát màu, độ mờ, khoảng cách, hướng và thậm chí độ trong suốt. Dưới đây là cấu hình thực tế hoạt động tốt cho hầu hết các báo cáo.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Tại sao bạn có thể muốn thay đổi các giá trị này:*  
- **BlurRadius** – tăng để tạo hiệu ứng mơ hồ, giảm để có cạnh sắc nét.  
- **Direction** – 0° hướng sang phải, 90° xuống, 180° sang trái, v.v. Xoay để phù hợp với bố cục trang.  
- **Transparency** – đặt `0` cho bóng đổ đặc, `0.5` cho nửa trong suốt, v.v.

### Cách thêm bóng đổ – các phương pháp thay thế

Nếu bạn cần **bóng đổ đa lớp** (ví dụ: một bóng đổ ngoài tối hơn cộng với một bóng trong sáng hơn), bạn có thể tạo một hình thứ hai, dịch chuyển nó và đặt một `ShadowFormat` khác. Hoặc, để có hiệu ứng “không mờ” nhanh chóng, đặt `BlurRadius = 0`.

## Bước 4: **Lưu tài liệu dưới dạng PDF** – xuất bản cuối cùng

Với hình chữ nhật và bóng đổ đã sẵn sàng, bước cuối cùng là ghi file ra dạng PDF. Aspose.Words thực hiện chuyển đổi nội bộ; bạn chỉ cần gọi `Save` với định dạng mong muốn.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Mẹo*: Nếu bạn cần kiểm soát tiêu chuẩn PDF (PDF/A, PDF/X) hoặc nhúng phông chữ, hãy sử dụng một overload:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Đó là phần **cách lưu pdf** một cách ngắn gọn.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào `Program.cs`. Nó biên dịch và chạy ngay (chỉ cần đảm bảo thư mục đầu ra tồn tại).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Kết quả mong đợi

Mở file `ShadowRectangle.pdf` vừa tạo. Bạn sẽ thấy một trang duy nhất với hình chữ nhật màu xanh nhạt, bóng đổ màu xám mềm được dịch chuyển 45° xuống‑phải, và các cạnh sạch sẽ. PDF có thể xem được trên bất kỳ trình đọc hiện đại nào (Adobe Acrobat, Edge, Chrome).

![Tạo hình chữ nhật có bóng đổ trong PDF](/images/shadow-rectangle.png "Tạo hình chữ nhật có bóng đổ")

*(Văn bản thay thế hình ảnh bao gồm từ khóa chính cho SEO.)*

## Câu hỏi thường gặp & xử lý các trường hợp đặc biệt

**Nếu bóng đổ không hiển thị trong PDF thì sao?**  
Đảm bảo bạn đang dùng phiên bản Aspose.Words mới (≥23.3). Các bản cũ có lỗi khiến một số thuộc tính bóng đổ bị bỏ qua khi chuyển đổi sang PDF.

**Có thể thay đổi màu bóng đổ để phù hợp với thương hiệu không?**  
Chắc chắn—chỉ cần thay `System.Drawing.Color.Gray` bằng bất kỳ `Color` nào bạn muốn, ví dụ `Color.FromArgb(128, 0, 0, 255)` cho màu xanh bán trong suốt.

**Làm sao thêm bóng đổ cho các hình khác (ellipse, star, …)?**  
`ShadowFormat` hoạt động cho bất kỳ đối tượng `Shape` nào. Sau khi tạo hình, lấy `ShadowFormat` của nó và đặt các thuộc tính.

**Vấn đề DPI hoặc tỷ lệ phóng đại?**  
Việc render PDF tôn trọng kích thước điểm của hình. Nếu bạn cần đầu ra độ phân giải cao hơn (để in), hãy điều chỉnh kích thước hình hoặc đặt `PdfSaveOptions.ImageResolution`.

**Có thể xuất sang các định dạng khác, như PNG không?**  
Có—chỉ cần gọi `document.Save("output.png", SaveFormat.Png)`. Bóng đổ sẽ được render tương tự.

## Mẹo chuyên nghiệp & thực hành tốt

- **Tái sử dụng builder**: Nếu bạn thêm nhiều hình, giữ một thể hiện `DocumentBuilder` duy nhất; việc này rẻ hơn so với tạo nhiều lần.  
- **Lưu hàng loạt**: Khi tạo nhiều PDF trong vòng lặp, tái sử dụng đối tượng `PdfSaveOptions` để tránh việc cấp phát lặp lại.  
- **Kiểm thử**: Luôn mở PDF sau khi lưu để xác nhận bóng đổ xuất hiện như mong đợi. Một số trình đọc PDF có thể render bóng hơi khác; Adobe Acrobat là tham chiếu đáng tin cậy nhất.  
- **Hiệu năng**: Đối với tài liệu lớn, tắt việc tự động ngắt trang của `DocumentBuilder.InsertShape` bằng cách đặt `builder.PageSetup.DifferentFirstPageHeaderFooter = false` nếu bạn không cần tính năng này.

## Kết luận

Chúng ta đã bao quát mọi thứ cần thiết để **tạo hình chữ nhật**, **thêm bóng đổ cho hình**, và **lưu tài liệu dưới dạng PDF** bằng Aspose.Words for .NET. Mã ngắn gọn, khái niệm được giải thích, và bạn giờ đã có nền tảng vững chắc để thử nghiệm với các hình dạng khác, kiểu bóng đổ đa dạng và các tùy chọn xuất.  

Bước tiếp theo? Hãy thử thay hình chữ nhật bằng một hình dạng có góc bo…

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}