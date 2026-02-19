---
category: general
date: 2026-02-18
description: Tìm hiểu cách bắt các cảnh báo phông chữ và phát hiện phông chữ thiếu
  trong C# bằng Aspose.Words. Hãy làm theo hướng dẫn từng bước này để xử lý phông
  chữ thiếu một cách hiệu quả.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: vi
og_description: Ghi lại cảnh báo phông chữ trong C# và học cách phát hiện, xử lý và
  liệt kê các phông chữ thiếu với ví dụ mã đầy đủ.
og_title: Bắt các Cảnh báo Font trong C# – Hướng dẫn toàn diện
tags:
- Aspose.Words
- C#
- Font Management
title: Bắt cảnh báo phông chữ trong C# – Hướng dẫn lập trình đầy đủ
url: /vi/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

translate.

Make sure to keep **bold** formatting.

Let's produce.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ghi lại Cảnh báo Phông chữ trong C# – Hướng dẫn Lập trình Toàn diện

Bạn đã bao giờ tự hỏi làm thế nào để **ghi lại cảnh báo phông chữ** khi một tài liệu tham chiếu tới một phông chữ chưa được cài đặt trên máy chủ chưa? Bạn không phải là người duy nhất. Trong nhiều ứng dụng doanh nghiệp, việc thiếu phông chữ gây ra các lỗi bố cục, và cách duy nhất đáng tin cậy để phát hiện chúng là lắng nghe các cảnh báo mà thư viện ném ra.  

Trong tutorial này, chúng tôi sẽ cho bạn một giải pháp sẵn sàng chạy mà không chỉ **ghi lại cảnh báo phông chữ** mà còn **phát hiện phông chữ thiếu**, **xử lý phông chữ thiếu**, và thậm chí **liệt kê phông chữ thiếu** để bạn có thể quyết định thay thế, nhúng, hoặc cảnh báo người dùng. Không cần tài liệu bên ngoài—chỉ cần sao chép, dán và chạy.

## Những gì bạn sẽ học

- Cách cấu hình `LoadOptions` để bật cảnh báo thay thế phông chữ.  
- Mã chính xác bạn cần để tải một tệp DOCX và lấy ra mọi cảnh báo.  
- Tại sao mỗi bước lại quan trọng, bao gồm các cân nhắc về hiệu năng.  
- Xử lý các trường hợp đặc biệt như tài liệu có phông chữ hỗn hợp hoặc thư mục phông chữ tùy chỉnh.  

**Yêu cầu trước**: .NET 6+ (hoặc .NET Framework 4.6+), một tham chiếu tới gói NuGet **Aspose.Words**, và kiến thức cơ bản về C#. Nếu bạn chưa từng dùng Aspose.Words, đừng lo—hướng dẫn này sẽ dẫn bạn qua mọi chi tiết.

![Diagram showing capture font warnings flow](image.png){alt="sơ đồ ghi lại cảnh báo phông chữ"}

## Ghi lại Cảnh báo Phông chữ – Tại sao lại quan trọng

Khi Aspose.Words tải một tài liệu, nó lặng lẽ thay thế bất kỳ phông chữ nào không có sẵn bằng một phông chữ dự phòng. Phông chữ dự phòng này giữ cho quá trình tải vẫn tiếp tục, nhưng kết quả hiển thị có thể hoàn toàn lệch. Bằng cách bật cờ **SubstitutionWarningLevel.All**, thư viện sẽ thêm một mục `WarningInfo` cho mỗi phông chữ thiếu, cho phép bạn **phát hiện phông chữ thiếu** trước khi tài liệu được render hoặc lưu.

> **Mẹo chuyên nghiệp:** Nếu bạn đang xử lý hàng trăm tệp trong một công việc batch, việc ghi lại các cảnh báo này vào một kho lưu trữ trung tâm có thể tiết kiệm cho bạn hàng giờ kiểm tra thủ công sau này.

## Bước 1: Thiết lập Dự án của Bạn

1. Mở IDE yêu thích của bạn (Visual Studio, Rider, VS Code).  
2. Tạo một dự án console mới:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Thêm gói Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Xong—không cần DLL bổ sung, không cần COM interop. Thư viện đã bao gồm mọi thứ bạn cần để **xử lý phông chữ thiếu**.

## Bước 2: Chuẩn bị Load Options để Ghi lại Tất cả Cảnh báo Thay thế Phông chữ

