---
category: general
date: 2026-08-07
description: Chèn hình chữ nhật trong C# bằng Aspose.Words và tìm hiểu cách ẩn hình,
  đặt màu nền, và thêm hình chữ nhật vào tài liệu Word một cách hiệu quả.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: vi
lastmod: 2026-08-07
og_description: Chèn hình chữ nhật vào tài liệu Word bằng C#. Tìm hiểu cách ẩn hình,
  đặt màu nền và thêm hình chữ nhật bằng Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Chèn hình chữ nhật trong C# – hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Chèn hình chữ nhật trong C# với Aspose.Words – hướng dẫn từng bước
url: /vi/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chèn hình chữ nhật trong C# với Aspose.Words – hướng dẫn từng bước

Nếu bạn cần **chèn hình chữ nhật** vào tài liệu Word từ C#, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác. Bạn sẽ thấy cách đặt màu nền, ẩn hình sao cho nó không xuất hiện trong bố cục cuối cùng, và lưu tệp—tất cả chỉ với vài dòng mã.

Trong các phần sau, chúng tôi sẽ bao phủ mọi thứ bạn cần biết: các yêu cầu trước, danh sách mã đầy đủ, giải thích cho mỗi bước, và các mẹo cho các biến thể phổ biến như làm cho hình hiển thị lại hoặc sử dụng màu khác. Khi kết thúc, bạn sẽ có thể **thêm hình chữ nhật** vào bất kỳ tệp .docx nào một cách lập trình.

## Yêu cầu trước

* **Aspose.Words for .NET** (phiên bản 23.10 trở lên). Bạn có thể cài đặt nó qua NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK hoặc phiên bản mới hơn đã được cài đặt trên máy của bạn.
* Kiến thức cơ bản về C# và Visual Studio (hoặc bất kỳ IDE nào bạn ưa thích).

Không cần thư viện bổ sung nào—các API liên quan đến hình là một phần của gói Aspose.Words cốt lõi.

## Chèn hình chữ nhật với Aspose.Words

Cốt lõi của giải pháp là một chương trình ngắn, tự chứa, tạo một tài liệu trống, chèn một hình chữ nhật, tô màu, ẩn nó, và sau đó lưu tệp. Dưới đây là mã nguồn đầy đủ với các chú thích nội dòng giải thích *lý do* cho mỗi dòng.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Mỗi bước thực hiện gì

| Bước | Lý do |
|------|--------|
| **Create a new document** | Cung cấp một canvas sạch; bạn cũng có thể tải một .docx hiện có bằng cách truyền đường dẫn tệp vào `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` là công cụ cấp cao cho phép bạn chèn văn bản, bảng và hình mà không cần xử lý cây node cấp thấp. |
| **Insert rectangle shape** | Phương thức `InsertShape` trả về một đối tượng `Shape` mà bạn có thể tùy chỉnh thêm (kích thước, vị trí, viền, v.v.). |
| **Set fill color** | Thuộc tính `FillColor` điều khiển màu bên trong; bạn có thể sử dụng bất kỳ giá trị `Color` nào (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, v.v.). |
| **Hide the shape** | `Hidden = true` báo cho Word bỏ qua hình trong quá trình bố trí trong khi vẫn giữ nó trong XML của tài liệu. Đây là cách tiêu chuẩn để lưu các đối tượng vô hình. |
| **Save the document** | Lưu các thay đổi vào tệp .docx. Tệp đã lưu sẽ chứa hình chữ nhật ẩn. |

## Cách đặt màu nền cho một hình

