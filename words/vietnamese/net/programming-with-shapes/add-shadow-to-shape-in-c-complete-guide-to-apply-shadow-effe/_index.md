---
category: general
date: 2026-02-13
description: Thêm bóng cho hình dạng trong C# một cách nhanh chóng. Tìm hiểu cách
  áp dụng hiệu ứng bóng, thay đổi màu bóng và tạo bóng 45 độ với các ví dụ mã dễ dàng.
draft: false
keywords:
- add shadow to shape
- apply shadow effect
- change shadow color
- 45 degree shadow
- how to add shadow
language: vi
og_description: Thêm bóng cho hình dạng trong C# ngay lập tức. Hướng dẫn này cho thấy
  cách áp dụng hiệu ứng bóng, thay đổi màu bóng và đặt bóng góc 45 độ.
og_title: Thêm bóng cho hình dạng trong C# – Hướng dẫn hiệu ứng bóng từng bước
tags:
- Aspose.Words
- C#
- Document Automation
title: Thêm bóng cho hình dạng trong C# – Hướng dẫn đầy đủ để áp dụng hiệu ứng bóng
url: /vi/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm bóng cho hình dạng trong C# – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi làm thế nào để **add shadow to shape** trong tài liệu Word bằng C# chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi cần một bóng mờ nhẹ để làm nổi bật sơ đồ, nhưng lại không tìm được ví dụ ngắn gọn, sẵn sàng chạy.

Tin tốt: hướng dẫn này cung cấp cho bạn đoạn mã chính xác để **add shadow to shape**, giải thích lý do mỗi dòng quan trọng, và chỉ cho bạn cách tinh chỉnh hiệu ứng — dù bạn muốn một làn sương xám mờ ảo hay một bóng đổ 45 ° mạnh mẽ. Trong quá trình này, chúng ta cũng sẽ **apply shadow effect**, **change shadow color**, và thậm chí nói về trường hợp **45 degree shadow** cổ điển.

## Những gì bạn sẽ học

- Cách tải DOCX, tìm một shape, và bật bóng cho nó.
- Ý nghĩa của từng thuộc tính bóng (visibility, color, transparency, size, distance, angle).
- Các cách **apply shadow effect** một cách động, như lặp qua tất cả các shape hoặc xử lý các đối tượng nhóm.
- Mẹo để **changing shadow color** một cách an toàn và xử lý tài liệu không có shape.
- Cách đạt được **45 degree shadow** chính xác mà không phải đoán góc.

Không cần tài liệu bên ngoài — chỉ cần sao chép, dán và chạy. Khi kết thúc, bạn sẽ có một chương trình hoạt động, thêm bóng chuyên nghiệp cho bất kỳ shape nào.

## Điều kiện tiên quyết

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động trên .NET Framework 4.7+).
- Aspose.Words for .NET (bản dùng thử miễn phí hoặc bản có giấy phép). Cài đặt qua NuGet: `dotnet add package Aspose.Words`.
- Một file Word cơ bản (`input.docx`) đã chứa ít nhất một shape (ví dụ: hình chữ nhật hoặc ảnh).

> **Pro tip:** Nếu bạn chưa có shape, hãy chèn một shape thủ công trong Word trước; hướng dẫn này giả định shape đầu tiên là mục tiêu.

---

## Bước 1: Thiết lập dự án và tải tài liệu

