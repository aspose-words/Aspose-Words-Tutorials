---
category: general
date: 2026-04-21
description: Tìm hiểu cách phát hiện phông chữ, ghi lại cảnh báo, cấu hình callback
  và liệt kê các cảnh báo với Aspose.Words trong C#. Hướng dẫn từng bước để xử lý
  phông chữ một cách đáng tin cậy.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: vi
og_description: Cách phát hiện phông chữ trong Aspose.Words? Hướng dẫn này cho bạn
  biết cách bắt các cảnh báo, cấu hình callback và liệt kê các cảnh báo trong C#.
og_title: Cách phát hiện phông chữ trong Aspose.Words – Hướng dẫn toàn diện
tags:
- Aspose.Words
- C#
- Document Processing
title: Cách phát hiện phông chữ trong Aspose.Words – Hướng dẫn đầy đủ
url: /vi/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách phát hiện phông chữ trong Aspose.Words – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi **cách phát hiện phông chữ** bị thiếu khi tải một tài liệu Word chưa? Đó là một tình huống xuất hiện thường xuyên hơn bạn nghĩ, đặc biệt khi làm việc với các tệp cũ hoặc triển khai đa nền tảng. Trong hướng dẫn này, chúng tôi sẽ trình bày một ví dụ hoàn chỉnh, có thể chạy được mà **bắt các cảnh báo**, **cấu hình callback**, và **liệt kê các cảnh báo** để bạn luôn biết phông chữ nào đã được thay thế.

Chúng tôi sẽ sử dụng Aspose.Words for .NET (v24.9 tại thời điểm viết) và C# thuần. Không có dịch vụ bên ngoài, không có phép màu—chỉ có API và một vài dòng mã. Khi kết thúc, bạn sẽ có thể phát hiện mọi sự thay thế phông chữ, ghi lại chúng, và thậm chí quyết định có hủy quá trình tải nếu một phông chữ quan trọng bị thiếu.  

