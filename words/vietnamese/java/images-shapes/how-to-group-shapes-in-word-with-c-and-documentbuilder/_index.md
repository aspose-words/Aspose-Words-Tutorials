---
category: general
date: 2026-10-04
description: Học cách nhóm các hình dạng trong Word bằng C#. Hướng dẫn này chỉ cách
  chèn hình chữ nhật, nhóm nhiều hình dạng và tạo một tệp Word trống một cách lập
  trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: vi
lastmod: 2026-10-04
og_description: Nhóm các hình dạng trong Word bằng C#. Hãy làm theo hướng dẫn từng
  bước này để chèn hình chữ nhật, nhóm nhiều hình dạng và tạo một tệp Word trống bằng
  DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Nhóm các hình dạng trong Word bằng C# – hướng dẫn đầy đủ DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Cách nhóm các hình dạng trong Word bằng C# và DocumentBuilder
url: /vi/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Word bằng C# và DocumentBuilder

Nếu bạn cần **nhóm các hình dạng trong Word** từ một ứng dụng C#, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác. Bạn sẽ thấy cách *chèn hình chữ nhật*, kết hợp một số bản vẽ thành một nhóm duy nhất, và cuối cùng **tạo một tệp Word trống** chứa các đối tượng đã được nhóm.

Làm việc với các hình dạng là một yêu cầu phổ biến khi tạo báo cáo, hoá đơn, hoặc mẫu tùy chỉnh một cách lập trình. Khi kết thúc hướng dẫn này, bạn sẽ có một đoạn mã có thể tái sử dụng mà bạn có thể chèn vào bất kỳ dự án .NET nào tham chiếu Aspose.Words.

## Những gì bạn sẽ học

- Tạo một tài liệu Word trống từ đầu.  
- Chèn một hình chữ nhật và một hình ellipse bằng `DocumentBuilder`.  
- **Nhóm nhiều hình dạng** vào một `GroupShape`.  
- Sử dụng **append child to group** để xây dựng cấu trúc phân cấp.  
- Lưu tệp vào đĩa và xác minh kết quả.

Không cần kinh nghiệm trước với Aspose.Words, nhưng bạn nên có hiểu biết cơ bản về C# và phát triển .NET.

## Yêu cầu

| Yêu cầu | Lý do |
|-------------|--------|
| .NET 6.0 hoặc mới hơn | Cung cấp môi trường chạy cho mã C#. |
| Aspose.Words cho .NET (phiên bản mới nhất) | Cung cấp các lớp `Document`, `DocumentBuilder` và các lớp hình dạng. |
| Một IDE như Visual Studio 2022 (hoặc VS Code) | Giúp việc biên dịch và chạy mẫu dễ dàng hơn. |
| Quyền ghi vào một thư mục trên máy của bạn | Cần thiết cho lệnh `doc.save`. |

Cài đặt Aspose.Words qua NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Nhóm các hình dạng trong Word – hướng dẫn từng bước

Dưới đây là chương trình đầy đủ, có thể chạy được. Mỗi phần được giải thích chi tiết để bạn hiểu **tại sao** mã được viết như vậy, không chỉ **cái gì** nó làm.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Tại sao mỗi bước lại quan trọng

1. **Tạo một tệp Word trống** – Bắt đầu với một tài liệu sạch sẽ đảm bảo không có định dạng ẩn can thiệp vào vị trí của hình dạng.  
2. **Khởi tạo DocumentBuilder** – `DocumentBuilder` trừu tượng hoá việc thao tác node cấp thấp, cho phép bạn tập trung vào bố cục.  
3. **Chèn các hình dạng riêng lẻ** – Bạn cần các đối tượng riêng biệt (`insert rectangle shape` và một ellipse) trước khi có thể nhóm chúng. Điều chỉnh `Left` và `Top` đảm bảo chúng xuất hiện cạnh nhau.  
4. **Nhóm nhiều hình dạng** – Bằng cách tạo một `GroupShape` và sử dụng **append child to group**, bạn biến hai bản vẽ độc lập thành một đơn vị logic duy nhất. Di chuyển hoặc thay đổi kích thước nhóm sẽ ảnh hưởng đến cả hai đối tượng con đồng thời.  
5. **Lưu tài liệu** – Tệp cuối cùng, `GroupedShapes.docx`, có thể mở trong Microsoft Word để xác minh rằng hình chữ nhật và ellipse thực sự đã được nhóm (chọn một, cả hai sẽ di chuyển cùng nhau).

