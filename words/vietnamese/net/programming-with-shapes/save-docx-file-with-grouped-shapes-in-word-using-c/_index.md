---
category: general
date: 2026-08-04
description: Lưu tệp docx một cách lập trình trong khi thêm hình chữ nhật và nhóm
  các hình dạng trong Word. Học cách đặt kích thước hình dạng và tạo hộp văn bản một
  cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: vi
lastmod: 2026-08-04
og_description: Lưu tệp docx bằng C# bằng cách thêm hình chữ nhật, nhóm các hình trong
  Word, đặt kích thước hình, và tạo hộp văn bản một cách lập trình.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Lưu tệp docx có các hình dạng được nhóm trong Word – Hướng dẫn chi tiết
  từng bước C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Lưu tệp docx có các hình dạng được nhóm trong Word bằng C#
url: /vi/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tệp docx với các hình dạng được nhóm trong Word bằng C#

Nếu bạn cần **save docx file** chứa một số hình dạng được sắp xếp cùng nhau, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng C#. Bạn sẽ học cách **add rectangle shape**, nhóm nhiều hình dạng trong tài liệu Word, **set shape dimensions**, và **create textbox programmatically**. Giải pháp hoạt động với Aspose.Words for .NET mới nhất và chạy trên .NET 6 hoặc phiên bản mới hơn.

Bài hướng dẫn sẽ đi qua từng bước, từ thiết lập dự án đến lệnh `doc.Save` cuối cùng. Khi hoàn thành, bạn sẽ có một đoạn mã có thể tái sử dụng mà bạn có thể dán vào bất kỳ dự án console hoặc ASP.NET nào. Không cần script bên ngoài hay chỉnh sửa thủ công tệp DOCX.

## Yêu cầu trước

* .NET 6 SDK (hoặc mới hơn) đã được cài đặt.
* Giấy phép hợp lệ cho **Aspose.Words for .NET** (bản dùng thử miễn phí hoạt động cho việc thử nghiệm).
* Visual Studio 2022, VS Code, hoặc bất kỳ IDE nào có thể xây dựng dự án .NET.

Mã chỉ sử dụng namespace Aspose.Words, vì vậy không cần gói NuGet bổ sung.

## Lưu tệp docx với các hình dạng được nhóm trong Word

Cốt lõi của giải pháp là xây dựng một `GroupShape` chứa hình chữ nhật và textbox, sau đó chèn nhóm vào tài liệu và gọi `doc.Save`. Các phần sau sẽ chia quá trình thành các bước dễ quản lý.

### 1. Tạo tài liệu mới và một builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Tại sao bước này quan trọng* – Một đối tượng `Document` mới đại diện cho một tệp *.docx* trống. `DocumentBuilder` cung cấp các phương thức cấp cao như `InsertNode`, mà chúng ta sẽ dùng để đặt nhóm hình dạng.

### 2. Thêm hình chữ nhật vào nhóm

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Tại sao bước này quan trọng* – Thao tác **add rectangle shape** cho thấy cách định nghĩa một phần tử trực quan với kích thước và vị trí chính xác. Hình chữ nhật nằm trong `group`, vì vậy việc di chuyển nhóm sau này sẽ tự động di chuyển hình chữ nhật.

### 3. Nhóm các hình dạng trong tài liệu Word

Lớp `GroupShape` tổng hợp nhiều đối tượng vẽ. Việc nhóm hữu ích khi bạn muốn xử lý nhiều đối tượng như một đơn vị duy nhất (ví dụ: di chuyển, xoay, hoặc sao chép chúng cùng nhau).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Tại sao chúng ta nhóm* – Việc nhóm giảm độ phức tạp của bố cục. Thay vì định vị từng hình dạng riêng lẻ trên trang, bạn chỉ cần điều chỉnh `Left`, `Top`, `Width`, và `Height` của nhóm một lần.

### 4. Đặt kích thước hình dạng để bố cục chính xác

