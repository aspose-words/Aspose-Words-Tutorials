---
category: general
date: 2025-12-31
description: Ghi lại cảnh báo phông chữ trong Aspose.Words để phát hiện phông chữ
  thiếu và liệt kê các phông chữ thiếu trong ứng dụng .NET của bạn. Tìm hiểu giải
  pháp C# từng bước.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: vi
og_description: Ghi lại cảnh báo phông chữ trong Aspose.Words để phát hiện phông chữ
  thiếu và liệt kê các phông chữ thiếu. Hướng dẫn C# đầy đủ kèm mã và mẹo.
og_title: Ghi lại Cảnh báo Phông chữ – Phát hiện & Liệt kê Phông chữ Thiếu
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Ghi lại Cảnh báo Phông chữ – Phát hiện và Liệt kê Các Phông chữ Thiếu
url: /vi/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ghi lại Cảnh báo Phông chữ – Phát hiện & Liệt kê Phông chữ Thiếu

Bạn đã bao giờ cần **ghi lại các cảnh báo phông chữ** khi tải một tài liệu Word nhưng không biết cách hiển thị chi tiết các phông chữ bị thiếu? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế, các phông chữ thiếu gây ra lỗi bố cục, và nếu không có cảnh báo thích hợp, bạn sẽ phải truy tìm những lỗi ảo.  

Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách **phát hiện các phông chữ thiếu** và **liệt kê các phông chữ thiếu** bằng Aspose.Words cho .NET. Khi kết thúc, bạn sẽ có một đoạn mã C# sẵn sàng chạy, in ra mọi cảnh báo thay thế, để bạn có thể ghi log, cảnh báo, hoặc thậm chí thay thế phông chữ một cách tự động.

---

## Tại sao Việc Ghi lại Cảnh báo Phông chữ lại Quan trọng

Khi Aspose.Words mở một tệp DOCX tham chiếu tới một phông chữ chưa được cài đặt trên máy chủ, nó sẽ im lặng thay thế bằng phông chữ dự phòng. Tài liệu trông ổn, nhưng độ chính xác về hình ảnh bị ảnh hưởng — ví dụ như logo thương hiệu công ty được hiển thị bằng kiểu chữ sai.  

Ghi lại những cảnh báo này giúp bạn:

* **Duy trì tính nhất quán thương hiệu** – bạn biết chính xác phông chữ nào đang thiếu.  
* **Tự động khắc phục** – thay thế các phông chữ thiếu bằng chương trình.  
* **Kiểm tra tuân thủ** – tạo báo cáo cho các cuộc đánh giá pháp lý hoặc thiết kế.  

Nói tóm lại, **ghi lại cảnh báo phông chữ** là hàng rào đầu tiên chống lại việc thay thế phông chữ âm thầm.

---

## Cấu hình LoadOptions để Phát hiện Phông chữ Thiếu

Yếu tố then chốt để hiển thị các cảnh báo là thuộc tính `LoadOptions.FontSubstitutionWarning`. Mặc định nó được đặt là `None`, có nghĩa là Aspose.Words sẽ nuốt chửng các thông báo. Đặt nó thành `All` sẽ yêu cầu thư viện ghi lại mọi sự kiện thay thế.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Mẹo chuyên nghiệp:** Nếu bạn đã có một thư mục phông chữ tùy chỉnh, hãy gán nó cho `FontSettings.SetFontsFolder("path")` trước khi tải tài liệu. Như vậy bạn có thể **phát hiện các phông chữ thiếu** mà không có trong thư mục hệ thống.

---

## Tải Tài liệu và Liệt kê Phông chữ Thiếu

Khi `LoadOptions` sẵn sàng, bước tiếp theo là tải tệp Word. Hàm khởi tạo chấp nhận đối tượng tùy chọn, và bất kỳ lần thay thế nào sẽ được ghi lại trong `WarningInfoCollection` của tài liệu.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Nếu tệp tham chiếu tới các phông chữ không có, mỗi phông chữ thiếu sẽ tạo ra một mục `WarningInfo`. Bạn có thể **liệt kê các phông chữ thiếu** bằng cách duyệt qua bộ sưu tập này.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

Kết quả thường trông như sau:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Mỗi dòng cho bạn biết chính xác phông chữ nào đã bị thiếu, đáp ứng yêu cầu **liệt kê các phông chữ thiếu**.

---

## Đọc và Giải thích WarningInfoCollection