Đầu tiên, tạo một ứng dụng console (hoặc bất kỳ dự án C# nào) và thêm tham chiếu tới Aspose.Words. Sau đó tải DOCX chứa shape bạn muốn cải thiện.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;          // For Shape and ShadowFormat

class Program
{
    static void Main()
    {
        // Load the Word document that contains the shape.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**Tại sao điều này quan trọng:** `Document` là điểm vào cho mọi tác vụ xử lý Word. Bằng cách tải file sớm, bạn đảm bảo mọi thao tác tiếp theo đều hoạt động trên biểu diễn trong bộ nhớ đúng.

---

## Bước 2: Lấy Shape mục tiêu

Tiếp theo, xác định shape bạn định chỉnh sửa. Ví dụ này lấy shape đầu tiên, nhưng bạn có thể điều chỉnh chỉ số hoặc lọc theo loại shape.

```csharp
        // Retrieve the first shape in the document (adjust the index if needed).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found. Add a shape to input.docx and try again.");
            return;
        }
```

**Giải thích:**  
- `GetChild(NodeType.Shape, 0, true)` duyệt cây tài liệu theo chiều sâu và trả về shape đầu tiên nó gặp.  
- Kiểm tra null ngăn ngừa `NullReferenceException` khi tài liệu không có shape — một trường hợp biên thường làm người mới gặp rắc rối.

---

## Bước 3: Bật bóng

Bóng của shape mặc định bị tắt. Bật nó chỉ cần chuyển một cờ Boolean.

```csharp
        // Turn on the shadow effect for the shape.
        targetShape.ShadowFormat.Visible = true;
```

**Điều đang diễn ra:** Đặt `Visible` thành `true` báo cho Word vẽ bóng. Nếu không có dòng này, bất kỳ cài đặt bóng nào khác bạn thay đổi sẽ bị bỏ qua.

---

## Bước 4: Cấu hình giao diện bóng

Bây giờ chúng ta định nghĩa cách bóng sẽ trông như thế nào. Đoạn mã dưới đây khớp với kiểu “đen, 30 % trong suốt, độ mờ 5 pt, độ dịch 3 pt, góc 45°” thường gặp.

```csharp
        // Configure the shadow's appearance.
        // • Black color
        // • 30 % transparent
        // • 5 pt blur radius (size)
        // • 3 pt offset distance
        // • 45° direction (angle)
        targetShape.ShadowFormat.Color = Color.Black;          // change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
        targetShape.ShadowFormat.Size = 5;                     // blur radius
        targetShape.ShadowFormat.Distance = 3;                 // offset distance
        targetShape.ShadowFormat.Angle = 45;                   // 45 degree shadow
```

**Tại sao mỗi thuộc tính quan trọng:**

| Thuộc tính | Hiệu ứng | Sử dụng điển hình |
|------------|----------|-------------------|
| `Visible` | Bật/tắt bóng | Cốt lõi để **apply shadow effect** |
| `Color` | Xác định màu sắc của bóng | Đổi sang xám để nhẹ nhàng, đỏ để nhấn mạnh |
| `Transparency` | 0 = đục, 1 = trong suốt hoàn toàn | 0.3 tạo cảm giác mềm mại, thực tế |
| `Size` | Điều chỉnh bán kính mờ (đơn vị point) | Giá trị lớn hơn tạo hiệu ứng “feathered” |
| `Distance` | Khoảng cách bóng dịch so với shape | Khoảng cách nhỏ giữ shape gắn chặt với nền |
| `Angle` | Hướng góc độ (độ, 0 = phải, 90 = lên) | 45 tạo bóng chéo cổ điển |

Bạn có thể tự do thử nghiệm — ví dụ, đặt `Color = Color.Gray` để **change shadow color** thành tông nhẹ hơn, hoặc dùng `Angle = 135` để bóng rơi về phía dưới‑trái.

---

## Bước 5: Lưu tài liệu đã chỉnh sửa

Cuối cùng, ghi các thay đổi ra đĩa. Bạn có thể ghi đè lên file gốc hoặc tạo file mới.

```csharp
        // Save the document with the new shadow.
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        Console.WriteLine("Shadow added successfully! Check output_with_shadow.docx");
    }
}
```

**Kết quả:** Mở `output_with_shadow.docx` trong Word, chọn shape, và bạn sẽ thấy một bóng đen sắc nét với góc 45 °, 30 % trong suốt, và độ mờ mềm mại. Hình ảnh này giống hệt như khi bạn tự tay áp dụng bóng qua giao diện Word.

---

## Bonus: Áp dụng bóng cho tất cả các Shape trong tài liệu

Nếu bạn cần **apply shadow effect** cho mọi shape, hãy lặp qua collection thay vì chỉ nhắm vào một node duy nhất.

```csharp
        // Loop through every shape and add the same shadow.
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Visible = true;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.3;
            shp.ShadowFormat.Size = 5;
            shp.ShadowFormat.Distance = 3;
            shp.ShadowFormat.Angle = 45;
        }
```

**Xử lý trường hợp biên:** Một số shape (ví dụ: WordArt) có thể bỏ qua một số thuộc tính. Luôn kiểm tra trên một mẫu đại diện.

---

## Xác nhận trực quan

Dưới đây là ảnh chụp màn hình của shape sau khi đã áp dụng bóng. Lưu ý độ dịch 45 ° sạch sẽ và độ trong suốt nhẹ nhàng.

![add shadow to shape example](add-shadow-to-shape.png){: .img alt="ví dụ thêm bóng cho hình dạng"}

---

## Câu hỏi thường gặp

**Hỏi: Tôi có thể sử dụng gradient màu tùy chỉnh cho bóng không?**  
Đáp: Aspose.Words chỉ hỗ trợ màu đồng nhất cho `ShadowFormat.Color`. Đối với gradient, bạn cần xuất shape dưới dạng ảnh và áp dụng hiệu ứng ở mức đồ họa.

**Hỏi: Nếu tài liệu chứa các shape được nhóm thì sao?**  
Đáp: Mỗi thành viên của một nhóm là một node `Shape` riêng. Vòng lặp trong phần “Bonus” sẽ tự động xử lý chúng.

**Hỏi: Điều này có hoạt động với các file Word 2007‑2019 không?**  
Đáp: Có. Aspose.Words trừu tượng hoá định dạng file, vì vậy cùng một đoạn mã hoạt động cho `.doc`, `.docx`, và thậm chí `.rtf`.

**Hỏi: Làm sao để làm bóng trở lại vô hiệu?**  
Đáp: Đặt `targetShape.ShadowFormat.Visible = false;` và lưu lại tài liệu.

---

## Kết luận

Bây giờ bạn đã biết chính xác cách **add shadow to shape** trong C#. Bằng cách bật `ShadowFormat.Visible` và tinh chỉnh màu, độ trong suốt, kích thước, khoảng cách và góc, bạn có thể **apply shadow effect** phù hợp với bất kỳ yêu cầu thiết kế nào — bao gồm cả **45 degree shadow** chính xác.

Dù bạn đang tự động hoá việc tạo báo cáo, xây dựng engine mẫu, hay chỉ đơn giản là làm đẹp một sơ đồ, cách tiếp cận này cho bạn toàn quyền kiểm soát lập trình đối với độ sâu hình ảnh của shape. Tiếp theo, hãy thử **changing shadow color** dựa trên theme, hoặc kết hợp với logic fill shape để tạo ra các hình ảnh động, dựa trên dữ liệu.

Chúc bạn lập trình vui vẻ, và đừng ngại thử nghiệm — bóng chỉ tốn ít công sức nhưng có thể cải thiện đáng kể khả năng đọc hiểu. Nếu bạn thấy hướng dẫn này hữu ích, hãy chia sẻ với đồng nghiệp hoặc để lại bình luận với những tùy chỉnh của bạn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}