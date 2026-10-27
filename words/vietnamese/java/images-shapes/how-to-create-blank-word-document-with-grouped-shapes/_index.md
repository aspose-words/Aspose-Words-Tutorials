---
category: general
date: 2026-09-08
description: Tìm hiểu cách tạo tài liệu Word trống, chèn hình chữ nhật và nhóm nhiều
  hình dạng bằng C#. Hãy làm theo hướng dẫn từng bước này.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: vi
lastmod: 2026-09-08
og_description: Tạo tài liệu Word trống, chèn hình chữ nhật và nhóm nhiều hình dạng
  trong C#. Hướng dẫn này sẽ đưa bạn qua toàn bộ quá trình.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Tạo tài liệu Word trống với các hình dạng được nhóm trong C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cách tạo tài liệu Word trống với các hình dạng được nhóm
url: /vi/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống với các hình dạng được nhóm

Nếu bạn cần **tạo tài liệu Word trống** chứa đồ họa tùy chỉnh, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ học cách **chèn hình chữ nhật**, **nhóm nhiều hình dạng**, và **thêm hình vào nhóm** bằng Aspose.Words for .NET.

Một tài liệu trống cung cấp cho bạn một canvas sạch sẽ, và việc nhóm các hình dạng cho phép bạn di chuyển, thay đổi kích thước hoặc xoay chúng như một đơn vị duy nhất. Bài học này bao gồm mọi bước—from khởi tạo tài liệu đến lưu file cuối cùng—để bạn có thể sao chép mã vào dự án của mình và thấy kết quả ngay lập tức.

## Những gì bạn cần

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
* Giấy phép Aspose.Words for .NET hợp lệ (phiên bản đánh giá miễn phí đủ cho việc thử nghiệm)
* Một IDE như Visual Studio 2022 hoặc Visual Studio Code
* Kiến thức cơ bản về cú pháp C#

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Cách tạo tài liệu Word trống

Bước đầu tiên là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho một file `.docx` rỗng mà bạn có thể chỉnh sửa bằng `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Constructor của `Document` tạo một **tài liệu Word trống** trong bộ nhớ. `DocumentBuilder` cung cấp một API dạng fluent để chèn văn bản, hình ảnh và các đối tượng vẽ.

## Chèn hình chữ nhật vào tài liệu

Tiếp theo, thêm một hình chữ nhật. Hình chữ nhật sẽ là phần tử con đầu tiên của nhóm mà chúng ta sẽ tạo sau.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Gọi `InsertShape` với `ShapeType.Rectangle` **chèn hình chữ nhật** tại vị trí con trỏ hiện tại. Chiều rộng và chiều cao được tính bằng điểm (1 pt ≈ 1/72 in).

## Nhóm nhiều hình dạng lại với nhau

`GroupShape` hoạt động như một container. Tất cả các hình con bên trong nhóm sẽ di chuyển và biến đổi cùng nhau. Đầu tiên, tạo nhóm, sau đó thêm hình chữ nhật vừa tạo.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Phương thức `InsertGroupShape` đặt một nhóm rỗng tại vị trí con trỏ của builder. Bằng cách gắn hình chữ nhật vào, chúng ta **nhóm nhiều hình dạng**—hình chữ nhật trở thành một phần của bộ sưu tập node nội bộ của nhóm.

## Thêm hình vào nhóm và lưu file

Bây giờ thêm một hình thứ hai—một hình ellipse—để minh họa cách nhiều đối tượng chia sẻ cùng một container. Sau đó, lưu tài liệu.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Lệnh `InsertShape` **thêm hình vào nhóm** khi bạn gắn `Shape` trả về vào `GroupShape`. Việc lưu `Document` sẽ ghi ra một file `.docx` mà bạn có thể mở bằng Microsoft Word, LibreOffice, hoặc bất kỳ trình xem nào hỗ trợ.

### Kết quả mong đợi

Khi mở *GroupShapeDemo.docx*, bạn sẽ thấy một trang trống với một đối tượng được nhóm chứa một hình chữ nhật màu xanh nhạt và một hình ellipse màu hồng. Khi chọn nhóm, bạn có thể di chuyển cả hai hình cùng lúc, xác nhận rằng **nhóm nhiều hình dạng** đã hoạt động đúng như mong đợi.

## Tại sao nên dùng GroupShape?

* **Biến đổi nguyên tử** – Thu phóng, xoay hoặc di chuyển nhóm sẽ ảnh hưởng đồng đều đến tất cả các phần tử con.
* **Tổ chức logic** – Giữ các đồ họa liên quan cùng nhau, giúp cấu trúc tài liệu dễ bảo trì hơn.
* **Hiệu năng** – Việc render một container duy nhất thường nhanh hơn so với xử lý nhiều hình độc lập.

Nếu sau này bạn cần chỉnh sửa một phần tử con riêng lẻ, có thể lấy nó từ `group.ChildNodes` bằng chỉ số hoặc bằng thuộc tính `Name`.

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản                                 | Cách điều chỉnh mã                                                            |
|------------------------------------------|--------------------------------------------------------------------------------|
| **Các loại hình dạng khác nhau**         | Thay `ShapeType.Rectangle` hoặc `ShapeType.Ellipse` bằng bất kỳ `ShapeType` nào khác |
| **Thêm văn bản vào trong hình**          | Dùng `Shape.TextPath.Text = "Hello"` sau khi chèn hình                         |
| **Đặt góc xoay**                          | `group.Rotation = 45;` (độ)                                                    |
| **Lưu dưới dạng PDF thay vì DOCX**      | `doc.Save("GroupShapeDemo.pdf");`                                               |
| **Áp dụng viền cho nhóm**                | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`             |

## Mẹo chuyên nghiệp

* **Đặt tên cho các hình** – `rectangle.Name = "MyRect";` giúp bạn dễ dàng tìm kiếm chúng sau này.
* **Sử dụng vị trí tương đối** – Đặt `group.RelativeHorizontalPosition` thành `RelativeHorizontalPosition.Page` nếu bạn muốn nhóm được neo vào lề trang.
* **Giải phóng tài nguyên** – Bao `Document` trong một khối `using` khi làm việc trong các ứng dụng lớn hơn để giải phóng bộ nhớ không quản lý kịp thời.

## Mã nguồn đầy đủ để sao chép nhanh

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Sao chép mã vào một dự án console mới, khôi phục gói NuGet `Aspose.Words`, và chạy. File đầu ra sẽ xuất hiện trong thư mục `bin/Debug/net6.0` (hoặc thư mục tương đương) của dự án.

## Các bước tiếp theo

Bây giờ bạn đã có thể **tạo tài liệu Word trống**, **chèn hình chữ nhật**, và **nhóm nhiều hình dạng**, bạn có thể khám phá:

* Thêm **hộp văn bản** vào trong nhóm để tạo các sơ đồ có nhãn.
* Xuất đồ họa đã nhóm ra hình ảnh bằng `doc.Save("image.png", SaveFormat.Png)`.
* Kết hợp các nhóm với bảng để tạo báo cáo định dạng phong phú.

Thử nghiệm với các thuộc tính hình dạng khác nhau, cấu trúc nhóm đa cấp, và các định dạng xuất để khai thác tối đa khả năng vẽ của Aspose.Words.

--- 

*Nhớ*: việc nhóm các hình dạng là cách mạnh mẽ để giữ tài liệu Word của bạn gọn gàng và mã nguồn dễ bảo trì. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong bài viết này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ cùng các giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}