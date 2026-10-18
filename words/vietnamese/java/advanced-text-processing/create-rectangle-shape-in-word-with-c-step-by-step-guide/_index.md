---
category: general
date: 2026-03-04
description: Học cách tạo hình chữ nhật, thêm bóng cho hình và áp dụng hiệu ứng bóng
  trong tài liệu Word, sau đó tự động lưu tài liệu Word.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- save word document
- create blank document
language: vi
og_description: Create rectangle shape, add shadow to shape and apply shadow effect
  in a Word document using C#. Follow this guide to save Word document effortlessly.
og_title: Create rectangle shape in Word – Complete C# Tutorial
tags:
- C#
- Aspose.Words
- Document Automation
title: Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước
url: /vi/java/advanced-text-processing/create-rectangle-shape-in-word-with-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn lập trình đầy đủ

Bạn đã bao giờ cần **tạo hình chữ nhật** trong một tệp Word nhưng không biết bắt đầu từ đâu? Bạn không đơn độc—nhiều nhà phát triển gặp khó khăn này khi lần đầu tiếp cận việc tạo tài liệu bằng mã. Tin tốt là chỉ với vài dòng C# bạn có thể chèn một hình chữ nhật, **thêm bóng cho hình**, và **áp dụng hiệu ứng bóng** mà không cần mở Word. Trong hướng dẫn này, chúng tôi sẽ đi qua toàn bộ quy trình, từ **tạo tài liệu trống** mới đến **lưu tài liệu Word** cuối cùng lên đĩa.

Chúng tôi sẽ bao phủ mọi thứ bạn cần: gói NuGet cần thiết, các API chính xác, lý do mỗi thuộc tính quan trọng, và một vài mẹo để tránh những lỗi thường gặp. Khi hoàn thành, bạn sẽ có một ví dụ chạy được mà có thể chèn vào bất kỳ dự án .NET nào.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
- Visual Studio 2022 hoặc bất kỳ IDE nào bạn thích
- **Aspose.Words for .NET** được cài đặt qua NuGet (`Install-Package Aspose.Words`)
- Kiến thức cơ bản về cú pháp C#

Không cần thêm bất kỳ thư viện interop Word nào—Aspose.Words xử lý mọi thứ trong bộ nhớ.

## Bước 1 – Tạo tài liệu trống

Điều đầu tiên chúng ta làm là **tạo tài liệu trống**. Hãy nghĩ đây là canvas rỗng mà sau này chúng ta sẽ **tạo hình chữ nhật** lên trên.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Initialize a new blank document
Document doc = new Document();   // This gives us a fresh Word file
```

> **Tại sao điều này quan trọng:** Bắt đầu với một đối tượng `Document` sạch sẽ đảm bảo không có kiểu dáng hay phần nào ẩn can thiệp vào vị trí của hình sau này.

## Bước 2 – Chèn hình chữ nhật vào tài liệu

Bây giờ chúng ta thực sự **tạo hình chữ nhật**. Chúng ta sẽ đặt kích thước, vị trí, và chỉ định cho Word không bao bọc văn bản quanh nó.

```csharp
// Step 2: Add a rectangle shape
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 200;          // Width in points (1 point = 1/72 inch)
rectangle.Height = 100;         // Height in points
rectangle.WrapType = WrapType.None; // No text wrapping
```

> **Mẹo chuyên nghiệp:** Nếu bạn cần hình chữ nhật nằm trong một ô bảng, thay đổi `WrapType` thành `WrapType.Inline`. Đối với hầu hết các báo cáo, `None` giữ hình nổi trên văn bản.

## Bước 3 – Thêm bóng cho hình và cấu hình hiển thị

Đây là phần “ma thuật”: chúng ta **thêm bóng cho hình** và **áp dụng hiệu ứng bóng**. Bóng giúp hình chữ nhật nổi bật trên trang, đặc biệt khi in.

```csharp
// Step 3: Enable shadow and set its properties
rectangle.ShadowFormat.Visible = true;          // Turn on the shadow
rectangle.ShadowFormat.BlurRadius = 5.0;        // Softness of the shadow edge
rectangle.ShadowFormat.Transparency = 0.3;      // 30 % transparent
rectangle.ShadowFormat.OffsetX = 8;             // Horizontal shift
rectangle.ShadowFormat.OffsetY = 8;             // Vertical shift
rectangle.ShadowFormat.Color = Color.Blue;     // Shadow colour
```

> **Tại sao lại dùng các giá trị này?**  
> - **BlurRadius** kiểm soát độ mờ của các cạnh; giá trị khoảng `5` tạo cảm giác tinh tế, chuyên nghiệp.  
> - **Transparency** cho phép văn bản phía dưới vẫn đọc được.  
> - **OffsetX/Y** di chuyển bóng ra xa hình, tạo độ sâu.  
> - Sử dụng màu **xanh dương** chỉ là ví dụ—bất kỳ `System.Drawing.Color` nào cũng được.

## Bước 4 – Thêm hình đã cấu hình vào phần thân tài liệu

Với hình chữ nhật đã được định dạng hoàn chỉnh, chúng ta **thêm hình chữ nhật** vào phần đầu tiên của tài liệu. Bước này thực sự đặt hình vào file.

```csharp
// Step 4: Append the shape to the first section's body
doc.FirstSection.Body.AppendChild(rectangle);
```

> **Trường hợp đặc biệt:** Nếu tài liệu của bạn đã có nhiều phần, bạn có thể muốn nhắm tới một phần cụ thể (`doc.Sections[2]` chẳng hạn). Đoạn mã trên hoạt động cho tài liệu một phần, thường gặp trong các báo cáo nhanh.

## Bước 5 – Lưu tài liệu Word

Cuối cùng, chúng ta **lưu tài liệu Word** lên đĩa. Tệp sẽ chứa hình chữ nhật cùng bóng, sẵn sàng mở trong Microsoft Word.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\shadowed_rectangle.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Mẹo:** Dùng `doc.Save(outputPath, SaveFormat.Docx)` nếu bạn muốn chỉ định rõ định dạng. Phương thức `Save` tự động phát hiện phần mở rộng, nhưng việc chỉ định rõ ràng có thể tránh nhầm lẫn khi đường dẫn được tạo bằng mã.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các câu lệnh `using` và phương thức `Main`, vì vậy bạn có thể chạy ngay lập tức.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document
            Document doc = new Document();

            // 2️⃣ Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 200;
            rectangle.Height = 100;
            rectangle.WrapType = WrapType.None;

            // 3️⃣ Apply shadow effect
            rectangle.ShadowFormat.Visible = true;
            rectangle.ShadowFormat.BlurRadius = 5.0;
            rectangle.ShadowFormat.Transparency = 0.3;
            rectangle.ShadowFormat.OffsetX = 8;
            rectangle.ShadowFormat.OffsetY = 8;
            rectangle.ShadowFormat.Color = Color.Blue;

            // 4️⃣ Insert the shape into the document body
            doc.FirstSection.Body.AppendChild(rectangle);

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\shadowed_rectangle.docx";
            doc.Save(outputPath);
            Console.WriteLine($"✅ Document saved at {outputPath}");
        }
    }
}
```

