---
category: general
date: 2026-04-04
description: Tìm hiểu cách ghi lại cảnh báo, phát hiện phông chữ thiếu và cách ghi
  nhật ký các sự kiện thay thế bằng Aspose.Words LoadOptions trong C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: vi
og_description: Cách ghi lại cảnh báo, phát hiện phông chữ thiếu và ghi nhật ký các
  sự kiện thay thế khi sử dụng Aspose.Words LoadOptions trong C#.
og_title: Cách bắt cảnh báo trong C# – Phát hiện phông chữ thiếu và ghi lại việc thay
  thế
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Cách bắt cảnh báo trong C# – Phát hiện phông chữ thiếu và ghi lại việc thay
  thế
url: /vi/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách bắt cảnh báo trong C# – Phát hiện phông chữ thiếu & Ghi lại việc thay thế

Bạn có bao giờ tự hỏi **cách bắt các cảnh báo** xuất hiện khi tải một tài liệu Word có phông chữ thiếu không? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế, phông chữ bị mất trong quá trình di chuyển, và việc tự động thay thế âm thầm có thể làm hỏng bố cục của bạn. Tin tốt là gì? Aspose.Words cung cấp cho bạn một cách sạch sẽ để lắng nghe các cảnh báo đó, phát hiện phông chữ thiếu, và thậm chí ghi lại mọi lần thay thế để bạn có thể sửa nguồn sau này.

Trong hướng dẫn này chúng tôi sẽ đi qua một giải pháp hoàn chỉnh, sẵn sàng chạy, cho thấy **cách bắt các cảnh báo**, minh họa **phát hiện phông chữ thiếu**, và giải thích **cách ghi lại các sự kiện thay thế**. Khi kết thúc, bạn sẽ có một bộ xử lý cảnh báo có thể tái sử dụng, một đối tượng `LoadOptions` được cấu hình đầy đủ, và một mẫu đầu ra console để bạn kiểm chứng.

> **Yêu cầu trước:** Bạn cần cài đặt Aspose.Words for .NET (v24.x trở lên) qua NuGet và có môi trường phát triển C# cơ bản (Visual Studio 2022 hoặc VS Code đều ổn).

---

## Cách bắt cảnh báo khi tải tài liệu

Cốt lõi của giải pháp là một lớp triển khai `IWarningCallback`. Aspose.Words sẽ tự động gọi callback này cho mọi cảnh báo được tạo ra trong quá trình tải tài liệu, bao gồm cả cảnh báo thay thế phông chữ.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Tại sao cần bước này?**  
> Bằng cách lọc trên `WarningType.FontSubstitution` chúng ta tránh được sự lộn xộn từ các cảnh báo không liên quan (như tính năng đã lỗi thời). Điều này giúp log tập trung vào vấn đề chính mà bạn quan tâm — phông chữ thiếu.

---

## Phát hiện phông chữ thiếu với Aspose.Words

Khi một tài liệu tham chiếu một phông chữ chưa được cài đặt trên máy, Aspose.Words sẽ thay thế bằng phông chữ gần nhất và đưa ra cảnh báo. Bộ xử lý ở trên sẽ bắt mỗi lần xảy ra, thực tế **phát hiện phông chữ thiếu**.

Để xem nó hoạt động, chúng ta cần cấu hình `LoadOptions` và gắn bộ xử lý:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Mẹo:** Nếu bạn muốn thu thập các cảnh báo để xử lý sau (ví dụ: ghi vào file), hãy thay `Console.WriteLine` bằng mã thêm thông điệp vào một `List<string>`.

---

## Cách ghi lại các sự kiện thay thế

Ghi log chỉ đơn giản là chuyển đầu ra cảnh báo tới một nơi lưu trữ lâu dài. Dưới đây là một ví dụ nhanh ghi mỗi cảnh báo thay thế vào file văn bản có tên `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Tại sao ghi log vào file?**  
> Log lâu dài cho phép bạn kiểm tra các vấn đề phông chữ qua nhiều lần chạy, tự động cảnh báo, hoặc đưa dữ liệu vào quy trình kiểm tra trong pipeline xây dựng.

---

## Ví dụ hoàn chỉnh hoạt động

Kết hợp mọi thứ lại, đây là một ứng dụng console tự chứa mà bạn có thể sao chép, dán và chạy. Nó minh họa **cách bắt cảnh báo**, **phát hiện phông chữ thiếu**, và **cách ghi lại việc thay thế** trong một bước.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Đầu ra console dự kiến

Nếu `input.docx` tham chiếu một phông chữ chưa được cài đặt, bạn sẽ thấy điều gì đó như sau:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Nếu bạn chuyển sang `FileLoggingWarningHandler`, các dòng tương tự sẽ xuất hiện trong `font-warnings.log` kèm thời gian.

![cách bắt cảnh báo đầu ra console](image-placeholder.png)

---

## Câu hỏi thường gặp & Trường hợp đặc biệt

### Nếu tôi cần bắt *tất cả* cảnh báo, không chỉ thay thế phông chữ thì sao?

Chỉ cần xóa kiểm tra `if (info.Type == WarningType.FontSubstitution)`. Callback sẽ nhận mọi loại cảnh báo (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, v.v.). Bạn có thể dựa vào `info.Type` để xử lý từng trường hợp khác nhau.

### Điều này có hoạt động với PDF hay chỉ với tài liệu Word?

`LoadOptions` và `IWarningCallback` là một phần của Aspose.Words, vì vậy chúng áp dụng cho các định dạng tương thích Word (`.docx`, `.doc`, `.rtf`, `.html`). Đối với PDF, bạn sẽ sử dụng cơ chế cảnh báo riêng của Aspose.PDF.

### Làm sao để vô hiệu hoá cảnh báo thay vì ghi log?

Đặt `LoadOptions.WarningCallback = null` hoặc triển khai callback nhưng để phần thân phương thức trống. Thư viện vẫn sẽ thực hiện việc thay thế một cách im lặng.

### Về tính an toàn đa luồng thì sao?

Đối tượng callback được gọi trên cùng một luồng tải tài liệu, vì vậy bạn không cần đồng bộ bổ sung trừ khi chia sẻ bộ xử lý giữa các tải song song. Trong trường hợp đó, hãy bảo vệ các tài nguyên chung (ví dụ: file log) bằng một lock hoặc sử dụng các collection đồng thời.

---

## Kết luận

Chúng tôi đã trình bày **cách bắt cảnh báo** từ Aspose.Words, chỉ cho bạn **cách phát hiện phông chữ thiếu**, và giải thích **cách ghi lại các sự kiện thay thế** để phân tích sau. Bằng cách gắn một triển khai `IWarningCallback` đơn giản vào `LoadOptions`, bạn sẽ có tầm nhìn đầy đủ về các vấn đề liên quan tới phông chữ mà không làm rối mã nguồn.

Bước tiếp theo? Hãy mở rộng logger để gửi email, tích hợp với Azure Monitor, hoặc tự động cài đặt phông chữ thiếu trên máy build. Bạn cũng có thể khám phá các loại cảnh báo khác — `WarningType.DegradedDocument` có thể cảnh báo bạn về các tính năng không tồn tại sau quá trình chuyển đổi.

Có thêm câu hỏi về xử lý phông chữ hoặc Aspose.Words nói chung? Hãy để lại bình luận hoặc mở một issue mới trên diễn đàn Aspose. Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng kiểu chữ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}