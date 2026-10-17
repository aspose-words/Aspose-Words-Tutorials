---
category: general
date: 2026-04-10
description: cách đặt bóng cho hình dạng trong C# – tìm hiểu cách áp dụng bóng đổ,
  thay đổi độ trong suốt, điều chỉnh độ mờ và thêm bóng cho hình dạng bằng Aspose.Words.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: vi
og_description: cách đặt bóng cho hình dạng trong C# – hướng dẫn này chỉ cách áp dụng
  bóng đổ, thay đổi độ trong suốt, điều chỉnh độ mờ và thêm bóng cho hình dạng với
  các ví dụ mã rõ ràng.
og_title: Cách đặt bóng cho một hình dạng trong C# – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Document Automation
title: Cách đặt bóng cho một hình dạng trong C# – hướng dẫn từng bước
url: /vi/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cách đặt bóng cho một hình dạng trong C# – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi **cách đặt bóng** cho một hình dạng khi bạn đang xây dựng tài liệu Word một cách lập trình không? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi họ cần một bóng đổ nhẹ cho hộp văn bản, logo, hoặc hộp chú thích, và tài liệu API có vẻ hơi thiếu.  

Trong tutorial này chúng ta sẽ đi qua toàn bộ quy trình: từ việc tải một tệp `.docx`, lấy `Shape` đầu tiên, đến việc áp dụng bóng đổ, điều chỉnh độ trong suốt, thay đổi bán kính mờ, và cuối cùng định vị nó một cách chính xác. Khi kết thúc, bạn sẽ có một đoạn mã có thể tái sử dụng, hoạt động với Aspose.Words .NET 2023 hoặc mới hơn, và bạn sẽ hiểu *tại sao* mỗi thuộc tính lại quan trọng.

## Những gì bạn cần

- **Aspose.Words for .NET** (gói NuGet `Aspose.Words`) – thư viện cung cấp các lớp `Document`, `Shape`, và `ShadowFormat`.  
- **.NET 6+** (hoặc .NET Framework 4.7.2) – bất kỳ runtime hiện đại nào cũng được.  
- Một tệp Word đơn giản (`input.docx`) đã chứa ít nhất một shape, chẳng hạn như một textbox.  
- Visual Studio, VS Code, hoặc IDE yêu thích của bạn.

Đó là tất cả. Không cần công cụ bên thứ ba, không cần COM interop, chỉ cần C# thuần.

![ví dụ cách đặt bóng](image-placeholder.png){:alt="cách đặt bóng trên một hình dạng trong tài liệu Word"}

## Cách đặt bóng – Tổng quan

Ý tưởng cốt lõi đằng sau **cách đặt bóng** là thao tác với đối tượng `ShadowFormat` nằm trong một `Shape`. Hãy nghĩ về `ShadowFormat` như một “bảng kiểu” thu nhỏ cho chính bóng: nó cho trình vẽ biết bóng có hiển thị hay không, màu nào, độ trong suốt, mức độ mờ, và vị trí tương đối so với shape.  

Dưới đây là chương trình *đầy đủ* có thể chạy được. Bạn có thể sao chép‑dán vào một ứng dụng console, nhấn **F5**, và xem bóng xuất hiện trong tệp `output.docx` đã lưu.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Tại sao các thiết lập này lại quan trọng

- **Visible** – Nếu không bật cờ này, tất cả các thuộc tính khác sẽ bị bỏ qua.  
- **Color** – Màu xám đậm mô phỏng bóng đổ UI tiêu chuẩn; bạn có thể thay bằng bất kỳ `Color` nào.  
- **Transparency** – 0.3 tạo cảm giác *mềm mại* trong khi vẫn giữ shape dễ đọc.  
- **Size** – Kiểm soát độ mờ; giá trị 6 thường đủ cho cảm giác chuyên nghiệp.  
- **Distance & Angle** – Cùng nhau chúng định nghĩa *offset*; 2 pts ở 45° tạo ra bóng chéo nhẹ.

Đó là bản chất của **cách đặt bóng**. Tiếp theo, chúng ta sẽ phân tích từng phần để bạn có thể **áp dụng bóng đổ**, **thay đổi độ trong suốt**, **điều chỉnh độ mờ**, và **thêm bóng cho shape** một cách riêng lẻ.

