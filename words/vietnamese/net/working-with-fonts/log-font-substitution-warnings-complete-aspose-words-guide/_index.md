---
category: general
date: 2026-01-14
description: Ghi lại cảnh báo thay thế phông chữ khi tải tài liệu Word bằng Aspose.Words.
  Tìm hiểu cách phát hiện phông chữ thiếu và cách ghi lại các phông chữ thiếu trong
  C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: vi
og_description: Ghi lại cảnh báo thay thế phông chữ khi tải tài liệu Word bằng Aspose.Words.
  Khám phá cách phát hiện phông chữ thiếu và ghi lại các phông chữ thiếu trong C#.
og_title: Ghi lại Cảnh báo Thay thế Phông chữ – Hướng dẫn Toàn diện Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Ghi nhật ký Cảnh báo Thay thế Phông chữ – Hướng dẫn Toàn diện Aspose.Words
url: /vi/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Log Font Substitution Warnings – Complete Aspose.Words Guide

Ghi lại các cảnh báo thay thế phông chữ là điều cần thiết khi bạn muốn đảm bảo tài liệu Word hiển thị chính xác như khi nó được tải bởi Aspose.Words. Nếu bạn từng tự hỏi **cách phát hiện phông chữ thiếu** hoặc muốn biết **cách ghi lại các phông chữ thiếu**, bạn đang ở đúng chỗ.  

Trong hướng dẫn này, chúng tôi sẽ đi qua một kịch bản thực tế, trình bày toàn bộ mã C#, và giải thích lý do mỗi dòng quan trọng. Khi kết thúc, bạn sẽ có thể ghi lại mọi sự kiện thay thế phông chữ và xử lý chúng—không còn cảnh báo bí ẩn nào nữa.

![Log font substitution warnings example](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## What You’ll Learn

- Cách cấu hình `LoadOptions` để Aspose.Words đưa ra các cảnh báo có kiểu cho việc thay thế phông chữ.  
- Các bước chính xác để **phát hiện phông chữ thiếu** trong quá trình tải tài liệu.  
- Một cách sạch sẽ để **ghi lại các phông chữ thiếu** và ghi chúng vào log hoặc hệ thống giám sát của bạn.  
- Xử lý các trường hợp đặc biệt (ví dụ: khi tài liệu chứa một phông chữ chưa được cài đặt trên máy chủ).  

### Prerequisites

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+).  
- Giấy phép Aspose.Words for .NET hợp lệ (hoặc bản dùng thử miễn phí).  
- Kiến thức cơ bản về C# và ứng dụng console.  

Nếu bạn đã có những điều trên, hãy bắt đầu.

## Step 1 – Set Up LoadOptions to Raise Typed Warnings

Trọng tâm của giải pháp nằm ở `LoadOptions.FontSubstitutionWarning`. Bằng cách chuyển nó sang `RaiseTypedWarnings` bạn nói với Aspose.Words rằng mỗi khi không tìm thấy phông chữ chính xác mà bạn yêu cầu, nó sẽ kích hoạt một sự kiện.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Why this matters:**  
> Hành vi mặc định sẽ âm thầm thay thế phông chữ thiếu bằng phông chữ gần nhất, điều này có thể gây ra các lỗi bố cục bạn không nhận ra. Việc đưa ra các cảnh báo có kiểu giúp bạn có đầy đủ khả năng quan sát.

## Step 2 – Subscribe to the Warning Event

Bây giờ chúng ta gắn hàm xử lý vào `loadOptions.FontSubstitutionWarning`. Lambda nhận một đối tượng `e` cho biết chính xác phông chữ nào bị thiếu và phông chữ nào đã được dùng thay thế.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Pro tip:** Nếu bạn chạy trên máy chủ web, thay `Console.WriteLine` bằng một logger có cấu trúc (Serilog, NLog, v.v.) để có thể truy vấn dữ liệu sau này.

## Step 3 – Load the Document Using the Configured Options

Với cơ chế cảnh báo đã được thiết lập, chỉ cần tải tài liệu như bình thường. Sự kiện sẽ tự động được kích hoạt cho mỗi phông chữ thiếu.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Expected Console Output

