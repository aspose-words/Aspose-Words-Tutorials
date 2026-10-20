---
category: general
date: 2026-03-27
description: Tạo tài liệu Word bằng C# và học cách thêm hình dạng, áp dụng bóng cho
  hình dạng và thiết lập khoảng cách bóng. Hướng dẫn chi tiết từng bước cho Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: vi
og_description: Tạo tài liệu Word bằng C# với hình chữ nhật và bóng tùy chỉnh. Theo
  dõi hướng dẫn đầy đủ này để thiết lập khoảng cách và kiểu bóng.
og_title: Tạo tài liệu Word C# – Thêm hình dạng có bóng
tags:
- Aspose.Words
- C#
- Document Automation
title: Tạo tài liệu Word C# – Thêm hình dạng có bóng
url: /vi/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word C# – Thêm hình dạng có bóng

Bạn đã bao giờ cần **create word document c#** chứa một hình chữ nhật được thiết kế đẹp mắt chưa? Có thể bạn đang xây dựng một mẫu báo cáo và muốn có một bóng đổ nhẹ để làm nổi bật bố cục. Trong hướng dẫn này, chúng ta sẽ đi qua cách thêm hình dạng, áp dụng bóng cho hình dạng, và thậm chí tinh chỉnh khoảng cách bóng bằng Aspose.Words.

Chúng ta sẽ bắt đầu với một tài liệu trống, chèn một hình chữ nhật, áp dụng bóng preset, và cuối cùng lưu file. Khi hoàn thành, bạn sẽ có một file .docx sẵn sàng, mở trong Word và ngay lập tức thấy hiệu ứng. Không cần công cụ bên ngoài, chỉ cần mã C# thuần.

## Yêu cầu trước

- .NET 6 (hoặc bất kỳ .NET Framework hiện đại nào) đã được cài đặt.
- Visual Studio 2022 hoặc VS Code với extension C#.
- Gói NuGet Aspose.Words for .NET (`Aspose.Words` phiên bản 23.12 trở lên).  
  Bạn có thể thêm nó qua Package Manager Console:

  ```powershell
  Install-Package Aspose.Words
  ```

Đó là tất cả – không cần DLL hay COM interop bổ sung.

## Bước 1: Khởi tạo Tài liệu và Builder mới – *create word document c#* Cơ bản

Đầu tiên chúng ta cần một đối tượng `Document` đại diện cho file Word và một `DocumentBuilder` để chỉnh sửa nó.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Tại sao bước này quan trọng:** Lớp `Document` là container cho tất cả các phần của Word (trang, style, hình ảnh). Builder là API cấp cao trừu tượng hoá việc thao tác node cấp thấp, giúp bạn **create word document c#** mà không phải làm việc trực tiếp với XML.

## Bước 2: Chèn hình chữ nhật – *how to create rectangle*  

