---
category: general
date: 2026-09-05
description: Tìm hiểu cách tạo tài liệu Word trống và thêm một hình chữ nhật có thể
  ẩn bằng Aspose.Words trong C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: vi
lastmod: 2026-09-05
og_description: Tạo tài liệu Word trống và chèn hình chữ nhật ẩn bằng Aspose.Words
  – hướng dẫn chi tiết từng bước cho các nhà phát triển C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Tạo tài liệu Word trống với hình chữ nhật ẩn
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Tạo một tài liệu Word trống và thêm một hình chữ nhật
url: /vi/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo một tài liệu Word trống và thêm một hình chữ nhật

Nếu bạn cần **tạo tài liệu Word trống** mà cũng chứa một hình dạng mà bạn không muốn hiển thị trong bố cục, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng Aspose.Words cho .NET. Bạn sẽ thấy một ví dụ đầy đủ, có thể chạy được, tạo một tài liệu mới, thêm một hình chữ nhật, ẩn hình đó và lưu tệp — không cần công cụ bổ sung nào.

Bài học bao gồm mọi thứ từ thiết lập dự án đến khắc phục các vấn đề thường gặp. Khi kết thúc, bạn sẽ có thể tạo một tệp Word trông như rỗng đối với người đọc nhưng vẫn chứa siêu dữ liệu ẩn, hữu ích cho các mục đích như watermark, lưu trữ XML tùy chỉnh, hoặc làm neo bố cục.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 SDK hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
* Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#)
* Giấy phép **Aspose.Words** NuGet đang hoạt động (bản dùng thử miễn phí đủ cho việc thử nghiệm)
* Kiến thức cơ bản về C# và khái niệm node trong tài liệu

Bạn có thể cài đặt thư viện bằng lệnh CLI sau:

```bash
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Giữ phiên bản Aspose.Words của bạn luôn cập nhật; API được sử dụng trong hướng dẫn này đã ổn định từ phiên bản 23.10.

## Cách tạo một tài liệu Word trống với Aspose.Words

Bước đầu tiên là khởi tạo một đối tượng `Document`. Một `Document` mới đại diện cho một **tài liệu Word trống** — không có đoạn văn, không có phần, chỉ có container tệp.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Tại sao điều này quan trọng:** Bắt đầu với một tài liệu sạch sẽ đảm bảo rằng hình dạng ẩn mà bạn sẽ thêm sau này sẽ không can thiệp vào nội dung hoặc kiểu dáng hiện có.

## Thêm một hình chữ nhật vào tài liệu

Tiếp theo chúng ta tạo một hình chữ nhật. Trong Aspose.Words, một shape là một node có thể được đặt ở bất kỳ vị trí nào trong cây tài liệu, và nó có thể được cấu hình kích thước, màu nền, kiểu đường viền và khả năng hiển thị.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Mã trên tạo ra một hình chữ nhật có thể nhìn thấy. Ở bước này bạn có thể chèn nó vào tài liệu bằng `builder.InsertNode(rectangle)`. Tuy nhiên, vì chúng ta muốn hình dạng này ẩn, chúng ta sẽ điều chỉnh thuộc tính `Hidden` trước khi chèn.

## Cách ẩn shape trong tài liệu Word

Word cung cấp thuộc tính `Hidden` cho các node shape. Khi được đặt thành `true`, shape sẽ không xuất hiện trong bố cục trang, nhưng vẫn là một phần của XML tài liệu. Đây là cốt lõi của yêu cầu **cách ẩn shape**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Giải thích:** Đặt `Hidden = true` sẽ thêm thuộc tính `<w:hide>` vào XML của shape. Các trình xử lý Word sẽ bỏ qua shape khi render, nhưng shape vẫn có thể được truy cập bằng mã hoặc qua chế độ xem XML của Word.

## Chèn shape ẩn vào tài liệu trống

Bây giờ chúng ta đặt hình chữ nhật ẩn vào cây tài liệu. Vì tài liệu vẫn còn trống, shape sẽ trở thành node đầu tiên trong main story.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Nếu bạn mở tệp kết quả trong Microsoft Word, sẽ thấy một trang dường như trống. Shape vẫn tồn tại, nhưng không hiển thị.

## Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.pdf`, `.odt`, …). Trong hướng dẫn này chúng ta sẽ dùng định dạng DOCX hiện đại.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Kết quả mong đợi

Mở `HiddenRectangle.docx` trong Word:

* Tài liệu hiển thị trống (không có shape hay văn bản nào nhìn thấy).
* Nếu bạn kiểm tra tệp bằng công cụ như **Open XML SDK** hoặc **Word XML Viewer**, sẽ thấy phần tử `<w:pict>` chứa hình chữ nhật với thuộc tính `hidden`.

![blank word document with hidden rectangle shape](image.png){: .align-center alt="blank word document with hidden rectangle shape"}

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các `using` cần thiết, xử lý lỗi và chú thích.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Chạy chương trình (`dotnet run`) và kiểm tra tệp đầu ra. Console sẽ thông báo vị trí lưu tệp.

## Các câu hỏi thường gặp và trường hợp đặc biệt

### Có thể ẩn nhiều shape cùng lúc không?

Có. Tạo mỗi shape, đặt `Hidden = true`, và chèn chúng theo thứ tự. Cờ ẩn hoạt động riêng cho từng node, vì vậy việc trộn lẫn shape ẩn và hiển thị trong cùng một tài liệu là được hỗ trợ.

### Nếu tôi muốn shape chỉ ẩn trong chế độ xem in thì sao?

Word phân biệt giữa **hiển thị** và **in** thông qua thuộc tính `DisplayWhen`. Aspose.Words không cung cấp API trực tiếp cho cờ này, nhưng bạn có thể chỉnh sửa XML nền:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Chỉ sử dụng cách này khi bạn thực sự cần chế độ hiển thị chỉ dành cho bản in.

### Shape ẩn có ảnh hưởng tới kích thước tệp không?

Một shape ẩn sẽ thêm cùng một payload XML như một shape hiển thị, vì vậy tăng kích thước tệp là tương đương. Tuy nhiên, vì shape

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, dựa trên các kỹ thuật đã trình bày trong bài viết này. Mỗi tài nguyên bao gồm mã mẫu hoàn chỉnh với giải thích chi tiết từng bước, giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}