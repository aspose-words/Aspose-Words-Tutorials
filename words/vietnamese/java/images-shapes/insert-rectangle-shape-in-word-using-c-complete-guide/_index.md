---
category: general
date: 2026-08-04
description: Chèn hình chữ nhật vào tài liệu Word bằng C#. Tìm hiểu cách nhóm các
  hình trong Word, lưu tài liệu dưới dạng docx và sử dụng DocumentBuilder cho các
  bố cục nâng cao.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: vi
lastmod: 2026-08-04
og_description: Chèn hình chữ nhật vào tệp Word bằng C# và sau đó nhóm các hình để
  tạo bố cục nâng cao. Hướng dẫn này cũng đề cập đến việc lưu tài liệu dưới dạng docx
  và sử dụng DocumentBuilder một cách hiệu quả.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Chèn hình chữ nhật trong Word – Hướng dẫn từng bước C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Chèn hình chữ nhật vào Word bằng C# – hướng dẫn chi tiết
url: /vi/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn hình chữ nhật trong Word bằng C# – hướng dẫn đầy đủ

Nếu bạn cần **chèn hình chữ nhật** vào tài liệu Word bằng C#, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn cũng sẽ học **cách nhóm các hình** trong Word, **lưu tài liệu dưới dạng docx**, và **cách sử dụng Builder** để có mã sạch, dễ bảo trì.

Làm việc với các hình là yêu cầu phổ biến khi tạo báo cáo, chứng chỉ, hoặc bố cục tùy chỉnh một cách tự động. Khi kết thúc hướng dẫn, bạn sẽ có một ví dụ chạy được đầy đủ, tạo một hình chữ nhật, thêm một hình ellipse, nhóm chúng lại, và lưu kết quả dưới dạng file DOCX.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 hoặc phiên bản mới hơn được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#)  
* Thư viện **Aspose.Words for .NET** (có sẵn qua NuGet)  

Bạn có thể thêm thư viện bằng lệnh sau:

```bash
dotnet add package Aspose.Words
```

## Chèn hình chữ nhật bằng DocumentBuilder

Bước đầu tiên là tạo một `Document` mới và một `DocumentBuilder`. Builder cung cấp một API dạng fluent để chèn nội dung, bao gồm các hình.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

Đối tượng `DocumentBuilder` là thành phần cốt lõi bạn sẽ dùng để **chèn hình chữ nhật** và các yếu tố khác. Nó theo dõi vị trí con trỏ hiện tại trong tài liệu, vì vậy mọi chèn sẽ diễn ra chính xác ở nơi bạn muốn.

## Cách chèn hình chữ nhật

Khi builder đã sẵn sàng, gọi `InsertShape`. Bạn chỉ định `ShapeType`, chiều rộng và chiều cao tính bằng điểm (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Tại sao điều này quan trọng*: Đặt `FillColor` và `StrokeColor` làm cho hình chữ nhật nổi bật hơn, giúp bạn dễ dàng nhóm nó với các hình khác sau này.

## Cách nhóm các hình trong Word

Nhóm các hình cho phép bạn di chuyển, xoay, hoặc định dạng nhiều đối tượng như một thực thể duy nhất. Sau khi chèn hình chữ nhật, thêm một hình khác (ellipse trong ví dụ này) và sau đó tạo một `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Lệnh `InsertGroupShape` tạo một placeholder có thể chứa bất kỳ số lượng hình con nào. Bằng cách thêm hình chữ nhật và ellipse vào, bạn thực tế **nhóm các hình trong Word**. Nhóm này hoạt động như một hình duy nhất—bạn có thể thay đổi vị trí, áp dụng viền, hoặc thay đổi kích thước mà không ảnh hưởng tới bố cục nội bộ của từng hình con.

### Mẹo chuyên nghiệp

Sau khi nhóm, bạn có thể thay đổi vị trí của nhóm so với trang:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Lưu tài liệu dưới dạng docx

Khi các hình đã được sắp xếp, bạn cần lưu file. Phương thức `Document.Save` tự động xác định định dạng dựa trên phần mở rộng của file. Để **lưu tài liệu dưới dạng docx**, truyền vào đường dẫn kết thúc bằng `.docx`.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Chạy chương trình sẽ tạo ra `output.docx`. Mở file trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu xanh nhạt và một ellipse màu hồng nhạt được nhóm lại với nhau. Bạn có thể nhấp vào nhóm và di chuyển nó như một đối tượng duy nhất.

## Cách sử dụng DocumentBuilder một cách hiệu quả

`DocumentBuilder` không chỉ là công cụ chèn hình; nó còn xử lý văn bản, bảng, header và footer. Khi kết hợp tạo hình với văn bản, hãy nhớ đặt lại con trỏ nếu bạn cần chèn nội dung ở vị trí khác:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Giữ trạng thái của builder một cách rõ ràng giúp tránh việc ghi đè ngoài ý muốn và làm cho mã dễ bảo trì hơn.

## Các trường hợp đặc biệt và biến thể

| Tình huống | Cách tiếp cận đề xuất |
|-----------|----------------------|
| **Nhiều hơn hai hình** | Chèn từng hình, sau đó gọi `AppendChild` cho mỗi hình trước khi lưu. |
| **Nhóm lồng nhau** | Tạo một nhóm, thêm các hình, rồi chèn nhóm đó vào một `GroupShape` khác. |
| **Đơn vị đo khác nhau** | Sử dụng `builder.ConvertPixelsToPoints` nếu bạn có kích thước tính bằng pixel. |
| **Tương thích với các phiên bản Word cũ** | Lưu dưới dạng `.doc` bằng cách thay đổi phần mở rộng; hầu hết các tính năng hình vẫn hoạt động. |

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là toàn bộ chương trình bạn có thể sao chép‑dán vào một dự án console mới. Không cần bất kỳ đoạn mã bổ sung nào.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Kết quả mong đợi**: Mở `output.docx` sẽ hiển thị một hình chữ nhật màu xanh nhạt và một ellipse màu hồng nhạt được nhóm lại, đặt cách lề trái 150 pt và cách lề trên 100 pt. Chú thích xuất hiện dưới nhóm.

## Kết luận

Bây giờ bạn đã biết cách **chèn hình chữ nhật** vào file Word bằng C#, **cách nhóm các hình trong Word**, và **cách lưu tài liệu dưới dạng docx** với `DocumentBuilder` của Aspose.Words. Khi nắm vững các bước này, bạn có thể xây dựng các bố cục phức tạp—chứng chỉ, báo cáo, hoặc biểu mẫu tùy chỉnh—hoàn toàn bằng mã.

Tiếp theo, khám phá các chủ đề liên quan như **thêm textbox**, **làm việc với bảng**, hoặc **xuất ra PDF**. Mỗi chủ đề đều dựa trên các nguyên tắc cơ bản của `DocumentBuilder` mà bạn vừa thực hành.

Sẵn sàng tự động hoá tài liệu Word của mình? Hãy thử mở rộng ví dụ bằng cách thêm nhiều hình hơn, áp dụng gradient, hoặc lặp qua dữ liệu để tạo một báo cáo đầy đủ trong một lần chạy. Chúc bạn lập trình vui vẻ!


## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ cùng các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}