---
category: general
date: 2026-09-21
description: Tạo một tài liệu Word trống bằng Aspose.Words, thiết lập kích thước hình,
  thiết lập vị trí hình, thiết lập màu sắc hình và lưu tệp docx trong một lần thực
  hiện.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: vi
lastmod: 2026-09-21
og_description: Tạo một tài liệu Word trống, đặt kích thước hình, đặt vị trí hình,
  đặt màu sắc hình và lưu tệp docx bằng Aspose.Words trong vài phút.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Tạo tài liệu Word trống và thêm các hình dạng màu – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Tạo tài liệu Word trống và thêm các hình dạng màu sắc bằng Aspose.Words
url: /vi/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo một tài liệu Word trống và thêm các hình dạng màu sắc với Aspose.Words

Nếu bạn cần **tạo một tài liệu Word trống** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words. Bạn sẽ học cách **đặt kích thước hình dạng**, **đặt vị trí hình dạng**, **đặt màu sắc hình dạng**, và cuối cùng **lưu tệp docx** mà không rời khỏi IDE của mình.

Làm việc với các tệp Word trong C# thường đồng nghĩa với việc phải xử lý các cuộc gọi OpenXML mức thấp, nhưng Aspose.Words trừu tượng hoá sự phức tạp. Khi kết thúc hướng dẫn này, bạn sẽ có một tệp `.docx` hoạt động đầy đủ chứa một nhóm hình dạng được tạo từ hai hình chữ nhật màu—hoàn hảo cho báo cáo, chứng chỉ, hoặc mẫu tùy chỉnh.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
- Aspose.Words for .NET 23.9 hoặc mới hơn (cài đặt qua NuGet: `Install-Package Aspose.Words`)
- Kiến thức cơ bản về C# và Visual Studio (hoặc bất kỳ trình chỉnh sửa C# nào)

Không cần tệp Word hiện có; hướng dẫn bắt đầu bằng việc **tạo một tài liệu Word trống** từ đầu.

## Tạo một tài liệu Word trống với Aspose.Words

Bước đầu tiên là tạo một đối tượng `Document`. Đối tượng này đại diện cho một tệp Word trống trong bộ nhớ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` bắt đầu là trống, chính xác là những gì bạn cần khi **tạo một tài liệu Word trống**. `builder` sẽ được sử dụng sau này để chèn nhóm hình dạng vào vị trí con trỏ hiện tại.

## Đặt kích thước hình dạng và tạo một GroupShape

`GroupShape` hoạt động như một container có thể chứa nhiều hình dạng riêng lẻ. Đầu tiên, xác định kích thước tổng thể của container.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Ở đây chúng ta **đặt kích thước hình dạng** cho chính nhóm (300 × 200). Các tên thuộc tính giống nhau (`Width`, `Height`) được sử dụng cho mỗi hình con, cho phép bạn kiểm soát chi tiết từng phần tử.

## Thêm hình chữ nhật đầu tiên và đặt màu sắc hình dạng

Bây giờ thêm một hình chữ nhật vào nhóm và đặt màu nền cho nó.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Thuộc tính `FillColor` **đặt màu sắc hình dạng**. Sử dụng `System.Drawing.Color` cho phép bạn chọn bất kỳ giá trị ARGB đã định sẵn hoặc tùy chỉnh nào.

## Thêm hình chữ nhật thứ hai, đặt kích thước, vị trí và màu sắc

Hình chữ nhật thứ hai minh họa cách **đặt vị trí hình dạng** tương đối với nhóm và cách thay đổi màu sắc của nó.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Vì chiều rộng của nhóm là 300 điểm, hai hình chữ nhật 120 điểm mỗi hình vừa vặn với khoảng cách 30 điểm. Điều chỉnh `Left` và `Top` nếu bạn cần bố cục khác.

## Chèn GroupShape vào tài liệu

Khi nhóm đã được cấu hình đầy đủ, đặt nó vào vị trí con trỏ hiện tại.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` ghi hình dạng trực tiếp vào phần body của tài liệu, bảo tồn **vị trí hình dạng đã đặt** chính xác mà bạn đã định nghĩa trước đó.

