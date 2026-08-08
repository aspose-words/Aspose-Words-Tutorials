---
category: general
date: 2026-08-07
description: Lấy dấu phân cách chú thích dưới chân bằng Aspose.Words cho .NET. Tìm
  hiểu cách trích xuất dấu phân cách chú thích dưới chân và chú thích cuối, kiểm tra
  loại nút, và sửa đổi chúng trong C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: vi
lastmod: 2026-08-07
og_description: Khôi phục dấu tách chú thích dưới trang với Aspose.Words cho .NET.
  Hướng dẫn này cho thấy cách trích xuất dấu tách chú thích dưới trang và chú thích
  cuối trang, kiểm tra loại nút của chúng và lưu các thay đổi.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: Lấy dấu phân cách chú thích trong C# – hướng dẫn chi tiết Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Lấy dấu phân cách chú thích trong C# – hướng dẫn đầy đủ Aspose.Words
url: /vi/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# truy xuất dấu tách chú thích trong C# – hướng dẫn đầy đủ Aspose.Words

Nếu bạn cần **retrieve footnote separator** từ một tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện chính xác bằng Aspose.Words cho .NET. Dù bạn đang xây dựng dịch vụ xử lý tài liệu hay làm sạch định dạng chú thích, bạn sẽ thấy một ví dụ đầy đủ, có thể chạy được, trích xuất cả dấu tách chú thích và dấu tách chú giải cuối.

Trong hướng dẫn này, bạn sẽ học cách tải tệp `.docx`, gọi các thuộc tính `FootnoteSeparator` và `EndnoteSeparator`, kiểm tra các đối tượng `Node` trả về, và tùy chọn thay thế dòng dấu tách. Không cần tài liệu bên ngoài—mọi thứ bạn cần đã được bao gồm dưới đây.

## Yêu cầu trước

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động trên .NET Framework 4.7.2)
* Gói NuGet Aspose.Words cho .NET (phiên bản 24.9 hoặc mới hơn)
* Một tài liệu Word chứa chú thích và/hoặc chú giải cuối (ví dụ: `Footnotes.docx`)

Bạn có thể thêm gói Aspose.Words bằng lệnh CLI sau:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Bước 1: Thiết lập dự án và nhập các namespace

Tạo một dự án console mới hoặc thêm mã vào dự án hiện có. Các chỉ thị `using` cần thiết được liệt kê bên dưới.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Các namespace này cung cấp quyền truy cập vào lớp `Document`, cấu trúc `Node`, và enum `NodeType` cần thiết cho các thao tác **retrieve footnote separator**.

## Bước 2: Tải tài liệu chứa chú thích và chú giải cuối

Hoạt động đầu tiên trong bất kỳ quy trình làm việc nào của Aspose.Words là tải tệp nguồn. Thay thế đường dẫn placeholder bằng vị trí thực tế của tệp `.docx` của bạn.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Việc tải tệp chuẩn bị cây node nội bộ, điều này rất quan trọng cho **retrieve footnote separator** vì các node dấu tách nằm trong cây đó.

## Bước 3: Truy xuất nút dấu tách chú thích

Bây giờ bạn có thể **retrieve footnote separator** bằng cách truy cập thuộc tính `FootnoteSeparator` của đối tượng `Document`. Node này đại diện cho dòng phân cách giữa các chú thích và nội dung chính.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

`NodeType` sẽ là `Paragraph` đối với một dòng dấu tách tiêu chuẩn. Biết loại node giúp bạn quyết định có cần chỉnh sửa dấu tách hay thay thế hoàn toàn hay không.

## Bước 4: Truy xuất nút dấu tách chú giải cuối

Tương tự, bạn có thể **retrieve endnote separator** bằng thuộc tính `EndnoteSeparator`. Node này phân cách các chú giải cuối khỏi nội dung chính.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Cả hai node dấu tách đều có cùng `NodeType` (`Paragraph`) trong hầu hết các tài liệu, nhưng chúng có thể được tùy chỉnh độc lập.

