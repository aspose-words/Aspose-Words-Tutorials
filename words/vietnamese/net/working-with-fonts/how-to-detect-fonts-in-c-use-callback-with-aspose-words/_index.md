---
category: general
date: 2026-03-17
description: Cách phát hiện phông chữ trong C# bằng Aspose.Words và callback cảnh
  báo. Tìm hiểu cách sử dụng callback để ghi lại các thay thế phông chữ bị thiếu khi
  tải tài liệu.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: vi
og_description: Cách phát hiện phông chữ trong C# bằng Aspose.Words. Hướng dẫn này
  cho thấy cách sử dụng callback để ghi lại các cảnh báo thiếu phông chữ khi tải tài
  liệu.
og_title: Cách phát hiện phông chữ trong C# – Sử dụng Callback với Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Cách phát hiện phông chữ trong C# – Sử dụng Callback với Aspose.Words
url: /vi/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

formatting, code block placeholders unchanged.

Let's craft final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách phát hiện phông chữ trong C# – Sử dụng Callback với Aspose.Words

Bạn đã bao giờ cần **cách phát hiện phông chữ** trong một tài liệu Word một cách lập trình và tự hỏi tại sao một số ký tự trông lạ sau khi chuyển đổi không? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế—công cụ tạo hoá đơn, xuất báo cáo, hoặc các pipeline xử lý hàng loạt—các phông chữ thiếu gây ra các lỗi bố cục im lặng khó debug.  

Tin tốt? Aspose.Words cung cấp cho bạn một cách sạch sẽ để hiển thị những vấn đề đó bằng một warning callback. Trong hướng dẫn này, bạn sẽ thấy **cách sử dụng callback** để ghi lại mọi việc thay thế phông chữ mà Aspose thực hiện khi tải tài liệu, và bạn sẽ có một ví dụ sẵn sàng chạy, in ra báo cáo rõ ràng về các phông chữ bị thiếu.

Chúng tôi sẽ đề cập tới:

* Các yêu cầu tối thiểu (một dự án .NET và gói NuGet Aspose.Words).  
* Cách triển khai `IWarningCallback` để lắng nghe `WarningType.FontSubstitution`.  
* Cách gắn callback vào `LoadOptions` và tải một tài liệu.  
* Kết quả đầu ra trông như thế nào, cùng một vài mẹo thực tiễn cho mã sản xuất.

Khi hoàn thành, bạn sẽ có thể tự động **phát hiện phông chữ** trong bất kỳ tệp DOCX, DOC, hoặc RTF nào và xử lý thông tin phông chữ thiếu—cho dù điều đó có nghĩa là ghi log, cảnh báo người dùng, hoặc thay thế bằng phông chữ dự phòng.

---

