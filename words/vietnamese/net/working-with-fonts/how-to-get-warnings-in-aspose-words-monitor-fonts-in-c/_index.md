---
category: general
date: 2026-01-06
description: Tìm hiểu cách nhận cảnh báo khi tải tài liệu và cách giám sát phông chữ
  bằng Aspose.Words. Hướng dẫn này bao gồm các callback cảnh báo và việc theo dõi
  thay thế phông chữ.
draft: false
keywords:
- how to get warnings
- how to monitor fonts
- Aspose.Words warning callback
- font substitution detection
- document load options
language: vi
og_description: Cách nhận cảnh báo trong Aspose.Words? Hãy làm theo hướng dẫn từng
  bước này để giám sát phông chữ và ghi lại các thông báo thay thế khi tải tài liệu.
og_title: Cách nhận cảnh báo trong Aspose.Words – Giám sát phông chữ
tags:
- Aspose.Words
- C#
- Font Monitoring
title: Cách nhận cảnh báo trong Aspose.Words – Giám sát phông chữ trong C#
url: /vi/net/working-with-fonts/how-to-get-warnings-in-aspose-words-monitor-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách nhận cảnh báo trong Aspose.Words – Giám sát phông chữ trong C#

Bạn có bao giờ tự hỏi **cách nhận cảnh báo** khi một tài liệu Word chứa các phông chữ mà bạn không cài đặt không? Đó là một vấn đề phổ biến—ứng dụng của bạn âm thầm thay thế các phông chữ thiếu, và bạn không bao giờ biết điều gì đã thay đổi. Tin tốt là bạn có thể kết nối vào hệ thống cảnh báo của Aspose.Words và **giám sát phông chữ** theo thời gian thực.

Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách chính xác để bắt các cảnh báo thay thế phông chữ, lý do tại sao chúng quan trọng, và cách xử lý thông tin khi đã có. Không cần tài liệu bên ngoài, chỉ một ví dụ hoàn chỉnh, có thể chạy được mà bạn có thể dán vào Visual Studio ngay lập tức.

> **Mẹo:** Nếu bạn đang xây dựng một quy trình chuyển đổi tài liệu, việc ghi lại các phông chữ thiếu sớm sẽ giúp bạn tránh những bất ngờ về bố cục không mong muốn ở các bước sau.

## Những gì bạn cần

- **Aspose.Words for .NET** (phiên bản mới nhất; API chưa thay đổi kể từ v23.10)
- Môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code với phần mở rộng C#)
- Một tệp mẫu `.docx` tham chiếu tới một phông chữ mà bạn chưa cài đặt (ví dụ, **“NonExistentFont”**)

Chỉ vậy—không cần gói NuGet bổ sung nào ngoài Aspose.Words.

## Bước 1 – Thiết lập bộ thu thập cảnh báo (Từ khóa chính trong tiêu đề)

Điều đầu tiên bạn cần là một nơi để lưu trữ các cảnh báo khi chúng xảy ra. Aspose.Words cung cấp thuộc tính `WarningCallback` trên `LoadOptions` cho mục đích này.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

// Create a collection that will receive every warning emitted during load.
WarningInfoCollection warningCollector = new WarningInfoCollection();

// Attach the collector to LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = warningCollector
};
```

**Tại sao điều này quan trọng:**  
Khi thư viện gặp phải một phông chữ thiếu, nó không ném ra ngoại lệ; nó phát ra một đối tượng `WarningInfo`. Bằng cách kết nối một bộ thu thập, bạn có được khả năng quan sát toàn bộ các sự kiện thay thế, cho phép bạn **giám sát phông chữ** mà không làm bẩn console bằng các tin nhắn không liên quan.

## Bước 2 – Tải tài liệu với các tùy chọn bật cảnh báo

Bây giờ chúng ta thực sự đọc tệp. `LoadOptions` mà chúng ta chuẩn bị ở bước trước sẽ đảm bảo mọi cảnh báo liên quan đến phông chữ được ghi lại.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\unknownFont.docx";

Document doc = new Document(docPath, loadOptions);
```

