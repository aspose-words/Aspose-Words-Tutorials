---
category: general
date: 2026-03-01
description: Thêm hình chữ nhật vào PDF nhanh chóng bằng Aspose.Words. Tìm hiểu cách
  chèn hình dạng vào PDF, thêm đồ họa vào PDF và tạo tài liệu PDF một cách lập trình
  với bóng tùy chỉnh.
draft: false
keywords:
- add rectangle to pdf
- insert shape pdf
- add graphics to pdf
- create pdf document programmatically
- create pdf with shape
language: vi
og_description: Thêm hình chữ nhật vào PDF bằng Aspose.Words. Hướng dẫn này cho thấy
  cách chèn hình dạng vào PDF, thêm đồ họa vào PDF và tạo tài liệu PDF một cách lập
  trình bằng C#.
og_title: Thêm hình chữ nhật vào PDF bằng Aspose.Words – Hướng dẫn đầy đủ
tags:
- pdf
- aspnet
- csharp
- graphics
title: Thêm hình chữ nhật vào PDF bằng Aspose.Words – Hướng dẫn chi tiết
url: /vi/python/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm hình chữ nhật vào PDF với Aspose.Words – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **thêm hình chữ nhật vào PDF** nhưng không chắc API nào thực hiện được không? Bạn không phải là người duy nhất—các nhà phát triển thường hỏi, “Làm sao chèn shape vào PDF mà vẫn giữ file nhẹ?” Tin tốt là Aspose.Words làm cho việc này trở nên cực kỳ đơn giản. Trong tutorial này chúng ta sẽ đi qua toàn bộ quy trình, từ tạo tài liệu PDF bằng mã đến việc tạo kiểu cho hình chữ nhật với bóng đổ.

Chúng tôi cũng sẽ thêm một vài mẹo phụ: bạn sẽ học cách **thêm đồ họa vào PDF**, xem các bước chính xác để **chèn shape vào PDF**, và kết thúc bằng một ví dụ sẵn sàng chạy mà **tạo PDF với shape**. Không có tài liệu tham khảo bên ngoài, chỉ có một giải pháp tự chứa mà bạn có thể sao chép‑dán ngay hôm nay.

## Yêu cầu trước

Trước khi bắt tay vào, hãy chắc chắn bạn đã có:

- .NET 6.0 hoặc mới hơn (Aspose.Words hỗ trợ .NET Standard 2.0+)
- Giấy phép Aspose.Words for .NET hợp lệ hoặc khóa đánh giá tạm thời
- Visual Studio 2022 (hoặc bất kỳ IDE nào bạn thích)
- Kiến thức cơ bản về C#—không cần gì phức tạp, chỉ cần có khả năng chạy một ứng dụng console

Đó là tất cả. Nếu bạn đã có những thứ trên, bạn đã sẵn sàng.

## Bước 1: Tạo tài liệu PDF bằng mã

Điều đầu tiên bạn làm khi muốn **thêm hình chữ nhật vào PDF** là khởi tạo một tài liệu trống. Hãy nghĩ lớp `Document` như một canvas trắng; mọi thứ bạn thêm sau này sẽ nằm bên trong nó.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – initialise a new empty document
        Document doc = new Document();

        // The rest of the steps follow...
```

Tại sao lại bắt đầu với tài liệu trống? Vì nó đảm bảo bạn có toàn quyền kiểm soát mọi thành phần—không có tiêu đề hay chân trang ẩn nào phải xử lý sau này.

## Bước 2: Khởi tạo DocumentBuilder để chèn shape PDF

`DocumentBuilder` là cây cọ vẽ của bạn. Nó biết cách đặt văn bản, hình ảnh và, quan trọng nhất đối với chúng ta, các shape. Nếu không có nó, bạn sẽ phải tự thao tác cây node cấp thấp—a nightmare đối với hầu hết các nhà phát triển.

```csharp
        // Step 2 – create a builder that will let us add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Lưu ý chúng ta chưa thêm bất kỳ trang nào. Builder sẽ tự động tạo một trang khi bạn chèn thứ gì đó lần đầu tiên, giúp mã gọn gàng hơn.

