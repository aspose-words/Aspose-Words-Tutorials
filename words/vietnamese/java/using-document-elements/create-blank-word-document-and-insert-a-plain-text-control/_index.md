---
category: general
date: 2026-09-18
description: Tạo tài liệu Word trống bằng C# và đặt văn bản giữ chỗ, sau đó lưu tài
  liệu dưới dạng docx. Học cách chèn điều khiển văn bản thuần và thêm tên giữ chỗ.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: vi
lastmod: 2026-09-18
og_description: Tạo tài liệu Word trống bằng C#. Đặt văn bản giữ chỗ, chèn điều khiển
  văn bản thuần, thêm tên giữ chỗ và lưu tài liệu dưới dạng docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Tạo tài liệu Word trống với văn bản giữ chỗ – Hướng dẫn C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Tạo tài liệu Word trống và chèn một điều khiển văn bản thuần
url: /vi/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word trống và chèn điều khiển văn bản thuần

Nếu bạn cần **create blank Word document** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện bằng C#. Bạn sẽ học cách **insert plain text control**, **set placeholder text**, **add placeholder name**, và cuối cùng **save document as docx**. Các bước đều tự chứa, vì vậy bạn có thể sao chép mã vào bất kỳ dự án .NET nào và chạy ngay lập tức.

Làm việc với các tệp Word thường đòi hỏi một điểm khởi đầu sạch sẽ — một tài liệu trống đã chứa sẵn các điều khiển mà người dùng sẽ điền. Khi kết thúc hướng dẫn này, bạn sẽ có một tệp `.docx` chứa một điều khiển nội dung văn bản thuần với một placeholder hữu ích, tiếp theo là nội dung thường.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
- Tham chiếu tới thư viện **Aspose.Words for .NET** (có sẵn qua NuGet `Install-Package Aspose.Words`)
- Kiến thức cơ bản về các ứng dụng console C#
- Quyền ghi vào thư mục đầu ra bạn chỉ định trong `doc.save(...)`

## Bạn sẽ xây dựng gì

Tài liệu cuối cùng (`SDT.docx`) chứa:

1. Một tệp Word trống (the **blank Word document** bạn đã tạo)
2. Một điều khiển nội dung văn bản thuần (the **insert plain text control** step)
3. Văn bản placeholder xuất hiện bên trong điều khiển cho đến khi người dùng gõ gì đó (the **set placeholder text** step)
4. Một tên placeholder có thể được sử dụng để truy cập chương trình sau này (the **add placeholder name** step)
5. Một dòng văn bản thường sau điều khiển, chứng minh rằng nội dung bình thường có thể theo sau

## Bước 1: Tạo tài liệu Word trống

Hoạt động đầu tiên là khởi tạo một đối tượng `Document` rỗng. Đối tượng này đại diện cho một **blank Word document** hoàn toàn mới trong bộ nhớ.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Why this matters:* An empty `Document` gives you full control over every element you add, ensuring no hidden styles or sections interfere with the content control you will insert later.

* Tại sao điều này quan trọng:* Một `Document` rỗng cho phép bạn kiểm soát hoàn toàn mọi thành phần bạn thêm vào, đảm bảo không có kiểu hoặc phần ẩn can thiệp vào điều khiển nội dung mà bạn sẽ chèn sau này.

## Bước 2: Khởi tạo DocumentBuilder

`DocumentBuilder` là lớp trợ giúp cho phép bạn ghi vào `Document`. Nó theo dõi vị trí con trỏ hiện tại và cung cấp các phương thức để chèn mọi loại đối tượng Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Why this matters:* Using a `DocumentBuilder` simplifies the process of adding a **plain‑text control** because the builder knows the exact insertion point.

* Tại sao điều này quan trọng:* Sử dụng `DocumentBuilder` đơn giản hoá quá trình thêm **plain‑text control** vì builder biết chính xác vị trí chèn.

## Bước 3: Chèn điều khiển văn bản thuần

Bây giờ chúng ta thêm một **plain‑text content control** (còn gọi là Structured Document Tag, hoặc SDT). Kiểu điều khiển `StructuredDocumentTagType.PLAIN_TEXT` báo cho Word xử lý nội dung như văn bản thuần, không phải định dạng phong phú.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Why this matters:* The `InsertStructuredDocumentTag` method creates the control and returns a reference (`sdt`) that you can further configure, such as adding placeholder text or a custom name.

* Tại sao điều này quan trọng:* Phương thức `InsertStructuredDocumentTag` tạo ra điều khiển và trả về một tham chiếu (`sdt`) mà bạn có thể cấu hình thêm, như thêm văn bản placeholder hoặc tên tùy chỉnh.