Nếu `input.docx` tham chiếu một phông chữ tên *MyFancyFont* mà không được cài đặt, bạn sẽ thấy:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Mỗi dòng tương ứng với một sự kiện **detect missing fonts**, cung cấp cho bạn một chuỗi kiểm tra đầy đủ.

## Step 4 – Handling Edge Cases and Advanced Scenarios

### 4.1 When No Substitution Happens

Đôi khi tài liệu chỉ sử dụng các phông chữ hệ thống đã có sẵn. Trong trường hợp này, sự kiện cảnh báo sẽ không bao giờ được kích hoạt và console sẽ sạch sẽ không có đầu ra. Đó là dấu hiệu tốt—môi trường của bạn đã có đầy đủ các phông chữ cần thiết.

### 4.2 Capturing Warnings for Later Analysis

Nếu bạn cần lưu trữ các cảnh báo để báo cáo hàng đêm, hãy thu thập chúng vào một danh sách:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Sau khi tải, bạn có thể serialize `missingFonts` thành JSON, ghi vào cơ sở dữ liệu, hoặc gửi email tóm tắt.

### 4.3 Working with PDFs or Other Formats

Cách tiếp cận `LoadOptions` tương tự cũng hoạt động cho các lệnh `Load` trên PDF, RTF và thậm chí HTML. Chỉ cần truyền cùng một đối tượng options, và Aspose.Words sẽ đưa ra cảnh báo cho bất kỳ phông chữ nào không khớp.

## Step 5 – Verify the Result Programmatically

Nếu bạn muốn một kiểm thử tự động thay vì nhìn vào console, hãy xác nhận rằng danh sách chứa các mục mong đợi:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Đoạn mã này minh họa **cách ghi lại các phông chữ thiếu** trong code, không chỉ trong log.

## Common Pitfalls & How to Avoid Them

| Pitfall | Why it Happens | Fix |
|---------|----------------|-----|
| Forgetting to set `RaiseTypedWarnings` | The default is `DoNotRaise`, so no events fire. | Explicitly set `FontSubstitutionWarning` as shown in Step 1. |
| Using `Console.WriteLine` in a web app | Console output disappears in IIS/ASP.NET Core. | Switch to a persistent logger (e.g., Serilog). |
| Loading a document with a relative path | The working directory may differ at runtime. | Use absolute paths or `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignoring the `SubstitutedFontName` | You lose insight into which fallback was chosen. | Always log both `FontName` and `SubstitutedFontName`. |

## Bonus: Automating Font Installation

Nếu bạn kiểm soát môi trường triển khai, có thể cài đặt trước các phông chữ thiếu bằng một script PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Chạy script này trước khi ứng dụng khởi động sẽ loại bỏ hầu hết các cảnh báo **detect missing fonts**.

## Conclusion

Chúng ta đã bao quát mọi thứ cần thiết để **log font substitution warnings** khi tải tài liệu Word bằng Aspose.Words. Bằng cách cấu hình `LoadOptions`, đăng ký sự kiện cảnh báo, và tùy chọn lưu trữ kết quả, bạn có thể đáng tin cậy **detect missing fonts** và hiểu **how to capture missing fonts** cho bất kỳ dự án .NET nào.

Hãy lấy mã, điều chỉnh logger cho phù hợp với stack của bạn, và bạn sẽ không còn bất ngờ với việc thay thế phông chữ âm thầm nữa. Các bước tiếp theo có thể bao gồm:

- Tích hợp danh sách cảnh báo vào pipeline CI/CD để ngăn build khi các phông chữ quan trọng bị thiếu.  
- Mở rộng cách tiếp cận để giám sát việc sử dụng phông chữ trên một tập hợp lớn tài liệu.  
- Khám phá API `FontSettings` của Aspose.Words để cung cấp các phông chữ dự phòng tùy chỉnh.

Có câu hỏi hoặc kịch bản khó khăn? Để lại bình luận, chúng ta sẽ cùng giải quyết. Chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}