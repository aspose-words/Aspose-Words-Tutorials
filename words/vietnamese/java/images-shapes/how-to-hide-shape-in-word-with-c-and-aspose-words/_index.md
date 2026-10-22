---
category: general
date: 2026-09-11
description: Tìm hiểu cách ẩn hình dạng trong Word bằng C#. Hướng dẫn này cũng chỉ
  cách chèn hình chữ nhật và chèn hình dạng vào tài liệu Word bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: vi
lastmod: 2026-09-11
og_description: Cách ẩn hình dạng trong Word bằng C# và Aspose.Words. Tham khảo hướng
  dẫn từng bước để chèn hình chữ nhật và quản lý các hình dạng trong tài liệu Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Cách ẩn hình trong Word – hướng dẫn C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Cách ẩn hình trong Word bằng C# và Aspose.Words
url: /vi/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách ẩn hình dạng trong Word bằng C# và Aspose.Words

Nếu bạn cần ẩn hình dạng trong Word mà vẫn giữ hình dạng trong cấu trúc tài liệu, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Sử dụng Aspose.Words cho .NET, bạn có thể chèn một hình chữ nhật, ẩn nó và vẫn giữ vị trí để xử lý sau này.

Tự động hoá Word thường đòi hỏi kiểm soát chi tiết các hình dạng — dù bạn đang tạo mẫu, chuẩn bị báo cáo, hay xây dựng dịch vụ chỉnh sửa tài liệu. Khi hoàn thành hướng dẫn này, bạn sẽ có thể:

* Chèn một hình chữ nhật vào tài liệu Word (`insert rectangle shape`).
* Ẩn bất kỳ hình dạng nào mà không xóa nó (`how to hide shape in word`).
* Lưu kết quả và xác minh rằng hình ẩn không xuất hiện trong chế độ hiển thị (`insert shape into word document`).

Ví dụ hoạt động với Aspose.Words 24.10 hoặc mới hơn và nhắm tới .NET 6.0+, nhưng các khái niệm cũng áp dụng cho các phiên bản trước.

## Yêu cầu trước

* **Aspose.Words for .NET** ≥ 24.10. Bạn có thể lấy giấy phép tạm thời miễn phí từ trang web Aspose.
* **.NET SDK** 6.0 hoặc mới hơn được cài đặt trên máy của bạn.
* Môi trường phát triển như Visual Studio 2022, VS Code, hoặc Rider.
* Kiến thức cơ bản về C# và khái niệm Word Open XML (không bắt buộc nhưng hữu ích).

## Cách ẩn hình dạng trong Word với Aspose.Words

Dưới đây là một chương trình hoàn chỉnh, có thể chạy được, minh họa toàn bộ quy trình — từ tạo tài liệu, chèn hình chữ nhật và cuối cùng ẩn nó.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Giải thích từng bước

1. **Tạo tài liệu mới** – `Document` đại diện cho tệp Word trong bộ nhớ. `DocumentBuilder` cung cấp API dạng fluent để chèn nội dung.
2. **Chèn hình chữ nhật** – `InsertShape` tạo một đối tượng vẽ loại `Rectangle`. Kích thước được biểu diễn bằng điểm (1 pt ≈ 1/72 in). Điều này đáp ứng yêu cầu `insert rectangle shape`.
3. **Ẩn hình dạng** – Đặt `Shape.Hidden = true` đánh dấu hình dạng là ẩn trong markup Word (`<w:hidden/>`). Hình dạng vẫn là một phần của cây tài liệu, vì vậy bạn có thể bật lại hoặc tham chiếu nó bằng mã. Đây là phần cốt lõi của `how to hide shape in word`.
4. **Lưu tệp** – Tài liệu được ghi ra `output.docx`. Khi mở trong Microsoft Word, hình chữ nhật sẽ không hiển thị, nhưng nó vẫn tồn tại trong XML và có thể kiểm tra bằng trình xem ZIP hoặc Open XML SDK.

### Kết quả mong đợi

Mở `output.docx` trong Microsoft Word:

* Tài liệu trông trống — không có hình nào hiển thị.
* Nếu bạn kiểm tra XML nền (`word/document.xml`) sẽ thấy một phần tử `<w:pict>` có thuộc tính `<w:hidden/>`, xác nhận rằng hình dạng vẫn tồn tại nhưng đã bị ẩn.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Bạn có thể hiển thị lại hình ẩn bằng cách đặt `Hidden = false` và lưu lại tài liệu.

## Chèn hình chữ nhật vào tài liệu Word

Mặc dù mục tiêu chính là ẩn một hình dạng, nhiều trường hợp bắt đầu bằng việc chèn hình dạng trước. Phương thức `InsertShape` hỗ trợ nhiều giá trị `ShapeType`, bao gồm `Rectangle`, `Ellipse`, `Line` và các hình ảnh tùy chỉnh.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Tại sao lại dùng hình chữ nhật?**  
Hình chữ nhật cung cấp một khung chứa thẳng hàng, có thể chứa văn bản, hình ảnh hoặc các hình dạng lồng nhau khác. Nó thường được dùng làm chỗ giữ cho nội dung động như bảng hoặc biểu đồ. Bằng cách chèn hình chữ nhật trước, bạn duy trì tính nhất quán bố cục ngay cả khi ẩn nó sau này.

