---
category: general
date: 2026-03-30
description: Cách bắt cảnh báo khi tải tệp DOCX – học cách phát hiện phông chữ thiếu,
  cấu hình cài đặt phông chữ và thiết lập tùy chọn tải trong C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: vi
og_description: cách bắt các cảnh báo khi tải tệp DOCX – hướng dẫn từng bước để phát
  hiện phông chữ thiếu và cấu hình cài đặt phông chữ trong C#
og_title: cách bắt cảnh báo – cấu hình tùy chọn tải cho phông chữ thiếu
tags:
- Aspose.Words
- C#
- Font management
title: Cách ghi lại cảnh báo – Cấu hình tùy chọn tải cho phông chữ thiếu
url: /vi/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cách ghi nhận cảnh báo – cấu hình tùy chọn tải cho phông chữ thiếu

Bạn đã bao giờ tự hỏi **cách ghi nhận cảnh báo** xuất hiện khi một tài liệu cố gắng sử dụng phông chữ mà bạn chưa cài đặt không? Đây là một tình huống khiến nhiều nhà phát triển làm việc với các thư viện xử lý văn bản gặp khó khăn, đặc biệt khi bạn cần **phát hiện phông chữ thiếu** trước khi chúng làm hỏng quy trình xuất PDF của bạn.  

Trong tutorial này chúng tôi sẽ cho bạn thấy một giải pháp thực tế, sẵn sàng chạy mà **cấu hình cài đặt phông chữ**, **đặt tùy chọn tải**, và in mọi cảnh báo thay thế ra console. Khi kết thúc, bạn sẽ biết chính xác **cách xử lý phông chữ thiếu** sao cho ứng dụng của bạn vẫn ổn định và người dùng hài lòng.

## Những gì bạn sẽ học

- Cách **đặt tùy chọn tải** để thư viện báo cáo vấn đề phông chữ thay vì tự động thay thế âm thầm.  
- Các bước chính xác để **cấu hình cài đặt phông chữ** nhằm ghi nhận cảnh báo.  
- Các cách **phát hiện phông chữ thiếu** bằng chương trình và phản hồi tương ứng.  
- Một ví dụ C# đầy đủ, copy‑paste, hoạt động với Aspose.Words for .NET mới nhất (v24.10 tại thời điểm viết).  
- Mẹo mở rộng giải pháp để ghi log cảnh báo, fallback sang phông chữ tùy chỉnh, hoặc hủy xử lý khi phông chữ quan trọng không có.

