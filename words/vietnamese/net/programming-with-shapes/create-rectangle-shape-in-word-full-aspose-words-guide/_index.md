---
category: general
date: 2026-02-26
description: Tạo hình chữ nhật trong Word bằng Aspose.Words và học cách thêm hình
  vào Word, áp dụng bóng đổ cho hình, và thiết lập độ trong suốt của hình chỉ trong
  vài phút.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: vi
og_description: Tạo hình chữ nhật trong Word bằng Aspose.Words. Học cách thêm hình
  vào Word, áp dụng bóng cho hình và thiết lập độ trong suốt của hình một cách nhanh
  chóng.
og_title: Tạo hình chữ nhật trong Word – Hướng dẫn đầy đủ Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Tạo hình chữ nhật trong Word – Hướng dẫn đầy đủ Aspose.Words
url: /vi/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Hình Chữ Nhật trong Word – Hướng Dẫn Toàn Diện Aspose.Words

Bạn đã bao giờ cần **tạo hình chữ nhật** trong một tài liệu Word nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn khi tự động hoá báo cáo hoặc hoá đơn. Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy, cho bạn thấy cách **thêm hình vào Word**, áp dụng một bóng mờ tinh tế, và kiểm soát độ trong suốt của hình, tất cả đều bằng Aspose.Words cho .NET.

Khi hoàn thành, bạn sẽ có một tệp `.docx` chứa một hình chữ nhật sạch sẽ với bóng mờ được đánh bóng—hoàn hảo cho thương hiệu, chú thích, hoặc chỉ để làm tài liệu của bạn trông chuyên nghiệp hơn một chút. Không cần công cụ bên ngoài, chỉ vài dòng C#.

## Những Gì Bạn Cần Chuẩn Bị

- **Aspose.Words cho .NET** (phiên bản mới nhất tính đến đầu năm 2026). Bạn có thể tải về từ NuGet (`Install-Package Aspose.Words`).
- Môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code với extension C#).
- Kiến thức cơ bản về cú pháp C#—không cần gì phức tạp, chỉ các câu lệnh `using` và tạo đối tượng thông thường.

Nếu bạn đã có những thứ trên, tuyệt vời—cùng bắt đầu.

## Tạo Hình Chữ Nhật – Các Bước Cốt Lõi

Dưới đây là mã nguồn đầy đủ. Sao chép‑dán vào một dự án console mới, nhấn **F5**, và bạn sẽ thấy `ShadowDemo.docx` xuất hiện trong thư mục bạn chỉ định.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Tại Sao Cách Này Hoạt Động

- **`Document`** là điểm vào; nó đại diện cho toàn bộ tệp Word.
- **`Shape`** với `ShapeType.Rectangle` cho Aspose biết chúng ta muốn một đối tượng vẽ hình chữ nhật.
- Đặt **`Width`** và **`Height`** cho hình kích thước xác định; nếu không sẽ mặc định là một placeholder rất nhỏ.
- Đối tượng **`Shadow`** cho phép chúng ta tinh chỉnh mọi khía cạnh hình ảnh: độ mờ, khoảng cách, hướng, màu, độ trong suốt và độ lan. Đây là phần cốt lõi của *apply shadow to shape*.
- Cuối cùng, **`AppendChild`** chèn hình vào đoạn văn đầu tiên của tài liệu, là cách đơn giản nhất để *add shape to Word* mà không phải lo về bảng hay header.

Khi bạn mở `ShadowDemo.docx`, sẽ thấy một hình chữ nhật màu xám nằm thoải mái trong tài liệu, bóng của nó nghiêng xuống‑phải ở góc 45°. Bóng không phải là một khối đặc; bán kính mờ làm mềm các cạnh, và độ trong suốt khiến nó trông giống như một bóng thả tự nhiên thay vì một lớp phủ cứng.

![ví dụ tạo hình chữ nhật](image.png "tạo hình chữ nhật với bóng mờ trong Word bằng Aspose.Words")

*(Hình ảnh trên hiển thị kết quả cuối cùng của đoạn mã.)*

## Thêm Hình Vào Tài Liệu Word – Các Tùy Chọn Đặt Vị Trí

Ví dụ sử dụng **đoạn văn đầu tiên** vì đây là cách nhanh nhất để thấy kết quả trên màn hình. Trong các tình huống thực tế, bạn có thể muốn:

- Chèn hình vào một **section** hoặc **header/footer** cụ thể.
- Đặt nó bên trong một **ô bảng** để căn chỉnh với dữ liệu dạng bảng.
- Bao bọc nó bằng các tùy chọn **text wrapping** (ví dụ, `WrapType.Square`) để văn bản xung quanh chảy quanh hình chữ nhật.

Dưới đây là một biến thể nhanh đặt hình vào một đoạn văn mới với kiểu dáng tùy chỉnh:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Pro tip:* Luôn thêm hình **sau** khi bạn đã cấu hình các thuộc tính của nó; nếu không bạn có thể cần gọi `UpdateLayout` để làm mới hiển thị.

## Áp Dụng Bóng Cho Hình – Tinh Chỉnh Ngoại Hình

