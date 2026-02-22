---
category: general
date: 2026-02-21
description: Thêm bóng cho hình dạng trong C# và tìm hiểu cách tùy chỉnh bóng, áp
  dụng hiệu ứng bóng, và thiết lập độ trong suốt của bóng với một ví dụ đầy đủ, có
  thể chạy được.
draft: false
keywords:
- add shadow to shape
- how to customize shadow
- apply shadow effect
- how to add shadow
- set shadow opacity
language: vi
og_description: Thêm bóng cho hình dạng trong C# với hướng dẫn này. Tìm hiểu cách
  tùy chỉnh bóng, áp dụng hiệu ứng bóng và thiết lập độ trong suốt của bóng chỉ trong
  vài dòng mã.
og_title: Thêm Bóng Đổ cho Hình – Hướng Dẫn C# Toàn Diện
tags:
- C#
- Aspose.Words
- Graphics
- Shadow Effect
title: Thêm bóng cho hình dạng – Hướng dẫn từng bước cho các nhà phát triển C#
url: /vi/net/programming-with-shapes/add-shadow-to-shape-step-by-step-guide-for-c-developers/
---

All preserved.

Make sure to keep markdown formatting.

Let's produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm Bóng Đổ cho Hình – Hướng Dẫn C# Đầy Đủ

Bạn đã bao giờ cần **thêm bóng đổ cho hình** trong một tài liệu Word nhưng không biết bắt đầu từ đâu chưa? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn này khi hoàn thiện báo cáo hoặc tờ rơi marketing. Tin tốt là gì? Chỉ trong vài bước, bạn có thể biến một hình chữ nhật phẳng thành một yếu tố ba‑chiều được đánh bóng, nổi bật trên trang.

Trong hướng dẫn này, chúng tôi sẽ đi qua một **ví dụ đầy đủ, có thể chạy được** cho thấy cách tùy chỉnh bóng, áp dụng hiệu ứng bóng, và thậm chí đặt độ mờ của bóng cho bất kỳ hình nào. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng, có thể chèn vào bất kỳ dự án Aspose.Words nào, không cần tham chiếu bí ẩn.

## Yêu Cầu Trước

* **.NET 6.0** (hoặc mới hơn) đã được cài đặt – mã này cũng hoạt động với .NET Framework 4.6+.
* **Aspose.Words for .NET** package NuGet – nên dùng phiên bản 23.9 hoặc mới hơn.
* Kiến thức cơ bản về C# và lập trình hướng đối tượng.

Nếu bạn chưa có package NuGet, chạy:

```bash
dotnet add package Aspose.Words
```

Bây giờ nền tảng đã sẵn sàng, hãy bắt tay vào thực hành.

## Bước 1 – Tải hoặc Tạo một Tài liệu và Lấy Hình Đầu Tiên

Điều đầu tiên chúng ta cần là một đối tượng `Document` thực sự chứa một hình. Để minh họa, chúng ta sẽ tạo một tài liệu mới, chèn một hình chữ nhật đơn giản, và sau đó lấy nó.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank document
        Document doc = new Document();

        // 2️⃣ Add a new shape (a rectangle) to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;

        // Insert the shape into the document body
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Retrieve the shape we just added (demonstrates add shadow to shape)
        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // The remaining steps modify the shadow of firstShape
```

**Tại sao chúng ta làm như vậy:**  
Lấy hình bằng `GetChild` mô phỏng các tình huống thực tế nơi hình đã tồn tại (ví dụ, được tải từ một mẫu). Nó cũng đảm bảo rằng mã bóng tiếp theo hoạt động trên một đối tượng hợp lệ, tránh ngoại lệ tham chiếu null.

> **Mẹo chuyên nghiệp:** Nếu bạn làm việc với nhiều hình, hãy dùng `GetChild(NodeType.Shape, index, true)` hoặc lặp qua `doc.GetChildNodes(NodeType.Shape, true)`.

## Bước 2 – Bật Hiệu Ứng Bóng

Bóng của một hình mặc định bị tắt. Bật nó là điều kiện tiên quyết đầu tiên để tùy chỉnh thêm.

```csharp
        // 4️⃣ Enable the shadow
        firstShape.Shadow.Enabled = true;
