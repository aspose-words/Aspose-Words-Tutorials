---
category: general
date: 2026-10-23
description: Tạo một tài liệu Word trống, thêm một hình chữ nhật và ẩn hình trong
  Word bằng Aspose.Words. Mã từng bước cho các nhà phát triển .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: vi
lastmod: 2026-10-23
og_description: Tạo một tài liệu Word trống, thêm một hình chữ nhật và ẩn hình trong
  Word bằng Aspose.Words. Tham khảo ví dụ C# đầy đủ.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Tạo một tài liệu Word trống và thêm một hình chữ nhật ẩn
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Tạo tài liệu Word trống và thêm hình chữ nhật
url: /vi/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo một tài liệu Word trống và thêm một hình chữ nhật

Nếu bạn cần **tạo một tài liệu Word trống**, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words cho .NET. Bạn cũng sẽ học **cách chèn hình**—cụ thể là một hình chữ nhật—và **ẩn hình trong Word** để nó không ảnh hưởng đến bố cục.

Bài hướng dẫn sẽ đi qua từng dòng mã, giải thích lý do mỗi bước quan trọng, và đề cập đến các lỗi thường gặp như việc hiển thị hình ẩn trong các chế độ xem Word khác nhau. Khi kết thúc, bạn sẽ có một tệp `.docx` hoạt động đầy đủ chứa một hình chữ nhật ẩn mà bạn có thể bật lại hoặc thao tác bằng chương trình.

## Yêu cầu trước

- .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.6+)
- Gói NuGet Aspose.Words cho .NET (`Install-Package Aspose.Words`)
- Môi trường phát triển như Visual Studio 2022 hoặc VS Code với các extension C#
- Kiến thức cơ bản về cú pháp C# và các khái niệm tài liệu Word

Không cần cài đặt Office bổ sung vì Aspose.Words hoạt động hoàn toàn trong bộ nhớ.

## Tạo một tài liệu Word trống

Bước đầu tiên là khởi tạo một đối tượng `Document` trống. Đối tượng này đại diện cho một tệp Word chưa có phần, đoạn văn hay nội dung nào.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Tại sao điều này quan trọng:**  
Một `Document` trống cung cấp cho bạn một nền vẽ sạch sẽ. Nếu bạn bắt đầu từ một mẫu có sẵn, các hình ẩn có thể kế thừa các kiểu không mong muốn. Bắt đầu từ đầu đảm bảo rằng hình chữ nhật bạn thêm sau là nội dung duy nhất bạn kiểm soát.

## Thêm một hình chữ nhật vào tài liệu

Tiếp theo, chúng ta cần một `DocumentBuilder` để đặt nội dung vào tài liệu. Phương thức `InsertShape` của builder là cách chuẩn **để chèn hình** như hình chữ nhật, hình tròn, hoặc các bản vẽ tùy chỉnh.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Tại sao điều này quan trọng:**  
`InsertShape` trả về một đối tượng `Shape` mà bạn có thể cấu hình thêm (màu, kiểu đường viền, v.v.). Kích thước được đưa ra bằng điểm (1 point = 1/72 inch), phù hợp với hệ thống đo lường nội bộ của Word.

### Tùy chọn: định dạng hình chữ nhật (tùy chọn)

Nếu bạn muốn hình chữ nhật có viền hiển thị khi bạn bật lại sau này, bạn có thể đặt độ dày và màu của đường viền:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Các dòng này là tùy chọn vì hình sẽ được ẩn trong bước tiếp theo.

## Ẩn hình trong Word

Word cho phép ẩn các hình khỏi bố cục trong khi vẫn là một phần của mô hình đối tượng tài liệu. Đặt thuộc tính `Hidden` thành `true` làm cho hình không hiển thị trong chế độ xem bình thường nhưng vẫn có thể được chọn qua API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Tại sao điều này quan trọng:**  
Một hình ẩn hữu ích để lưu trữ siêu dữ liệu, chỗ giữ cho các xử lý sau, hoặc nội dung có điều kiện mà bạn chỉ bật lên trong một số trường hợp nhất định (ví dụ, khi tạo báo cáo cuối cùng). Hình vẫn tồn tại trong tệp, vì vậy bạn có thể bật lại bằng cách lập trình với `rectangleShape.Hidden = false;`.

## Lưu tài liệu

