---
category: general
date: 2026-10-26
description: Tạo một tài liệu Word trống trong C# và học cách chèn một nhóm hình dạng,
  sau đó thêm một hình chữ nhật vào nhóm. Hướng dẫn này trình bày cách nhóm nhiều
  hình dạng từng bước một.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: vi
lastmod: 2026-10-26
og_description: Tạo tài liệu Word trống trong C# và xem cách chèn nhóm, sau đó thêm
  hình chữ nhật. Thành thạo việc nhóm nhiều hình dạng với ví dụ mã đầy đủ.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Tạo tài liệu Word trống và nhóm nhiều hình – Hướng dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách tạo tài liệu Word trống và nhóm nhiều hình dạng
url: /vi/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống và nhóm nhiều hình dạng

Nếu bạn cần **tạo tài liệu Word trống** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy cách chèn một nhóm hình, sau đó **thêm hình chữ nhật** vào nhóm đó, bao quát toàn bộ quy trình từ tài liệu rỗng đến bản vẽ đã nhóm.

Làm việc với các tệp Word thường đồng nghĩa với việc sắp xếp nhiều bản vẽ lại với nhau — tưởng tượng một sơ đồ được tạo từ nhiều hình dạng. Khi kết thúc hướng dẫn này, bạn sẽ có thể **nhóm nhiều hình dạng**, chèn một **hình chữ nhật**, và hiểu **cách chèn nhóm** và **cách thêm hình chữ nhật** một cách sạch sẽ, có thể tái sử dụng.

## Những gì bạn cần

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
* Gói NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)
* Kiến thức cơ bản về C# và môi trường Visual Studio IDE (bất kỳ IDE nào cũng được)

> **Pro tip:** Aspose.Words chạy hoàn toàn offline; bạn không cần kết nối internet sau khi đã cài đặt gói.

## Bước 1: Tạo tài liệu Word trống

Hoạt động đầu tiên là khởi tạo một đối tượng `Document` rỗng. Đối tượng này đại diện cho **tài liệu Word trống** mà bạn sẽ bổ sung các hình dạng sau này.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Lý do quan trọng:* Một `Document` không có bất kỳ phần hay đoạn văn nào vẫn là một tệp .docx hợp lệ. Bắt đầu từ một trang trắng đảm bảo không có định dạng ẩn can thiệp vào các hình dạng bạn sẽ thêm sau.

## Bước 2: Chèn một nhóm hình (cách chèn nhóm)

Một **nhóm hình** hoạt động như một container có thể chứa các đối tượng vẽ khác. Trong Aspose.Words bạn tạo nó bằng `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Tại sao nên dùng nhóm?* Nhóm cho phép bạn di chuyển, xoay hoặc thay đổi kích thước nhiều hình dạng như một đơn vị duy nhất. Điều này rất cần thiết cho các sơ đồ mà các thành phần phải giữ căn chỉnh với nhau.

## Bước 3: Chèn một hình chữ nhật (chèn hình chữ nhật)

Bây giờ thêm một hình chữ nhật vào tài liệu. Phương thức `InsertShape` trả về một đối tượng `Shape` mà bạn có thể gắn vào nhóm sau này.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Tại sao lại là hình chữ nhật?* Hình chữ nhật là khối xây dựng phổ biến nhất cho lưu đồ, mô phỏng UI và các đồ họa placeholder. Kích thước được biểu thị bằng điểm (1 pt ≈ 1/72 inch).

## Bước 4: Thêm hình chữ nhật vào nhóm (cách thêm hình chữ nhật)

Một hình được tạo bằng `InsertShape` sẽ nằm trực tiếp trong phần thân tài liệu. Để đưa nó vào nhóm, gọi `AppendChild` trên `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Điều gì xảy ra phía sau?* `AppendChild` di chuyển nút hình chữ nhật từ câu chuyện chính của tài liệu vào bộ sưu tập nội bộ của nhóm, giữ nguyên kích thước và vị trí tương đối so với gốc của nhóm.

## Bước 5: Lưu tài liệu

Cuối cùng, ghi tệp ra đĩa. Bạn có thể mở file `.docx` kết quả trong Microsoft Word để xem hình chữ nhật đã được nhóm.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Trường hợp đặc biệt:** Nếu bạn muốn thêm nhiều hình dạng khác (ví dụ: vòng tròn, đường thẳng) vào cùng một nhóm, lặp lại **Bước 3** và **Bước 4** cho mỗi hình mới trước khi lưu. Nhóm sẽ tự động điều chỉnh hộp bao để chứa tất cả các thành phần con.

## Cách nhóm nhiều hình dạng – mở rộng ví dụ

Dưới đây là một đoạn mã nhanh thêm một hình dạng thứ hai (hình elip) vào cùng một nhóm, minh họa **nhóm nhiều hình dạng** trong một tài liệu duy nhất.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Khi bạn mở `GroupedShapeExample.docx`, bạn sẽ thấy hình chữ nhật và elip di chuyển cùng nhau khi chọn nhóm trong Word.

## Các câu hỏi thường gặp và khắc phục sự cố

| Câu hỏi | Trả lời |
|----------|--------|
| **Tôi có cần giấy phép cho Aspose.Words không?** | Bản đánh giá miễn phí hoạt động mà không cần giấy phép, nhưng sẽ có watermark. Đối với môi trường production, áp dụng giấy phép để loại bỏ watermark và mở khóa hiệu năng đầy đủ. |
| **Tôi có thể định vị các hình dạng một cách chính xác không?** | Có. Sau khi chèn hình, bạn có thể đặt các thuộc tính `Shape.Left`, `Shape.Top`, `Shape.Width` và `Shape.Height`. |
| **Nếu hình chữ nhật biến mất sau khi lưu thì sao?** | Đảm bảo bạn gọi `group.AppendChild(rectangle)` *sau* khi chèn hình chữ nhật. Việc thêm hình vào phần thân tài liệu trước rồi mới di chuyển vào nhóm là bắt buộc. |
| **Có thể nhóm các hình dạng qua các phần khác nhau không?** | Không. Tất cả các hình trong một nhóm phải thuộc cùng một câu chuyện (section). Nếu cần, tạo các nhóm riêng cho mỗi phần. |

## Tóm tắt

Bây giờ bạn đã biết cách **tạo tài liệu Word trống**, **chèn nhóm**, **thêm hình chữ nhật**, và **nhóm nhiều hình dạng** bằng Aspose.Words cho .NET. Ví dụ hoàn chỉnh, có thể chạy được ở trên có thể sao chép vào một ứng dụng console và thực thi ngay lập tức.

## Các bước tiếp theo

* Thử nghiệm với kích thước và màu sắc của **hình chữ nhật** (`rectangle.FillColor = Color.LightBlue;`).  
* Khám phá các loại hình dạng khác (`ShapeType.Polygon`, `ShapeType.Line`) để làm phong phú hơn các sơ đồ của bạn.  
* Tìm hiểu cách chuyển đổi `.docx` cuối cùng sang PDF (`doc.Save("output.pdf");`) để phân phối.  
* Đào sâu vào **cách thêm hình chữ nhật** vào các tài liệu đã có sẵn nội dung—sử dụng `DocumentBuilder.MoveTo` để đặt nhóm ở vị trí mong muốn.

Hãy tự do điều chỉnh mã cho nhu cầu báo cáo hoặc tạo sơ đồ của riêng bạn. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có mã mẫu đầy đủ và giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create blank Word document and group shapes in C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [How to group shapes in Word and add shapes to Word document](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}