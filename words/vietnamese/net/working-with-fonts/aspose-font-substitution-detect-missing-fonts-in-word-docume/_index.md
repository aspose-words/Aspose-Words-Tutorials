---
category: general
date: 2026-04-05
description: Hướng dẫn thay thế phông chữ của Aspose để phát hiện phông chữ thiếu
  khi tải tài liệu Word. Tìm hiểu cách cấu hình cài đặt phông chữ và xử lý phông chữ
  thiếu một cách hiệu quả.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: vi
og_description: Hướng dẫn thay thế phông chữ của Aspose để phát hiện các phông chữ
  thiếu khi tải tài liệu Word. Tìm hiểu cách cấu hình cài đặt phông chữ và xử lý các
  phông chữ thiếu một cách hiệu quả.
og_title: Thay thế phông chữ Aspose – Phát hiện phông chữ thiếu trong tài liệu Word
tags:
- Aspose.Words
- C#
- Font Management
title: Thay thế phông chữ Aspose – Phát hiện phông chữ thiếu trong tài liệu Word
url: /vi/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Phát hiện phông chữ thiếu trong tài liệu Word

Bạn đã bao giờ gặp một tệp Word trông hoàn hảo trên một máy nhưng lại hiển thị các thay đổi phông chữ lạ trên máy khác chưa? Đó là vấn đề **aspose font substitution** kinh điển, thường có nghĩa là một số phông chữ bị thiếu trên hệ thống đích. Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn, từng bước một, cách **phát hiện phông chữ thiếu** khi **tải một tài liệu Word**, cách **cấu hình cài đặt phông chữ**, và cách **xử lý phông chữ thiếu** một cách nhẹ nhàng.

Chúng tôi sẽ đi qua một ví dụ C# đầy đủ, có thể chạy được, giải thích lý do mỗi dòng quan trọng, và thậm chí cho bạn thấy đầu ra console mà bạn nên mong đợi. Khi kết thúc, bạn sẽ có thể phát hiện các thay thế phông chữ ngay khi tài liệu được tải — không cần đoán mò.

## Những gì bạn sẽ học

- Cách bật bộ thu thập chẩn đoán của Aspose.Words để nhận cảnh báo về phông chữ.  
- Mã chính xác cần **tải một tài liệu Word** với **cài đặt phông chữ** tùy chỉnh.  
- Cách lặp qua các đối tượng `WarningInfo` để liệt kê mọi phông chữ đã được thay thế.  
- Mẹo để ẩn các cảnh báo không mong muốn hoặc cung cấp phông chữ dự phòng.  
- Một mẫu sẵn sàng chạy mà bạn có thể sao chép‑dán vào Visual Studio.

### Yêu cầu trước

- .NET 6.0 hoặc mới hơn (API hoạt động tương tự trên .NET Framework).  
- Aspose.Words for .NET (gói NuGet `Aspose.Words`).  
- Một tệp Word tham chiếu tới một phông chữ bạn không có trên máy (ví dụ, `MissingFont.docx`).  

Nếu bạn đã có những thứ trên, hãy bắt đầu.

## Bước 1 – Bật Bộ thu thập Chẩn đoán (Cấu hình Cài đặt Phông chữ)

Điều đầu tiên: Aspose.Words chỉ ghi lại cảnh báo thay thế phông chữ nếu bạn bật nó. Điều này được thực hiện bằng cách tạo một đối tượng `FontSettings` và gán nó cho một thể hiện `LoadOptions`. Hãy nghĩ đây như việc bật “đèn debug” cho việc xử lý phông chữ.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Tại sao?**  
Nếu không có đối tượng `FontSettings`, bộ thu thập cảnh báo sẽ im lặng và bạn sẽ không bao giờ biết phông chữ nào đã bị thay thế. Bằng cách khởi tạo nó rỗng, chúng ta cho phép Aspose sử dụng các phông chữ hệ thống mặc định *và* theo dõi mọi sự thay thế.

> **Mẹo chuyên nghiệp:** Nếu bạn biết một thư mục cụ thể chứa các phông chữ công ty, hãy chỉ định `FontSettings` tới đó bằng `SetFontsFolder("path")`. Điều này có thể giảm số lượng cảnh báo phông chữ thiếu.

## Bước 2 – Tải Tài liệu với Các Tùy chọn Đã Cấu hình (Load Word Document)

Bây giờ bộ thu thập đã hoạt động, hãy tải tệp `.docx` của bạn bằng cùng một `LoadOptions`. Đây là thời điểm Aspose quét tài liệu, tìm mọi tham chiếu phông chữ và quyết định có cần thay thế hay không.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Tại sao điều này quan trọng?**  
Nếu bạn chỉ gọi `new Document("MissingFont.docx")`, các cài đặt mặc định sẽ được áp dụng *và* danh sách cảnh báo sẽ trống. Việc truyền `loadOptions` đảm bảo bộ thu thập chẩn đoán được gắn vào quy trình tải.

