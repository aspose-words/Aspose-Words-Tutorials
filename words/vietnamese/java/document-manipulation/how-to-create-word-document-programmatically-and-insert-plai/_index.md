---
category: general
date: 2026-10-10
description: Tạo tài liệu Word bằng lập trình với Aspose.Words và chèn điều khiển
  nội dung văn bản thuần – hướng dẫn chi tiết từng bước cho các nhà phát triển .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- insert plain text content control
language: vi
lastmod: 2026-10-10
og_description: Tạo tài liệu Word một cách lập trình bằng Aspose.Words và thêm một
  điều khiển nội dung văn bản thuần hiển thị văn bản chỗ giữ chỗ, cho phép các trường
  biểu mẫu động trong các tệp .docx.
og_image_alt: Screenshot of a Word document displaying a plain text content control
  placeholder
og_title: Tạo tài liệu Word bằng lập trình và thêm một điều khiển nội dung văn bản
  thuần
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create word document programmatically with Aspose.Words and insert
    plain text content control – a step‑by‑step guide for .NET developers.
  headline: How to create word document programmatically and insert plain text content
    control
  type: TechArticle
tags:
- word
- document automation
- content control
- Aspose.Words
- C#
title: Cách tạo tài liệu Word bằng lập trình và chèn điều khiển nội dung văn bản thuần
url: /vi/java/document-manipulation/how-to-create-word-document-programmatically-and-insert-plai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word bằng chương trình và chèn kiểm soát nội dung văn bản thuần

Nếu bạn cần **tạo tài liệu Word bằng chương trình**, hướng dẫn này sẽ cho bạn biết chính xác cách thực hiện với Aspose.Words for .NET. Chỉ trong vài dòng mã, bạn còn sẽ học cách **chèn kiểm soát nội dung văn bản thuần** (còn gọi là Structured Document Tag) để tài liệu có thể hoạt động như một biểu mẫu có thể điền.

Bạn sẽ đi qua toàn bộ quy trình—từ khởi tạo một đối tượng `Document` mới đến lưu tệp .docx cuối cùng. Không cần công cụ bên ngoài, và ví dụ này hoạt động với .NET 6, .NET 7, hoặc bất kỳ môi trường .NET hiện đại nào.

## Prerequisites

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* Một giấy phép Aspose.Words for .NET hợp lệ (hoặc sử dụng chế độ đánh giá miễn phí).  
* .NET 6+ SDK đã được cài đặt.  
* Một IDE như Visual Studio 2022, Rider, hoặc VS Code.  

Nếu bạn chưa cài đặt gói Aspose.Words NuGet, chạy:

```bash
dotnet add package Aspose.Words
```

## Step 1: Create a Word document programmatically

Bước đầu tiên là khởi tạo một `Document` trống và một `DocumentBuilder`. Builder cung cấp cho bạn một API tiện lợi để thêm nội dung, trang và Structured Document Tags (SDTs).

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;
using Aspose.Words.Markup;

// Create an empty document and a builder attached to it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Tại sao điều này quan trọng** – `Document` đại diện cho toàn bộ tệp .docx trong bộ nhớ. Khi tạo nó bằng chương trình, bạn tránh được chi phí mở một tệp mẫu, điều này hữu ích cho việc tạo báo cáo, hoá đơn, hoặc bất kỳ tài liệu nào được tạo ngay lập tức.

## Step 2: Insert a plain text content control

Bước 2: Chèn kiểm soát nội dung văn bản thuần

Một **kiểm soát nội dung văn bản thuần** (SDT) cho phép người dùng nhập văn bản vào một vùng được định trước. Nó cũng hỗ trợ văn bản placeholder xuất hiện khi kiểm soát trống.

```csharp
// Insert a plain‑text Structured Document Tag (SDT) with an identifier "MyTag"
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Set placeholder text that shows inside the control when it is empty
plainTextTag.PlaceholderName = "Enter name";
```

**Giải thích** – `InsertStructuredDocumentTag` tạo SDT tại vị trí con trỏ hiện tại của `DocumentBuilder`. Giá trị enum `StructuredDocumentTagType.PlainText` chỉ cho Aspose.Words hiển thị một hộp văn bản thuần thay vì combo box hay bộ chọn ngày. Thuộc tính `PlaceholderName` cung cấp một gợi ý trực quan cho người dùng, tương tự như văn bản mờ màu xám mà bạn thấy trong các biểu mẫu Word hiện đại.

### Các biến thể phổ biến

| Biến thể | Cách thực hiện |
|-----------|-------------------|
| **Rich‑text content control** | Sử dụng `StructuredDocumentTagType.RichText` thay vì `PlainText`. |
| **Repeating section** | Sử dụng `StructuredDocumentTagType.Group` và lồng các thẻ khác bên trong. |
| **Custom XML mapping** | Gọi `plainTextTag.SetXmlMapping(xmlPart, xpath, false)` sau khi tạo một `XmlPart`. |

## Step 3: Add additional document content (optional)

Bước 3: Thêm nội dung tài liệu bổ sung (tùy chọn)

Bạn có thể thêm các đoạn văn, bảng hoặc hình ảnh thông thường trước hoặc sau kiểm soát nội dung. Dưới đây là một ví dụ nhanh thêm tiêu đề và một đoạn văn:

```csharp
// Add a heading above the content control
builder.Font.Size = 16;
builder.Font.Bold = true;
builder.Writeln("Employee Information");

// Move the cursor back to the placeholder location (already set by InsertStructuredDocumentTag)
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Writeln(); // Adds a line break after the control
```

