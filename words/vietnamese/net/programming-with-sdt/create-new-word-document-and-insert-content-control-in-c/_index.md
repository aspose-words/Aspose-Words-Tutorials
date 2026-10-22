---
category: general
date: 2026-10-13
description: Tạo tài liệu Word mới bằng C# và chèn một điều khiển nội dung với văn
  bản giữ chỗ. Tìm hiểu cách đặt văn bản giữ chỗ và lưu tài liệu Word một cách hiệu
  quả.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: vi
lastmod: 2026-10-13
og_description: Tạo tài liệu Word mới bằng C# với Aspose.Words, chèn một điều khiển
  nội dung, đặt văn bản chỗ giữ chỗ và lưu tài liệu Word—tất cả trong một hướng dẫn
  duy nhất.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Tạo tài liệu Word mới và chèn điều khiển nội dung trong C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Tạo tài liệu Word mới và chèn điều khiển nội dung trong C#
url: /vi/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo tài liệu Word mới và chèn content control trong C#

Nếu bạn cần **tạo tài liệu Word mới** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words for .NET. Bạn sẽ học cách **chèn content control**, gán **văn bản placeholder**, và cuối cùng **lưu tài liệu Word C#** bằng đoạn mã mà bạn có thể sao chép vào dự án của mình.

Bài học sẽ đi qua từng bước, giải thích lý do mỗi lời gọi API quan trọng, và đề cập đến các biến thể phổ biến như thêm SDT dạng rich‑text hoặc xử lý tài liệu đã tồn tại. Khi hoàn thành, bạn sẽ có một ví dụ đầy đủ, có thể chạy được và có thể tùy chỉnh cho hoá đơn, hợp đồng, hoặc bất kỳ đầu ra Word mẫu nào.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)
* Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
* Một IDE như Visual Studio 2022 hoặc Visual Studio Code

Không cần thư viện bổ sung nào khác.

## Tạo tài liệu Word mới với Aspose.Words

Bước đầu tiên là khởi tạo một đối tượng `Document`. Đối tượng này đại diện cho một tệp Word trống trong bộ nhớ.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` cung cấp một API dạng fluent để chèn các phần tử tại vị trí con trỏ hiện tại. Vì tài liệu đang rỗng, con trỏ bắt đầu ở đầu phần (section) đầu tiên (và duy nhất).

## Chèn content control (StructuredDocumentTag)

Một **content control** trong Word được gọi là Structured Document Tag (SDT). Đoạn mã sau tạo một SDT dạng plain‑text, đặt tiêu đề, và định nghĩa văn bản placeholder sẽ hiển thị khi người dùng mở tệp.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Tại sao điều này quan trọng:**  
* `SdtType.PlainText` giới hạn nội dung thành một dòng văn bản thuần, rất phù hợp cho các trường đơn giản như tên hoặc email.  
* Đặt `PlaceholderName` cung cấp một gợi ý trực quan (`Enter name here`) giúp người dùng cuối biết phải nhập gì.  

Nếu bạn cần một trường phong phú hơn (ví dụ: văn bản đa dòng hoặc bộ chọn ngày), hãy thay `SdtType.PlainText` bằng `SdtType.RichText` hoặc `SdtType.Date`.

## Thêm văn bản bao quanh tùy chọn

Hầu hết các mẫu đều có một nhãn trước content control. Bạn có thể thêm nhãn này bằng cùng một thể hiện `DocumentBuilder`:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Kết quả tệp Word sẽ hiển thị:

```
Customer Name: [Enter name here]
```

## Lưu tài liệu Word kiểu C#

Cuối cùng, ghi tài liệu ra đĩa. Aspose.Words sẽ tự động xác định định dạng dựa trên phần mở rộng tệp.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Khi bạn mở `output.docx` trong Microsoft Word, bạn sẽ thấy văn bản placeholder nằm trong một content control có nền màu xám. Người dùng có thể nhấp vào control và thay thế placeholder bằng giá trị của mình.

## Ví dụ đầy đủ, có thể chạy

Dưới đây là một chương trình console tự chứa, kết hợp mọi thứ lại với nhau. Sao chép mã vào một dự án console mới và chạy nó.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Kết quả mong đợi** (console):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Mở `output.docx` sẽ thấy một dòng duy nhất với nhãn *Customer Name:* theo sau là một content control hiển thị *Enter name here*.

## Các biến thể phổ biến và trường hợp đặc biệt

| Scenario | Code change | Reason |
|----------|-------------|--------|
| **Rich‑text field** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Cho phép nhập đa dòng và định dạng cơ bản. |
| **Read‑only control** | `sdt.LockContentControl = true;` | Ngăn người dùng chỉnh sửa nội dung của control. |
| **Pre‑populate with data** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Chèn giá trị mặc định thay thế placeholder. |
| **Add to an existing document** | Load with `new Document("template.docx")` instead of an empty `Document` | Hỗ trợ kịch bản templating khi control được đặt trong bố cục đã định sẵn. |
| **Multiple controls** | Repeat the creation block with different titles and placeholders | Thích hợp cho các biểu mẫu thu thập nhiều thông tin. |

### Mẹo chuyên nghiệp

Khi tạo tài liệu lớn, hãy tái sử dụng một thể hiện `DocumentBuilder` duy nhất thay vì tạo mới cho mỗi control. Điều này giảm tải bộ nhớ và cải thiện hiệu năng.

## Kiểm tra kết quả

1. Chạy ứng dụng console.  
2. Mở `output.docx` trong Microsoft Word.  
3. Xác nhận rằng văn bản placeholder xuất hiện trong một hộp có nền xám.  
4. Nhấp vào hộp, nhập tên, và lưu tệp. Văn bản đã nhập sẽ thay thế placeholder.

Nếu placeholder không xuất hiện, hãy chắc chắn rằng bạn đang dùng Aspose.Words phiên bản 23.9 trở lên, vì các phiên bản cũ hơn có lỗi với `PlaceholderName` trên SDT dạng plain‑text.

## Kết luận

Bây giờ bạn đã biết cách **tạo tài liệu Word mới**, **chèn content control**, **đặt văn bản placeholder**, và **lưu tài liệu Word C#** bằng Aspose.Words. Ví dụ hoàn chỉnh minh họa mẫu chuẩn, và bảng biến thể cho thấy cách điều chỉnh giải pháp cho các kịch bản phong phú hơn.

Tiếp theo, bạn có thể khám phá:

* **Chèn content control cho ngày** – sử dụng enum `SdtType.Date`.  
* **Điền dữ liệu vào mẫu** – kết hợp `StructuredDocumentTag` với các trường mail‑merge.  
* **Xuất ra PDF** – gọi `doc.Save("output.pdf")` sau khi đã thêm các control.

Hãy tự do thử nghiệm các loại SDT khác nhau, cài đặt khóa, và kiểu dáng để phù hợp với yêu cầu dự án của bạn. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}