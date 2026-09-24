---
category: general
date: 2026-02-18
description: Tạo hình chữ nhật bằng Aspose.Words và tìm hiểu cách thêm bóng, đặt kích
  thước hình, và lưu tài liệu Word trong vài phút.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: vi
og_description: Tạo hình chữ nhật trong tệp Word, tìm hiểu cách thêm bóng, đặt kích
  thước hình dạng và lưu tài liệu bằng Aspose.Words trong C#.
og_title: Tạo hình chữ nhật trong Word – Hướng dẫn đầy đủ Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo hình chữ nhật trong Word bằng Aspose.Words – Hướng dẫn từng bước
url: /vi/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

Let's produce final translation.

We'll keep the same structure.

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong Word bằng Aspose.Words – Hướng dẫn từng bước

Bạn đã bao giờ cần **tạo hình chữ nhật** trong một tệp Word nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất—các nhà phát triển thường hỏi, “làm sao để thêm bóng cho một hình và vẫn giữ cho tài liệu có thể chỉnh sửa?” Trong tutorial này chúng tôi sẽ trả lời câu hỏi đó và cũng chỉ cho bạn **cách thêm bóng**, **đặt kích thước hình**, và **lưu tài liệu Word** trong một quy trình liền mạch.

Chúng ta sẽ đi qua mọi thứ bạn cần, từ khởi tạo một tài liệu mới (đúng, đó là bước đầu tiên để **cách tạo tài liệu**) đến việc lưu *.docx* cuối cùng lên đĩa. Không có tham chiếu bên ngoài, chỉ một ví dụ tự chứa mà bạn có thể sao chép‑dán vào Visual Studio và chạy ngay hôm nay.

---

## Yêu cầu trước

- .NET 6+ (hoặc .NET Framework 4.7+). Aspose.Words hoạt động với bất kỳ runtime .NET hiện đại nào.
- Giấy phép Aspose.Words hợp lệ (hoặc khóa dùng thử miễn phí) – nếu không sẽ thấy watermark.
- Visual Studio, Rider, hoặc bất kỳ trình soạn thảo C# nào bạn thích.
- Kiến thức cơ bản về C#—không cần gì phức tạp, chỉ cần có khả năng chạy một ứng dụng console.

> **Mẹo chuyên nghiệp:** Nếu bạn đang dùng Mac, cùng một đoạn mã vẫn chạy dưới .NET 6 với VS Code—chỉ cần chắc chắn bạn đã tham chiếu gói NuGet `Aspose.Words`.

---

## Bước 1: Khởi tạo tài liệu – nền tảng của **cách tạo tài liệu**

