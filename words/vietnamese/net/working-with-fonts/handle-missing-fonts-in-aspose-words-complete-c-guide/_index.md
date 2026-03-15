---
category: general
date: 2026-03-14
description: Xử lý nhanh các phông chữ thiếu với Aspose.Words. Tìm hiểu cách bắt các
  cảnh báo thay thế phông chữ, cấu hình LoadOptions và tránh các vấn đề hiển thị.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: vi
og_description: Xử lý các phông chữ bị thiếu trong Aspose.Words bằng bộ thu thập cảnh
  báo. Hướng dẫn này trình bày chi tiết từng bước cách phát hiện và ghi lại việc thay
  thế phông chữ.
og_title: Xử lý phông chữ thiếu trong Aspose.Words – Hướng dẫn C# đầy đủ
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Xử lý phông chữ thiếu trong Aspose.Words – Hướng dẫn C# đầy đủ
url: /vi/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

The core idea stays the same: capture the warning, act on it, and keep your documents looking exactly as intended." => "Hãy thoải mái thử nghiệm — thay `"Arial"` bằng `"Tahoma"` hoặc tải một bộ tài liệu khác. Ý tưởng cốt lõi vẫn như cũ: bắt cảnh báo, thực hiện hành động và giữ cho tài liệu của bạn hiển thị đúng như mong muốn."

Now "Happy coding! 🚀" => "Chúc lập trình vui vẻ! 🚀"

Now ensure we keep shortcodes at top and bottom unchanged.

Now produce final output.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xử lý Phông chữ Bị thiếu trong Aspose.Words – Hướng dẫn C# Đầy đủ

Bạn đã bao giờ cần **xử lý phông chữ bị thiếu** khi tải một tài liệu Word và tự hỏi tại sao đầu ra PDF hoặc hình ảnh của bạn lại bị sai lệch? Bạn không phải là người duy nhất. Các tệp phông chữ thiếu là một kẻ gây rắc rối âm thầm có thể biến một báo cáo được thiết kế hoàn hảo thành một mớ hỗn độn.  

Tin tốt? Aspose.Words cung cấp cho bạn một cách sạch sẽ để bắt các sự kiện thay thế phông chữ, ghi lại chúng, và thậm chí thay thế bằng một phông chữ dự phòng nếu bạn muốn. Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy, cho thấy cách thiết lập bộ thu thập cảnh báo, gắn nó vào `LoadOptions`, và tải một tài liệu có thể chứa các phông chữ bị thiếu.

Khi kết thúc hướng dẫn này, bạn sẽ có thể:

* Phát hiện mọi lần thay thế phông chữ xảy ra trong quá trình tải tài liệu.  
* Xuất một thông báo console thân thiện (hoặc chuyển tới logger) cho mỗi phông chữ bị thiếu.  
* Mở rộng giải pháp để thay thế phông chữ, nếu cần.  

**Prerequisites** – bạn sẽ cần:

* .NET 6.0 trở lên (mã hoạt động với .NET Core và .NET Framework cũng được).  
* Gói NuGet Aspose.Words cho .NET (phiên bản hiện tại 23.11).  
* Một tệp Word cố tình tham chiếu tới một phông chữ bạn không có trên máy — chúng tôi sẽ gọi nó là `doc-with-missing-font.docx`.  

Nếu bạn đã quen thuộc với C# và đã có dự án thiết lập, bạn có thể ngay lập tức chuyển sang phần mã. Nếu không, hãy tiếp tục đọc; chúng tôi sẽ đề cập đến các bước thiết lập nhỏ trước.

---

## Tại sao việc Xử lý Phông chữ Bị thiếu lại Quan trọng

Khi Aspose.Words tải một tài liệu, nó cố gắng khớp mỗi glyph với một phông chữ được cài đặt trên máy. Nếu không tìm thấy phông chữ chính xác, nó sẽ âm thầm thay thế bằng phông chữ gần nhất. Việc thay thế này có thể thay đổi chiều cao dòng, kerning, và thậm chí làm cho một số ký tự biến mất. Bằng cách bắt sự kiện `WarningType.FontSubstitution` bạn sẽ có một cái nhìn trong suốt về **cái gì** đã được thay thế và **tại sao**, điều này thiết yếu cho:

* Duy trì tính nhất quán thương hiệu (phông chữ công ty của bạn phải xuất hiện đúng như thiết kế).  
* Gỡ lỗi các vấn đề chuyển đổi PDF — thường nguyên nhân là phông chữ bị thiếu.  
* Xây dựng các pipeline tài liệu tự động, nơi bạn cần đánh dấu các tệp có vấn đề để kiểm tra thủ công.

Bây giờ vì đã rõ “tại sao”, chúng ta hãy đi sâu vào **cách thực hiện**.

---

## Bước 1 – Thiết lập Bộ Thu thập Cảnh báo

Đối tượng đầu tiên chúng ta cần là một đối tượng có thể lắng nghe các cảnh báo của Aspose.Words. `DocumentWarnings` thực thi `IWarningCallback`, cho phép chúng ta phản hồi mỗi khi thư viện phát sinh một cảnh báo.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**What’s happening?**  
* `DocumentWarnings` là một lớp bọc mỏng quanh giao diện callback.  
* Lambda kiểm tra `e.WarningType` để chúng ta bỏ qua các cảnh báo không liên quan (như các tính năng đã lỗi thời).  
* `e.WarningInfo` chứa tên của phông chữ bị thiếu, chúng ta in nó ra console.  

