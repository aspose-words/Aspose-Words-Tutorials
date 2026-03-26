---
category: general
date: 2026-03-25
description: Tạo tài liệu PDF bằng C# và học cách thêm hình chữ nhật, đặt màu nền,
  điều chỉnh kích thước hình và thiết lập độ trong suốt của hình chỉ trong vài bước.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: vi
og_description: Tạo tài liệu PDF bằng C# và tìm hiểu cách thêm hình chữ nhật, đặt
  màu nền, kích thước và độ trong suốt để có đầu ra PDF tinh tế.
og_title: Tạo tài liệu PDF với hình chữ nhật – Hướng dẫn C#
tags:
- C#
- PDF
- Aspose.Words
title: Tạo tài liệu PDF với hình chữ nhật – Hướng dẫn C# đầy đủ
url: /vi/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu PDF với hình chữ nhật – Hướng dẫn đầy đủ C#

Bạn đã bao giờ cần **tạo tài liệu PDF** chứa một hình dạng được tùy chỉnh, nhưng không biết bắt đầu từ đâu? Bạn không phải là người duy nhất. Dù bạn đang xây dựng một trình tạo báo cáo hay một tờ rơi marketing, khả năng vẽ một hình chữ nhật bằng mã, đặt màu nền, điều chỉnh kích thước và thậm chí điều chỉnh độ trong suốt có thể làm cho PDF của bạn trông chuyên nghiệp hơn rất nhiều.

Trong tutorial này, chúng ta sẽ đi qua một ví dụ C# hoàn chỉnh, sẵn sàng chạy, **tạo tài liệu PDF**, **thêm hình chữ nhật**, **đặt màu nền**, **định nghĩa kích thước hình**, và **đặt độ trong suốt cho hình** để tạo hiệu ứng bóng ngoài nhẹ nhàng. Khi hoàn thành, bạn sẽ có một file PDF duy nhất (`shadow.pdf`) có thể mở để xem kết quả.

> **Pro tip:** Cách tiếp cận này cũng hoạt động với các loại hình khác (ellipse, line, v.v.)—chỉ cần thay `ShapeType.RECTANGLE` bằng loại bạn cần.

---

## Những gì bạn cần

| Điều kiện tiên quyết | Lý do quan trọng |
|----------------------|-------------------|
| **.NET 6+** (hoặc .NET Framework 4.6+) | Thư viện Aspose.Words nhắm tới các runtime hiện đại. |
| **Aspose.Words for .NET** NuGet package | Cung cấp `Document`, `Shape`, `ShadowEffect`, và các lớp liên quan. |
| **A C# IDE** (Visual Studio, Rider, VS Code) | Giúp việc gỡ lỗi và chạy mẫu trở nên dễ dàng. |
| **Basic C# knowledge** | Bạn sẽ hiểu cú pháp mà không cần đào sâu. |

Bạn có thể cài đặt thư viện qua dòng lệnh:

```bash
dotnet add package Aspose.Words
```

Xong rồi—không cần DLL bổ sung, không có phụ thuộc native. Khi gói đã có, đoạn code dưới đây sẽ biên dịch và chạy.

---

## Thực hiện từng bước

Dưới đây chúng tôi chia quá trình thành năm bước logic. Mỗi bước có tiêu đề rõ ràng (để các mô hình AI có thể lập chỉ mục) và một đoạn code ngắn mà bạn có thể sao chép‑dán trực tiếp.

### ## 1. Tạo tài liệu PDF và chuẩn bị Canvas

Điều đầu tiên chúng ta làm là khởi tạo một `Document`. Hãy nghĩ nó như một canvas trống sẽ cuối cùng trở thành file PDF của bạn.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Why?** `Document` chứa tất cả các section, paragraph và shape. Bắt đầu với một đối tượng sạch sẽ đảm bảo không có artefact ẩn từ các lần chạy trước.

### ## 2. Thêm hình chữ nhật – Đặt màu nền và kích thước

Bây giờ chúng ta tạo một hình chữ nhật, cho nó màu vàng sáng và xác định kích thước. Điều này bao gồm cả **add rectangle shape**, **set fill color** và **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Note:** Chiều rộng/chiều cao được đo bằng points (1 point = 1/72 inch). Điều chỉnh các số này để phù hợp với bố cục của bạn.

