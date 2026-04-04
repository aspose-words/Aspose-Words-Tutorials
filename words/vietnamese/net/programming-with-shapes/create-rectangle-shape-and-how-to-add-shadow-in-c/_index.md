---
category: general
date: 2026-04-04
description: Tạo hình chữ nhật trong C# bằng Aspose.Words và tìm hiểu cách thêm bóng,
  áp dụng hiệu ứng làm mờ cho bóng, và làm bóng trong suốt – hướng dẫn chi tiết từng
  bước.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: vi
og_description: Tạo hình chữ nhật trong C# bằng Aspose.Words. Học cách thêm bóng,
  áp dụng hiệu ứng làm mờ cho bóng và làm bóng trong suốt trong một hướng dẫn ngắn
  gọn.
og_title: Tạo hình chữ nhật và cách thêm bóng trong C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Tạo hình chữ nhật và cách thêm bóng trong C#
url: /vi/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật và cách thêm bóng trong C#

Bạn đã bao giờ cần **create rectangle shape** trong một tài liệu Word nhưng không chắc cách thêm một bóng đổ nhẹ nhàng? Bạn không phải là người duy nhất. Trong nhiều trường hợp báo cáo hoặc thương hiệu, một hình chữ nhật đơn giản với bóng mềm, bán trong suốt có thể làm cho bố cục trông tinh tế mà không tốn nhiều công sức.

Trong hướng dẫn này, chúng ta sẽ đi qua **how to create document** bằng cách sử dụng Aspose.Words, sau đó trình bày **how to add shadow**, **apply blur to shadow**, và thậm chí **make shadow transparent**. Khi kết thúc, bạn sẽ có một đoạn mã C# sẵn sàng chạy, tạo ra một tệp *.docx* với hình chữ nhật được tô bóng đẹp mắt—chỉ trong vài phút.

## Những gì bạn cần

- .NET 6 hoặc mới hơn (API cũng hoạt động với .NET Framework 4.6+)
- Aspose.Words cho .NET (bản dùng thử miễn phí hoạt động cho ví dụ này)
- Một trình soạn thảo mã – Visual Studio, VS Code, Rider, bất kỳ cái nào bạn thích
- Kiến thức cơ bản về C# – không cần phức tạp, chỉ cần khả năng chạy một ứng dụng console

Nếu bạn đã có những thứ này, chúng ta có thể chuyển thẳng vào giải pháp.

## Bước 1 – How to create document và khởi tạo canvas

Đầu tiên, bạn cần một đối tượng `Document` trống. Hãy nghĩ nó như một tờ giấy trắng mà Aspose.Words sẽ chuyển thành tệp Word sau này.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Tại sao chúng ta khởi tạo `Document` thay vì tải một mẫu? Bắt đầu từ đầu đảm bảo không có kiểu dáng hay phần nào ẩn can thiệp vào hình chữ nhật của chúng ta. Nó cũng giữ kích thước tệp nhỏ – một thói quen tốt khi bạn tạo nhiều tài liệu trong một vòng lặp.

## Bước 2 – Create rectangle shape (cốt lõi của từ khóa chính của chúng ta)

Bây giờ chúng ta thực sự **create rectangle shape**. Lớp `Shape` rất linh hoạt; bạn chỉ định loại (Rectangle), kích thước và cách nó sẽ bọc với văn bản xung quanh.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Lưu ý việc sử dụng cú pháp khởi tạo đối tượng – nó ngắn gọn và giảm khả năng quên thiết lập một thuộc tính sau này. Hình chữ nhật sẽ nằm trong đoạn văn đầu tiên, mà chúng ta sẽ thêm ở bước tiếp theo.

## Bước 3 – How to add shadow và tùy chỉnh giao diện

Thêm bóng không chỉ là một dòng duy nhất; bạn có một số thuộc tính để điều chỉnh. Đây là nơi các từ khóa phụ **apply blur to shadow** và **make shadow transparent** xuất hiện.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Một lưu ý nhanh về các số: `BlurRadius` = 5 tạo độ mờ nhẹ; tăng lên 10 để có vẻ mềm hơn, hoặc giảm xuống 2 để có cạnh sắc nét. Giá trị `Transparency` dao động từ 0 (độ trong suốt) đến 1 (vô hình). Điều chỉnh dựa trên yêu cầu độ tương phản của thương hiệu.