*Pro tip*: Thay `Console.WriteLine` bằng một logger có cấu trúc (Serilog, NLog) trong môi trường production — cách này bạn sẽ có sẵn timestamp và mức log mà không tốn công sức.

---

## Bước 2 – Kết nối Bộ Thu thập vào LoadOptions

`LoadOptions` là người kiểm soát mọi tài liệu bạn mở bằng Aspose.Words. Bằng cách gán thể hiện `fontWarnings` của chúng ta vào thuộc tính `WarningCallback` của nó, chúng ta đảm bảo bộ thu thập hoạt động trong suốt quá trình tải.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Why use LoadOptions?**  
Ngoài việc xử lý cảnh báo, `LoadOptions` cho phép bạn kiểm soát việc xử lý mật khẩu, mã hóa, và thậm chí tải tài nguyên tùy chỉnh. Ở đây chúng ta tập trung vào phần cảnh báo, nhưng cùng một mẫu có thể áp dụng cho các callback khác.

---

## Bước 3 – Tải Tài liệu với Các Tùy chọn Đã Cấu hình

Bây giờ chúng ta cuối cùng đưa tài liệu vào bộ nhớ. Nếu có bất kỳ phông chữ nào bị thiếu, bộ thu thập sẽ được kích hoạt và bạn sẽ thấy một dòng console cho mỗi lần thay thế.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Nếu bạn chạy đoạn mã này với một tài liệu tham chiếu, ví dụ, *Calibri Light* trong khi máy thử nghiệm của bạn chỉ có *Calibri*, bạn sẽ nhận được đầu ra tương tự như:

```
Font 'Calibri Light' was substituted.
```

Đó là toàn bộ vòng lặp phát hiện — đơn giản nhưng mạnh mẽ.

---

## Bước 4 – (Tùy chọn) Thay thế Phông chữ Bị thiếu bằng Phông chữ Dự phòng

Đôi khi bạn không chỉ muốn ghi log vấn đề; bạn muốn áp dụng một phông chữ dự phòng để đầu ra được hiển thị nhất quán. Aspose.Words cho phép bạn cung cấp một đối tượng `FontSettings` tùy chỉnh để ánh xạ các phông chữ bị thiếu sang một phông chữ thay thế.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Explanation**  
* Ký tự đại diện `"*"` cho Aspose.Words biết xử lý *bất kỳ* phông chữ bị thiếu theo cùng một cách.  
* Bạn cũng có thể ánh xạ các phông chữ cụ thể riêng lẻ nếu cần kiểm soát chi tiết.  
* Sau khi thiết lập `document.FontSettings`, bất kỳ việc render tiếp theo (PDF, hình ảnh, HTML) đều sẽ tuân theo việc thay thế.

---

## Ví dụ Hoạt động Đầy đủ

Dưới đây là chương trình hoàn chỉnh mà bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các câu lệnh `using` cần thiết, xử lý lỗi, và các chú thích để rõ ràng.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Expected output** (when a missing font is detected):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Nếu tài liệu nguồn đã chứa tất cả các phông chữ cần thiết, dòng cảnh báo sẽ không xuất hiện — không có gì phải lo.

---

## Câu hỏi Thường gặp & Trường hợp Đặc biệt

| Question | Answer |
|----------|--------|
| **Nếu tôi chỉ muốn ghi log, không thay thế phông chữ thì sao?** | Bỏ qua khối `FontSettings` hoàn toàn; chỉ cần bộ thu thập cảnh báo là đủ. |
| **Tôi có thể chuyển hướng cảnh báo tới một tệp không?** | Có — thay thế `Console.WriteLine` bằng `File.AppendAllText("font-warnings.log", …)`. |
| **Điều này có hoạt động với DOC, DOCX và ODT không?** | Hoàn toàn có. `LoadOptions` áp dụng cho tất cả các định dạng được Aspose.Words hỗ trợ. |
| **Còn các phông chữ tùy chỉnh được nhúng trong tài liệu thì sao?** | Các phông chữ nhúng bỏ qua cơ chế thay thế; chúng được sử dụng nguyên trạng. |
| **Có ảnh hưởng đến hiệu năng không?** | Chi phí bổ sung là tối thiểu — chỉ một callback cho mỗi phông chữ bị thiếu. Đối với các lô lớn, hãy cân nhắc gom lại các cảnh báo thay vì ghi từng sự kiện. |

---

## Kết luận

Chúng tôi đã trình bày **cách xử lý phông chữ bị thiếu** trong Aspose.Words bằng cách gắn bộ thu thập `DocumentWarnings` vào `LoadOptions`, tùy chọn thay thế bằng một phông chữ dự phòng, và lưu kết quả. Mẫu này cung cấp cho bạn khả năng quan sát đầy đủ các sự kiện thay thế phông chữ, giúp duy trì độ trung thực hình ảnh qua các chuyển đổi PDF, hình ảnh hoặc HTML.

Các bước tiếp theo bạn có thể khám phá:

* Tích hợp bộ thu thập cảnh báo với một framework ghi log tập trung.  
* Xây dựng bảng điều khiển UI liệt kê các tài liệu có phông chữ bị thiếu để xử lý hàng loạt.  
* Kết hợp cách tiếp cận này với Aspose.PDF để xác minh rằng các PDF được tạo thực sự sử dụng phông chữ dự phòng.  

Hãy thoải mái thử nghiệm — thay `"Arial"` bằng `"Tahoma"` hoặc tải một bộ tài liệu khác. Ý tưởng cốt lõi vẫn như cũ: bắt cảnh báo, thực hiện hành động và giữ cho tài liệu của bạn hiển thị đúng như mong muốn.

Chúc lập trình vui vẻ! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}