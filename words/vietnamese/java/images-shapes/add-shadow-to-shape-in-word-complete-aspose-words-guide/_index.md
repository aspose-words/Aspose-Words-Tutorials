---
category: general
date: 2026-02-18
description: Thêm bóng cho hình dạng trong Word bằng Aspose.Words. Tìm hiểu cách thay
  đổi màu bóng trong Word, thiết lập độ dịch chuyển, độ mờ và độ trong suốt chỉ trong
  vài dòng.
draft: false
keywords:
- add shadow to shape
- how to change shadow color in word
language: vi
og_description: Thêm bóng cho hình dạng trong Word bằng Aspose.Words. Hướng dẫn này
  cho thấy cách thay đổi màu bóng trong Word, điều chỉnh độ mờ, độ lệch và độ trong
  suốt.
og_title: Thêm bóng cho hình dạng trong Word – Hướng dẫn đầy đủ Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Thêm bóng cho hình dạng trong Word – Hướng dẫn đầy đủ Aspose.Words
url: /vi/java/images-shapes/add-shadow-to-shape-in-word-complete-aspose-words-guide/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thêm bóng cho hình dạng trong Word – Hướng dẫn đầy đủ Aspose.Words

Bạn đã bao giờ cần **thêm bóng cho hình dạng** trong tài liệu Word nhưng không biết bắt đầu từ đâu chưa? Bạn không phải là người duy nhất—các nhà phát triển thường hỏi *cách thay đổi màu bóng trong Word* khi họ muốn có hiệu ứng hình ảnh thêm.

Trong tutorial này chúng ta sẽ đi qua một ví dụ thực tế sử dụng thư viện Aspose.Words cho .NET. Khi kết thúc, bạn sẽ có một chương trình sẵn sàng chạy, tải một file DOCX, lấy hình dạng đầu tiên và áp dụng bóng màu xanh, bán trong suốt với độ mờ và độ lệch tùy chỉnh. Không có các “xem tài liệu” mơ hồ—chỉ có một giải pháp hoàn chỉnh, copy‑paste.

## Những gì bạn sẽ học

- Cách tải tài liệu Word và xác định nút hình dạng.  
- Các lời gọi API chính xác để **thêm bóng cho hình dạng**.  
- Cách **thay đổi màu bóng trong Word**, đặt bán kính mờ, độ lệch X/Y và độ trong suốt.  
- Mẹo xử lý nhiều hình dạng, bóng đã tồn tại và các phiên bản Word.  

### Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã có thể biên dịch với các phiên bản cũ hơn, nhưng .NET 6 được khuyến nghị).  
- Gói NuGet Aspose.Words cho .NET (`Install-Package Aspose.Words`).  
- Kiến thức cơ bản về C# và mô hình đối tượng Word.  

Nếu bạn đã có những thứ trên, hãy bắt đầu ngay.

---

## Bước 1 – Tải tài liệu Word chứa hình dạng

Đầu tiên chúng ta tạo một thể hiện `Document` trỏ tới file nguồn của chúng ta. Đường dẫn có thể là tuyệt đối hoặc tương đối so với file thực thi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the DOCX that already contains at least one shape.
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Why this matters:** Lớp `Document` là điểm vào cho mọi thao tác Aspose.Words. Tải file một lần giúp giảm sử dụng bộ nhớ và cho phép truy vấn cây node một cách hiệu quả.

## Bước 2 – Lấy nút hình dạng đầu tiên

Các hình dạng tồn tại trong cấu trúc cây node của tài liệu. Chúng ta yêu cầu node đầu tiên có kiểu `NodeType.SHAPE`. Tham số `true` có nghĩa là “tìm kiếm sâu”.

```csharp
// Grab the first Shape object in the document (depth‑first search).
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    System.Console.WriteLine("No shape found in the document.");
    return;
}
```

> **Pro tip:** Nếu bạn cần nhắm mục tiêu một hình dạng cụ thể, hãy lọc bằng `firstShape.Name` hoặc `firstShape.AlternativeText` thay vì luôn lấy phần tử đầu tiên.

