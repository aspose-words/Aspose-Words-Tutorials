---
category: general
date: 2026-09-18
description: Tạo hình chữ nhật trong tài liệu Word bằng C#. Tìm hiểu cách thêm nhiều
  hình, thêm các hình vào một nhóm và chèn nhóm hình bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: vi
lastmod: 2026-09-18
og_description: Tạo hình chữ nhật trong tệp Word bằng C#. Hướng dẫn này chỉ cách thêm
  nhiều hình, thêm các hình vào một nhóm và chèn hình nhóm bằng Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Tạo hình chữ nhật và nhóm các hình trong C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Tạo hình chữ nhật và nhóm nhiều hình trong C#
url: /vi/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo hình chữ nhật và nhóm nhiều hình trong C#

Nếu bạn cần **tạo hình chữ nhật** trong tài liệu Word, hướng dẫn này cung cấp giải pháp hoàn chỉnh. Bạn sẽ thấy cách **thêm nhiều hình**, **thêm các hình vào một nhóm**, và **chèn nhóm hình** bằng cách sử dụng Aspose.Words API cho .NET.

Làm việc với các hình là yêu cầu phổ biến khi tạo báo cáo, hợp đồng hoặc tài liệu marketing một cách tự động. Khi kết thúc hướng dẫn, bạn sẽ có một ứng dụng console C# có thể chạy được, tạo ra tệp `.docx` chứa một hình chữ nhật, một hình elip và một nhóm chứa cả hai hình.

Các yêu cầu duy nhất là một .NET SDK gần đây (6.0 trở lên) và bản quyền Aspose.Words cho .NET. Không cần công cụ bổ sung nào khác.

## Prerequisites

- .NET 6.0 SDK hoặc mới hơn  
- Aspose.Words cho .NET (gói NuGet `Aspose.Words`)  
- Kiến thức cơ bản về cú pháp C#  

Bạn có thể cài đặt gói bằng lệnh sau:

```bash
dotnet add package Aspose.Words
```

## Bước 1: Tạo hình chữ nhật với Aspose.Words

Bước đầu tiên là tạo một đối tượng `Shape` loại `Rectangle`. Đối tượng này đại diện cho hình chữ nhật sẽ hiển thị trong tài liệu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Tại sao lại quan trọng:** `ShapeType.Rectangle` báo cho Aspose.Words vẽ một hình chữ nhật hình học. Đặt `Width` và `Height` xác định kích thước tính bằng điểm (1 point = 1/72 inch). Thêm màu nền và màu viền giúp hình hiển thị mà không cần định dạng bổ sung.

## Bước 2: Thêm nhiều hình vào tài liệu

Sau hình chữ nhật, bạn có thể tạo bất kỳ số lượng hình bổ sung nào. Trong ví dụ này, chúng ta thêm một hình elip để minh họa cách **thêm nhiều hình** hoạt động.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Tại sao lại quan trọng:** Mỗi lần gọi `new Shape` tạo ra một đối tượng vẽ độc lập. Khi chèn chúng lần lượt, bạn xây dựng một tập hợp các hình có thể sau này được nhóm lại hoặc định vị riêng lẻ.

## Bước 3: Thêm các hình vào nhóm

Nhóm các hình giúp đơn giản hoá việc quản lý bố cục vì nhóm hoạt động như một nút duy nhất. Bước này cho thấy cách **thêm các hình vào nhóm** bằng `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Tại sao lại quan trọng:** `GroupShape` hoạt động như một container. Khi bạn di chuyển, xoay hoặc thay đổi kích thước nhóm, tất cả các hình con sẽ tự động theo. Hộp bao (200 × 200 point) xác định không gian tọa độ cho các hình con.

## Bước 4: Chèn nhóm hình vào tài liệu

Bây giờ nhóm đã chứa hình chữ nhật và elip, bạn cần **chèn nhóm hình** vào vị trí mong muốn. Builder đã đặt nhóm rỗng, nhưng bạn cũng có thể chèn nó ở nơi khác nếu cần.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Tại sao lại quan trọng:** Điều chỉnh `Left` và `Top` di chuyển toàn bộ nhóm trong trang. Lưu tài liệu sẽ ghi lại cấu trúc hình vào tệp `.docx` có thể mở bằng Microsoft Word, LibreOffice hoặc bất kỳ trình xem tương thích nào.

## Ví dụ chạy được đầy đủ

Dưới đây là chương trình hoàn chỉnh kết hợp tất cả các bước. Sao chép mã vào một dự án console mới và chạy để tạo `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Kết quả mong đợi:**  
Mở `GroupShapeExample.docx` sẽ thấy một nhóm duy nhất chứa một hình chữ nhật màu xanh nhạt và một hình elip màu san hô nhạt, cả hai đều nằm trong container 200 × 200 point. Nhóm có thể được chọn như một đối tượng duy nhất trong Word, xác nhận rằng **thêm các hình vào nhóm** đã thành công.

## Các biến thể thường gặp và trường hợp góc cạnh

| Situation | Recommended adjustment |
|-----------|------------------------|
| Các loại hình khác nhau (ví dụ, `ShapeType.Line`) | Tạo hình với `ShapeType` mong muốn và đặt hình học tương ứng. |
| Cần xoay một hình | Sử dụng `shape.Rotation = 45;` (độ) trước khi thêm vào nhóm. |
| Tài liệu lớn với nhiều nhóm | Tái sử dụng một thể hiện `DocumentBuilder` duy nhất; tránh tạo builder mới cho mỗi nhóm để giảm tải bộ nhớ. |
| Lưu thành PDF thay vì DOCX | Gọi `doc.Save("output.pdf", SaveFormat.Pdf);` sau khi nhóm đã được chèn. |

**Pro tip:** Luôn đặt giá trị `Left` và `Top` rõ ràng cho nhóm khi bạn cần vị trí chính xác. Nếu bỏ qua, nhóm sẽ kế thừa vị trí con trỏ hiện tại của builder, có thể dẫn đến kết quả bố cục không mong muốn.

## Kết luận

Bạn đã biết cách **tạo hình chữ nhật**, **thêm nhiều hình**, **thêm các hình vào nhóm**, và **chèn nhóm hình** trong tài liệu Word bằng C#. Ví dụ đầy đủ minh họa quy trình từ tạo tài liệu đến lưu tệp cuối cùng.

Tiếp theo, hãy khám phá các chủ đề liên quan như **định vị hình so với văn bản**, **áp dụng vòng text wrapping**, và **xuất các nhóm hình sang PDF**. Những mở rộng này cho phép bạn xây dựng bố cục tài liệu phức tạp, lập trình một cách chuyên nghiệp với Aspose.Words.

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}