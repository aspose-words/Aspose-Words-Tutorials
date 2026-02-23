---
category: general
date: 2026-02-23
description: Tạo tài liệu Word trống bằng C# và Aspose.Words. Học cách thêm hình chữ
  nhật, thêm hiệu ứng đổ bóng, và lưu tài liệu Word có hình dạng trong vài phút.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: vi
og_description: Tạo tài liệu Word trống nhanh chóng. Hướng dẫn này chỉ cách thêm hình
  chữ nhật, thêm bóng cho văn bản và lưu tài liệu Word có hình dạng bằng Aspose.Words.
og_title: Tạo tài liệu Word trống – Hướng dẫn đầy đủ C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Tạo tài liệu Word trống với Aspose.Words – Hướng dẫn từng bước
url: /vi/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống – Hướng dẫn đầy đủ C#

Bạn đã bao giờ tự hỏi cách **create blank word document** một cách lập trình mà không mở Microsoft Word chưa? Bạn không phải là người duy nhất. Trong nhiều dự án tự động hoá, chúng ta cần một tệp .docx mới, chèn một hình dạng vào, cho hình dạng đó một bóng đẹp, và sau đó **save word with shape** để sử dụng sau.  

Trong hướng dẫn này, chúng ta sẽ đi qua từng bước—bắt đầu từ một tài liệu trống, **adding a rectangle shape**, cấu hình hiệu ứng **add shadow word**, và cuối cùng lưu lại tệp. Khi kết thúc, bạn sẽ có một đoạn mã hoàn chỉnh, có thể chạy được mà bạn có thể dán vào bất kỳ ứng dụng console .NET nào. Không có bí ẩn, không có phần thiếu sót.

## Những gì bạn cần

- **Aspose.Words for .NET** (bất kỳ phiên bản mới nào, ví dụ, 24.10).  
- .NET 6 trở lên (mã hoạt động với .NET Framework 4.7+ cũng được).  
- Một IDE C# cơ bản—Visual Studio, Rider, hoặc thậm chí VS Code với phần mở rộng C#.  

Chỉ vậy thôi. Không cần gói NuGet bổ sung nào ngoài Aspose.Words, và không yêu cầu cài đặt Word.

---

## Bước 1: Tạo tài liệu Word trống

Điều đầu tiên bạn làm khi muốn **create blank word document** là khởi tạo lớp `Document`. Hãy nghĩ nó như một canvas sạch mà Aspose.Words cung cấp cho bạn.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Why this matters:** Đối tượng `Document` chứa tất cả các phần, đoạn văn và hình dạng. Bắt đầu với một thể hiện trống đảm bảo bạn kiểm soát mọi yếu tố được thêm vào sau này.

---

## Bước 2: Thêm hình dạng hình chữ nhật vào tài liệu

Bây giờ chúng ta đã có một tài liệu sạch, hãy **add rectangle shape**. Một hình chữ nhật là một `Shape` đơn giản với `ShapeType.Rectangle`. Tất nhiên bạn có thể chọn các loại khác, nhưng hình chữ nhật rất phù hợp cho mục đích minh họa.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Pro tip:** Nếu bạn bao giờ tự hỏi **how to add shape** không phải là hình chữ nhật, chỉ cần thay đổi `ShapeType.Rectangle` thành bất kỳ giá trị enum nào khác như `ShapeType.Ellipse` hoặc `ShapeType.Polygon`. Phần còn lại của mã vẫn giữ nguyên.

---

## Bước 3: Cấu hình bóng tùy chỉnh cho hình dạng

Một hình chữ nhật đơn giản trông hơi nhạt, vì vậy chúng ta sẽ **add shadow word** để làm nó nổi bật hơn. Aspose.Words cung cấp một đối tượng `ShadowFormat` với nhiều thuộc tính.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Why this matters:** Bóng tạo ra một cảm giác chiều sâu nhẹ nhàng, đặc biệt khi tài liệu được xem trên màn hình. Điều chỉnh `OffsetX`, `OffsetY`, và `BlurRadius` để phù hợp với ngôn ngữ thiết kế của bạn.