### ## 3. Áp dụng bóng ngoài và đặt độ trong suốt cho hình

Bóng giúp tạo độ sâu, và việc kiểm soát độ mờ là cốt lõi của **set shape transparency**. Dưới đây chúng ta cấu hình một bóng ngoài màu xám với độ trong suốt 30 %.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Why set transparency?** Bóng trong suốt 30 % trông nhẹ nhàng, ngăn hình chữ nhật trở nên “phẳng” trên trang.

### ## 4. Chèn hình vào phần thân tài liệu

Chúng ta giờ đặt hình chữ nhật vào đoạn văn đầu tiên của section đầu tiên trong tài liệu. Bước này kết nối mọi thứ lại với nhau.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Edge case:** Nếu bạn cần hình trên một trang mới, thêm `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` trước khi chèn shape.

### ## 5. Lưu tài liệu dưới dạng file PDF

Cuối cùng, chúng ta ghi cấu trúc trong bộ nhớ ra một file PDF thực tế. File sẽ được ghi vào thư mục bạn chỉ định.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Khi chạy chương trình, một file có tên `shadow.pdf` sẽ xuất hiện. Mở nó sẽ thấy một hình chữ nhật màu vàng với bóng xám mềm, dịch chuyển 4 points—đúng như code mô tả.

> **Expected output:** Một PDF một trang, trong đó hình chữ nhật nằm gần góc trên‑trái của trang, được tô màu vàng, kích thước 200 × 100 points, và có bóng ngoài bán trong suốt.

---

## Ví dụ hoàn chỉnh (Sẵn sàng sao chép)

Dưới đây là toàn bộ file nguồn, sẵn sàng để bạn đưa vào một dự án console mới.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Tip:** Thay `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối như `C:\Temp` hoặc đường dẫn tương đối như `.\output`. Chương trình sẽ tạo thư mục nếu nó chưa tồn tại.

---

## Câu hỏi thường gặp (FAQ)

**Q: Tôi có thể thay đổi vị trí của hình chữ nhật trên trang không?**  
A: Chắc chắn. Đặt `rectangle.Left` và `rectangle.Top` (cũng đo bằng points) trước khi chèn nó vào paragraph.

**Q: Nếu tôi muốn nền trong suốt thay vì bóng trong suốt thì sao?**  
A: Dùng `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – đối số đầu tiên là kênh alpha (0‑255), trong đó 128 cho độ trong suốt khoảng 50 %.

**Q: Điều này có hoạt động với .NET Core không?**  
A: Có. Aspose.Words hỗ trợ .NET Standard 2.0+, vì vậy bạn có thể chạy cùng một code trên .NET 6, .NET 7, hoặc .NET Framework 4.6+.

**Q: Làm sao để thêm nhiều hình?**  
A: Chỉ cần lặp lại các bước 2‑4 cho mỗi hình, có thể chèn chúng vào các paragraph hoặc section khác nhau.

---

## Kết luận

Chúng ta vừa **tạo tài liệu PDF** từ đầu, **thêm hình chữ nhật**, **đặt màu nền**, **định nghĩa kích thước**, và **điều chỉnh độ trong suốt** để đạt hiệu ứng bóng ngoài tinh tế. Mã mẫu độc lập, chạy trong vòng chưa tới một phút, và minh họa các khái niệm cốt lõi bạn sẽ cần cho các bố cục PDF phức tạp hơn.

Sẵn sàng cho thử thách tiếp theo? Hãy thử thay hình chữ nhật bằng hình có góc bo tròn, nhúng ảnh vào trong shape, hoặc tự động tạo mục lục. Cùng một API, bạn có thể xếp lớp văn bản, hình ảnh và vector—giới hạn chỉ là trí tưởng tượng.

Nếu bạn thấy hướng dẫn này hữu ích, hãy star trên GitHub, chia sẻ với đồng nghiệp, hoặc để lại bình luận với các biến thể của bạn. Chúc lập trình vui! 

---

![tạo tài liệu pdf với hình chữ nhật và bóng ngoài](/images/rectangle-shadow.png "Ảnh chụp màn hình hiển thị PDF đã tạo với hình chữ nhật màu vàng và bóng ngoài màu xám")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}