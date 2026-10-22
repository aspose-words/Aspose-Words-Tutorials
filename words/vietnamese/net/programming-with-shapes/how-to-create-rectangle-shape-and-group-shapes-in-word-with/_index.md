---
category: general
date: 2026-09-05
description: Tạo hình chữ nhật trong tài liệu Word bằng Aspose.Words, sau đó học cách
  chèn hình elip và nhóm các hình dạng trong Word để có bố cục phong phú hơn.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: vi
lastmod: 2026-09-05
og_description: Tạo hình chữ nhật trong tài liệu Word bằng Aspose.Words, sau đó xem
  cách chèn hình elip và nhóm các hình trong Word cho các bố cục phức tạp.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Tạo hình chữ nhật và nhóm các hình dạng trong Word – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cách tạo hình chữ nhật và nhóm các hình dạng trong Word bằng Aspose.Words
url: /vi/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo hình chữ nhật và nhóm các hình trong Word bằng Aspose.Words

Nếu bạn cần **tạo hình chữ nhật** trong một tài liệu Word, hướng dẫn này sẽ cho bạn các bước chính xác với Aspose.Words cho .NET. Bạn cũng sẽ thấy cách chèn ellipse word, nhóm các hình trong Word, và lưu kết quả dưới dạng tệp DOCX. Giải pháp hoạt động trong bất kỳ dự án .NET 6+ nào và không yêu cầu cài đặt Microsoft Office trên máy chủ.

Bài hướng dẫn bao gồm mọi thứ từ thiết lập dự án đến xử lý các lỗi thường gặp về bố cục, vì vậy bạn có thể sao chép mã và chạy ngay lập tức.

## Yêu cầu trước

* .NET 6 SDK hoặc phiên bản mới hơn đã được cài đặt  
* Một IDE tương thích NuGet (Visual Studio, Rider, hoặc VS Code)  
* Giấy phép Aspose.Words cho .NET (hoặc khóa đánh giá tạm thời)  
* Kiến thức cơ bản về C# và cấu trúc tài liệu Word  

Những mục này cho phép mã biên dịch và các hình được hiển thị đúng.

## Bước 1: Thiết lập dự án và thêm Aspose.Words

Tạo một dự án console mới và thêm gói Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Gói này cung cấp các lớp `Document`, `DocumentBuilder`, `Shape` và `GroupShape` được sử dụng xuyên suốt trong hướng dẫn này.

## Bước 2: Khởi tạo tài liệu trống và một builder

Đối tượng `Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cho phép bạn chèn nội dung một cách lập trình.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Việc tạo tài liệu trước đảm bảo rằng tất cả các thao tác hình tiếp theo có một container hợp lệ.

## Bước 3: **Tạo hình chữ nhật** và đặt kích thước của nó

Hình chữ nhật là container phổ biến nhất cho văn bản hoặc hình ảnh. Bạn định nghĩa kích thước của nó bằng điểm (1 pt ≈ 1/72 inch).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Tại sao bước này quan trọng: lớp `Shape` bao gồm các thuộc tính hình học, màu nền và đường viền. Đặt `Width` và `Height` trước khi chèn đảm bảo hình xuất hiện với kích thước mong muốn.

## Bước 4: **Cách chèn ellipse word** – thêm một hình ellipse

Ellipse có thể được sử dụng cho biểu tượng, dấu hiệu, hoặc các yếu tố trang trí. Mã lặp lại việc tạo hình chữ nhật, chỉ khác ở `ShapeType`.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Các thuộc tính `FillColor` và `Line.Color` minh họa cách tùy chỉnh giao diện mà không cần hình ảnh bên ngoài.

## Bước 5: **Nhóm các hình trong Word** – kết hợp hình chữ nhật và ellipse

Việc nhóm cho phép bạn di chuyển, thay đổi kích thước hoặc xoay nhiều hình như một đơn vị duy nhất. Điều này rất cần thiết khi bạn cần một đồ họa tổng hợp (ví dụ: một biểu tượng có nhãn).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Khi bạn gọi `AppendChild`, các hình gốc sẽ bị loại bỏ khỏi luồng tài liệu chính và trở thành con của `GroupShape`. Nhóm này hoạt động như một hình duy nhất, giúp đơn giản hoá việc điều chỉnh bố cục sau này.

## Bước 6: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.pdf`, `.html`, v.v.). Đối với hướng dẫn này, chúng tôi giữ định dạng Word gốc.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Sau khi chạy chương trình, mở *GroupShape.docx* trong Microsoft Word. Bạn sẽ thấy một hình chữ nhật và một ellipse được nhóm lại với nhau, nằm ở tọa độ bạn đã chỉ định.

