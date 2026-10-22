---
category: general
date: 2026-08-10
description: Định dạng dấu phân cách chú thích trong C# bằng Aspose.Words để tùy chỉnh
  các dòng chú thích và chú giải cuối. Học cách định dạng chú thích trong C# trong
  vài phút.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: vi
lastmod: 2026-08-10
og_description: Định dạng dấu phân cách chú thích trong C# bằng Aspose.Words. Thực
  hiện theo hướng dẫn này để tạo kiểu cho dấu phân cách chú thích và chú giải cuối
  trang một cách nhanh chóng và đáng tin cậy.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Định dạng bộ tách chú thích trong C# – hướng dẫn toàn diện Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Định dạng dấu phân cách chú thích trong C# bằng Aspose.Words
url: /vi/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Định dạng dấu tách chú thích trong C# bằng Aspose.Words

Nếu bạn cần **định dạng dấu tách chú thích** trong tài liệu Word, hướng dẫn này sẽ chỉ cho bạn cách thực hiện với Aspose.Words cho .NET. Bạn sẽ thấy một ví dụ đầy đủ, có thể chạy được, thay đổi căn chỉnh và màu sắc của đoạn văn dấu tách, và bạn sẽ học cách áp dụng kỹ thuật tương tự cho dấu tách chú thích cuối.

Hướng dẫn bao gồm mọi bước—từ tải tệp nguồn đến lưu tài liệu đã chỉnh sửa—để bạn có thể sao chép‑dán mã vào dự án của mình mà không cần nghiên cứu thêm.

## Những gì bạn cần

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+)
* Giấy phép Aspose.Words cho .NET hợp lệ (bản dùng thử miễn phí đủ cho việc đánh giá)
* Tệp Word chứa ít nhất một chú thích hoặc chú thích cuối (ví dụ, `Footnotes.docx`)
* Visual Studio 2022 hoặc bất kỳ IDE C# nào bạn ưa thích

Có sẵn những mục này sẽ giúp bạn tập trung vào logic **định dạng chú thích C#** thay vì cấu hình môi trường.

## Bước 1: Tải tài liệu chứa chú thích và chú thích cuối

Hoạt động đầu tiên là tạo một đối tượng `Document` trỏ tới tệp nguồn của bạn. Aspose.Words đọc toàn bộ gói DOCX vào bộ nhớ, cho phép bạn truy cập đầy đủ vào các nút chú thích và chú thích cuối.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Why this matters*: Tải tài liệu là điều kiện tiên quyết cho mọi thao tác. Nếu đường dẫn tệp sai, Aspose.Words sẽ ném ra `FileNotFoundException`, vì vậy hãy kiểm tra đường dẫn trước khi tiếp tục.

## Bước 2: Lấy các nút separator và continuation‑separator

Các dấu tách chú thích và chú thích cuối được lưu dưới dạng các nút đặc biệt trong các collection `Footnotes` và `Endnotes`. Mỗi collection cung cấp các thuộc tính `Separator` và `ContinuationSeparator` trả về một tham chiếu `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Why this matters*: Nút `Separator` đại diện cho đường kẻ tách trực quan giữa văn bản chính và khối chú thích. Khi có tham chiếu, bạn có thể chỉnh sửa định dạng đoạn văn, phông chữ, hoặc thậm chí thay thế toàn bộ nút.

## Bước 3: Thay đổi kiểu hiển thị của dấu tách chú thích

Trong hầu hết các tài liệu Word, dấu tách là một đoạn văn duy nhất chứa dấu gạch ngang hoặc dấu sao. Đoạn mã dưới đây kiểm tra xem separator có phải là `Paragraph` không và, nếu có, căn giữa và đổi màu chữ thành màu xám.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Định dạng continuation separator (tùy chọn)

Dấu tách continuation xuất hiện khi một chú thích kéo dài qua nhiều trang. Bạn có thể định dạng nó tương tự:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Why this matters*: Căn chỉnh dấu tách cải thiện khả năng đọc, và việc đổi màu giúp nó nổi bật so với văn bản đoạn bình thường. Bạn có thể thay `ParagraphAlignment.Center` bằng `Left` hoặc `Right` để phù hợp với quy chuẩn thiết kế tài liệu của mình.

## Bước 4: Lưu tài liệu đã chỉnh sửa

Sau khi áp dụng kiểu mong muốn, ghi tài liệu trở lại đĩa. Bạn có thể ghi đè lên tệp gốc hoặc tạo một phiên bản mới.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Khi bạn mở `Footnotes_Styled.docx` trong Microsoft Word, dấu tách chú thích sẽ hiển thị ở vị trí trung tâm và màu xám, chính xác như mã đã chỉ định.

## Các biến thể nâng cao

### Định dạng dấu tách chú thích cuối

Nếu tài liệu của bạn cũng sử dụng chú thích cuối, bạn có thể áp dụng cùng một logic cho collection `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Sử dụng chuỗi tùy chỉnh cho dấu tách

Đôi khi bạn muốn dấu tách là một chuỗi dấu sao (`***`). Thay thế các run hiện có bằng một run mới:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Xử lý tài liệu không có nút separator

Một trường hợp hiếm gặp là tài liệu không có nút separator (ví dụ, khi tác giả đã xóa nó). Trong trường hợp này `document.Footnotes.Separator` sẽ trả về `null`. Hãy kiểm tra trước:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Những lỗi thường gặp và cách tránh

| Pitfall | Why it happens | Fix |
|---------|----------------|-----|
| **Separator is not a `Paragraph`** | Một số mẫu Word sử dụng `Table` hoặc `Shape` làm dấu tách. | Kiểm tra loại nút bằng `is Paragraph` trước khi ép kiểu. |
| **`Runs` collection is empty** | Dấu tách có thể là một đoạn văn rỗng. | Xác minh `Runs.Count > 0` trước khi truy cập `Runs[0]`. |
| **License not applied** | Không có giấy phép, Aspose.Words chèn watermark và có thể giới hạn việc sử dụng API. | Gọi `License license = new License(); license.SetLicense("Aspose.Words.lic");` ở đầu chương trình. |
| **Saving to a read‑only folder** | Phương thức `Save` ném ra `UnauthorizedAccessException`. | Đảm bảo thư mục đích có quyền ghi. |

Việc giải quyết những vấn đề này từ sớm ngăn ngừa ngoại lệ thời chạy và đảm bảo trải nghiệm **sửa đổi dấu tách chú thích** suôn sẻ.

## Ví dụ hoàn chỉnh, có thể chạy

Dưới đây là một ứng dụng console tự chứa, minh họa mọi bước đã thảo luận ở trên. Sao chép mã vào một dự án console .NET mới, thay đổi đường dẫn tệp, và chạy nó.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Kết quả mong đợi**  

Khi bạn mở `Footnotes_Styled.docx`:

* Dòng dấu tách chú thích được căn giữa dưới văn bản chính.
* Màu của nó hiển thị dưới dạng xám nhạt, giúp nó nổi bật trực quan.
* Nếu tài liệu có chú thích cuối, dấu tách của chúng cũng được căn giữa và tô màu xám (hoặc xám đậm)

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Xử lý Word với Chú thích và Chú thích cuối](/words/english/net/working-with-footnote-and-endnote/)
- [Đặt vị trí Chú thích và Chú thích cuối](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Làm việc với Chú thích và Chú thích cuối](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}