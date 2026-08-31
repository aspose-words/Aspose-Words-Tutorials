---
category: general
date: 2026-01-03
description: Tạo hình chữ nhật trong Word bằng C# và thêm bóng cho hình. Học cách
  chèn hình vào Word, thêm bóng cho hình và tạo tài liệu Word một cách lập trình.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: vi
og_description: Tạo hình chữ nhật trong Word bằng C# và thêm bóng cho hình. Hãy làm
  theo hướng dẫn này để chèn hình vào Word, cấu hình bóng và tạo tài liệu một cách
  lập trình.
og_title: Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn chi tiết
tags:
- C#
- Word Automation
- Aspose.Words
title: Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước
url: /vi/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **create rectangle shape** trong một tài liệu Word nhưng không biết bắt đầu từ đâu? Bạn không cô đơn—nhiều nhà phát triển gặp cùng vấn đề khi họ muốn **add shadow to shape** để có vẻ ngoài chuyên nghiệp. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn chi tiết các bước để **insert shape in Word**, áp dụng một bóng nhẹ, và cuối cùng **c# generate word document** các tệp mà bạn có thể phát hành cho người dùng.

Chúng tôi sẽ bao phủ mọi thứ từ việc thiết lập dự án đến tinh chỉnh các thuộc tính bóng, và sẽ kết thúc với một mẫu mã sẵn sàng chạy. Không có phần thừa, chỉ những phần thực tế giúp hoàn thành công việc.

## Những gì bạn sẽ học

- Cách **create rectangle shape** với Aspose.Words (hoặc Open XML) trong C#
- Các thuộc tính chính xác bạn cần để **add shadow to shape** nhằm tạo độ sâu
- Vị trí đặt hình bằng cách sử dụng `DocumentBuilder`
- Cách lưu tệp sao cho mở đúng trong Microsoft Word
- Mẹo, lưu ý và các biến thể cho các kịch bản thực tế

### Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã chạy trên .NET Core và .NET Framework)  
- Một gói NuGet có thể thao tác các tệp Word – chúng tôi sẽ dùng **Aspose.Words for .NET** vì API của nó ngắn gọn. Nếu bạn thích Open XML SDK, các khái niệm vẫn giống, chỉ các lớp khác nhau.  
- Visual Studio, VS Code, hoặc bất kỳ IDE C# nào bạn thích  

> **Mẹo chuyên nghiệp:** Nếu bạn có ngân sách hạn hẹp, Aspose cung cấp bản dùng thử miễn phí rất phù hợp để học. Chỉ cần thay dòng giấy phép bằng một chú thích khi bạn thử.

## Bước 1: Cài đặt Thư viện Xử lý Word

Đầu tiên, thêm thư viện vào dự án của bạn. Mở terminal trong thư mục giải pháp và chạy:

```bash
dotnet add package Aspose.Words
```

Nếu bạn đang sử dụng Open XML SDK, lệnh sẽ là `dotnet add package DocumentFormat.OpenXml`. Phần còn lại của hướng dẫn này giả định dùng Aspose.Words, nhưng việc thay đổi các lời gọi API là đơn giản.

## Bước 2: Tạo tài liệu trống mới

