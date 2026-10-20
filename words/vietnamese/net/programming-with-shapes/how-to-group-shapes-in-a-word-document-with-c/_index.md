---
category: general
date: 2026-08-14
description: Cách nhóm các hình dạng trong tài liệu Word bằng C#. Học cách tạo tài
  liệu Word, chèn hình chữ nhật, nhóm các hình dạng trong Word và lưu tài liệu dưới
  dạng docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: vi
lastmod: 2026-08-14
og_description: Cách nhóm các hình dạng trong tài liệu Word bằng C#. Tham khảo hướng
  dẫn đầy đủ này để tạo tệp Word, chèn hình chữ nhật, nhóm các hình dạng trong Word
  và lưu kết quả dưới dạng docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Cách nhóm các hình dạng trong tài liệu Word bằng C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Cách nhóm các hình dạng trong tài liệu Word bằng C#
url: /vi/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong tài liệu Word bằng C#

Nếu bạn cần **cách nhóm các hình dạng** trong một tài liệu Word, hướng dẫn này sẽ cho bạn các bước chính xác bằng C# và thư viện Aspose.Words. Bạn sẽ thấy cách tạo tài liệu Word, chèn hình chữ nhật, nhóm các hình dạng trong Word, và cuối cùng **lưu tài liệu dưới dạng docx**—tất cả trong một chương trình có thể chạy được.

Việc tạo và thao tác các hình dạng là một yêu cầu phổ biến khi tự động tạo báo cáo, hợp đồng hoặc tài liệu quảng cáo. Khi kết thúc hướng dẫn này, bạn sẽ có một đoạn mã có thể tái sử dụng mà bạn có thể chèn vào bất kỳ dự án .NET nào.

## Yêu cầu trước

- .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt  
- Visual Studio 2022 (hoặc bất kỳ IDE nào hỗ trợ .NET)  
- Giấy phép Aspose.Words cho .NET (hoặc bản dùng thử miễn phí)  
- Kiến thức cơ bản về cú pháp C#  

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Cách nhóm các hình dạng trong tài liệu Word

Cốt lõi của giải pháp là quy trình năm bước. Mỗi bước được giải thích chi tiết, và mã nguồn đầy đủ được cung cấp ở cuối bài viết.

### Bước 1: Tạo tài liệu trống mới

Điều đầu tiên bạn làm khi muốn **tạo tài liệu Word** một cách lập trình là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ tệp .docx trong bộ nhớ.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:** `DocumentBuilder` là một công cụ trợ giúp cấp cao cho phép bạn chèn văn bản, bảng và hình dạng mà không cần xử lý thủ công cây node bên dưới.

### Bước 2: Chèn hình chữ nhật

Để minh họa **chèn hình chữ nhật**, chúng ta sử dụng phương thức `InsertShape`. Hình chữ nhật sẽ là thành viên đầu tiên của nhóm.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Tại sao điều này quan trọng:** Các hình dạng được định vị tương đối so với điểm chèn. Đặt màu nền giúp bạn nhìn thấy hình dạng khi mở tài liệu kết quả.

### Bước 3: Chèn hình ellipse

Tiếp theo, chúng ta **chèn hình ellipse** (API gọi nó là `Ellipse`). Đây sẽ là thành viên thứ hai của nhóm.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Tại sao điều này quan trọng:** Bằng cách chèn ellipse ngay sau hình chữ nhật, cả hai hình sẽ nằm trong cùng một đoạn, giúp việc nhóm sau này trở nên đơn giản hơn.

### Bước 4: Nhóm hình chữ nhật và ellipse

Bây giờ chúng ta trả lời câu hỏi trung tâm **cách nhóm các hình dạng** trong tài liệu Word. Aspose.Words cung cấp `AppendGroupShape` để tạo một container nhóm, và sau đó bạn gọi `Group()` trên container đó.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Tại sao điều này quan trọng:** Khi đã được nhóm, bất kỳ biến đổi nào (di chuyển, thay đổi kích thước, xoay) áp dụng cho `groupedShape` sẽ tự động ảnh hưởng đến cả hình chữ nhật và ellipse. Điều này rất cần thiết để duy trì tính nhất quán bố cục trong các tài liệu được tạo.

### Bước 5: Lưu tài liệu dưới dạng tệp DOCX