## Các biến thể phổ biến và trường hợp đặc biệt

| Situation | What to change | Reason |
|-----------|----------------|--------|
| **Đơn vị kích thước khác** | Use `ConvertUtil.InchToPoint(2.5)` for inches or `ConvertUtil.MillimeterToPoint(30)` for millimetres. | Giữ cho mã dễ đọc khi bạn làm việc với các đơn vị không phải là điểm. |
| **Thêm văn bản vào bên trong hình chữ nhật** | Create a `Paragraph` node, set its `Text` property, and add it to `rectangleShape` via `AppendChild`. | Cho phép bạn gắn nhãn cho hình mà không cần các hộp văn bản riêng. |
| **Xoay nhóm** | Set `groupShape.Rotation = 45;` (degrees). | Hữu ích để tạo các huy hiệu hoặc watermark chéo. |
| **Lưu dưới dạng PDF** | Call `doc.Save("GroupShape.pdf");`. | Aspose.Words tự động raster hoá các hình vector khi xuất PDF. |
| **Nhiều nhóm** | Create additional `GroupShape` instances and repeat the append/insert steps. | Cho phép bố cục trang phức tạp với nhiều thành phần độc lập. |

### Mẹo chuyên nghiệp

Luôn luôn thêm các hình **trước** khi bạn nhóm chúng. Nếu bạn cố gắng nhóm một hình đã thuộc về một nhóm khác, Aspose.Words sẽ ném ra một `ArgumentException`. Xây dựng nhóm trong một phương thức duy nhất sẽ ngăn ngừa lỗi thời gian chạy này.

### Cẩn thận với

* **Coordinate system** – `Left` và `Top` được đo từ lề trái và lề trên của trang, không phải từ cạnh tài liệu. Hiểu sai có thể khiến các hình bị đặt ra ngoài trang.  
* **Licensing** – Nếu không có giấy phép hợp lệ, tài liệu đã lưu sẽ chứa watermark nói “Aspose.Words for .NET Evaluation”. Áp dụng giấy phép của bạn sớm trong mã (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) để tránh điều này.

## Mã nguồn đầy đủ (có thể chạy)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Chạy chương trình này sẽ tạo ra *GroupShape.docx* với các hình đã được nhóm chính xác như mô tả.

## Kết luận

Bây giờ bạn đã biết cách **tạo hình chữ nhật**, **cách chèn ellipse word**, và **nhóm các hình trong Word** bằng Aspose.Words. Ví dụ đầy đủ minh họa quy trình làm việc toàn bộ — từ khởi tạo tài liệu đến lưu tệp cuối cùng — để bạn có thể tích hợp việc xử lý hình vào bất kỳ giải pháp báo cáo tự động hoặc tạo tài liệu nào.

### Tiếp theo là gì?

* Khám phá **aspose.words create shapes** để tạo hình học phức tạp hơn như `Polygon` hoặc `Freeform`.  
* Kết hợp các hình đã nhóm với **content controls** để xây dựng các mẫu động.  
* Chuyển đổi DOCX sang PDF hoặc HTML để xem cách các hình vector được hiển thị trên các định dạng khác nhau.  

Hãy tự do thử nghiệm với các kích thước, màu sắc và góc xoay khác nhau. Khi bạn thành thạo việc nhóm hình, bạn có thể xây dựng các sơ đồ tinh vi, huy hiệu và các thành phần UI tùy chỉnh trực tiếp trong tài liệu Word.

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Chèn Shapes trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}