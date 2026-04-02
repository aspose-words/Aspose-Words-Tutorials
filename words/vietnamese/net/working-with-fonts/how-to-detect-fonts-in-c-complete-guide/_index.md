---
category: general
date: 2026-04-02
description: Cách phát hiện phông chữ trong tài liệu C# bằng Aspose.Words. Tìm hiểu
  cách cấu hình cài đặt phông chữ và xử lý các phông chữ thiếu một cách hiệu quả.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: vi
og_description: Cách phát hiện phông chữ trong tài liệu C# bằng Aspose.Words. Hướng
  dẫn này cho bạn biết cách cấu hình cài đặt phông chữ và xử lý các phông chữ bị thiếu.
og_title: Cách phát hiện phông chữ trong C# – Hướng dẫn đầy đủ
tags:
- C#
- Aspose.Words
- Document Processing
title: Cách phát hiện phông chữ trong C# – Hướng dẫn đầy đủ
url: /vi/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách phát hiện phông chữ trong C# – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi **cách phát hiện phông chữ** bị thiếu hoặc bị thay thế khi tải tài liệu Word trong .NET chưa? Bạn không phải là người duy nhất—các nhà phát triển thường gặp khó khăn khi một tài liệu tham chiếu tới một phông chữ không được cài đặt trên máy chủ. Tin tốt là Aspose.Words cung cấp cho bạn một cách tiếp cận lập trình sạch sẽ để phát hiện những khoảng trống này.

Trong tutorial này, chúng ta sẽ đi qua một ví dụ thực tế không chỉ cho thấy **cách phát hiện phông chữ**, mà còn minh họa **cách cấu hình cài đặt phông chữ** và **xử lý phông chữ thiếu** một cách khéo léo. Khi hoàn thành, bạn sẽ có một đoạn mã sẵn sàng chạy, in ra mọi cảnh báo thay thế phông chữ, để bạn có thể ghi log, cảnh báo hoặc thay thế phông chữ khi cần.

---

## Những gì bạn cần

- **Aspose.Words for .NET** (phiên bản mới nhất hoạt động tốt nhất; mã dưới đây nhắm tới .NET 6+)
- Môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code)
- Một tệp mẫu `.docx` tham chiếu tới một phông chữ bạn không có trên máy (rất hữu ích để thử nghiệm)

Không cần thêm bất kỳ gói NuGet nào ngoài Aspose.Words, và giải pháp này hoạt động trên Windows, Linux và macOS.

---

## Bước 1: Cài đặt và tham chiếu Aspose.Words

Đầu tiên, thêm thư viện vào dự án của bạn. Lệnh NuGet rất đơn giản:

```bash
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang chạy trên máy CI, hãy cố định phiên bản gói để tránh các thay đổi gây lỗi không mong muốn.

---

## Bước 2: Cấu hình cài đặt phông chữ (và chuẩn bị Load Options)

Trước khi mở tài liệu, bạn có thể chỉ định cho Aspose.Words nơi tìm kiếm các phông chữ dự phòng. Đây là phần **cấu hình cài đặt phông chữ** giúp ngăn engine tự động thay thế phông chữ mà bạn không muốn.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Tại sao lại cần? Nếu tài liệu tham chiếu *Comic Sans* nhưng máy chủ của bạn chỉ có *Calibri*, Aspose.Words sẽ thay thế bằng *Calibri* và đưa ra cảnh báo. Bằng cách cấu hình đường dẫn tìm kiếm, bạn giảm thiểu những bất ngờ không mong muốn.

---

## Bước 3: Tải tài liệu với các tùy chọn đã chuẩn bị

Bây giờ chúng ta thực sự mở tệp. Đối tượng `LoadOptions` mà chúng ta tạo ở bước trước sẽ được truyền trực tiếp vào hàm khởi tạo `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Nếu tệp không tìm thấy hoặc bị hỏng, một ngoại lệ sẽ được ném—do đó bạn có thể muốn bọc đoạn mã này trong try/catch trong môi trường production.

---

## Bước 4: Quét các cảnh báo của tài liệu để tìm thay thế phông chữ

Aspose.Words thu thập một danh sách các cảnh báo trong quá trình phân tích. Trong số đó, `FontSubstitutionWarning` cho bạn biết chính xác phông chữ nào đã bị thay thế.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