Bây giờ chúng ta sẽ đặt một hình chữ nhật lên trang. Kích thước được biểu thị bằng điểm (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Mẹo chuyên nghiệp:** Nếu bạn cần một hình dạng khác, chỉ cần thay `ShapeType.Rectangle` bằng `ShapeType.Ellipse`, `ShapeType.Triangle`, v.v. Cùng một đoạn mã hoạt động cho **how to add shape** bất kỳ loại nào.

## Bước 3: Áp dụng bóng preset và tinh chỉnh – *apply shadow to shape*  

Aspose.Words cung cấp một số định dạng bóng preset. Chúng ta sẽ dùng `Preset1` rồi tùy chỉnh khoảng cách, độ mờ, độ trong suốt và màu sắc.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Tại sao cần tùy chỉnh bóng?** Thuộc tính `Distance` điều khiển khoảng cách bóng so với hình chữ nhật – giống như “độ nâng” trong render 3‑D. Thay đổi `BlurRadius` làm mềm các cạnh, trong khi `Transparency` cho phép tạo một vẻ ngoài tinh tế, chuyên nghiệp. Điều này đáp ứng yêu cầu **set shadow distance** và cho bạn thấy cách **apply shadow to shape** một cách linh hoạt.

## Bước 4: Lưu tài liệu – *create word document c#* Hoàn tất

Cuối cùng, ghi tài liệu ra đĩa. Điều chỉnh đường dẫn tới thư mục bạn có quyền ghi.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Mở file kết quả trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu xanh nhạt với bóng xám mềm được dịch chuyển 5 pt. Đó là bằng chứng trực quan rằng bạn đã **create word document c#** thành công với một hình dạng được thiết kế.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="create word document c# example showing rectangle with shadow"}

## Các biến thể tùy chọn & Trường hợp đặc biệt

| Kịch bản | Cần thay đổi | Tại sao quan trọng |
|----------|--------------|--------------------|
| **Phong cách bóng khác** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Mang lại vẻ ngoài ấn tượng hơn mà không cần thêm mã. |
| **Không dùng preset – bóng tùy chỉnh** | Bỏ `Format` và đặt `OffsetX`, `OffsetY` thủ công. | Kiểm soát hoàn toàn hướng và độ sâu. |
| **Nhiều hình dạng** | Gọi `builder.InsertShape` lại trước khi lưu. | Hữu ích cho các mẫu phức tạp có biểu tượng, logo, v.v. |
| **Tương thích với phiên bản Aspose cũ** | Sử dụng lớp `ShadowEffect` (có trong v20.x). | Đảm bảo mã chạy trên các dự án legacy. |
| **Lưu dưới dạng PDF** | `document.Save("ShadowShape.pdf");` | Bóng sẽ được render tương tự trong file PDF. |

> **Câu hỏi thường gặp:** *Nếu bóng không xuất hiện trong Word thì sao?*  
> Đảm bảo bạn đang dùng phiên bản Aspose.Words mới (≥ 22.9). Các phiên bản cũ hơn có hỗ trợ bóng hạn chế. Ngoài ra, kiểm tra rằng tài liệu được mở bằng phiên bản Word mới (2016+).

## Ví dụ Hoàn chỉnh

Dưới đây là chương trình đầy đủ, sẵn sàng sao chép‑dán. Bao gồm tất cả các `using` directive, chú thích, và xử lý lỗi để trải nghiệm mượt mà.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Chạy chương trình, điều hướng tới `C:\Temp\ShadowShape.docx`, và bạn sẽ thấy hình chữ nhật với bóng chính xác như đã cấu hình.

## Tóm tắt & Các bước tiếp theo

- Giờ bạn đã biết cách **create word document c#**, chèn hình chữ nhật, và **apply shadow to shape** với **set shadow distance** tùy chỉnh.  
- Ví dụ sử dụng Aspose.Words, giúp trừu tượng hoá các phức tạp của OpenXML và đảm bảo render nhất quán trên các phiên bản Word.  
- Muốn tiến xa hơn? Hãy thử kết hợp nhiều hình dạng, thêm văn bản vào trong hình chữ nhật, hoặc xuất cùng tài liệu dưới dạng PDF để xem bóng được chuyển đổi như thế nào.

### Các chủ đề liên quan bạn có thể khám phá

- **How to add shape** vào header/footer để branding.  
- Sử dụng **Aspose.Words** để chèn biểu đồ và bảng một cách lập trình.  
- Tùy chỉnh **shadow effects** trên ảnh thay vì hình vector.  
- Tự động tạo hàng loạt tài liệu cho hoá đơn hoặc chứng chỉ.

Hãy thoải mái thử nghiệm, phá vỡ mã, rồi xây dựng lại – đó là cách nhanh nhất để nắm vững các khái niệm. Nếu gặp khó khăn, để lại bình luận bên dưới hoặc tham khảo tài liệu chính thức của Aspose.Words để hiểu sâu hơn về API.

Chúc lập trình vui vẻ, và chúc các file Word của bạn trở nên tinh tế hơn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}