Thay đổi màu nền đơn giản như việc gán một `System.Drawing.Color` cho thuộc tính `FillColor`. Nếu bạn cần một sắc màu tùy chỉnh, hãy sử dụng `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*​Tại sao điều này quan trọng*: Màu nền được lưu trong XML của hình (`<w:fill>` attribute). Khi hình bị ẩn, màu vẫn tồn tại, điều này có thể hữu ích cho việc xử lý tiếp theo (ví dụ, trích xuất siêu dữ liệu dựa trên mã màu).

## Cách ẩn hình trong tài liệu cuối cùng

Cờ `Hidden` là một thuộc tính boolean trên lớp `Shape`. Đặt nó thành `true` sẽ đảm bảo hình bị bỏ qua bởi engine bố trí của Word.

```csharp
rectangleShape.Hidden = true;
```

**Những lỗi thường gặp**

* **Hidden vs. Visible** – Nếu sau này bạn cần hình xuất hiện, chỉ cần đặt `Hidden = false`.
* **Compatibility** – Các phiên bản Word cũ hơn (trước 2007) có thể xử lý các đối tượng vẽ ẩn khác nhau. Aspose.Words duy trì tính tương thích bằng cách lưu cờ trong phần tử OOXML thích hợp.

## Cách chèn hình một cách lập trình

Mặc dù ví dụ sử dụng hình chữ nhật, phương thức `InsertShape` tương tự hoạt động cho nhiều hình khác (ellipse, triangle, line, v.v.). Đối số đầu tiên là một giá trị enum `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Mẹo**: Nếu bạn cần đặt hình ở vị trí cụ thể trên trang, hãy dùng `builder.MoveTo` để đặt điểm chèn trước khi gọi `InsertShape`.

## Thêm hình chữ nhật vào tài liệu hiện có

Thường bạn sẽ cải thiện một mẫu thay vì bắt đầu từ đầu. Thay thế bước 1 bằng:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Tất cả các bước tiếp theo vẫn giống nhau, và hình chữ nhật sẽ được thêm vào vị trí con trỏ của builder (thường là cuối tài liệu theo mặc định).

## Xử lý các trường hợp biên và biến thể

### 1. Làm cho hình hiển thị lại

Nếu một phần sau của quy trình làm việc của bạn cần hiển thị lại hình chữ nhật ẩn, bạn có thể chuyển đổi cờ:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Thêm viền (stroke)

Một hình ẩn vẫn có thể có viền hiển thị khi bạn quyết định hiển thị nó. Đặt các thuộc tính `LineColor` và `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Định vị hình chữ nhật một cách tuyệt đối

Để kiểm soát bố trí chính xác, chuyển `WrapType` của hình sang `WrapType.Inline` (mặc định) hoặc `WrapType.TopBottom` và điều chỉnh các thuộc tính `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Sử dụng đơn vị đo khác

Aspose.Words làm việc bằng điểm (1 pt = 1/72 inch). Nếu bạn muốn sử dụng centimet, hãy chuyển đổi trước:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Ví dụ đầy đủ có thể chạy được

Dưới đây là chương trình *đầy đủ* mà bạn có thể sao chép, dán và chạy. Nó bao gồm tất cả các chỉ thị `using` cần thiết và sử dụng các đường dẫn tuyệt đối mà bạn nên điều chỉnh cho môi trường của mình.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả mong đợi**: Tệp `HiddenRectangleShape.docx` mở trong Microsoft Word mà *không có hình nào hiển thị*, nhưng hình chữ nhật ẩn vẫn có trong XML của tài liệu. Bạn có thể xác minh sự tồn tại của nó bằng cách mở .docx như một tệp zip và kiểm tra `word/document.xml` để tìm phần tử `<w:shape>` có thuộc tính `w:fill="yellow"` và `w:hidden="true"`.

## Kết luận

Bây giờ bạn đã biết cách **chèn hình chữ nhật** vào tài liệu Word bằng C# và Aspose.Words, cách **đặt màu nền**, và cách **ẩn hình** để nó không hiển thị trong bố cục cuối cùng. Mẫu tương tự áp dụng cho các loại hình khác, màu tùy chỉnh, và các mẫu hiện có. Hãy thử nghiệm với viền, định vị tuyệt đối, và các đơn vị đo khác nhau để điều chỉnh hình cho đúng yêu cầu của bạn.

### Các bước tiếp theo

* Khám phá **cách chèn hình** vào trong bảng hoặc header/footer để tạo watermark.
* Kết hợp **thêm hình chữ nhật** với content controls để tạo các placeholder động.
* Xem lại API **shape manipulation** của Aspose.Words để biết các tính năng nâng cao như xoay, gradient fill, và nhập SVG.

Hãy tự do điều chỉnh mã cho dự án của bạn, và cho chúng tôi biết trong phần bình luận thử thách liên quan đến hình nào bạn đã giải quyết tiếp theo!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao phủ các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Hướng dẫn Shadow cho Shape trong Aspose.Words – Thêm bóng cho Shape trong Word bằng C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}