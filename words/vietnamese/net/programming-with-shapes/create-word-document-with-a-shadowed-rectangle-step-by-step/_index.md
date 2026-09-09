---
category: general
date: 2026-01-13
description: Tạo tài liệu Word bằng Aspose.Words và tìm hiểu cách chèn hình chữ nhật,
  cách thêm bóng, và cách thêm bóng cho hình dạng trong C#. Bao gồm ví dụ hoàn chỉnh.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: vi
og_description: Tạo tài liệu Word với Aspose.Words, xem cách chèn hình chữ nhật và
  cách thêm bóng. Tham khảo ví dụ C# đầy đủ.
og_title: Tạo tài liệu Word với hình chữ nhật có bóng – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Document Automation
title: Tạo tài liệu Word với hình chữ nhật có bóng – Hướng dẫn từng bước
url: /vi/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word với hình chữ nhật có bóng – Hướng dẫn từng bước

Bạn đã bao giờ cần **create word document** chứa một hình chữ nhật được tô bóng đẹp mắt, nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp cùng một khó khăn khi họ mới bắt đầu làm việc với Aspose.Words.  

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn mọi thứ cần thiết để **create word document** một cách lập trình, **insert rectangle shape**, và chỉ ra **how to add shadow** để hình dạng thực sự nổi bật. Khi kết thúc, bạn sẽ có một đoạn mã C# sẵn sàng chạy mà bạn có thể chèn vào bất kỳ dự án .NET nào.

## Những gì bạn sẽ học

- Mã chính xác để **how to insert shape** (một hình chữ nhật) vào tệp Word.  
- Các thuộc tính bạn phải điều chỉnh để **add shape shadow** và kiểm soát giao diện của nó.  
- Cách lưu kết quả và xác minh rằng bóng được hiển thị.  
- Một vài mẹo thực tế và lưu ý các trường hợp đặc biệt giúp bạn tránh rắc rối sau này.

Không cần tài liệu bên ngoài—mọi thứ đều có ở đây.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

1. **.NET 6.0** (hoặc bất kỳ phiên bản .NET nào gần đây) đã được cài đặt.  
2. Một **license** cho Aspose.Words cho .NET, hoặc bạn có thể sử dụng chế độ đánh giá miễn phí để thử nghiệm.  
3. Môi trường phát triển—Visual Studio 2022 hoạt động tốt, nhưng bất kỳ trình soạn thảo nào có thể biên dịch C# cũng được.

Chỉ vậy thôi. Không cần gói NuGet nào khác ngoài `Aspose.Words` được cần.

## Bước 1 – Thiết lập dự án và tham chiếu Aspose.Words

Đầu tiên, tạo một ứng dụng console mới và thêm gói Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng bản dùng thử miễn phí, hãy nhớ gọi `License.SetLicense` với tệp giấy phép của bạn; nếu không thư viện sẽ thêm watermark.

## Bước 2 – Khởi tạo Document Builder

Bây giờ chúng ta sẽ bắt đầu quá trình **create word document** thực tế. Lớp `Document` cung cấp cho chúng ta một canvas trống, và `DocumentBuilder` cho phép chúng ta vẽ lên đó.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Tại sao chúng ta cần một builder? Nó trừu tượng hoá các chi tiết OpenXML cấp thấp, vì vậy bạn có thể tập trung vào *cái gì* bạn muốn thay vì *cách* tệp được cấu trúc. Đây là cốt lõi của **how to insert shape** nhanh chóng.

## Bước 3 – Chèn hình chữ nhật

Đây là nơi chúng ta thực sự **insert rectangle shape**. Hình chữ nhật sẽ có kích thước 150 × 100 điểm (khoảng 2 inch × 1.3 inch).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Phương thức `InsertShape` trả về một đối tượng `Shape`, mà chúng ta có thể tùy chỉnh thêm. Tại thời điểm này, hình chữ nhật chỉ là một hộp trắng đặc—chưa có bóng.

## Bước 4 – Cách thêm bóng (Add Shape Shadow)

Thêm bóng thực sự đơn giản khi bạn biết những thuộc tính nào cần chỉnh. Đối tượng `ShadowFormat` điều khiển khả năng hiển thị, màu, độ mờ, độ lệch và kích thước.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Khối mã đó trả lời **how to add shadow** một cách rõ ràng: bật nó lên, chọn màu, điều chỉnh độ trong suốt, độ lệch, độ mờ và kích thước. Bạn có thể thử nghiệm các số này để có bóng đổ dày hoặc mỏng như thì thầm.

