---
category: general
date: 2026-03-13
description: Cách bắt các cảnh báo khi tải tài liệu bằng Aspose.Words, kèm các mẹo
  xử lý phông chữ thiếu và thiết lập cài đặt phông chữ tùy chỉnh. Tìm hiểu giải pháp
  C# đầy đủ.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: vi
og_description: Cách bắt các cảnh báo khi tải tệp Word bằng Aspose.Words, cùng các
  cách thực tế để xử lý phông chữ thiếu và thiết lập cài đặt phông chữ tùy chỉnh.
og_title: Cách bắt cảnh báo trong Aspose.Words – Hướng dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Document Processing
title: Cách bắt các cảnh báo trong Aspose.Words – Hướng dẫn chi tiết
url: /vi/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

top button.

Make sure to keep them.

Now craft final answer.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Ghi Nhận Cảnh Báo trong Aspose.Words – Hướng Dẫn Đầy Đủ

Bạn đã bao giờ tự hỏi **cách ghi nhận cảnh báo** xuất hiện khi Aspose.Words tải một tài liệu chưa? Trong nhiều dự án thực tế, bạn sẽ thấy các cảnh báo thay thế phông chữ, ghi chú tính năng đã lỗi thời, hoặc thậm chí các thông báo liên quan đến bảo mật. Bỏ qua chúng giống như lái xe với kính chắn gió bị nứt—bạn có thể đến đích, nhưng sẽ không biết khi nào có thứ gì đó sắp hỏng.

Tin tốt là Aspose.Words cung cấp cho bạn một cách sạch sẽ, dựa trên callback để chặn các thông điệp đó. Trong hướng dẫn này, chúng tôi sẽ đi qua một **ví dụ C# đầy đủ** không chỉ ghi nhận cảnh báo mà còn chỉ cho bạn cách **xử lý phông chữ thiếu** và **đặt cấu hình phông chữ tùy chỉnh** để tài liệu của bạn hiển thị chính xác như mong đợi.

---

## Những Điều Bạn Sẽ Học

- Cấu hình `LoadOptions` để gắn một đối tượng `FontSettings` tùy chỉnh.  
- Đăng ký callback cảnh báo để lọc các sự kiện `FontSubstitution`.  
- Xuất chi tiết cảnh báo ra console (hoặc bất kỳ trình ghi log nào bạn muốn).  
- Mở rộng giải pháp để xử lý phông chữ thiếu một cách nhẹ nhàng trên các nền tảng khác nhau.  

Khi kết thúc hướng dẫn này, bạn sẽ có một đoạn mã sẵn sàng chạy mà có thể chèn vào bất kỳ dự án .NET nào, cùng với một vài mẹo thực tế để tránh các lỗi thường gặp.

---

## Yêu Cầu Trước

| Yêu Cầu | Lý Do Quan Trọng |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 hoặc mới hơn) | API chúng ta sử dụng (`LoadOptions`, `IWarningCallback`) nằm ở đây. |
| **.NET 6+** (hoặc .NET Framework 4.7.2+) | Các tính năng ngôn ngữ hiện đại làm cho mã sạch hơn. |
| **Một tệp DOCX mẫu** (có tên `input.docx`) đặt trong thư mục đã biết | Chúng ta cần một thứ gì đó để tải và kích hoạt cảnh báo. |
| **Một console hoặc framework ghi log** (tùy chọn) | Để xem các cảnh báo đã ghi nhận khi thực thi. |

Không cần thêm bất kỳ gói NuGet nào ngoài Aspose.Words.

---

## Bước 1: Thiết Lập Cấu Hình Phông Chữ Tùy Chỉnh  

Trước khi tải tài liệu, bạn có thể chỉ cho Aspose.Words nơi tìm kiếm phông chữ. Đây là phần **đặt cấu hình phông chữ tùy chỉnh** của câu đố.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Tại sao điều này quan trọng:**  
Nếu một DOCX tham chiếu tới một phông chữ không được cài đặt trên máy, Aspose.Words sẽ tự động thay thế bằng phông chữ dự phòng *trừ khi* bạn đã cấu hình một thư mục chứa các phông chữ cần thiết. Bằng cách đặt thư mục tùy chỉnh, bạn giảm khả năng xuất hiện các cảnh báo “thay thế phông chữ” ngay từ đầu.

> **Mẹo chuyên nghiệp:** Trên Linux bạn có thể cần cài đặt gói `fonts-dejavu-core` hoặc bất kỳ bộ sưu tập TrueType nào mà tài liệu của bạn phụ thuộc.

---

## Bước 2: Đăng Ký Callback Cảnh Báo  