`WarningInfoCollection` có thể chứa nhiều loại cảnh báo khác nhau (ví dụ: `DocumentStructure`, `ImageLoading`). Để chỉ tập trung vào vấn đề phông chữ, hãy lọc theo `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Tại sao phải lọc? Vì một tài liệu lớn có thể cũng tạo ra các cảnh báo về hình ảnh bị hỏng hoặc tính năng không hỗ trợ. Khi thu hẹp bộ sưu tập, bạn loại bỏ tiếng ồn và giữ cho đầu ra **ghi lại cảnh báo phông chữ** sạch sẽ.

---

## Ví dụ Hoàn chỉnh – Ghi lại Cảnh báo Phông chữ trong Thực tế

Dưới đây là chương trình đầy đủ, tự chứa, bạn có thể chèn vào bất kỳ dự án console .NET nào. Nó minh họa mọi bước từ cấu hình `LoadOptions` đến việc in ra danh sách phông chữ thiếu gọn gàng.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Kết quả dự kiến trên console**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Nếu tài liệu không có phông chữ nào thiếu, bạn sẽ thấy:

```
All referenced fonts are available – no warnings captured.
```

---

## Các Trường hợp Đặc biệt Thường Gặp & Cách Xử Lý

| Tình huống | Nguyên nhân | Giải pháp đề xuất |
|-----------|-------------|-------------------|
| **Tài liệu sử dụng phông chữ OpenType nhúng** | Aspose.Words có thể đọc phông chữ nhúng, nhưng chỉ khi tệp không bị hỏng. | Kiểm tra DOCX trong Word trước; nếu cần, nhúng lại phông chữ. |
| **Số lượng cảnh báo lớn** (ví dụ: >200 phông chữ thiếu) | Các import hàng loạt từ hệ thống cũ thường tham chiếu tới một dải phông chữ rộng. | Xử lý cảnh báo theo lô: lưu vào cơ sở dữ liệu, sau đó chạy script cài đặt phông chữ. |
| **WarningInfoCollection rỗng** | Hoặc tài liệu đã có đầy đủ phông chữ, hoặc `FontSubstitutionWarning` vẫn để ở `None`. | Kiểm tra lại cấu hình `LoadOptions` và chắc chắn bạn đang tải đúng đường dẫn tệp. |
| **Phông chữ tùy chỉnh nằm trên ổ chia mạng** | Độ trễ mạng có thể gây timeout khi tra cứu phông chữ. | Tải trước các phông chữ vào `FontSettings` bằng `SetFontsFolder` và bật `CacheFontData = true`. |

Những mẹo này giúp bạn **phát hiện các phông chữ thiếu** một cách đáng tin cậy, ngay cả trong môi trường phức tạp.

---

## Hình minh họa

![capture font warnings example](https://example.com/images/capture-font-warnings.png "capture font warnings example")

*Ảnh chụp màn hình cho thấy một lần chạy console nơi hai phông chữ thiếu được báo cáo.*

---

## Các Bước Tiếp Theo – Vượt Qua Báo cáo Đơn giản

Bây giờ bạn đã có thể **ghi lại cảnh báo phông chữ**, hãy cân nhắc tự động hoá việc khắc phục:

1. **Thay thế Phông chữ Tự động** – Thay thế các phông chữ thiếu bằng phông chữ dự phòng được công ty phê duyệt bằng cách chỉnh `FontSettings.SubstitutionSettings`.  
2. **Ghi log vào Hệ thống Giám sát** – Đưa các thông báo cảnh báo vào Serilog, ELK, hoặc Azure Application Insights.  
3. **Báo cáo Dành cho Người Dùng** – Tạo bản tóm tắt HTML hoặc PDF để các nhà thiết kế xem xét những phông chữ cần được cài đặt.

Tất cả các mở rộng này dựa trên nền tảng đã trình bày: cấu hình `LoadOptions`, tải tài liệu, và đọc `WarningInfoCollection`.

---

## Kết luận

Bạn vừa học cách **ghi lại cảnh báo phông chữ** trong Aspose.Words, **phát hiện các phông chữ thiếu**, và **liệt kê các phông chữ thiếu** với đầu ra sạch sẽ, thân thiện với console. Cách tiếp cận này đơn giản, chỉ cần vài dòng C#, và hoạt động với bất kỳ phiên bản .NET nào hỗ trợ Aspose.Words 23.x trở lên.  

Hãy thử trên một tệp DOCX mẫu mà bạn cố tình gỡ bỏ một phông chữ – bạn sẽ ngay lập tức thấy các cảnh báo xuất hiện. Từ đó, bạn có thể quyết định cài đặt các phông chữ thiếu, thay thế chúng bằng chương trình, hoặc chỉ ghi lại vấn đề để xem xét sau.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng phông chữ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}