> **Yêu cầu trước:** Bạn cần cài đặt gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`). Không cần bất kỳ phụ thuộc bên ngoài nào khác.

---

## Bước 1: Nhập không gian tên và chuẩn bị dự án

Đầu tiên, thêm các chỉ thị `using` cần thiết. Đây không chỉ là đoạn mã mẫu; nó cho trình biên dịch biết `LoadOptions`, `FontSettings`, và `Document` nằm ở đâu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang dùng .NET 6+ có thể bật *global using* để tránh lặp lại các dòng này trong mỗi file.

---

## Bước 2: Đặt tùy chọn tải và bật cảnh báo thay thế phông chữ

Trọng tâm của **cách ghi nhận cảnh báo** nằm ở đối tượng `LoadOptions`. Bằng cách tạo một thể hiện `FontSettings` mới và gắn một bộ xử lý sự kiện vào `SubstitutionWarning`, bạn yêu cầu thư viện thông báo mỗi khi không tìm thấy phông chữ được yêu cầu.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Tại sao điều này quan trọng:** Nếu không đăng ký sự kiện, Aspose.Words sẽ âm thầm chuyển sang phông chữ mặc định và bạn sẽ không biết glyph nào đã bị thay thế. Khi lắng nghe `SubstitutionWarning`, bạn sẽ có một bản ghi đầy đủ—rất quan trọng trong các môi trường yêu cầu tuân thủ nghiêm ngặt.

---

## Bước 3: Tải tài liệu bằng các tùy chọn đã cấu hình

Bây giờ các cảnh báo đã được kết nối, hãy tải DOCX (hoặc bất kỳ định dạng hỗ trợ nào) bằng `loadOptions` vừa chuẩn bị. Hàm khởi tạo `Document` sẽ kích hoạt logic kiểm tra phông chữ ngay lập tức.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Nếu tệp tham chiếu, ví dụ, *“Comic Sans MS”* trên máy chỉ có *“Arial”*, bạn sẽ thấy một thông báo như:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Dòng này được in thẳng ra console vì bộ xử lý chúng ta đã gắn ở trên.

---

## Bước 4: Xác minh và phản hồi với các cảnh báo đã ghi nhận

Ghi nhận cảnh báo chỉ là một nửa công việc; bạn thường cần quyết định bước tiếp theo. Dưới đây là một mẫu nhanh lưu các cảnh báo vào danh sách để phân tích sau—hoàn hảo nếu bạn muốn ghi log vào file hoặc hủy nhập khi một phông chữ quan trọng bị thiếu.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Xử lý các trường hợp đặc biệt:**  
- **Nhiều phông chữ thiếu:** Danh sách sẽ chứa một mục cho mỗi lần thay thế, vì vậy bạn có thể duyệt và tạo báo cáo chi tiết.  
- **Phông chữ fallback tùy chỉnh:** Nếu bạn có các tệp phông chữ riêng, thêm chúng vào `FontSettings` trước khi tải: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Các cảnh báo sau đó sẽ hiển thị fallback tùy chỉnh thay vì mặc định hệ thống.  

---

## Bước 5: Ví dụ hoàn chỉnh (Sẵn sàng sao chép‑dán)

Kết hợp mọi thứ lại, đây là một ứng dụng console tự chứa mà bạn có thể biên dịch và chạy ngay lập tức.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Kết quả console dự kiến** (khi DOCX tham chiếu một phông chữ thiếu):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Nếu một phông chữ *quan trọng* như “Times New Roman” bị thiếu, bạn sẽ thấy thông báo hủy thay vì tiếp tục.

---

## Câu hỏi thường gặp & Lưu ý

| Question | Answer |
|----------|--------|
| **Do I need to call `SetFontsFolder` to capture warnings?** | No. The warning event works with the default system fonts. Use `SetFontsFolder` only when you want to provide extra fallback fonts. |
| **Will this work on .NET Core / .NET 5+?** | Absolutely. Aspose.Words 24.10 supports all modern .NET runtimes. Just ensure the NuGet package matches your target framework. |
| **What if I want to log warnings to a file instead of console?** | Replace `Console.WriteLine(msg);` with any logging framework call, e.g., `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Can I suppress warnings for specific fonts?** | Yes. Inside the event handler you can filter: `if (e.FontName == "SomeFont") return;`. This gives fine‑grained control. |
| **Is there a way to treat missing fonts as errors?** | Throw an exception manually inside the handler when a condition is met, or set a flag and abort after `Document` construction as shown in the example. |

---

## Kết luận

Bạn giờ đã có một mẫu vững chắc, sẵn sàng cho môi trường production để **cách ghi nhận cảnh báo** xảy ra khi tải tài liệu có phông chữ thiếu. Bằng cách **phát hiện phông chữ thiếu**, **cấu hình cài đặt phông chữ**, và **đặt tùy chọn tải** một cách thích hợp, bạn sẽ có toàn bộ khả năng quan sát các sự kiện thay thế phông chữ và có thể quyết định ghi log, fallback, hoặc hủy.  

Hãy tiến tới bước tiếp theo bằng cách tích hợp logic này vào quy trình chuyển đổi PDF, thêm phông chữ fallback tùy chỉnh, hoặc đưa danh sách cảnh báo vào hệ thống giám sát. Cách tiếp cận này mở rộng từ các tiện ích nhỏ đến dịch vụ xử lý tài liệu cấp doanh nghiệp.

### Đọc thêm & Các bước tiếp theo

- **Explore more FontSettings features** – embedding custom fonts, controlling fallback order, and licensing considerations.  
- **Combine with PDF conversion** – after capturing warnings, call `doc.Save("output.pdf");` and verify that the PDF uses the expected fonts.  
- **Automate testing** – write unit tests that load documents with known missing fonts and assert that the warning list contains the expected messages.  

Nếu bạn gặp bất kỳ khó khăn nào hoặc có ý tưởng cải tiến, đừng ngần ngại để lại bình luận. Chúc bạn lập trình vui!  

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}