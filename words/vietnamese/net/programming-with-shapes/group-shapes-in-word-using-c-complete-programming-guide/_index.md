---
category: general
date: 2026-10-13
description: Nhóm các hình dạng trong Word bằng C# – học cách nhóm các hình dạng và
  thêm hình dạng vào nhóm bằng Aspose.Words trong vài bước đơn giản.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- add shapes to group
language: vi
lastmod: 2026-10-13
og_description: Nhóm các hình dạng trong Word bằng C# và Aspose.Words. Tham khảo hướng
  dẫn này để học cách nhóm các hình dạng và thêm hình dạng vào nhóm trong tài liệu
  Word.
og_image_alt: Screenshot of a Word document showing two shapes combined into a single
  grouped shape
og_title: Nhóm các hình dạng trong Word bằng C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  headline: Group shapes in Word using C# – complete programming guide
  type: TechArticle
- description: group shapes in Word with C# – learn how to group shapes and add shapes
    to group using Aspose.Words in a few easy steps.
  name: Group shapes in Word using C# – complete programming guide
  steps:
  - name: Load the Word document
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Retrieve the shapes you want to group
    text: '```csharp // Get the first shape (index 0) and second shape (index 1) from
      the whole document. Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0,
      true); Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true); ```'
  - name: Create a new `GroupShape` container
    text: '```csharp GroupShape groupShape = new GroupShape(doc); ```'
  - name: Add the individual shapes to the group
    text: '```csharp groupShape.AppendChild(firstShape); groupShape.AppendChild(secondShape);
      ```'
  - name: Insert the group shape into the document body
    text: '```csharp // Insert the group as the last child of the first paragraph.
      Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph; firstParagraph.AppendChild(groupShape);
      ```'
  - name: Save the modified document
    text: '```csharp string outputPath = @"YOUR_DIRECTORY\output.docx"; doc.Save(outputPath);
      ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Nhóm các hình dạng trong Word bằng C# – hướng dẫn lập trình đầy đủ
url: /vi/net/programming-with-shapes/group-shapes-in-word-using-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nhóm các hình dạng trong Word bằng C# – hướng dẫn lập trình đầy đủ

Nếu bạn cần **nhóm các hình dạng trong Word** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác. Sau hai câu đầu tiên, bạn sẽ biết đoạn mã cần thiết, lý do cho mỗi bước, và cách **thêm hình dạng vào nhóm** mà không gặp bất ngờ.

Chúng tôi sẽ đề cập đến mọi thứ từ việc tải một tệp `.docx` đến lưu tài liệu đã cập nhật. Bài hướng dẫn giả định bạn đã có kiến thức cơ bản về C# và đã tham chiếu thư viện Aspose.Words for .NET. Không cần tài liệu bên ngoài—chỉ cần sao chép, dán và chạy.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Một tài liệu Word (`input.docx`) đã chứa ít nhất hai hình dạng (ví dụ: ảnh, AutoShape)

> **Mẹo chuyên nghiệp:** Nếu bạn đang thử nghiệm, tạo một tệp Word đơn giản với hai hình chữ nhật qua giao diện Word. Lưu nó dưới tên `input.docx` trong một thư mục bạn kiểm soát.

## Nhóm các hình dạng trong Word – hướng dẫn từng bước

Dưới đây chúng tôi chia quy trình thành năm bước logic. Mỗi bước bao gồm đoạn mã C# chính xác, giải thích *tại sao* dòng mã cần thiết, và một ghi chú ngắn về những lỗi thường gặp.

