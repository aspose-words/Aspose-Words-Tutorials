---
category: general
date: 2026-02-21
description: Tìm hiểu cách bật cảnh báo, phát hiện phông chữ thiếu và cách tải tài
  liệu docx một cách an toàn bằng Aspose.Words trong C#. Thực hiện theo hướng dẫn
  từng bước.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: vi
og_description: Cách bật cảnh báo, phát hiện phông chữ thiếu và tải đúng các tệp docx
  bằng Aspose.Words. Bao gồm ví dụ mã hoàn chỉnh.
og_title: Cách bật cảnh báo và phát hiện phông chữ thiếu khi tải DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Cách bật cảnh báo và phát hiện phông chữ thiếu khi tải tệp DOCX
url: /vi/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

X file to capturing font substitution warnings – how to enable warnings in Aspere.Words". Should translate alt text but keep the URL unchanged.

Also translate the "Pro tip:" etc.

Let's produce final content.

Be careful with bullet lists: keep dash and spacing.

Translate "How to enable warnings and detect missing fonts when loading DOCX files" to Vietnamese: "Cách bật cảnh báo và phát hiện phông chữ thiếu khi tải tệp DOCX".

Proceed.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách bật cảnh báo và phát hiện phông chữ thiếu khi tải tệp DOCX

Bạn đã bao giờ tự hỏi **cách bật cảnh báo** cho các phông chữ thiếu trước khi chúng âm thầm làm hỏng việc hiển thị tài liệu? Bạn không phải là người duy nhất—hầu hết các nhà phát triển cho rằng thư viện sẽ “làm đúng việc”, chỉ để sau này phát hiện ra một phông chữ đã bị thay thế mà không có bất kỳ dấu hiệu nào.  

Trong tutorial này chúng tôi sẽ chỉ cho bạn **cách bật cảnh báo**, **cách phát hiện phông chữ thiếu**, và cách **tải docx** đúng cách bằng Aspose.Words cho .NET. Khi hoàn thành, bạn sẽ có một mẫu có thể chạy ngay, in mọi cảnh báo thay thế phông chữ ra console, để bạn không còn phải đoán mò những gì đã xảy ra trong tệp.

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng chạy trên .NET Framework 4.7+)  
- Visual Studio 2022 hoặc bất kỳ IDE C# nào bạn thích  
- Gói NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  
- Một tệp DOCX có thể chứa các phông chữ chưa được cài đặt trên máy của bạn (chúng tôi sẽ gọi nó là `input.docx`)

> **Mẹo chuyên nghiệp:** Nếu bạn chưa có tệp thử nghiệm, chỉ cần mở một tài liệu Word sử dụng phông chữ công ty tùy chỉnh và lưu lại dưới tên `input.docx`. Điều này sẽ kích hoạt cảnh báo mà chúng ta muốn bắt.

## Tổng quan về giải pháp

1. **Tạo** một đối tượng `LoadOptions` với `FontSubstitutionWarnings` được bật.  
2. **Tải** tệp DOCX bằng các tùy chọn đó.  
3. **Kiểm tra** bộ sưu tập `WarningCallback` để tìm bất kỳ mục `FontSubstitution` nào.  
4. **Phản hồi** – bạn có thể ghi log, hiển thị, hoặc thậm chí thay thế phông chữ thiếu một cách lập trình.

Dưới đây chúng tôi sẽ phân tích từng bước, giải thích *tại sao* nó quan trọng, và cung cấp cho bạn một đoạn mã hoàn chỉnh, có thể chạy.

---

## Bước 1: Cài đặt Aspose.Words và thiết lập dự án

Trước khi chúng ta có thể **cách bật cảnh báo**, chúng ta cần thư viện thực sự hỗ trợ tính năng này.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Hoặc, trong Visual Studio Package Manager Console:

```powershell
Install-Package Aspose.Words
```

> **Tại sao cần bước này?**  
> Nếu không có gói này, các lớp `LoadOptions`, `Document` và cơ chế cảnh báo sẽ không tồn tại. Thêm tham chiếu NuGet đảm bảo bạn đang sử dụng phiên bản ổn định mới nhất (tại thời điểm viết, 24.5).

---

## Bước 2: Tạo load options bật cảnh báo thay thế phông chữ

Trái tim của **cách bật cảnh báo** nằm trong lớp `LoadOptions`. Đặt `FontSubstitutionWarnings` thành `true` sẽ yêu cầu engine ghi lại mỗi lần nó phải thay thế một phông chữ thiếu.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Tại sao phải bật cờ này?**  
> Mặc định Aspose.Words sẽ âm thầm thay thế các phông chữ thiếu bằng một phông dự phòng (thường là Arial). Điều này có thể gây ra dịch chuyển bố cục, ký tự không hiển thị, hoặc vi phạm thương hiệu. Bật cờ này giúp bạn có toàn bộ thông tin.

