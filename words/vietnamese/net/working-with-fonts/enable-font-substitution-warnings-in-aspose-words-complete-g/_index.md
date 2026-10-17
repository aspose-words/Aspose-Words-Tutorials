---
category: general
date: 2026-01-11
description: Bật cảnh báo thay thế phông chữ để phát hiện các phông chữ thiếu trong
  tài liệu .NET của bạn. Tìm hiểu cách lấy tên phông chữ thiếu và liệt kê các phông
  chữ thiếu bằng Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: vi
og_description: Bật cảnh báo thay thế phông chữ trong Aspose.Words để phát hiện phông
  chữ thiếu, lấy tên phông chữ thiếu và liệt kê các phông chữ thiếu trong tài liệu
  của bạn.
og_title: Bật Cảnh Báo Thay Thế Phông Chữ – Hướng Dẫn C# Từng Bước
tags:
- Aspose.Words
- C#
- Document Processing
title: Kích hoạt Cảnh báo Thay thế Phông chữ trong Aspose.Words – Hướng dẫn đầy đủ
url: /vi/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kích hoạt Cảnh báo Thay thế Phông chữ – Hướng dẫn đầy đủ

Bạn đã bao giờ tự hỏi tại sao một tài liệu Word trông hơi lệch sau khi tải lên máy chủ chưa? Rất có thể phông chữ mà tác giả gốc đã sử dụng không có trên máy của bạn, và Aspose.Words đã âm thầm thay thế nó bằng phông chữ gần nhất. **Kích hoạt cảnh báo thay thế phông chữ** và bạn sẽ ngay lập tức biết phông chữ nào bị thiếu, chúng đã được thay thế bằng gì, và cách xử lý thông tin đó.

Trong hướng dẫn này, chúng tôi sẽ đi qua một ví dụ thực tế, từ đầu đến cuối, cho bạn thấy cách **phát hiện phông chữ bị thiếu**, lấy **tên phông chữ bị thiếu**, và thậm chí **liệt kê các phông chữ bị thiếu** để báo cáo. Không có phần thừa thãi, chỉ có giải pháp rõ ràng mà bạn có thể đưa vào bất kỳ dự án .NET nào ngay hôm nay.

---

## Bạn sẽ học được gì

- Cách cấu hình `LoadOptions` để Aspose.Words phát ra các cảnh báo chi tiết.
- Mã chính xác cần thiết để tải tài liệu và liệt kê các cảnh báo liên quan đến phông chữ.
- Cách trích xuất tên phông chữ bị thiếu và sự thay thế của nó, sau đó xuất ra báo cáo gọn gàng.
- Mẹo xử lý các trường hợp đặc biệt, chẳng hạn như tài liệu có hàng chục phông chữ bị thiếu hoặc thư mục phông chữ tùy chỉnh.

### Yêu cầu trước

- .NET 6+ (mã cũng hoạt động với .NET Framework 4.7+)
- Aspose.Words cho .NET 23.10 trở lên (bạn có thể lấy từ NuGet)
- Một tệp DOCX mẫu tham chiếu đến phông chữ bạn chưa cài đặt (chúng tôi sẽ gọi nó là `MissingFont.docx`)

Nếu bạn đã có những điều cơ bản này, hãy bắt đầu.

---

## Bước 1: Thiết lập LoadOptions để Kích hoạt Cảnh báo Thay thế Phông chữ  

Điều đầu tiên bạn cần làm là thông báo cho Aspose.Words rằng bạn quan tâm đến các phông chữ bị thiếu. Theo mặc định, thư viện chỉ ghi cảnh báo nội bộ. Đặt `SubstitutionWarningLevel` thành `Typical` (hoặc `All` để có đầu ra chi tiết nhất) sẽ bật tính năng này.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Tại sao điều này quan trọng:**  
Khi `SubstitutionWarningLevel` được đặt, mỗi khi Aspose.Words không thể tìm thấy phông chữ được tham chiếu, nó sẽ thêm một `FontSubstitutionWarning` vào bộ sưu tập `Warnings` của tài liệu. Bộ sưu tập này là cách duy nhất đáng tin cậy để **phát hiện phông chữ bị thiếu** mà không cần phân tích tài liệu thủ công.

> **Mẹo chuyên nghiệp:** Nếu bạn đang xử lý một loạt tài liệu và muốn chắc chắn bắt được mọi sự thay thế, hãy sử dụng `FontSubstitutionWarningLevel.All`. Nó sẽ hơi ồn hơn nhưng đảm bảo không có cảnh báo nào bị bỏ lỡ.

---

## Bước 2: Tải tài liệu bằng các tùy chọn đã cấu hình  

Bây giờ hệ thống cảnh báo đã sẵn sàng, hãy tải DOCX của bạn bằng `LoadOptions` vừa chuẩn bị. Đường dẫn có thể là tuyệt đối hoặc tương đối; chỉ cần chắc chắn tệp tồn tại.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Điều gì đang diễn ra phía sau?**  
Aspose.Words phân tích XML của tài liệu, xác định mỗi phần tử `<w:font>`, và kiểm tra danh mục phông chữ của hệ thống (cùng với bất kỳ thư mục phông chữ tùy chỉnh nào bạn đã thêm vào `FontSettings`). Khi không thể tìm thấy phông chữ, nó ghi lại một cảnh báo — chính xác những gì chúng ta cần để **liệt kê các phông chữ bị thiếu** sau này.