### Các biến thể phổ biến

- **Màu khác nhau:** Sử dụng `Color.Black` cho bóng đổ cổ điển, hoặc `Color.BlueViolet` cho hiệu ứng phong cách.  
- **Không độ mờ:** Đặt `BlurRadius = 0` để có cạnh sắc nét, rõ ràng.  
- **Độ lệch lớn hơn:** Tăng `OffsetX`/`OffsetY` để đẩy bóng xa hơn khỏi hình dạng.

## Bước 5 – Lưu tài liệu và xác minh

Cuối cùng, ghi tài liệu ra đĩa. Tệp sẽ là một `.docx` tiêu chuẩn mà bất kỳ trình xử lý Word hiện đại nào cũng có thể mở.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Mở *ShadowRectangle.docx* kết quả trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật với bóng xám mềm, lệch về phía dưới‑phải—đúng như mã đã chỉ định.

> **Kết quả mong đợi:** Một tệp Word một trang chứa hình chữ nhật 150 × 100 điểm với bóng xám trong suốt 30 %, lệch 5 pts, mờ 4 pts, và kích thước 75 % của hình dạng.

## Ví dụ hoạt động đầy đủ

Kết hợp mọi thứ lại, đây là chương trình hoàn chỉnh, sẵn sàng chạy:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Chạy chương trình (`dotnet run`) và bạn sẽ có một tệp Word mới với hình chữ nhật có bóng đẹp mắt—hoàn hảo cho báo cáo, chứng chỉ, hoặc bất kỳ dấu hiệu trực quan nào bạn cần.

## Câu hỏi thường gặp (FAQs)

**Q: Tôi có thể chèn các hình dạng khác (ellipse, star) và vẫn sử dụng cùng mã bóng không?**  
A: Chắc chắn. Phương thức `InsertShape` chấp nhận bất kỳ giá trị enum `ShapeType` nào. Khi bạn có một thể hiện `Shape`, các thuộc tính `ShadowFormat` hoạt động giống nhau, vì vậy **how to add shadow** không phụ thuộc vào hình dạng.

**Q: Nếu tôi cần bóng ở cả hai phía của hình dạng thì sao?**  
A: Aspose.Words chỉ hỗ trợ một bóng đổ duy nhất cho mỗi hình dạng. Để mô phỏng hiệu ứng hai phía, sao chép hình dạng, lệch mỗi bản sao khác nhau, và đặt `ShadowFormat.Visible` của một bản sao thành `false` trong khi giữ bóng của bản sao còn lại hiển thị.

**Q: Điều này có hoạt động trên .NET Framework 4.8 không?**  
A: Có. API không phụ thuộc vào phiên bản; chỉ cần tham chiếu DLL Aspose.Words phù hợp cho framework mục tiêu của bạn.

## Mẹo & Cạm bẫy

- **Đừng quên đặt `Visible = true`**—các thuộc tính bóng sẽ bị bỏ qua nếu không.  
- **Giá trị trong suốt nằm trong khoảng từ 0.0 (độ đục) đến 1.0 (hoàn toàn trong suốt).** Một lỗi thường gặp là sử dụng `30` thay vì `0.3`.  
- **Lưu vào thư mục chỉ đọc sẽ gây ra ngoại lệ.** Đảm bảo thư mục đầu ra có quyền ghi.

## Bước tiếp theo

Bây giờ bạn đã biết **how to insert shape**, **add shape shadow**, và **create word document** với Aspose.Words, bạn có thể muốn khám phá:

- Thêm **text inside the rectangle** bằng cách sử dụng `builder.InsertParagraph()` trước khi chèn hình dạng.  
- Áp dụng **gradient fills** hoặc **patterned borders** để có kiểu dáng trực quan phong phú hơn.  
- Tự động tạo nhiều trang, mỗi trang có một hình dạng có bóng khác nhau, để xây dựng báo cáo động.

Hãy thoải mái thử nghiệm—thay đổi màu, độ mờ hoặc kích thước của bóng có thể thay đổi đáng kể giao diện tài liệu của bạn.

---

*Sẵn sàng đưa vào sản xuất? Lấy mã, điều chỉnh các tham số, và xem các tệp Word của bạn trở nên chuyên nghiệp trong tích tắc.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}