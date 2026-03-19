---
category: general
date: 2026-03-19
description: Tìm hiểu cách bắt các cảnh báo trong Aspose.Words, thiết lập cài đặt
  phông chữ mặc định và phát hiện phông chữ thiếu khi tải tài liệu Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: vi
og_description: Cách bắt các cảnh báo trong Aspose.Words, thiết lập cài đặt phông
  chữ mặc định và phát hiện phông chữ thiếu khi tải tài liệu Word.
og_title: Cách ghi lại cảnh báo – Thiết lập cài đặt phông chữ mặc định
tags:
- Aspose.Words
- C#
- Document Processing
title: Cách ghi lại cảnh báo – Đặt cài đặt phông chữ mặc định
url: /vi/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Thu Thập Cảnh Báo – Đặt Cài Đặt Phông Mặc Định

**Cách thu thập cảnh báo** là nhu cầu phổ biến khi bạn làm việc với Aspose.Words, đặc biệt nếu tài liệu của bạn phụ thuộc vào các phông chữ cụ thể có thể không có trên máy đích. Đã bao giờ mở một tệp DOCX và tự hỏi tại sao bố cục lại bị lệch? Câu trả lời thường ẩn trong một cảnh báo về phông chữ bị thiếu.  

Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn **cách thu thập cảnh báo** khi **load word document**, cấu hình **set default font settings**, và cuối cùng **detect missing fonts** để bạn có thể phản hồi một cách lập trình. Không có phần thừa—chỉ có một ví dụ hoàn chỉnh, có thể chạy được và lý do cho mỗi dòng lệnh.

> *Mẹo chuyên nghiệp:* Thu thập cảnh báo sớm sẽ giúp bạn tránh việc gỡ lỗi những lỗi bố cục bí ẩn sau này.

---

## Những Gì Bạn Cần Chuẩn Bị

- **Aspose.Words for .NET** (phiên bản mới nhất tính đến năm 2026).  
- Môi trường phát triển .NET (Visual Studio, Rider, hoặc VS Code).  
- Một tệp DOCX mẫu tham chiếu tới một phông chữ bạn *không* có sẵn (ví dụ, *Comic Sans MS* trên máy Linux).  

Chỉ cần những thứ trên. Không cần thêm bất kỳ gói NuGet nào ngoài Aspose.Words.

---

## Bước 1 – Hiểu Vì Sao Bạn Cần Thu Thập Cảnh Báo

Khi Aspose.Words phân tích một tài liệu, nó có thể gặp phải các phông chữ không có trên máy chủ. Mặc định, thư viện sẽ âm thầm thay thế bằng một phông chữ dự phòng, điều này có thể làm thay đổi ngắt dòng, khoảng cách, và thậm chí khiến văn bản biến mất.  

Sử dụng **WarningCallback** cùng với đối tượng **FontSettings** mang lại cho bạn hai lợi ích:

1. **Visibility** – bạn nhận được một mục `WarningInfo` cho mỗi lần thay thế.  
2. **Control** – bạn có thể cấu hình trước một phông chữ mặc định để giảm thiểu bất ngờ về hình ảnh.

Hãy nghĩ nó như việc cài đặt một “watchdog” luôn hét lên mỗi khi động cơ thay đổi bộ phận dưới nắp capo.

---

## Bước 2 – Đặt Cài Đặt Phông Mặc Định

Từ khóa phụ thứ nhất, **set default font settings**, xuất hiện ngay tại đây. Bạn tạo một thể hiện `FontSettings` và tùy chọn chỉ tới thư mục chứa các phông chữ dự phòng của bạn.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Tại sao?**  
> Nếu bạn **không** chỉ định phông dự phòng, Aspose.Words sẽ chọn phông hệ thống đầu tiên khớp với kiểu, có thể hoàn toàn khác biệt. Bằng cách đặt một phông mặc định đã biết, bạn đảm bảo việc render nhất quán trên mọi máy.

---

## Bước 3 – Chuẩn Bị Callback Cảnh Báo Để Thu Thập Cảnh Báo

Bây giờ chúng ta sẽ **cách thu thập cảnh báo** bằng cách gắn một `WarningInfoCollection` vào các tùy chọn tải. Bộ sưu tập này sẽ lưu trữ mọi cảnh báo được phát ra trong quá trình tải.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

`WarningInfoCollection` thực thi `IWarningCallback`, vì vậy Aspose.Words sẽ tự động đẩy mỗi cảnh báo vào `warningInfos`. Không cần polling.

---

## Bước 4 – Tải Tài Liệu Word Với Các Tùy Chọn Đã Cấu Hình

Đây là nơi từ khóa phụ thứ hai, **load word document**, tỏa sáng. Chúng ta truyền cả `FontSettings` và `WarningCallback` thông qua một thể hiện `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Nếu tài liệu tham chiếu tới một phông chữ chưa được cài đặt, callback cảnh báo sẽ ghi nhận một mục `WarningType.FontSubstitution`.

---

## Bước 5 – Phát Hiện Các Phông Chữ Thiếu Từ Các Cảnh Báo Đã Thu Thập

Cuối cùng, chúng ta trả lời từ khóa phụ thứ ba, **detect missing fonts**, bằng cách duyệt qua các cảnh báo đã thu thập.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Kết quả điển hình trông như sau:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Dòng này cho bạn biết chính xác phông chữ nào bị thiếu và phông dự phòng nào đã được sử dụng — thông tin bạn có thể ghi log, hiển thị cho người dùng, hoặc thậm chí kích hoạt một quy trình cài đặt phông chữ tùy chỉnh.

---

## Ví Dụ Hoàn Chỉnh Có Thể Chạy

Dưới đây là toàn bộ chương trình bạn có thể sao chép‑dán vào một ứng dụng console. Nó minh họa **cách thu thập cảnh báo**, **đặt cài đặt phông mặc định**, **load word document**, và **detect missing fonts** trong một luồng duy nhất.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Kết quả mong đợi:** Khi DOCX được chỉ định tham chiếu tới một phông chữ chưa được cài đặt, console sẽ in ra một cảnh báo cho mỗi lần thay thế. Nếu tất cả phông chữ đều có, vòng lặp sẽ không xuất ra gì.

---

## Các Cạm Bẫy Thường Gặp & Trường Hợp Đặc Biệt

| Tình huống | Nguyên nhân | Cách xử lý |
|-----------|-------------|------------|
| **Không có cảnh báo nào xuất hiện** mặc dù bố cục trông sai | Tài liệu có thể đang sử dụng phông chữ *embedded*, mà Aspose.Words render mà không cần thay thế. | Kiểm tra `Document.HasEmbeddedFonts` và cân nhắc trích xuất các phông chữ nhúng nếu bạn cần chúng trên máy khác. |
| **Multiple warnings for the |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}