## Bước 5: Kiểm tra hoặc chỉnh sửa nội dung dấu tách (tùy chọn)

Nếu bạn cần thay đổi giao diện trực quan của dấu tách—ví dụ thay một dòng gạch ngang bằng một đường mảnh—bạn có thể chỉnh sửa trực tiếp node `Paragraph`. Dưới đây là ví dụ thay thế văn bản dấu tách mặc định bằng một chuỗi tùy chỉnh.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Sau khi chỉnh sửa các node, bạn có thể lưu tài liệu để thấy các thay đổi được phản ánh trong Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Đầu ra console dự kiến

Khi bạn chạy chương trình với tệp `Footnotes.docx` gốc, bạn sẽ thấy kết quả tương tự như sau:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Nếu bạn mở `Footnotes_Updated.docx` trong Microsoft Word, các dấu tách chú thích và chú giải cuối sẽ hiển thị văn bản tùy chỉnh mà bạn đã chèn.

## Các câu hỏi thường gặp và trường hợp đặc biệt

**What if the document has no footnotes?**  
Thuộc tính `FootnoteSeparator` vẫn trả về một node `Paragraph` vì Word luôn bao gồm một placeholder cho dấu tách. Node sẽ rỗng, vì vậy bạn có thể an toàn thêm nội dung hoặc để nguyên.

**Can I retrieve the separator for a specific section?**  
Dấu tách chú thích và chú giải cuối áp dụng cho toàn bộ tài liệu, không riêng cho từng phần. Nếu bạn cần kiểm soát ở mức phần, phải làm việc với `Section.FootnoteOptions` và `Section.EndnoteOptions` thay vì các node dấu tách toàn cục.

**Does this work with .NET Core?**  
Có. Aspose.Words cho .NET là đa nền tảng, và cùng một đoạn mã chạy trên Windows, Linux và macOS với .NET 6+.

**What node type should I expect?**  
Cả `FootnoteSeparator` và `EndnoteSeparator` đều trả về một node `Paragraph` (`NodeType.Paragraph`). Nếu bạn gặp loại khác, tài liệu có thể bị hỏng và bạn nên tải lại hoặc xác thực tệp nguồn.

## Mã nguồn đầy đủ để sao chép nhanh

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Sao chép mã vào tệp `Program.cs`, điều chỉnh đường dẫn tệp, và chạy `dotnet run`. Chương trình minh họa quy trình **retrieve footnote separator** hoàn chỉnh, từ tải tài liệu đến lưu các thay đổi.

## Kết luận

Bạn đã biết cách **retrieve footnote separator** và **endnote separator retrieval** bằng Aspose.Words cho .NET, kiểm tra `document node type` của chúng, và tùy chọn thay thế nội dung. Kỹ thuật này cho phép bạn tự động hoá định dạng chú thích, tạo các dòng dấu tách tùy chỉnh, hoặc xác thực cấu trúc tài liệu trong bất kỳ ứng dụng C# nào.

Tiếp theo, bạn có thể khám phá các chủ đề liên quan như **C# footnote extraction** để lấy nội dung từng chú thích, hoặc học cách **modify footnote reference marks** bằng `FootnoteOptions`. Cả hai khái niệm đều dựa trực tiếp trên các nguyên tắc cây node được trình bày ở đây.

Chúc bạn lập trình vui vẻ, và hãy tự do thử nghiệm các kiểu dấu tách khác nhau để phù hợp với thương hiệu dự án của bạn!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm mã nguồn làm việc đầy đủ với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Xử lý Văn bản với Chú thích và Chú giải cuối](/words/english/net/working-with-footnote-and-endnote/)
- [Thêm Nội dung bằng Document Builder trong Aspose.Words cho .NET](/words/english/net/add-content-using-document-builder/)
- [Làm việc với Chú thích và Chú giải cuối](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}