Trước khi chúng ta có thể vẽ bất cứ thứ gì, cần một canvas trống. Aspose.Words gọi nó là một `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Tại sao lại quan trọng:** Đối tượng `Document` đại diện cho toàn bộ tệp *.docx*. Tất cả các hình, đoạn văn và phần bạn thêm sẽ trở thành con của đối tượng này. Bắt đầu với một tài liệu sạch sẽ giúp tránh các style ẩn can thiệp vào hình chữ nhật của bạn.

---

## Bước 2: Định nghĩa hình chữ nhật và **đặt kích thước hình**

Một hình chữ nhật chỉ là một `Shape` với `ShapeType.Rectangle`. Chúng ta sẽ chỉ định kích thước cụ thể để nó hiển thị đúng như mong muốn.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Ý nghĩa của các số:** Aspose.Words sử dụng đơn vị điểm (1 pt = 1/72 in). Điều chỉnh các giá trị để phù hợp với bố cục của bạn; với một trang A4 tiêu chuẩn, 200 pt là chiều rộng thoải mái.

---

## Bước 3: **Cách thêm bóng** – làm cho hình nổi bật hơn

Bóng tạo ra cảm giác hình “nổi lên” khỏi trang. Thuộc tính `Shadow` cho phép bạn tinh chỉnh màu, khoảng cách, độ trong suốt và độ mờ.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Tại sao dùng độ trong suốt?** Một bóng hoàn toàn đục có thể trông gắt gao. Đặt giá trị 0.4 sẽ tạo hiệu ứng nhẹ nhàng và chuyên nghiệp.

---

## Bước 4: Đặt vị trí hình chữ nhật – dòng chảy nội tuyến với văn bản xung quanh

Nếu bạn muốn hình hành xử như một ký tự trong đoạn văn, đặt `WrapType` thành `Inline`. Điều này giữ cho bố cục dự đoán được, đặc biệt khi tài liệu được chỉnh sửa sau này.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Trường hợp đặc biệt:** Nếu bạn cần hình chữ nhật nổi trên văn bản (ví dụ: watermark), thay đổi `WrapType` thành `Square` hoặc `BehindText`.

---

## Bước 5: Chèn hình vào phần thân tài liệu

Bây giờ chúng ta thực sự đặt hình chữ nhật vào đoạn văn đầu tiên. Nếu tài liệu chưa có nội dung, `FirstParagraph` sẽ được tạo tự động.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Mẹo:** Bạn cũng có thể tạo một đoạn văn mới trước và sau đó thêm hình—hữu ích khi cần văn bản bao quanh.

---

## Bước 6: **Lưu tài liệu Word** – bước cuối cùng

Với mọi thứ đã sẵn sàng, việc lưu file chỉ mất một dòng lệnh. Chọn bất kỳ đường dẫn nào bạn muốn; ví dụ dưới đây dùng một placeholder mà bạn nên thay bằng thư mục thực tế của mình.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Kết quả:** Mở *.docx* đã tạo trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật có bóng đen, rộng 200 pt và cao 100 pt, nằm nội tuyến với đoạn văn đầu tiên.

---

## Kết quả mong đợi

Khi bạn mở **ShadowShape.docx**, tài liệu sẽ hiển thị:

- Một đoạn văn duy nhất chứa một hình chữ nhật.
- Hình chữ nhật có bóng đen nhẹ, dịch chuyển 5 pt.
- Kích thước hình khớp với các giá trị đã đặt ở Bước 2.
- Không có văn bản thừa nào xuất hiện trừ khi bạn tự thêm vào.

Nếu hình không hiển thị, hãy kiểm tra lại rằng bạn đã tham chiếu đúng phiên bản Aspose.Words và giấy phép (hoặc bản dùng thử) đang hoạt động.

---

## Câu hỏi thường gặp & Các biến thể

| Câu hỏi | Trả lời |
|----------|--------|
| *Tôi có thể đổi màu bóng sang màu khác ngoài đen không?* | Chắc chắn—đặt `rectangleShape.Shadow.Color = Color.Blue;` hoặc bất kỳ `System.Drawing.Color` nào. |
| *Nếu tôi cần một hình chữ nhật lớn hơn?* | Điều chỉnh giá trị `Width` và `Height`. Nhớ rằng chúng tính bằng điểm; 72 pt = 1 in. |
| *Có thể đặt hình ở vị trí tuyệt đối không?* | Có—sử dụng `WrapType = WrapType.Absolute` và đặt các thuộc tính `Top`/`Left`. |
| *Điều này có hoạt động với .NET Core không?* | Có. Aspose.Words đa nền tảng; chỉ cần cài đặt gói NuGet cho .NET Standard. |
| *Tôi có thể chèn văn bản bên trong hình chữ nhật không?* | Không trực tiếp; bạn cần chèn một shape `TextBox` thay vì hình chữ nhật thông thường. |

---

## Ví dụ đầy đủ (Sẵn sàng sao chép‑dán)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Chạy chương trình, điều hướng tới `C:\Temp\ShadowShape.docx`, và bạn sẽ thấy hình chữ nhật có bóng đúng như mô tả.

---

## Kết luận

Bây giờ bạn đã biết cách **tạo hình chữ nhật** trong tệp Word bằng Aspose.Words, cách **đặt kích thước hình**, **thêm bóng**, và cuối cùng **lưu tài liệu Word** với các thay đổi. Toàn bộ quy trình—từ **cách tạo tài liệu** đến việc lưu kết quả—chỉ mất vài dòng C# và có thể mở rộng cho các bố cục phức tạp hơn.

Sẵn sàng cho thử thách tiếp theo? Hãy thử thay hình chữ nhật bằng hình có góc bo tròn, thử nghiệm các màu bóng khác nhau, hoặc nhúng hình vào trong một ô bảng. Mỗi thay đổi đều củng cố các khái niệm cốt lõi mà chúng ta đã đề cập.

Nếu bạn thấy hướng dẫn này hữu ích, hãy chia sẻ, để lại bình luận với các biến thể của bạn, hoặc khám phá các tutorial khác của chúng tôi về tự động hoá Word, như chèn hình ảnh hoặc tạo bảng với Aspose.Words. Chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}