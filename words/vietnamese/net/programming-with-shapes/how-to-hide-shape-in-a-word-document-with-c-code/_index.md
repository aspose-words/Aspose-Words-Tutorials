---
category: general
date: 2026-09-14
description: Tìm hiểu cách ẩn hình dạng trong Word bằng C# — bao gồm mã tạo tài liệu
  Word, chèn hình chữ nhật vào Word và ẩn hình dạng trong Word một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: vi
lastmod: 2026-09-14
og_description: Cách ẩn hình dạng trong Word bằng C# — hướng dẫn chi tiết từng bước,
  đồng thời chỉ cách tạo mã tài liệu Word và chèn hình chữ nhật vào Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Cách ẩn hình dạng trong tài liệu Word bằng mã C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách ẩn hình dạng trong tài liệu Word bằng mã C#
url: /vi/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách ẩn hình dạng trong tài liệu Word bằng mã C#

Nếu bạn cần **cách ẩn hình dạng** trong một tệp Word, hướng dẫn này sẽ trình bày giải pháp đầy đủ. Bạn sẽ thấy cách tạo tài liệu Word, chèn một hình chữ nhật, thêm một hình ellipse, và ẩn ellipse đó sao cho chỉ hình chữ nhật hiển thị khi mở tệp.

Hướng dẫn bao gồm mọi thứ bạn cần—không có tham chiếu bên ngoài, chỉ có mã và giải thích. Khi hoàn thành, bạn sẽ có thể nhúng đồ họa ẩn trong bất kỳ tài liệu Word nào bạn tạo một cách lập trình.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
- Aspose.Words for .NET (bản dùng thử miễn phí hoặc phiên bản có giấy phép)  
  Cài đặt qua NuGet: `dotnet add package Aspose.Words`
- Kiến thức cơ bản về C# và Visual Studio hoặc bất kỳ IDE nào bạn thích

## Bước 1: Thiết lập dự án và nhập các namespace

Bắt đầu một ứng dụng console mới và thêm các câu lệnh `using` cần thiết. Những import này cho phép bạn truy cập vào các lớp `Document`, `DocumentBuilder` và các lớp vẽ cần thiết để thao tác với hình dạng.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Tại sao điều này quan trọng** – Việc nhập các namespace đúng ngăn ngừa lỗi biên dịch và cung cấp các API cần thiết cho việc tạo hình và kiểm soát hiển thị.

## Bước 2: Tạo tài liệu Word mới và một builder

`Document` đại diện cho tệp, trong khi `DocumentBuilder` cung cấp một API mượt mà để thêm nội dung. Đây là nơi đầu tiên bạn áp dụng logic **cách ẩn hình dạng**: bạn cần một ngữ cảnh tài liệu trước khi bất kỳ hình nào có thể tồn tại.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Giải thích** – Đối tượng `Document` bắt đầu rỗng. `DocumentBuilder` được đặt ở đầu đoạn văn đầu tiên, sẵn sàng chèn hình hoặc văn bản.

## Bước 3: Chèn một hình chữ nhật hiển thị

Hình chữ nhật sẽ là hình dạng vẫn hiển thị khi tài liệu được mở. Bạn có thể kiểm soát kích thước, vị trí và định dạng của nó trực tiếp qua đối tượng shape.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Tại sao bước này** – Thêm một hình chữ nhật minh họa yêu cầu **insert rectangle shape word**. Đặt `FillColor` và `LineColor` giúp hình dễ nhận biết trong tài liệu cuối cùng.

## Bước 4: Chèn một hình ellipse và ẩn nó

