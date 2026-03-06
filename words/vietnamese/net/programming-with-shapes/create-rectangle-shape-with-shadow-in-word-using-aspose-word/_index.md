---
category: general
date: 2026-03-06
description: Tạo hình chữ nhật trong Word và thêm bóng cho hình dạng bằng Aspose.Words.
  Tìm hiểu cách chèn hình chữ nhật trong Word và cách thêm bóng cho hình dạng trong
  C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: vi
og_description: Tạo hình chữ nhật trong Word và thêm bóng cho hình dạng bằng Aspose.Words.
  Hướng dẫn chi tiết từng bước cách chèn hình chữ nhật trong Word và cách thêm bóng
  cho hình dạng.
og_title: Tạo hình chữ nhật có bóng trong Word bằng Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Tạo hình chữ nhật có bóng trong Word bằng Aspose.Words
url: /vi/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật với bóng đổ trong Word bằng Aspose.Words

Bạn đã bao giờ cần **tạo hình chữ nhật** trong một tài liệu Word nhưng không chắc làm sao để nó trông chuyên nghiệp? Bạn không phải là người duy nhất—hầu hết các nhà phát triển đều gặp khó khăn tương tự khi lần đầu tiên muốn thêm yếu tố hình ảnh vào tài liệu tự động. Tin tốt là gì? Với Aspose.Words cho .NET, bạn có thể vừa **tạo hình chữ nhật** vừa **thêm bóng cho hình** chỉ trong vài dòng C#.

Trong hướng dẫn này, chúng ta sẽ đi qua chi tiết **cách chèn hình chữ nhật vào Word**, sau đó chỉ ra **cách thêm bóng cho hình** để nó nổi bật trên trang. Khi kết thúc, bạn sẽ có một tệp `Shadow.docx` sẵn sàng để lưu, có thể mở trong Word và thấy một hình chữ nhật màu xám với bóng đổ mềm mại. Không cần tệp ảnh bổ sung, không cần chỉnh sửa thủ công—chỉ cần mã.

## Những gì bạn sẽ học

- Các câu lệnh C# chính xác cần thiết để **tạo hình chữ nhật** với Aspose.Words.  
- Cách bật và cấu hình bóng bằng đối tượng `Shadow`.  
- Lý do mỗi thuộc tính quan trọng (ví dụ: `Transparency`, `Blur`, `Angle`).  
- Những lỗi thường gặp (đơn vị, tương thích phiên bản) và cách khắc phục nhanh.  
- Một chương trình hoàn chỉnh, sẵn sàng sao chép‑dán mà bạn có thể chạy ngay hôm nay.

### Yêu cầu trước

- .NET 6+ (hoặc .NET Framework 4.7+).  
- Aspose.Words cho .NET 23.10 trở lên (gói NuGet là `Aspose.Words`).  
- Kiến thức cơ bản về C# và Visual Studio (hoặc bất kỳ IDE nào bạn thích).

Nếu bạn đã có những thứ này, hãy bắt đầu ngay.

---

## Bước 1: Thiết lập dự án và nhập namespace

Đầu tiên, tạo một ứng dụng console mới (hoặc sử dụng lại một ứng dụng hiện có) và thêm gói NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Bây giờ, đưa các namespace cần thiết vào file `Program.cs` của bạn:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang nhắm tới .NET 6+, bạn có thể bật các chỉ thị `using` toàn cục để tránh lặp lại các dòng này trong mỗi file.

---

## Bước 2: **Tạo hình chữ nhật** trong một tài liệu Word trống

Chúng ta sẽ bắt đầu với một đối tượng `Document` mới và một `DocumentBuilder` để thao tác. Phương thức `InsertShape` của builder là nơi phép thuật diễn ra.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Tại sao lại dùng 200 × 100 điểm? Trong Word, một điểm bằng 1/72 inch, vì vậy hình chữ nhật sẽ có kích thước khoảng 2.8 × 1.4 inch—đủ lớn để nhận thấy nhưng không quá to. Bạn có thể thay đổi các số này để phù hợp với bố cục; chỉ cần nhớ chúng được đo bằng **điểm**, không phải pixel.

---

## Bước 3: **Thêm bóng cho hình** – cấu hình giao diện

Bây giờ chúng ta đã có hình chữ nhật, hãy thêm cho nó một bóng xám nhẹ. Đối tượng `Shadow` nằm trong `Shape` và cung cấp một số thuộc tính hữu ích.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Mô tả từng thuộc tính