### Bước 1: Tải tài liệu Word

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
```

**Tại sao:** `Document` là điểm vào cho mọi thao tác với Word. Cung cấp đường dẫn đầy đủ sẽ tải tài liệu vào bộ nhớ, cho phép chúng ta truy vấn và sửa đổi cây node của nó.

**Cạm bẫy:** Truyền đường dẫn tương đối có thể thất bại khi thư mục làm việc khác nhau. Hãy dùng đường dẫn tuyệt đối hoặc `Path.Combine` với `AppContext.BaseDirectory`.

### Bước 2: Lấy các hình dạng bạn muốn nhóm

```csharp
// Get the first shape (index 0) and second shape (index 1) from the whole document.
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);
```

**Tại sao:** `GetChild` duyệt cây tài liệu và trả về node *thứ n* của kiểu được yêu cầu. Đặt `isDeep` thành `true` sẽ tìm kiếm toàn bộ tài liệu, không chỉ trong phần hiện tại.

**Trường hợp đặc biệt:** Nếu tài liệu chứa ít hơn hai hình dạng, `firstShape` hoặc `secondShape` sẽ là `null` và sẽ ném ngoại lệ khi chúng ta cố gắng ép kiểu. Hãy kiểm tra trước:

```csharp
if (firstShape == null || secondShape == null)
    throw new InvalidOperationException("The document must contain at least two shapes to group.");
```

### Bước 3: Tạo một container `GroupShape` mới

```csharp
GroupShape groupShape = new GroupShape(doc);
```

**Tại sao:** `GroupShape` hoạt động như một node cha có thể chứa nhiều đối tượng `Shape`. Nó kế thừa từ `Shape`, vì vậy có thể chèn ở bất kỳ vị trí nào cho phép chèn hình dạng thường (ví dụ: trong một đoạn văn).

### Bước 4: Thêm các hình dạng riêng lẻ vào nhóm

```csharp
groupShape.AppendChild(firstShape);
groupShape.AppendChild(secondShape);
```

**Tại sao:** `AppendChild` di chuyển các hình dạng từ vị trí gốc vào nhóm mới. Sau lệnh này, các hình dạng gốc không còn tồn tại như các node độc lập; chúng trở thành một phần của `groupShape`.

**Mẹo:** Khi nhóm, vị trí tương đối của các hình con sẽ tự động được điều chỉnh. Nếu bạn cần bố cục cụ thể, hãy đặt thuộc tính `GroupShape.Bounds` *trước* khi thêm các con vào.

```csharp
// Example: set the group to start at (100, 100) points and be 300x200 points large.
groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);
```

### Bước 5: Chèn nhóm hình dạng vào phần thân tài liệu

```csharp
// Insert the group as the last child of the first paragraph.
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
firstParagraph.AppendChild(groupShape);
```

**Tại sao:** Một `GroupShape` phải được đặt bên trong một đoạn văn (hoặc một ô bảng) để được hiển thị. Bằng cách thêm nó vào đoạn văn đầu tiên, chúng ta đảm bảo vị trí hiển thị mà không làm gián đoạn bố cục hiện có.

### Bước 6: Lưu tài liệu đã chỉnh sửa

```csharp
string outputPath = @"YOUR_DIRECTORY\output.docx";
doc.Save(outputPath);
```

**Tại sao:** `Save` ghi các thay đổi trong bộ nhớ trở lại tệp `.docx`. Bạn cũng có thể lưu vào luồng hoặc sang PDF bằng cách thay đổi overload.

**Xác minh kết quả:** Mở `output.docx` trong Microsoft Word. Bạn sẽ thấy hai hình dạng gốc hiện giờ đã được kết hợp thành một đối tượng nhóm duy nhất. Khi chọn nhóm, sẽ xuất hiện các tay cầm nhóm tiêu chuẩn của Word.

## Cách nhóm các hình dạng bằng lập trình – hiểu sâu hơn

- **Quyền sở hữu node:** Khi bạn gọi `AppendChild`, tham chiếu `ParentNode` của hình dạng sẽ tự động thay đổi. Điều này ngăn ngừa các node “mồ côi” có thể làm hỏng tài liệu.
- **Bảo toàn định dạng:** Việc nhóm **không** làm mất bất kỳ định dạng nào của hình dạng (màu nền, kiểu đường viền, v.v.). Tất cả các hình con giữ nguyên các thuộc tính gốc.
- **Nhóm lồng nhau:** `GroupShape` có thể chứa các đối tượng `GroupShape` khác, cho phép tạo cấu trúc đa cấp. Chỉ cần xử lý nhóm bên trong như bất kỳ hình dạng nào khác.

## Thêm hình dạng vào nhóm và quản lý chúng sau này

Nếu bạn cần thêm nhiều hình dạng sau khi đã tạo nhóm ban đầu, có thể tái sử dụng cùng một thể hiện `GroupShape`:

```csharp
// Assume we have a third shape somewhere in the document.
Shape thirdShape = (Shape)doc.GetChild(NodeType.Shape, 2, true);
groupShape.AppendChild(thirdShape);
```

Khi cần tách nhóm, duyệt qua `groupShape.GetChildNodes(NodeType.Shape, true)` và chèn lại từng con vào vị trí mong muốn.

```csharp
foreach (Shape child in groupShape.GetChildNodes(NodeType.Shape, true))
{
    // Example: move each child back to the original paragraph.
    firstParagraph.AppendChild(child);
}
firstParagraph.RemoveChild(groupShape); // Remove the empty group container.
```

**Tại sao điều này quan trọng:** Một số quy trình làm việc yêu cầu nhóm tạm thời (ví dụ: căn chỉnh nhiều đối tượng) rồi tách nhóm để chỉnh sửa từng đối tượng riêng lẻ.

## Ví dụ hoàn chỉnh có thể chạy được

Dưới đây là một chương trình tự chứa mà bạn có thể biên dịch và chạy ngay. Thay `YOUR_DIRECTORY` bằng đường dẫn thư mục thực tế trên máy của bạn.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the document.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2. Retrieve the first two shapes.
        Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        Shape secondShape = (Shape)doc.GetChild(NodeType.Shape, 1, true);

        if (firstShape == null || secondShape == null)
        {
            Console.WriteLine("Document must contain at least two shapes.");
            return;
        }

        // 3. Create a GroupShape container.
        GroupShape groupShape = new GroupShape(doc);

        // Optional: define the group’s bounding box.
        groupShape.Bounds = new System.Drawing.RectangleF(100, 100, 300, 200);

        // 4. Add the shapes to the group.
        groupShape.AppendChild(firstShape);
        groupShape.AppendChild(secondShape);

        // 5. Insert the group into the first paragraph.
        Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(groupShape);

        // 6. Save the result.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Grouped shapes saved to {outputPath}");
    }
}
```