---

## Bước 4: Chèn hình dạng vào tài liệu

Khi hình dạng đã sẵn sàng, chúng ta cần đặt nó vào một vị trí nào đó. Điểm đơn giản nhất là đoạn văn đầu tiên của phần đầu tiên. Nếu tài liệu chưa có đoạn nào, Aspose sẽ tự động tạo một đoạn.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Edge case:** Nếu bạn dự định chèn hình dạng vào một vị trí cụ thể (ví dụ, sau một tiêu đề nhất định), hãy tìm `Paragraph` mục tiêu bằng `document.GetChildNodes(NodeType.Paragraph, true)` và sử dụng `InsertAfter` hoặc `InsertBefore` tương ứng.

---

## Bước 5: Lưu tài liệu Word với hình dạng

Cuối cùng, chúng ta **save word with shape** lên đĩa. Phương thức `Save` tự động xác định định dạng dựa trên phần mở rộng tệp.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **What you’ll see:** Mở `shadowedRectangle.docx` trong Word (hoặc bất kỳ trình xem tương thích nào) và bạn sẽ thấy một hình chữ nhật màu xám với bóng mềm nằm ở đầu trang đầu tiên.

---

## Ví dụ Hoạt động đầy đủ

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các chỉ thị using, chú thích, và các bước chính xác mà chúng ta đã thảo luận.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Chạy chương trình, điều hướng đến `YOUR_DIRECTORY`, và mở tệp `shadow.docx` đã tạo. Bạn sẽ thấy hình chữ nhật với bóng xám nhẹ—đúng như chúng ta mong muốn.

---

## Câu hỏi thường gặp & Mẹo

### Làm thế nào để thay đổi màu của hình dạng?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Chỉ cần đặt `FillColor` trước khi thêm hình dạng.

### Nếu tôi cần nhiều hình dạng trên cùng một trang thì sao?
Tạo các đối tượng `Shape` bổ sung và thêm mỗi cái vào cùng một đoạn hoặc vào các đoạn khác nhau. Bạn cũng có thể kiểm soát bố cục bằng cách sử dụng `WrapType` và `RelativeHorizontalPosition`.

### Tôi có thể xuất ra PDF đồng thời giữ bóng không?
Chắc chắn. Sử dụng `document.Save("output.pdf")`—Aspose.Words giữ nguyên hiệu ứng bóng trong quá trình chuyển đổi sang PDF.

### Điều này có hoạt động trên .NET Core không?
Có. Aspose.Words là đa nền tảng; cùng một đoạn mã chạy trên .NET Core, .NET 5+, và .NET Framework.

### Cách thêm hình dạng mà không có đoạn văn?
Bạn có thể thêm hình dạng trực tiếp vào một `Run` hoặc vào một `Story`. Để định vị chính xác hơn, đặt `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` và điều chỉnh các thuộc tính `Left`/`Top`.

---

## Kết quả hình ảnh

![Rectangle shape with gray shadow in a Word document – add shadow word example](https://example.com/placeholder-image.png "add shadow word example")

*Văn bản alt của hình ảnh bao gồm từ khóa phụ **add shadow word** để đáp ứng SEO.*

---

## Kết luận

Chúng ta vừa trình diễn cách **create blank word document**, **add rectangle shape**, áp dụng hiệu ứng **add shadow word**, và cuối cùng **save word with shape** bằng Aspose.Words cho .NET. Quy trình rất đơn giản: khởi tạo một `Document`, tạo một `Shape`, điều chỉnh `ShadowFormat` của nó, chèn vào, và gọi `Save`.  

Từ đây bạn có thể thử nghiệm—thử các loại hình dạng khác nhau, chơi với màu sắc, hoặc xếp chồng nhiều hình dạng. Nếu bạn cần hợp nhất tài liệu này với nội dung hiện có, chỉ cần tải tệp hiện có bằng `new Document("existing.docx")` và thực hiện các bước tương tự.  

Có thêm câu hỏi? Hãy để lại bình luận, và chúc bạn lập trình vui vẻ!

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}