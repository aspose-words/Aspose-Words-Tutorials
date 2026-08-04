---
category: general
date: 2026-08-04
description: Thay đổi dấu phân cách chú thích trong C# bằng Aspose.Words – tìm hiểu
  cách chỉnh sửa dấu phân cách chú thích và thay đổi dấu phân cách chú giải trong
  tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: vi
lastmod: 2026-08-04
og_description: Thay đổi dấu phân cách chú thích trong C# với Aspose.Words. Hướng
  dẫn này chỉ cho bạn cách chỉnh sửa dấu phân cách chú thích, tùy chỉnh dấu phân cách
  chú giải cuối, và lưu tài liệu đã cập nhật.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Thay đổi dấu phân cách chú thích trong C# – hướng dẫn đầy đủ Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Thay đổi dấu phân cách chú thích cuối trang trong C# bằng Aspose.Words
url: /vi/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thay đổi dấu phân cách chú thích trong C# bằng Aspose.Words

Nếu bạn cần **thay đổi dấu phân cách chú thích** trong một tài liệu Word, hướng dẫn này sẽ chỉ cho bạn các bước chính xác với Aspose.Words cho .NET. Cho dù bạn muốn thay thế đường kẻ mặc định bằng một ký hiệu, hoặc áp dụng kiểu khác cho dấu phân cách chú giải cuối, đoạn mã dưới đây bao quát toàn bộ quy trình.

Bạn cũng sẽ học cách **chỉnh sửa dấu phân cách chú thích** và thao tác **thay đổi dấu phân cách chú giải cuối** liên quan, để cùng một tài liệu có thể có phong cách nhất quán cho cả chú thích và chú giải cuối. Không cần công cụ bên ngoài—chỉ vài dòng C#.

## Những gì bạn sẽ đạt được

* Tải một tệp *.docx* hiện có có chứa chú thích và chú giải cuối.  
* Truy cập các nút phân cách cho chú thích, tiếp tục chú thích và chú giải cuối.  
* Thay thế ký tự phân cách (ví dụ, đổi đường kẻ mặc định thành dấu sao).  
* Lưu tài liệu đã chỉnh sửa mà không mất bất kỳ nội dung nào khác.  

Hướng dẫn giả định bạn đã có kiến thức cơ bản về C# và đã cài đặt gói NuGet **Aspose.Words** (phiên bản 24.9 trở lên).  

---

## Yêu cầu trước

| Yêu cầu | Lý do |
|-------------|--------|
| .NET 6.0+ hoặc .NET Framework 4.7.2+ | Runtime cần thiết cho Aspose.Words |
| Thư viện Aspose.Words for .NET | Cung cấp các API `Document` và `FootnoteOptions` |
| Tệp Word đầu vào (`input.docx`) có ít nhất một chú thích hoặc chú giải cuối | Minh họa việc thay đổi dấu phân cách |

Bạn có thể thêm Aspose.Words vào dự án của mình bằng lệnh CLI sau:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Bước 1: Tải tài liệu chứa chú thích

Hoạt động đầu tiên là đọc tệp nguồn vào một đối tượng `Document`. Đối tượng này đại diện cho toàn bộ tệp Word trong bộ nhớ và cho phép bạn truy cập tất cả các nút của nó.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Tại sao điều này quan trọng:** Việc tải tài liệu là điểm khởi đầu cho mọi thao tác. Nếu không tìm thấy tệp, Aspose.Words sẽ ném ra `FileNotFoundException`, vì vậy hãy chắc chắn đường dẫn đúng trước khi tiếp tục.

---

## Bước 2: Truy cập các nút phân cách chú thích và chú giải cuối

`Document.FootnoteOptions` cung cấp ba nút phân cách:

* `Separator` – đường kẻ xuất hiện sau bộ sưu tập chú thích trên trang đầu tiên.  
* `ContinuationSeparator` – đường kẻ được sử dụng khi chú thích tiếp tục sang trang tiếp theo.  
* `EndnoteSeparator` – đường kẻ tách phần văn bản chính khỏi danh sách chú giải cuối.

Bạn lấy các nút này dưới dạng đối tượng `Node` chung, sau đó ép kiểu chúng thành `Run` để sửa đổi văn bản.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Tại sao điều này quan trọng:** Những nút này là nơi duy nhất chứa ký tự phân cách hiển thị. Thay đổi bất kỳ nút nào khác (ví dụ, một đoạn văn thông thường) sẽ không ảnh hưởng đến định dạng chú thích.

---

## Bước 3: Thay đổi ký tự phân cách chú thích

Yêu cầu phổ biến nhất là thay thế đường kẻ mặc định bằng một ký hiệu như dấu sao (`*`). Vì dấu phân cách được lưu dưới dạng `Run`, bạn có thể an toàn sửa đổi thuộc tính `Text` của nó.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Tại sao điều này quan trọng:** Việc chỉnh sửa trực tiếp `Run.Text` cập nhật hình ảnh trực quan trong tài liệu cuối cùng mà không ảnh hưởng đến nội dung chú thích khác. Mẫu này cũng có thể được dùng để áp dụng bất kỳ chuỗi nào, bao gồm cả ký tự Unicode.