Bước cuối cùng là **lưu tài liệu dưới dạng docx**. Bạn có thể chọn bất kỳ đường dẫn nào; ví dụ sử dụng placeholder `"YOUR_DIRECTORY"` mà bạn nên thay thế bằng thư mục thực.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Tại sao điều này quan trọng:** Lưu dưới dạng DOCX giữ nguyên siêu dữ liệu nhóm, vì vậy khi bạn mở tệp trong Microsoft Word, bạn sẽ thấy hình chữ nhật và ellipse hoạt động như một đối tượng duy nhất.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là chương trình hoàn chỉnh kết hợp cả năm bước. Sao chép nó vào một dự án console mới, khôi phục gói NuGet Aspose.Words, và chạy nó.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Kết quả mong đợi

Khi bạn mở `groupedShapes.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật màu xanh nhạt và một hình ellipse màu hồng nhạt được khóa cùng nhau. Nhấp vào bất kỳ hình nào sẽ chọn cả hai, cho phép bạn di chuyển hoặc thay đổi kích thước chúng như một đơn vị duy nhất.

## Các câu hỏi thường gặp và trường hợp đặc biệt

| Question | Answer |
|----------|--------|
| **Tôi có thể nhóm nhiều hơn hai hình không?** | Có. Bạn có thể truyền bất kỳ số lượng đối tượng `Shape` nào vào `AppendGroupShape`. Phương thức này chấp nhận một mảng, vì vậy bạn có thể xây dựng bộ sưu tập một cách động. |
| **Nếu tôi cần nhóm được neo vào một ô bảng thì sao?** | Chèn các hình vào trong đoạn của ô, sau đó gọi `AppendGroupShape` trên đoạn đó. Nhóm sẽ kế thừa việc neo của ô. |
| **Việc nhóm có ảnh hưởng đến XML nền không?** | Aspose.Words ghi một phần tử `<w:grpSp>` chứa các hình con. Word nhận diện đây là một nhóm, giữ nguyên vị trí tương đối. |
| **Làm sao để tách nhóm sau này?** | Gọi `groupedShape.Ungroup()`; phương thức này trả về các hình riêng lẻ để bạn có thể thao tác chúng riêng biệt. |
| **Có ảnh hưởng đến hiệu năng khi nhóm nhiều hình không?** | Việc nhóm bản thân nó không tốn nhiều tài nguyên, nhưng việc render các nhóm rất lớn (hàng trăm hình) có thể làm tăng kích thước tệp. Hãy cân nhắc làm phẳng (flatten) các hình ảnh nếu kích thước trở thành vấn đề. |

## Mẹo chuyên nghiệp

- **Đặt vị trí cụ thể** (`Left`, `Top`) nếu bạn cần căn chỉnh chính xác trước khi nhóm.  
- **Sử dụng `Shape.WrapType = WrapType.Inline`** khi bạn muốn nhóm hoạt động như một phần tử đoạn thay vì một đối tượng nổi.  
- **Áp dụng kiểu đường viền** cho nhóm (`groupedShape.LineFormat`) để cung cấp cho toàn bộ bộ sưu tập một viền.  
- **Tái sử dụng nhóm**: sau khi gọi `Group()`, bạn có thể sao chép `groupedShape` và chèn bản sao vào vị trí khác trong tài liệu.

## Các bước tiếp theo

Bây giờ bạn đã biết **cách nhóm các hình dạng** trong tài liệu Word, bạn có thể khám phá các chủ đề liên quan như:

- **Chèn hình chữ nhật** với văn bản hoặc hình ảnh tùy chỉnh bên trong hình.  
- **Tạo sơ đồ phức tạp** bằng cách lồng nhóm (nhóm một nhóm).  
- **Xuất tài liệu dưới dạng PDF** trong khi giữ nguyên nhóm hình (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

## Kết luận

Hướng dẫn này đã trình bày **cách nhóm các hình dạng** trong tài liệu Word bằng C#. Bạn đã học cách **tạo tài liệu Word**, **chèn hình chữ nhật**, **nhóm các hình dạng trong Word**, và cuối cùng **lưu tài liệu dưới dạng docx**. Với ví dụ đầy đủ, có thể chạy và các mẹo thực tế được cung cấp, bạn có thể tích hợp việc nhóm hình vào bất kỳ quy trình tạo tài liệu nào. Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo Nhóm Hình trong Tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Chèn Hình dạng trong Tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}