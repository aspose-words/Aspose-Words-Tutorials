---
category: general
date: 2026-08-07
description: Cách nhóm các hình dạng trong Word bằng Aspose.Words và thêm các hình
  dạng vào tài liệu Word bằng C#. Hãy làm theo hướng dẫn từng bước này để có mã sạch,
  có thể tái sử dụng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: vi
lastmod: 2026-08-07
og_description: Cách nhóm các hình dạng trong Word bằng Aspose.Words cho .NET. Hướng
  dẫn này chỉ cho bạn cách thêm các hình dạng vào tài liệu Word, nhóm chúng lại và
  lưu tệp với mã C# rõ ràng.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Cách nhóm các hình dạng trong Word – hướng dẫn nhanh C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cách nhóm các hình dạng trong Word và thêm hình dạng vào tài liệu Word
url: /vi/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Word và thêm hình dạng vào tài liệu Word

Nếu bạn cần **how to group shapes in Word**, hướng dẫn này sẽ đưa bạn qua toàn bộ quy trình sử dụng Aspose.Words cho .NET. Bạn cũng sẽ học **add shapes to Word document** chỉ với vài dòng mã C#, vì vậy kết quả sẵn sàng cho bất kỳ kịch bản báo cáo hay tạo mẫu nào.

Bài hướng dẫn bao gồm mọi thứ bạn cần: các gói NuGet bắt buộc, một tệp nguồn đầy đủ, và giải thích lý do mỗi bước quan trọng. Khi hoàn thành, bạn có thể tạo một tệp DOCX chứa một hình chữ nhật và một hình elip được kết hợp thành một nhóm hình duy nhất.

## Yêu cầu trước

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt  
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ .NET)  
* Gói NuGet Aspose.Words cho .NET (`Aspose.Words`) – bản dùng thử miễn phí hoạt động cho việc thử nghiệm, nhưng giấy phép sẽ loại bỏ các dấu nước đánh giá  

Các mục này là những phụ thuộc bên ngoài duy nhất cho **add shapes to Word document**.

## Cách nhóm các hình dạng trong Word

Cốt lõi của giải pháp là tạo các hình dạng riêng lẻ, đặt chúng trên trang, và sau đó bao bọc chúng trong một `GroupShape`. Các bước sau phản ánh thứ tự logic của mã.

### Bước 1: Tạo tài liệu và builder

Đối tượng `Document` đại diện cho toàn bộ tệp DOCX. `DocumentBuilder` cung cấp một API tiện lợi để chỉnh sửa tài liệu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Tiêu đề quan trọng*: `Document` là container cho tất cả các thành phần Word. `DocumentBuilder` theo dõi vị trí con trỏ hiện tại, điều này cần thiết khi bạn chèn hình dạng đã nhóm sau này.

### Bước 2: Thêm hình chữ nhật

Một hình chữ nhật được tạo bằng cách chỉ định `ShapeType.Rectangle`. Chiều rộng, chiều cao và vị trí được đặt bằng điểm (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Tiêu đề quan trọng*: Đặt `StrokeColor` làm cho hình dạng hiển thị khi tài liệu được mở. Bạn cũng có thể tô đầy hình bằng `FillColor` nếu cần một nội thất đồng nhất.

### Bước 3: Thêm hình elip

Hình elip sử dụng `ShapeType.Ellipse`. Kích thước và vị trí của nó độc lập với hình chữ nhật, cho phép bạn kiểm soát bố cục cuối cùng của nhóm.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Tiêu đề quan trọng*: Bằng cách đặt vị trí elip ở `Left = 120`, nó không chồng lên hình chữ nhật, làm cho nhóm trở nên rõ ràng về mặt hình ảnh.

### Bước 4: Nhóm hai hình dạng

`GroupShape` hoạt động như một container coi các phần tử con của nó như một đối tượng duy nhất. Đây là thao tác thiết yếu cho **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Tiêu đề quan trọng*: Nhóm cho phép bạn di chuyển, thay đổi kích thước hoặc xoay cả hai hình dạng cùng nhau. Bất kỳ biến đổi nào được áp dụng cho `groupShape` sẽ lan tới các phần tử con.

### Bước 5: Chèn nhóm hình dạng vào tài liệu

`DocumentBuilder.InsertNode` đặt `GroupShape` tại vị trí con trỏ hiện tại. Vì chúng ta chưa di chuyển builder, nhóm sẽ xuất hiện ở đầu trang đầu tiên.

```csharp
builder.InsertNode(groupShape);
```

*Tiêu đề quan trọng*: Chèn node trực tiếp tránh việc cần một đoạn văn hoặc ô bảng riêng. Nhóm trở thành một phần của luồng tài liệu.

### Bước 6: Lưu tài liệu

Cuối cùng, ghi tệp DOCX ra đĩa. Sử dụng đường dẫn đầy đủ mà ứng dụng của bạn có thể ghi vào.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Tiêu đề quan trọng*: `doc.Save` hoàn thiện mọi thay đổi. Tệp kết quả có thể được mở trong Microsoft Word, LibreOffice, hoặc bất kỳ trình xem nào hỗ trợ DOCX.

## Tệp nguồn đầy đủ

Sao chép mã bên dưới vào một dự án console mới (`dotnet new console`) và chạy nó. Chương trình sẽ tạo một tệp có tên `GroupShape.docx` chứa một hình chữ nhật và một hình elip đã được nhóm.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Kết quả mong đợi

Mở `GroupShape.docx`. Bạn sẽ thấy một đối tượng hình ảnh duy nhất chứa một hình chữ nhật màu xanh dương ở phía trái và một hình elip màu xanh lá ở phía phải. Khi chọn đối tượng trong Word, cả hai hình sẽ được đánh dấu cùng lúc—chứng minh rằng **how to group shapes in Word** đã thành công.

## Các câu hỏi thường gặp và trường hợp đặc biệt

* **Tôi có thể thêm nhiều hơn hai hình không?**  
  Có. Gọi `groupShape.AppendChild` cho mỗi `Shape` bổ sung trước khi chèn nhóm.

* **Nếu tôi cần xoay nhóm thì sao?**  
  Đặt `groupShape.RotationAngle = 45;` (góc tính bằng độ) sau khi nhóm đã được tạo.

* **Tôi có cần gọi `doc.UpdatePageLayout()` không?**  
  Không cần cho trường hợp này. Bố cục sẽ tự động cập nhật khi tài liệu được lưu.

* **Giấy phép ảnh hưởng như thế nào đến mã?**  
  Với giấy phép Aspose.Words hợp lệ (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) tài liệu được tạo sẽ không có dấu nước đánh giá.

## Kết luận

Bây giờ bạn đã biết **how to group shapes in Word** và **add shapes to Word document** bằng cách sử dụng Aspose.Words cho .NET. Bài hướng dẫn đã bao gồm việc tạo tài liệu, định nghĩa các hình dạng riêng lẻ, nhóm chúng, chèn nhóm vào tài liệu và lưu tệp.  

Từ đây bạn có thể thử nghiệm với:

* Thêm hộp văn bản hoặc hình ảnh vào nhóm  
* Thay đổi màu nền, kiểu đường viền hoặc hiệu ứng bóng  
* Nhóm các hình dạng trong bảng hoặc phần đầu trang  

Các mở rộng này cho phép bạn xây dựng các mẫu Word tinh vi một cách lập trình trong khi giữ mã nguồn sạch sẽ và dễ bảo trì. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Word Document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}