## Bước 3: Chèn shape hình chữ nhật – phần cốt lõi của “thêm hình chữ nhật vào PDF”

Bây giờ là phần thú vị: chèn hình chữ nhật. Phương thức `InsertShape` hỗ trợ hàng chục giá trị `ShapeType`; chúng ta sẽ chọn `ShapeType.Rectangle` và đặt kích thước 200 × 100 point.

```csharp
        // Step 3 – insert a rectangle (200 × 100 points) into the document
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Tại thời điểm này PDF đã chứa một hình chữ nhật đơn giản. Nếu bạn mở file ngay bây giờ, sẽ thấy một hộp đơn giản nằm ở góc trên‑trái của trang đầu. Đó là nền tảng cho **thêm đồ họa vào PDF**.

## Bước 4: Tạo kiểu cho hình chữ nhật – thêm bóng tùy chỉnh

Một hình chữ nhật không có kiểu dáng thật nhàm chán. Hãy thêm một bóng nhẹ để nó *nổi bật* khi PDF được render. Đối tượng `ShadowFormat` điều khiển mọi thứ từ bán kính mờ tới độ trong suốt.

```csharp
        // Step 4 – configure a custom shadow for the shape
        ShadowFormat shadow = rectangle.ShadowFormat;
        shadow.Visible = true;
        shadow.BlurRadius = 8.0;          // pixels
        shadow.Distance = 5.0;           // points from the shape
        shadow.Direction = 45.0;         // degrees clockwise
        shadow.Opacity = 0.6;            // 0‑1 range
        shadow.Color = Color.Black;
```

Tại sao lại cần bóng? Ngoài việc tăng tính thẩm mỹ, bóng còn giúp phân biệt các đồ họa chồng lên nhau—điều bạn có thể cần khi **thêm đồ họa vào PDF** trong các báo cáo phức tạp hơn.

## Bước 5: Lưu file – hoàn thiện quy trình “tạo PDF với shape”

Dòng cuối cùng ghi mọi thứ ra đĩa. Aspose.Words tự động chọn phiên bản PDF phù hợp và nhúng các tài nguyên cần thiết.

```csharp
        // Step 5 – save the document as a PDF file
        doc.Save(@"C:\Temp\ShapeWithShadow.pdf");
    }
}
```

Mở `ShapeWithShadow.pdf` và bạn sẽ thấy một hình chữ nhật có bóng đẹp mắt hiện ra trên trang. Đó là toàn bộ luồng **tạo tài liệu pdf bằng mã** được gói gọn trong chưa đầy 30 dòng code.

## Ví dụ hoàn chỉnh – tạo PDF với shape từ đầu đến cuối

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào một dự án Console App mới. Nó bao gồm tất cả các câu lệnh `using`, phương thức `Main`, và một phần header chú thích ngắn cho tương lai.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectanglePdfDemo
{
    /// <summary>
    /// Demonstrates how to add a rectangle to PDF, configure a shadow,
    /// and save the result using Aspose.Words for .NET.
    /// </summary>
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty PDF document
            Document doc = new Document();

            // 2️⃣ Initialise a DocumentBuilder – the tool that lets us add content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a rectangle shape (200 × 100 points) – this is the core of "add rectangle to pdf"
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

            // 4️⃣ Apply a custom shadow – makes the graphic stand out
            ShadowFormat shadow = rect.ShadowFormat;
            shadow.Visible = true;
            shadow.BlurRadius = 8.0;   // pixels
            shadow.Distance = 5.0;    // points
            shadow.Direction = 45.0;  // degrees
            shadow.Opacity = 0.6;     // semi‑transparent
            shadow.Color = Color.Black;

            // 5️⃣ Save the document – the final step in creating a PDF with shape
            string outputPath = @"C:\Temp\ShapeWithShadow.pdf";
            doc.Save(outputPath);

            Console.WriteLine($"PDF saved successfully to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi:** một file PDF một trang, trong đó một hình chữ nhật 200 × 100 point nằm gần góc trên‑trái, được trang trí bằng bóng mờ 45 độ. Mở file bằng bất kỳ trình xem PDF nào để kiểm tra.

## Câu hỏi thường gặp & Trường hợp đặc biệt

### Có hoạt động với các loại shape khác không?
Chắc chắn. Thay `ShapeType.Rectangle` bằng `ShapeType.Ellipse`, `ShapeType.Triangle`, hoặc bất kỳ trong hơn 150 tùy chọn mà Aspose.Words hỗ trợ. Các thuộc tính `ShadowFormat` vẫn áp dụng tương tự.

### Nếu tôi muốn hình chữ nhật ở một trang cụ thể thì sao?
Sau khi chèn shape, bạn có thể di chuyển nó sang trang khác bằng cách điều chỉnh thuộc tính `CurrentPage` của builder trước khi gọi `InsertShape`. Ví dụ:

```csharp
builder.MoveToPage(3);
Shape rectOnPage3 = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

