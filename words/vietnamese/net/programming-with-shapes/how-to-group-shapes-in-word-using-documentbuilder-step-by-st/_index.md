---
category: general
date: 2026-09-08
description: Tìm hiểu cách nhóm các hình dạng trong Word bằng DocumentBuilder, tạo
  một tài liệu Word trống và chèn một hình chữ nhật chỉ trong vài dòng mã C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: vi
lastmod: 2026-09-08
og_description: Nhóm các hình dạng trong Word bằng DocumentBuilder. Hướng dẫn này
  cho thấy cách tạo một tài liệu Word trống, chèn một hình chữ nhật và kết hợp các
  hình dạng thành một GroupShape.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Nhóm các hình dạng trong Word bằng DocumentBuilder – ví dụ C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách nhóm các hình dạng trong Word bằng DocumentBuilder – hướng dẫn từng bước
url: /vi/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Word bằng DocumentBuilder – hướng dẫn từng bước

Nếu bạn cần **nhóm các hình dạng trong Word** một cách lập trình, hướng dẫn này cung cấp giải pháp hoàn chỉnh bằng C#. Bạn sẽ thấy cách **tạo một tài liệu Word trống**, sử dụng **DocumentBuilder**, và **chèn một hình chữ nhật** trước khi nhóm nó với một hình ellipse. Kết quả là một `GroupShape` duy nhất mà bạn có thể di chuyển, thay đổi kích thước hoặc định dạng như một đối tượng.

Hướng dẫn này bao gồm mọi thứ bạn cần biết để tạo một tài liệu Word có đồ họa được nhóm lại bằng thư viện Aspose.Words for .NET. Khi kết thúc bài viết, bạn sẽ có một dự án có thể chạy được tạo ra file `GroupedShapes.docx` chứa một hình chữ nhật và một hình ellipse được kết hợp thành một hình duy nhất.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7.2+)
- Gói NuGet Aspose.Words for .NET (`Aspose.Words`) – phiên bản 23.12 hoặc mới hơn
- Một IDE C# như Visual Studio 2022 hoặc Visual Studio Code
- Kiến thức cơ bản về cú pháp C# và lập trình hướng đối tượng

> **Pro tip:** Cài đặt gói NuGet từ dòng lệnh để giữ dự án gọn gàng:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Bước 1: Tạo tài liệu Word trống

Hoạt động đầu tiên là khởi tạo một đối tượng `Document`, đại diện cho một file Word trống, và một `DocumentBuilder` cho phép bạn thêm nội dung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Tại sao điều này quan trọng:** `Document` cung cấp container cho file, trong khi `DocumentBuilder` cung cấp API dạng fluent để chèn văn bản, hình ảnh và hình dạng. Nếu không có `DocumentBuilder`, bạn sẽ phải thao tác cây node của tài liệu một cách thủ công, điều này dễ gây lỗi.

## Bước 2: Chèn một hình chữ nhật

Một hình chữ nhật là khối xây dựng phổ biến cho các sơ đồ. Sử dụng `InsertShape` với `ShapeType.Rectangle` và chỉ định chiều rộng và chiều cao bằng điểm (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Tại sao điều này quan trọng:** Đặt vị trí `Left` và `Top` giúp hình chữ nhật được đặt chính xác trên trang, điều này rất cần thiết khi bạn sau này nhóm nó với các hình khác. Phương thức `InsertShape` tự động thêm hình vào đoạn hiện tại.

## Bước 3: Chèn một hình ellipse

Tiếp theo, thêm một hình ellipse sẽ nằm cạnh hình chữ nhật.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Tại sao điều này quan trọng:** Sử dụng một `ShapeType` khác cho thấy cách API `DocumentBuilder` giống nhau có thể tạo ra các đồ họa đa dạng. Đặt vị trí ellipse sao cho nó chồng lên hình chữ nhật làm cho hiệu ứng nhóm trở nên rõ ràng.

## Bước 4: Nhóm hai hình lại với nhau

`GroupShape` hoạt động như một container. Bằng cách thêm hình chữ nhật và ellipse làm các child, chúng sẽ hoạt động như một đối tượng duy nhất.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Tại sao điều này quan trọng:** Thuộc tính `Bounds` cho Word biết nhóm nằm ở vị trí nào trên trang. Khi thêm các hình con, bạn giữ nguyên định dạng riêng của chúng đồng thời cho phép các biến đổi chung (di chuyển, xoay, thay đổi kích thước).

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể thay đổi đường dẫn tới bất kỳ thư mục nào bạn muốn.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Khi bạn mở `GroupedShapes.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật và một hình ellipse được nhóm lại với nhau. Khi chọn nhóm, cả hai hình sẽ được đánh dấu, cho phép bạn kéo hoặc thay đổi kích thước chúng như một đơn vị duy nhất.

### Kết quả mong đợi

- Một file Word có tên **GroupedShapes.docx**
- Trang đầu tiên chứa một **hình chữ nhật** (100 pt × 50 pt) tại vị trí (50, 50)
- Một **ellipse** (80 pt × 80 pt) tại vị trí (200, 70)
- Cả hai hình đều là một phần của **GroupShape** với hộp bao (bounding box) kích thước 300 pt × 200 pt

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Điều chỉnh |
|----------|------------|
| **Kích thước trang khác** | Set `document.Sections[0].PageSetup.PageWidth` and `PageHeight` before inserting shapes. |
| **Nhiều hơn hai hình** | Create additional `Shape` objects and call `groupShape.AppendChild(newShape)` for each. |
| **Áp dụng màu nền** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Xoay nhóm** | `groupShape.Rotation = 45;` (degrees) |
| **Xuất ra PDF** | After saving the DOCX, call `document.Save("GroupedShapes.pdf");` |

## Mã nguồn đầy đủ (sẵn sàng chạy)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Sao chép mã vào một dự án console mới, khôi phục gói NuGet Aspose.Words, và chạy. Console sẽ xác nhận vị trí file, và khi mở file sẽ hiển thị đồ họa đã được nhóm.

## Kết luận

Bây giờ bạn đã biết **cách nhóm các hình dạng trong Word** bằng Aspose.Words `DocumentBuilder`. Hướng dẫn đã đi qua việc tạo một **tài liệu Word trống**, **chèn một hình chữ nhật**, thêm một ellipse, và kết hợp chúng thành một `GroupShape`. Với nền tảng này, bạn có thể xây dựng các sơ đồ, lưu đồ hoặc đồ họa tùy chỉnh phong phú hơn trực tiếp từ C#.

### Tiếp theo là gì?

- Khám phá **cách sử dụng DocumentBuilder** cho bảng, header và footer.
- Kết hợp các kỹ thuật **chèn hình chữ nhật trong Word** với các textbox để tạo sơ đồ có chú thích.
- Sử dụng **tạo tài liệu Word trống** làm mẫu cho việc tạo báo cáo tự động.

Bạn có thể tự do thử nghiệm với màu sắc, gradient và các hình dạng bổ sung. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Chèn Shapes trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}