Bóng có thể thay đổi đáng kể thẩm mỹ của tài liệu. Lớp `Shadow` cung cấp một số thuộc tính:

| Property      | What It Controls                                   | Typical Values |
|---------------|----------------------------------------------------|----------------|
| `BlurRadius`  | Softness of the shadow edges                      | 2.0 – 10.0      |
| `Distance`    | How far the shadow is offset from the shape        | 1.0 – 8.0       |
| `Direction`   | Angle in degrees (0 = left, 90 = up)              | 0 – 360         |
| `Color`       | Shadow colour (any `System.Drawing.Color`)        | Gray, Black, Custom |
| `Transparency`| Opacity (0 = fully opaque, 1 = invisible)        | 0.0 – 0.5       |
| `Spread`      | Expansion of the shadow before blur is applied    | 0.0 – 1.0       |

Nếu bạn muốn một **giao diện tinh tế, chuyên nghiệp**, giữ `BlurRadius` khoảng 4‑6 và `Transparency` gần 0.2, giống như đoạn mã trên. Đối với **hiệu ứng mạnh mẽ**, tăng `Distance` lên 6, đặt `Direction` thành 135°, và giảm `Transparency` xuống 0.05.

## Đặt Độ Trong Suốt và Độ Lan Của Bóng Cho Hình

Độ trong suốt không chỉ áp dụng cho bóng; bạn cũng có thể làm cho hình chữ nhật tự nó một phần trong suốt:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Kết hợp màu nền bán trong suốt với bóng mềm thường tạo cảm giác UI hiện đại—rất thích hợp cho bảng điều khiển hoặc mock‑up thiết kế nhúng trong báo cáo.

### Các Trường Hợp Cần Lưu Ý

1. **Phiên bản Word cũ** (trước 2007) không hỗ trợ một số thuộc tính bóng. Nếu bạn tạo file `.doc`, hãy cân nhắc đơn giản hoá bóng (ví dụ, đặt `BlurRadius` = 0).
2. **Màn hình DPI cao** có thể hiển thị bóng hơi khác nhau. Kiểm tra trên môi trường mục tiêu nếu độ chính xác hình ảnh là quan trọng.
3. **Các hình chồng lên nhau**—Aspose vẽ bóng theo thứ tự chúng được thêm. Chèn các hình từ phía sau ra phía trước để tránh che lấp không mong muốn.

## Lưu và Kiểm Tra Kết Quả

Phương thức `Document.Save` tự động phát hiện định dạng đầu ra từ phần mở rộng tệp. Đối với tệp **`.docx`** bạn nhận được định dạng Open XML, mà hầu hết các trình xử lý Word hiện đại đều hiểu. Nếu bạn cần một phiên bản **PDF** với cùng kiểu dáng, chỉ cần thay đổi phần mở rộng:

```csharp
document.Save("ShadowDemo.pdf");
```

Mở `ShadowDemo.docx` (hoặc `ShadowDemo.pdf`) sẽ hiển thị một **hình chữ nhật có bóng**, xác nhận rằng bạn đã thành công trong việc *create rectangle shape* và *apply shadow to shape* bằng Aspose.Words.

## Câu Hỏi Thường Gặp

**Q: Tôi có thể dùng một hình dạng khác, như ellipse không?**  
A: Chắc chắn. Thay `ShapeType.Rectangle` bằng `ShapeType.Ellipse` (hoặc bất kỳ enum `ShapeType` nào khác). Các thuộc tính bóng vẫn giữ nguyên.

**Q: Nếu muốn hình chữ nhật có thể nhấp được thì sao?**  
A: Bạn có thể gán một hyperlink cho hình:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Điều này có hoạt động trên .NET 6+ không?**  
A: Có. Aspose.Words 23.11 trở lên hoàn toàn hỗ trợ .NET 6, .NET 7 và .NET 8. Chỉ cần tham chiếu gói NuGet tương ứng.

**Q: Làm sao thay đổi màu bóng để phù hợp với thương hiệu của tôi?**  
A: Sử dụng bất kỳ `System.Drawing.Color` nào bạn muốn:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Kết Luận

Chúng ta đã bao quát mọi thứ bạn cần để **tạo hình chữ nhật** trong tài liệu Word, **thêm hình vào Word**, **áp dụng bóng cho hình**, và **đặt độ trong suốt cho hình**. Mã hoàn chỉnh, có thể chạy, nằm ở đầu trang này, và các giải thích sẽ giúp bạn tự tin điều chỉnh kích thước, màu sắc và các tham số bóng cho bất kỳ dự án nào.

Sẵn sàng cho bước tiếp theo? Hãy thử:

- Nhiều hình chồng lên nhau để tạo hiệu ứng huy hiệu.
- Kích thước động dựa trên nội dung tài liệu (ví dụ, tính chiều rộng từ cột bảng).
- Xuất tài liệu sang PDF hoặc HTML trong khi giữ nguyên bóng.

Bạn cứ để lại bình luận nếu gặp khó khăn, hoặc chia sẻ các biến thể của bạn về chủ đề “hình chữ nhật có bóng”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}