## Bước 3 – Lấy đối tượng bóng liên kết với hình dạng

Mỗi `Shape` đều có thuộc tính `Shadow` có thể là `null` nếu chưa có bóng nào. Truy cập thuộc tính này sẽ cho chúng ta một đối tượng `Shadow` có thể thay đổi.

```csharp
// The Shadow object is automatically created if it doesn't exist.
Shadow shapeShadow = firstShape.Shadow;
```

> **Edge case:** Các file Word cũ (trước 2007) đôi khi lưu bóng theo cách khác. Aspose.Words chuẩn hoá điều này, vì vậy cùng một API hoạt động trên DOC, DOCX và thậm chí RTF.

## Bước 4 – Xác định bán kính làm mờ (đơn vị điểm)

Bán kính làm mờ `5.0` điểm tạo ra một cạnh mềm mà không bị mờ nhạt.

```csharp
shapeShadow.BlurRadius = 5.0;   // points
```

## Bước 5 – Đặt độ lệch ngang và dọc

Độ lệch di chuyển bóng so với hình dạng. Giá trị dương dịch sang phải/dưới; giá trị âm dịch sang trái/lên.

```csharp
shapeShadow.OffsetX = 3.0;      // move right 3 points
shapeShadow.OffsetY = 3.0;      // move down 3 points
```

## Bước 6 – Chọn màu xanh cho bóng  

Ở đây chúng ta minh họa **cách thay đổi màu bóng trong Word** bằng cách sử dụng `System.Drawing.Color`.

```csharp
shapeShadow.Color = Color.Blue;   // any System.Drawing.Color works
```

> **Why color matters:** Bóng màu xanh có thể tạo cảm giác mát mẻ, doanh nghiệp, trong khi màu xám đậm thì trung tính hơn. Hãy chọn màu phù hợp với thương hiệu của bạn.

## Bước 7 – Điều chỉnh độ mờ của bóng

Độ trong suốt dao động từ `0.0` (vô hình) đến `1.0` (đầy đủ). Chúng ta sẽ dùng `0.6` cho hiệu ứng nhẹ nhàng.

```csharp
shapeShadow.Opacity = 0.6;   // 60% opacity
```

## Bước 8 – Lưu tài liệu đã chỉnh sửa

Cuối cùng, ghi các thay đổi trở lại đĩa. Bạn có thể ghi đè lên file gốc hoặc tạo file mới.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
System.Console.WriteLine("Shadow applied and document saved.");
```

### Ví dụ hoạt động đầy đủ

Kết hợp tất cả lại, đây là chương trình hoàn chỉnh mà bạn có thể sao chép, dán và chạy:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class AddShadowToShapeDemo
{
    static void Main()
    {
        // 1️⃣ Load the document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Find the first shape
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (firstShape == null)
        {
            System.Console.WriteLine("No shape found in the document.");
            return;
        }

        // 3️⃣ Get (or create) the shadow object
        Shadow shapeShadow = firstShape.Shadow;

        // 4️⃣ Set blur radius
        shapeShadow.BlurRadius = 5.0;

        // 5️⃣ Set offsets
        shapeShadow.OffsetX = 3.0;
        shapeShadow.OffsetY = 3.0;

        // 6️⃣ Change shadow color (how to change shadow color in Word)
        shapeShadow.Color = Color.Blue;

        // 7️⃣ Set opacity
        shapeShadow.Opacity = 0.6;

        // 8️⃣ Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        System.Console.WriteLine("Shadow applied and document saved.");
    }
}
```

**Expected result:** Mở `output_with_shadow.docx` trong Microsoft Word. Hình dạng đầu tiên giờ hiển thị một bóng xanh mềm, dịch 3 pt sang phải và xuống, với độ mờ vừa phải và độ trong suốt 60 %.

---

## Xử lý nhiều hình dạng