### Mẹo chuyên nghiệp

Nếu bạn cần một bóng màu (ví dụ màu xanh công ty), chỉ cần thay `Color.DarkGray` bằng `Color.FromArgb(80, 0, 120, 215)`. Tham số đầu tiên là kênh alpha – giữ giá trị thấp để tạo độ tinh tế.

## Bước 4 – Insert the shape vào tài liệu

Với hình chữ nhật và bóng của nó đã sẵn sàng, chúng ta sẽ đặt nó vào đoạn văn đầu tiên của tài liệu. Bước này đảm bảo hình xuất hiện ở đầu tệp.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Tại sao lại là đoạn văn đầu tiên? Đó là mặc định an toàn, hoạt động ngay cả khi tài liệu hoàn toàn trống. Nếu bạn có vị trí cụ thể (ví dụ sau một tiêu đề), bạn sẽ tìm node đó và chèn hình vào đó.

## Bước 5 – Lưu tệp và xác minh kết quả

Cuối cùng, chúng ta lưu tài liệu ra đĩa. Bạn có thể chọn bất kỳ đường dẫn nào; chỉ cần đảm bảo thư mục tồn tại.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Khi bạn mở *ShadowRectangle.docx* trong Microsoft Word, bạn sẽ thấy một hình chữ nhật 200 × 100 point với bóng màu xám đậm, hơi mờ, độ trong suốt 30 % và dịch chuyển ba point sang phải và xuống. Hiệu ứng này nhẹ nhàng nhưng thêm chiều sâu cho các bố cục phẳng.

![tạo hình chữ nhật với bóng trong Aspose.Words](https://example.com/placeholder-image.png "tạo hình chữ nhật với bóng trong Aspose.Words")

*Văn bản thay thế hình ảnh:* **create rectangle shape with shadow in Aspose.Words** – hình ảnh cho thấy tài liệu cuối cùng với hình chữ nhật có bóng.

## Các biến thể phổ biến và trường hợp đặc biệt

### Thay đổi màu bóng một cách động

Nếu ứng dụng của bạn hỗ trợ giao diện, bạn có thể lấy màu bóng từ tệp cấu hình:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Đặt hình không phải dạng nội dòng

Đôi khi bạn muốn hình chữ nhật nổi trên văn bản. Đổi `WrapType` thành `WrapType.Square` và đặt `RelativeHorizontalPosition` thành `RelativeHorizontalPosition.Margin` để có kiểm soát tốt hơn.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Xử lý nhiều trang

Nếu bạn cần một hình chữ nhật trên mỗi trang, lặp qua `doc.Sections` và thêm một hình đã sao chép vào đoạn văn đầu tiên của mỗi phần. Đừng quên gọi `rect.Clone(true)` để sao chép cả cài đặt bóng.

## Tóm tắt – Những gì chúng ta đã đạt được

- **Created rectangle shape** bằng Aspose.Words
- **How to add shadow** với màu, độ dịch, độ mờ và độ trong suốt
- Đã trình bày **apply blur to shadow** và **make shadow transparent**
- Đã lưu tệp Word mà bạn có thể mở ngay lập tức

Tất cả những điều này được thực hiện chỉ với một vài dòng mã, chứng minh rằng các điều chỉnh hình ảnh tinh vi không luôn cần các thư viện đồ họa nặng.

## Tiếp theo là gì?

- Thử nghiệm các `ShapeType` khác (Ellipse, Cloud, v.v.) và xem cách bóng hoạt động.
- Kết hợp hình chữ nhật với các hộp văn bản để tạo các chú thích có nhãn.
- Tìm hiểu sâu về **how to create document** mẫu đã chứa sẵn các placeholder cho hình, sau đó điền dữ liệu bằng chương trình.

Bạn có thể tự do điều chỉnh bán kính mờ, màu sắc hoặc độ trong suốt cho đến khi bóng trông phù hợp với ngôn ngữ thiết kế của bạn. API rất linh hoạt, và các thay đổi sẽ hiển thị ngay khi bạn chạy lại ứng dụng console.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn có chiều sâu thêm vào!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}