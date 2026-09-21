---
category: general
date: 2026-09-21
description: Tìm hiểu cách nhóm các hình dạng trong Word bằng Aspose.Words cho C#.
  Hướng dẫn từng bước này bao gồm việc tạo, định vị và lưu các hình dạng đã nhóm.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: vi
lastmod: 2026-09-21
og_description: Nhóm các hình dạng trong Word bằng Aspose.Words cho C#. Tham khảo
  hướng dẫn ngắn gọn này để tạo, đặt vị trí và lưu các nhóm hình dạng một cách lập
  trình.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Nhóm các hình dạng trong Word bằng Aspose.Words – hướng dẫn C# đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Cách nhóm các hình dạng trong Word bằng Aspose.Words cho C#
url: /vi/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhóm các hình dạng trong Word bằng Aspose.Words cho C#

Nếu bạn cần **nhóm các hình dạng trong Word** một cách lập trình, Aspose.Words giúp thực hiện điều này một cách đơn giản. Hướng dẫn này sẽ chỉ cho bạn cách tạo hai hình chữ nhật, đặt chúng cạnh nhau, kết hợp chúng thành một `GroupShape`, và lưu kết quả dưới dạng tệp DOCX.

Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được, giải thích lý do mỗi bước quan trọng, và mẹo xử lý các trường hợp đặc biệt như hình chồng lên nhau hoặc kích thước động. Khi hoàn thành hướng dẫn này, bạn có thể tích hợp việc nhóm hình dạng vào bất kỳ dự án tự động hoá Word nào.

