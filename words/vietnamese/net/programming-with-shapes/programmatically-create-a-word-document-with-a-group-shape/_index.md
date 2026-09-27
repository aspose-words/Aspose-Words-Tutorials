---
category: general
date: 2026-09-27
description: Tạo tài liệu Word có hình nhóm một cách lập trình bằng Aspose.Words trong
  C#. Hãy làm theo hướng dẫn từng bước này để tạo tệp và học các mẹo hữu ích.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: vi
lastmod: 2026-09-27
og_description: Tạo tài liệu Word có hình nhóm một cách lập trình bằng Aspose.Words.
  Hướng dẫn này sẽ đưa bạn qua toàn bộ mã C#, giải thích từng bước và hiển thị kết
  quả cuối cùng.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Tạo tài liệu Word có nhóm hình dạng bằng lập trình – Hướng dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo tài liệu Word có nhóm hình dạng một cách lập trình
url: /vi/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word bằng lập trình với một hình dạng nhóm

Nếu bạn cần **tạo tài liệu Word bằng lập trình** có chứa một bản vẽ nhóm, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác với Aspose.Words for .NET. Dù bạn đang xây dựng công cụ tạo hợp đồng, công cụ tạo báo cáo, hay công cụ điền biểu mẫu, bạn sẽ học toàn bộ mã C#, lý do mỗi lời gọi API quan trọng, và cách xử lý các trường hợp góc phổ biến.

Việc tạo một hình dạng nhóm trong Word có thể cảm thấy khó khăn vì mô hình đối tượng Word coi các hình dạng nhóm là các container cho các đối tượng vẽ khác. Bài hướng dẫn này không chỉ trả lời **cách tạo group shape word** tài liệu, mà còn minh họa cách nhúng một StructuredDocumentTag (SDT) dạng văn bản thuần bên trong nhóm để hình dạng có thể chứa nội dung có thể chỉnh sửa.

## Những gì bạn sẽ đạt được

- Khởi tạo một tài liệu Word trống mới bằng `Document` và `DocumentBuilder`.
- Chèn một `GroupShape` tại vị trí con trỏ hiện tại.
- Thêm một `StructuredDocumentTag` (SDT) dạng văn bản thuần vào hình dạng nhóm.
- Lưu tệp dưới dạng `.docx` có thể mở trong Microsoft Word.
- Hiểu các thuộc tính chính của `GroupShape` và `StructuredDocumentTag` để mở rộng trong tương lai.

### Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+).
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).
- Một IDE C# như Visual Studio 2022 hoặc VS Code với phần mở rộng C#.

---

## Tạo tài liệu Word bằng lập trình – thiết lập dự án

1. **Tạo một dự án console mới**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Mở dự án trong IDE của bạn** và thay thế nội dung của `Program.cs` bằng mã được hiển thị trong các phần tiếp theo.

> **Mẹo chuyên nghiệp:** Giữ thư mục dự án của bạn sạch sẽ; Aspose.Words ghi tệp đầu ra vào thư mục làm việc trừ khi bạn cung cấp đường dẫn tuyệt đối.

## Bước 1: Khởi tạo tài liệu và builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Tại sao điều này quan trọng:**  
`Document` đại diện cho toàn bộ tệp Word, trong khi `DocumentBuilder` cho phép bạn đặt vị trí các phần tử mới mà không cần điều hướng cây node thủ công. Đặt kích thước trang sớm đảm bảo hình dạng nhóm không tràn ra ngoài trang.

## Bước 2: Chèn một GroupShape tại vị trí con trỏ hiện tại

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Giải thích:**  
`GroupShape` là một đối tượng vẽ có thể chứa các hình dạng, hình ảnh hoặc hộp văn bản khác. Bằng cách đặt `Width`, `Height`, `Left`, và `Top`, bạn kiểm soát vị trí chính xác của nó trên trang. Phương thức `InsertNode` đặt hình dạng vào luồng tài liệu chính, hoạt động như một đối tượng nổi.

## Bước 3: Thêm một StructuredDocumentTag (SDT) dạng văn bản thuần vào bên trong nhóm

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Tại sao lại dùng SDT?**  
StructuredDocumentTag là các điều khiển nội dung gốc của Word. Chúng cho phép người dùng chỉnh sửa văn bản trực tiếp trong tài liệu đã lưu, và có thể được truy cập bằng lập trình sau này để trích xuất dữ liệu. Đặt một SDT bên trong một hình dạng nhóm cho phép bạn kết hợp việc nhóm trực quan với nội dung có thể chỉnh sửa.

## Bước 4: Lưu tài liệu

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Kết quả:**  
Mở `GroupShapeDemo.docx` trong Microsoft Word sẽ hiển thị một hình chữ nhật nổi (hình dạng nhóm) chứa một placeholder văn bản có nội dung “Enter text here”. Người dùng có thể nhấp vào bên trong hình dạng và gõ trực tiếp.

### Ảnh chụp màn hình đầu ra dự kiến (khái niệm)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Hộp bên ngoài là `GroupShape`; vùng xám bên trong là `StructuredDocumentTag`.

---

## Cách tạo group shape word – các cân nhắc bổ sung

### Thêm nhiều hình con hơn

Bạn có thể làm phong phú nhóm bằng cách thêm các đối tượng vẽ bổ sung, chẳng hạn như hình ảnh hoặc hộp văn bản:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Kiểm soát kiểu bao bọc

Nếu bạn cần hình dạng nhóm nằm phía sau văn bản hoặc có bao bọc chặt, hãy đặt thuộc tính `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Trường hợp đặc biệt: Hình dạng nhóm rỗng

`GroupShape` không có con sẽ hiển thị như một placeholder vô hình. Luôn xác minh rằng ít nhất một phần tử con (ví dụ: một SDT hoặc một hình ảnh) đã được thêm; nếu không Word có thể loại bỏ nhóm khi lưu.

### Lưu ý về khả năng tương thích

Aspose.Words 23.10+ hoàn toàn hỗ trợ `GroupShape` và `StructuredDocumentTag`. Nếu bạn nhắm tới các phiên bản cũ hơn, phương thức `AppendChild` có thể hoạt động khác, và bạn có thể cần gọi `UpdatePageLayout` sau khi lưu.

---

## Ví dụ hoàn chỉnh có thể chạy

Sao chép toàn bộ đoạn mã dưới đây vào `Program.cs` và chạy dự án. Mã bao gồm tất cả các bước trên trong một chương trình duy nhất, tự chứa.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoạt động đầy đủ với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}