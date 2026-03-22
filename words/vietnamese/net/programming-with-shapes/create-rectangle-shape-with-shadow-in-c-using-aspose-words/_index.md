---
category: general
date: 2026-03-22
description: Tạo hình chữ nhật trong C# và thêm bóng cho hình dạng bằng Aspose.Words.
  Tìm hiểu cách thêm bóng, cách tạo hình chữ nhật và cách thiết lập các thuộc tính
  bóng.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: vi
og_description: Tạo hình chữ nhật trong C# và thêm bóng cho hình dạng bằng Aspose.Words.
  Hướng dẫn từng bước về cách thêm bóng, cách tạo hình chữ nhật và cách thiết lập
  bóng.
og_title: Tạo hình chữ nhật có bóng trong C# – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Document Automation
title: Tạo hình chữ nhật có bóng trong C# bằng Aspose.Words
url: /vi/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật có bóng trong C# bằng Aspose.Words

Bạn đã bao giờ cần **tạo hình chữ nhật** trong một tài liệu Word nhưng không chắc làm thế nào để thêm một bóng đổ nhẹ? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp khó khăn này khi mới bắt đầu với tự động hoá tài liệu. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách **thêm bóng vào hình** bằng Aspose.Words, và đồng thời trả lời các câu hỏi “**cách thêm bóng**”, “**cách tạo hình chữ nhật**”, và “**cách đặt bóng**”.

Chúng ta sẽ bắt đầu với một `Document` trống, vẽ một hình chữ nhật, bật bóng cho nó, điều chỉnh độ mờ, khoảng cách, góc và màu sắc, và cuối cùng lưu file. Khi kết thúc, bạn sẽ có một file `.docx` sẵn sàng sử dụng hiển thị một hình chữ nhật màu xám nổi lên phía trên trang. Không có gì bí ẩn, chỉ là mã đơn giản bạn có thể sao chép‑dán vào bất kỳ dự án .NET nào.

## Yêu cầu trước

* **Aspose.Words for .NET** (phiên bản mới nhất tính đến tháng 3 2026). Bạn có thể tải về từ NuGet bằng lệnh `Install-Package Aspose.Words`.
* Môi trường phát triển .NET – Visual Studio, Rider, hoặc thậm chí VS Code với extension C# cũng hoạt động tốt.
* Kiến thức cơ bản về C# – không cần gì phức tạp, chỉ cần khả năng tạo một ứng dụng console hoặc WinForms.

Hết rồi. Không cần thư viện bổ sung, không có bước ẩn. Sẵn sàng? Hãy bắt đầu.

## Bước 1: Khởi tạo một tài liệu trống mới

Để **tạo hình chữ nhật**, trước tiên chúng ta cần một container – một đối tượng `Document` – đại diện cho file Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

Lớp `Document` là điểm khởi đầu cho mọi thao tác của Aspose.Words. Hãy nghĩ nó như một bảng vẽ trống; nếu không có nó, bạn không thể thêm bất kỳ hình dạng, bảng hay văn bản nào.

## Bước 2: Tạo hình chữ nhật sẽ chứa bóng

Bây giờ chúng ta sẽ **cách tạo hình chữ nhật** bằng cách khởi tạo một `Shape` loại `Rectangle`. Chúng ta cũng sẽ đặt kích thước của nó bằng điểm (1 point ≈ 1/72 inch).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Tại sao chọn 200 × 100 point? Đó là kích thước vừa phải cho một demo – đủ lớn để nhìn rõ bóng, nhưng không quá to đến mức lấn át trang. Bạn có thể tự do điều chỉnh các số này để phù hợp với bố cục của mình.

## Bước 3: Bật hiệu ứng bóng và cấu hình giao diện

Đây là phần cốt lõi của hướng dẫn: **cách thêm bóng** và **cách đặt bóng** cho các thuộc tính. Aspose.Words cung cấp một đối tượng `Shadow` trên mỗi hình, cho phép bạn bật/tắt hiệu ứng và điều chỉnh các tham số hình ảnh.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** làm mềm các cạnh – giá trị cao hơn khiến bóng trông mờ hơn.
* **Distance** đẩy bóng xa hơn so với hình chữ nhật.
* **Angle** xác định hướng ánh sáng; 45° tạo ra góc chéo, nhìn tự nhiên.
* **Color** cho phép bạn chọn bất kỳ `System.Drawing.Color` nào. Màu xám là mặc định an toàn, nhưng bạn có thể dùng `Color.Black` táo bạo hoặc `Color.LightGray` nhẹ nhàng.

Mẹo: Nếu bạn đặt `Enabled = false`, tất cả các cài đặt bóng khác sẽ bị bỏ qua, vì vậy luôn kiểm tra lại cờ này.

## Bước 4: Chèn hình vào phần thân tài liệu