## Các yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 (hoặc mới hơn) được cài đặt – Aspose.Words hỗ trợ .NET Standard 2.0+, .NET Core và .NET Framework.
* Giấy phép Aspose.Words for .NET hợp lệ (hoặc khóa đánh giá tạm thời) – thư viện vẫn hoạt động mà không có giấy phép nhưng sẽ thêm watermark.
* Visual Studio 2022 (hoặc bất kỳ IDE C# nào) để biên dịch và chạy mẫu.

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words`.

## Cách nhóm các hình dạng trong Word bằng Aspose.Words

Cốt lõi của giải pháp là một đối tượng **`GroupShape`** hoạt động như một container cho các hình dạng riêng lẻ. Dưới đây chúng ta sẽ chia quá trình thành các bước rõ ràng.

### Bước 1: Tạo tài liệu trống và một `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Tại sao cần bước này?*  
`Document` đại diện cho toàn bộ tệp DOCX, trong khi `DocumentBuilder` cung cấp các phương thức fluent (ví dụ: `InsertShape`) tự động đặt các phần tử mới tại vị trí con trỏ hiện tại.

### Bước 2: Chèn hình chữ nhật đầu tiên

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Lệnh `InsertShape` thêm hình vào tài liệu và trả về một đối tượng `Shape` mà bạn có thể cấu hình thêm (màu, viền, v.v.). Kích thước được biểu thị bằng điểm (1 pt ≈ 1/72 in).

### Bước 3: Chèn hình chữ nhật thứ hai và dịch chuyển nó

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Thiết lập `Left` định vị hình so với lề trang. Khoảng dịch chuyển phải lớn hơn chiều rộng của hình đầu tiên (100 pt) để tránh chồng lấn; chúng ta dùng 120 pt để để lại một khoảng cách nhỏ.

### Bước 4: Tạo một `GroupShape` đủ lớn cho cả hai hình chữ nhật

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` nhận `Document` sở hữu và kích thước container. Chiều rộng của container phải vượt quá cạnh phải của hình cách xa nhất; nếu không, hình thứ hai sẽ bị cắt.

### Bước 5: Thêm các hình riêng lẻ vào nhóm

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Việc thêm (append) di chuyển các hình vào bộ sưu tập nội bộ của nhóm. Sau lệnh này, các hình không còn là các đối tượng độc lập trong cây tài liệu – chúng thuộc về nhóm.

### Bước 6: Chèn lại hình đã nhóm vào tài liệu

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` đặt toàn bộ `GroupShape` vào vị trí con trỏ hiện tại. Nếu bạn cần nhóm ở một đoạn văn cụ thể, hãy di chuyển builder tới đoạn văn đó trước.

### Bước 7: Lưu tài liệu

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Tệp kết quả chứa hai hình chữ nhật hoạt động như một đối tượng duy nhất – bạn có thể di chuyển, thay đổi kích thước hoặc xóa chúng cùng nhau trong Microsoft Word.

## Mã nguồn đầy đủ

Kết hợp tất cả các bước lại sẽ tạo ra một chương trình tự chứa:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Kết quả mong đợi:** Mở *GroupedShapes.docx* trong Microsoft Word sẽ hiển thị hai hình chữ nhật cạnh nhau, được xử lý như một đối tượng có thể chọn duy nhất. Kéo nhóm sẽ di chuyển cả hai hình cùng lúc.

## Các biến thể phổ biến và trường hợp đặc biệt

| Tình huống | Điều chỉnh đề xuất |
|-----------|--------------------|
| **Nhiều hơn hai hình** | Tạo thêm các đối tượng `Shape`, định vị chúng tương ứng, và thêm từng cái vào cùng một `GroupShape`. |
| **Kích thước động** | Tính chiều rộng/chiều cao của nhóm dựa trên giá trị `Right` và `Bottom` lớn nhất của các hình con. |
| **Các loại hình dạng khác nhau** | `ShapeType.Ellipse`, `ShapeType.Triangle`, v.v., có thể chèn theo cùng cách; container nhóm không quan tâm tới loại. |
| **Hình dạng xoay** | Đặt `shape.Rotation = 45;` trước khi thêm; góc xoay sẽ được giữ lại trong nhóm. |
| **Lưu dưới dạng PDF** | Gọi `doc.Save("GroupedShapes.pdf");` – nhóm sẽ được giữ lại trong bản render PDF. |

**Mẹo chuyên nghiệp:** Sau khi nhóm, bạn vẫn có thể sửa đổi các hình riêng lẻ bằng cách truy cập `group.GetChildNodes(NodeType.Shape, true)`. Điều này hữu ích khi bạn muốn thay đổi màu nền của một hình chữ nhật mà không phá vỡ nhóm.

## Cách kiểm tra việc nhóm một cách lập trình

Nếu bạn cần xác nhận rằng các hình đã được nhóm đúng cách (ví dụ, trong các bài kiểm thử đơn vị), hãy kiểm tra cấu trúc cây node của tài liệu:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Kết quả nên là:

```
Number of groups: 1
Children in first group: 2
```

Điều này xác nhận rằng **nhóm các hình dạng trong Word** đã được tạo như mong đợi.

## Kết luận

Bây giờ bạn đã biết cách **nhóm các hình dạng trong Word** bằng Aspose.Words cho C#. Quy trình bao gồm tạo các hình riêng lẻ, định vị chúng, gói chúng trong một `GroupShape`, và chèn nhóm trở lại tài liệu. Với ví dụ hoàn chỉnh ở trên, bạn có thể mở rộng kỹ thuật này cho bất kỳ số lượng hình nào, các loại hình khác nhau, hoặc thậm chí kết hợp chúng với các hộp văn bản và hình ảnh.

Tiếp theo, hãy khám phá các chủ đề liên quan như **Aspose.Words shape grouping**, **C# Word shape manipulation**, và **DocumentBuilder insert shape** để thực hiện các kịch bản tự động hoá tài liệu nâng cao hơn. Thử nghiệm với kích thước động, nhóm có điều kiện, và xuất ra PDF để tận dụng tối đa sức mạnh của Aspose.Words.

## Bạn Nên Học Gì Tiếp Theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}