### Kết quả mong đợi

Mở `GroupedShapes.docx` trong Microsoft Word:

- Bạn sẽ thấy một hình chữ nhật và một ellipse đặt cạnh nhau.  
- Khi chọn bất kỳ hình nào, cả hai sẽ được đánh dấu, xác nhận chúng thuộc cùng một nhóm.  
- Nhóm có thể được kéo, thay đổi kích thước, hoặc định dạng như một đối tượng duy nhất.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Sơ đồ hình chữ nhật và ellipse đã được nhóm trong tài liệu Word"}

*Ảnh chụp màn hình minh họa các hình dạng đã được nhóm cuối cùng.*

---

## Chèn hình chữ nhật – tùy chỉnh kích thước và kiểu

Nếu bạn cần một hình chữ nhật với màu nền hoặc viền cụ thể, hãy sửa đổi đối tượng `Shape` sau khi chèn:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Các thuộc tính này là một phần của lớp `Shape`, và chúng hoạt động cho bất kỳ loại hình dạng nào, không chỉ hình chữ nhật. Điều chỉnh kiểu trước khi bạn **append child to group** đảm bảo nhóm kế thừa các thuộc tính trực quan bạn đã đặt.

---

## Nhóm nhiều hình dạng – xử lý hơn hai đối tượng

Ví dụ này nhóm một hình chữ nhật và một ellipse, nhưng bạn có thể thêm bất kỳ số lượng hình dạng nào:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Mẹo chuyên nghiệp:** Sau khi bạn đã xây dựng một nhóm phức tạp, bạn có thể khóa bố cục của nó để ngăn thay đổi vô tình:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – thứ tự quan trọng

Thứ tự bạn gọi `AppendChild` xác định Z‑order (hình nào xuất hiện trên cùng). Trong mẫu, hình chữ nhật được thêm đầu tiên, sau đó là ellipse, vì vậy ellipse sẽ phủ lên hình chữ nhật nếu chúng giao nhau. Thay đổi thứ tự chỉ cần gọi `RemoveChild` và thêm lại:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Tạo tệp Word trống – phương thức trợ giúp có thể tái sử dụng

Nếu ứng dụng của bạn thường xuyên cần một tài liệu mới, hãy đóng gói logic tạo ra:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Bạn có thể thay thế dòng `new Document()` trong chương trình chính bằng `CreateBlankWordFile()`. Điều này minh họa khái niệm **tạo tệp Word trống** một cách có thể tái sử dụng.

---

## Những lỗi thường gặp và cách tránh chúng

| Vấn đề | Tại sao xảy ra | Cách khắc phục |
|-------|----------------|----------------|
| Các hình xuất hiện ngoài trang | Giá trị mặc định của `Left`/`Top` là 0, đặt hình ở lề. | Đặt rõ `Left` và `Top` sau khi chèn. |
| Nhóm mất định dạng | Thay đổi một hình con sau khi đã thêm vào nhóm có thể phá vỡ bố cục của nhóm. | Áp dụng tất cả các thuộc tính hiển thị **trước** khi gọi `AppendChild`. |
| Tệp đã lưu rỗng | `DocumentBuilder` chưa bao giờ được dùng để thêm node, hoặc `doc.Save` được gọi trên một instance `Document` khác. | Kiểm tra bạn đang lưu cùng một `Document` mà bạn đã xây dựng. |
| Cảnh báo tương thích trong Word | Sử dụng các tính năng hình dạng mới hơn không được hỗ trợ |  |

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Nhóm Hình trong Tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Chèn Hình dạng trong Tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}