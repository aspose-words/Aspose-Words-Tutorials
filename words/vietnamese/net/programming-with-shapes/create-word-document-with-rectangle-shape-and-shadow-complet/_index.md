---
category: general
date: 2026-01-02
description: Tạo tài liệu Word với một hình chữ nhật, đặt màu nền cho hình, và lưu
  tệp docx bằng Aspose.Words. Học cách tạo hình chữ nhật có bóng trong vài phút.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: vi
og_description: Tạo tài liệu Word với một hình chữ nhật tùy chỉnh, đặt màu nền, thêm
  bóng đổ và lưu dưới dạng DOCX. Mã đầy đủ và giải thích.
og_title: Tạo tài liệu Word với hình chữ nhật – Bước từng bước
tags:
- Aspose.Words
- C#
- Document Generation
title: Tạo tài liệu Word với hình chữ nhật và bóng – Hướng dẫn chi tiết
url: /vi/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Tài Liệu Word với Hình Chữ Nhật và Bóng – Hướng Dẫn Đầy Đủ

Bạn đã bao giờ tự hỏi làm sao **tạo tài liệu word** có chứa một hình chữ nhật được thiết kế đẹp mắt? Có thể bạn cần một chỗ giữ chỗ cho logo, một biểu ngữ màu, hoặc chỉ đơn giản là một chỉ dẫn trực quan trong báo cáo. Trong hướng dẫn này, chúng ta sẽ **thêm hình chữ nhật**, đặt màu nền, áp dụng một bóng nhẹ, và cuối cùng **lưu file docx** – tất cả đều bằng Aspose.Words cho .NET.

Bạn sẽ có một đoạn mã C# sẵn sàng chạy, giải thích rõ ràng từng dòng, và một vài mẹo có thể tái sử dụng trong dự án của mình. Không có phần thừa, chỉ có giải pháp thực tiễn để bạn copy‑paste.

## Những Điều Bạn Cần Có

- .NET 6 trở lên (mã cũng chạy trên .NET Framework)  
- Visual Studio 2022 (hoặc bất kỳ trình soạn thảo nào bạn thích)  
- Gói NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  

Nếu bạn đã có những thứ trên, tuyệt vời – hãy bắt đầu.

## Bước 1 – Khởi Tạo Tài Liệu Mới (Cách tạo word document)

Điều đầu tiên bạn cần làm là **tạo tài liệu word** trong bộ nhớ. Hãy tưởng tượng đây là một canvas trống mà bạn sẽ vẽ hình chữ nhật lên sau này.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Tại sao điều này quan trọng:** `Document` đại diện cho toàn bộ file DOCX, trong khi `DocumentBuilder` là một công cụ tiện lợi cho phép bạn chèn văn bản, bảng, hình ảnh và các hình dạng mà không cần thao tác trực tiếp với cây node bên dưới.

## Bước 2 – Chèn Hình Chữ Nhật (Thêm hình chữ nhật)

Bây giờ chúng ta sẽ **thêm hình chữ nhật** vào tài liệu. Phương thức `InsertShape` nhận loại hình và kích thước của nó tính bằng point (1 point = 1/72 inch).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Mẹo chuyên nghiệp:** Nếu bạn cần tạo một hình dạng khác (ellipse, triangle, …), chỉ cần thay `ShapeType.Rectangle` bằng giá trị enum mong muốn.

## Bước 3 – Cấu Hình Bóng (Đặt màu nền & bóng cho hình)

Bóng có thể làm cho một hình phẳng trông có chiều sâu hơn. Ở đây chúng ta bật bóng và tinh chỉnh ngoại hình của nó.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Tại sao lại dùng các giá trị này?** Bán kính mờ vừa phải và khoảng cách 5 point giúp bóng không lấn át hình, trong khi góc 45° mô phỏng nguồn sáng đến từ góc trên‑trái – một quy ước UI phổ biến.

## Bước 4 – Lưu Tài Liệu (Lưu file docx)

Cuối cùng, chúng ta **lưu file docx** lên đĩa. Hãy điều chỉnh đường dẫn cho phù hợp với môi trường của bạn.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Khi mở `ShadowDemo.docx` trong Word, bạn sẽ thấy một hình chữ nhật màu xanh nhạt với bóng xám mềm mại, giống như ảnh chụp màn hình dưới đây.

