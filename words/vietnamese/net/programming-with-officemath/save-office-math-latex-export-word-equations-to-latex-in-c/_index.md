---
category: general
date: 2026-04-21
description: Lưu công thức LaTeX của Office nhanh chóng bằng Aspose.Words – đồng thời
  tìm hiểu cách lưu văn bản thuần của Word và xuất công thức Word sang LaTeX trong
  một lần.
draft: false
keywords:
- save office math latex
- save word plain text
- export word equations latex
- convert word math latex
- convert word equations mathml
language: vi
og_description: lưu LaTeX toán học Office ngay lập tức; học cách xuất LaTeX các công
  thức Word và chuyển đổi LaTeX toán học Word bằng Aspose.Words trong C#
og_title: Lưu Office Math LaTeX – Xuất các phương trình Word sang LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Lưu Office Math LaTeX – Xuất các phương trình Word sang LaTeX trong C#
url: /vi/net/programming-with-officemath/save-office-math-latex-export-word-equations-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# lưu Office Math LaTeX – Xuất công thức Word sang LaTeX với Aspose.Words

Bạn đã bao giờ cần **lưu Office Math LaTeX** từ một tệp `.docx` nhưng không chắc bắt đầu từ đâu? Bạn không phải là người duy nhất, và tin tốt là giải pháp khá đơn giản. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn chi tiết các bước để xuất công thức Word sang LaTeX (và thậm chí MathML) bằng Aspose.Words cho .NET, đồng thời chỉ cho bạn cách **lưu văn bản thuần Word** cùng với các công thức.

Chúng tôi sẽ đề cập đến mọi điều bạn có thể thắc mắc: tại sao bạn nên chọn LaTeX thay vì các định dạng khác, cách cấu hình `TxtSaveOptions`, và cách thực hiện nếu bạn cần **chuyển đổi LaTeX của công thức Word** sang dạng khác. Khi kết thúc, bạn sẽ có một đoạn mã có thể chạy được, nhận một tài liệu Word có các đối tượng Office Math và tạo ra một tệp `.txt` sạch chứa các công thức LaTeX (hoặc MathML). Không cần công cụ bên ngoài, không cần sao chép‑dán thủ công—chỉ có mã C# sạch mà bạn có thể đưa vào bất kỳ dự án nào.

## Yêu cầu trước

- **Aspose.Words for .NET** (v23.10 hoặc sau). Gói NuGet là `Aspose.Words`.
- Môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code với phần mở rộng C#).
- Tệp Word (`.docx`) chứa ít nhất một công thức được tạo bằng trình chỉnh sửa Office Math.
- Kiến thức cơ bản về cú pháp C#—không có gì phức tạp, chỉ các câu lệnh `using` thông thường.

Nếu bạn đã có tất cả các mục trên, tuyệt vời—hãy bắt đầu.

## Bước 1 – Thiết lập các tùy chọn **lưu Office Math LaTeX**

Điều đầu tiên bạn cần làm là chỉ cho Aspose.Words cách bạn muốn nội dung toán học được xuất ra. Lớp `TxtSaveOptions` có thuộc tính `OfficeMathExportMode` chấp nhận ba giá trị: `LaTeX`, `MathML`, hoặc `Text`. Đối với mục tiêu chính của chúng ta, chúng ta sẽ chọn `LaTeX`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Configure TXT save options to export equations as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // This line makes the library output LaTeX for every Office Math object
    OfficeMathExportMode = OfficeMathExportMode.LaTeX
    // You could also use OfficeMathExportMode.MathML or .Text here
};
```

**Tại sao điều này quan trọng:** Khi bạn đặt `OfficeMathExportMode` thành `LaTeX`, mỗi công thức sẽ được chuyển đổi thành mã nguồn LaTeX thô. Mã nguồn này sau này có thể được biên dịch bằng bất kỳ công cụ LaTeX nào, cho bạn kết quả gõ chữ hoàn hảo mà không cần nhập lại các công thức.

> **Mẹo chuyên nghiệp:** Nếu bạn cần **chuyển đổi công thức Word sang MathML**, chỉ cần đổi giá trị enum thành `OfficeMathExportMode.MathML`. Phần còn lại của mã vẫn giữ nguyên.

## Bước 2 – Tải tài liệu Word (kịch bản **lưu văn bản thuần Word**)

Tiếp theo, chúng ta tải tệp nguồn `.docx`. Bước này giống nhau dù bạn chỉ quan tâm đến việc trích xuất văn bản thuần hay bạn cũng muốn các công thức ở dạng LaTeX.

```csharp
// Load the document that contains Office Math objects
Document doc = new Document(@"C:\MyDocs\input.docx");