### Có thể thay đổi màu nền của hình chữ nhật không?
Có chứ. Sử dụng thuộc tính `FillColor`:

```csharp
rect.FillColor = Color.LightBlue;
```

### Điều này ảnh hưởng đến kích thước file như thế nào?
Thêm một shape đơn giản và một bóng chỉ tăng vài kilobyte. Nếu bạn bắt đầu xếp chồng nhiều đồ họa, hãy cân nhắc nén hình ảnh hoặc sử dụng các shape dựa trên vector để giữ PDF gọn nhẹ.

### Cần giấy phép cho môi trường production không?
Aspose.Words hoạt động ở chế độ đánh giá, nhưng file PDF đầu ra sẽ có watermark. Mua giấy phép để sử dụng không giới hạn và loại bỏ watermark.

## Mẹo & Thủ thuật (Cấp độ Pro)

- **Chèn hàng loạt:** Nếu cần chèn hàng chục hình chữ nhật, lặp qua một tập hợp tọa độ và tái sử dụng cùng một `DocumentBuilder`—hiệu năng vẫn tuyến tính.
- **Lớp phủ:** Đặt `rect.WrapType = WrapType.Inline` nếu muốn hình chữ nhật chạy cùng văn bản, hoặc `WrapType.Square` để văn bản bao quanh nó.
- **Tuân thủ PDF/A:** Gọi `doc.CompatibilityOptions.OptimizeForPdfA = true;` trước khi lưu nếu bạn cần PDF phù hợp lưu trữ.

## Tóm tắt hình ảnh

![add rectangle to pdf example](https://example.com/rectangle-shadow.png "add rectangle to pdf example")

Hình ảnh minh họa bố cục PDF cuối cùng: một hình chữ nhật sạch sẽ với bóng nhẹ, chính xác như code của chúng ta tạo ra.

## Kết luận

Bây giờ bạn đã biết **cách thêm hình chữ nhật vào PDF** bằng Aspose.Words, **cách chèn shape PDF**, và **cách thêm đồ họa vào PDF** với kiểu tùy chỉnh—tất cả trong khi **tạo tài liệu PDF bằng mã** và kết thúc bằng một ví dụ **tạo PDF với shape** mà bạn có thể tái sử dụng ngay ngày mai.  

Tiếp theo, hãy thử thay hình chữ nhật bằng logo, hoặc kết hợp nhiều shape để xây dựng một sơ đồ đơn giản. Bạn cũng có thể khám phá việc bao quanh văn bản, xoay, hoặc thậm chí nhúng hyperlink vào shape. API đủ mạnh để biến một PDF tĩnh thành một báo cáo tương tác, giàu đồ họa mà không cần rời khỏi C#.

Hãy thoải mái thử nghiệm, và nếu gặp khó khăn, hãy để lại bình luận bên dưới. Chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}