**Đi gì đang diễn ra bên trong?**  
Aspose.Words phân tích tệp Word, xác định phông chữ, và bất cứ khi nào không tìm thấy phông chữ được yêu cầu, nó sẽ chuyển sang một phông chữ thay thế (thường là Arial). Việc chuyển đổi này kích hoạt một cảnh báo `WarningType.FontSubstitution`, và nó sẽ được đưa vào `warningCollector`.

## Bước 3 – Kiểm tra các cảnh báo đã thu thập (Từ khóa chính xuất hiện lại)

Sau khi tài liệu được tải, chúng ta chỉ cần lặp qua `warningCollector` và in ra bất kỳ thông báo thay thế phông chữ nào.

```csharp
foreach (WarningInfo warning in warningCollector)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        // The Description contains a readable message like:
        // "Font 'NonExistentFont' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warning.Description}");
    }
}
```

**Kết quả mong đợi** (giả sử phông chữ thiếu là *“FancyScript”*):

```
Substituted font: Font 'FancyScript' was not found. Substituted with 'Arial'.
```

Nếu tài liệu chứa nhiều phông chữ không xác định, bạn sẽ thấy một dòng cho mỗi lần thay thế—rất phù hợp cho việc ghi log hoặc cảnh báo.

## Bước 4 – Tùy chọn: Ghi log hoặc lưu trữ thông tin cảnh báo

Trong môi trường production, bạn có thể muốn hơn một `Console.WriteLine`. Dưới đây là một ví dụ nhanh ghi các cảnh báo vào tệp JSON để phân tích sau.

```csharp
using System.IO;
using System.Text.Json;

// Build a simple DTO.
var warnings = warningCollector
    .Where(w => w.WarningType == WarningType.FontSubstitution)
    .Select(w => new { FontMessage = w.Description })
    .ToList();

string json = JsonSerializer.Serialize(warnings, new JsonSerializerOptions { WriteIndented = true });
File.WriteAllText(@"C:\Logs\font-warnings.json", json);

Console.WriteLine("Font warnings saved to font-warnings.json");
```

Bây giờ bạn có một bản ghi vĩnh viễn mà bạn có thể đưa vào bảng điều khiển giám sát, hoặc thậm chí kích hoạt một yêu cầu tự động cho các tệp phông chữ thiếu.

## Bước 5 – Xác minh kết quả và dọn dẹp

Chạy chương trình. Nếu bạn thấy các thông báo thay thế, bạn đã thành công **nhận được cảnh báo** và hiện đang **giám sát phông chữ**. Nếu không có gì xuất hiện, hãy kiểm tra lại xem tài liệu thử nghiệm thực sự tham chiếu tới một phông chữ chưa được cài đặt trên máy hay không.

```csharp
// Quick sanity check – print the total number of warnings captured.
Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
```

Số lượng bằng không thường có nghĩa là một trong hai:

1. Tất cả các phông chữ đã được giải quyết (có thể phông chữ *đã* được cài đặt cục bộ), hoặc
2. Tài liệu không chứa bất kỳ tham chiếu phông chữ nào cần thay thế.

## Những bẫy thường gặp & Cách tránh chúng

| Pitfall | Why It Happens | Fix |
|---------|----------------|-----|
| **Không có cảnh báo nào xuất hiện** | Phông chữ thực tế đã tồn tại trên hệ thống, hoặc tài liệu chỉ sử dụng các phông chữ tích hợp sẵn. | Đổi tên phông chữ trong tệp nguồn thành một tên không thể tồn tại (ví dụ, `XYZ123`) và thử lại. |
| **Quá nhiều cảnh báo (nhiễu)** | Bạn đang tải nhiều tài liệu trong vòng lặp mà không xóa bộ thu thập. | Tạo lại `WarningInfoCollection` cho mỗi tài liệu, hoặc gọi `warningCollector.Clear()` sau khi xử lý. |
| **Ảnh hưởng đến hiệu năng** | Ghi log quá mức vào đĩa có thể làm chậm quá trình xử lý hàng loạt. | Lưu các cảnh báo trong bộ nhớ và ghi chúng hàng loạt, hoặc sử dụng I/O bất đồng bộ. |
| **Thiếu `using Aspose.Words.Loading;`** | `LoadOptions` nằm trong không gian tên này. | Thêm chỉ thị `using` bị thiếu, như đã trình bày ở Bước 1. |