![Tạo Tài Liệu Word với hình chữ nhật và bóng](https://example.com/images/rectangle-shadow.png "Tạo Tài Liệu Word với hình chữ nhật và bóng")

*Văn bản thay thế cho ảnh:* **Tạo Tài Liệu Word** hiển thị một hình chữ nhật có bóng.

## Ví Dụ Đầy Đủ, Sẵn Sàng Chạy (Cách tạo hình chữ nhật và lưu)

Kết hợp mọi thứ lại, đây là chương trình hoàn chỉnh mà bạn có thể sao chép vào một ứng dụng console:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Kết Quả Mong Đợi

- Một file có tên **ShadowDemo.docx** xuất hiện trong thư mục đích.  
- Mở nó bằng Microsoft Word sẽ hiển thị một trang duy nhất với văn bản “Shadow Demo” tiếp theo là một hình chữ nhật màu xanh nhạt.  
- Hình chữ nhật tạo ra một bóng xám mềm mại với góc 45°, mang lại cảm giác 3‑D nhẹ.

## Các Câu Hỏi Thường Gặp & Trường Hợp Cạnh

### Nếu tôi cần kích thước khác thì sao?

Chỉ cần thay đổi các đối số `200, 100` trong `InsertShape`. Những con số này là chiều rộng và chiều cao tính bằng point. Đối với hình vuông, dùng các giá trị bằng nhau.

### Làm sao để bóng nổi bật hơn?

Tăng `BlurRadius` để làm viền mờ hơn, tăng `Distance` để đẩy bóng xa hơn, hoặc giảm `Transparency` (ví dụ `0.1`) để bóng tối hơn.

### Làm sao thêm viền quanh hình chữ nhật?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Có tương thích với các phiên bản cũ của Aspose.Words không?

Có. Lớp `ShadowFormat` đã tồn tại từ các bản phát hành đầu năm 2020. Nếu bạn đang dùng một phiên bản rất cũ, có thể cần nâng cấp để truy cập tất cả các thuộc tính.

## Mẹo & Những Sai Lầm Thường Gặp

- **Mẹo chuyên nghiệp:** Luôn giải phóng tài nguyên của các tài liệu lớn (`doc.Dispose()`) khi không còn dùng, đặc biệt trong các ứng dụng web, để giải phóng bộ nhớ native.  
- **Cảnh báo:** Sử dụng đường dẫn tương đối mà không có quyền phù hợp có thể gây ra `UnauthorizedAccessException`. Nên dùng đường dẫn tuyệt đối hoặc đảm bảo pool ứng dụng có quyền ghi.  
- **Nhớ rằng:** Thuộc tính `FillColor` chấp nhận bất kỳ `System.Drawing.Color` nào. Bạn có thể dùng `Color.FromArgb(255, 173, 216, 230)` cho một màu pastel tùy chỉnh.

## Bước Tiếp Theo

Bây giờ bạn đã biết cách **tạo tài liệu word**, **thêm hình chữ nhật**, **đặt màu nền cho hình**, và **lưu file docx**, hãy thử nghiệm thêm:

- Chèn nhiều hình và sắp xếp chúng bằng `RelativeHorizontalPosition` và `RelativeVerticalPosition`.  
- Kết hợp hình chữ nhật với văn bản bằng `Shape.TextBox` để tạo chú thích.  
- Xuất cùng một tài liệu sang PDF (`doc.Save("output.pdf")`) để phân phối.

Nếu bạn muốn khám phá đồ họa nâng cao hơn, hãy xem hỗ trợ **WordArt**, **biểu đồ**, và **hình ảnh nội tuyến** của Aspose.Words. Tất cả đều theo cùng một mẫu: tạo node, cấu hình thuộc tính, và lưu.

---

### TL;DR

- Dùng `Document` và `DocumentBuilder` để **tạo tài liệu word**.  
- Gọi `InsertShape(ShapeType.Rectangle, …)` để **thêm hình chữ nhật**.  
- Đặt `FillColor` cho màu nền mong muốn.  
- Bật `ShadowFormat` và tinh chỉnh các thuộc tính để có giao diện chuyên nghiệp.  
- Kết thúc bằng `document.Save("yourPath.docx")` để **lưu file docx**.

Chúc lập trình vui vẻ, và hãy làm cho các file Word của bạn trở nên phong cách hơn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}