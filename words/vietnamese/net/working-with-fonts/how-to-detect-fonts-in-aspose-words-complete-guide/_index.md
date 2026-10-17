---
category: general
date: 2026-04-07
description: Học cách phát hiện phông chữ và ghi lại cảnh báo khi xử lý phông chữ
  thiếu trong C# bằng Aspose.Words. Bao gồm mã mẫu từng bước.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: vi
og_description: Cách phát hiện phông chữ trong Aspose.Words? Hãy theo dõi hướng dẫn
  này để ghi lại cảnh báo và xử lý các phông chữ thiếu một cách dễ dàng.
og_title: Cách phát hiện phông chữ trong Aspose.Words – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Font handling
title: Cách phát hiện phông chữ trong Aspose.Words – Hướng dẫn đầy đủ
url: /vi/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Phát Hiện Phông Chữ trong Aspose.Words – Hướng Dẫn Toàn Diện

Bạn đã bao giờ tự hỏi **cách phát hiện phông chữ** bị thiếu trong tài liệu Word trước khi đưa vào sản xuất chưa? Bạn không phải là người duy nhất. Trong nhiều kịch bản doanh nghiệp, một phông chữ lạc lõng có thể làm hỏng quy trình chuyển đổi PDF hoặc gây ra các lỗi bố cục trông không chuyên nghiệp. Tin tốt là Aspose.Words cung cấp cho bạn một cách tích hợp để phát hiện những kiểu chữ thiếu và hiển thị cảnh báo rõ ràng.

Trong hướng dẫn này, chúng ta sẽ đi qua chi tiết **cách phát hiện phông chữ**, **cách thu thập cảnh báo**, và các thực tiễn tốt nhất để **xử lý phông chữ thiếu** nhằm giữ cho ứng dụng của bạn luôn ổn định. Không cần công cụ bên ngoài, không cần đoán mò—chỉ cần mã C# thuần túy mà bạn có thể chèn vào dự án ngay lập tức.

> **Xem nhanh:** Khi kết thúc, bạn sẽ có một `FontSubstitutionWarningCollector` có thể tái sử dụng, thu thập mọi thông báo thay thế phông chữ trong quá trình tải tài liệu, và bạn sẽ biết cách phản hồi khi không tìm thấy một phông chữ.

---

## Những Điều Bạn Sẽ Học

- Cách cấu hình `LoadOptions` để lắng nghe các cảnh báo thay thế phông chữ.  
- Cách thu thập các cảnh báo đó trong một lớp collector tùy chỉnh.  
- Cách xử lý các cảnh báo đã thu thập và quyết định có nên hủy, ghi log, hay thay thế phông chữ.  
- Xử lý các trường hợp đặc biệt cho tài liệu tham chiếu phông chữ từ xa hoặc nhúng.  

**Yêu cầu trước:** .NET 6+ (hoặc .NET Framework 4.6+), Aspose.Words cho .NET (phiên bản mới nhất), và kiến thức cơ bản về C#. Nếu bạn chưa từng sử dụng Aspose.Words, đừng lo—hướng dẫn này chỉ yêu cầu vài phút thiết lập.

## Cách Phát Hiện Phông Chữ Sử Dụng Aspose.Words LoadOptions

Bước đầu tiên để phát hiện phông chữ bị thiếu là yêu cầu Aspose.Words báo cáo chúng. Điều này được thực hiện qua thuộc tính `LoadOptions.WarningCallback`, cho phép bất kỳ lớp nào triển khai `IWarningCallback`. Dưới đây chúng ta tạo một collector nhỏ để lưu trữ mọi cảnh báo để kiểm tra sau.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Tại sao điều này quan trọng:** Nếu không có callback cảnh báo, Aspose.Words sẽ im lặng thay thế phông chữ thiếu bằng phông mặc định, và bạn sẽ không biết có vấn đề. Bằng cách bắt `WarningType.FontSubstitution` chúng ta có được toàn bộ thông tin—đúng là dữ liệu bạn cần để **phát hiện phông chữ** không có trên máy chủ.