## Bước 3 – Lấy và Hiển thị Cảnh báo Thay thế Phông chữ (Detect Missing Fonts)

Sau khi tài liệu đã được nạp vào bộ nhớ, Aspose lưu mọi cảnh báo trong `document.WarningCallback.Warnings`. Duyệt qua bộ sưu tập này, lọc các mục có `WarningType.FontSubstitution`, và in ra mô tả. Mỗi mô tả cho bạn biết phông chữ nào bị thiếu và phông chữ nào đã được dùng thay thế.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Đầu ra console dự kiến**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Đầu ra này cho bạn biết chính xác những phông chữ nào đang thiếu trên máy chạy mã. Bạn có thể quyết định cài đặt các phông chữ thiếu, nhúng chúng vào tài liệu, hoặc giữ nguyên việc thay thế.

![Kết quả console hiển thị cảnh báo thay thế phông chữ của Aspose](/images/aspose-font-substitution-console.png)

*Văn bản thay thế ảnh:* aspose font substitution – console output listing substituted fonts

## Bước 4 – Tùy chọn: Tùy chỉnh Hành vi Thay thế (Handle Missing Fonts)

Đôi khi bạn không chỉ muốn biết *rằng* một sự thay thế đã xảy ra — bạn còn muốn kiểm soát *cách* nó xảy ra. Aspose.Words cho phép bạn đăng ký một `IFontSubstitutionRule` tùy chỉnh. Dưới đây là một ví dụ nhanh buộc bất kỳ phông chữ nào thiếu đều sẽ quay lại `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Khi nào bạn sẽ dùng điều này?**  
Nếu bạn đang tạo PDF cho một dịch vụ web và biết rằng mọi khách hàng đều có thể hiển thị `Tahoma`, việc buộc fallback này đảm bảo tính nhất quán về giao diện mà không cần phải phân phối hàng chục tệp phông chữ.

## Ví dụ Hoạt động Đầy đủ (Tất cả các Bước Kết hợp)

Dưới đây là toàn bộ chương trình mà bạn có thể dán vào một dự án console mới. Nó biên dịch ngay, với giả định bạn đã cài đặt gói NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Chạy chương trình, quan sát console, và bạn sẽ thấy mọi sự kiện phông chữ thiếu được in ra. Từ đó, bạn có thể quyết định cài đặt phông chữ thiếu, nhúng chúng, hoặc giữ nguyên fallback.

## Câu hỏi Thường gặp

**H: Điều này có hoạt động với chuyển đổi PDF không?**  
Có. Khi bạn sau này gọi `doc.Save("output.pdf")`, bất kỳ phông chữ nào đã được thay thế trong quá trình tải sẽ là những phông chữ được nhúng trong PDF. Vì vậy, việc bắt các cảnh báo sớm giúp bạn tránh những thay đổi phông chữ bất ngờ trong PDF cuối cùng.

**H: Nếu tôi có nhiều tài liệu cần xử lý thì sao?**  
Bao bọc logic tải trong một khối try‑catch và tái sử dụng một thể hiện `FontSettings` duy nhất cho các tài liệu. Điều này giảm tải và giữ cho bộ thu thập cảnh báo hoạt động cho mỗi tệp.

**H: Tôi có thể tắt hoàn toàn các cảnh báo không?**  
Bạn có thể đặt `loadOptions.WarningCallback = null;` trước khi tải, nhưng sẽ mất khả năng **phát hiện phông chữ thiếu** — thường không phải là điều bạn muốn.

## Kết luận

Chúng ta đã bao quát mọi thứ bạn cần để làm chủ **aspose font substitution**: bật bộ thu thập chẩn đoán, tải tệp Word với **cài đặt phông chữ** tùy chỉnh, trích xuất danh sách phông chữ thiếu, và thậm chí ghi đè quy tắc thay thế mặc định để **xử lý phông chữ thiếu** theo cách của bạn. Chỉ với vài dòng C#, bạn sẽ có được khả năng quan sát đầy đủ các vấn đề phông chữ mà nếu không sẽ ẩn sau những thay đổi bố cục tinh vi.

Bước tiếp theo? Hãy thử nhúng các phông chữ gốc vào tài liệu bằng `FontSettings.SetFontsFolder` hoặc khám phá `FontSourceBase` để tải phông chữ từ cơ sở dữ liệu. Bạn cũng có thể thử nghiệm với bộ sưu tập `Document.BuiltInStyle` để xem cách các thay đổi phông chữ ở mức độ style lan truyền như thế nào.

Có thêm câu hỏi về Aspose.Words hoặc quản lý phông chữ? Để lại bình luận, khám phá tài liệu chính thức của Aspose, hoặc khởi động một dự án mới và chơi thử với mã ở trên. Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng như mong muốn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}