---

## Bước 3: Duyệt qua các Cảnh báo và Trích xuất Chi tiết Phông chữ Bị Thiếu  

Với tài liệu đã được nạp vào bộ nhớ, bộ sưu tập `Warnings` chứa mọi `FontSubstitutionWarning`. Chúng ta sẽ lặp qua nó, lọc theo loại phù hợp, và in ra một báo cáo thân thiện.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Kết quả mong đợi** (giả sử tài liệu nguồn tham chiếu `MyCustomFont` mà không được cài đặt):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Lưu ý mỗi mục đều cung cấp cả **tên phông chữ bị thiếu** (`MyCustomFont`) và phông chữ thay thế (`Arial`). Đó chính là thông tin bạn cần để quyết định có nên nhúng phông chữ gốc, yêu cầu tác giả cung cấp phông chữ thay thế, hay chỉ đơn giản chấp nhận sự thay thế.

---

## Bước 4: Tùy chọn – Thu thập Dữ liệu vào Danh sách để Xử lý Tiếp theo  

Nếu bạn cần xuất báo cáo ra CSV, gửi qua API, hoặc chỉ lưu trong bộ nhớ để sử dụng sau, bạn có thể lưu các cảnh báo vào một danh sách có kiểu mạnh.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Bây giờ bạn đã **liệt kê các phông chữ bị thiếu** ở định dạng mà bất kỳ hệ thống nào phía sau có thể tiêu thụ. Dù bạn đang cung cấp dữ liệu cho bảng điều khiển hay tạo nhật ký kiểm toán, dữ liệu đã sẵn sàng.

---

## Bước 5: Xử lý Các Trường hợp Đặc biệt và Những Cạm bẫy Thông thường  

### Nhiều Phông chữ Bị Thiếu trong Một Lần Chạy  

Các mẫu doanh nghiệp lớn thường tham chiếu tới hàng chục phông chữ tùy chỉnh. Bộ sưu tập cảnh báo có thể trở nên lớn, nhưng mẫu lặp được trình bày ở trên mở rộng tuyến tính, vì vậy hiệu năng không phải là vấn đề. Chỉ cần nhớ giữ đầu ra dễ đọc — việc nhóm theo trang hoặc kiểu có thể hữu ích nếu bạn cần phân tích sâu hơn.

### Thư mục Phông chữ Tùy chỉnh  

Nếu bạn lưu phông chữ trong thư mục không chuẩn (ví dụ: một thư mục chia sẻ trên mạng), hãy cho Aspose.Words biết nơi tìm kiếm:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Việc thiết lập này *trước* khi tải tài liệu cho thư viện cơ hội tìm thấy các phông chữ, có thể loại bỏ hoàn toàn một số cảnh báo.

### Loại bỏ Các Cảnh báo Cụ thể  

Đôi khi bạn biết một sự thay thế cụ thể là chấp nhận được (ví dụ: một phông chữ trang trí mà bạn không quan tâm tới việc thay thế). Bạn có thể lọc chúng ra sau khi thu thập:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Tương thích Phiên bản  

Enum `FontSubstitutionWarningLevel` đã ổn định kể từ Aspose.Words 20.12. Nếu bạn đang dùng phiên bản cũ hơn, có thể cần nâng cấp để truy cập tính năng mức cảnh báo.

---

## Ví dụ Hoàn chỉnh  

Dưới đây là chương trình hoàn chỉnh, sẵn sàng chạy, tích hợp tất cả các bước ở trên. Dán nó vào một dự án console mới, thêm gói NuGet Aspose.Words, và chỉ định `docPath` tới tài liệu có tham chiếu đến phông chữ bị thiếu.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Chạy chương trình này sẽ **kích hoạt cảnh báo thay thế phông chữ**, **phát hiện phông chữ bị thiếu**, **lấy tên phông chữ bị thiếu**, và **liệt kê các phông chữ bị thiếu** cả trên console và trong tệp CSV.

---

## Kết luận  

Chúng tôi vừa trình bày mọi thứ bạn cần để **kích hoạt cảnh báo thay thế phông chữ** trong Aspose.Words, từ cấu hình ban đầu đến việc trích xuất danh sách phông chữ bị thiếu sạch sẽ. Bằng cách làm theo các bước trên, bạn sẽ có thể kiểm tra tài liệu, đảm bảo độ chính xác hình ảnh, và tránh những bất ngờ không mong muốn khi hiển thị trên máy chủ.

Tiếp theo, bạn có thể khám phá:

- **Nhúng phông chữ bị thiếu** trực tiếp vào PDF hoặc DOCX đầu ra (sử dụng `FontSettings.EmbeddedFonts`).
- **Tự động cài đặt phông chữ** trên các máy build dựa trên báo cáo đã tạo.
- **Tích hợp với quy trình CI** để làm thất bại các build khi phông chữ quan trọng thiếu.

Hãy thử những điều trên, và bạn sẽ biến một hệ thống cảnh báo đơn giản thành quy trình quản lý phông chữ đầy đủ.

Chúc lập trình vui vẻ, và hy vọng mọi phông chữ của bạn đều được tìm thấy!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}