**Mẹo** – Con trỏ của builder tự động di chuyển tới cuối SDT đã chèn, vì vậy bất kỳ lệnh `Writeln` nào tiếp theo sẽ xuất hiện sau kiểm soát.

## Step 4: Save the document containing the content control

Bước 4: Lưu tài liệu chứa kiểm soát nội dung

Cuối cùng, ghi tài liệu ra đĩa. Bạn có thể chọn bất kỳ định dạng nào được hỗ trợ (`.docx`, `.pdf`, `.html`, v.v.). Trong hướng dẫn này chúng tôi lưu dưới dạng tệp Word.

```csharp
// Save the document to the specified path
string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Kết quả mong đợi

Khi bạn mở *SdtExample.docx* trong Microsoft Word, bạn sẽ thấy:

1. Một tiêu đề **Employee Information**.  
2. Một kiểm soát nội dung văn bản thuần với placeholder màu xám **Enter name**.  

Nếu bạn nhấp vào bên trong kiểm soát, placeholder sẽ biến mất và bạn có thể nhập bất kỳ văn bản nào. Định danh thẻ của kiểm soát (`MyTag`) sau này có thể được truy cập bằng chương trình để trích xuất dữ liệu hoặc xác thực.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là một ứng dụng console tự chứa, kết hợp tất cả các bước lại với nhau. Sao chép mã vào một dự án console .NET mới và chạy nó.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordContentControlDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create an empty document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text content control (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // 3️⃣ Set placeholder text that appears when the control is empty
            sdt.PlaceholderName = "Enter name";

            // Optional: add a heading above the control
            builder.MoveToDocumentStart(); // Ensure heading appears before the control
            builder.Font.Size = 16;
            builder.Font.Bold = true;
            builder.Writeln("Employee Information");

            // Move back to the end of the control to continue writing
            builder.MoveToDocumentEnd();
            builder.Font.Size = 12;
            builder.Font.Bold = false;
            builder.Writeln(); // Adds a line break after the control

            // 4️⃣ Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "SdtExample.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

Chạy chương trình sẽ in ra đường dẫn đầy đủ của tệp đã tạo. Mở tệp trong Word để xác nhận rằng **kiểm soát nội dung văn bản thuần** xuất hiện cùng placeholder của nó.

## Khắc phục sự cố và các trường hợp đặc biệt

| Vấn đề | Nguyên nhân | Giải pháp |
|-------|-------------|-----------|
| Văn bản placeholder không hiển thị | Kiểm soát đã được điền sẵn văn bản hoặc tài liệu được mở ở chế độ ẩn placeholder. | Đảm bảo SDT trống trước khi lưu, hoặc đặt `sdt.IsShowingPlaceholder = true` (có sẵn trong các phiên bản Aspose.Words mới hơn). |
| Kiểm soát nội dung biến mất sau khi lưu dưới dạng PDF | Xuất PDF không giữ lại các trường biểu mẫu tương tác theo mặc định. | Sử dụng `PdfSaveOptions` với `SaveFormat.Pdf` và đặt `ExportDocumentStructure = true`. |
| Không tìm thấy định danh thẻ khi xử lý sau | Tên thẻ bị viết sai hoặc bị ghi đè. | Xác minh định danh được truyền vào `InsertStructuredDocumentTag` khớp với tên bạn truy vấn sau này (`MyTag`). |

## Các thực tiễn tốt nhất khi tạo tài liệu Word bằng chương trình

* **Tái sử dụng một `DocumentBuilder` duy nhất** cho mỗi tài liệu để tránh việc cấp phát bộ nhớ không cần thiết.  
* **Đặt phông chữ và kiểu trước khi viết văn bản**; thay đổi chúng sau khi đã thêm nội dung có thể gây ra định dạng không đồng nhất.  
* **Giải phóng các đối tượng lớn** (ví dụ, `MemoryStream` nếu bạn stream tài liệu) bằng câu lệnh `using`.  
* **Xác thực tài liệu** bằng `doc.UpdateFields()` và `doc.UpdatePageLayout()` trước khi lưu, đặc biệt khi bạn thêm bảng hoặc hình ảnh.  

## Kết luận

Bạn giờ đã biết cách **tạo tài liệu Word bằng chương trình** và **chèn kiểm soát nội dung văn bản thuần** bằng Aspose.Words for .NET. Ví dụ đầy đủ minh họa việc khởi tạo tài liệu, chèn SDT với văn bản placeholder, nội dung bổ sung tùy chọn, và lưu thành tệp .docx.

Từ đây bạn có thể:

* Thay thế kiểm soát văn bản thuần bằng các kiểm soát **rich‑text** hoặc **date picker**.  
* Điền dữ liệu vào tài liệu từ cơ sở dữ liệu và sau đó trích xuất các giá trị đã nhập bằng `StructuredDocumentTag.GetText()`.  
* Xuất cùng một tài liệu sang PDF, HTML, hoặc định dạng OpenXML trong khi vẫn giữ các trường biểu mẫu.

Hãy thử nghiệm với các loại thẻ khác nhau và khám phá API Aspose.Words để xây dựng các mẫu Word tinh vi, có thể điền dữ liệu, tích hợp liền mạch vào các ứng dụng .NET của bạn. Chúc lập trình vui!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Thêm trường biểu mẫu Combo Box vào tài liệu Word với Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Chèn trường biểu mẫu nhập văn bản vào tài liệu Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Thêm trường biểu mẫu Check Box vào tài liệu Word với Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}