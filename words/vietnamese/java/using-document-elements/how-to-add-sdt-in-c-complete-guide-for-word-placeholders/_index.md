---
category: general
date: 2026-08-14
description: Cách thêm SDT nhanh chóng với Aspose.Words. Tìm hiểu cách tạo trình giữ
  chỗ Word và chèn điều khiển văn bản thuần trong tệp .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: vi
lastmod: 2026-08-14
og_description: Cách thêm SDT trong C# bằng Aspose.Words. Theo dõi hướng dẫn này để
  tạo trình giữ chỗ Word và chèn điều khiển văn bản thuần cho tài liệu động.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Cách thêm SDT trong C# – hướng dẫn chi tiết từng bước về placeholder trong
  Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Cách thêm SDT trong C# – hướng dẫn chi tiết cho các placeholder trong Word
url: /vi/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thêm SDT trong C# – hướng dẫn đầy đủ cho các placeholder trong Word

Nếu bạn cần **cách thêm sdt** vào một tệp Word, hướng dẫn này sẽ chỉ cho bạn các bước chính xác bằng cách sử dụng Aspose.Words for .NET. Khi kết thúc hướng dẫn, bạn sẽ có thể **tạo thẻ placeholder trong Word** cho phép người dùng cuối nhập trực tiếp vào tài liệu, và bạn sẽ hiểu cách **chèn plain text control** một cách đáng tin cậy.

Làm việc với Structured Document Tags (SDT) loại bỏ nhu cầu tạo các trường biểu mẫu thủ công và cung cấp cho bạn một cách tiếp cận lập trình sạch sẽ để xây dựng các hợp đồng, báo cáo hoặc thư động. Ví dụ dưới đây bao gồm mọi thứ từ thiết lập dự án đến lưu tệp .docx cuối cùng, vì vậy bạn có thể sao chép‑dán mã vào giải pháp của mình mà không bỏ lỡ bất kỳ phụ thuộc nào.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
- Visual Studio 2022 hoặc bất kỳ IDE C# nào bạn thích
- Giấy phép Aspose.Words for .NET (giấy phép tạm thời miễn phí cũng đủ cho việc thử nghiệm)
- Kiến thức cơ bản về cú pháp C# và khái niệm SDT

> **Mẹo chuyên nghiệp:** Nếu bạn dự định phân phối các tài liệu đã tạo, hãy nhúng tệp giấy phép để tránh dấu watermark đánh giá.

## Bước 1: Thiết lập dự án và nhập Aspose.Words

Tạo một ứng dụng console mới và thêm gói NuGet Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Các chỉ thị `using` này cho phép bạn truy cập các lớp `Document`, `DocumentBuilder` và `StructuredDocumentTag` cần thiết cho các thao tác **insert plain text control**.

## Bước 2: Khởi tạo tài liệu và builder

Khối mã đầu tiên tạo một tài liệu Word trống và một `DocumentBuilder` cho phép bạn ghi nội dung vào đó.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` hoạt động như một con trỏ; mỗi lời gọi tiếp theo sẽ thêm nội dung tại vị trí hiện tại. Khởi tạo tài liệu là nền tảng cho mọi kịch bản **cách thêm sdt** vì SDT phải thuộc về một thể hiện `Document` đang hoạt động.

## Bước 3: Chèn Structured Document Tag (SDT) dạng plain‑text

Bây giờ chúng ta **chèn plain text control** hoạt động như một placeholder nơi người dùng có thể nhập tên, ngày tháng hoặc bất kỳ giá trị tùy chỉnh nào.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` báo cho Aspose.Words tạo một trường văn bản đơn giản.
- `SdtAppearanceTags.Default` cung cấp cho thẻ kiểu hiển thị chuẩn của Word (một hộp có nền màu khi tài liệu được mở trong Word).

## Bước 4: Cấu hình SDT với tiêu đề và văn bản placeholder

