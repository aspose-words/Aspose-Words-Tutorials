---
category: general
date: 2026-03-01
description: Tạo FontSettings trong C# để phát hiện phông chữ thiếu, ghi lại thông
  báo phông chữ và xử lý phông chữ thiếu bằng Aspose.Words. Hướng dẫn chi tiết từng
  bước cho các nhà phát triển.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: vi
og_description: Tạo FontSettings trong C# để phát hiện phông chữ thiếu, ghi lại thông
  báo phông chữ và xử lý phông chữ thiếu bằng Aspose.Words. Hướng dẫn đầy đủ kèm mã.
og_title: Tạo FontSettings trong C# – Phát hiện phông chữ thiếu & Ghi lại thông báo
  phông chữ
tags:
- Aspose.Words
- C#
- Font Management
title: Tạo FontSettings trong C# – Phát hiện phông chữ thiếu & Ghi lại tin nhắn phông
  chữ
url: /vi/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo FontSettings trong C# – Phát hiện Phông chữ thiếu & Ghi lại Thông báo Phông chữ

Bạn đã bao giờ cần **create FontSettings** trong một dự án .NET nhưng không chắc cách phát hiện các phông chữ chưa được cài đặt trên máy đích? Bạn không phải là người duy nhất. Trong nhiều ứng dụng thực tế—như các công cụ tạo báo cáo tự động hoặc chuyển đổi tài liệu—các phông chữ thiếu có thể làm hỏng bố cục một cách âm thầm, và bạn sẽ không biết cho đến khi PDF trông lộn xộn.  

Nếu bạn có thể **detect missing fonts**, **capture font messages**, và **handle missing fonts** trước khi chúng làm hỏng kết quả? Tin tốt là Aspose.Words làm cho việc này trở nên dễ dàng. Trong hướng dẫn này, chúng tôi sẽ hướng dẫn toàn bộ quy trình, từ việc thiết lập đối tượng `FontSettings` đến việc gắn một callback cảnh báo cho bạn biết chính xác ký tự nào đã được thay thế.

> **TL;DR:** Khi kết thúc, bạn sẽ có một ứng dụng console C# sẵn sàng chạy, ghi lại mọi lần thay thế phông chữ, cho phép bạn quyết định nhúng phông thay thế hoặc cảnh báo người dùng.

---

## Yêu cầu trước

- .NET 6 SDK (hoặc bất kỳ phiên bản .NET gần đây nào)  
- Visual Studio 2022 hoặc VS Code với các extension C#  
- Giấy phép Aspose.Words cho .NET (bản dùng thử miễn phí hoạt động cho bản demo này)  
- Một tệp DOCX mẫu tham chiếu một phông chữ bạn chưa cài đặt (ví dụ, *Comic Sans MS* trên máy Linux)  

Không cần gói NuGet đặc biệt nào ngoài `Aspose.Words`.

---

## Bước 1 – Cài đặt Aspose.Words và Thiết lập Dự án

Đầu tiên, tạo một dự án console mới và đưa thư viện Aspose.Words vào dự án.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Nếu bạn đã có một solution, chỉ cần thêm gói qua giao diện NuGet Package Manager—giúp việc theo dõi phiên bản dễ dàng hơn.

---

## Bước 2 – Tạo FontSettings (Từ khóa chính xuất hiện ở đây)

Bước **create FontSettings** là nền tảng của bất kỳ quy trình làm việc nào liên quan đến phông chữ. `FontSettings` cho Aspose.Words biết nơi tìm phông chữ, có nên sử dụng các thư mục hệ thống hay không, và cách dự phòng khi có thứ gì đó thiếu.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Tại sao lại quan trọng? Nếu không cấu hình đúng `FontSettings`, engine sẽ âm thầm thay thế các glyph thiếu bằng phông chữ hệ thống mặc định, và bạn sẽ không bao giờ nhận được cảnh báo.

---

## Bước 3 – Kết nối LoadOptions với FontSettings

`LoadOptions` cho phép bạn truyền `FontSettings` vào bộ tải tài liệu. Đây là cầu nối cho phép engine **detect missing fonts** trong giai đoạn xây dựng `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Bây giờ mỗi khi bạn tải một DOCX bằng `loadOptions`, Aspose.Words sẽ tham khảo `FontSettings` mà chúng ta đã thiết lập trước đó.

---

## Bước 4 – Gắn Callback Cảnh báo để **Capture Font Messages**

Aspose.Words phát ra các cảnh báo cho nhiều tình huống—thay thế phông chữ là một trong số chúng. Bằng cách cung cấp một triển khai của `IWarningCallback`, bạn có thể **capture font messages** ngay lập tức.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### Lớp Xử lý Cảnh báo

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Trường `info.Description` chứa thông điệp dễ đọc như *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Đây chính là loại đầu ra bạn cần để **handle missing fonts** một cách nhẹ nhàng.

---

## Bước 5 – Tải Tài liệu và Để Callback Thực hiện Công việc của Nó

Với mọi thứ đã được kết nối, việc tải tài liệu trở nên đơn giản. Nếu tệp nguồn tham chiếu một phông chữ không có trong hệ thống, trình xử lý cảnh báo của chúng ta sẽ được kích hoạt.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Khi bạn chạy chương trình, bạn sẽ thấy đầu ra console tương tự như:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Đầu ra đó là phần **capture font messages** của quy trình của chúng ta. Bạn có thể mở rộng trình xử lý để ghi vào tệp, gửi telemetry, hoặc thậm chí hủy chuyển đổi nếu các phông chữ quan trọng bị thiếu.

---

## Bước 6 – Ví dụ Hoạt động Đầy đủ (Tất cả Các Phần Kết Hợp)

Dưới đây là một chương trình hoàn chỉnh, sẵn sàng sao chép. Dán vào `Program.cs`, điều chỉnh các đường dẫn tệp, và chạy `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Đầu ra Dự kiến