## Lưu tệp docx

Bước cuối cùng là lưu tài liệu vào đĩa. Điều này minh họa thao tác **lưu tệp docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Sau khi chạy chương trình, mở `GroupShape.docx` trong Microsoft Word. Bạn sẽ thấy một trang trống với một nhóm hình dạng chứa hai hình chữ nhật màu được đặt cạnh nhau.

### Kết quả mong đợi

- Một tệp `.docx` một trang.
- Trang chứa một nhóm hình dạng nằm cách lề trái và trên 100 pts.
- Bên trong nhóm, một hình chữ nhật màu xanh nhạt nằm ở phía trái, và một hình chữ nhật màu san hô nhạt nằm ở phía phải, mỗi hình có kích thước 120 × 80 pts.

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một ứng dụng console. Không cần tệp bổ sung nào.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Chạy chương trình này sẽ tạo ra tài liệu chính xác như đã mô tả ở trên, đáp ứng bốn mục tiêu: **tạo tài liệu word trống**, **đặt kích thước hình dạng**, **đặt vị trí hình dạng**, **đặt màu sắc hình dạng**, và **lưu tệp docx**.

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Cần thay đổi gì | Lý do quan trọng |
|----------|----------------|-------------------|
| **Các loại hình dạng khác nhau** | Thay thế `ShapeType.Rectangle` bằng `ShapeType.Ellipse`, `ShapeType.Triangle`, v.v. | Cho phép bạn tạo đồ họa phức tạp hơn mà không cần hình ảnh bên ngoài. |
| **Kích thước động** | Tính `Width` và `Height` từ đầu vào người dùng hoặc tệp cấu hình. | Giúp giải pháp có thể tái sử dụng cho nhiều mẫu tài liệu. |
| **Lưu dưới dạng PDF** | Gọi `document.Save("output.pdf", SaveFormat.Pdf);` | Nếu người nhận cần định dạng không thể chỉnh sửa, PDF là lựa chọn an toàn. |
| **Thêm văn bản vào trong hình dạng** | Tạo một hình dạng `TextBox` và đặt `TextBox.Text`. | Hữu ích cho việc tạo các huy hiệu có nhãn hoặc chú thích. |
| **Nhiều nhóm trên một trang** | Lặp lại các bước 2‑5 với các giá trị `Left`/`Top` khác nhau. | Cho phép bạn xây dựng bảng điều khiển hoặc bố cục đa phần. |

### Mẹo chuyên nghiệp

Khi bạn cần căn chỉnh các hình dạng một cách chính xác, hãy sử dụng thuộc tính `ShapeBase.WrapType = WrapType.Inline` trước khi chèn nhóm. Điều này buộc nhóm hành xử như một đoạn văn, ngăn chặn luồng văn bản không mong muốn xung quanh nó.

## Kết luận

Bây giờ bạn đã biết cách **tạo một tài liệu Word trống** với Aspose.Words, **đặt kích thước hình dạng**, **đặt vị trí hình dạng**, **đặt màu sắc hình dạng**, và **lưu tệp docx**. Ví dụ đầy đủ minh họa một mẫu sạch sẽ, có thể tái sử dụng để thêm đồ họa nhóm vào bất kỳ dự án tự động hoá Word nào.

Từ đây bạn có thể khám phá:

- Thêm nhiều hình dạng hoặc hình ảnh vào cùng một `GroupShape` (các biến thể **đặt kích thước hình dạng**, **đặt màu sắc hình dạng**).
- Sử dụng `ShapeBase.Rotation` để xoay các hình chữ nhật nhằm tạo hiệu ứng trang trí.
- Xuất cùng một tài liệu dưới dạng PDF hoặc HTML để mở rộng phạm vi phân phối (lựa chọn thay thế cho **lưu tệp docx**).

Hãy thoải mái thử nghiệm với các màu sắc, kích thước và logic bố cục khác nhau để phù hợp với nhu cầu báo cáo hoặc mẫu của bạn. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Nhóm Hình Dạng trong Tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Hướng Dẫn Đổ Bóng cho Hình Dạng Aspose.Words – Thêm Đổ Bóng vào Hình Dạng Word trong C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}