![Cách phát hiện phông chữ trong tài liệu Word bằng Aspose.Words warning callback](https://example.com/images/detect-fonts.png "cách phát hiện phông chữ trong tài liệu Word")

## Những gì bạn cần

* **.NET 6.0** trở lên (ví dụ biên dịch được với .NET Framework 4.6+).  
* **Aspose.Words for .NET** – cài đặt qua NuGet: `Install-Package Aspose.Words`.  
* Một tệp Word mẫu cố tình tham chiếu tới một phông chữ bạn không có trên máy (ví dụ, `MissingFont.docx`).  

Không cần thư viện bổ sung nào; mọi thứ đều nằm trong không gian tên Aspose.

---

## Cách phát hiện phông chữ bằng Warning Callback

### Bước 1: Tạo lớp warning‑callback

Lớp callback triển khai `IWarningCallback`. Khi Aspose.Words gặp một phông chữ không tìm thấy, nó sẽ tạo ra một `WarningInfo` với `WarningType.FontSubstitution`. Lớp của chúng ta chỉ đơn giản ghi một dòng thân thiện ra console.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Tại sao điều này quan trọng:** Bằng cách lọc trên `WarningType.FontSubstitution` chúng ta tránh được các cảnh báo ồn ào (như tính năng đã lỗi thời) và giữ log tập trung vào vấn đề chính bạn đang muốn giải quyết—**phát hiện phông chữ** không có trên máy.

---

### Bước 2: Gắn callback vào `LoadOptions`

`LoadOptions` cho phép bạn tùy chỉnh cách tài liệu được phân tích. Gán `FontWarningCollector` của chúng ta vào thuộc tính `WarningCallback` sẽ khiến Aspose gọi nó mỗi khi gặp phông chữ bị thiếu.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Mẹo:** Bạn cũng có thể đặt `LoadOptions.FontSettings` ở đây nếu muốn cung cấp một phông chữ dự phòng một cách lập trình. Đó là một kịch bản nâng cao mà chúng tôi sẽ đề cập sau.

---

### Bước 3: Tải tài liệu và quan sát đầu ra

Bây giờ chúng ta thực sự tải tệp. Ngay khi Aspose phân tích tài liệu, bất kỳ phông chữ nào không thể định vị sẽ kích hoạt callback của chúng ta.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Kết quả console dự kiến** (giả sử tài liệu tham chiếu *Comic Sans MS* mà không được cài đặt):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Nếu tài liệu chứa nhiều phông chữ bị thiếu, bạn sẽ thấy một dòng cho mỗi phông chữ—đúng là thông tin **cách phát hiện phông chữ** mà bạn cần.

---

## Cách sử dụng Callback cho các kịch bản phức tạp hơn

### Ghi log vào tệp thay vì console

Trong môi trường sản xuất bạn có thể muốn một log bền vững. Thay `Console.WriteLine` bằng một `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Thu thập cảnh báo để phân tích sau

Đôi khi bạn cần danh sách các phông chữ bị thiếu sau khi tài liệu đã được tải, có thể để hiển thị một hộp thoại UI. Lưu các cảnh báo vào một `List<string>` và cung cấp nó:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Cung cấp phông chữ dự phòng một cách lập trình

Nếu bạn có một phông chữ công ty muốn áp dụng, bạn có thể thêm nó vào `FontSettings` trước khi tải:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Bây giờ Aspose sẽ thay thế các phông chữ bị thiếu bằng *Arial Unicode MS* đồng thời vẫn báo cáo việc thay thế qua callback. Đây là một cách hay để **cách sử dụng callback** cho cả phát hiện và khắc phục tự động.

---

## Các lỗi thường gặp và mẹo chuyên nghiệp

| Vấn đề | Nguyên nhân | Cách tránh |
|--------|-------------|------------|
| **Quên tham chiếu `Aspose.Words.Warnings`** | Giao diện `IWarningCallback` nằm trong không gian tên này. | Thêm `using Aspose.Words.Warnings;` ở đầu file. |
| **Tải tài liệu mà không có `LoadOptions`** | Trình tải mặc định sẽ thay thế phông chữ một cách im lặng mà không thông báo. | Luôn tạo một thể hiện `LoadOptions` và gán callback của bạn. |
| **Chạy trên server có quyền hạn hạn chế** | Việc ghi vào tệp log có thể gây `UnauthorizedAccessException`. | Sử dụng thư mục có quyền ghi (ví dụ, thư mục dữ liệu của ứng dụng) hoặc chỉ dùng các collection trong bộ nhớ. |
| **Nhiều luồng chia sẻ cùng một collector** | `FontWarningCollector` không an toàn với đa luồng theo mặc định. | Tạo một collector riêng cho mỗi luồng hoặc bảo vệ danh sách bằng lock. |
| **Giả định callback sẽ chạy cho phông chữ nhúng** | Phông chữ nhúng đã có trong tài liệu; không có cảnh báo nào được đưa ra. | Nếu cần kiểm tra tính toàn vẹn của phông chữ nhúng, hãy xem `FontInfo` qua `FontSettings`. |

---

## Ví dụ hoàn chỉnh (Sẵn sàng sao chép)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Kết quả bạn sẽ thấy** (giả sử tệp tham chiếu hai phông chữ không tồn tại):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Nếu tệp chỉ sử dụng các phông chữ đã được cài đặt, console sẽ chỉ in:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Kết luận

Chúng tôi đã hướng dẫn **cách phát hiện phông chữ** trong một tài liệu Word bằng cách gắn một warning callback tùy chỉnh vào Aspose.Words. Cách tiếp cận này nhẹ, yêu cầu

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}