---

## Bước 3: Tải tệp DOCX bằng các tùy chọn đã cấu hình

Bây giờ chúng ta đã biết **cách tải docx** với cảnh báo được bật, chúng ta thực hiện việc tải.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Điều gì xảy ra phía sau?**  
> Khi phân tích DOCX, Aspose.Words sẽ kiểm tra mọi phần tử `<w:rFonts>`. Nếu phông chữ được chỉ định chưa được cài đặt, nó sẽ ghi lại một cảnh báo `FontSubstitution` và chuyển sang phông mặc định. Vì chúng ta đã bật cảnh báo, các mục này sẽ xuất hiện trong `document.WarningCallback.Warnings`.

---

## Bước 4: Lấy và hiển thị các cảnh báo thay thế phông chữ

Thuộc tính `WarningCallback` chứa một `WarningInfoCollection`. Duyệt qua nó, lọc các mục có `WarningType.FontSubstitution`, và in ra thông báo.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Kết quả mong đợi** (ví dụ):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Bạn sẽ làm gì với những thông báo này?**  
> Bạn có thể ghi chúng vào file, hiển thị trong giao diện người dùng, hoặc thậm chí kích hoạt một quy trình thay thế phông chữ tùy chỉnh. Điều quan trọng là bây giờ bạn *phát hiện được phông chữ thiếu* thay vì đoán mò sau này.

---

## Bước 5: (Tùy chọn) Thay thế phông chữ thiếu bằng một phông dự phòng cụ thể

Nếu bạn có một phông chữ công ty muốn áp dụng nhất quán, bạn có thể xử lý các cảnh báo và thay thế chúng ngay lập tức.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Tại sao nên cân nhắc việc này?**  
> Nó đảm bảo tính nhất quán về hình ảnh trên mọi tài liệu được tạo, điều rất quan trọng cho việc tuân thủ thương hiệu.

---

## Ví dụ đầy đủ, có thể chạy

Dưới đây là một file C# duy nhất mà bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm mọi thứ—from cài đặt gói tới in cảnh báo.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Chạy nó**: `dotnet run` từ thư mục dự án. Nếu có bất kỳ phông chữ nào thiếu, bạn sẽ thấy các cảnh báo được in ra, và việc thay thế tùy chọn sẽ được áp dụng trước khi lưu file.

---

## Câu hỏi thường gặp

### Điều này có hoạt động với chuyển đổi PDF không?

Có. Sau khi xử lý các cảnh báo, bạn có thể gọi `doc.Save("output.pdf")` và các phông chữ đã được thay thế sẽ xuất hiện trong PDF giống như trong DOCX.

### Nếu tôi muốn bỏ qua cảnh báo cho một phông chữ cụ thể thì sao?

Bạn có thể lọc chúng trong vòng lặp—chỉ cần bỏ qua `WarningInfo` có `Message` chứa tên phông chữ bạn muốn bỏ qua.

### `FontSubstitutionWarnings` có có trong các phiên bản Aspose.Words cũ không?

Tính năng này được giới thiệu từ phiên bản 20.5. Nếu bạn đang dùng phiên bản cũ hơn, hãy nâng cấp qua NuGet; thay đổi API vẫn tương thích ngược.

---

## Kết luận

Chúng ta đã đi qua **cách bật cảnh báo**, chỉ ra **cách phát hiện phông chữ thiếu**, và trình bày cách **tải docx** đúng cách với Aspose.Words đồng thời giữ được toàn bộ thông tin về các lần thay thế phông chữ. Bằng cách kiểm tra `document.WarningCallback.Warnings` bạn sẽ có một bản ghi đáng tin cậy—không còn những lần thay thế âm thầm nữa.

Bước tiếp theo? Hãy tích hợp logic cảnh báo vào framework ghi log như Serilog, hoặc xây dựng UI hiển thị các phông chữ thiếu trước khi phát hành tài liệu cho người dùng. Bạn cũng có thể khám phá lớp `FontSettings` để kiểm soát chi tiết hơn các chính sách thay thế phông chữ.

Chúc lập trình vui vẻ, và hy vọng tài liệu của bạn luôn hiển thị đúng như mong muốn! 

![Diagram illustrating the flow from loading a DOCX file to capturing font substitution warnings – how to enable warnings in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}