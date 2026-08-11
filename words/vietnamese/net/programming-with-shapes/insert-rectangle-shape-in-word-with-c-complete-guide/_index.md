---
category: general
date: 2026-08-10
description: Chèn hình chữ nhật vào Word bằng C#. Tìm hiểu cách ẩn hình, ẩn hình trong
  Word và tạo hình ẩn bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: vi
lastmod: 2026-08-10
og_description: Chèn hình chữ nhật trong Word bằng C#. Hướng dẫn này giải thích cách
  ẩn hình, ẩn hình trong Word và tạo hình ẩn với các ví dụ mã đầy đủ.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Chèn hình chữ nhật trong Word bằng C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Chèn hình chữ nhật trong Word bằng C# – hướng dẫn đầy đủ
url: /vi/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn hình chữ nhật trong Word bằng C# – hướng dẫn đầy đủ

Nếu bạn cần **chèn hình chữ nhật** vào tài liệu Word bằng C#, hướng dẫn này sẽ chỉ cho bạn các bước chính xác. Bạn cũng sẽ học **cách ẩn hình** để nó không xuất hiện trong tệp cuối cùng, trả lời câu hỏi thường gặp **ẩn hình trong Word** và trình bày cách **tạo hình ẩn** một cách lập trình.

Bài hướng dẫn bao gồm mọi thứ từ việc thiết lập Aspose.Words SDK đến việc xác minh rằng hình đã được ẩn. Khi kết thúc bài viết, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ dự án .NET nào.

## Yêu cầu trước

- .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt (mã cũng hoạt động với .NET Framework 4.6+)
- Giấy phép Aspose.Words for .NET hợp lệ hoặc khóa đánh giá tạm thời
- Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ C#)
- Kiến thức cơ bản về cú pháp C# và Document Object Model (DOM) của các tệp Word

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Bước 1: Tạo tài liệu trống mới và DocumentBuilder

Hoạt động đầu tiên là khởi tạo một đối tượng `Document`. `DocumentBuilder` cung cấp một API tiện lợi để chèn nội dung như hình dạng, đoạn văn và bảng.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Tại sao điều này quan trọng:** `Document` đại diện cho toàn bộ tệp .docx, trong khi `DocumentBuilder` duy trì một con trỏ để theo dõi vị trí sẽ chèn phần tử tiếp theo. Khởi tạo cả hai đối tượng là nền tảng cho bất kỳ tác vụ tự động hoá Word nào.

## Bước 2: Chèn hình chữ nhật

Bây giờ bạn chèn hình chữ nhật. Phương thức `InsertShape` yêu cầu loại hình và kích thước của nó tính bằng điểm (1 point ≈ 1/72 inch). Kích thước **200 × 100 points** tạo ra một hình chữ nhật khoảng 2.78 × 1.39 inch.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Tại sao điều này quan trọng:** Đối tượng `Shape` nhận được có thể cấu hình hoàn toàn — màu sắc, viền, văn bản và khả năng hiển thị đều có thể thay đổi trước khi lưu tài liệu.

## Bước 3: Ẩn hình

Để ngăn hình chữ nhật hiển thị hoặc in ra, đặt thuộc tính `Hidden` của nó thành `true`. Thuộc tính này ánh xạ trực tiếp tới thuộc tính “Hidden” của Word, mà Word tôn trọng cả trong chế độ xem và in.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Tại sao điều này quan trọng:** Đặt `Hidden` là cách tiêu chuẩn để **ẩn hình trong Word** mà không xóa nó khỏi cấu trúc tài liệu. Hình vẫn có thể truy cập được bởi mã, cho phép các thao tác sau này như định dạng có điều kiện hoặc bật/tắt hiển thị dựa trên dữ liệu.

## Bước 4: Lưu tài liệu

Cuối cùng, lưu tài liệu vào đĩa. Chọn bất kỳ thư mục nào bạn muốn; ví dụ sử dụng một đường dẫn placeholder mà bạn nên thay thế bằng đường dẫn thực.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Tại sao điều này quan trọng:** Việc lưu hoàn thiện tệp và ghi cờ ẩn vào Open XML nền. Khi bạn mở tài liệu trong Microsoft Word, hình chữ nhật sẽ không hiển thị, xác nhận rằng bạn đã **tạo hình ẩn** thành công.

## Bước 5: Xác minh hình ẩn

Mở tệp `HiddenShape.docx` đã tạo trong Microsoft Word:

