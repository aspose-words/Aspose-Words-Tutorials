---
category: general
date: 2026-09-11
description: Học cách tạo tài liệu Word, thêm hình chữ nhật và thiết lập kích thước
  hình dạng với Aspose.Words. Hướng dẫn C# từng bước để định kích thước hình dạng
  một cách chính xác.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: vi
lastmod: 2026-09-11
og_description: Tạo tài liệu Word bằng Aspose.Words trong C#. Hướng dẫn này chỉ cách
  thêm hình chữ nhật, thiết lập kích thước hình dạng và quản lý các kích thước của
  hình dạng một cách lập trình.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Tạo tài liệu Word với các hình dạng – Hướng dẫn Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Cách tạo tài liệu Word với các hình dạng bằng Aspose.Words trong C#
url: /vi/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word có hình dạng bằng Aspose.Words trong C#

Nếu bạn cần **tạo tài liệu Word** chứa đồ họa tùy chỉnh, bạn có thể thực hiện hoàn toàn bằng mã. Hướng dẫn này sẽ chỉ cho bạn cách tạo một tệp Word, thêm một hình chữ nhật, và kiểm soát mọi kích thước của hình. Khi hoàn thành, bạn sẽ có một đoạn mã có thể tái sử dụng và chèn vào bất kỳ dự án .NET nào.

Bạn sẽ học cách **thêm hình chữ nhật**, **đặt kích thước hình**, và **đặt các chiều của hình** trong một container nhóm. Ví dụ sử dụng Aspose.Words 13.9, nhưng các khái niệm cũng áp dụng cho các phiên bản sau. Không yêu cầu kinh nghiệm trước với API vẽ của Aspose—chỉ cần kiến thức cơ bản về C#.

## Yêu cầu trước

- .NET 6.0 hoặc phiên bản mới hơn đã được cài đặt  
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Một IDE như Visual Studio 2022 (bất kỳ trình soạn thảo nào hỗ trợ C# đều được)  

Có sẵn các công cụ này sẽ cho phép bạn chạy mã ngay lập tức mà không cần cấu hình thêm.

## Bước 1: Khởi tạo tài liệu và builder – tạo các yếu tố cơ bản của tài liệu Word

Hoạt động đầu tiên là khởi tạo một đối tượng `Document` và một `DocumentBuilder`. `Document` đại diện cho tệp, trong khi `DocumentBuilder` cung cấp API dạng fluent để chèn nội dung.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng:**  
Tạo tài liệu ngay từ đầu giúp bạn có một canvas sạch sẽ. Con trỏ của builder bắt đầu ở đoạn văn đầu tiên, nơi chúng ta sẽ **tạo hình trong Word** sau này.

## Bước 2: Xây dựng một GroupShape để chứa nhiều đồ họa

`GroupShape` hoạt động như một container; bạn có thể di chuyển, xoay hoặc thay đổi kích thước toàn bộ nhóm như một đơn vị. Ở đây chúng ta định nghĩa chiều rộng và chiều cao của container bằng điểm (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Tại sao điều này quan trọng:**  
Nhóm các hình giúp đơn giản hoá việc quản lý bố cục. Nếu sau này bạn muốn thêm các hình khác (ví dụ: vòng tròn hoặc hộp văn bản), chúng sẽ kế thừa vị trí và tỉ lệ của nhóm.

## Bước 3: Tạo hình chữ nhật và cấu hình các chiều của nó

Bây giờ chúng ta thêm hình chữ nhật thực tế. Hàm khởi tạo `Shape` yêu cầu tham chiếu tới tài liệu và loại hình. Sau khi tạo, chúng ta **đặt kích thước hình** và **đặt các chiều của hình** một cách rõ ràng.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Tại sao điều này quan trọng:**  
Việc chỉ định chiều rộng, chiều cao, vị trí trái và trên cho phép bạn kiểm soát hình một cách chính xác đến pixel. Điều này rất cần thiết khi tài liệu phải tuân theo một bản thiết kế hoặc mẫu in.

## Bước 4: Lắp ráp nhóm bằng cách nối thêm hình chữ nhật

Nối hình chữ nhật vào `GroupShape` sẽ biến nó thành một nút con. Bạn có thể thêm bao nhiêu nút con tùy ý trước khi chèn nhóm vào tài liệu.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Mẹo:** Nếu bạn muốn thêm một hình thứ hai, tạo nó theo cùng cách và gọi `group.AppendChild(secondShape)`. Tất cả các nút con sẽ chia sẻ hệ tọa độ của nhóm.

## Bước 5: Chèn nhóm hình vào tài liệu và lưu

Khi nhóm đã được xây dựng hoàn chỉnh, chúng ta đặt nó vào đoạn văn hiện tại. Thuộc tính `CurrentParagraph` của builder cung cấp truy cập trực tiếp tới cây node nền.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Tại sao điều này quan trọng:**  
Nối nhóm vào một đoạn văn đảm bảo hình xuất hiện nội tuyến với luồng văn bản. Lưu tài liệu sẽ hoàn tất thao tác **tạo tài liệu Word**.

## Các biến thể phổ biến và trường hợp đặc biệt

| Kịch bản | Điều chỉnh |
|----------|------------|
| **Định hướng trang khác** | Đặt `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` trước khi tạo nhóm. |
| **Nhiều hình chữ nhật** | Tạo các đối tượng `Shape` bổ sung và gọi `group.AppendChild(newRect)` cho mỗi hình. |
| **Kích thước động dựa trên nội dung** | Tính toán chiều rộng/chiều cao từ kích thước ảnh hoặc số liệu văn bản, sau đó gán cho `rectangle.Width` / `rectangle.Height`. |
| **Xuất ra PDF** | Sau `doc.Save`, gọi `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Tương thích với các phiên bản Word cũ** | Lưu bằng `SaveFormat.Doc` thay vì `Docx` để tương thích với Word 97‑2003. |

Các biến thể này cho thấy cách logic cốt lõi có thể được điều chỉnh cho nhiều yêu cầu thực tế.

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép, dán và chạy. Nó bao gồm tất cả các chỉ thị `using`, một điểm vào `Main`, và các chú thích giải thích từng dòng.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Kết quả mong đợi:**  
Khi mở *GroupShape.docx*, trang đầu tiên sẽ hiển thị một hình chữ nhật viền xám, đặt cách lề trái/trên 50 pt, và hình chữ nhật bên trong lệch 10 pt so với nhóm. Các kích thước khớp với giá trị được đặt trong mã.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word**, **thêm hình chữ nhật**, và chính xác **đặt kích thước hình** cũng như **đặt các chiều của hình** bằng Aspose.Words. Cách tiếp cận nhóm‑hình giữ cho bố cục của bạn linh hoạt và sẵn sàng mở rộng trong tương lai, chẳng hạn như thêm đồ họa hoặc hộp văn bản khác.

Tiếp theo, khám phá các chủ đề liên quan như **tạo hình trong Word** cho vòng tròn, mũi tên, hoặc đường SVG tùy chỉnh, và học cách **đặt màu nền cho hình** hoặc **áp dụng xoay**. Thử nghiệm với các đơn vị đo khác nhau để xem Word render điểm so với centimet, và tích hợp mã vào các pipeline tạo tài liệu lớn hơn.

Chúc bạn lập trình vui vẻ, và hãy tự do điều chỉnh mẫu này cho bất kỳ kịch bản báo cáo tự động hoặc điền mẫu nào bạn gặp phải!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ và giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}