Cả nhóm và các hình dạng con của nó đều cần kích thước rõ ràng; nếu không Word sẽ áp dụng kích thước mặc định có thể không phù hợp với thiết kế của bạn.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Tại sao chúng ta đặt kích thước* – Đo lường chính xác đảm bảo rằng hình chữ nhật và textbox không chồng lên nhau một cách không mong muốn và rằng **save docx file** cuối cùng khớp với bố cục dự định.

### 5. Tạo textbox một cách lập trình bên trong nhóm

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Tại sao bước này quan trọng* – Phân đoạn **create textbox programmatically** cho thấy cách nhúng văn bản phong phú vào một hình dạng. Sử dụng `Paragraph` và `Run` cho phép bạn kiểm soát hoàn toàn việc định dạng sau này.

### 6. Chèn nhóm hình dạng và **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Tại sao bước cuối cùng này quan trọng* – Lệnh `InsertNode` đặt các hình dạng đã nhóm chính xác tại vị trí con trỏ của builder. Phương thức `doc.Save` thực hiện thao tác **save docx file**, ghi một tài liệu Word đầy đủ tính năng ra đĩa.

> **Kết quả:** Mở *GroupShape.docx* trong Microsoft Word sẽ hiển thị một hình chữ nhật ở phía trái và một textbox ở phía phải, cả hai được khóa cùng nhau trong một nhóm duy nhất. Bạn có thể di chuyển nhóm như một đơn vị, thay đổi kích thước, hoặc áp dụng định dạng bổ sung.

## Ví dụ đầy đủ, có thể chạy

Sao chép mã dưới đây vào một dự án console mới (`dotnet new console`) và chạy `dotnet run`. Chương trình sẽ tạo `GroupShape.docx` trong thư mục đầu ra của dự án.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Kết quả mong đợi

* Một tệp có tên **GroupShape.docx** xuất hiện trong thư mục đầu ra.
* Khi mở tệp, sẽ hiển thị một hình dạng hình chữ nhật ở phía trái và một textbox chứa “Grouped text” ở phía phải, cả hai được khóa cùng nhau.
* Khi chọn bất kỳ hình dạng nào, cả nhóm sẽ di chuyển, xác nhận rằng chức năng **group shapes word** hoạt động như mong đợi.

## Các biến thể phổ biến và trường hợp đặc biệt

| Situation | Recommendation |
|-----------|----------------|
| Cần nhiều hơn hai hình dạng | Thêm các đối tượng `Shape` bổ sung vào `group` trước khi gọi `builder.InsertNode`. |
| Muốn nhóm xuất hiện trên một trang cụ thể | Di chuyển con trỏ của builder bằng `builder.MoveToDocumentEnd()` hoặc `builder.MoveToPage(pageNumber)`. |
| Yêu cầu đơn vị khác (ví dụ: centimet) | Sử dụng `ConvertUtil.InchToPoint(1.0)` để chuyển đổi inch sang point, đơn vị mà Word mong đợi. |
| Muốn textbox bao quanh văn bản | Đặt `textBox.TextBoxWrap = TextBoxWrapType.Square` sau khi tạo textbox. |
| Làm việc với các phiên bản .NET Framework cũ hơn | Cùng API hoạt động với .NET Framework 4.7+, nhưng hãy chắc chắn bạn tham chiếu đúng phiên bản Aspose.Words. |

**Mẹo:** Luôn đặt `Width` và `Height` của nhóm *sau* khi đã thêm tất cả các hình dạng con. Điều này đảm bảo nhóm bao trọn nội dung, ngăn việc cắt xén khi tài liệu được mở trong Word.

## Kết luận

Bây giờ bạn đã biết cách **save docx file** đồng thời **add rectangle shape**, **group shapes word**, **set shape dimensions**, và **create textbox programmatically** bằng Aspose.Words cho .NET. Ví dụ hoàn chỉnh minh họa một mẫu sạch sẽ, có thể tái sử dụng mà bạn có thể áp dụng cho các bố cục phức tạp hơn, như biểu đồ, hình ảnh,

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Hướng dẫn Shape Shadow của Aspose.Words – Thêm bóng cho Shape trong Word bằng C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}