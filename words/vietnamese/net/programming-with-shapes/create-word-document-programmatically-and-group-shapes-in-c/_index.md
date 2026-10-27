---
category: general
date: 2026-08-10
description: Tạo tài liệu Word bằng cách lập trình sử dụng Aspose.Words, học cách
  nhóm nhiều hình dạng trong Word, thêm hình chữ nhật vào Word và tạo một nhóm hình
  dạng trong C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: vi
lastmod: 2026-08-10
og_description: Tạo tài liệu Word bằng lập trình với Aspose.Words. Hướng dẫn này chỉ
  cho bạn cách nhóm nhiều hình dạng trong Word, thêm hình chữ nhật vào Word và nhúng
  một điều khiển nội dung dạng văn bản thuần, tất cả bằng C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Tạo tài liệu Word bằng lập trình – nhóm các hình dạng trong C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Tạo tài liệu Word bằng cách lập trình và nhóm các hình dạng trong C#
url: /vi/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình và nhóm các hình dạng trong C#

Nếu bạn cần **create word document programmatically**, hướng dẫn này sẽ chỉ cho bạn cách tạo tệp DOCX bằng Aspose.Words và **group multiple shapes word** lại với nhau. Chúng tôi cũng sẽ đề cập đến **add rectangle to word** và **how to create group shape** chứa cả hình chữ nhật và hình elip, cộng với một StructuredDocumentTag dạng văn bản thuần cho người dùng nhập dữ liệu.

Bạn sẽ có một tệp Word sẵn sàng sử dụng chứa một hình dạng nhóm hình chữ nhật‑elip và một điều khiển nội dung cho phép người dùng nhập tên. Không cần chỉnh sửa thủ công trong Word sau khi mã chạy.

## Những gì bạn cần

- .NET 6.0 hoặc mới hơn (mẫu này nhắm tới .NET 6, nhưng bất kỳ phiên bản .NET gần đây nào cũng hoạt động)
- Giấy phép Aspose.Words cho .NET (bản dùng thử miễn phí hoạt động cho việc thử nghiệm)
- Visual Studio 2022 hoặc bất kỳ IDE C# nào bạn thích
- Kiến thức cơ bản về cú pháp C#

## Tạo tài liệu Word bằng chương trình – quy trình tổng thể

Quá trình bao gồm ba giai đoạn logic:

1. **Initialize** một `Document` và một `DocumentBuilder` – nền tảng cho bất kỳ tệp Word nào bạn tạo.
2. **Build a group shape** chứa một hình chữ nhật và một hình elip – minh họa **group multiple shapes word** và **how to create group shape**.
3. **Insert a StructuredDocumentTag (SDT)** – một điều khiển nội dung dạng văn bản thuần cho phép người dùng cuối nhập dữ liệu, minh họa **add rectangle to word** như một phần của bố cục tài liệu tổng thể.

Dưới đây là mã hoàn chỉnh, có thể chạy được kèm theo phần phân tích từng bước.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Bước 1 – Khởi tạo tài liệu và builder
`Document` đại diện cho toàn bộ tệp DOCX, trong khi `DocumentBuilder` cung cấp một API tiện lợi để thêm nội dung. Khởi tạo chúng là yêu cầu đầu tiên mỗi khi bạn **create word document programmatically**.

> **Pro tip:** Nếu bạn dự định tái sử dụng cùng một tài liệu cho nhiều thao tác, hãy giữ một thể hiện `DocumentBuilder` duy nhất để tránh việc tạo đối tượng không cần thiết.

### Bước 2 – Tạo một container nhóm hình dạng
Một `Shape` với `ShapeType.Group` hoạt động như một canvas có thể chứa các hình dạng khác. Đặt `Width` và `Height` xác định hộp bao cho nhóm. Đây là cốt lõi của **how to create group shape** trong Aspose.Words.

> **Edge case:** Nếu chiều rộng của nhóm nhỏ hơn tổng chiều rộng của các đối tượng con, các đối tượng con sẽ bị cắt. Luôn làm cho nhóm đủ lớn để chứa mọi hình dạng con.