```

**Tại sao điều này quan trọng:**  
Nếu không đặt `Enabled = true`, bất kỳ thay đổi thuộc tính nào sau này (màu, độ mờ, độ dịch) sẽ bị bỏ qua. Hãy nghĩ như việc bật công tắc đèn trước khi bạn có thể điều chỉnh độ sáng của đèn.

## Bước 3 – Chọn Màu Bóng (và Tại Sao Đen Là Điểm Bắt Đầu Tốt)

Lựa chọn màu sắc ảnh hưởng mạnh mẽ đến độ sâu cảm nhận. Đen (hoặc xám rất tối) là màu phổ biến nhất vì nó hoạt động trên mọi nền.

```csharp
        // 5️⃣ Set the shadow color – black gives a classic look
        firstShape.Shadow.Color = Color.Black;
```

**Thay thế:**  
Nếu tài liệu của bạn có nền tối, hãy thử một tông màu sáng hơn:

```csharp
        // firstShape.Shadow.Color = Color.FromArgb(150, 150, 150); // light gray
```

## Bước 4 – Đặt Độ Mờ Của Bóng (Set Shadow Opacity)

Độ mờ được biểu thị bằng giá trị từ `0.0` (hoàn toàn trong suốt) đến `1.0` (đầy đủ không trong suốt). Một bóng có độ trong suốt 40 % cảm giác tự nhiên cho hầu hết các thiết kế UI.

```csharp
        // 6️⃣ Make the shadow 40 % transparent
        firstShape.Shadow.Transparency = 0.4; // 0 = opaque, 1 = invisible
```

**Cách tùy chỉnh:**  
- **Nhẹ hơn:** `0.2` (20 % trong suốt)  
- **Rất mờ:** `0.7` (70 % trong suốt)

## Bước 5 – Định Nghĩa Độ Mờ và Độ Mềm Cạnh

Độ mờ kiểm soát độ mềm của các cạnh bóng. Giá trị `4.0` hoạt động tốt cho các hình có kích thước trung bình.

```csharp
        // 7️⃣ Soften the edges with a blur radius
        firstShape.Shadow.Blur = 4.0;
```

**Trường hợp đặc biệt:**  
Nếu bạn đặt `Blur` thành `0`, bóng sẽ trở thành một hình bóng có cạnh cứng, có thể trông gắt gao. Ngược lại, giá trị trên `10` có thể làm bóng trông như một ánh sáng halo.

## Bước 6 – Định Vị Bóng So Với Hình

Các giá trị offset dịch bóng theo chiều ngang (`OffsetX`) và chiều dọc (`OffsetY`). Số dương di chuyển bóng xuống và sang phải.

```csharp
        // 8️⃣ Position the shadow 5 points right and 5 points down
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;
```

**Thử nghiệm:**  
- **Bóng thả:** `OffsetX = 0`, `OffsetY = 10`  
- **Hiệu ứng nâng lên:** `OffsetX = -5`, `OffsetY = -5`

## Bước 7 – Lưu và Kiểm Tra Kết Quả

Cuối cùng, ghi tài liệu ra đĩa và mở nó trong Microsoft Word (hoặc bất kỳ trình xem tương thích nào) để xem bóng hoạt động.

```csharp
        // 9️⃣ Save the document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

Khi bạn mở **ShadowedShape.docx**, bạn sẽ thấy một hình chữ nhật màu xanh nhạt với bóng đen mềm, bán trong suốt, dịch sang năm điểm. Nếu bóng không xuất hiện, hãy kiểm tra lại rằng `firstShape.Shadow.Enabled` là `true` và bạn đang sử dụng phiên bản mới của Aspose.Words.