Một SDT có tên rõ ràng giúp tài liệu tự giải thích cho người dùng cuối. Ở đây chúng ta **tạo word placeholder** và đặt gợi ý hiển thị bên trong trường.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` là định danh nội bộ mà bạn có thể sử dụng sau này khi trích xuất hoặc cập nhật giá trị bằng mã.
- `PlaceholderName` là gợi ý màu xám hiển thị trong Word, cho người dùng biết cần nhập gì.

## Bước 5: Thêm nội dung xung quanh

Một tài liệu hiếm khi chỉ có một SDT duy nhất. Thông thường bạn cần các đoạn văn thông thường trước và sau placeholder. Sử dụng phương thức `WriteLine` của builder để thêm văn bản tĩnh.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Lệnh `InsertNode` đặt SDT đã tạo trước đó chính xác ở vị trí bạn muốn, giữ nguyên luồng văn bản xung quanh.

## Bước 6: Lưu tài liệu thành tệp .docx

Cuối cùng, lưu tài liệu vào đĩa. Đường dẫn có thể là tuyệt đối hoặc tương đối so với thư mục dự án.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Mở `SDT.docx` trong Microsoft Word sẽ hiển thị một placeholder màu xám có nội dung **Enter name here**. Người dùng có thể nhấp vào trường, nhập giá trị, và tài liệu sẽ giữ lại giá trị đó khi lưu lại lần nữa.

## Ví dụ đầy đủ, có thể chạy ngay

Kết hợp tất cả các phần lại sẽ cho bạn một chương trình tự chứa mà bạn có thể chạy ngay:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Kết quả mong đợi** khi chạy chương trình:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Mở `SDT.docx` đã tạo sẽ hiển thị:

```
Dear [Enter name here],
After the SDT
```

Văn bản trong ngoặc là placeholder **insert plain text control** mà người dùng có thể thay thế.

## Các biến thể phổ biến và trường hợp góc cạnh

| Tình huống | Cách điều chỉnh mã |
|-----------|-----------------------|
| **Nhiều placeholder** | Gọi `InsertStructuredDocumentTag` nhiều lần và đặt mỗi thẻ một `Title` duy nhất. |
| **SDT dạng rich‑text** | Sử dụng `StructuredDocumentTagType.RichText` thay vì `PlainText`. |
| **Khóa placeholder** | Đặt `plainTextTag.LockContentControl = true;` để ngăn người dùng xóa trường. |
| **Tiền‑điền giá trị** | Gán `plainTextTag.Text = "John Doe";` trước khi lưu. |
| **Hiển thị có điều kiện** | Sử dụng `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` cho điều khiển dạng hộp kiểm. |

Các biến thể này cho phép bạn **tạo word placeholder** phù hợp với hầu hết các kịch bản dạng biểu mẫu.

## Mẹo khắc phục sự cố

- **Placeholder không hiển thị** – Đảm bảo bạn mở tệp trong Microsoft Word (hoặc trình xem tương thích). Một số trình soạn thảo nhẹ có thể ẩn SDT.
- **Cảnh báo giấy phép** – Nếu bạn thấy watermark đánh giá, hãy kiểm tra xem tệp giấy phép của bạn đã được tải đúng chưa (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Vị trí con trỏ không đúng** – Sau khi chèn SDT, con trỏ của builder vẫn ở *sau* thẻ. Nếu bạn cần thêm văn bản *bên trong* thẻ, hãy dùng `builder.MoveTo(plainTextTag);` trước khi ghi.

## Kết luận

Bây giờ bạn đã biết **cách thêm sdt** vào tài liệu Word bằng Aspose.Words for .NET, cách **tạo word placeholder** và cách **chèn plain text control** cho phép người dùng chỉnh sửa trực tiếp trong Word. Ví dụ đầy đủ minh họa việc khởi tạo, chèn thẻ, cấu hình, thêm nội dung xung quanh và lưu – tất cả trong một chương trình có thể chạy ngay.

Tiếp theo, hãy khám phá các chủ đề liên quan như **insert rich text control**, **populate SDTs from a database**, hoặc **convert the final document to PDF**. Tất cả đều dựa trên những nguyên tắc cơ bản đã được trình bày ở đây, giúp bạn mở rộng quy trình tự động hoá tài liệu một cách tự tin.

Chúc bạn lập trình vui vẻ, và đừng ngại thử nghiệm các loại SDT khác nhau để phù hợp với nhu cầu tự động hoá tài liệu của mình!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Create Editable Ranges in Read-Only Documents Using Aspose.Words for Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Add Bookmarks Word with Aspose.Words for Java – Insert, Update, Delete](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}