## Bước 4: Đặt văn bản placeholder và thêm tên placeholder

Văn bản placeholder cung cấp cho người dùng một gợi ý trực quan về những gì cần gõ. Bước **add placeholder name** gán một định danh chương trình mà bạn có thể truy vấn sau này bằng `doc.GetChildNodes` hoặc các API tương tự.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Why this matters:* `SetPlaceholderName` controls the gray hint text shown inside the content control. Setting `Tag` (the **add placeholder name** action) lets you locate the control in the document tree without scanning the whole file.

* Tại sao điều này quan trọng:* `SetPlaceholderName` kiểm soát văn bản gợi ý màu xám hiển thị bên trong điều khiển nội dung. Đặt `Tag` (hành động **add placeholder name**) cho phép bạn tìm vị trí điều khiển trong cây tài liệu mà không cần quét toàn bộ tệp.

## Bước 5: Thêm nội dung thường sau điều khiển

Để chứng minh tài liệu tiếp tục bình thường sau điều khiển, chúng ta ghi một dòng văn bản đơn giản.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Bước 6: Lưu tài liệu dưới dạng docx

Cuối cùng, chúng ta ghi tài liệu trong bộ nhớ ra đĩa. Đây là thao tác **save document as docx** tạo ra tệp bạn có thể mở trong Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Why this matters:* Using the `.docx` format ensures maximum compatibility with modern versions of Word, Google Docs, and other Office‑compatible tools.

* Tại sao điều này quan trọng:* Sử dụng định dạng `.docx` đảm bảo khả năng tương thích tối đa với các phiên bản Word hiện đại, Google Docs và các công cụ tương thích Office khác.

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép vào một dự án console‑app. Thay `YOUR_DIRECTORY` bằng đường dẫn thư mục thực tế trên máy của bạn.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Kết quả mong đợi

- Mở `SDT.docx` trong Word sẽ hiển thị một hộp xám trống với văn bản **Enter text…** bên trong.
- Hộp này là một **plain‑text content control**; bạn có thể gõ trực tiếp vào đó.
- Dưới hộp, dòng **After the tag.** xuất hiện như văn bản đoạn bình thường.

Nếu placeholder không hiển thị, hãy kiểm tra rằng bạn đang sử dụng phiên bản mới của Aspose.Words (v23.1 trở lên) và tài liệu được mở trong phiên bản Word hỗ trợ điều khiển nội dung (Word 2007+).

## Các biến thể phổ biến và trường hợp đặc biệt

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Multiple placeholders** | Call `InsertStructuredDocumentTag` again with a different tag ID and placeholder name. |
| **Rich‑text control** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Setting default text** | After insertion, assign `sdt.Text = "Default value";` – this text replaces the placeholder when the document loads. |
| **Saving to a stream** | Replace `doc.Save(outputPath);` with `doc.Save(stream, SaveFormat.Docx);` to send the file over HTTP. |
| **Changing placeholder color** | Use `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (requires `using System.Drawing`). |

## Pro tips

- **Reuse the tag ID**: Keeping the tag (`MyTag`) consistent across documents lets you automate data population later with `doc.Range.Replace` or the `StructuredDocumentTagCollection`.
- **Avoid hard‑coded paths**: Use `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` for a portable output location.
- **Performance**: If you need to generate thousands of documents, create a single `Document` template with the SDT already present, then clone it with `doc.Clone()` for each iteration.

## Kết luận

Bạn giờ đã biết cách **create blank Word document**, **insert plain text control**, **set placeholder text**, **add placeholder name**, và **save document as docx** bằng Aspose.Words cho .NET. Mô hình này là nền tảng để xây dựng các mẫu Word có biểu mẫu, báo cáo tự động, hoặc bất kỳ giải pháp nào yêu cầu placeholder có thể chỉnh sửa bởi người dùng.

Hãy tự do thử nghiệm các loại điều khiển khác, kết hợp nhiều placeholder, hoặc tích hợp mã này vào một API web trả về tệp `.docx` được tạo trực tiếp cho người gọi. Đối với bước tiếp theo, khám phá **populate a content control with data programmatically** hoặc **convert the generated Word file to PDF** bằng các tính năng chuyển đổi tích hợp của Aspose.Words. Chúc bạn lập trình vui!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Chèn trường biểu mẫu nhập văn bản trong tài liệu Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Tạo tài liệu Word với bảng bằng Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Tạo tài liệu Word với Header và Footer bằng Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}