Bộ sưu tập `Warnings` cũng có thể chứa các mục khác (ví dụ, `DocumentStructureWarning`). Lọc ra `FontSubstitutionWarning` giúp chúng ta chỉ báo cáo **trường hợp xử lý phông chữ thiếu** mà chúng ta quan tâm.

---

## Bước 5: Kết hợp tất cả – Ví dụ hoàn chỉnh, có thể chạy ngay

Dưới đây là chương trình đầy đủ. Sao chép‑dán vào một ứng dụng console mới và chạy; bạn sẽ thấy mỗi phông chữ thiếu được in ra console.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Kết quả mong đợi** (ví dụ):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Nếu tài liệu chỉ sử dụng các phông chữ đã có trên máy, bạn sẽ thấy dòng “No font substitutions detected” thay vì các cảnh báo.

---

## Các trường hợp đặc biệt & Câu hỏi thường gặp

### Nếu tài liệu **không có bất kỳ cảnh báo** nào?

Điều này chỉ có nghĩa là mọi phông chữ được tham chiếu đều được tìm thấy trong các thư mục tìm kiếm mà bạn đã cấu hình. Cờ `anySubstitutions` trong ví dụ xử lý trường hợp này.

### Tôi có thể **ghi log** cảnh báo vào file thay vì console không?

Chắc chắn rồi. Thay thế các lời gọi `Console.WriteLine` bằng một logger mà bạn ưa thích (Serilog, NLog, v.v.). Đối tượng `WarningInfo` cũng cung cấp `WarningType` và `WarningMessage` nếu bạn cần chi tiết hơn.

### Làm sao **bỏ qua** một số phông chữ, chẳng hạn phông chữ thương hiệu công ty không bao giờ được thay thế?

Bạn có thể thêm quy tắc thay thế tùy chỉnh:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Bây giờ Aspose.Words sẽ chỉ thay thế *MyBrandFont* bằng các lựa chọn thay thế bạn liệt kê, và bạn vẫn sẽ nhận được cảnh báo để xử lý.

### Điều này có hoạt động trên các container **Linux** không?

Có—chỉ cần đảm bảo bạn gắn một thư mục chứa các tệp `.ttf`/`.otf` cần thiết và trỏ `SetFontsFolder` tới đó. Aspose.Words không phụ thuộc vào phông chữ được cài đặt sẵn trên hệ điều hành.

---

## Tổng quan trực quan

![luồng phát hiện phông chữ](detect-fonts.png "Sơ đồ mô tả các bước phát hiện phông chữ trong một tài liệu")

*Văn bản thay thế ảnh:* **luồng phát hiện phông chữ** mô tả cấu hình, tải tài liệu và kiểm tra cảnh báo.

---

## Tóm tắt – Những gì chúng ta đã học

- **Cách phát hiện phông chữ** bị thiếu hoặc bị thay thế bằng các cảnh báo của Aspose.Words.  
- Cách **cấu hình cài đặt phông chữ** để chỉ tới các thư mục phông chữ tùy chỉnh và đặt fallback mặc định.  
- Các chiến lược **xử lý phông chữ thiếu**, từ ghi log đến quy tắc thay thế tùy chỉnh.

Tất cả những điều này được gói gọn trong một ứng dụng console ngắn gọn, tự chứa, bạn có thể đưa vào bất kỳ giải pháp .NET nào.

---

## Bước tiếp theo & Các chủ đề liên quan

- **Nhúng phông chữ** trực tiếp vào tài liệu đầu ra để tránh các thay thế trong tương lai (`SaveOptions` với `EmbedFullFonts`).  
- **Thay thế phông chữ bằng lập trình** – thay thế các phông chữ thiếu bằng một lựa chọn cụ thể trước khi lưu.  
- **Tối ưu hiệu năng** – cache `FontSettings` khi xử lý nhiều tài liệu trong một batch.  

Nếu bạn quan tâm tới các chủ đề này, hãy tìm kiếm *configure font settings* và *handle missing fonts*—chúng sẽ dẫn bạn đến các bài viết sâu hơn về quản lý phông chữ với Aspose.Words.

---

Chúc lập trình vui! Gặp phải trường hợp phông chữ lạ? Để lại bình luận, chúng tôi sẽ cùng bạn giải quyết.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}