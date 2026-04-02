---
category: general
date: 2026-04-02
description: Tìm hiểu cách đặt bóng cho một hình dạng trong Aspose.Words bằng C#.
  Chúng tôi cũng sẽ chỉ cho bạn cách thêm bóng vào hình dạng, điều chỉnh độ mờ, tùy
  chỉnh bóng và lưu tài liệu có bóng.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- how to adjust blur
- how to customize shadow
- save document with shadow
language: vi
og_description: Cách đặt bóng cho một hình dạng trong Aspose.Words bằng C#. Tham khảo
  hướng dẫn từng bước để thêm bóng cho hình dạng, điều chỉnh độ mờ, tùy chỉnh bóng
  và lưu tài liệu có bóng.
og_title: Cách thiết lập bóng cho hình dạng trong Aspose.Words (C#)
tags:
- Aspose.Words
- C#
- Document Automation
title: Cách đặt bóng cho hình dạng trong Aspose.Words (C#)
url: /vi/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Bóng cho Hình Dạng trong Aspose.Words (C#)

Bạn đã bao giờ tự hỏi **cách đặt bóng** cho một hình dạng để tài liệu Word của bạn trông chuyên nghiệp hơn chưa? Bạn không phải là người duy nhất—các nhà phát triển thường hỏi cách thêm một bóng mờ nhẹ nhàng làm cho sơ đồ nổi bật mà không phá vỡ bố cục. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn chi tiết các bước **cách đặt bóng** cho một hình dạng bằng cách sử dụng Aspose.Words cho .NET, và trong quá trình đó chúng tôi cũng sẽ đề cập đến **thêm bóng vào hình dạng**, **cách điều chỉnh độ mờ**, **cách tùy chỉnh bóng**, và cuối cùng là **lưu tài liệu với bóng**.

Chúng tôi sẽ bắt đầu với các yêu cầu tiên quyết, sau đó đi sâu vào từng thuộc tính của lớp `ShadowFormat`, và kết thúc bằng một ví dụ hoàn chỉnh, có thể chạy được mà bạn có thể sao chép‑dán vào Visual Studio. Khi kết thúc, bạn sẽ hiểu tại sao mỗi cài đặt quan trọng, những trường hợp góc cạnh cần lưu ý, và cách xác minh rằng bóng thực sự tạo ra sự khác biệt.

---

## Những Gì Bạn Cần

- **Aspose.Words for .NET** (phiên bản mới nhất tại thời điểm viết, 23.12). Bạn có thể lấy nó qua NuGet: `Install-Package Aspose.Words`.
- Môi trường phát triển .NET (Visual Studio 2022 hoặc VS Code với phần mở rộng C# hoạt động tốt).
- Một tệp DOCX đầu vào đã chứa ít nhất một hình dạng (hình chữ nhật, hình ảnh, hoặc SmartArt). Nếu bạn chưa có, hãy tạo một tệp Word nhanh và chèn bất kỳ hình dạng nào—Aspose.Words sẽ đọc nó như bình thường.
- Không cần thư viện bên thứ ba nào khác; mọi thứ đều nằm trong không gian tên `Aspose.Words`.

## Cách Đặt Bóng cho Hình Dạng

### Bước 1 – Tải Tài liệu và Lấy Hình Dạng Mục Tiêu

Đầu tiên chúng ta mở tệp nguồn và lấy hình dạng đầu tiên mà chúng ta muốn định dạng. Đây là mẫu giống như bạn sẽ dùng cho bất kỳ thao tác nào với hình dạng.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains a shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Retrieve the first shape in the document (index 0). 
// The GetChild method walks the node tree recursively.
Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
```

> **Tại sao điều này quan trọng:**  
> `GetChild` với `true` đảm bảo chúng ta tìm kiếm toàn bộ cây tài liệu, vì vậy ngay cả khi hình dạng nằm trong tiêu đề, chân trang, hoặc hộp văn bản, chúng ta vẫn sẽ tìm thấy nó. Bỏ qua bước này sẽ khiến bạn nhận được một tham chiếu `null` và một `NullReferenceException`.

### Bước 2 – Truy cập Đối tượng ShadowFormat

Mỗi `Shape` cung cấp một thuộc tính `ShadowFormat` gộp tất cả các cài đặt liên quan đến bóng. Hãy nghĩ nó như “hộp công cụ bóng”.

```csharp
// Grab the ShadowFormat – this is where we configure colour, distance, blur, etc.
ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Mẹo chuyên nghiệp:** Nếu hình dạng đã có bóng, `ShadowFormat` sẽ chứa các giá trị hiện có. Bạn có thể đọc chúng trước khi ghi đè nếu cần giữ lại bất kỳ mặc định nào.

### Bước 3 – Thêm Bóng vào Hình Dạng: Chọn Màu và Khoảng Cách

Bây giờ chúng ta thực sự **thêm bóng vào hình dạng** bằng cách đặt màu và khoảng cách offset. Màu được định nghĩa bằng ARGB để bạn có thể kiểm soát độ trong suốt trực tiếp.

```csharp
// Semi‑transparent purple (alpha 128, red 0, green 0, blue 128)
shadow.Color = Color.FromArgb(128, 0, 0, 128);

// Distance from the shape to the shadow, measured in points.
shadow.Distance = 5.0;   // 5 points ≈ 1.75 mm
```

> **Tại sao màu quan trọng:** Kênh alpha (số đầu tiên) xác định mức độ trong suốt của bóng. Một bóng hoàn toàn mờ (alpha 255) có thể trông gắt, trong khi alpha thấp hơn tạo ra hiệu ứng mềm mại, thực tế hơn.

### Bước 4 – Cách Điều Chỉnh Độ Mờ cho Hiệu Ứng Thực Tế

Một bóng sắc nét, có cạnh cứng hiếm khi trông đẹp trong tài liệu kinh doanh. Hãy sử dụng thuộc tính `BlurRadius` để làm mềm các cạnh.

```csharp
// Blur radius in points – larger values create a softer edge.
shadow.BlurRadius = 3.0;
```

> **Sai lầm thường gặp:** Đặt `BlurRadius` thành `0` sẽ tạo ra bóng răng cưa có thể phá vỡ luồng hình ảnh của báo cáo. Giá trị từ `2` đến `5` thường hoạt động tốt cho hầu hết các tài liệu xem trên màn hình.

### Bước 5 – Cách Tùy Chỉnh Độ Trong Suốt và Kiểu Dáng của Bóng

Ngoài màu và độ mờ, bạn có thể điều chỉnh độ trong suốt tổng thể của bóng. Điều này tách biệt với kênh alpha của màu.

```csharp
// Overall transparency (0 = opaque, 1 = fully transparent)
shadow.Transparency = 0.3;   // 30 % transparent
```

> **Trường hợp đặc biệt:** Nếu bạn đặt cả alpha của màu và `Transparency` ở mức cao, bóng có thể trở nên vô hình. Hãy kiểm tra bằng bản xem trước để chắc chắn nó vẫn nhìn thấy được.

### Bước 6 – Lưu Tài liệu với Bóng

Cuối cùng, lưu các thay đổi. Bước này minh họa **lưu tài liệu với bóng** để bạn có thể mở tệp trong Word và xem kết quả.

```csharp
// Save the updated document. Overwrite or use a new file name as you prefer.
doc.Save("YOUR_DIRECTORY/output.docx");
```

> **Mẹo kiểm tra:** Mở `output.docx` trong Microsoft Word, chọn hình dạng, và nhìn vào menu thả xuống “Shadow” dưới “Shape Format”. Bạn sẽ thấy màu tùy chỉnh, offset, độ mờ và độ trong suốt mà bạn vừa thiết lập.

## Thêm Bóng vào Hình Dạng – Lựa Chọn Màu và Khoảng Cách Phù Hợp

Khi bạn **thêm bóng vào hình dạng**, tác động hình ảnh phụ thuộc mạnh vào độ tương phản màu với nền trang. Bóng tối trên trang sáng cảm giác tự nhiên, trong khi màu sáng có thể dùng cho hiệu ứng nghệ thuật.

- **Màu xám đậm (ví dụ, #808080)** hoạt động tốt cho báo cáo chính thức.  
- **Màu nhấn** (như màu tím bán trong suốt chúng tôi đã dùng) có thể làm nổi bật hộp chú thích trong tài liệu marketing.

Bạn cũng có thể thay đổi thuộc tính `ShadowFormat.Angle` để xoay hướng bóng, nhưng mặc định (45°) thường tạo ra offset chéo hài hòa.

```csharp
shadow.Angle = 45.0;   // Default angle – feel free to experiment
```

## Cách Điều Chỉnh Độ Mờ cho Các Phương Tiện Đầu Ra Khác Nhau

Nếu tài liệu của bạn sẽ được in, bạn có thể muốn độ mờ hơi chặt hơn vì máy in độ phân giải cao có thể hiển thị gradient nhẹ. Ngược lại, đối với PDF chỉ xem trên màn hình, độ mờ lớn hơn tránh các cạnh răng cưa trên màn hình DPI thấp.

```csharp
// Example: tighter blur for print
if (doc.PageCount > 0 && doc.FirstSection.PageSetup.PaperSize == PaperSize.A4)
{
    shadow.BlurRadius = 2.0;   // Slightly sharper for print
}
else
{
    shadow.BlurRadius = 4.0;   // Softer for screen
}
```

> **Tại sao điều kiện này hữu ích:** Nó minh họa **cách điều chỉnh độ mờ** dựa trên một kiểm tra thời gian chạy đơn giản, cho thấy bạn có thể làm cho bóng đáp ứng với môi trường tiêu thụ cuối cùng.

## Cách Tùy Chỉnh Độ Trong Suốt và Màu Sắc của Bóng một cách Động

Đôi khi bạn cần tạo tài liệu cho các hướng dẫn thương hiệu khác nhau. Hãy làm cho màu bóng và độ trong suốt có thể cấu hình qua các tham số phương thức.

```csharp
void ApplyCustomShadow(Shape shape, Color colour, double distance, double blur, double transparency)
{
    ShadowFormat sf = shape.ShadowFormat;
    sf.Color = colour;
    sf.Distance = distance;
    sf.BlurRadius = blur;
    sf.Transparency = transparency;
}
```

Bạn có thể gọi:

```csharp
ApplyCustomShadow(targetShape, Color.FromArgb(200, 255, 0, 0), 4.0, 2.5, 0.2);
```

> **Trường hợp thực tế:** Các đội marketing thường yêu cầu bóng màu đỏ đặc trưng cho thương hiệu trên tờ rơi quảng cáo. Phương thức trợ giúp này cho phép bạn đáp ứng yêu cầu mà không cần viết lại logic cốt lõi.

## Lưu Tài liệu với Bóng – Lưu Trữ Các Thay Đổi của Bạn

Một câu hỏi thường gặp là liệu bóng có tồn tại khi tài liệu được chuyển đổi sang PDF hay không. Câu trả lời là **có**, miễn là bạn sử dụng `PdfSaveOptions` bảo tồn các đối tượng vẽ.

```csharp
PdfSaveOptions pdfOpts = new PdfSaveOptions
{
    // Ensure all drawing effects, including shadows, are retained.
    EmbedFullFonts = true,
    Compliance = PdfCompliance.PdfA2b
};

doc.Save("YOUR_DIRECTORY/output.pdf", pdfOpts);
```

Bây giờ bạn có cả DOCX và PDF mà bóng của hình dạng trông giống hệt nhau.

## Ví Dụ Hoàn Chỉnh Hoạt Động

Dưới đây là chương trình đầy đủ, sẵn sàng sao chép‑dán, kết nối mọi thứ lại với nhau. Thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế trên máy của bạn.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the source document.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Grab the first shape (you could loop over all shapes if needed).
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Access the shadow format.
        ShadowFormat shadow = shape.ShadowFormat;

        // 4️⃣ Set colour, distance, blur and transparency.
        shadow.Color = Color.FromArgb(128, 0, 0, 128); // semi‑transparent purple
        shadow.Distance = 5.0;                        // offset in points
        shadow.BlurRadius = 3.0;                      // soft edge
        shadow.Transparency = 0.3;                    // 30 % transparent

        // Optional: tweak angle for a different light source.
        shadow.Angle = 45.0;

        // 5️⃣ Save the DOCX – this demonstrates save document with shadow.
        doc.Save("YOUR_DIRECTORY/output.docx");

        // 6️⃣ Also export to PDF to prove the shadow carries over.
        PdfSaveOptions pdfOpts = new PdfSaveOptions

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}