Bây giờ thư viện đã sẵn sàng, chúng ta có thể **create rectangle shape** bằng cách bắt đầu với một đối tượng `Document` sạch sẽ. Hãy nghĩ đây như một bảng vẽ mới.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` cung cấp cho chúng ta cách ở mức cao để chèn nội dung mà không cần đi sâu vào cây node cấp thấp.

## Bước 3: Chèn hình chữ nhật

Với builder trong tay, chúng ta có thể **insert shape in Word**. Phương thức `InsertShape` nhận loại hình và kích thước (rộng, cao) tính bằng điểm.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Ở thời điểm này, hình chữ nhật xuất hiện trong tài liệu, nhưng trông hơi phẳng. Đó là lúc bước tiếp theo sẽ giúp.

## Bước 4: Thêm bóng cho hình

Bóng tạo cho hình cảm giác sâu hơn. Đối tượng `Shadow` cho phép chúng ta tinh chỉnh độ mờ, khoảng cách, góc, màu và độ trong suốt. Dưới đây là cấu hình đầy đủ hoạt động tốt cho hầu hết các báo cáo.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Tại sao lại dùng các giá trị này?**  
- **BlurRadius** là `5.0` giữ cạnh mượt mà mà không bị mờ.  
- **Distance** là `4.0` dịch bóng đủ để nhận thấy.  
- **Angle** `45` mô phỏng ánh sáng tự nhiên từ góc trên‑trái, một quy ước UI phổ biến.  
- **Transparency** `0.3` ngăn bóng lấn át màu nền của hình.

Nếu bạn muốn hiệu ứng mạnh hơn, tăng `BlurRadius` và giảm `Transparency`. Đối với một hiệu ứng nhẹ, gần như không nhìn thấy, đảo ngược các con số đó.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tệp ra đĩa. Phương thức `Save` tự động phát hiện định dạng từ phần mở rộng tệp, vì vậy `.docx` sẽ cho bạn định dạng Word hiện đại.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Mở `ShadowRectangle.docx` trong Microsoft Word, và bạn sẽ thấy một hình chữ nhật sắc nét với bóng mềm—chính xác những gì bạn muốn khi hỏi “**how to add shape**” với một kết quả chuyên nghiệp.

![Tạo hình chữ nhật với bóng trong Word](placeholder-image.png "Tạo hình chữ nhật với bóng trong Word")

*Văn bản thay thế hình ảnh: tạo hình chữ nhật với bóng trong Word*

## Ví dụ làm việc đầy đủ

Kết hợp tất cả lại, đây là chương trình hoàn chỉnh, sẵn sàng chạy. Sao chép‑dán vào một ứng dụng console và nhấn **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Kết quả mong đợi

- Tệp `ShadowRectangle.docx` được tạo chứa **một hình chữ nhật** nằm ở trung tâm vị trí con trỏ.  
- Hình chữ nhật hiển thị **bóng đen mềm, trong suốt 30 %** lệch ở góc 45°.  
- Không có nội dung nào khác được thêm, giữ tệp nhẹ và dễ nhúng vào các báo cáo lớn hơn.

## Câu hỏi thường gặp & Trường hợp đặc biệt

### Nếu tôi cần một hình dạng khác thì sao?

Thay `ShapeType.Rectangle` bằng bất kỳ giá trị enum `ShapeType` nào khác (ví dụ, `Ellipse`, `Triangle`). API bóng hoạt động tương tự, vì vậy bạn có thể tái sử dụng cấu hình.

### Làm sao để thay đổi màu nền?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Tôi có thể chèn hình vào một đoạn văn cụ thể không?

Có. Di chuyển `DocumentBuilder` tới đoạn văn mục tiêu bằng `builder.MoveToParagraph(index)` trước khi gọi `InsertShape`. Điều này đảm bảo hình xuất hiện chính xác ở vị trí bạn muốn.

### Còn định dạng Word cũ hơn (.doc) thì sao?

Chỉ cần thay đổi phần mở rộng:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

Tính năng bóng được hỗ trợ từ Word 2003 trở lên, vì vậy bạn vẫn sẽ thấy hiệu ứng.

### Sử dụng Open XML SDK thay vì Aspose?

Các bước vẫn giữ nguyên: tạo một `WordprocessingDocument`, thêm một phần tử `Drawing`, thiết lập các thuộc tính `<a:shadow>`. XML sẽ chi tiết hơn, nhưng các khái niệm (kích thước, độ mờ, khoảng cách, góc) vẫn áp dụng.

## Mẹo tránh lỗi

- **Đừng quên giấy phép** nếu bạn đang dùng phiên bản Aspose trả phí; nếu không sẽ nhận được watermark.  
- **Đơn vị là điểm**, không phải pixel. Một pixel màn hình điển hình ≈ 0.75 pt, vì vậy điều chỉnh kích thước cho phù hợp.  
- **Các thuộc tính bóng bị bỏ qua** nếu `WrapType` của hình được đặt thành `Inline`. Sử dụng `WrapType = WrapType.Square` cho các hình nổi mà tôn trọng việc hiển thị bóng.  
- **Lưu vào chia sẻ mạng** có thể yêu cầu quyền phù hợp; luôn kiểm tra đường dẫn trước.

## Kết luận

Bây giờ bạn đã biết cách **create rectangle shape** trong tài liệu Word bằng C#, **add shadow to shape**, và **c# generate word document** các tệp trông chuyên nghiệp ngay từ đầu. Các bước cốt lõi—cài đặt thư viện, khởi tạo `Document`, chèn hình, cấu hình bóng, và lưu—dễ nhớ và có thể áp dụng cho các hình dạng, màu sắc, hoặc dữ liệu động khác.

Tiếp theo gì? Hãy thử xếp chồng nhiều hình, nhúng hình ảnh, hoặc tạo một báo cáo đầy đủ với bảng và biểu đồ. Bạn cũng có thể khám phá định dạng có điều kiện—thay đổi độ mạnh của bóng dựa trên giá trị dữ liệu—để tài liệu của bạn không chỉ chức năng mà còn hấp dẫn về mặt thị giác.

Hãy tự do thử nghiệm, và nếu gặp bất kỳ vấn đề nào, hãy để lại bình luận bên dưới. Chúc lập trình vui vẻ, và mong các tài liệu Word của bạn luôn có bóng đổ hoàn hảo!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}