Chạy chương trình trên máy không có *Comic Sans MS* sẽ in ra một thứ gì đó như:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Bạn cũng sẽ có `Result.pdf` sử dụng các phông chữ đã được thay thế, đảm bảo quá trình chuyển đổi không bao giờ bị lỗi.

---

## Câu hỏi Thường gặp & Trường hợp Cạnh

| Câu hỏi | Câu trả lời |
|----------|--------|
| **Nếu tôi muốn quá trình chuyển đổi thất bại thay vì thay thế thì sao?** | Trong `FontSubstitutionWarningHandler`, ném một ngoại lệ khi `info.Description` chứa tên phông chữ quan trọng. |
| **Tôi có thể tự động nhúng phông chữ thay thế không?** | Có. Sau khi phát hiện phông chữ thiếu, bạn có thể tải một `FontInfo` dự phòng từ một đường dẫn đã biết và thêm nó vào `fontSettings` bằng `fontSettings.SetFontsFolder`. |
| **Điều này có hoạt động trên Linux/macOS không?** | Hoàn toàn có. `FontSettings` hoạt động đa nền tảng; chỉ cần đảm bảo thư mục dự phòng chứa các tệp `.ttf` hoặc `.otf` phù hợp. |
| **Callback cảnh báo có an toàn đa luồng không?** | Callback chạy trên cùng một luồng tải tài liệu, vì vậy bạn không cần đồng bộ thêm cho việc ghi log console. Đối với các kịch bản đa luồng, hãy bảo vệ các tài nguyên chia sẻ. |
| **Làm sao tôi ghi cảnh báo vào tệp?** | Thay `Console.WriteLine` bằng `File.AppendAllText("font_warnings.log", ...)` hoặc sử dụng bất kỳ framework ghi log nào (Serilog, NLog). |

---

## Mẹo chuyên nghiệp cho Xử lý Phông chữ Sẵn sàng cho Sản xuất

1. **Cache Font Lookups** – Tái sử dụng cùng một thể hiện `FontSettings` cho nhiều lần tải tài liệu giúp tránh việc quét hệ thống tệp lặp lại.  
2. **Whitelist Critical Fonts** – Nếu thương hiệu của bạn yêu cầu một phông chữ cụ thể, hãy kiểm tra sự hiện diện của nó sớm và hủy với thông báo lỗi rõ ràng.  
3. **Use `SetFontFolder` Recursively** – Đặt `recursive: true` để đảm bảo các thư mục con được quét, hữu ích khi bạn cung cấp một bộ sưu tập phông chữ đầy đủ.  
4. **Combine with `FontSubstitutionSettings`** – Bạn có thể tinh chỉnh các quy tắc thay thế (ví dụ, ưu tiên các phông chữ có cùng tên họ).  

---

## Kết luận

Chúng tôi vừa **tạo FontSettings**, cấu hình `LoadOptions` để **detect missing fonts**, gắn một callback **captures font messages**, và trình bày cách **handle missing fonts** một cách sạch sẽ, sẵn sàng cho sản xuất. Toàn bộ quy trình chỉ cần vài chục dòng C#, nhưng cung cấp cho bạn khả năng quan sát đầy đủ về các phông chữ trong bất kỳ DOCX nào bạn xử lý.

Tiếp theo, bạn có thể khám phá:

- **Embedding fallback fonts** trực tiếp vào PDF đầu ra (`PdfSaveOptions.FontEmbeddingMode`).  
- **Programmatically substituting fonts** dựa trên quy tắc thương hiệu doanh nghiệp.  
- **Integrating with a CI pipeline** để tự động đánh dấu các tài liệu sử dụng phông chữ không được phép.

Hãy thử nghiệm, điều chỉnh trình xử lý cảnh báo cho phù hợp với nhu cầu của bạn, và để các pipeline tài liệu của bạn chạy một cách tự tin—không còn những lỗi bố cục bí ẩn do việc thay đổi phông chữ ẩn.

Chúc lập trình vui! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}