Cuối cùng, ghi tài liệu ra đĩa. Phần mở rộng tệp xác định định dạng Word; `.docx` là định dạng Open XML hiện đại.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Kết quả:**  
Mở `HiddenShape.docx` trong Microsoft Word sẽ hiển thị một trang **trống**. Hình chữ nhật không hiển thị, nhưng nếu bạn vào **Home → Select → Selection Pane**, bạn sẽ thấy hình được liệt kê và có thể bật/tắt hiển thị của nó.

## Ví dụ đầy đủ hoạt động

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép, dán và chạy. Nó bao gồm tất cả các câu lệnh `using` cần thiết và các chú thích.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả mong đợi:**  

- Console in ra đường dẫn lưu.  
- `HiddenShape.docx` mở ra như một trang trống trong Word.  
- Hình chữ nhật tồn tại nhưng bị ẩn; bạn có thể xác nhận qua *Selection Pane* hoặc bằng cách lập trình đặt `Hidden = false` và mở lại tệp.

## Các câu hỏi thường gặp và trường hợp đặc biệt

| Câu hỏi | Câu trả lời |
|----------|--------|
| **Tôi có thể ẩn các loại hình khác không?** | Có. Bất kỳ `Shape` nào (ví dụ, `ShapeType.Ellipse`, `ShapeType.Picture`) đều hỗ trợ thuộc tính `Hidden`. |
| **Hình ẩn có làm tăng kích thước tệp không?** | Sự tăng kích thước là không đáng kể (một vài kilobyte) vì dữ liệu hình được lưu dưới dạng XML trong gói `.docx`. |
| **Nếu tôi muốn hình chỉ xuất hiện trong chế độ xem in thì sao?** | Sử dụng thuộc tính `Shape.IsPrint` thay vì `Hidden`. Đặt `IsPrint = false` sẽ ẩn hình khỏi đầu ra in nhưng vẫn hiển thị trên màn hình. |
| **Làm thế nào để bật lại hình sau này?** | Tải tài liệu, tìm hình (ví dụ, bằng `Shape.Name`), sau đó đặt `shape.Hidden = false;` và lưu. |
| **Điều này có hoạt động với định dạng .doc (nhị phân) không?** | Có, Aspose.Words có thể lưu thành `.doc` bằng cách sử dụng `document.Save("file.doc");`. Thuộc tính ẩn được giữ nguyên. |

## Mẹo chuyên nghiệp

- **Đặt tên cho các hình**: `rectangleShape.Name = "PlaceholderRectangle";` giúp việc tìm kiếm sau này dễ dàng hơn qua `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Xử lý hàng loạt**: Nếu bạn cần thêm các hình ẩn vào nhiều tài liệu, hãy bọc mã trong một phương thức và tái sử dụng đối tượng `DocumentBuilder`.
- **Hiệu năng**: Tạo một hình là thao tác nhẹ, nhưng lưu các tài liệu lớn thường xuyên có thể bị giới hạn bởi I/O. Hãy cân nhắc sử dụng `MemoryStream` cho quá trình xử lý trung gian.

## Kết luận

Bây giờ bạn đã biết cách **tạo một tài liệu Word trống**, **thêm một hình chữ nhật**, và **ẩn hình trong Word** bằng Aspose.Words cho .NET. Kỹ thuật này cho phép bạn nhúng các chỗ giữ ẩn mà bạn có thể bật lại hoặc thao tác sau này, một mẫu hữu ích cho việc tạo báo cáo động, nội dung có điều kiện, và mẫu tài liệu.

Các bước tiếp theo bạn có thể khám phá:

- Thay thế hình chữ nhật bằng ảnh hoặc biểu đồ bằng `ShapeType.Picture`.
- Sử dụng **cách chèn hình** trong các phần header/footer để tạo chỗ giữ kiểu watermark.
- Kết hợp các hình ẩn với việc **thêm hình chữ nhật** để thực hiện kiểm tra dữ liệu (ví dụ, lưu JSON trong thuộc tính `AlternativeText` của hình).

Chúc lập trình vui vẻ, và hãy thoải mái thử nghiệm các loại hình khác và các tùy chọn hiển thị để phù hợp với nhu cầu tự động hoá tài liệu của bạn!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Word Document – How to Add Rectangle Shape and Shadow](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}