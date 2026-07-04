---
category: general
date: 2026-04-28
description: Cách đặt bóng cho hình nhanh chóng. Tìm hiểu cách thêm bóng cho hình,
  thiết lập màu bóng và tùy chỉnh bóng cho hình với Aspose.Words cho .NET.
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: vi
og_description: Cách đặt bóng cho một hình dạng trong C# với Aspose.Words. Hướng dẫn
  từng bước bao gồm thêm bóng cho hình dạng, đặt màu bóng và tùy chỉnh bóng cho hình
  dạng.
og_title: Cách Đặt Bóng Đổ cho Hình Dạng trong C# – Hướng Dẫn Toàn Diện
tags:
- Aspose.Words
- C#
- Document Automation
title: Cách đặt bóng cho hình trong C# – Thêm bóng cho hình một cách dễ dàng
url: /vi/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Bóng Cho Hình Dạng trong C# – Thêm Bóng Hình Dễ Dàng

Bạn đã bao giờ tự hỏi **cách đặt bóng** cho một hình dạng mà không phải lục lọi qua vô số tài liệu API chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi cần một bóng đổ nhẹ nhàng để làm cho sơ đồ nổi bật, nhưng lại không tìm được ví dụ sạch sẽ thể hiện cả “cái gì” và “tại sao”.

Trong hướng dẫn này, chúng ta sẽ đi qua cách thêm bóng cho hình dạng, thay đổi màu bóng, và tinh chỉnh độ mờ, độ dịch và độ trong suốt — tất cả đều sử dụng Aspose.Words cho .NET. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy mà có thể chèn vào bất kỳ dự án C# nào, cùng với một vài mẹo để tùy chỉnh bóng hình trong các kịch bản phức tạp hơn.

> **Note:** Mã này hoạt động với Aspose.Words 22.9 trở lên và yêu cầu .NET 6+ (hoặc .NET Framework 4.7.2+).  

![Hình với bóng tùy chỉnh](shape-shadow.png "Hình với bóng tùy chỉnh")

## Những Điều Bạn Sẽ Học

- **Thêm bóng cho hình dạng** một cách lập trình vào hình đầu tiên trong tài liệu Word.  
- **Đặt màu bóng** thành bất kỳ `System.Drawing.Color` nào.  
- **Tùy chỉnh bóng hình dạng** bằng cách điều chỉnh bán kính mờ, độ dịch và độ trong suốt.  
- Cách xử lý nhiều hình và đặt lại cài đặt bóng nếu cần.  

Không cần công cụ bên ngoài, không cần macro Visual Basic — chỉ C# thuần túy.

---

## Yêu Cầu Trước

| Yêu Cầu | Lý Do Quan Trọng |
|-------------|----------------|
| **Aspose.Words for .NET** (gói NuGet `Aspose.Words`) | Cung cấp các lớp `Document`, `Shape`, và `ShadowFormat` được sử dụng trong ví dụ. |
| **.NET 6 SDK** (hoặc .NET Framework 4.7.2) | Đảm bảo tương thích với bề mặt API mới nhất. |
| **Một tệp .docx** có ít nhất một hình (ví dụ: hình chữ nhật hoặc hình ảnh) | Hướng dẫn thao tác với *hình đầu tiên*; bạn có thể tạo một hình trong Word nếu chưa có. |

Cài đặt thư viện bằng:

```bash
dotnet add package Aspose.Words
```

---

## Các Bước: Cách Đặt Bóng Cho Hình Dạng

### 1. Tải tài liệu Word

Chúng ta bắt đầu bằng việc mở tệp `.docx`. Hàm khởi tạo `Document` đọc tệp vào bộ nhớ, cho phép chúng ta truy cập đầy đủ vào các nút của nó.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why?** Tải tài liệu là nền tảng — nếu không có nó, bạn không thể duyệt cây hình dạng.

### 2. Lấy hình đầu tiên (hoặc bất kỳ hình nào bạn cần)

Aspose.Words lưu trữ các hình dưới dạng nút loại `NodeType.SHAPE`. Phương thức `GetChild` cho phép chúng ta lấy hình *thứ n*; ở đây chúng ta lấy chỉ số 0, tức là hình đầu tiên.

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **Pro tip:** Nếu bạn cần **thêm bóng cho hình dạng** vào một hình cụ thể, hãy thay đổi chỉ số thành giá trị phù hợp hoặc lặp qua `doc.GetChildNodes(NodeType.Shape, true)`.

### 3. Truy cập đối tượng định dạng bóng

Mỗi `Shape` có thuộc tính `ShadowFormat` cung cấp tất cả các cài đặt liên quan đến bóng.

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

Bây giờ chúng ta có thể bắt đầu tinh chỉnh bóng.

### 4. Đặt bán kính mờ – làm mềm các cạnh

