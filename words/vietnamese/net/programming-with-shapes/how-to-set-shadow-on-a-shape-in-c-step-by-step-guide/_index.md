---
category: general
date: 2026-03-28
description: Cách thiết lập bóng cho một hình dạng trong C# với Aspose.Words – thêm
  bóng vào hình, áp dụng bóng và tùy chỉnh giao diện.
draft: false
keywords:
- how to set shadow
- add shadow to shape
- apply shadow to shape
- how to add shadow
language: vi
og_description: Cách đặt bóng cho một hình dạng trong C# nhanh chóng. Học cách thêm
  bóng vào hình dạng, áp dụng bóng và điều chỉnh độ mờ, khoảng cách và góc.
og_title: Cách Đặt Bóng Cho Hình Dạng Trong C# – Hướng Dẫn Toàn Diện
tags:
- Aspose.Words
- C#
- Document Automation
- Graphics
title: Cách Thiết Lập Bóng Đổ cho Hình Dạng trong C# – Hướng Dẫn Từng Bước
url: /vi/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Đặt Bóng Đổ cho Hình Dạng trong C# – Hướng Dẫn Lập Trình Toàn Diện

Bạn đã bao giờ tự hỏi **cách đặt bóng đổ** cho một hình dạng khi bạn đang tạo tài liệu Word một cách lập trình chưa? Bạn không phải là người duy nhất. Trong nhiều báo cáo, bản trình bày hoặc tờ rơi, một bóng đổ nhẹ nhàng có thể làm cho đồ họa nổi bật mà không trông rẻ tiền. Tin tốt? Với Aspose.Words for .NET, bạn có thể thêm bóng đổ vào hình dạng chỉ trong vài dòng mã.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình: tải một DOCX, lấy hình dạng đầu tiên, và sau đó **áp dụng bóng đổ cho hình dạng** — bao gồm màu sắc, độ mờ, khoảng cách và góc. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy mà bạn có thể chèn vào bất kỳ dự án C# nào. Không cần thư viện bổ sung, không có phép thuật ẩn.

## Những Gì Bạn Cần

- **Aspose.Words for .NET** (phiên bản 23.9 hoặc mới hơn) – thư viện giúp việc thao tác Word trở nên dễ dàng.  
- Môi trường phát triển .NET (Visual Studio 2022, Rider, hoặc CLI).  
- Một tệp DOCX mẫu đã chứa ít nhất một hình dạng (hình chữ nhật, ảnh, hoặc SmartArt đều được).  

Nếu bạn thiếu bất kỳ mục nào, hãy tải gói NuGet bằng `Install-Package Aspose.Words` và tạo một tệp Word đơn giản với một hình dạng được chèn thủ công—chỉ để minh họa.

## Bước 1: Tải Tài Liệu (Chuẩn Bị Thêm Bóng Đổ)