Nếu tài liệu của bạn chứa nhiều đồ họa, hãy lặp qua chúng:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shp in shapes)
{
    // Apply the same shadow settings to each shape
    shp.Shadow.BlurRadius = 5.0;
    shp.Shadow.OffsetX = 3.0;
    shp.Shadow.OffsetY = 3.0;
    shp.Shadow.Color = Color.Blue;
    shp.Shadow.Opacity = 0.6;
}
```

> **Note:** Cách tiếp cận này ghi đè bất kỳ cấu hình bóng nào đã tồn tại. Nếu bạn cần giữ nguyên cài đặt gốc, hãy sao chép đối tượng `Shadow` trước.

## Những khó khăn thường gặp & Mẹo

| Pitfall | How to avoid it |
|---------|-----------------|
| **Null `Shape`** – tài liệu không có đồ họa. | Luôn kiểm tra `null` sau khi gọi `GetChild`. |
| **Shadow already exists** – bạn có thể vô tình ghi đè một kiểu tùy chỉnh. | Đọc các thuộc tính hiện tại của `shapeShadow` trước khi thay đổi chúng. |
| **Incorrect color space** – sử dụng `System.Drawing.Color` với phiên bản Word cũ có thể gây màu không mong muốn. | Dùng các màu tiêu chuẩn hoặc định nghĩa ARGB thủ công (`Color.FromArgb(255, 0, 0, 255)`). |
| **Performance hit on large docs** – lặp qua hàng ngàn node có thể chậm. | Sử dụng `doc.GetChildNodes(NodeType.Shape, false)` nếu bạn chỉ cần các shape cấp cao. |

## Nếu tôi cần hiệu ứng bóng khác?

- **Hard edges:** Đặt `BlurRadius = 0`.  
- **Larger offset:** Tăng `OffsetX`/`OffsetY` lên 10 pt hoặc hơn.  
- **Different opacity:** Dùng giá trị như `0.3` cho ánh sáng nhẹ hoặc `0.9` cho hiệu ứng đậm.  
- **Gradient shadows:** Aspose.Words không hỗ trợ bóng gradient trực tiếp; bạn cần chèn một hình ảnh đã được render sẵn hiệu ứng.

## Xác minh kết quả bằng chương trình

Đôi khi bạn muốn xác nhận các thiết lập bóng mà không mở Word:

```csharp
Shadow s = firstShape.Shadow;
System.Console.WriteLine($"Blur: {s.BlurRadius}, OffsetX: {s.OffsetX}, OffsetY: {s.OffsetY}, " +
                         $"Color: {s.Color}, Opacity: {s.Opacity}");
```

Nếu console in ra các số bạn đã đặt, bạn biết lời gọi API đã thành công.

## Kết luận

Chúng tôi đã chỉ ra **cách thêm bóng cho hình dạng** trong tài liệu Word bằng Aspose.Words, và trình bày **cách thay đổi màu bóng trong Word** cùng với độ mờ, độ lệch và độ trong suốt. Mã hoàn chỉnh, có thể chạy ở trên cho phép bạn nhanh chóng áp dụng bóng cho bất kỳ hình dạng nào, trong khi các mẹo bổ sung giúp bạn tránh các lỗi thường gặp.  

Sẵn sàng cho thử thách tiếp theo? Hãy thử áp dụng các màu khác nhau cho từng hình dạng, hoặc kết hợp bóng với phản chiếu để có hiệu ứng hình ảnh phong phú hơn. Bạn cũng có thể khám phá lớp `ShapeStyle` của Aspose.Words để điều chỉnh độ dày đường viền, mẫu nền hoặc quay 3‑D.  

Nếu bạn thấy hướng dẫn này hữu ích, hãy chia sẻ với đồng nghiệp, star repo Aspose.Words, hoặc để lại bình luận với các thử nghiệm của mình. Chúc lập trình vui vẻ!  

![Hình dạng Word với bóng xanh – ví dụ thêm bóng cho hình dạng](https://example.com/images/shape-shadow.png "ví dụ thêm bóng cho hình dạng")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}