---
category: general
date: 2026-03-25
description: Tạo callback cảnh báo để tải tài liệu Word và phát hiện các phông chữ
  bị thiếu. Tìm hiểu cách cấu hình cài đặt phông chữ trong Aspose.Words cho .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: vi
og_description: Tạo callback cảnh báo để tải tài liệu Word đồng thời phát hiện các
  phông chữ thiếu. Hướng dẫn này chỉ cách cấu hình cài đặt phông chữ trong Aspose.Words.
og_title: Tạo callback cảnh báo – Tải tài liệu Word và phát hiện phông chữ thiếu
tags:
- Aspose.Words
- C#
- Font handling
title: Tạo callback cảnh báo khi tải tài liệu Word – Hướng dẫn đầy đủ
url: /vi/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo callback cảnh báo – Tải tài liệu Word & phát hiện phông chữ thiếu

Bạn đã bao giờ **tạo callback cảnh báo** khi tải một tài liệu Word và tự hỏi tại sao một số phông chữ lại biến mất không? Bạn không phải là người duy nhất. Trong nhiều ứng dụng doanh nghiệp, phông chữ thiếu gây ra thảm họa bố cục, và nếu không có một callback thích hợp, bạn có thể không bao giờ nhận ra vấn đề.  

Tin tốt? Với Aspose.Words for .NET, bạn có thể **tải tài liệu Word**, **phát hiện phông chữ thiếu**, và **cấu hình cài đặt phông chữ** chỉ trong vài dòng code gọn gàng. Trong tutorial này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, có thể chạy được, giải thích lý do mỗi phần quan trọng, và cho bạn thấy cách kiểm tra xem callback cảnh báo đã hoạt động đúng chưa.

> **Bạn sẽ nhận được gì**  
> * Một chương trình C# đầy đủ tải DOCX, báo cáo bất kỳ việc thay thế phông chữ nào, và cho phép bạn tùy chỉnh đường dẫn tìm kiếm phông chữ.  
> * Hiểu biết về các lớp `FontSettings`, `LoadOptions`, và `IWarningCallback`.  
> * Mẹo xử lý các trường hợp đặc biệt như phông chữ nhúng hoặc thư mục phông chữ toàn hệ thống.

---

## Các yêu cầu trước