---

## Áp dụng bóng đổ cho một hình dạng

Khi mọi người hỏi “làm sao tôi **áp dụng bóng đổ** trong C#?”, họ thường chỉ cần bật chế độ hiển thị và một màu. Đoạn mã sau tách riêng hai dòng này:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro tip:** Nếu bạn đang nhắm tới các phiên bản Word cũ hơn (2003‑2007), hãy dùng các màu chuẩn. Một số giá trị ARGB kỳ lạ có thể bị bộ render legacy bỏ qua.

---

## Cách thay đổi độ trong suốt của bóng

Độ trong suốt được biểu thị dưới dạng **float từ 0 đến 1**. Giá trị **0** nghĩa là bóng hoàn toàn đục; **1** làm bóng trở nên vô hình. Hầu hết các nhà thiết kế thường chọn khoảng **0.2‑0.4** để có vẻ tự nhiên.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Trường hợp đặc biệt

- **Negative values** – Aspose.Words sẽ ép chúng về 0, nhưng tốt hơn nên kiểm tra đầu vào.  
- **Values > 1** – Được ép về 1, thực chất ẩn bóng.

Nếu bạn cần cho người dùng chọn phần trăm, hãy chuyển đổi trước:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Cách điều chỉnh độ mờ (Kích thước) của bóng

Thuộc tính **Size** kiểm soát bán kính mờ. Số lớn hơn tạo ra bóng mềm hơn, lan tỏa hơn. Đơn vị đo là điểm (pt), không phải pixel.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Khi nào nên dùng độ mờ nhỏ vs. lớn

- **Small blur (2‑4 pt)** – Thích hợp cho các callout kiểu UI muốn cạnh sắc nét.  
- **Large blur (8‑12 pt)** – Thích hợp cho báo cáo in hoặc khi shape cách nền xa.

---

## Thêm bóng cho hình dạng – Vị trí và hướng

Phần cuối cùng của **thêm bóng cho shape** là offset. Hai thuộc tính làm việc cùng nhau:

| Thuộc tính | Ý nghĩa |
|------------|----------|
| **Distance** | Khoảng cách bóng cách hình dạng (đơn vị điểm). |
| **Angle**    | Hướng của offset (0° = phải, 90° = xuống, 180° = trái, 270° = lên). |

Ví dụ tạo một bóng nhẹ ở góc dưới‑phải:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Bạn có thể thử nghiệm các góc để mô phỏng ánh sáng đến từ các nguồn khác nhau. Một mẹo phổ biến là cho người dùng chọn “nguồn sáng” từ dropdown và ánh xạ nó thành giá trị góc.

---

## Ví dụ hoàn chỉnh (Tất cả các bước kết hợp)

Dưới đây là cùng một chương trình như trên, nhưng có **bình luận bổ sung** giúp logic trở nên trong suốt. Sao chép vào `Program.cs` và chạy; tệp đầu ra sẽ chứa một textbox với bóng được tinh chỉnh hoàn hảo.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Kết quả mong đợi:** Mở `output.docx`. Textbox đầu tiên sẽ hiển thị bóng màu xám đậm, trong suốt 30 %, hơi mờ (size = 6) và offset 2 pt ở góc 45°. Hiệu ứng nhẹ nhàng nhưng đáng chú ý — chính xác những gì hầu hết các nhà thiết kế UI mong muốn.

---

## Câu hỏi thường gặp & Lưu ý

- **“Điều này có hoạt động với hình ảnh không?”**  
  Có. Bất kỳ `Shape` nào — dù là textbox, picture, hay auto‑shape — đều có `ShadowFormat`. Chỉ cần thay thế logic lấy shape bằng chỉ mục hoặc tên phù hợp.

- **“Nếu tài liệu có nhiều shape thì sao?”**  
  Duyệt qua `doc.GetChildNodes(NodeType.Shape, true)` và áp dụng cùng một cài đặt cho mỗi shape. Bạn cũng có thể lọc bằng `shape.Name` hoặc `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}