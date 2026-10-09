---
category: general
date: 2026-03-19
description: Tạo tài liệu Word trong C# bằng Aspose.Words, học cách thêm hình dạng,
  thêm hình chữ nhật, áp dụng bóng đổ và lưu tài liệu dưới dạng docx trong vài phút.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: vi
og_description: Tạo tài liệu Word bằng Aspose.Words, thêm hình chữ nhật, áp dụng bóng
  đổ bên ngoài và lưu tài liệu dưới dạng docx. Hướng dẫn từng bước.
og_title: Tạo tài liệu Word – Thêm hình chữ nhật và bóng
tags:
- Aspose.Words
- C#
- Document Automation
title: Tạo tài liệu Word – Cách thêm hình chữ nhật và bóng
url: /vi/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word – Cách Thêm Hình Chữ Nhật và Đổ Bóng

Bạn đã bao giờ cần **create word document** một cách lập trình và tự hỏi nên bắt đầu từ đâu chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp cùng một rào cản khi họ lần đầu cố gắng tạo một tệp .docx chứa đồ họa tùy chỉnh. Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình — cách thêm shape, cụ thể là **add rectangle shape**, tạo cho nó một **add shadow to shape** phong cách, và cuối cùng **save document as docx**.  

Kết thúc hướng dẫn, bạn sẽ có một đoạn mã C# sẵn sàng sử dụng mà có thể chèn vào bất kỳ dự án .NET nào. Không có những tham chiếu mơ hồ, chỉ có một ví dụ hoàn chỉnh, có thể chạy được.  

## Yêu cầu trước

- .NET 6.0 hoặc cao hơn (mã cũng hoạt động với .NET Framework).  
- Aspose.Words for .NET đã được cài đặt (gói NuGet `Aspose.Words`).  
- Hiểu biết cơ bản về cú pháp C# — không cần kiến thức phức tạp.  

Nếu bạn chưa có thư viện, chạy:

```bash
dotnet add package Aspose.Words
```

Đó là tất cả — không cần SDK bổ sung, không cần COM interop, chỉ một tham chiếu NuGet duy nhất.

---

## Bước 1: Tạo tài liệu Word (Mục tiêu chính)

Điều đầu tiên chúng ta cần là một canvas sạch sẽ. Hãy nghĩ lớp `Document` như một trang trắng trong Microsoft Word; nó chứa các section, paragraph và mọi thứ khác bạn sẽ thêm sau.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Tại sao bắt đầu bằng một `Document` trống? Bởi vì nó đảm bảo không có định dạng ẩn nào lén vào từ mẫu. Theo kinh nghiệm của tôi, bắt đầu từ đầu giúp tránh những thay đổi bố cục bí ẩn khi bạn chèn shape sau này.

---

## Bước 2: Chèn hình chữ nhật – Thêm yếu tố trực quan

Bây giờ chúng ta đã có tài liệu, hãy **add rectangle shape** vào đoạn văn đầu tiên. Đối tượng `Shape` rất linh hoạt; bạn có thể chọn `ShapeType.Rectangle`, `Ellipse` hoặc thậm chí các bản vẽ tùy chỉnh. Đây là đoạn mã tối thiểu:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Điều gì đang diễn ra phía sau?**  
- `ShapeType.Rectangle` cho Aspose biết chúng ta muốn một hộp đơn giản.  
- `WrapType.Inline` đảm bảo hình chữ nhật di chuyển cùng luồng văn bản, thường là điều bạn mong đợi trong một kịch bản xử lý văn bản.  
- Bằng cách thêm vào `FirstParagraph`, chúng ta tránh việc phải chèn một đoạn văn mới thủ công; Aspose sẽ tự tạo một đoạn nếu tài liệu thực sự trống.

> **Mẹo chuyên nghiệp:** Nếu bạn muốn shape nằm *phía sau* văn bản, chuyển `WrapType` thành `WrapType.Transparent`. Thay đổi nhỏ này có thể tạo ra sự khác biệt lớn về mặt hình ảnh.

---

## Bước 3: Áp dụng Đổ bóng ngoài – Nâng cao giao diện

Một hình chữ nhật phẳng là… thật sự phẳng. Thêm một **add shadow to shape** sẽ tạo độ sâu mà không cần hình ảnh bổ sung. `ShadowFormat` của Aspose biến việc này thành một dòng lệnh.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Tại sao lại dùng những giá trị cụ thể này?  
- **Blur** = `5.0` tạo cạnh mờ nhẹ, trông chuyên nghiệp trên hầu hết màn hình.  
- **Distance** = `3.0` và **Angle** = `45` tạo nguồn sáng tự nhiên từ góc trên‑trái, một quy ước thiết kế phổ biến.  
- **Color.Gray** hoạt động tốt trên cả giao diện sáng và tối; bạn có thể đổi thành `Color.Black` nếu cần độ tương phản mạnh hơn.

