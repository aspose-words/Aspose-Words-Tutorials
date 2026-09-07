---
category: general
date: 2026-01-10
description: Tìm hiểu cách sử dụng LoadOptions để xử lý các phông chữ thiếu trong
  Aspose.Words. Mã từng bước, mẹo và các thực tiễn tốt nhất để tải tài liệu một cách
  ổn định.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: vi
og_description: Cách sử dụng LoadOptions để xử lý phông chữ thiếu trong Aspose.Words.
  Nhận một ví dụ đầy đủ, có thể chạy được kèm theo giải thích và các mẹo thực tế.
og_title: Cách Sử Dụng LoadOptions trong Aspose.Words – Hướng Dẫn Toàn Diện
tags:
- Aspose.Words
- C#
- .NET
title: Cách sử dụng LoadOptions trong Aspose.Words – Hướng dẫn đầy đủ
url: /vi/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Sử Dụng LoadOptions trong Aspose.Words – Hướng Dẫn Đầy Đủ

Bạn đã bao giờ tự hỏi **cách sử dụng LoadOptions** khi tải một tài liệu Word có thể thiếu một số phông chữ chưa? Bạn không phải là người duy nhất băn khoăn về vấn đề này. Trong nhiều dự án thực tế, tài liệu di chuyển qua các máy tính, và hệ thống đích thường không có các kiểu chữ chính xác mà tác giả đã dùng. Kết quả? Các phông chữ được thay thế không mong muốn, có thể làm hỏng bố cục, ẩn các ký tự quan trọng, hoặc chỉ đơn giản là trông không đúng thương hiệu.  

May mắn là Aspose.Words cung cấp một cách sạch sẽ để *xử lý các phông chữ thiếu* bằng cách cung cấp một đối tượng `LoadOptions` với callback cảnh báo. Trong hướng dẫn này, bạn sẽ học **cách sử dụng LoadOptions** để bắt các cảnh báo thay thế phông chữ, ghi log chúng, và giữ cho quy trình xử lý của bạn luôn ổn định.

Chúng ta sẽ đề cập tới:

* Tạo lớp callback cảnh báo  
* Cấu hình `LoadOptions` với callback đó  
* Tải tài liệu trong khi theo dõi các phông chữ thiếu  
* Mẹo khắc phục sự cố và mở rộng giải pháp  

Không cần tài liệu bên ngoài — mọi thứ bạn cần đều có ở đây.

---

## Những Gì Bạn Cần Chuẩn Bị

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* **Aspose.Words for .NET** (phiên bản mới nhất tính đến năm 2026) được cài đặt qua NuGet  
* Môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code)  
* Một tệp DOCX mẫu tham chiếu tới một phông chữ mà bạn không có trên máy (chúng ta sẽ gọi nó là `input.docx`)  

Đó là tất cả — không cần thư viện bổ sung nào khác.

---

## Bước 1 – Định Nghĩa Callback Cảnh Báo Để Bắt Thay Thế Phông Chữ

Phần đầu tiên của giải pháp là một lớp triển khai `IWarningCallback`. Aspose.Words sẽ gọi phương thức `Warning` của nó mỗi khi gặp một vấn đề đáng chú ý — chẳng hạn như một phông chữ thiếu.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Tại sao điều này quan trọng:**  
Bằng cách lọc theo `WarningType.FontSubstitution` chúng ta tránh được sự lộn xộn từ các cảnh báo không liên quan (ví dụ: tính năng đã lỗi thời). Callback cho bạn toàn quyền kiểm soát — bạn có thể ghi log vào file, ném ngoại lệ, hoặc thậm chí cố gắng nhúng một phông chữ dự phòng một cách lập trình.

---

## Bước 2 – Cấu Hình LoadOptions Với Callback

Bây giờ chúng ta đã có handler, cần thông báo cho Aspose.Words sử dụng nó. Đây là nơi **cách sử dụng LoadOptions** trong thực tế.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Mẹo:** `LoadOptions` còn có nhiều tùy chọn khác (ví dụ: `Password`, `LoadFormat`, `Encoding`). Bạn có thể xâu chuỗi chúng lại, nhưng đối với việc xử lý phông chữ thiếu, `WarningCallback` là yếu tố quan trọng nhất.

---

## Bước 3 – Tải Tài Liệu Bằng Các Tùy Chọn Đã Cấu Hình

Với `LoadOptions` đã sẵn sàng, việc tải tài liệu trở nên đơn giản. Aspose.Words sẽ tự động gọi callback cho bất kỳ phông chữ nào không tìm thấy.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Kết quả mong đợi:**  

Nếu `input.docx` sử dụng một phông chữ tên *“GothicBold”* mà không được cài đặt, bạn sẽ thấy một thông báo như sau:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Dòng cảnh báo xuất hiện **ngay khi phông chữ bị thiếu được gặp**, cung cấp phản hồi tức thời.

---

## Bước 4 – (Tùy Chọn) Tiếp Tục Xử Lý Tài Liệu

Thường thì bạn sẽ muốn làm nhiều hơn chỉ tải tệp. Dưới đây là một vài hành động phổ biến sau khi tải, hoạt động mượt mà với thiết lập cảnh báo của chúng ta.

### 4.1 Lưu Tài Liệu Dưới Dạng PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Thay Thế Phông Chữ Thiếu Bằng Một Phông Chữ Dự Phòng Đã Biết

