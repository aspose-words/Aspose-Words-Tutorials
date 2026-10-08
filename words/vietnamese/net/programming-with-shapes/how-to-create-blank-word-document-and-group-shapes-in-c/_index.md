---
category: general
date: 2026-10-07
description: Tạo tài liệu Word trống bằng C# và học cách thêm hình chữ nhật, chèn
  hình ảnh, và nhóm nhiều hình lại để tạo báo cáo động.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: vi
lastmod: 2026-10-07
og_description: Tạo tài liệu Word trống trong C# với Aspose.Words. Tìm hiểu cách thêm
  hình chữ nhật, chèn hình ảnh và nhóm nhiều hình lại để tạo tài liệu chuyên nghiệp.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Tạo tài liệu Word trống và nhóm các hình dạng trong C# – hướng dẫn chi tiết
  từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Cách tạo tài liệu Word trống và nhóm các hình dạng trong C#
url: /vi/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word trống và nhóm các hình dạng trong C#

Nếu bạn cần **tạo tài liệu Word trống** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Bạn sẽ thấy cách **thêm hình chữ nhật**, **chèn hình ảnh**, và **nhóm nhiều hình dạng** để chúng hoạt động như một đối tượng duy nhất khi bạn **thêm hình ảnh vào Word** sau này.

Làm việc với các tệp Word từ mã có thể gây cảm giác khó khăn, nhưng Aspose.Words làm cho quá trình này trở nên đơn giản. Khi kết thúc tutorial, bạn sẽ có một đoạn mã C# có thể tái sử dụng để tạo ra một tệp Word sạch, trống, chứa một hình chữ nhật và logo đã được nhóm. Bạn có thể nhúng kết quả này vào hoá đơn, báo cáo, hoặc bất kỳ quy trình tài liệu tự động nào.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+).  
* Giấy phép Aspose.Words for .NET hợp lệ hoặc khóa dùng thử miễn phí.  
* Một tệp hình ảnh (ví dụ: `logo.png`) được đặt trong thư mục bạn có thể tham chiếu từ mã.  
* Visual Studio 2022 hoặc bất kỳ IDE nào hỗ trợ C#.

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Cách tạo tài liệu Word trống với Aspose.Words

Bước đầu tiên luôn là **tạo tài liệu Word trống**. Đối tượng này sẽ chứa tất cả các hình dạng tiếp theo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` đại diện cho toàn bộ tệp `.docx`. Tại thời điểm này tệp vẫn rỗng, đáp ứng yêu cầu *tạo tài liệu Word trống*.

## Tạo một container để nhóm nhiều hình dạng

Nhóm các hình dạng cho phép bạn di chuyển, xoay hoặc thay đổi kích thước chúng cùng nhau. Aspose.Words cung cấp lớp `GroupShape` cho mục đích này.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Hình chữ nhật `Bounds` xác định vị trí của nhóm trên trang. Bằng cách đặt nhóm trong đoạn văn đầu tiên, bạn đảm bảo rằng **tạo tài liệu Word trống** sẽ ngay lập tức chứa một container trực quan.

## Cách thêm hình chữ nhật vào trong nhóm

Một yêu cầu phổ biến là **thêm hình chữ nhật** làm nền hoặc viền. Đoạn mã sau tạo một hình chữ nhật và thêm nó vào nhóm đã định nghĩa trước.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Vì hình chữ nhật nằm bên trong `GroupShape`, nó sẽ di chuyển cùng với bất kỳ hình dạng nào khác bạn thêm sau này. Đây là phần cốt lõi của chức năng **nhóm nhiều hình dạng**.

## Cách chèn hình ảnh vào trong nhóm

Tiếp theo, bạn sẽ **chèn hình ảnh** (logo) và đặt nó bên cạnh hình chữ nhật. Điều này minh họa quy trình **thêm hình ảnh vào Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Phương thức `SetImage` đọc tệp và nhúng trực tiếp vào tài liệu Word, đảm bảo hình ảnh vẫn tồn tại ngay cả khi tệp nguồn bị di chuyển. Điều này hoàn thành bước **chèn hình ảnh** và đáp ứng yêu cầu **thêm hình ảnh vào Word**.

## Lưu tài liệu

Cuối cùng, ghi tệp ra đĩa. Tệp đã lưu sẽ chứa tài liệu trống, nhóm hình chữ nhật và logo đã nhúng.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Khi bạn mở `GroupShape.docx` trong Microsoft Word, sẽ thấy một nhóm duy nhất bao gồm một hình chữ nhật màu xám nhạt và logo được đặt cạnh nhau. Việc chọn bất kỳ phần nào của nhóm đều cho phép bạn di chuyển hoặc thay đổi kích thước toàn bộ bộ sưu tập, chứng minh rằng các hình dạng thực sự **nhóm nhiều hình dạng**.

## Ví dụ hoàn chỉnh, có thể chạy được

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép, dán và chạy. Thay `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối tồn tại trên máy của bạn.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Kết quả mong đợi

* Một tệp có tên `GroupShape.docx` nằm trong `YOUR_DIRECTORY`.  
* Mở tệp trong Word sẽ hiển thị một nhóm trực quan duy nhất chứa một hình chữ nhật màu xám ở bên trái và `logo.png` ở bên phải.  
* Khi chọn bất kỳ phần nào của nhóm, bạn có thể di chuyển hoặc thay đổi kích thước toàn bộ bộ sưu tập, xác nhận rằng các hình dạng đã được **nhóm nhiều hình dạng** đúng cách.

## Các câu hỏi thường gặp và xử lý các trường hợp đặc biệt

| Câu hỏi | Trả lời |
|---|---|
| **Tôi có thể thêm hơn hai hình dạng vào cùng một nhóm không?** | Có. Gọi `group.AppendChild(yourShape)` cho mỗi `Shape` bổ sung. Nhóm có thể chứa bất kỳ số lượng đối tượng vẽ nào. |
| **Nếu tệp hình ảnh bị thiếu thì sao?** | `SetImage` sẽ ném ra `FileNotFoundException`. Hãy bao quanh lời gọi này bằng khối try‑catch và cung cấp phương án dự phòng (ví dụ: một hình dạng placeholder). |
| **Có cần đặt `WrapType` cho các hình dạng không?** | Mặc định các hình dạng là inline. Nếu bạn cần hành vi nổi, đặt `picture.WrapType = WrapType.Inline;` hoặc một chế độ wrap khác trước khi thêm vào nhóm. |
| **Kích thước tài liệu ảnh hưởng như thế nào đến giới hạn của nhóm?** | Hình chữ nhật `Bounds` được định nghĩa bằng điểm (1 pt ≈ 1/72 in). Điều chỉnh kích thước nếu bạn đặt nhóm trên bố cục trang khác (ví dụ: A4 so với Letter). |
| **Tôi có thể tái sử dụng cùng một nhóm trong tài liệu khác không?** | Có. Clone nhóm bằng `GroupShape cloned = (GroupShape)group.Clone(true);` và chèn nó vào một `Document` khác. |

## Mẹo chuyên nghiệp

* **Tái sử dụng `DocumentBuilder`** để thêm văn bản trước hoặc sau nhóm. Nó tự động tuân theo vị trí con trỏ hiện tại.  
* **Đặt `Shape.StrokeColor`** nếu bạn cần viền hiển thị quanh hình chữ nhật.  
* **Sử dụng PNG độ phân giải cao** cho logo để tránh hiện tượng pixel khi

## Bạn nên học gì tiếp theo?

Các tutorial sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích chi tiết từng bước, giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}