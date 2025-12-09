---
language: vi
url: /vietnamese/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Phát hiện phông chữ thiếu trong tài liệu Aspose.Words – Hướng dẫn C# đầy đủ

Bạn đã bao giờ tự hỏi làm thế nào để **phát hiện phông chữ thiếu** khi tải một tệp Word bằng Aspose.Words chưa? Trong công việc hàng ngày, tôi đã gặp một vài PDF trông không đúng vì tài liệu gốc sử dụng một phông chữ mà tôi không cài đặt. Tin tốt là gì? Aspose.Words có thể cho bạn biết chính xác khi nó thay thế một phông chữ, và bạn có thể ghi lại thông tin đó bằng một callback cảnh báo đơn giản.  

Trong hướng dẫn này, chúng ta sẽ đi qua một **ví dụ đầy đủ, có thể chạy được** cho thấy cách ghi lại mọi lần thay thế phông, lý do tại sao callback quan trọng, và một vài mẹo bổ sung để phát hiện phông chữ thiếu một cách chắc chắn. Không có phần thừa thãi, chỉ có mã và lý giải bạn cần để làm cho nó hoạt động ngay hôm nay.

---

## Những gì bạn sẽ học

- Cách triển khai **callback cảnh báo Aspose.Words** để bắt các sự kiện thay thế phông chữ.  
- Cách cấu hình **LoadOptions C#** để callback được gọi khi tải tài liệu.  
- Cách xác minh rằng việc phát hiện phông chữ thiếu thực sự hoạt động, và cách đầu ra console trông như thế nào.  
- Các điều chỉnh tùy chọn cho các lô lớn hoặc môi trường không giao diện.  

**Yêu cầu trước** – Bạn cần một phiên bản mới của Aspose.Words cho .NET (mã đã được kiểm tra với 23.12), .NET 6 trở lên, và kiến thức cơ bản về C#. Nếu bạn đã có những thứ này, bạn đã sẵn sàng.

---

## Phát hiện phông chữ thiếu bằng Callback cảnh báo

Trọng tâm của giải pháp là việc triển khai `IWarningCallback`. Aspose.Words phát ra một đối tượng `WarningInfo` cho nhiều tình huống, nhưng chúng ta chỉ quan tâm đến `WarningType.FontSubstitution`. Hãy xem cách kết nối vào đó.

### Bước 1: Tạo Bộ Thu Thập Cảnh Báo Phông Chữ

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Tại sao điều này quan trọng*: Bằng cách lọc theo `WarningType.FontSubstitution` chúng ta tránh được sự lộn xộn từ các cảnh báo không liên quan (như các tính năng đã lỗi thời). `info.Description` đã chứa tên phông chữ gốc và phông chữ dự phòng được sử dụng, cung cấp cho bạn một chuỗi kiểm tra rõ ràng.

---

## Cấu hình LoadOptions để sử dụng Callback

Bây giờ chúng ta cho Aspose.Words biết sử dụng bộ thu thập của chúng ta khi nó tải một tệp.

### Bước 2: Thiết lập LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Tại sao điều này quan trọng*: `LoadOptions` là nơi duy nhất bạn có thể gắn callback, mật khẩu mã hoá và các hành vi tải khác. Giữ nó tách biệt khỏi hàm khởi tạo `Document` giúp mã có thể tái sử dụng cho nhiều tệp.

---

## Tải tài liệu và ghi lại phông chữ thiếu

Với callback đã được kết nối, bước tiếp theo chỉ là tải tài liệu.

### Bước 3: Tải DOCX của bạn (hoặc bất kỳ định dạng hỗ trợ nào)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Khi hàm khởi tạo `Document` phân tích tệp, bất kỳ phông chữ nào thiếu sẽ kích hoạt `FontWarningCollector` của chúng ta. Console sẽ hiển thị các dòng như:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Dòng đó là bằng chứng cụ thể rằng **phát hiện phông chữ thiếu** đã hoạt động.

---

## Xác minh đầu ra – Những gì mong đợi

