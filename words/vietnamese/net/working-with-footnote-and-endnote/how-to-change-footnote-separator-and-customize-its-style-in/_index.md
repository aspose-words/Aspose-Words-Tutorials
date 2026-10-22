---
category: general
date: 2026-10-13
description: Cách thay đổi bộ tách chú thích trong tài liệu Word bằng Aspose.Words.
  Tìm hiểu cách thay đổi màu phông chữ trong tài liệu Word một cách lập trình.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: vi
lastmod: 2026-10-13
og_description: Cách thay đổi dấu phân cách chú thích trong tài liệu Word bằng Aspose.Words.
  Hướng dẫn này chỉ cho bạn cách thay đổi màu phông chữ trong tài liệu Word bằng C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Cách thay đổi dấu phân cách chú thích cuối trang trong tài liệu Word – hướng
  dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Cách thay đổi dấu phân cách chú thích cuối trang và tùy chỉnh kiểu dáng của
  nó trong tài liệu Word
url: /vi/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách thay đổi dấu phân cách chú thích cuối trang và tùy chỉnh kiểu dáng trong tài liệu Word

Nếu bạn cần **cách thay đổi dấu phân cách chú thích cuối trang** trong một tài liệu Word, hướng dẫn này cung cấp giải pháp hoàn chỉnh, sẵn sàng chạy. Sử dụng Aspose.Words for .NET, bạn cũng có thể **thay đổi màu phông chữ trong tài liệu Word** cho các thành phần như dấu phân cách chú thích cuối trang và chú thích cuối tài liệu, giúp tệp cuối cùng phù hợp với thương hiệu hoặc hướng dẫn phong cách của bạn.

Các tác giả tài liệu thường hỏi: *Tại sao dấu phân cách chú thích mặc định trông đơn giản, và làm sao để làm nó nổi bật hơn?* Câu trả lời là truy cập trực tiếp vào các đối tượng đoạn văn phân cách, điều chỉnh thuộc tính phông chữ, và lưu kết quả. Bài hướng dẫn này sẽ dẫn bạn qua từng bước, từ việc tải tệp .docx đến việc lưu file đã được định dạng.

Bạn sẽ học cách:

* Tải một tệp Word đã chứa chú thích cuối trang và chú thích cuối tài liệu.  
* Xác định các đoạn văn phân cách chú thích và chú thích cuối.  
* Thay đổi màu phông chữ của mỗi phân cách (đỏ cho chú thích cuối trang, xanh dương cho chú thích cuối).  
* Lưu tài liệu đã chỉnh sửa mà không mất bất kỳ nội dung nào hiện có.

Không cần công cụ bên ngoài nào ngoài thư viện Aspose.Words và môi trường phát triển .NET.

## Yêu cầu trước

* .NET 6.0 SDK hoặc phiên bản mới hơn (mã cũng hoạt động với .NET Framework 4.7+).  
* Visual Studio 2022, Rider, hoặc bất kỳ trình chỉnh sửa C# nào bạn thích.  
* Gói NuGet Aspose.Words for .NET (`Aspose.Words`).  
* Một tệp Word mẫu (`Footnotes.docx`) chứa ít nhất một chú thích cuối trang và một chú thích cuối.

> **Mẹo chuyên nghiệp:** Nếu bạn chưa có tệp mẫu, tạo một tài liệu Word mới, chèn một chú thích cuối trang (`References → Insert Footnote`) và một chú thích cuối (`References → Insert Endnote`). Lưu nó dưới tên `Footnotes.docx` trong một thư mục bạn có thể tham chiếu từ mã.

## Cách thay đổi dấu phân cách chú thích cuối trang với Aspose.Words

Cốt lõi của nhiệm vụ là truy xuất các đoạn văn đặc biệt mà Aspose.Words cung cấp dưới dạng nút *separator*. Những nút này có kiểu `Paragraph` và có thể được định dạng giống như bất kỳ đoạn văn nào khác.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Tại sao mỗi dòng lại quan trọng

* **Tải tài liệu** (`new Document`) cung cấp cho bạn một đại diện trong bộ nhớ mà Aspose.Words có thể thao tác.  
* **`GetChild` với `ParagraphNodeType.FootnoteSeparator`** trả về đoạn văn ẩn mà Word dùng để vẽ đường phân cách chú thích cuối trang với nội dung chính. Phương pháp tương tự cũng hoạt động cho dấu phân cách chú thích cuối.  
* **Thay đổi `Font.Color`** ảnh hưởng trực tiếp đến giao diện của đường vì Word render phân cách dưới dạng một đoạn văn chứa một ký tự “‑”. Đặt màu thành `Color.Red` (hoặc bất kỳ `System.Drawing.Color` nào) sẽ cập nhật kiểu hiển thị.  
* **Lưu** ghi lại các thay đổi vào tệp .docx mà bất kỳ trình xử lý Word nào cũng mở được.

### Kết quả mong đợi

Khi bạn mở `FootnoteSeparatorsStyled.docx` trong Microsoft Word:

* Đường phân cách chú thích cuối trang hiển thị **đỏ**.  
* Đường phân cách chú thích cuối hiển thị **xanh dương**.  