Aspose.Words triển khai `IWarningCallback`. Chúng ta sẽ tạo một handler nhỏ chỉ in ra các cảnh báo mà chúng ta quan tâm: phông chữ thiếu hoặc đã được thay thế.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Tại sao điều này quan trọng:**  
Kịch bản **xử lý phông chữ thiếu** giờ đã hiển thị cho bạn. Thay vì đoán phông chữ nào đã bị thay thế, bạn nhận được mô tả rõ ràng như “Font 'Calibri' was substituted with 'Arial'”. Điều này vô giá khi gỡ lỗi các vấn đề bố cục trong PDF được tạo hoặc báo cáo đã in.

---

## Bước 3: Tải Tài Liệu Với Các Tùy Chọn Đã Cấu Hình  

Bây giờ chúng ta cuối cùng đưa tài liệu vào bộ nhớ, sử dụng `LoadOptions` mà chúng ta vừa chuẩn bị.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Nếu tệp nguồn sử dụng một phông chữ không có trong `C:\MyFonts`, bạn sẽ thấy đầu ra tương tự như:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Dòng đó là kết quả **cách ghi nhận cảnh báo** mà bạn đang tìm kiếm.

---

## Bước 4: Ví Dụ Hoàn Chỉnh (Sẵn Sàng Sao Chép‑Dán)

Dưới đây là toàn bộ chương trình, sẵn sàng biên dịch. Dán nó vào một dự án console mới và chạy—chỉ cần đảm bảo các đường dẫn trỏ tới vị trí thực tế trên máy của bạn.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Kết quả mong đợi:**  

- Nếu tất cả phông chữ có sẵn:  
  `Document processed. Check console for any warning messages.`  

- Nếu một phông chữ bị thiếu:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Bước 5: Các Biến Thể Thông Thường & Trường Hợp Cạnh  

| Tình Huống | Cần Điều Chỉnh |
|-----------|----------------|
| **Nhiều thư mục phông chữ** | Gọi `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` cho mỗi vị trí bổ sung. |
| **Chặn tất cả cảnh báo** | Triển khai `Warn` nhưng để phần thân trống, hoặc đặt `loadOptions.WarningCallback = null;`. |
| **Ghi nhận các loại cảnh báo khác** | Kiểm tra `info.WarningType` so với `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent`, v.v. |
| **Chạy trên Linux/macOS** | Đảm bảo thư mục phông chữ chứa các tệp `.ttf`/`.otf` tương thích với Linux; bạn có thể cần cài đặt `libfontconfig`. |
| **Tài liệu lớn** | Xem xét stream tài liệu (`LoadOptions.LoadFormat = LoadFormat.Docx;`) để giảm áp lực bộ nhớ. |

Bằng cách dự đoán các kịch bản này, bạn sẽ tránh được bất ngờ khi chuyển từ máy phát triển sang pipeline CI hoặc máy ảo đám mây.

---

## Bước 6: Xác Nhận Bằng Hình Ảnh (Tùy Chọn)

Nếu bạn muốn một gợi ý trực quan nhanh chóng, bạn có thể xuất các cảnh báo đã ghi nhận ra một báo cáo HTML nhỏ. Dưới đây là một đoạn mã ngắn ghi các thông điệp vào `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Sau khi tải tài liệu, gọi `handler.WriteReport(@"C:\Docs\warnings.html");` và mở nó trong trình duyệt. Hình ảnh dưới đây cho thấy báo cáo có thể trông như thế nào:

![How to capture warnings screenshot](/images/capture-warnings.png)

*Alt text:* **cách ghi nhận cảnh báo** – ảnh chụp màn hình đầu ra console và báo cáo HTML.

---

## Kết Luận  

Chúng tôi đã trình bày **cách ghi nhận cảnh báo** trong Aspose.Words, minh họa một cách đáng tin cậy để **xử lý phông chữ thiếu**, và chỉ cho bạn cách **đặt cấu hình phông chữ tùy chỉnh** để hiển thị một cách quyết định. Ví dụ đầy đủ đã sẵn sàng chèn vào bất kỳ giải pháp .NET nào, và `FontWarningHandler` mô-đun có thể được mở rộng để phù hợp với chiến lược ghi log hoặc thu thập dữ liệu của bạn.

Bước tiếp theo? Hãy thử thay thế các lời gọi `Console.WriteLine` bằng một logger có cấu trúc như Serilog, hoặc đẩy các cảnh báo vào Application Insights để giám sát thời gian thực. Bạn cũng có thể khám phá mẫu `DocumentVisitor` nếu cần kiểm tra nội dung tài liệu sau khi tải.

Có câu hỏi về các loại cảnh báo khác hoặc chiến lược nhúng phông chữ? Để lại bình luận bên dưới—chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}