1. Đi tới **File → Options → Display** và đảm bảo mục *“Show hidden text”* **không được chọn**.  
2. Hình chữ nhật không nên hiển thị trên bất kỳ trang nào.  
3. Để kiểm tra lại, bật mục *“Show hidden text”*; hình chữ nhật sẽ xuất hiện với viền đứt nét nhẹ, chứng minh rằng hình tồn tại nhưng đã bị ẩn.

Nếu hình chữ nhật vẫn hiển thị, hãy xác nhận rằng bạn đã lưu tệp sau khi đặt `Hidden = true` và bạn đang mở đúng tệp.

## Ví dụ đầy đủ có thể chạy

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép, dán và chạy ngay.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Kết quả mong đợi:** Console sẽ in ra đường dẫn tệp và một lời nhắc ngắn. Khi tệp được mở trong Word, hình chữ nhật sẽ không hiển thị trừ khi bật chế độ hiển thị văn bản ẩn.

## Các câu hỏi thường gặp và trường hợp đặc biệt

### Tôi có thể ẩn chỉ viền mà vẫn giữ phần nền hiển thị không?

Có. Thay vì đặt `Hidden = true`, bạn có thể đặt `rectangle.LineFormat.Visible = false` để ẩn viền trong khi vẫn giữ màu nền. Đây là một biến thể của **cách ẩn hình** mà vẫn giữ một phần giao diện trực quan.

### Thuộc tính ẩn có hoạt động trong các phiên bản Word cũ hơn (2003, 2007) không?

Thuộc tính ẩn là một phần của đặc tả Open XML được giới thiệu cùng với Word 2007. Các tài liệu được lưu ở định dạng nhị phân `.doc` cũ sẽ không giữ lại cờ này. Để hỗ trợ các định dạng legacy, lưu tài liệu dưới dạng `.docx` và, nếu cần, chuyển đổi sau này bằng `SaveFormat.Doc` của Aspose.Words.

### Nếu tôi cần ẩn nhiều hình cùng lúc thì sao?

Duyệt qua collection `Document.GetChildNodes(NodeType.Shape, true)` và đặt `Hidden = true` cho mỗi hình đáp ứng tiêu chí của bạn (ví dụ: một `ShapeType` cụ thể hoặc giá trị `AlternativeText` tùy chỉnh).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Việc ẩn hình có ảnh hưởng đến hiệu năng không?

Thuộc tính ẩn chỉ thêm một thuộc tính XML rất nhỏ; nó không ảnh hưởng đến tốc độ render. Tuy nhiên, một số lượng lớn các đối tượng ẩn có thể làm tăng kích thước tệp một chút. Hãy loại bỏ các hình bạn không bao giờ cần để giữ tài liệu gọn nhẹ.

## Mẹo và thực tiễn tốt nhất

- **Đặt tên có ý nghĩa cho hình** bằng cách sử dụng `rectangle.Name = "MyHiddenRectangle"`; điều này giúp khi bạn tìm kiếm hình trong DOM sau này.
- **Đặt `AlternativeText`** thành một thẻ tùy chỉnh (ví dụ: `"HiddenShape"`). Điều này cho phép bạn xác định hình mà không cần dựa vào chỉ mục của nó.
- **Bao quanh mã bằng khối try‑catch** để xử lý lỗi giấy phép hoặc ngoại lệ I/O một cách nhẹ nhàng.
- **Giải phóng Document** sau khi lưu nếu bạn đang xử lý nhiều tệp trong vòng lặp để giải phóng tài nguyên không quản lý: `document.Dispose();`.

## Kết luận

Bây giờ bạn đã biết cách **chèn hình chữ nhật** vào tài liệu Word bằng C#, cách **ẩn hình trong Word**, và cách **tạo hình ẩn** vẫn là một phần của cấu trúc tài liệu nhưng không hiển thị với người dùng cuối. Ví dụ đầy đủ, có thể chạy được, minh họa toàn bộ quy trình, từ tạo tài liệu đến xác minh.

Tiếp theo, bạn có thể khám phá **cách ẩn hình** dựa trên đầu vào của người dùng, hoặc kết hợp các hình ẩn với content controls để tạo tài liệu động. Bạn cũng có thể áp dụng kỹ thuật này cho các loại hình khác như elip, mũi tên, hoặc các bản vẽ tùy chỉnh.

Hãy tự do thử nghiệm với các kích thước, màu sắc và cài đặt hiển thị khác nhau. Nếu gặp bất kỳ vấn đề nào, hãy xem lại các bước ở trên hoặc tham khảo tài liệu Aspose.Words để biết chi tiết API sâu hơn. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}