### Những gì bạn cần
- **Aspose.Words for .NET** (cài đặt qua NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 hoặc mới hơn (mã này cũng hoạt động trên .NET Framework)
- Một tệp DOCX mẫu tham chiếu tới một phông chữ không có trên máy (ví dụ: “MyCustomFont.ttf”)
- Visual Studio, Rider, hoặc bất kỳ trình chỉnh sửa C# nào bạn thích

> **Mẹo chuyên nghiệp:** Nếu bạn không có tài liệu nào có phông chữ bị thiếu, chỉ cần đổi tên một tệp phông chữ trên hệ thống của bạn hoặc chỉnh sửa XML của DOCX để tham chiếu tới một họ phông chữ không tồn tại.

---

## Cách phát hiện phông chữ với Aspose.Words

Ý tưởng cốt lõi là gắn vào hệ thống cảnh báo của Aspose.Words. Khi thư viện không thể tìm thấy một phông chữ được yêu cầu, nó sẽ phát ra cảnh báo `WarningType.FontSubstitution`. Bằng cách cung cấp một triển khai tùy chỉnh của `IWarningCallback`, bạn có thể **phát hiện phông chữ** đã được thay thế trong quá trình tải.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Tại sao cách này hoạt động:** Aspose.Words gọi phương thức `Warning` cho mọi vấn đề không quan trọng. Bằng cách lưu trữ các đối tượng `WarningInfo`, bạn có quyền truy cập đầy đủ vào loại, thông điệp và ngữ cảnh, chính là những gì bạn cần để **phát hiện phông chữ** đã được thay thế.

## Cách bắt các cảnh báo khi tải tài liệu

Bây giờ chúng ta đã có bộ thu thập, chúng ta cần chỉ định cho `LoadOptions` sử dụng nó. Đây là phần **cách bắt các cảnh báo** của câu đố.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Trường hợp đặc biệt:** Nếu bạn tải tài liệu từ một luồng (`new Document(stream, loadOptions)`), callback vẫn hoạt động—chỉ cần truyền luồng thay vì đường dẫn tệp.

Tại thời điểm này, tài liệu đã được tải đầy đủ, nhưng mọi cảnh báo thay thế phông chữ đều được lưu an toàn trong `warningCollector.Warnings`.

## Cách liệt kê các cảnh báo và báo cáo việc thay thế phông chữ

Cuối cùng, chúng ta sẽ lọc qua các cảnh báo đã thu thập và **liệt kê các cảnh báo** liên quan cụ thể tới việc thay thế phông chữ. Bước này biến dữ liệu thô thành một báo cáo dễ đọc.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Kết quả mong đợi** (ví dụ):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Nếu tài liệu không chứa phông chữ nào bị thiếu, vòng lặp sẽ không tạo ra bất kỳ đầu ra nào—không có gì phải lo lắng.

## Ví dụ hoàn chỉnh (Tất cả các bước trong một tệp)

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào một dự án console. Nó kết hợp **cách phát hiện phông chữ**, **cách bắt các cảnh báo**, **cách cấu hình callback**, và **cách liệt kê các cảnh báo** trong một luồng duy nhất, gắn kết.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Chạy chương trình này** sẽ in ra mọi phông chữ mà Aspose.Words đã phải thay thế. Bạn có thể chuyển hướng đầu ra tới tệp log, phát cảnh báo, hoặc thậm chí hủy tải nếu một phông chữ quan trọng bị thiếu.

## Các câu hỏi thường gặp & Lưu ý

### Nếu tôi cần dừng việc tải khi một phông chữ bắt buộc bị thiếu thì sao?
Bạn có thể kiểm tra các đối tượng `WarningInfo` trong callback và ném một ngoại lệ khi một tên phông chữ cụ thể xuất hiện. Ngoại lệ sẽ hủy quá trình tải, cho bạn quyền kiểm soát hoàn toàn.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Điều này có hoạt động với PDF hoặc các định dạng khác không?
Có. Aspose.Words sử dụng cùng một cơ sở hạ tầng cảnh báo cho PDF, RTF và HTML. Chỉ cần thay đổi phần mở rộng tệp và phần còn lại của mã vẫn giống nhau.

### Làm sao để ghi cảnh báo vào tệp thay vì console?
Thay thế `Console.WriteLine` bằng bất kỳ khung ghi log nào bạn thích (`Serilog`, `NLog`, v.v.). Lớp `WarningInfo` cung cấp `Message`, `Source` và `Exception` để ghi log chi tiết.

### Điều này có ảnh hưởng tới hiệu năng không?
Chi phí bổ sung là không đáng kể—Aspose.Words đã tạo ra các cảnh báo nội bộ. Thêm một callback chỉ đơn giản là lưu chúng vào một danh sách, độ phức tạp O(n) theo số lượng cảnh báo. Đối với các tài liệu thông thường, ảnh hưởng thấp hơn 1 % tổng thời gian tải.

## Tóm tắt trực quan

![Cách phát hiện phông chữ trong Aspose.Words – sơ đồ luồng cảnh báo](https://example.com/images/font-detection-diagram.png "cách phát hiện phông chữ")

*Văn bản thay thế:* **cách phát hiện phông chữ** – sơ đồ hiển thị callback cảnh báo, bộ thu thập và các bước liệt kê.

## Tổng kết

Chúng tôi đã đề cập **cách phát hiện phông chữ** trong Aspose.Words bằng cách **bắt các cảnh báo**, **cấu hình callback**, và **liệt kê các cảnh báo**. Mẫu mã đầy đủ cho thấy một mẫu sẵn sàng cho môi trường sản xuất mà bạn có thể đưa vào bất kỳ ứng dụng .NET nào.  

Tiếp theo, bạn có thể muốn khám phá:

- **Cách bắt các cảnh báo** cho các vấn đề khác (ví dụ: vấn đề chuyển đổi hình ảnh)
- **Cách cấu hình callback** cho các khung ghi log tùy chỉnh
- **Cách liệt kê các cảnh báo** trên nhiều tài liệu trong một công việc batch
- Sử dụng **Aspose.Words.Fonts.FontSettings** để cung cấp các thư mục phông chữ dự phòng, có thể giảm số lần thay thế ngay từ đầu.

Hãy thử nghiệm, điều chỉnh bộ thu thập để phù hợp với phong cách ghi log của bạn, và bạn sẽ không bao giờ bị bất ngờ bởi một sự thay thế phông chữ không mong muốn nữa. Nếu gặp bất kỳ vấn đề nào, hãy để lại bình luận bên dưới—chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}