Bây giờ bạn thêm hình mà mình muốn giấu. Thuộc tính `Hidden` thông báo cho Word không hiển thị hình trong giao diện người dùng, mặc dù nó vẫn tồn tại trong cấu trúc tài liệu.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Giải thích** – Đặt `Hidden = true` là cốt lõi của **hide shape in word**. Word tôn trọng cờ này trong quá trình xem và in bình thường, nhưng hình vẫn có thể được truy cập bằng lập trình nếu cần.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Chọn một thư mục bạn có quyền ghi, và đặt tên tệp rõ ràng để phản ánh mục đích của hướng dẫn.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Kết quả** – Mở `ShapeVisibility.docx` trong Microsoft Word chỉ hiển thị hình chữ nhật màu xanh nhạt. Hình ellipse ẩn không xuất hiện, xác nhận rằng bạn đã thành công trong việc **cách ẩn hình dạng** trong một tệp Word.

## Ví dụ đầy đủ hoạt động

Kết hợp tất cả các đoạn mã lại với nhau sẽ cho bạn một chương trình duy nhất, có thể chạy được:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Kết quả mong đợi

- **Visual**: Khi mở `ShapeVisibility.docx`, bạn sẽ thấy một hình chữ nhật màu xanh nhạt nằm gần lề trái. Không có ellipse nào hiển thị.
- **Programmatic**: Hình ellipse ẩn vẫn tồn tại trong XML của tài liệu (`<w:drawing>` element) với thuộc tính `w:hidden` được đặt, bạn có thể xác minh bằng cách mở tệp dưới dạng zip và kiểm tra `document.xml`.

## Các câu hỏi thường gặp và các trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| *Tôi có thể ẩn nhiều hình không?* | Có. Đặt `Hidden = true` cho mỗi hình bạn muốn giấu. |
| *Các hình ẩn có được in không?* | Mặc định Word không in các đối tượng ẩn. Nếu bạn cần chúng được in, hãy xóa cờ `Hidden` trước khi in. |
| *Thuộc tính hidden có được hỗ trợ trong các phiên bản Word cũ không?* | Thuộc tính `Hidden` là một phần của tiêu chuẩn Office Open XML và hoạt động trong Word 2007 và các phiên bản sau. |
| *Nếu tôi cần chuyển đổi trạng thái hiển thị ở thời gian chạy thì sao?* | Lấy hình bằng `document.GetChildNodes(NodeType.Shape, true)` và đảo ngược thuộc tính `Hidden` dựa trên logic của bạn. |

## Mẹo chuyên nghiệp

- **Performance**: Nếu bạn tạo nhiều tài liệu, hãy tái sử dụng một thể hiện `DocumentBuilder` duy nhất thay vì tạo mới cho mỗi tệp.
- **Version control**: Lưu các tệp `.docx` đã tạo trong một thư mục được kiểm soát phiên bản; các hình ẩn có thể đóng vai trò là dấu hiệu metadata cho các quy trình xử lý tiếp theo.
- **Testing**: Tự động hoá một kiểm tra nhanh bằng cách chuyển DOCX sang PDF với Aspose.Words (`document.Save("out.pdf")`). PDF cũng sẽ ẩn ellipse, xác nhận rằng cờ hidden được truyền qua quá trình chuyển đổi định dạng.

## Kết luận

Bạn giờ đã biết **cách ẩn hình dạng** trong tài liệu Word bằng C#. Hướng dẫn đã đi qua việc tạo tài liệu, **insert rectangle shape word**, thêm một ellipse, và áp dụng cờ `Hidden` để đạt được hành vi **hide shape in word**. Với mã hoàn chỉnh, có thể chạy được, bạn có thể tích hợp đồ họa ẩn vào bất kỳ quy trình báo cáo tự động hoặc mẫu tài liệu nào.

### Các bước tiếp theo

- Khám phá các thuộc tính hình dạng khác như xoay, bóng đổ và bọc văn bản.  
- Kết hợp các hình ẩn với thuộc tính tài liệu tùy chỉnh để nhúng dữ liệu có thể đọc được bởi máy.  
- Tìm hiểu các mẫu **create word document code** cho bảng, biểu đồ và content controls để mở rộng bộ công cụ tự động hoá của bạn.

Hãy thoải mái thử nghiệm với các loại hình dạng và cài đặt hiển thị khác nhau—dự án tự động hoá Word tiếp theo của bạn chỉ cách vài dòng mã!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}