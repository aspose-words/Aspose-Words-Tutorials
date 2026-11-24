---
category: general
date: 2026-11-18
description: Học cách tạo hình chữ nhật trong tài liệu Word bằng C#. Hướng dẫn cũng
  bao gồm cách đặt kích thước hình, đặt vị trí hình và nhóm các hình trong Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: vi
lastmod: 2026-11-18
og_description: Tạo hình chữ nhật trong tệp Word bằng C# và học cách đặt kích thước
  hình, đặt vị trí hình và nhóm các hình trong Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Tạo hình chữ nhật và nhóm các hình dạng trong Word bằng C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cách tạo hình chữ nhật và nhóm các hình trong Word bằng C#
url: /vi/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo hình chữ nhật và nhóm các hình trong Word bằng C#

Nếu bạn cần **tạo hình chữ nhật** trong một tài liệu Word, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, sẵn sàng chạy. Bạn sẽ thấy cách đặt kích thước hình, đặt vị trí hình và nhóm các hình trong Word để chúng hoạt động như một đối tượng duy nhất.

Làm việc với các hình là yêu cầu phổ biến khi tạo báo cáo, hoá đơn hoặc sơ đồ một cách lập trình. Khi kết thúc hướng dẫn này, bạn sẽ có thể tạo một tệp `.docx` chứa một hình chữ nhật, một hình elip và một container được nhóm — tất cả đều được tạo bằng Aspose.Words cho .NET.

## Yêu cầu trước

- .NET 6.0 SDK hoặc phiên bản mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
- Gói NuGet Aspose.Words cho .NET (`Install-Package Aspose.Words`)
- Một trình soạn thảo mã hoặc IDE (Visual Studio, VS Code, Rider, v.v.)

Không cần thư viện bổ sung nào khác.

## Cách tạo hình chữ nhật và nhóm các hình trong Word

Các bước chính là:

1. **Tạo một tài liệu trống** và một `DocumentBuilder`.
2. **Chèn một `GroupShape`** sẽ chứa các hình riêng lẻ.
3. **Tạo một hình chữ nhật**, đặt kích thước và thêm vào nhóm.
4. **Tạo một hình elip**, đặt kích thước và vị trí, sau đó thêm vào nhóm.
5. **Lưu** tài liệu.

Mỗi bước được giải thích dưới đây, và mã nguồn hoàn chỉnh được đưa ra sau phần giải thích.

### Bước 1: Khởi tạo tài liệu và builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cung cấp một API lưu loát để chèn nội dung. Việc khởi tạo chúng là bắt buộc trước khi bạn có thể thêm bất kỳ hình nào.

### Bước 2: Chèn một nhóm hình

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

`GroupShape` hoạt động như một container; tất cả các hình con di chuyển cùng nhau. Đây là cách được khuyến nghị để **nhóm các hình trong Word** khi bạn cần các biến đổi chung (ví dụ: di chuyển, xoay hoặc xóa).

### Bước 3: Tạo hình chữ nhật và đặt kích thước

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Ở đây chúng ta **tạo hình chữ nhật** và **đặt kích thước hình** bằng cách gán `Width` và `Height`. Trong Aspose.Words, kích thước được biểu thị bằng điểm (1 pt ≈ 1/72 in). Đặt kích thước một cách rõ ràng đảm bảo hình chữ nhật hiển thị đúng như mong muốn.

### Bước 4: Tạo hình elip, đặt kích thước và vị trí

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

**Đặt kích thước hình** cho elip có chiều rộng và chiều cao bằng nhau, tạo ra một vòng tròn hoàn hảo. Thuộc tính `Left` minh họa **đặt vị trí hình**: elip bắt đầu cách gốc của nhóm 120 pt sang phải, vì vậy nó không chồng lên hình chữ nhật.

### Bước 5: Lưu tài liệu

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Lưu sẽ ghi tệp Word ra đĩa. Bạn có thể mở `GroupShape.docx` trong Microsoft Word để xác nhận rằng hình chữ nhật và elip đã được nhóm và đặt vị trí đúng.

## Đặt kích thước và kích thước hình – nhìn sâu hơn

- **Điểm so với inch**: 72 pt = 1 in. Nếu bạn muốn dùng inch, nhân với 72 (ví dụ, `2.5 * 72` cho 2.5 in).
- **Tự động co giãn**: Nếu bạn bỏ qua `Width` hoặc `Height`, hình sẽ sử dụng kích thước mặc định. **Đặt kích thước hình** một cách rõ ràng để tránh bất ngờ trong bố cục.
- **Tỷ lệ khung hình**: Đối với các hình như `Ellipse`, giữ `Width` và `Height` bằng nhau giúp duy trì hình dạng vòng tròn.