// Optional: verify that the document actually has equations
bool hasMath = doc.GetChildNodes(NodeType.OfficeMath, true).Count > 0;
if (!hasMath)
{
    Console.WriteLine("Warning: No Office Math objects found in the document.");
}
```

**Điều gì đang xảy ra ở đây?** Hàm khởi tạo `Document` đọc tệp vào bộ nhớ. Kiểm tra nhanh bằng `GetChildNodes` giúp bạn phát hiện một trường hợp góc phổ biến—cố gắng xuất LaTeX từ tệp không chứa công thức nào. Đây là một biện pháp bảo vệ nhỏ giúp bạn tránh kết quả trống gây bối rối sau này.

## Bước 3 – **lưu Office Math LaTeX** vào tệp văn bản thuần

Bây giờ chúng ta cuối cùng ghi tệp. Phương thức `Save` tuân theo `TxtSaveOptions` mà chúng ta đã cấu hình trước đó, vì vậy tệp `.txt` kết quả sẽ chứa cả văn bản thường và các đoạn LaTeX cho mỗi công thức.

```csharp
// Define the output path
string outputPath = @"C:\MyDocs\Equations.txt";

// Save the document as plain text, with LaTeX equations embedded
doc.Save(outputPath, txtOptions);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

Khi bạn mở `Equations.txt` bạn sẽ thấy một nội dung giống như:

```
This is a sample paragraph.

\begin{equation}
E = mc^2
\end{equation}

Another paragraph follows.
```

Các khối LaTeX sẽ được tự động bao bọc trong `\begin{equation}` … `\end{equation}`, giúp chúng sẵn sàng để chèn vào bất kỳ tài liệu LaTeX nào.

## Bước 4 – Thay thế: **chuyển đổi công thức Word sang MathML** thay vì LaTeX

Nếu chuỗi công cụ downstream của bạn ưu tiên MathML (ví dụ, một trang web hiển thị công thức bằng MathJax), chỉ cần thay đổi chế độ xuất:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
doc.Save(@"C:\MyDocs\EquationsMathML.txt", txtOptions);
```

Kết quả bây giờ sẽ chứa các thẻ MathML dạng XML, như:

```xml
<math xmlns="http://www.w3.org/1998/Math/MathML">
  <mi>E</mi>
  <mo>=</mo>
  <mi>m</mi>
  <msup><mi>c</mi><mn>2</mn></msup>
