---
category: general
date: 2026-04-24
description: Lưu tài liệu dưới dạng txt và chuyển đổi Word sang LaTeX với Aspose.Words.
  Tìm hiểu cách xuất các công thức toán học Word sang LaTeX nhanh chóng.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: vi
og_description: Lưu tài liệu dưới dạng txt và chuyển đổi các phương trình Word sang
  LaTeX bằng C#. Hướng dẫn chi tiết từng bước kèm mã nguồn.
og_title: Lưu tài liệu dưới dạng TXT – Xuất công thức Word sang LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Lưu tài liệu dưới dạng TXT – Xuất công thức Word sang LaTeX trong C#
url: /vi/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu tài liệu dưới dạng TXT – Xuất công thức Word sang LaTeX trong C#

Bạn đã bao giờ cần **save document as txt** trong khi vẫn giữ nguyên các công thức đẹp mắt? Bạn không phải là người duy nhất. Tính năng “Save as plain text” tích hợp sẵn của Word loại bỏ Office Math, để lại cho bạn những ký tự vô nghĩa không đọc được. Nếu bạn có thể giữ lại các công thức đó, nhưng dưới dạng LaTeX sạch sẽ thì sao?  

Trong hướng dẫn này chúng ta sẽ đi qua các bước chính xác để **convert Word to LaTeX**‑ready text bằng Aspose.Words cho .NET. Khi hoàn thành, bạn sẽ có một tệp `.txt` trong đó mọi công thức đều được biểu diễn dưới dạng markup LaTeX chuẩn, sẵn sàng chèn vào bài báo hoặc tệp markdown. Không cần bộ chuyển đổi bên ngoài, không cần sao chép‑dán thủ công—chỉ vài dòng C#.

## Bạn sẽ học được

- Cách tải tệp `.docx` bằng Aspose.Words.  
- Cấu hình `TxtSaveOptions` để Office Math được xuất dưới dạng LaTeX.  
- Lưu kết quả thành tệp văn bản thuần túy mà bạn có thể mở bằng bất kỳ trình soạn thảo nào.  
- Xử lý các trường hợp đặc biệt cho công thức nội dòng và công thức hiển thị, cùng một mẹo nhanh để xử lý hàng loạt nhiều tài liệu.

### Yêu cầu trước

- .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.6+).  
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Một tài liệu Word chứa ít nhất một công thức (đối tượng Office Math).

---

## Bước 1: Cài đặt Aspose.Words và thiết lập dự án

Đầu tiên, thêm thư viện vào dự án của bạn. Mở terminal trong thư mục solution và chạy:

```bash
dotnet add package Aspose.Words
```

> **Pro tip:** Nếu bạn đang dùng Visual Studio, UI NuGet Package Manager cũng hoạt động tốt—tìm “Aspose.Words” và nhấn Install.

Bây giờ tạo một ứng dụng console mới (hoặc chèn mã vào dự án hiện có). Các chỉ thị `using` bạn cần là:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Những chỉ thị này sẽ đưa lớp `Document` và kiểu `TxtSaveOptions` vào phạm vi sử dụng.

## Bước 2: Tải tài liệu nguồn

Chúng ta cần chỉ định cho Aspose.Words vị trí tệp Word chứa các công thức. Thay `YOUR_DIRECTORY/input.docx` bằng đường dẫn thực tế trên máy của bạn.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Tại sao lại quan trọng:** Việc tải tài liệu cho phép Aspose.Words truy cập đầy đủ vào các đối tượng Office Math nội bộ, những thứ mà một bộ xuất văn bản đơn giản không thể nhìn thấy.

## Bước 3: Cấu hình TxtSaveOptions để xuất LaTeX

Phép màu xảy ra trong đối tượng `TxtSaveOptions`. Bằng cách đặt `OfficeMathExportMode` thành `LaTeX`, mọi công thức sẽ được chuyển thành dạng LaTeX tương ứng.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **Còn muốn MathML?** Thay `OfficeMathExportMode` thành `MathML`. API này hỗ trợ nhiều định dạng đầu ra.

## Bước 4: Lưu tài liệu dưới dạng văn bản thuần

