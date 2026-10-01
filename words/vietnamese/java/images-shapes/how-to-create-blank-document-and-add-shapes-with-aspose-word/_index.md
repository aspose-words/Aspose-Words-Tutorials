---
category: general
date: 2026-09-30
description: Tạo tài liệu trống và chèn hình chữ nhật, hình elip, và nhóm nhiều hình
  trong C# bằng Aspose.Words. Tìm hiểu cách chèn hình và cách tạo nhóm.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: vi
lastmod: 2026-09-30
og_description: Tạo tài liệu trống bằng C# và học cách chèn hình dạng cũng như nhóm
  nhiều hình dạng với Aspose.Words. Thực hiện theo hướng dẫn từng bước.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Tạo tài liệu trống và nhóm các hình dạng trong C# – Hướng dẫn Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Cách tạo tài liệu trống và thêm hình dạng bằng Aspose.Words trong C#
url: /vi/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu trống và thêm các hình dạng với Aspose.Words trong C#

Nếu bạn cần **tạo tài liệu trống** và điền nó bằng đồ họa, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy cách **chèn hình chữ nhật**, thêm các đối tượng vẽ khác, và sau đó **nhóm nhiều hình dạng** để chúng hoạt động như một đơn vị duy nhất.

Làm việc với các hình dạng là yêu cầu phổ biến khi tạo hợp đồng, chứng chỉ hoặc báo cáo tùy chỉnh. Trong tutorial này, bạn sẽ học quy trình hoàn chỉnh, từ khởi tạo tài liệu đến lưu file cuối cùng, sử dụng Aspose.Words API cho .NET.

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 (hoặc mới hơn) SDK được cài đặt  
* Giấy phép Aspose.Words for .NET hợp lệ (bản dùng thử miễn phí cũng hoạt động cho ví dụ này)  
* Một IDE như Visual Studio 2022 hoặc Visual Studio Code  

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Cách tạo tài liệu trống và làm việc với các hình dạng

Bước đầu tiên là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho tệp Word trong bộ nhớ và cho phép bạn truy cập `DocumentBuilder`, công cụ chính để chèn nội dung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Lý do quan trọng:** Một tài liệu trống cung cấp một canvas sạch sẽ. `DocumentBuilder` duy trì vị trí chèn hiện tại, vì vậy mỗi hình dạng bạn thêm sẽ tự động được đặt vào trang thích hợp.

## Chèn hình chữ nhật và các hình dạng khác

Tiếp theo, chúng ta thêm một hình chữ nhật và một hình ellipse. Cả hai lời gọi đều sử dụng cùng một phương thức `InsertShape`, đây là cách được khuyến nghị **cách chèn các hình dạng** trong Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Phương thức `InsertShape` tự động đặt hình dạng tại vị trí con trỏ hiện tại.* Nếu bạn cần vị trí chính xác, có thể điều chỉnh `Shape.Left` và `Shape.Top` sau khi chèn.

## Nhóm nhiều hình dạng thành một đối tượng duy nhất

Bây giờ chúng ta kết hợp hình chữ nhật và ellipse thành một thực thể logic. Việc nhóm hữu ích khi bạn muốn di chuyển hoặc thay đổi kích thước nhiều hình dạng cùng lúc.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Cách hoạt động:** `InsertGroupShape` tạo một container hoạt động như bất kỳ `Shape` nào khác. Bằng cách gọi `AppendChild`, bạn di chuyển các hình dạng hiện có vào container, và container sẽ tự động cập nhật tọa độ tương đối của chúng.

### Mẹo thực tế

Nếu sau này bạn cần **cách tạo nhóm** một cách lập trình cho hơn hai hình dạng, chỉ cần lặp lại `AppendChild` cho mỗi đối tượng `Shape` bổ sung. Nhóm có thể chứa bất kỳ số lượng đối tượng vẽ nào, bao gồm ảnh, hộp văn bản, hoặc thậm chí các nhóm khác.

## Ví dụ đầy đủ – cách chèn các hình dạng và lưu tài liệu

Dưới đây là chương trình hoàn chỉnh, có thể chạy được, minh họa mọi bước đã thảo luận. Khi chạy mã, sẽ tạo ra tệp `ShapesDemo.docx` chứa một hình chữ nhật màu xanh, một ellipse màu xanh lá và một hình dạng nhóm với viền màu xám bao quanh.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả mong đợi:** Mở `ShapesDemo.docx` trong Microsoft Word sẽ hiển thị một trang duy nhất với hình chữ nhật xanh, ellipse xanh lá và viền xám đại diện cho nhóm. Khi di chuyển nhóm, cả hai hình dạng sẽ di chuyển cùng nhau, xác nhận rằng thao tác **nhóm nhiều hình dạng** đã thành công.

## Các câu hỏi thường gặp và xử lý các trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| *Nếu tôi cần các hình dạng trên một trang cụ thể thì sao?* | Gọi `builder.MoveToDocumentEnd();` trước khi chèn các hình dạng, hoặc sử dụng `builder.MoveToSection(sectionIndex);` để nhắm tới một phần cụ thể. |
| *Có thể thêm văn bản bên trong một hình dạng nhóm không?* | Có. Tạo một `Shape` loại `ShapeType.TextBox`, cấu hình nội dung văn bản, sau đó `AppendChild` nó vào `GroupShape`. |
| *Kích thước của hình dạng được tính bằng điểm hay pixel?* | Aspose.Words sử dụng **points** (1 pt = 1/72 inch). Điều này đảm bảo kích thước nhất quán trên máy in và màn hình. |
| *Cách thay đổi góc quay của nhóm?* | Đặt `groupShape.RotationAngle = 45;` (độ). Tất cả các hình dạng con sẽ quay quanh gốc của nhóm. |

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu trống**, **chèn hình chữ nhật**, **cách chèn các hình dạng** như ellipse, và **nhóm nhiều hình dạng** thành một đối tượng duy nhất bằng Aspose.Words cho .NET. Ví dụ mã đầy đủ minh họa cách tiếp cận được khuyến nghị, và các mẹo trên giúp bạn điều chỉnh giải pháp cho các kịch bản phức tạp hơn như thêm hộp văn bản hoặc quay nhóm.

Sẵn sàng khám phá thêm? Hãy thử thêm một hình ảnh vào nhóm, thử nghiệm với các màu nền khác nhau, hoặc tạo báo cáo đa trang trong đó mỗi trang chứa một sơ đồ nhóm riêng. Các nguyên tắc này vẫn áp dụng, vì vậy bạn có thể mở rộng mẫu này cho bất kỳ dự án tự động hoá tài liệu nào.

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích chi tiết từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}