Điều đầu tiên là mở tệp nguồn. Đây là nơi thao tác **thêm bóng đổ vào hình dạng** sẽ bắt đầu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class ShadowDemo
{
    static void Main()
    {
        // Load the DOCX that holds the shape you want to enhance
        Document doc = new Document("input.docx");
```

> **Tại sao điều này quan trọng:** Việc tải tài liệu cung cấp cho bạn một đối tượng `Document` sở hữu tất cả các nút, bao gồm các hình dạng. Nếu không có nó, sẽ không có gì để chỉnh sửa.

## Bước 2: Lấy Hình Dạng Mục Tiêu (Chọn Đúng Hình)

Tiếp theo chúng ta xác định hình dạng mà chúng ta muốn định dạng. Trong ví dụ này, chúng ta lấy hình dạng đầu tiên trong đoạn đầu tiên, nhưng bạn có thể điều chỉnh truy vấn cho bất kỳ bộ sưu tập nút nào.

```csharp
        // Grab the first shape inside the first paragraph of the first section
        Shape targetShape = doc.FirstSection.Body.FirstParagraph
            .GetChildNodes(NodeType.Shape, true)[0] as Shape;

        if (targetShape == null)
        {
            Console.WriteLine("No shape found – check your input file.");
            return;
        }
```

> **Mẹo chuyên nghiệp:** `GetChildNodes(NodeType.Shape, true)` duyệt cây con một cách đệ quy, đảm bảo bạn không bỏ lỡ các hình dạng lồng nhau như WordArt.

## Bước 3: Truy Cập Đối Tượng Định Dạng Bóng Đổ (Nơi Phép Thuật Xảy Ra)

Mỗi `Shape` đều cung cấp thuộc tính `ShadowFormat`. Đối tượng này điều khiển khả năng hiển thị, màu sắc, độ mờ, khoảng cách và góc—tất cả các tham số bạn cần để **áp dụng bóng đổ cho hình dạng**.

```csharp
        // The ShadowFormat object holds all shadow‑related settings
        ShadowFormat shadow = targetShape.ShadowFormat;
```

> **Tại sao chúng ta dùng `ShadowFormat`:** Nó trừu tượng hoá đại diện XML bên dưới, cho phép bạn điều chỉnh bóng đổ mà không cần làm việc trực tiếp với OpenXML thô.

## Bước 4: Đặt Bóng Đổ Thành Hiện Thị và Chọn Màu (Thêm Bóng Đổ vào Hình Dạng)

Bóng đổ sẽ không xuất hiện cho đến khi bạn đặt `Visible` thành `true`. Sau đó, bạn có thể chọn bất kỳ `System.Drawing.Color` nào. Ở đây chúng tôi sử dụng màu xám trung bình, nhưng bạn có thể tự do thử nghiệm.

```csharp
        // Turn the shadow on and give it a subtle gray tone
        shadow.Visible = true;
        shadow.Color = Color.FromArgb(80, 80, 80);   // dark gray
```

> **Sai lầm phổ biến:** Quên bật `Visible` sẽ dẫn đến lỗi im lặng—hình dạng của bạn không thay đổi dù bạn đã thiết lập các thuộc tính khác.

## Bước 5: Cấu Hình Ngoại Hình – Độ Mờ, Khoảng Cách và Góc (Tinh Chỉnh Hiệu Ứng)

Bây giờ chúng ta định hình ảnh hưởng trực quan. `BlurRadius` làm mềm các cạnh, `Distance` đẩy bóng ra xa hình dạng, và `Angle` xác định hướng nguồn sáng.

```csharp
        // Adjust how the shadow looks
        shadow.BlurRadius = 5.0;   // in points – higher = softer
        shadow.Distance   = 3.0;   // how far the shadow is offset
        shadow.Angle      = 45.0;  // degrees clockwise from the horizontal
```

> **Trường hợp đặc biệt:** Nếu bạn đặt khoảng cách âm, bóng sẽ xuất hiện *bên trong* hình dạng, điều này có thể hữu ích cho hiệu ứng nổi.

## Bước 6: Lưu Tài Liệu Đã Cập Nhật (Xem Kết Quả)

Cuối cùng, ghi các thay đổi trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc tạo một tệp mới.

```csharp
        // Persist the changes – you’ll see the shadow in Word or any viewer
        doc.Save("output-with-shadow.docx");
        Console.WriteLine("Shadow applied successfully! Check output-with-shadow.docx");
    }
}
```

Chạy chương trình sẽ tạo ra `output-with-shadow.docx`. Mở nó trong Microsoft Word, và bạn sẽ thấy hình dạng đã chọn hiện có một bóng đổ màu xám nhẹ, nghiêng 45°, mờ 5 pts và dịch chuyển 3 pts.

![Sơ đồ hiển thị bóng đổ trên một hình dạng](https://example.com/images/shadow-diagram.png "Sơ đồ hiển thị bóng đổ trên một hình dạng")

*Văn bản thay thế: Sơ đồ hiển thị bóng đổ trên một hình dạng* – hình ảnh này minh họa hiệu ứng trước và sau.

## Cách Thêm Bóng Đổ – Các Biến Thể Thông Thường và Trường Hợp Đặc Biệt

Mặc dù các bước cơ bản khá đơn giản, các tình huống thực tế thường yêu cầu điều chỉnh. Dưới đây là một vài tình huống “nếu‑thì” bạn có thể gặp.

### 1. Nhiều Hình Dạng, Bóng Đổ Khác Nhau

Nếu tài liệu của bạn chứa nhiều đồ họa, hãy lặp qua bộ sưu tập hình dạng và gán các cài đặt bóng đổ độc đáo cho mỗi hình.

```csharp
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            ShadowFormat sf = shp.ShadowFormat;
            sf.Visible = true;
            sf.Color = Color.FromArgb(100, 100, 150); // bluish tint
            sf.BlurRadius = 3.0;
            sf.Distance = 2.0;
            sf.Angle = 30.0;
        }