### Bước 3 – Thêm hình chữ nhật vào Word
Một hình chữ nhật được tạo bằng `ShapeType.Rectangle`. Các thuộc tính `Left` và `Top` của nó định vị nó tương đối với gốc của nhóm. Bước này minh họa **add rectangle to word** và cho thấy cách bạn có thể kiểm soát vị trí chính xác.

> **Common mistake:** Quên đặt `Left`/`Top` sẽ khiến hình chữ nhật xuất hiện tại gốc mặc định của nhóm (0,0), có thể chồng lên các đối tượng con khác.

### Bước 4 – Thêm một elip (hình tròn) vào nhóm
Một elip được thêm theo cách tương tự như hình chữ nhật, nhưng với `ShapeType.Ellipse`. `Left = 210` di chuyển nó sang bên phải của hình chữ nhật, tạo thành một cặp hình dạng rõ ràng về mặt hình ảnh trong cùng một nhóm.

> **Why use a group?** Việc nhóm cho phép bạn di chuyển, xoay hoặc thay đổi kích thước cả hai hình dạng cùng một lúc bằng một thao tác duy nhất sau này, giữ nguyên bố cục tương đối của chúng.

### Bước 5 – Chèn nhóm hình dạng đã hoàn thành vào tài liệu
`builder.InsertNode(groupShape)` đặt toàn bộ nhóm tại vị trí con trỏ hiện tại. Vì nhóm đã chứa các đối tượng con, bạn không cần các lời gọi chèn bổ sung cho hình chữ nhật hoặc elip.

### Bước 6 – Tạo StructuredDocumentTag (SDT) dạng văn bản thuần
StructuredDocumentTag là một điều khiển nội dung mà người dùng cuối có thể điền khi tài liệu được mở trong Word. Đặt `Title = "CustomerName"` cung cấp cho điều khiển một định danh có ý nghĩa, hữu ích cho việc trích xuất dữ liệu sau này.

> **Why a plain‑text SDT?** Nó giới hạn đầu vào chỉ là văn bản thuần, ngăn ngừa việc định dạng ngẫu nhiên có thể làm hỏng quá trình xử lý sau này.

### Bước 7 – Lưu tài liệu
`doc.Save("GroupAndSDT.docx")` ghi tệp ra đĩa. DOCX kết quả chứa các hình dạng đã nhóm và SDT. Mở tệp trong Microsoft Word sẽ hiển thị một hình chữ nhật bên cạnh một vòng tròn, cả hai có thể chọn như một đối tượng duy nhất, tiếp theo là một placeholder “Enter name here …”.

#### Kết quả mong đợi
- Một tệp có tên **GroupAndSDT.docx** trong thư mục thực thi.
- Trong Word: một nhóm hình dạng (hình chữ nhật + elip) mà bạn có thể di chuyển như một đơn vị.
- Ngay dưới nhóm, một điều khiển nội dung màu xám nhạt yêu cầu người dùng nhập tên.

## Các biến thể bổ sung và thực hành tốt nhất

### Sử dụng các loại hình dạng khác
Bạn có thể thay thế `ShapeType.Rectangle` hoặc `ShapeType.Ellipse` bằng bất kỳ `ShapeType` nào khác (ví dụ, `ShapeType.Polygon`, `ShapeType.Line`). Logic nhóm vẫn giống nhau.

### Setting fill color and borders
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Thêm màu nền và đường viền cải thiện sự phân biệt trực quan, đặc biệt khi tài liệu được chia sẻ với các bên không chuyên môn.

### Rotating the entire group
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Xoay nhóm hiệu quả hơn so với việc xoay từng đối tượng con riêng lẻ.

### Exporting to PDF
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Tất cả các hình dạng đã nhóm và SDT (được hiển thị dưới dạng trường văn bản) sẽ xuất hiện trong PDF.

## Những khó khăn thường gặp và cách tránh

| Triệu chứng | Nguyên nhân | Cách khắc phục |
|------------|-------------|----------------|
|            |             |                |

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo nhóm hình dạng trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tạo tài liệu Word trống với hình chữ nhật có bóng – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}