</math>
```

Đó là cách nhanh để **chuyển đổi công thức Word sang MathML** mà không cần viết bộ phân tích tùy chỉnh.

## Bước 5 – Thêm: **lưu văn bản thuần Word** trong khi giữ các công thức riêng biệt

Đôi khi bạn muốn một phiên bản văn bản sạch của tài liệu *không* có bất kỳ LaTeX hay MathML nào được nhúng. Bạn có thể đạt được điều này bằng cách chuyển chế độ xuất sang `Text` và thực hiện một lần lưu thứ hai:

```csharp
// Export pure plain text (no math markup)
txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
doc.Save(@"C:\MyDocs\PlainDocument.txt", txtOptions);
```

Bây giờ bạn có ba tệp nằm cạnh nhau:

| File                         | Nội dung                                   |
|------------------------------|--------------------------------------------|
| `Equations.txt`              | Văn bản thuần **+** công thức LaTeX       |
| `EquationsMathML.txt`        | Văn bản thuần **+** công thức MathML      |
| `PlainDocument.txt`          | Văn bản thuần, đã loại bỏ các công thức    |

Mẫu này hữu ích khi bạn cần đưa văn bản thuần vào chỉ mục tìm kiếm trong khi vẫn giữ lại các công thức gốc cho việc xuất bản học thuật.

## Ví dụ Hoạt động Đầy đủ (Sẵn sàng Sao chép‑Dán)

Dưới đây là chương trình hoàn chỉnh mà bạn có thể biên dịch và chạy ngay. Nó minh họa **lưu Office Math LaTeX**, **xuất công thức Word sang LaTeX**, **chuyển đổi LaTeX của công thức Word**, và **lưu văn bản thuần Word**—tất cả trong một script gọn gàng.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure TXT save options for LaTeX export
        TxtSaveOptions txtOptions = new TxtSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        // 2️⃣ Load the source Word document
        string inputPath = @"C:\MyDocs\input.docx";
        Document doc = new Document(inputPath);

        // Quick sanity check for equations
        if (doc.GetChildNodes(NodeType.OfficeMath, true).Count == 0)
        {
            Console.WriteLine("No equations found – proceeding with plain‑text export only.");
        }

        // 3️⃣ Save with LaTeX equations embedded
        string latexPath = @"C:\MyDocs\Equations.txt";
        doc.Save(latexPath, txtOptions);
        Console.WriteLine($"LaTeX export saved to {latexPath}");

        // 4️⃣ Switch to MathML and save (optional)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML;
        string mathmlPath = @"C:\MyDocs\EquationsMathML.txt";
        doc.Save(mathmlPath, txtOptions);
        Console.WriteLine($"MathML export saved to {mathmlPath}");

        // 5️⃣ Finally, pure plain‑text export (no math markup)
        txtOptions.OfficeMathExportMode = OfficeMathExportMode.Text;
        string plainPath = @"C:\MyDocs\PlainDocument.txt";
        doc.Save(plainPath, txtOptions);
        Console.WriteLine($"Plain‑text export saved to {plainPath}");
    }
}
```

**Kết quả mong đợi:** Sau khi chạy, bạn sẽ thấy ba tệp văn bản trong `C:\MyDocs`. Mở `Equations.txt` và bạn sẽ thấy các khối LaTeX; `EquationsMathML.txt` sẽ chứa MathML; `PlainDocument.txt` sẽ không có bất kỳ dấu hiệu nào của công thức.

## Câu hỏi Thường gặp & Trường hợp Cạnh

- **Nếu tôi chỉ cần LaTeX cho một phần các công thức?**  
  Sử dụng API nút `OfficeMath` để lặp qua từng công thức, xuất thủ công bằng `MathConverter`, và thay thế văn bản placeholder ở vị trí mong muốn. Cách này cho bạn kiểm soát chi tiết nhưng sẽ thêm một vài dòng mã.

- **Có hoạt động với .NET Core / .NET 5+ không?**  
  Hoàn toàn có. Aspose.Words hỗ trợ đa nền tảng, vì vậy cùng một đoạn mã chạy trên Windows, Linux và macOS miễn là phiên bản runtime phù hợp với yêu cầu của thư viện.

- **Tôi có thể thay đổi phần bao bọc LaTeX (`\begin{equation}`) thành gì khác không?**  
  Có. Đặt `txtOptions.OfficeMathExportMode = OfficeMathExportMode.LaTeX` và sau đó chỉnh sửa `txtOptions.MathExportSettings` (có trong các phiên bản mới) để tùy chỉnh dấu phân cách.

- **Lo ngại về hiệu năng khi xử lý tài liệu lớn?**  
  Thư viện stream đầu ra, vì vậy việc sử dụng bộ nhớ vẫn ở mức vừa phải. Tuy nhiên

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}