## Chèn hình dạng vào tài liệu Word – các thực tiễn tốt nhất

Khi bạn `insert shape into word document`, hãy cân nhắc các yếu tố sau:

* **Đặt kích thước rõ ràng** – Tránh dựa vào kích thước tự động; chỉ định chiều rộng và chiều cao bằng điểm để đảm bảo bố cục nhất quán trên mọi nền tảng.
* **Xác định vị trí** – Mặc định hình dạng được neo vào đoạn hiện tại. Sử dụng `builder.MoveTo` hoặc `builder.StartBookmark` để đặt nó một cách chính xác.
* **Áp dụng kiểu dáng sớm** – Màu nền, kiểu đường viền và cách bọc văn bản ảnh hưởng đến giao diện cuối cùng. Ngay cả các hình ẩn cũng hưởng lợi từ việc định dạng đúng vì markup không thay đổi.
* **Tương thích phiên bản** – Thuộc tính `Hidden` chỉ có từ Aspose.Words 24.10 trở lên. Nếu bạn nhắm tới phiên bản cũ hơn, có thể tự thêm thuộc tính `<w:hidden/>` bằng API `Node`.

### Thêm thuộc tính ẩn thủ công (phương án dự phòng)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Ví dụ hoàn chỉnh từ đầu đến cuối

Kết hợp mọi thứ lại, đây là một chương trình duy nhất thực hiện:

1. Chèn một hình chữ nhật.
2. Ẩn hình chữ nhật.
3. Chèn một hình ellipse hiển thị để tạo độ tương phản.
4. Lưu tài liệu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Chạy chương trình sẽ tạo ra `demo_output.docx`. Khi mở, bạn sẽ chỉ thấy ellipse màu san hô; hình chữ nhật màu xanh lá vẫn tồn tại trong XML nhưng bị ẩn khỏi giao diện.

## Các câu hỏi thường gặp và trường hợp đặc biệt

**H: Ẩn hình dạng có ảnh hưởng đến việc phân trang không?**  
Đ: Không. Các hình ẩn bị bỏ qua bởi engine bố cục, vì vậy chúng không chiếm không gian. Điều này hữu ích cho nội dung chỗ giữ không muốn ảnh hưởng đến ngắt trang.

**H: Tôi có thể ẩn hình dạng nằm trong header hoặc footer không?**  
Đ: Có. Thuộc tính `Hidden` hoạt động với các hình dạng ở bất kỳ vị trí nào trong cây tài liệu, bao gồm header, footer và thậm chí trong bảng.

**H: Nếu cần ẩn nhiều hình dạng cùng lúc thì sao?**  
Đ: Duyệt qua collection `Document.GetChildNodes(NodeType.Shape, true)` và đặt `Hidden = true` cho mỗi hình mục tiêu.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**H: Thuộc tính ẩn có được giữ lại khi chuyển đổi sang PDF không?**  
Đ: Khi chuyển đổi sang PDF, các hình ẩn mặc định sẽ bị loại bỏ, giống như cách Word hiển thị. Nếu bạn muốn chúng xuất hiện trong PDF, cần bỏ ẩn chúng trước khi chuyển đổi.

## Mẹo và lưu ý

* **Mẹo chuyên nghiệp:** Đặt `shape.WrapType = WrapType.None` trước khi ẩn nếu bạn dự định bật lại hình mà không làm xáo trộn văn bản xung quanh.
* **Cảnh báo phiên bản cũ của Aspose.Words:** Thuộc tính `Hidden` sẽ ném `NotSupportedException` trước 24.10. Hãy dùng cách thêm XML thủ công trong trường hợp đó.
* **Kiểm thử:** Luôn mở file `.docx` đã tạo trong Word và bật “Show XML markup” (tab Developer) để xác nhận thuộc tính `<w:hidden/>` tồn tại.

## Kết luận

Bây giờ bạn đã biết cách ẩn hình dạng trong Word bằng C# và Aspose.Words, cũng như cách chèn hình chữ nhật và chèn hình dạng vào tài liệu Word với kiểm soát đầy đủ về khả năng hiển thị. Bằng cách tận dụng thuộc tính `Hidden`, bạn có thể giữ các hình dạng trong mô hình tài liệu để xử lý sau, đồng thời cung cấp giao diện sạch sẽ cho người dùng cuối.

Tiếp theo, hãy khám phá các chủ đề liên quan như **cập nhật thuộc tính hình dạng tại thời gian chạy**, **chuyển đổi hình ẩn thành hình ảnh**, hoặc **sử dụng Open XML SDK để thao tác trực tiếp với các phần tử ẩn**. Những mở rộng này sẽ giúp bạn đi sâu hơn.

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}