| Thuộc tính | Hiệu ứng | Giá trị điển hình |
|------------|----------|-------------------|
| **Enabled** | Bật hoặc tắt bóng | `true` hoặc `false` |
| **Color** | Màu cơ bản của bóng | Bất kỳ `System.Drawing.Color` nào |
| **Transparency** | Độ trong suốt (0 = đặc, 1 = vô hình) | 0.0 – 1.0 |
| **Blur** | Độ mềm của cạnh | 0 – 10 (cao hơn = mềm hơn) |
| **Distance** | Khoảng cách giữa hình và bóng | 0 – 20 điểm |
| **Angle** | Hướng ánh sáng tới | 0 – 360 độ |
| **Size** | Tỷ lệ bóng so với hình | 0 – 200 % |

> **Tại sao cần các thiết lập này?**  
> Điều chỉnh bóng một cách tinh tế cho phép bạn phù hợp với hướng dẫn thương hiệu công ty (ví dụ, độ trong suốt 20 % nhẹ nhàng cho vẻ ngoài chuyên nghiệp) mà không cần dùng đến các phần mềm chỉnh sửa ảnh bên ngoài.

---

## Bước 4: Lưu tài liệu và kiểm tra kết quả

Cuối cùng, ghi tệp ra đĩa. Bạn có thể chọn bất kỳ thư mục nào; chỉ cần thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Mở `Shadow.docx` trong Microsoft Word và bạn sẽ thấy một hình chữ nhật màu xám với bóng đổ nhẹ, lệch 45° độ. Hiệu ứng này khiến hình trông như “nổi lên” khỏi trang—đúng như mong đợi từ một báo cáo hoặc hoá đơn chuyên nghiệp.

---

## Ví dụ hoàn chỉnh

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào `Program.cs`. Không có phần nào bị thiếu; nó biên dịch và chạy ngay.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Kết quả mong đợi

- **Tệp:** `Shadow.docx` được đặt trong thư mục thực thi của dự án.  
- **Hình ảnh:** Một hình chữ nhật duy nhất ở giữa trang, nền trắng mặc định, và một bóng xám lệch 4 điểm về phía dưới‑phải, hơi mờ để tạo cảm giác tự nhiên.

---

## Câu hỏi thường gặp & Trường hợp đặc biệt

### 1. Nếu tôi cần đơn vị khác (ví dụ: centimet) thì sao?

Aspose.Words làm việc bằng điểm, nhưng bạn có thể chuyển đổi centimet sang điểm bằng công thức đơn giản:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Điều này có hoạt động với các phiên bản Aspose.Words cũ hơn không?

API `Shadow` được giới thiệu từ phiên bản 14.0. Nếu bạn đang dùng phiên bản cũ hơn, bạn sẽ cần nâng cấp qua NuGet. Phần còn lại của mã (tạo hình) đã ổn định trong nhiều năm, vì vậy bạn sẽ không gặp các thay đổi gây lỗi.

### 3. Tôi có thể thêm bóng cho các hình khác (ví dụ: vòng tròn) không?

Tất nhiên—bất kỳ đối tượng `Shape` nào cũng có thuộc tính `Shadow`. Chỉ cần thay `ShapeType.Rectangle` bằng `ShapeType.Ellipse` hoặc `ShapeType.Cloud`, sau đó áp dụng cùng các thiết lập bóng.

### 4. Nếu tôi cần bóng màu (ví dụ: màu xanh cho thương hiệu) thì sao?

Thay `Color.Gray` bằng bất kỳ `Color` nào bạn muốn:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Hãy nhớ điều chỉnh `Transparency` để màu không trở nên quá nổi bật.

---

## 🎨 Tổng quan hình ảnh

![tạo hình chữ nhật với bóng đổ trong Word bằng Aspose.Words](image-placeholder.png "tạo hình chữ nhật với bóng đổ trong Word bằng Aspose.Words")

*Văn bản thay thế: tạo hình chữ nhật với bóng đổ trong Word bằng Aspose.Words*

Bản chụp màn hình (placeholder) hiển thị tài liệu cuối cùng—chỉ có hình chữ nhật và bóng xám mềm.

---

## Kết luận

Bây giờ bạn đã biết cách **tạo hình chữ nhật** trong một tệp Word, **thêm bóng cho hình**, và tinh chỉnh mọi khía cạnh hình ảnh bằng Aspose.Words cho .NET. Chương trình ngắn mà chúng ta xây dựng bao phủ toàn bộ quy trình—từ

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}