Bán kính mờ lớn hơn sẽ làm cho bóng trông phân tán hơn. Giá trị tính bằng điểm (1 pt ≈ 1/72 inch).

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **When to adjust?** Nếu hình của bạn rất nhỏ, độ mờ 2–3 pt có thể đủ; đối với các biểu ngữ lớn, hãy tăng lên 8–10 pt.

### 5. Xác định độ dịch ngang và dọc

Độ dịch kiểm soát khoảng cách bóng được dịch chuyển so với hình. Giá trị dương di chuyển bóng sang phải/dưới; giá trị âm di chuyển sang trái/lên trên.

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. Tinh chỉnh độ trong suốt (độ mờ)

`Transparency` có giá trị từ `0.0` (đầy đủ) đến `1.0` (hoàn toàn trong suốt). Giá trị khoảng `0.3` tạo ra hiệu ứng nhẹ, bán trong suốt.

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. Chọn màu bóng – **đặt màu bóng** thành bất kỳ `System.Drawing.Color`

Bạn có thể chọn bất kỳ màu đã định nghĩa sẵn hoặc tạo màu tùy chỉnh bằng giá trị RGB.

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

Nếu bạn thích bóng đen cổ điển, chỉ cần dùng `Color.Black`.

### 8. Lưu tài liệu đã chỉnh sửa

Cuối cùng, ghi lại các thay đổi. Bạn có thể ghi đè lên tệp gốc hoặc lưu vào vị trí mới.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## Ví Dụ Hoàn Chỉnh (Tất Cả Các Bước Trong Một Khối)

Sao chép‑dán đoạn dưới đây vào phương thức `Main` của một ứng dụng console. Nó biên dịch ngay, với giả định rằng gói NuGet đã được cài đặt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**Expected result:** Mở `output_with_shadow.docx` trong Word; hình đầu tiên bây giờ hiển thị bóng xanh nhẹ, dịch 3 pt, với độ mờ nhẹ và 30 % độ trong suốt.

---

## Các Biến Thể Thông Thường & Trường Hợp Cạnh

### Thêm bóng cho *tất cả* các hình

Nếu tài liệu của bạn chứa nhiều sơ đồ, bạn có thể lặp qua mọi hình:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### Đặt lại bóng

Đôi khi một hình đã có bóng và bạn cần loại bỏ nó. Đặt `ShadowFormat.Visible` thành `false`:

```csharp
shape.ShadowFormat.Visible = false;
```

### Sử dụng màu tùy chỉnh với alpha (bán trong suốt)

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### Ghi chú về khả năng tương thích

API `ShadowFormat` ổn định qua các phiên bản Aspose.Words, nhưng các bản phát hành cũ hơn (< 19.1) sử dụng các trường `ShadowFormat` với cách đặt tên hơi khác. Luôn nhắm tới gói NuGet mới nhất để có kết quả tốt nhất.

---

## Mẹo Chuyên Nghiệp Để Có Bóng Hoàn Hảo

- **Cân bằng mờ và độ dịch:** Một độ mờ lớn với độ dịch nhỏ có thể trông “phát sáng” hơn là một bóng đổ thực sự. Thử nghiệm với `BlurRadius` × `DistanceX/Y`.
- **Phù hợp với giao diện tài liệu:** Nếu tệp Word dùng giao diện tối, một bóng sáng (`Color.White`) có thể tạo hiệu ứng nâng nhẹ.
- **Hiệu năng:** Thay đổi bóng cho hàng trăm hình có thể tốn vài mili giây cho mỗi hình. Hãy gộp thao tác nếu bạn xử lý các báo cáo lớn.
- **Kiểm thử:** Mở tệp `.docx` kết quả trên cả Word Desktop và Word Online để đảm bảo bóng hiển thị nhất quán.

---

## Kết Luận

Chúng ta vừa mới khám phá **cách đặt bóng** cho một hình dạng bằng C#. Bằng cách làm theo tám bước trên, bạn có thể **thêm bóng cho hình dạng**, **đặt màu bóng**, và **tùy chỉnh bóng hình** để phù hợp với bất kỳ ngôn ngữ thiết kế nào. Ví dụ này độc lập, chạy ngay, và cung cấp nền tảng vững chắc để mở rộng logic sang nhiều hình, màu động, hoặc thậm chí các tham số do người dùng định nghĩa.

Sẵn sàng cho thử thách tiếp theo? Hãy thử kết hợp kỹ thuật này với **xoay hình**, hoặc tạo một báo cáo toàn bộ nơi mỗi biểu đồ đều có bóng thương hiệu riêng. Khả năng là vô hạn, và đoạn mã bạn vừa học là một bệ phóng hoàn hảo.

Nếu bạn thấy hướng dẫn này hữu ích, hãy sao sao lưu repository, để lại bình luận, hoặc chia sẻ mẹo tinh chỉnh bóng của bạn bên dưới. Chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}