Để engine **ghi lại cảnh báo phông chữ**, bạn phải yêu cầu nó ghi lại mọi lần thay thế. Đoạn mã dưới đây tạo một thể hiện `LoadOptions`, bật mức cảnh báo, và (tùy chọn) chỉ định một thư mục chứa các phông chữ tùy chỉnh mà bạn có thể muốn sử dụng.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Tại sao điều này quan trọng:**  
- `SubstitutionWarningLevel.All` đảm bảo **mọi** sự kiện phông chữ thiếu đều được ghi lại, không chỉ lần đầu tiên.  
- Nếu không bật cờ này, Aspose.Words sẽ lặng lẽ thay thế phông chữ và bạn sẽ không bao giờ biết có vấn đề.

## Bước 3: Tải Tài liệu bằng Các Tuỳ chọn Đã Cấu hình

Bây giờ chúng ta thực sự mở tệp. Thay `DocumentWithMissingFonts.docx` bằng đường dẫn tới tài liệu thử nghiệm của bạn.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Nếu tệp chứa bất kỳ tham chiếu tới phông chữ nào không có trên máy (hoặc trong thư mục tùy chọn bạn đã thêm), `document.WarningInfoCollection` sẽ được điền đầy.

## Bước 4: Tìm và Hiển thị Các Cảnh báo Thay thế Phông chữ

Đây là phần cốt lõi của tutorial: lặp qua `WarningInfoCollection` để **liệt kê các phông chữ thiếu**. Chúng ta sẽ lọc theo `WarningType.FontSubstitution` và in ra một thông điệp thân thiện.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Kết quả Dự kiến

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Nếu tài liệu chỉ sử dụng các phông chữ đã được cài đặt, bạn sẽ thấy dòng “✅ No missing fonts detected”.

## Bước 5: Nâng cao – Cách **Xử lý Phông chữ Thiếu** một cách Chương trình

Chỉ in ra danh sách có thể đủ cho một công cụ chẩn đoán, nhưng nhiều hệ thống sản xuất cần **xử lý phông chữ thiếu** một cách tự động. Dưới đây là hai chiến lược phổ biến:

### 5.1 Thay thế bằng Phông chữ Dự phòng đã Biết

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Nhúng Phông chữ Tùy chỉnh Khi Cần

Nếu bạn có một tệp phông chữ công ty (`MyBrand.ttf`), bạn có thể nhúng nó khi phát hiện phông chữ thiếu:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Lưu ý:** Nhúng phông chữ có thể làm tăng kích thước tệp đầu ra, vì vậy hãy cân nhắc giữa độ trung thực và băng thông.

## Những Sai Lầm Thường Gặp và Cách Tránh

| Triệu chứng | Nguyên nhân Có thể | Cách khắc phục |
|------------|-------------------|----------------|
| Không có cảnh báo nào xuất hiện dù tài liệu trông sai | `SubstitutionWarningLevel` chưa được đặt thành `All` | Đảm bảo bước 2 đã thiết lập cờ đúng như hướng dẫn |
| Cảnh báo liệt kê cùng một phông chữ nhiều lần | Tài liệu chứa phông chữ trong nhiều kiểu | Loại bỏ trùng lặp nếu bạn chỉ cần danh sách duy nhất: `fontWarnings.Select(w => w.Description).Distinct()` |
| Ứng dụng bị sập khi xử lý các tệp DOCX lớn | Tải với cài đặt bộ nhớ mặc định | Sử dụng `LoadOptions.LoadFormat` hoặc stream tệp để giảm áp lực bộ nhớ |

## Ví dụ Hoàn chỉnh (Sẵn sàng Sao chép‑Dán)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Chạy chương trình bằng `dotnet run`. Bạn sẽ thấy danh sách các phông chữ thiếu được in ra console, xác nhận rằng bạn đã **ghi lại thành công các cảnh báo phông chữ**.

## Kết luận

Bạn đã có một mẫu hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **ghi lại cảnh báo phông chữ**, **phát hiện phông chữ thiếu**, **xử lý phông chữ thiếu**, và **liệt kê phông chữ thiếu** bằng Aspose.Words trong C#. Cách tiếp cận này nhẹ, chỉ cần vài dòng mã, và có thể được đưa vào bất kỳ pipeline hiện có nào—dù bạn

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}