### Kết quả mong đợi

Khi mở *shadowed_rectangle.docx* trong Microsoft Word, bạn sẽ thấy một hình chữ nhật viền xanh nổi gần đầu trang đầu tiên, với bóng xanh nhạt được dịch sang phải và xuống dưới 8 pt. Không có văn bản nào bao quanh vì chúng ta đã đặt `WrapType.None`.

## Câu hỏi thường gặp & Biến thể

| Câu hỏi | Trả lời |
|----------|--------|
| **Tôi có thể đổi hình thành ellipse không?** | Có—thay `ShapeType.Rectangle` bằng `ShapeType.Ellipse`. Tất cả các thuộc tính bóng vẫn giữ nguyên. |
| **Nếu tôi cần nhiều hình thì sao?** | Chỉ cần lặp lại Các bước 2‑4 cho mỗi đối tượng `Shape` mới, điều chỉnh `OffsetX/Y` hoặc `Left/Top` để tránh chồng lấn. |
| **Có cách làm cho màu bóng khớp với màu nền của hình không?** | Chắc chắn. Đặt `rectangle.FillColor` trước, sau đó gán `rectangle.ShadowFormat.Color = rectangle.FillColor;`. |
| **Làm sao chèn hình vào ô bảng?** | Dùng `cell.FirstParagraph.AppendChild(rectangle);` sau khi đã lấy được đối tượng `Cell` mong muốn. |
| **Điều này có hoạt động trên .NET Core không?** | Có—Aspose.Words hỗ trợ đa nền tảng. Chỉ cần chắc chắn bạn tham chiếu đúng phiên bản NuGet cho .NET Core/5/6. |

## Những lỗi thường gặp & Mẹo chuyên nghiệp

- **Lỗi:** Quên đặt `ShadowFormat.Visible = true`. Các thuộc tính bóng sẽ bị bỏ qua một cách im lặng.  
  **Cách khắc phục:** Luôn bật tính năng hiển thị trước khi tinh chỉnh các tham số bóng khác.

- **Lỗi:** Dùng `BlurRadius` quá lớn (ví dụ 20) khiến bóng trông mờ và không chuyên nghiệp.  
  **Cách khắc phục:** Giữ giá trị trong khoảng `3`‑`8` cho hầu hết các tài liệu doanh nghiệp.

- **Mẹo:** Nếu bạn muốn hình có thể được chọn sau này (ví dụ để người dùng cuối chỉnh sửa), tránh đặt `WrapType.Inline`. Các hình nổi (`WrapType.None`) dễ di chuyển bằng mã hơn.

- **Mẹo:** Khi tạo nhiều tài liệu trong một vòng lặp, tái sử dụng một đối tượng `Document` duy nhất và gọi `doc.Clone(true)` cho mỗi lần lặp để cải thiện hiệu năng.

## Các chủ đề liên quan bạn có thể khám phá tiếp

- **Thêm văn bản vào hình chữ nhật** – học cách dùng `Shape.TextPath` cho nhãn.  
- **Tạo sơ đồ phức tạp** – kết hợp nhiều hình, kết nối và nhóm lại.  
- **Xuất ra PDF** – chuyển đổi cùng tài liệu sang PDF chỉ bằng một lệnh `doc.Save("output.pdf")`.  
- **Áp dụng các kiểu nền khác nhau** – gradient, texture, hoặc thậm chí hình ảnh bên trong các hình.

## Kết luận

Chúng ta vừa **tạo hình chữ nhật**, **thêm bóng cho hình**, và **áp dụng hiệu ứng bóng** trong một tệp Word bằng C#. Bằng cách làm theo năm bước ngắn gọn, bạn đã có một mẫu có thể tái sử dụng cho bất kỳ kịch bản tự động hoá tài liệu nào, và bạn biết cách **lưu tài liệu Word** một cách đáng tin cậy. Hãy thoải mái điều chỉnh kích thước, màu sắc, hoặc thậm chí thay hình chữ nhật bằng hình dạng khác—Aspose.Words làm cho mọi thứ trở nên đơn giản.

Nếu bạn thấy hướng dẫn này hữu ích, hãy cho nó một ngôi sao trên GitHub, hoặc chia sẻ các biến thể của bạn trong phần bình luận. Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn trông thật chuyên nghiệp như hình chữ nhật có bóng này!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}