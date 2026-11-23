---
category: general
date: 2026-11-22
description: Tạo tài liệu Word bằng lập trình C# và chèn hình chữ nhật, chèn nhiều
  hình dạng, và ghi các hình dạng vào Word bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: vi
lastmod: 2026-11-22
og_description: Tạo tài liệu Word bằng C# một cách lập trình bằng cách chèn hình chữ
  nhật, chèn nhiều hình dạng và ghi các hình dạng vào Word bằng Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Tạo tài liệu Word có hình dạng bằng lập trình trong C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Tạo tài liệu Word có hình dạng bằng lập trình C#
url: /vi/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng chương trình với các hình dạng trong C#

Nếu bạn cần **tạo tài liệu Word bằng chương trình** có chứa đồ họa tùy chỉnh, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words cho .NET. Bạn sẽ học cách chèn một hình chữ nhật, thêm các hình dạng khác, nhóm chúng lại, và cuối cùng ghi các hình dạng vào Word—tất cả trong vài dòng C#.

Việc tạo tệp Word có đồ họa không còn cần chỉnh sửa thủ công hay script macro. Khi kết thúc hướng dẫn này, bạn sẽ có một phương thức tái sử dụng tạo ra tệp `.docx` chứa một hình chữ nhật và một hình ellipse được nhóm lại, sẵn sàng cho các quy trình xử lý hoặc báo cáo tiếp theo.

## Những gì bạn cần

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
- Aspose.Words cho .NET (gói NuGet `Aspose.Words`)
- Một IDE như Visual Studio 2022 (bất kỳ trình chỉnh sửa nào có thể biên dịch C# đều được)

> **Mẹo chuyên nghiệp:** Cài đặt gói bằng lệnh CLI `dotnet add package Aspose.Words` trước khi bạn bắt đầu viết mã.

## Tạo tài liệu Word bằng chương trình – tổng quan

Luồng tổng thể bao gồm ba giai đoạn logic:

1. **Khởi tạo** một `Document` mới và một `DocumentBuilder`.  
2. **Chèn nhiều hình dạng** (một hình chữ nhật và một hình ellipse) và đặt chúng vào bên trong một `GroupShape`.  
3. **Ghi các hình dạng vào Word** bằng cách lưu `Document` thành tệp `.docx`.

Mỗi giai đoạn được đóng gói trong một bước riêng bên dưới, vì vậy bạn có thể sao chép‑dán mã trực tiếp vào dự án của mình.

![Tạo tài liệu Word bằng chương trình với các hình dạng được nhóm](grouped-shapes.png){: .align-center alt="Tạo tài liệu Word bằng chương trình với các hình dạng được nhóm"}

## Bước 1: Khởi tạo tài liệu và builder

Lớp `Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cung cấp một API mượt mà để thêm nội dung.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*​Tại sao điều này quan trọng:* Việc tạo `Document` trước tiên cung cấp cho bạn một canvas sạch sẽ. `DocumentBuilder` theo dõi vị trí chèn hiện tại, điều này rất cần thiết khi bạn sau này gắn các hình dạng vào cấu trúc đoạn văn.

## Bước 2: Chèn một container GroupShape

`GroupShape` cho phép bạn xử lý nhiều hình dạng riêng lẻ như một đơn vị duy nhất. Điều này hữu ích khi bạn muốn di chuyển hoặc thay đổi kích thước chúng cùng nhau.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Giải thích:* `InsertGroupShape` chèn một container trống và tự động làm nó thành hình dạng hiện tại. Tất cả các chèn hình dạng tiếp theo sẽ được thêm vào container này cho đến khi bạn đóng nhóm.

## Chèn hình chữ nhật

Bây giờ chúng ta thêm đồ họa đầu tiên—một hình chữ nhật. Điều này đáp ứng yêu cầu **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Hình chữ nhật kế thừa ngữ cảnh định dạng của nhóm, vì vậy nó xuất hiện bên trong `GroupShape`. Bạn cũng có thể đặt màu đường viền, màu nền hoặc văn bản sau này nếu cần.

## Chèn nhiều hình dạng

Để minh họa khả năng **insert multiple shapes**, chúng ta thêm một hình ellipse ngay sau hình chữ nhật. Bạn có thể tiếp tục thêm bất kỳ số lượng hình dạng nào (ví dụ: tam giác, ngôi sao) trước khi đóng nhóm.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Tại thời điểm này, nhóm chứa hai hình dạng riêng biệt: một hình chữ nhật và một hình ellipse. Vì chúng cùng chia sẻ cùng một cha, bạn có thể di chuyển chúng như một đơn vị.

## Bước 3: Gắn GroupShape vào cấu trúc đoạn văn

Các tài liệu Word lưu trữ nội dung trong cây đoạn văn. Để nhóm hiển thị trong tệp cuối cùng, chúng ta phải gắn nó vào đoạn văn hiện tại.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*​Tại sao bước này cần thiết:* Nếu không thêm nhóm vào một đoạn văn, các hình dạng chỉ tồn tại trong bộ nhớ và sẽ bị bỏ qua khi tài liệu được lưu.

## Bước 4: Lưu tài liệu – ghi các hình dạng vào Word

Cuối cùng, chúng ta ghi `Document` đang ở trong bộ nhớ ra đĩa. Điều này hoàn thành mục tiêu **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Khi bạn mở `GroupShape.docx` trong Microsoft Word, bạn sẽ thấy một hình chữ nhật và một hình ellipse được nhóm lại, chính xác như mã đã chèn.

### Kết quả mong đợi

- Một tệp có tên **GroupShape.docx** nằm trong thư mục đầu ra của dự án.  
- Trong tệp Word: một đoạn văn duy nhất chứa một hình chữ nhật được nhóm (100 pt × 50 pt) và một hình ellipse (80 pt × 40 pt). Khi chọn bất kỳ hình nào, cả nhóm sẽ được chọn.

## Xử lý các trường hợp góc phổ biến

| Situation | Recommendation |
|-----------|----------------|
| **DPI hoặc kích thước trang khác nhau** | Đặt rõ `builder.PageSetup.PaperSize` trước khi chèn các hình dạng để tránh việc co giãn không mong muốn. |
| **Cần định vị các hình dạng một cách chính xác** | Sử dụng `builder.MoveTo` để di chuyển vị trí chèn, sau đó đặt các thuộc tính `groupShape.Left` và `groupShape.Top` (giá trị tính bằng điểm). |

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word – Chèn hình chữ nhật & bóng trong C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Tạo tài liệu word bằng chương trình và nhóm các hình dạng trong C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Tạo tài liệu Word bằng chương trình với một group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}