Bây giờ chúng ta gắn collector vào `LoadOptions` và tải một tài liệu:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Mẹo chuyên nghiệp:** Nếu bạn làm việc với nhiều tài liệu trong một batch, hãy tái sử dụng cùng một thể hiện `FontSubstitutionWarningCollector` nhưng nhớ gọi `Clear()` giữa các lần tải để tránh trộn lẫn các cảnh báo từ các tệp khác nhau.

## Thu Thập Cảnh Báo Khi Tải Tài Liệu

Sau khi tài liệu được tải, collector đã chứa mọi cảnh báo liên quan đến phông chữ. Câu hỏi tiếp theo hợp lý là: *Làm sao tôi có thể thu thập các cảnh báo* một cách dễ dàng để ghi log hoặc hiển thị?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

Kết quả thường thấy như sau:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Điều này cho bạn biết:** Mỗi dòng hiển thị tên phông chữ gốc và phông thay thế mà Aspose.Words đã chọn. Với thông tin này, bạn có thể quyết định liệu phông thay thế có chấp nhận được hay bạn cần nhúng phông chữ thiếu một cách thủ công.

## Xử Lý Phông Chữ Thiếu Một Cách Trơn Truột

Phát hiện và thu thập cảnh báo chỉ là một nửa cuộc chiến. Giá trị thực sự đến khi bạn **xử lý phông chữ thiếu** một cách sẵn sàng cho môi trường sản xuất. Dưới đây là ba chiến lược phổ biến:

1. **Log và Tiếp Tục** – Thích hợp cho xử lý batch nơi bạn chỉ cần một bản ghi audit.  
2. **Hủy Khi Phông Chữ Quan Trọng Thiếu** – Ném ngoại lệ nếu một phông chữ cụ thể (ví dụ: phông chữ thương hiệu) bị thiếu.  
3. **Nhúng Phông Chữ Trực Tiếp** – Tải phông chữ thiếu từ thư mục đã biết và đăng ký nó với Aspose.Words trước khi tải lại tài liệu.

### Ví dụ: Hủy Khi Phông Chữ Quan Trọng Thiếu

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Ví dụ: Tự Động Nhúng Phông Chữ Thiếu

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Tại sao các mẫu này hữu ích:** Bằng cách quyết định rõ ràng hành động khi một phông chữ thiếu, bạn loại bỏ các fallback im lặng có thể ảnh hưởng đến thương hiệu hoặc khả năng đọc. Đây là bản chất của **việc xử lý phông chữ thiếu** một cách kiểm soát.

## Ví Dụ Hoàn Chỉnh Hoạt Động

Kết hợp mọi thứ lại, đây là một chương trình duy nhất, sẵn sàng chạy, minh họa **cách phát hiện phông chữ**, **cách thu thập cảnh báo**, và một chính sách đơn giản để **xử lý phông chữ thiếu** bằng cách ghi log.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Kết quả mong đợi:** Khi bạn chạy chương trình với một tài liệu tham chiếu phông chữ không có trên máy, console sẽ liệt kê mỗi cảnh báo thay thế. Nếu bất kỳ cảnh báo nào liên quan đến phông chữ trong tập `critical`, chương trình sẽ kết thúc sớm, ngăn ngừa việc tạo PDF lỗi.

## Câu Hỏi Thường Gặp (FAQs)

| Question | Answer |
|----------|--------|
| *Tôi có cần giấy phép cho Aspose.Words để sử dụng đoạn mã này không?* | Có, giấy phép Aspose.Words hợp lệ sẽ loại bỏ watermark đánh giá và mở khóa toàn bộ chức năng. |
| *Phương pháp này có thể phát hiện phông chữ được nhúng không?* | Phông chữ được nhúng đã có trong tệp, vì vậy Aspose.Words sẽ không đưa ra cảnh báo thay thế. Bạn có thể kiểm tra `Document.FontInfos` để liệt kê các phông chữ nhúng nếu cần. |
| *Nếu phông chữ thiếu là phông chữ hệ thống trên Windows nhưng không có trên Linux thì sao?* | Cảnh báo tương tự sẽ xuất hiện trên Linux vì phông chữ không được cài đặt ở đó. Hãy sử dụng chiến lược “xử lý phông chữ thiếu” để cung cấp các tệp `.ttf` cần thiết cùng với ứng dụng của bạn. |
| *Bộ thu thập cảnh báo có phải là đa luồng không* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}