## Mở rộng giải pháp – Giám sát các loại cảnh báo khác

Mặc dù thay thế phông chữ là dễ thấy nhất, Aspose.Words có thể phát ra cảnh báo cho:

- **Tính năng đã lỗi thời** (`WarningType.Deprecated`),
- **Rủi ro mất dữ liệu** (`WarningType.DataLoss`),
- **Định dạng tệp không được hỗ trợ** (`WarningType.UnsupportedFileFormat`).

Bạn có thể mở rộng bộ lọc ở Bước 3 để bắt các cảnh báo này nữa:

```csharp
if (warning.WarningType != WarningType.None)
{
    Console.WriteLine($"{warning.WarningType}: {warning.Description}");
}
```

Bằng cách đó, bạn không chỉ **giám sát phông chữ** mà còn **nhận cảnh báo** cho bất kỳ tình huống nào mà ứng dụng của bạn có thể gặp.

## Ví dụ đầy đủ hoạt động (Sẵn sàng sao chép‑dán)

```csharp
using System;
using System.IO;
using System.Linq;
using System.Text.Json;
using Aspose.Words;
using Aspose.Words.Fonts;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // Step 1 – Prepare a warning collector.
        WarningInfoCollection warningCollector = new WarningInfoCollection();
        LoadOptions loadOptions = new LoadOptions { WarningCallback = warningCollector };

        // Step 2 – Load the document (adjust the path to your file).
        string docPath = @"C:\Docs\unknownFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // Step 3 – Output font substitution warnings.
        foreach (WarningInfo warning in warningCollector)
        {
            if (warning.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Substituted font: {warning.Description}");
            }
        }

        // Optional Step 4 – Persist warnings to JSON.
        var fontWarnings = warningCollector
            .Where(w => w.WarningType == WarningType.FontSubstitution)
            .Select(w => new { Message = w.Description })
            .ToList();

        string json = JsonSerializer.Serialize(fontWarnings, new JsonSerializerOptions { WriteIndented = true });
        File.WriteAllText(@"C:\Logs\font-warnings.json", json);
        Console.WriteLine("Font warnings saved to font-warnings.json");

        // Step 5 – Quick sanity check.
        Console.WriteLine($"Total warnings captured: {warningCollector.Count}");
    }
}
```

**Chạy nó:** Xây dựng dự án, thực thi, và bạn sẽ thấy các cảnh báo được in ra và lưu lại. Đó là câu trả lời đầy đủ cho **cách nhận cảnh báo** và **cách giám sát phông chữ** với Aspose.Words.

## Kết luận

Bây giờ bạn đã biết **cách nhận cảnh báo** từ Aspose.Words, đặc biệt cho các trường hợp thay thế phông chữ, và bạn đã học **cách giám sát phông chữ** trong suốt quá trình tải tài liệu. Bằng cách gắn `WarningCallback`, lặp qua các đối tượng `WarningInfo` đã thu thập, và tùy chọn lưu trữ dữ liệu, bạn có được sự trong suốt hoàn toàn về các sự kiện phông chữ thiếu—một khả năng thiết yếu cho bất kỳ quy trình xử lý tài liệu nào.

Bước tiếp theo? Hãy thử mở rộng bộ lọc cảnh báo để bao phủ các cảnh báo mất dữ liệu hoặc tính năng đã lỗi thời, hoặc tích hợp log JSON vào bảng điều khiển giám sát như Grafana. Mẫu này hoạt động cho mọi loại cảnh báo, vì vậy bạn sẽ sẵn sàng theo dõi bất kỳ vấn đề nào mà Aspose.Words đưa ra.

Chúc lập trình vui vẻ, và hy vọng tài liệu của bạn luôn hiển thị chính xác như mong đợi! 

<img src="font-warnings.png" alt="cách nhận cảnh báo trong Aspose.Words" style="max-width:100%;">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}