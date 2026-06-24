---
category: general
date: 2026-06-20
description: Kích hoạt cảnh báo thay thế phông chữ trong C# bằng Aspose.Words. Tìm
  hiểu cách cấu hình LoadOptions, ghi lại các cảnh báo và xử lý phông chữ thiếu một
  cách hiệu quả.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: vi
og_description: Kích hoạt cảnh báo thay thế phông chữ trong C# với Aspose.Words. Hướng
  dẫn này chỉ cho bạn cách thiết lập LoadOptions, đọc WarningInfo và hiển thị thông
  báo phông chữ thiếu.
og_title: Kích hoạt Cảnh báo Thay thế Phông chữ trong C# – Hướng dẫn toàn diện
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Kích hoạt cảnh báo thay thế phông chữ trong C# với Aspose.Words
url: /vi/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Bật Cảnh Báo Thay Thế Phông Chữ trong C# với Aspose.Words

Bạn đã bao giờ tự hỏi làm thế nào để **bật cảnh báo thay thế phông chữ** khi một tài liệu Word tham chiếu đến một phông chữ không được cài đặt trên máy chủ chưa? Bạn không phải là người duy nhất. Các phông chữ thiếu có thể âm thầm làm hỏng bố cục của các PDF hoặc hình ảnh được tạo ra, và cách duy nhất để phát hiện sớm là lắng nghe các cảnh báo mà Aspose.Words phát ra.

Trong hướng dẫn này, chúng tôi sẽ hướng dẫn bạn qua một ví dụ thực tế cho thấy cách bật các cảnh báo đó, lấy chúng ra khỏi bộ sưu tập `WarningInfo`, và in các thông báo có ý nghĩa ra console. Khi kết thúc, bạn sẽ biết cách cấu hình **Aspose.Words LoadOptions**, xử lý **cảnh báo thay thế phông chữ C#**, và giữ cho quy trình xử lý tài liệu của bạn luôn an toàn.

Chúng tôi cũng sẽ đề cập đến một vài trường hợp đặc biệt—điều gì xảy ra nếu bạn ẩn cảnh báo, hoặc nếu bạn cần ghi chúng thay vì in—và cung cấp cho bạn một mẫu mã hoàn chỉnh, sẵn sàng sao chép và dán, hoạt động với phiên bản mới nhất của Aspose.Words cho .NET (tại phiên bản 24.10).

## Những Điều Cần Chuẩn Bị

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động trên .NET Framework 4.7+)
- Tham chiếu NuGet tới `Aspose.Words` (cài đặt bằng `dotnet add package Aspose.Words`)
- Một tệp Word tham chiếu đến một phông chữ mà bạn **không** có cài đặt (ví dụ, `DocumentWithMissingFont.docx`)
- Một IDE tốt (Visual Studio, Rider, hoặc VS Code)

Chỉ vậy thôi—không cần dịch vụ bổ sung, không cần công cụ độc quyền. Sẵn sàng chưa? Hãy bắt đầu.

## Bước 1: Bật Cảnh Báo Thay Thế Phông Chữ

Điều đầu tiên bạn cần làm là thông báo cho Aspose.Words rằng bạn muốn nhận thông báo khi nó thay thế một phông chữ thiếu. Điều này được thực hiện thông qua thuộc tính `FontSettings` của đối tượng `LoadOptions`. Mặc định, các cảnh báo **bị tắt** để API không gây ồn, vì vậy chúng ta phải bật chúng thủ công.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Tại sao điều này hoạt động:** Khi `FontSettings` không phải `null`, thư viện tự động điền `Document.WarningInfo` với bất kỳ mục `WarningType.FontSubstitution` nào nó gặp khi tải tài liệu. Hãy nghĩ nó như việc bật “chế độ debug” cho phông chữ.

## Bước 2: Tải Tài Liệu với Các Tùy Chọn Đã Cấu Hình