Chạy chương trình từ terminal hoặc Visual Studio. Nếu tài liệu nguồn chứa một phông chữ mà bạn không cài đặt, bạn sẽ thấy ít nhất một dòng “Font substituted”. Nếu tài liệu chỉ sử dụng các phông chữ đã cài đặt, callback sẽ im lặng và bạn chỉ nhận được thông báo “Document loaded successfully.”.

**Mẹo**: Để kiểm tra lại, mở tệp Word trong Microsoft Word và xem danh sách phông chữ. Bất kỳ phông chữ nào xuất hiện trong *Replace Fonts* dưới nhóm *Home → Font* đều là ứng cử viên cho việc thay thế.

---

## Nâng cao: Phát hiện phông chữ thiếu hàng loạt

Thường bạn cần quét hàng chục tệp. Mẫu tương tự mở rộng tốt:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Vì `FontWarningCollector` ghi ra console mỗi khi được gọi, bạn sẽ nhận được báo cáo theo từng tệp mà không cần cấu hình thêm. Đối với các kịch bản sản xuất, bạn có thể muốn ghi log vào tệp hoặc cơ sở dữ liệu – chỉ cần thay thế `Console.WriteLine` bằng logger bạn ưa thích.

---

## Những lỗi thường gặp & Mẹo chuyên nghiệp

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|----------------|-----|
| **Không có cảnh báo nào xuất hiện** | Tài liệu thực tế chỉ chứa các phông chữ đã được cài đặt. | Xác minh bằng cách mở tệp trong Word hoặc cố ý gỡ bỏ một phông chữ khỏi hệ thống. |
| **Callback không được gọi** | `LoadOptions.WarningCallback` chưa bao giờ được gán hoặc một đối tượng `LoadOptions` mới đã được sử dụng sau này. | Giữ một đối tượng `LoadOptions` duy nhất và tái sử dụng nó cho mỗi lần tải. |
| **Quá nhiều cảnh báo không liên quan** | Bạn chưa lọc theo `WarningType.FontSubstitution`. | Thêm điều kiện `if (info.Type == WarningType.FontSubstitution)` như đã minh họa. |
| **Giảm hiệu năng trên các tệp lớn** | Callback chạy trên mỗi cảnh báo, có thể rất nhiều đối với tài liệu lớn. | Vô hiệu hoá các loại cảnh báo khác qua `LoadOptions.WarningCallback` hoặc đặt `LoadOptions.LoadFormat` thành một kiểu cụ thể nếu bạn biết. |

---

## Ví dụ đầy đủ hoạt động (Sẵn sàng sao chép‑dán)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Đầu ra console dự kiến** (khi gặp phông chữ thiếu):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Nếu không có sự thay thế nào xảy ra, bạn sẽ chỉ thấy dòng thành công.

---

## Kết luận

Bạn đã có một **cách đầy đủ, sẵn sàng cho sản xuất để phát hiện phông chữ thiếu** trong bất kỳ tài liệu nào được xử lý bởi Aspose.Words. Bằng cách tận dụng **callback cảnh báo Aspose.Words** và cấu hình **LoadOptions C#**, bạn có thể ghi lại mọi lần thay thế phông chữ, khắc phục các vấn đề bố cục, và đảm bảo PDF của bạn giữ được giao diện mong muốn.

Từ một tệp đơn lẻ đến một lô hàng khổng lồ, mẫu vẫn giống nhau—triển khai `IWarningCallback`, gắn nó vào `LoadOptions`, và để Aspose.Words thực hiện phần công việc nặng.

Sẵn sàng cho bước tiếp theo? Hãy thử kết hợp điều này với **font embedding** hoặc **fallback font families** để tự động khắc phục vấn đề, hoặc khám phá API **DocumentVisitor** để phân tích nội dung sâu hơn. Chúc lập trình vui vẻ, và hy vọng mọi phông chữ của bạn luôn ở nơi bạn mong đợi!

---

![Phát hiện phông chữ thiếu trong Aspose.Words – ảnh chụp màn hình đầu ra console](https://example.com/images/detect-missing-fonts.png "đầu ra console phát hiện phông chữ thiếu")

{{< layout-end >}}

{{< layout-end >}}