---

## Bước 4: Thay đổi phân cách chú giải cuối (tùy chọn)

Nếu bạn cũng cần **thay đổi dấu phân cách chú giải cuối**, quy trình tương tự như thay đổi chú thích. Thay thế văn bản của `endnoteSeparator` bằng ký tự mong muốn.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Tại sao điều này quan trọng:** Chú giải cuối thường được định dạng khác với chú thích. Cung cấp một dấu phân cách riêng giúp bạn duy trì tính nhất quán về mặt hình ảnh theo các hướng dẫn thiết kế của tài liệu.

---

## Bước 5: Lưu tài liệu đã chỉnh sửa

Sau khi thực hiện mọi thay đổi, lưu các thay đổi bằng `Document.Save`. Bạn có thể ghi đè lên tệp gốc hoặc ghi vào vị trí mới.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Tại sao điều này quan trọng:** `Save` ghi đại diện trong bộ nhớ ra đĩa, giữ nguyên tất cả các yếu tố khác (kiểu dáng, hình ảnh, bảng) không thay đổi.

---

## Ví dụ đầy đủ, có thể chạy

Kết hợp tất cả các phần lại, dưới đây là một ứng dụng console tự chứa minh họa toàn bộ quy trình:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Kết quả mong đợi:** Mở *ModifiedSeparators.docx* trong Microsoft Word. Dòng phân cách chú thích ở cuối trang chú thích đầu tiên sẽ trở thành một dấu sao đơn (`*`). Nếu tài liệu có chú giải cuối, dòng tách phần văn bản chính khỏi danh sách chú giải cuối sẽ hiển thị dưới dạng dấu gạch ngang (`-`). Tất cả nội dung khác (văn bản, hình ảnh, bảng) vẫn nguyên vẹn.

---

## Các câu hỏi thường gặp & xử lý trường hợp đặc biệt

| Câu hỏi | Câu trả lời |
|----------|--------|
| **Nếu tài liệu không có chú thích thì sao?** | `FootnoteOptions.Separator` vẫn trả về một nút `Run`, nhưng văn bản của nó có thể rỗng. Mã sẽ kiểm tra kiểu nút một cách an toàn trước khi sửa đổi. |
| **Tôi có thể dùng chuỗi đa ký tự (ví dụ, "***") không?** | Có. Thuộc tính `Run.Text` chấp nhận bất kỳ chuỗi nào, bao gồm cả ký tự Unicode. |
| **Thay đổi dấu phân cách có ảnh hưởng đến đánh số chú thích hiện có không?** | Không. Dấu phân cách độc lập với hệ thống đánh số. |
| **Có cần giải phóng đối tượng `Document` không?** | `Document` thực hiện ngầm `IDisposable` thông qua `Node`. Trong một ứng dụng console ngắn hạn, việc này là tùy chọn, nhưng với dịch vụ chạy lâu, bạn có thể bọc nó trong khối `using`. |
| **Cách hoạt động này khác nhau giữa .NET Core và .NET Framework như thế nào?** | API giống hệt trên mọi runtime; chỉ phiên bản framework mục tiêu cần được hỗ trợ bởi gói Aspose.Words. |

**Mẹo chuyên nghiệp:** Nếu bạn cần áp dụng các dấu phân cách khác nhau cho các phần khác nhau, có thể lặp qua `doc.GetChildNodes(NodeType.Footnote, true)` và điều chỉnh thuộc tính `Separator` của từng chú thích riêng lẻ. Đây là kỹ thuật nâng cao nhưng hữu ích cho tài liệu phức tạp.

---

## Kết luận

Bạn đã biết cách **thay đổi dấu phân cách chú thích** và **thay đổi dấu phân cách chú giải cuối** trong một tệp Word bằng Aspose.Words cho C#. Hướng dẫn đã bao gồm việc tải tài liệu, truy cập các nút phân cách liên quan, sửa đổi văn bản của chúng và lưu kết quả—tất cả trong một chương trình tự chứa duy nhất.

Từ đây, bạn có thể khám phá các chủ đề liên quan như **chỉnh sửa kiểu dấu phân cách chú thích**, tùy chỉnh đánh số chú thích, hoặc áp dụng định dạng có điều kiện dựa trên bố cục trang. Mẫu tương tự (lấy nút, ép kiểu thành `Run`, sửa `Text`) hoạt động cho nhiều kịch bản xử lý Word khác.

Chúc bạn lập trình vui vẻ, và đừng ngại thử nghiệm các ký hiệu khác nhau hoặc thậm chí chèn hình ảnh làm dấu phân cách để tạo ra bố cục tài liệu thực sự độc đáo!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh cùng giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Xử lý từ ngữ với Chú thích và Chú giải cuối](/words/english/net/working-with-footnote-and-endnote/)
- [Lấy dấu phân cách kiểu đoạn trong tài liệu Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Chèn dấu phân cách kiểu trong Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}