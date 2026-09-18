---
category: general
date: 2026-09-18
description: Tạo một tài liệu Word trống và ẩn một hình ellipse bằng Aspose.Words.
  Tìm hiểu cách ẩn hình trong Word, cách chèn ellipse và tạo hình ẩn nhanh chóng.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: vi
lastmod: 2026-09-18
og_description: Tạo một tài liệu Word trống và ẩn một hình elip trong Word. Hướng
  dẫn này sẽ chỉ cho bạn từng bước cách chèn hình elip, ẩn hình trong Word và tạo
  hình ẩn bằng Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Tạo tài liệu Word trống có hình ellipse ẩn
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo tài liệu Word trống có hình ellipse ẩn
url: /vi/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống với hình ellipse ẩn

Nếu bạn cần **tạo một tài liệu Word trống** chứa một hình dạng mà bạn không muốn hiển thị trong bố cục, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác. Bằng cách sử dụng Aspose.Words for .NET, bạn có thể chèn một ellipse một cách lập trình và sau đó ẩn hình dạng để tài liệu vẫn trông rỗng về mặt hình ảnh trong khi vẫn giữ dữ liệu hình dạng.

Trong tutorial này bạn sẽ học:

* cách **tạo đối tượng tài liệu Word trống**,
* cách **chèn ellipse** bằng `DocumentBuilder`,
* cách **ẩn hình dạng trong Word** để nó không ảnh hưởng đến trang,
* cách **tạo đối tượng hình dạng ẩn** để xử lý sau này.

Các bước này hoạt động với .NET 6+ và phiên bản Aspose.Words mới nhất (23.9 tại thời điểm viết). Không cần cài đặt Office bổ sung.

## Prerequisites

* Visual Studio 2022 (hoặc bất kỳ IDE C# nào)
* .NET 6 SDK hoặc phiên bản mới hơn
* Gói NuGet Aspose.Words for .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
* Kiến thức cơ bản về C# và các khái niệm tài liệu Word

## Step 1: Create a blank Word document

Điều đầu tiên bạn phải làm là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho một tệp `.docx` trống và là nền tảng cho mọi thao tác tiếp theo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Việc **tạo tài liệu Word trống** cung cấp cho bạn một canvas sạch – không đoạn văn, không phần, chỉ có cấu trúc gói cơ bản. Đây là điểm khởi đầu lý tưởng khi bạn chỉ cần một hình dạng ẩn và không có gì khác.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` cung cấp một API tiện lợi để thêm nội dung vào một `Document`. Nó hoạt động như một con trỏ di chuyển qua tài liệu.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder tự động tạo một phần và đoạn văn mặc định đầu tiên, vì vậy bạn có thể bắt đầu chèn hình dạng mà không cần thêm phần thủ công.

## Step 3: Insert an ellipse shape

Bây giờ chúng ta **chèn ellipse** bằng phương thức `InsertShape`. Phương thức này nhận một enum `ShapeType`, chiều rộng và chiều cao (đơn vị điểm).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Tại sao lại là ellipse? Ellipse là một hình dạng vector có thể ẩn mà không ảnh hưởng đến luồng văn bản xung quanh. Chiều rộng 100 pt và chiều cao 50 pt chỉ là ví dụ; bạn có thể điều chỉnh chúng cho phù hợp với nhu cầu xử lý sau này.

## Step 4: Hide the shape so it does not appear in the layout

Để **ẩn hình dạng trong Word**, đặt thuộc tính `Hidden` của đối tượng `Shape` thành `true`. Khi tài liệu được mở trong Microsoft Word, hình dạng sẽ không hiển thị và không chiếm không gian trong bố cục.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Cờ `Hidden` được lưu trong XML của hình dạng (`<w:hidden/>`). Word tôn trọng thuộc tính này khi render, vì vậy tài liệu trông hoàn toàn trống mặc dù hình dạng vẫn tồn tại.

### Pro tip

Nếu sau này bạn cần hiển thị lại hình dạng, chỉ cần đặt `ellipse.Hidden = false;` và lưu tài liệu.

## Step 5: Save the document with the hidden shape

Cuối cùng, lưu tài liệu ra đĩa. Tệp sẽ là một `.docx` thông thường mà bất kỳ trình xử lý Word nào cũng có thể mở.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Tệp đã lưu, `HiddenEllipse.docx`, là một **tạo tài liệu Word trống** chứa một ellipse ẩn. Khi mở trong Microsoft Word, bạn sẽ thấy một trang trống, nhưng hình dạng vẫn tồn tại trong cấu trúc Open XML.

## Full working example

Dưới đây là chương trình hoàn chỉnh, tự chứa mà bạn có thể sao chép, dán và chạy.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi**

* Một tệp có tên `HiddenEllipse.docx` xuất hiện trong `C:\Temp`.
* Mở tệp trong Microsoft Word hiển thị một trang hoàn toàn trống.
* Nếu bạn kiểm tra tài liệu bằng Open XML SDK hoặc trình xem zip, bạn sẽ thấy phần tử `<w:shape>` có `<w:hidden/>` bên trong phần tài liệu.

## Common questions and edge cases

### What if the shape still appears?

* Đảm bảo bạn đang sử dụng Aspose.Words 23.9 hoặc mới hơn – các phiên bản cũ hơn có lỗi khiến `Hidden` bị bỏ qua đối với một số loại hình dạng.
* Kiểm tra xem bạn có áp dụng bất kỳ định dạng bổ sung nào (ví dụ, `WrapType`) khiến hình dạng chiếm không gian bố cục hay không.

### Can I hide other shape types?

Có. Thuộc tính `Hidden` hoạt động tương tự cho `ShapeType.Rectangle`, `ShapeType.Picture`, v.v. Chỉ cần thay `ShapeType.Ellipse` bằng loại mong muốn.

### How to list hidden shapes later?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Đoạn mã này duyệt qua tất cả các hình dạng và in ra những hình dạng bị ẩn, hữu ích cho quy trình **tạo hình dạng ẩn** khi bạn cần xử lý hoặc hiển thị lại chúng sau này.

## Conclusion

Bây giờ bạn đã biết cách **tạo tài liệu Word trống**, **chèn ellipse**, và **ẩn hình dạng trong Word** để tạo ra một **hình dạng ẩn** mà người đọc không thể thấy. Kỹ thuật này hữu ích để lưu trữ siêu dữ liệu, bookmark, hoặc XML tùy chỉnh trong tài liệu mà không làm thay đổi giao diện trực quan.

### Next steps

* Khám phá **cách ẩn hình dạng** có điều kiện dựa trên nội dung tài liệu.
* Học **cách hiển thị lại hình dạng** khi tạo phiên bản cuối cùng của tài liệu.
* Kết hợp các hình dạng ẩn với **thuộc tính tài liệu tùy chỉnh** để nhúng dữ liệu có thể đọc được bởi máy.

Hãy tự do thử nghiệm với các loại hình dạng, kích thước và logic trạng thái ẩn khác nhau để phù hợp với kịch bản tự động hóa của bạn. Chúc bạn lập trình vui vẻ!

## What Should You Learn Next?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word trống với hình chữ nhật có bóng – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tạo hình chữ nhật trong Word bằng Aspose.Words – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}