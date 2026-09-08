---
category: general
date: 2026-09-08
description: Tạo hình chữ nhật trong tài liệu Word bằng C#. Học cách đặt kích thước
  hình, nhóm nhiều hình lại với nhau và tạo tài liệu Word trống một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: vi
lastmod: 2026-09-08
og_description: Tạo hình chữ nhật trong tài liệu Word bằng C#. Hướng dẫn này chỉ cách
  đặt kích thước hình, nhóm nhiều hình lại với nhau và tạo tài liệu Word trống một
  cách lập trình.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Tạo hình chữ nhật và nhóm các hình trong Word bằng C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo hình chữ nhật và nhóm các hình trong Word bằng C#
url: /vi/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật và nhóm các hình trong Word bằng C#

Nếu bạn cần **create rectangle shape** trong một tệp Word, hướng dẫn này cung cấp cho bạn một giải pháp hoàn chỉnh, sẵn sàng chạy. Bạn sẽ thấy cách thiết lập kích thước hình, nhóm nhiều hình, và tạo một tài liệu Word trống từ đầu — tất cả đều sử dụng thư viện Aspose.Words for .NET.

Làm việc với các tài liệu Word một cách lập trình thường cảm giác như phải cân bằng rất nhiều chi tiết nhỏ. Khi kết thúc hướng dẫn này, bạn sẽ có một phương thức duy nhất tạo ra tệp `.docx` chứa một hình chữ nhật và một hình ellipse được nhóm lại với nhau, sẵn sàng cho việc chỉnh sửa hoặc in ấn tiếp theo.

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
* Bản sao có giấy phép của **Aspose.Words for .NET** (bạn có thể dùng khóa đánh giá miễn phí)
* Một IDE như Visual Studio 2022 hoặc Visual Studio Code
* Kiến thức cơ bản về cú pháp C#

Không cần bất kỳ gói NuGet bổ sung nào ngoài `Aspose.Words`.

## Bước 1: Tạo tài liệu Word trống

Bước đầu tiên là tạo một tài liệu rỗng để chứa các hình. Điều này đáp ứng yêu cầu *create blank word document*.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Tạo một tài liệu trống giúp bạn có một canvas sạch sẽ. Đối tượng `Document` đại diện cho toàn bộ tệp `.docx`, và `FirstSection.Body.FirstParagraph` là vị trí chèn mặc định cho các nút mới.

## Bước 2: Tạo hình chữ nhật

Bây giờ bạn có thể thêm hình chữ nhật. Đây là nơi thực hiện thao tác **create rectangle shape**.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Việc đặt kích thước trực tiếp trả lời từ khóa **set shape size**. Tất cả các giá trị kích thước được biểu thị bằng điểm, cho phép kiểm soát chính xác cách hình xuất hiện trong tài liệu cuối cùng.

## Bước 3: Tạo hình bổ sung (ellipse)

Một trường hợp sử dụng điển hình là kết hợp nhiều hình. Ở đây chúng ta thêm một ellipse sẽ sau này chia sẻ cùng một container.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Cả hai hình vẫn độc lập tại thời điểm này. Bước tiếp theo sẽ cho thấy cách **group multiple shapes** lại với nhau.

## Bước 4: Nhóm các hình trong Word

Nhóm các hình cho phép bạn di chuyển, thay đổi kích thước hoặc định dạng chúng như một đơn vị duy nhất. Điều này đáp ứng các yêu cầu **group shapes in word** và **group multiple shapes**.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

Thuộc tính `GroupShape.Bounds` xác định hệ tọa độ cho các hình con. Bằng cách đặt hình chữ nhật và ellipse vào cùng một `GroupShape`, bạn có thể sau này di chuyển hoặc xoay chúng cùng nhau chỉ bằng một lệnh duy nhất.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Tệp sẽ chứa các hình đã được nhóm mà bạn vừa tạo.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Sau khi chạy chương trình, mở `GroupedShapes.docx` trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật và một ellipse được nhóm lại với nhau; việc chọn một hình cũng sẽ chọn hình còn lại, xác nhận việc nhóm đã thành công.

## Mã nguồn đầy đủ

Sao chép chương trình hoàn chỉnh dưới đây vào một dự án console‑app mới và chạy nó. Không cần mã bổ sung nào khác.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Kết quả mong đợi

Chạy chương trình sẽ tạo ra `GroupedShapes.docx`. Mở tệp trong Word sẽ hiển thị:

* Một **rectangle** (100 pt × 50 pt) với viền màu xanh và nền màu xám nhạt.
* Một **ellipse** (80 pt × 80 pt) với viền màu xanh lá đậm và nền màu vàng nhạt.
* Cả hai hình đều nằm trong một nhóm duy nhất, vì vậy di chuyển một hình sẽ di chuyển hình còn lại.

## Các câu hỏi thường gặp và trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Can I add more than two shapes to the group?** | Yes. Create additional `Shape` objects and call `group.AppendChild(yourShape)` for each. |
| **What if I need to rotate the group?** | Set `group.RotationAngle = 45;` (degrees). All child shapes rotate together. |
| **Is it possible to group shapes after the document is saved?** | You must modify the document structure before saving; otherwise you’d need to load the file, locate the shapes, and recreate the group. |
| **Do I need to dispose of any objects?** | Aspose.Words manages its own resources, but you should dispose of `FileStream` objects if you open streams manually. |
| **Will the code work with .doc (binary) format?** | Yes, change `doc.Save("output.doc")`. The grouping behavior is identical. |

## Kết luận

Bạn giờ đã biết cách **create rectangle shape**, **set shape size**, và **group multiple shapes** trong một tệp Word bằng C#. Cách tiếp cận này cho phép bạn xây dựng các sơ đồ phức tạp, dấu nước, hoặc báo cáo dựa trên mẫu một cách lập trình mà không cần chỉnh sửa thủ công.

### Các bước tiếp theo

* Khám phá thêm **group shapes in word** bằng cách thêm các hộp văn bản hoặc hình ảnh vào cùng một nhóm.
* Sử dụng mẫu `SetShapeSize` để tính toán kích thước một cách động dựa trên bố cục trang.
* Kết hợp kỹ thuật này với các trường mail‑merge để tạo tài liệu cá nhân hoá ở quy mô lớn.

Hãy tự do thử nghiệm với các loại hình khác nhau, màu sắc và các biến đổi nhóm. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có mã mẫu đầy đủ và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}