- .NET 6+ (hoặc .NET Framework 4.7.2+) với trình biên dịch C#.  
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`).  
- Một tệp Word mẫu (`input.docx`) sử dụng ít nhất một phông chữ không được cài đặt trên máy (ví dụ: *Calibri Light* trên một container Windows tối thiểu).  
- Kiến thức cơ bản về ứng dụng console C#.

Không cần thư viện bổ sung nào; mọi thứ đều nằm trong Aspose.Words.

---

## Bước 1: Tạo callback cảnh báo để phát hiện phông chữ thiếu

Phần **chính** của câu đố này là một lớp triển khai `IWarningCallback`. Aspose.Words sẽ gọi callback này mỗi khi gặp một tình huống cần cảnh báo – việc thay thế phông chữ là trường hợp phổ biến nhất.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Tại sao điều này quan trọng** – Nếu không có callback, bạn sẽ phải lọc qua log sau khi xảy ra. Bằng cách xử lý cảnh báo ngay trong thời gian thực, bạn có thể quyết định hủy tải, thay thế phông chữ thiếu bằng một phông chữ dự phòng, hoặc chỉ đơn giản ghi lại vấn đề để xem sau.

---

## Bước 2: Cấu hình FontSettings để xử lý phông chữ tùy chỉnh

Trước khi thực sự tải tài liệu, chúng ta có thể muốn chỉ cho Aspose.Words nơi tìm kiếm các phông chữ không có trên hệ thống. Đó là lúc `FontSettings` xuất hiện.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Tại sao điều này quan trọng** – Bằng cách chỉ định cho Aspose.Words một thư mục chứa các phông chữ thiếu, bạn thường tránh được việc thay thế. Khi không thể, một phông chữ mặc định hợp lý (như *Arial*) vẫn giữ cho tài liệu có thể đọc được.

---

## Bước 3: Tải tài liệu Word với callback cảnh báo đã cấu hình

Bây giờ chúng ta gắn mọi thứ lại với nhau: tạo `LoadOptions`, gắn `FontSettings` và `FontWarningHandler`, và cuối cùng tải tài liệu.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Tại sao điều này quan trọng** – `LoadOptions` là nơi duy nhất bạn cấu hình *cách* một tài liệu được đọc. Bằng cách cung cấp cả cấu hình phông chữ và callback cảnh báo, chúng ta đảm bảo bất kỳ phông chữ nào thiếu đều được tìm kiếm ở đúng vị trí **và** được báo cáo ngay lập tức.

---

## Bước 4: Kiểm tra kết quả – bạn sẽ thấy gì?

Chạy chương trình từ console. Nếu `input.docx` sử dụng một phông chữ không được cài đặt và cũng không có trong `C:\SharedFonts`, bạn sẽ thấy một thông báo như:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Nếu tất cả phông chữ đều có sẵn, dòng cảnh báo sẽ không xuất hiện. Vòng phản hồi ngay lập tức này vô giá trong các pipeline xử lý tài liệu tự động, nơi các việc thay thế phông chữ im lặng có thể phá vỡ quy tắc thương hiệu.

---

## Bước 5: Những bẫy thường gặp và mẹo thực hành

| Bẫy | Cách tránh |
|---------|-----------------|
| **Quên tham chiếu `Aspose.Words.Fonts`** | Đảm bảo bạn có `using Aspose.Words.Fonts;` ở đầu file; nếu không trình biên dịch sẽ báo lỗi thiếu kiểu. |
| **Đường dẫn thư mục phông chữ sai** | Kiểm tra lại đường dẫn và đặt `recursive: true` nếu có thư mục con. Dùng `Path.GetFullPath` để debug. |
| **Nhiều callback cảnh báo** | Aspose.Words chỉ chấp nhận `WarningCallback` cuối cùng bạn gán. Giữ một handler duy nhất và ủy quyền nếu cần logic phức tạp hơn. |
| **Chạy trên server không có UI** | Viết ra console vẫn ổn, nhưng với ứng dụng web bạn có thể muốn ghi log vào file hoặc hệ thống giám sát thay vì `Console.WriteLine`. |
| **Tài liệu lớn gây giảm hiệu năng** | Tái sử dụng một thể hiện `FontSettings` duy nhất cho nhiều lần tải; tạo lại liên tục sẽ tốn kém. |

**Mẹo chuyên nghiệp:** Nếu bạn muốn *thu thập* các cảnh báo để phân tích sau, lưu chúng vào một `List<string>` trong handler thay vì in ra trực tiếp.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Bạn có thể kiểm tra `handler.Messages` sau khi tài liệu được tải.

---

## Bước 6: Mở rộng giải pháp – nếu tôi cần nhúng phông chữ dự phòng thì sao?

Đôi khi bạn muốn phông chữ thiếu được *nhúng* trong PDF đầu ra để người xem downstream thấy đúng hình ảnh. Sau khi tải tài liệu, bạn có thể buộc nhúng:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Đoạn mã này cho thấy cách **cấu hình cài đặt phông chữ** có thể được mở rộng ra ngoài việc chỉ tải.

---

## Ví dụ đầy đủ có thể chạy

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào một dự án Console App mới. Nó bao gồm tất cả các phần đã thảo luận ở trên.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Kết quả mong đợi** (khi có phông chữ thiếu):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Nếu không có việc thay thế, chỉ các thông báo thành công sẽ xuất hiện.

---

## Kết luận

Chúng ta vừa **tạo một callback cảnh báo** để **phát hiện phông chữ thiếu** một cách đáng tin cậy khi **tải tài liệu Word** bằng Aspose.Words, và đã chỉ ra cách **cấu hình cài đặt phông chữ** để kiểm soát nơi thư viện tìm kiếm phông chữ và phông chữ dự phòng nào sẽ được dùng. Bằng cách liên kết `FontSettings` và `LoadOptions` với nhau, bạn có được tầm nhìn đầy đủ về các vấn đề liên quan đến phông chữ — không còn những lỗi bố cục im lặng nữa.

Bước tiếp theo? Hãy thử thay thế `FontWarningHandler` bằng một logger ghi vào cơ sở dữ liệu, hoặc thử nghiệm **quy tắc thay thế phông chữ** để ánh xạ các phông chữ thiếu cụ thể sang các lựa chọn được phê duyệt của thương hiệu. Bạn cũng có thể khám phá **tải phông chữ động** từ lưu trữ đám mây nếu ứng dụng của bạn chạy trong môi trường container.

Có câu hỏi về trường hợp đặc biệt nào—như xử lý tính năng OpenType hoặc làm việc với tệp DOCX được mã hoá? Hãy để lại bình luận bên dưới, và chúc bạn lập trình vui vẻ!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}