Tất cả nội dung chú thích và chú thích cuối gốc vẫn nguyên vẹn.

## Thay đổi màu phông chữ trong tài liệu Word bằng C#

Hoạt động được minh họa ở trên là một trường hợp cụ thể của khả năng rộng hơn: **thay đổi màu phông chữ trong tài liệu Word** một cách lập trình. Khi bạn có một `Paragraph`, `Run`, hoặc bất kỳ `Node` nào chứa văn bản, bạn có thể điều chỉnh thuộc tính `Font.Color` của nó.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Đoạn mã này duyệt qua mọi đoạn văn, kiểm tra xem nó có sử dụng kiểu `Heading 1` không, và đặt màu phông chữ cho nó.  
* Bạn có thể điều chỉnh điều kiện để nhắm mục tiêu các chú thích, bảng, hoặc bất kỳ loại nút nào khác.

## Phân tích chi tiết từng bước

### 1. Cài đặt Aspose.Words

Mở terminal trong thư mục dự án và chạy:

```bash
dotnet add package Aspose.Words
```

Gói này bao gồm tất cả các assembly cần thiết cho mã đã trình bày ở trên.

### 2. Chuẩn bị tệp đầu vào

Đặt `Footnotes.docx` vào một thư mục đã biết (ví dụ, `C:\Docs`). Đảm bảo tệp chứa ít nhất một chú thích cuối trang và một chú thích cuối để các nút phân cách tồn tại.

### 3. Viết chương trình C#

Tạo một dự án console mới (`dotnet new console -n FootnoteStyler`) và thay thế `Program.cs` được tạo tự động bằng khối mã đầy đủ từ phần **Cách thay đổi dấu phân cách chú thích cuối trang**. Nhớ điều chỉnh các đường dẫn tệp cho phù hợp với môi trường của bạn.

### 4. Chạy và kiểm tra

Thực thi chương trình:

```bash
dotnet run
```

Sau khi chạy xong, mở `FootnoteSeparatorsStyled.docx`. Bạn sẽ thấy các đường phân cách màu đỏ và xanh dương như mô tả.

### 5. Mở rộng giải pháp

* **Màu khác:** Sử dụng bất kỳ giá trị `System.Drawing.Color` nào, ví dụ `Color.FromArgb(255, 128, 0)` cho màu cam.  
* **Kiểu đường tùy chỉnh:** Thay vì chỉ thay đổi màu, bạn có thể sửa các thuộc tính `ParagraphFormat` như `LineSpacing`, `Shading`, hoặc thậm chí thay thế ký tự phân cách.  
* **Nhiều tài liệu:** Đóng gói logic vào một phương thức nhận đường dẫn đầu vào và đầu ra, sau đó gọi trong vòng lặp để xử lý hàng loạt.

## Những lỗi thường gặp và cách tránh

| Triệu chứng | Nguyên nhân | Cách khắc phục |
|------------|-------------|----------------|
| `GetChild` trả về `null` | Tài liệu nguồn không có dấu phân cách chú thích/đầu cuối (ví dụ, không có chú thích). | Thêm ít nhất một chú thích hoặc chú thích cuối, hoặc kiểm tra `null` trước khi truy cập `Font`. |
| Thay đổi màu không hiển thị | Dấu phân cách được render dưới dạng đường thay vì ký tự trong một số phiên bản Word. | Đặt `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` và `ParagraphFormat.LineSpacing = 1` để buộc hiển thị ký tự. |
| Ngoại lệ runtime `FileNotFoundException` | Đường dẫn tệp không đúng. | Sử dụng đường dẫn tuyệt đối hoặc `Path.Combine` với `Environment.CurrentDirectory`. |

## Ví dụ đầy đủ, có thể chạy được

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm xử lý lỗi và các chú thích giải thích từng thao tác.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Chạy chương trình này sẽ tạo ra một tệp Word trong đó đường phân cách chú thích cuối trang màu đỏ và đường phân cách chú thích cuối màu xanh dương, đáp ứng yêu cầu **cách thay đổi dấu phân cách chú thích cuối trang** đồng thời minh họa **thay đổi màu phông chữ trong tài liệu Word**.

## Kết luận

Bạn đã biết **cách thay đổi dấu phân cách chú thích cuối trang** trong tài liệu Word bằng Aspose.Words for .NET và cách **thay đổi màu phông chữ trong tài liệu Word** một cách lập trình. Quy trình gồm:

1. Tải tài liệu.  
2. Lấy các đoạn văn phân cách ẩn.  
3. Đặt thuộc tính `Font.Color` cho chúng.  
4. Lưu tệp đã chỉnh sửa.

Từ đây, bạn có thể khám phá các kiểu dáng nâng cao hơn—điều chỉnh độ dày đường, áp dụng phông chữ khác, hoặc tự động hoá quy trình cho nhiều tệp. Thành thạo những kỹ thuật này sẽ cho bạn khả năng kiểm soát chi tiết giao diện tài liệu Word trực tiếp từ mã C#.

---


## Bạn nên học gì tiếp theo?


Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}