**Kết quả mong đợi:** Khi mở `output.docx`, hai hình dạng gốc sẽ xuất hiện dưới dạng một đối tượng nhóm duy nhất. Khi chọn nhóm, sẽ hiển thị các tay cầm nhóm quen thuộc của Word, cho phép bạn di chuyển, thay đổi kích thước hoặc xoay toàn bộ tập hợp cùng lúc.

## Kết luận

Bây giờ bạn đã biết cách **nhóm các hình dạng trong Word** bằng C# và Aspose.Words, và đã thấy các bước chính xác để **thêm hình dạng vào nhóm** và sau đó thao tác hoặc tách chúng. Kỹ thuật này rất phù hợp để tự động hoá bố cục báo cáo, tạo biểu đồ tổng hợp, hoặc chuẩn bị mẫu Word cần định vị chính xác nhiều đối tượng.

Tiếp theo, hãy khám phá các chủ đề liên quan như **cách nhóm các hình dạng** với các loại neo khác nhau, áp dụng **định dạng nâng cao** cho các đối tượng đã nhóm, hoặc xuất kết quả đã nhóm ra PDF. Thử nghiệm việc lồng nhóm để xây dựng đồ họa phức tạp một cách lập trình.

Chúc lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Shadow Effect to Word Shapes – Complete C# Guide](/words/english/net/programming-with-shapes/add-shadow-effect-to-word-shapes-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}