### Mã Nguồn Đầy Đủ (Sẵn Sàng Sao Chép‑Dán)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        Document doc = new Document();
        Shape rect = new Shape(doc, ShapeType.Rectangle);
        rect.Width = 150;
        rect.Height = 100;
        rect.WrapType = WrapType.Inline;
        rect.StrokeColor = Color.DarkBlue;
        rect.FillColor = Color.LightBlue;
        rect.StrokeWeight = 2.0;
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        Shape firstShape = doc.GetChild(NodeType.Shape, 0, true) as Shape;
        if (firstShape == null)
        {
            Console.WriteLine("No shape found – aborting.");
            return;
        }

        // Enable shadow
        firstShape.Shadow.Enabled = true;

        // Choose shadow color
        firstShape.Shadow.Color = Color.Black;

        // Set opacity (40 % transparent)
        firstShape.Shadow.Transparency = 0.4;

        // Soften edges
        firstShape.Shadow.Blur = 4.0;

        // Position shadow
        firstShape.Shadow.OffsetX = 5;
        firstShape.Shadow.OffsetY = 5;

        // Save document
        string outPath = "ShadowedShape.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}. Open it to see the shadow.");
    }
}
```

## Câu Hỏi Thường Gặp & Trường Hợp Đặc Biệt

| Question | Answer |
|----------|--------|
| **Nếu hình là ảnh thay vì hình chữ nhật thì sao?** | Các thuộc tính bóng vẫn áp dụng; chỉ cần đảm bảo `ShapeType` của hình là `Picture`. |
| **Tôi có thể tạo hoạt ảnh cho bóng không?** | Aspose.Words không hỗ trợ hoạt ảnh, nhưng bạn có thể tạo nhiều trang với offset tăng dần và dùng PowerPoint để tạo hoạt ảnh. |
| **Bóng có hoạt động khi xuất ra PDF không?** | Có. Khi bạn lưu tài liệu dưới dạng PDF (`doc.Save("out.pdf")`), Aspose.Words giữ nguyên hiệu ứng bóng. |
| **Làm sao để loại bỏ bóng sau này?** | Đặt `firstShape.Shadow.Enabled = false;` hoặc đơn giản đặt `firstShape.Shadow = null`. |
| **Có giới hạn nào cho giá trị blur không?** | Thực tế, giá trị trên `15` làm bóng trông như một vòng hào quang và có thể làm tăng kích thước tệp. |

## Các Bước Tiếp Theo – Tiếp Tục Đà Tiến

Bây giờ bạn đã biết **cách thêm bóng** và **đặt độ mờ của bóng**, hãy cân nhắc khám phá:

* **Cách tùy chỉnh bóng** hơn nữa với `Shadow.Distance` để tạo độ dịch nổi bật hơn.
* **Áp dụng hiệu ứng bóng** cho khung văn bản hoặc WordArt để thiết kế tài liệu phong phú hơn.
* **Kết hợp nhiều bóng** (ví dụ, trong + ngoài) để đạt được vẻ lớp.
* **Xuất ra HTML** và xem cách CSS `box‑shadow` phản ánh cùng các thiết lập.

Nếu bạn đang xây dựng một trình tạo báo cáo, hãy rải bóng lên tiêu đề, biểu đồ, hoặc các hộp chú thích để dẫn dắt mắt người đọc. Thử nghiệm với các màu và độ trong suốt khác nhau—có thể là một bóng xanh nhẹ cho giao diện doanh nghiệp.

---

### TL;DR

Chúng tôi đã đi qua một **ví dụ đầy đủ, tự chứa** cho thấy cách **thêm bóng vào hình**, **tùy chỉnh bóng**, **áp dụng hiệu ứng bóng**, và **đặt độ mờ của bóng** bằng Aspose.Words trong C#. Mã đã sẵn sàng chạy, các giải thích bao gồm cả *cái gì* và *tại sao*, và giờ bạn có nền tảng vững chắc để tạo kiểu cho các hình trong bất kỳ dự án tự động Word nào.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn có độ bóng đa chiều!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}