Nếu bạn muốn một phông chữ dự phòng cụ thể (ví dụ: *“Calibri”*), bạn có thể điều chỉnh `FontSettings` trước khi lưu:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Ghi Log Tất Cả Cảnh Báo Vào File

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Các đoạn mã này minh họa **cách sử dụng LoadOptions** vượt ra ngoài trường hợp cơ bản, cho bạn sự linh hoạt cho các giải pháp cấp sản xuất.

---

## Những Sai Lầm Thường Gặp & Cách **Xử Lý Phông Chữ Thiếu** Một Cách Trơn Tru

| Sai Lầm | Nguyên Nhân | Cách Khắc Phục / Giảm Thiểu |
|---------|-------------|-----------------------------|
| **Không gắn callback** | Quên thiết lập `WarningCallback`. | Luôn tạo một thể hiện `LoadOptions` và gán handler trước khi tải. |
| **Callback chỉ in ra, không lưu** | Trong dịch vụ web, output console biến mất. | Thay `Console.WriteLine` bằng một logger (Serilog, NLog) hoặc ghi vào kho lưu trữ bền vững. |
| **Nhiều phông chữ thiếu, chỉ báo cáo cái đầu tiên** | Callback ném ngoại lệ ở cảnh báo đầu tiên. | Giữ callback nhẹ nhàng; tránh ném ngoại lệ trừ khi bạn thực sự muốn dừng. |
| **Phông chữ thay thế trông không đúng** | Thay thế mặc định có thể chọn phông chữ không giống về hình ảnh. | Sử dụng `FontSettings.SubstitutionSettings.FontSubstitutionRules` để ưu tiên phông dự phòng của bạn. |
| **Giảm hiệu năng trên tài liệu lớn** | Callback được gọi hàng ngàn lần. | Thu thập cảnh báo vào danh sách và xử lý sau khi tải, hoặc lọc chỉ các tên phông chữ duy nhất. |

Biết trước những tình huống này giúp bạn **xử lý phông chữ thiếu** mà không gặp bất ngờ.

---

## Ví Dụ Hoàn Chỉnh – Tất Cả Các Thành Phần Cùng Nhau

Dưới đây là chương trình hoàn chỉnh, sẵn sàng chạy, minh họa toàn bộ quy trình. Sao chép‑dán vào một dự án console, thêm gói NuGet Aspose.Words, và nó sẽ hoạt động ngay.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**Chạy chương trình này** sẽ:

1. In bất kỳ cảnh báo thay thế phông chữ nào ra console.  
2. Lưu bố cục gốc dưới dạng `output.pdf`.  
3. Lưu một PDF thứ hai (`output-with-fallback.pdf`) buộc sử dụng phông dự phòng *Calibri* hoặc *Arial*.

---

## Câu Hỏi Thường Gặp (FAQs)

**Hỏi: Điều này có hoạt động với các tệp DOC, RTF, hoặc HTML không?**  
Đáp: Có. `LoadOptions` không phụ thuộc vào định dạng; miễn là bạn truyền đúng đường dẫn tệp, callback cảnh báo sẽ được kích hoạt cho các phông chữ thiếu trên mọi định dạng được hỗ trợ.

**Hỏi: Tôi có thể tắt hoàn toàn các cảnh báo không?**  
Đáp: Bạn có thể gán một callback rỗng (`new IWarningCallback { Warning = _ => {} }`) hoặc đặt `LoadOptions.WarningCallback = null`. Tuy nhiên, mất khả năng quan sát có nghĩa là bạn có thể bỏ lỡ các vấn đề phông chữ quan trọng.

**Hỏi: Nếu muốn thay thế phông chữ thiếu bằng các phông chữ đã nhúng thì sao?**  
Đáp: Sử dụng `FontSettings` để nhúng một phông chữ thay thế (`AddFontSource`). Kết hợp với các quy tắc thay thế để có trải nghiệm liền mạch.

**Hỏi: Callback có an toàn với đa luồng không?**  
Đáp: Callback có thể được gọi từ nhiều luồng khi tải tài liệu lớn song song. Đảm bảo các tài nguyên chia sẻ (ví dụ: file log) được đồng bộ.

---

## Kết Luận

Chúng ta đã đi qua **cách sử dụng LoadOptions** trong Aspose.Words để **xử lý phông chữ thiếu** một cách tinh tế. Bằng cách định nghĩa một `IWarningCallback` tùy chỉnh, gắn nó vào một đối tượng `LoadOptions`, và tải tài liệu với cấu hình đó, bạn sẽ có được cái nhìn thời gian thực về bất kỳ sự kiện thay thế phông chữ nào. Từ đó, bạn có thể ghi log, thay thế, hoặc nhúng phông chữ dự phòng để giữ cho đầu ra luôn đúng như mong muốn.

Nhớ lại các bước quan trọng:

1. Triển khai callback cảnh báo tập trung vào `WarningType.FontSubstitution`.  
2. Gắn callback vào đối tượng `LoadOptions`.  
3. Tải tài liệu bằng các tùy chọn này.  
4. (Tùy chọn) Áp dụng các quy tắc thay thế phông chữ hoặc ghi log thêm nếu cần.

Hãy thử nghiệm — thay thế logger console bằng một logger có cấu trúc, thêm cảnh báo email cho các phông chữ thiếu quan trọng, hoặc tích hợp mẫu này vào một pipeline xử lý tài liệu lớn. Cách tiếp cận này mở rộng tốt dù bạn chỉ xử lý một tệp hay hàng ngàn tệp trong một batch job.

Chúc lập trình vui vẻ, và mong rằng tài liệu của bạn luôn hiển thị đúng phông chữ!  

---

![ví dụ cách sử dụng loadoptions]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}