## Đặt vị trí một hình trong Word

Thuộc tính `Left` và `Top` kiểm soát độ dịch của hình bên trong container của nó (nhóm hoặc trang). Giá trị dương di chuyển hình sang phải/xuống; giá trị âm dịch sang trái/lên trên. Khi nhóm, vị trí được tính tương đối so với gốc của nhóm, giúp đơn giản hoá các phép tính bố cục.

## Nhóm các hình trong Word bằng Aspose.Words

Nhóm là điều cần thiết khi bạn muốn nhiều hình hoạt động như một đơn vị duy nhất. Đối tượng `GroupShape`:

- Hỗ trợ `AppendChild` để thêm bất kỳ `Shape` nào (hình chữ nhật, elip, hình ảnh, v.v.).
- Cho phép bạn di chuyển, xoay hoặc xóa toàn bộ nhóm bằng một lệnh duy nhất.
- Giữ vị trí các hình con tương đối so với nhóm, làm cho các sơ đồ phức tạp dễ quản lý hơn.

**Mẹo chuyên nghiệp:** Sau khi thêm tất cả các hình con, bạn có thể điều chỉnh `Width`, `Height`, `Left` và `Top` của nhóm để di chuyển toàn bộ bộ sưu tập trong một bước.

## Ví dụ đầy đủ có thể chạy

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép, dán và chạy. Nó bao gồm tất cả các chỉ thị `using`, một phương thức `Main`, và các chú thích giải thích từng dòng.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Kết quả mong đợi:** Sau khi chạy chương trình, `GroupShape.docx` sẽ xuất hiện trong thư mục thực thi. Mở nó trong Word sẽ thấy một hình chữ nhật (100 pt × 50 pt) ở phía trái và một hình elip (80 pt × 80 pt) được đặt cách 120 pt sang phải, cả hai nằm trong một đối tượng được nhóm duy nhất.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Ảnh chụp màn hình của một tài liệu Word hiển thị một hình chữ nhật và hình elip được nhóm tạo bằng C#" }

*Hình ảnh trên minh họa kết quả cuối cùng; hình chữ nhật và elip có thể được chọn như một nhóm duy nhất.*

## Các câu hỏi thường gặp và trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| **Tôi có thể thêm nhiều hơn hai hình không?** | Có. Gọi `group.AppendChild(yourShape)` cho mỗi hình bổ sung. |
| **Nếu tôi cần xoay nhóm thì sao?** | Sử dụng `group.RotationAngle = 45;` (độ) sau khi đã thêm tất cả các hình con. |
| **Làm sao thay đổi màu nền của nhóm?** | Đặt `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Điều này có hoạt động với tệp .doc không?** | Aspose.Words hỗ trợ `.doc` và `.docx`. Đoạn mã vẫn hoạt động; chỉ cần thay đổi phần mở rộng tệp trong `Save`. |
| **Việc nhóm nhiều hình có ảnh hưởng đến bộ nhớ không?** | Việc nhóm tự nó chỉ thêm một chút overhead. Mối quan tâm chính là tổng số hình; hãy giữ số lượng hợp lý cho các tài liệu lớn. |

## Kết luận

Trong hướng dẫn này, bạn đã học cách **tạo hình chữ nhật** trong một tệp Word bằng C#, cách **đặt kích thước hình**, **đặt kích thước hình**, **đặt vị trí hình**, và cuối cùng cách **nhóm các hình trong Word** với Aspose.Words. Ví dụ đầy đủ thể hiện một cách tiếp cận sạch sẽ, dễ bảo trì mà bạn có thể mở rộng cho các sơ đồ, biểu đồ hoặc đồ họa tùy chỉnh phức tạp hơn.

Tiếp theo, bạn có thể khám phá:

- Thêm văn bản bên trong các hình (`Shape.TextPath.Text = "Hello"`).
- Chèn hình ảnh vào một `GroupShape`.
- Xuất các hình đã nhóm ra PDF bằng `doc.Save("output.pdf")`.

Hãy tự do thử nghiệm với các kích thước, vị trí và loại hình bổ sung khác nhau để phù hợp với nhu cầu dự án của bạn. Chúc bạn lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách tạo hình chữ nhật và nhóm các hình trong Word với Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tạo hình chữ nhật trong Word bằng C# – Hướng dẫn từng bước](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}