Bây giờ chúng ta ghi tệp ra. Tệp `Math.txt` sẽ chứa văn bản thường cộng với các đoạn LaTeX cho mỗi công thức.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Chạy chương trình sẽ tạo ra một tệp trông giống như sau:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Chú ý công thức nội dòng được bao quanh bởi `$…$` trong khi công thức hiển thị được bao bọc bằng `\[` và `\]`. Đó là quy ước chuẩn của LaTeX, và Aspose.Words thực hiện tự động.

## Bước 5: Kiểm tra kết quả (Tùy chọn)

Nếu bạn muốn xác nhận LaTeX hợp lệ, có thể đưa tệp `.txt` vào trình biên dịch LaTeX như `pdflatex` hoặc một công cụ trực tuyến như Overleaf. Văn bản nên biên dịch mà không gặp lỗi, và các công thức sẽ xuất hiện đúng như trong Word.

```bash
pdflatex Math.txt
```

Nếu nhận được thông báo “Undefined control sequence”, hãy chắc chắn rằng các gói LaTeX cần thiết (ví dụ `amsmath`) đã được đưa vào phần preamble khi bạn nhúng văn bản vào tài liệu LaTeX lớn hơn.

## Xử lý các biến thể phổ biến

### Chuyển đổi nhiều tệp trong một thư mục

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Xử lý công thức nội dòng và công thức hiển thị

Aspose.Words tự động phát hiện loại công thức dựa trên bố cục trong Word. Nếu bạn muốn ép buộc một kiểu cụ thể, có thể xử lý hậu kỳ kết quả:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Xuất sang các định dạng khác

Nếu LaTeX không phải là mục tiêu của bạn, chỉ cần chuyển chế độ xuất:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Hoặc dùng `HtmlSaveOptions` nếu bạn muốn nhúng MathML trong HTML.

---

## Ví dụ hoàn chỉnh

Dưới đây là chương trình đầy đủ, sẵn sàng chạy. Sao chép‑dán vào `Program.cs` của dự án console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Chạy chương trình (`dotnet run`), mở `Math.txt`, và bạn sẽ thấy nội dung Word của mình với các công thức LaTeX được giữ nguyên.

---

## Câu hỏi thường gặp

**Hỏi: Điều này có hoạt động với các tệp .doc cũ không?**  
Đáp: Có—Aspose.Words có thể mở các tệp `.doc` legacy, nhưng các công thức phức tạp có thể được lưu dưới dạng hình ảnh. Trong trường hợp đó, bộ xuất sẽ thay thế bằng một chú thích placeholder.

**Hỏi: Nếu một công thức chứa ký hiệu tùy chỉnh thì sao?**  
Đáp: Aspose.Words ánh xạ hầu hết các ký hiệu Office Math sang các lệnh LaTeX chuẩn. Đối với các ký hiệu thực sự tùy chỉnh, bạn có thể cần chỉnh sửa LaTeX được tạo ra thủ công.

**Hỏi: Đầu ra có được mã hoá UTF‑8 không?**  
Đáp: Mặc định, `TxtSaveOptions` ghi dưới dạng UTF‑8, an toàn cho hầu hết các ngôn ngữ và ký hiệu.

---

## Kết luận

Bây giờ bạn đã biết cách **save document as txt** trong khi giữ nguyên mọi công thức dưới dạng LaTeX sạch sẽ. Cách tiếp cận này cho phép bạn **convert Word to LaTeX** mà không cần công cụ bên thứ ba, và có thể mở rộng từ một tệp duy nhất tới toàn bộ thư mục. Tiếp theo, bạn có thể khám phá **convert word equations to LaTeX** cho xử lý hàng loạt, hoặc tìm hiểu **export word math latex** cho các pipeline HTML hoặc Markdown.

Hãy thoải mái thử nghiệm—đổi `OfficeMathExportMode` sang MathML, tinh chỉnh cách xử lý ngắt dòng, hoặc tích hợp đoạn mã này vào quy trình tạo tài liệu lớn hơn. Chúc lập trình vui vẻ, và hy vọng các công thức của bạn luôn được render hoàn hảo!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}