Nếu bạn cần một *inner* shadow (giống như nút chìm), chỉ cần đổi `ShadowType.OuterShadow` thành `ShadowType.InnerShadow`. Các thuộc tính khác vẫn áp dụng.

---

## Bước 4: Lưu tài liệu dưới dạng DOCX – Lưu trữ công việc của bạn

Mọi thứ thật thú vị, nhưng cuối cùng bạn sẽ muốn có một tệp trên đĩa. Bước **save document as docx** rất đơn giản:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Một vài lưu ý:  
- Enum `SaveFormat.Docx` đảm bảo định dạng Office Open XML hiện đại, tương thích với Word 2007+.  
- Nếu bạn muốn truyền tệp trực tiếp tới phản hồi web, thay đường dẫn tệp bằng một `MemoryStream` và ghi nó vào HTTP response.

Sau khi chạy mã, mở `ShadowedRectangle.docx` trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật màu xám với bóng mềm, nằm inline với đoạn văn đầu tiên — chính xác như chúng ta mong muốn.

---

## Cách Thêm Shape – Các phương pháp thay thế

Ví dụ trên sử dụng cách *inline*, nhưng đôi khi bạn muốn một shape nổi trên văn bản. Đó là lúc **how to add shape** với các kiểu bao bọc khác nhau trở nên hữu ích.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Ở đây chúng ta chuyển `WrapType` thành `Square` và căn giữa shape trên trang. Mẫu này hữu ích cho trang bìa hoặc banner trang trí. Hãy nhớ: các shape nổi sẽ làm tăng kích thước tệp một chút vì Word lưu trữ dữ liệu vị trí bổ sung.

---

## Kết quả mong đợi & Kiểm tra

Khi bạn mở tệp đã tạo, bạn sẽ thấy:

- Một đoạn văn duy nhất chứa một hình chữ nhật màu xám.  
- Hình chữ nhật có kích thước khoảng 2.8 × 1.4 inch.  
- Một bóng ngoài nhẹ được dịch sang phía dưới‑phải.  

Nếu shape xuất hiện *ngoài* đoạn văn, hãy kiểm tra lại `WrapType`. Nếu bóng quá mạnh, giảm giá trị `Blur` hoặc đổi `Color` sang màu nhạt hơn.

---

## Những lỗi thường gặp & Cách tránh

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| Shape biến mất sau khi lưu | `WrapType` được đặt thành `Inline` nhưng đoạn văn đã bị xóa | Đảm bảo đoạn văn tồn tại; sử dụng `doc.FirstSection.Body.FirstParagraph` để chắc chắn. |
| Bóng bị pixel hoá | Giá trị `Blur` quá thấp | Tăng `Blur` lên ít nhất `3.0` để có cạnh mượt. |
| Kích thước tệp tăng đáng kể | Thêm nhiều hình ảnh độ phân giải cao cùng với shape | Gọi `doc.RemoveUnusedResources()` trước khi lưu nếu đã thêm hình ảnh. |
| Màu không hiển thị trong chế độ tối | Dùng màu tối cho shape | Chọn màu tương phản (ví dụ `Color.White`) để dễ nhìn hơn. |

---

## Ví dụ đầy đủ hoạt động

Dưới đây là đoạn mã hoàn chỉnh, có thể sao chép‑dán, tích hợp vào bất kỳ ứng dụng console nào.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Giải thích từng khối** được chèn dưới dạng comment, đáp ứng cả độc giả SEO và các trợ lý AI thích câu trả lời tự chứa.

---

## Kết luận

Chúng ta vừa **create word document** từ đầu, học **how to add shape**, cụ thể là **add rectangle shape**, thêm cho nó một **add shadow to shape**, và cuối cùng **save document as docx**. Các bước đơn giản, mã ngắn gọn, và kết quả trông chuyên nghiệp.  

Nếu bạn muốn tiến xa hơn, hãy thử thay hình chữ nhật bằng một hình ảnh tùy chỉnh, thử nghiệm các màu bóng khác nhau, hoặc tạo một báo cáo đầy đủ với nhiều section có shape. API Aspose.Words đủ linh hoạt để xử lý mọi thứ từ hoá đơn tới brochure marketing.

Có câu hỏi về các loại shape khác hoặc cần hỗ trợ tích hợp vào dịch vụ ASP.NET Core? Hãy để lại bình luận bên dưới, chúc bạn lập trình vui vẻ! 

![create word document with rectangle shape and shadow](placeholder-image.png "create word document with rectangle shape and shadow

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}