```

### 2. Bóng Đổ Trong Suốt

Aspose.Words cho phép bạn đặt kênh alpha qua `Color.FromArgb(alpha, r, g, b)`. Sử dụng alpha thấp (ví dụ, 50) để tạo hiệu ứng nhẹ, bán trong suốt.

```csharp
        shadow.Color = Color.FromArgb(50, 0, 0, 0); // 20% opacity black
```

### 3. Xóa Bóng Đổ

Đôi khi bạn cần tắt bóng đổ sau khi đã áp dụng. Chỉ cần đặt `Visible` thành `false`.

```csharp
        shadow.Visible = false;
```

### 4. Vấn Đề Tương Thích

Các tính năng bóng đổ được sử dụng ở đây được hỗ trợ trong Word 2007 + (định dạng DOCX). Nếu bạn nhắm tới định dạng nhị phân `.doc` cũ hơn, bóng đổ có thể bị bỏ qua vì định dạng này thiếu các phần tử XML cần thiết. Trong những trường hợp đó, hãy cân nhắc lưu dưới dạng DOCX hoặc sử dụng một dấu hiệu trực quan thay thế.

## Tóm Tắt: Những Gì Chúng Ta Đã Hoàn Thành

- **Đã tải** một DOCX bằng Aspose.Words.  
- **Đã lấy** hình dạng đầu tiên từ tài liệu.  
- **Đã truy cập** đối tượng `ShadowFormat` của nó.  
- **Đã bật** bóng đổ, đặt màu, bán kính mờ, khoảng cách và góc.  
- **Đã lưu** một tệp mới hiển thị rõ ràng hiệu ứng.  

Tất cả các bước này cùng nhau trả lời câu hỏi **cách đặt bóng đổ** trên một hình dạng, đồng thời cho bạn thấy cách **thêm bóng đổ vào hình dạng**, **áp dụng bóng đổ cho hình dạng**, và thậm chí **cách thêm bóng đổ** trong các kịch bản phức tạp hơn.

## Các Bước Tiếp Theo và Chủ Đề Liên Quan

Bây giờ khi bạn đã thành thạo việc tạo kiểu bóng đổ, bạn có thể muốn khám phá:

- **Đổ màu gradient** cho hình dạng (`Shape.FillFormat.GradientFill`).  
- **Hiệu ứng văn bản** như phát sáng hoặc phản chiếu (`TextEffect`).  
- **Chèn hình dạng mới bằng lập trình** (`doc.FirstSection.Body.AppendChild(new Shape(...))`).  
- **Xuất ra PDF** trong khi giữ nguyên bóng đổ (`doc.Save("output.pdf")`).  

Mỗi chủ đề này dựa trên các nguyên tắc mô hình đối tượng mà chúng ta đã sử dụng, vì vậy bạn sẽ cảm thấy quen thuộc.

---

*Chúc lập trình vui vẻ! Nếu gặp khó khăn, hãy để lại bình luận bên dưới hoặc xem tài liệu API của Aspose.Words để hiểu sâu hơn.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}