Bây giờ bộ sưu tập cảnh báo đã hoạt động, hãy tải tài liệu của bạn bằng cách sử dụng `LoadOptions` mà chúng ta vừa chuẩn bị. Nếu tài liệu chứa phông chữ thiếu, Aspose.Words sẽ thay thế bằng một phông chữ dự phòng và đẩy một cảnh báo vào danh sách `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang xử lý nhiều tệp trong một vòng lặp, hãy tái sử dụng cùng một thể hiện `LoadOptions`—tạo một lần sẽ tiết kiệm vài mili giây cho mỗi vòng lặp.

## Bước 3: Duyệt `WarningInfo` và Hiển Thị Thông Báo Thay Thế Phông Chữ

Khi tài liệu đã được tải, bộ sưu tập `WarningInfo` chứa mọi cảnh báo xảy ra trong quá trình tải. Chúng ta chỉ quan tâm đến `WarningType.FontSubstitution`, vì vậy chúng ta sẽ lọc theo đó.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Chạy đoạn mã trên với một tài liệu tham chiếu đến phông chữ “Papyrus” bị thiếu có thể tạo ra đầu ra như sau:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Đó là **các thông báo thay thế phông chữ** mà bạn đang tìm kiếm—rõ ràng, có thể hành động, và sẵn sàng được ghi log hoặc gửi tới hệ thống cảnh báo.

## Ví Dụ Hoàn Chỉnh Hoạt Động

Dưới đây là một chương trình console tự chứa, kết hợp mọi thứ lại với nhau. Sao chép‑dán nó vào một `.csproj` mới và nhấn **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Đầu Ra Dự Kiến

Nếu tài liệu tham chiếu đến các phông chữ chưa được cài đặt, bạn sẽ thấy điều gì đó tương tự như:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Nếu mọi phông chữ đều có trên máy, chương trình sẽ chỉ in ra:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Những Sai Lầm Thường Gặp & Mẹo Chuyên Nghiệp

| Vấn Đề | Nguyên Nhân | Cách Khắc Phục / Tránh |
|-------|----------------|--------------------|
| **Cảnh báo biến mất** | Bạn đã xóa `FontSettings` hoặc sử dụng `LoadOptions` mà không có nó. | Luôn tạo một thể hiện `FontSettings` ngay cả khi bạn không thay đổi bất kỳ thuộc tính nào. |
| **Quá nhiều cảnh báo** | Tài liệu sử dụng nhiều phông chữ lạ. | Xem xét thêm thư mục phông chữ tùy chỉnh vào `FontSettings` bằng `SetFontsFolder` để giảm thiểu việc thay thế. |
| **Giảm hiệu năng trong vòng lặp chặt** | Tạo lại `LoadOptions` mỗi lần lặp gây thêm chi phí. | Tái sử dụng một thể hiện `LoadOptions` duy nhất cho tất cả các tài liệu. |
| **Không có đầu ra console** | Chạy trong ứng dụng GUI nơi `Console.WriteLine` bị bỏ qua. | Chuyển hướng cảnh báo tới một logger (`ILogger`) hoặc ghi vào file. |

### Xử Lý Cảnh Báo trong Dịch Vụ Thực Tế

Trong một API web, bạn có thể không muốn ghi ra console. Thay vào đó, hãy chuyển các cảnh báo vào một log có cấu trúc:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

Bằng cách này bạn vẫn giữ **xử lý cảnh báo tài liệu** trong khi dịch vụ của bạn vẫn sạch sẽ.

## Mở Rộng Ví Dụ

- **Ghi lại các loại cảnh báo khác** (ví dụ, `WarningType.UnknownFileFormat`) bằng cách loại bỏ bộ lọc `if`.
- **Lưu báo cáo** tất cả các cảnh báo dưới dạng JSON để phân tích sau này.
- **Buộc một phông chữ dự phòng cụ thể** bằng cách đặt `FontSettings.SubstitutionSettings.DefaultFontName`.

Tất cả những điều này là các mở rộng tự nhiên sau khi bạn đã thành thạo **bật cảnh báo thay thế phông chữ**.

## Kết Luận

Chúng tôi đã chỉ cho bạn cách **bật cảnh báo thay thế phông chữ** trong C# bằng Aspose.Words, từ việc cấu hình `LoadOptions` đến duyệt `WarningInfo` và in các thông báo thân thiện. Bằng cách làm theo các bước trên, bạn có thể bảo vệ các pipeline xử lý tài liệu của mình khỏi các thay đổi bố cục âm thầm do phông chữ thiếu.

Tiếp theo, hãy thử thêm một thư mục phông chữ tùy chỉnh, ghi log các cảnh báo vào file, hoặc thậm chí gửi chúng tới bảng điều khiển giám sát. Mẫu này cũng áp dụng cho bất kỳ kịch bản **xử lý cảnh báo tài liệu** nào, dù bạn đang chuyển đổi sang PDF, render hình ảnh, hay thực hiện mail‑merge.

Có câu hỏi về **cảnh báo thay thế phông chữ C#** hoặc muốn chia sẻ một giải pháp thông minh? Để lại bình luận bên dưới—chúc lập trình vui!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với các giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Bật Cảnh Báo Thay Thế Phông Chữ trong Aspose.Words – Hướng Dẫn Đầy Đủ](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Cách Phát Hiện Phông Chữ trong Aspose.Words – Xử Lý Cảnh Báo & Cài Đặt](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Ghi lại Cảnh Báo Thay Thế Phông Chữ trong Java với Aspose.Words – Hướng Dẫn Đầy Đủ](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}