Với hình chữ nhật đã sẵn sàng và bóng đã được cấu hình, chúng ta cần đặt nó vào tài liệu. Cách đơn giản nhất là thêm nó vào đoạn văn đầu tiên của phần đầu tiên.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Nếu tài liệu của bạn đã có văn bản, bạn có thể tìm một `Paragraph` cụ thể hoặc thậm chí một ô `Table` và chèn hình vào đó. Phương thức `AppendChild` rất linh hoạt – nó hoạt động với bất kỳ kiểu `Node` nào.

## Bước 5: Lưu tài liệu và kiểm tra kết quả

Cuối cùng, chúng ta ghi file ra đĩa. Thay đổi đường dẫn thành bất kỳ vị trí nào bạn muốn; thư mục phải tồn tại, nếu không sẽ gây ra ngoại lệ.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Mở file `ShadowedRectangle.docx` vừa tạo trong Microsoft Word (hoặc LibreOffice) và bạn sẽ thấy một hình chữ nhật màu xám với bóng chéo rõ ràng, hướng xuống‑phải. Nếu bóng quá nhạt, tăng `BlurRadius` hoặc `Distance` và chạy lại mã – việc thử nghiệm là một phần thú vị.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Ví dụ tạo hình chữ nhật có bóng"}

### Kết quả mong đợi

* Một tài liệu Word một trang.
* Một hình chữ nhật màu xám 200 × 100 point được đặt ở góc trên‑trái của trang.
* Một bóng màu xám nhẹ được dịch chuyển 8 pixel ở góc 45°, mờ 5 pixel.

## Cách thêm bóng vào hình – khám phá sâu hơn

Bạn có thể tự hỏi, *“Tôi có thể tạo hoạt ảnh cho bóng hoặc làm nó thay đổi dựa trên đầu vào của người dùng không?”* Mặc dù Aspose.Words không hỗ trợ hoạt ảnh, bạn có thể điều chỉnh các thuộc tính bóng bằng mã trước khi lưu, tạo ra nhiều phiên bản của cùng một tài liệu với giao diện khác nhau. Ví dụ, lặp qua một tập hợp các màu:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Đoạn mã nhỏ này minh họa **cách đặt bóng** một cách động—rất hữu ích cho việc tạo báo cáo theo chủ đề.

## Cách tạo hình chữ nhật – các hình dạng thay thế

Nếu bạn cần một hình chữ nhật bo tròn, chỉ cần thay đổi `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Hoặc, để có một hình vuông hoàn hảo, đặt `Width` bằng `Height`. Các thuộc tính bóng vẫn áp dụng, vì vậy bạn đã có sẵn **cách thêm bóng** cho bất kỳ hình nào bạn chọn.

## Những lỗi thường gặp và cách khắc phục

| Triệu chứng | Nguyên nhân khả dĩ | Cách khắc phục |
|------------|--------------------|----------------|
| Bóng không xuất hiện | `Shadow.Enabled` để là `false` | Set `rectangleShape.Shadow.Enabled = true;` |
| Bóng trông quá sắc | `BlurRadius` được đặt thành 0 | Tăng `BlurRadius` lên ít nhất 3 |
| Tài liệu ném `FileNotFoundException` khi lưu | Thư mục đích không tồn tại | Tạo thư mục trước hoặc sử dụng đường dẫn hợp lệ |
| Hình không hiển thị | `Width`/`Height` được đặt thành 0 | Đảm bảo cả hai kích thước đều > 0 |

Theo dõi những vấn đề này sẽ giúp bạn tránh được tình huống “tại sao hình của tôi không hiển thị?” cổ điển.

## Tóm tắt – những gì chúng ta đã đạt được

* **Tạo hình chữ nhật** trong một tài liệu Word mới bằng Aspose.Words.  
* **Thêm bóng vào hình** bằng cách bật/tắt cờ `Shadow.Enabled` và điều chỉnh độ mờ, khoảng cách, góc và màu.  
* Trình bày **cách thêm bóng**, **cách tạo hình chữ nhật**, và **cách đặt bóng** trong một đoạn mã sạch sẽ, có thể tái sử dụng.  
* Cung cấp một ví dụ hoàn chỉnh, sẵn sàng chạy mà bạn có thể dán vào bất kỳ dự án C# nào.

## Bước tiếp theo là gì?

Bây giờ bạn đã nắm vững các kiến thức cơ bản, hãy xem xét khám phá:

* **Cách thêm bóng vào hình ảnh** – API `Shadow` tương tự hoạt động cho `ShapeType.Image`.
* **Kết hợp nhiều hình** – tạo lưu đồ hoặc infographic trực tiếp trong Word.
* **Xuất ra PDF** – gọi `document.Save("output.pdf")` sau khi thêm bóng để có phiên bản có thể in.

Bạn có thể thoải mái thử nghiệm với các màu sắc, góc độ khác nhau, hoặc thậm chí các màu gradient. API đủ linh hoạt để bạn tạo ra các tài liệu chuyên nghiệp mà không cần mở Word thủ công.

---

Chúc lập trình vui vẻ! Nếu bạn gặp bất kỳ vấn đề nào, hãy để lại bình luận bên dưới hoặc kiểm tra diễn đàn Aspose.Words – cộng đồng sẽ nhanh chóng hỗ trợ.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}