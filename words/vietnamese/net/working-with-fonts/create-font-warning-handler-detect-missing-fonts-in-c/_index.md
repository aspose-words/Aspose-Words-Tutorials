---
category: general
date: 2026-02-12
description: Tạo trình xử lý cảnh báo phông chữ để phát hiện và theo dõi các phông
  chữ thiếu trong Aspose.Words. Tìm hiểu cách ghi lại cảnh báo một cách hiệu quả.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: vi
og_description: Tạo trình xử lý cảnh báo phông chữ trong C# để phát hiện phông chữ
  bị thiếu và tìm hiểu cách ghi lại cảnh báo khi Aspose.Words thay thế phông chữ.
og_title: Tạo Trình Xử Lý Cảnh Báo Phông Chữ – Phát Hiện Phông Chữ Thiếu
tags:
- Aspose.Words
- C#
- Document Processing
title: Tạo Trình Xử Lý Cảnh Báo Phông Chữ – Phát Hiện Phông Chữ Thiếu Trong C#
url: /vi/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo Font Warning Handler – Phát hiện phông chữ thiếu trong C#

Bạn đã bao giờ cần **create font warning handler** vì một tài liệu Word lặng lẽ thay thế một phông chữ mà bạn không mong đợi chưa? Bạn không phải là người duy nhất. Khi Aspose.Words tải một DOCX tham chiếu tới một phông chữ không có trên máy chủ, nó lặng lẽ chuyển sang phông chữ mặc định—để lại bố cục của bạn bị hỏng nhẹ.  

Trong hướng dẫn này chúng tôi sẽ chỉ cho bạn cách **detect missing fonts**, **track missing fonts**, và **how to log warnings** để bạn có thể phát hiện các sự thay thế trước khi chúng gây rắc rối. Khi kết thúc, bạn sẽ có một trình xử lý cảnh báo có thể tái sử dụng, in mỗi sự kiện thay thế phông chữ ra console (hoặc bất kỳ logger nào bạn muốn). Không có bí ẩn, chỉ có mã rõ ràng, có thể hành động ngay.

## Prerequisites

- .NET 6.0 hoặc mới hơn (API giống nhau cho .NET Framework 4.6+)
- Aspose.Words for .NET đã được cài đặt (`dotnet add package Aspose.Words`)
- Một tệp Word tham chiếu tới một phông chữ chưa được cài trên máy của bạn (ví dụ, `MissingFont.docx`)

Nếu bạn đã có những thứ này, tuyệt vời—hãy bắt đầu.

## Step 1: Set Up LoadOptions with a Warning Callback  

Điều đầu tiên bạn làm khi muốn **create font warning handler** là yêu cầu Aspose.Words kích hoạt một callback mỗi khi gặp vấn đề. `LoadOptions` là nơi chứa cấu hình này.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Tại sao điều này quan trọng:**  
`LoadOptions` là nơi duy nhất bạn có thể gắn một `IWarningCallback`. Nếu không có, Aspose.Words sẽ ghi cảnh báo nội bộ nhưng bạn sẽ không thấy chúng. Bằng cách gán `FontWarningHandler` chúng ta có toàn quyền kiểm soát những gì xảy ra khi một phông chữ bị thay thế.

## Step 2: Implement the FontWarningHandler Class  

Bây giờ chúng ta thực sự **create font warning handler** bằng mã. Lớp này triển khai `IWarningCallback` và nhận một đối tượng `WarningInfo` cho mỗi cảnh báo mà Aspose.Words phát sinh.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Giải thích:**  
- `info.Type` cho chúng ta biết loại cảnh báo. Chúng ta quan tâm tới `WarningType.FontSubstitution` vì đây là dấu hiệu của phông chữ thiếu.  
- `info.Description` chứa thông điệp dễ đọc như *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Bằng cách ghi vào `Console.WriteLine` chúng ta **log warnings** ngay lập tức. Trong một ứng dụng thực tế, bạn có thể thay thế bằng `ILogger`, một trình ghi file, hoặc dịch vụ telemetry.

> **Pro tip:** Nếu bạn cần thu thập tất cả các phông chữ thiếu để báo cáo sau, lưu `info.Description` vào một `List<string>` thay vì in ra.

## Step 3: Load the Document Using the Configured LoadOptions  

Với callback đã được thiết lập, việc tải tài liệu sẽ tự động kích hoạt trình xử lý mỗi khi có phông chữ thiếu.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Bạn sẽ thấy:**  
Chạy chương trình sẽ in ra một dòng tương tự như:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Dòng này xác nhận bạn đã **detect missing fonts** thành công và hiện đang **track missing fonts** trong thời gian thực.

## Step 4: Verify the Handler Works with Different Scenarios  

Dễ dàng nghĩ rằng trình xử lý chỉ hoạt động với tệp DOCX, nhưng Aspose.Words hỗ trợ nhiều định dạng. Hãy thử tải một PDF tham chiếu tới một phông chữ được nhúng, hoặc một tệp `.doc` cũ. Callback giống nhau sẽ được kích hoạt cho bất kỳ định dạng nào đi qua quy trình giải quyết phông chữ.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Nếu PDF tham chiếu tới một phông chữ chưa được cài, bạn sẽ nhận được cùng một đầu ra console. Điều này chứng minh giải pháp **create font warning handler** của bạn không phụ thuộc vào định dạng.

## Step 5: Extending the Handler – Logging to a File  

Đầu ra console tiện cho demo, nhưng mã sản xuất thường ghi vào file log. Dưới đây là một chỉnh sửa nhanh.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Bây giờ mỗi khi một phông chữ được thay thế, thông điệp sẽ được thêm vào `font-warnings.log`. Điều này đáp ứng phần **how to log warnings** của yêu cầu và cung cấp một bản ghi kiểm toán bền vững.

## Step 6: Putting It All Together – Full, Runnable Example  

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào một ứng dụng console. Không thiếu bất kỳ phần nào; chỉ cần thay đổi đường dẫn tệp thành tài liệu của bạn.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Kết quả mong đợi:**  

- Console in mỗi dòng thay thế.  
- `font-warnings.log` chứa bản ghi có dấu thời gian của mọi sự kiện phông chữ thiếu.  
- Tệp `output.pdf` được tạo bằng các phông chữ đã được thay thế, đảm bảo việc chuyển đổi thành công ngay cả khi các phông chữ gốc không có sẵn.

## Common Questions & Edge Cases  

| Question | Answer |
|----------|--------|
| *Nếu tôi muốn bỏ qua một số phông chữ thì sao?* | Trong `Warning`, kiểm tra `info.Description` để lấy tên phông và `return;` sớm cho những phông bạn cho là chấp nhận được. |
| *Trình xử lý có được kích hoạt cho phông chữ nhúng không?* | Không—phông chữ nhúng luôn có sẵn cho tài liệu, vì vậy không có cảnh báo thay thế. |
| *Tôi có thể bắt các loại cảnh báo khác (ví dụ, vấn đề độ phân giải hình ảnh) không?* | Chắc chắn. Loại bỏ điều kiện `if (info.Type == WarningType.FontSubstitution)` hoặc thêm các khối `if` cho `WarningType.ImageResolution`. |
| *Trình xử lý có an toàn với đa luồng không?* | Cài đặt mặc định ở trên ghi vào file mà không có đồng bộ. Đối với kịch bản đa luồng, hãy bọc việc ghi file trong một `lock` hoặc sử dụng logger đồng thời. |

## Next Steps  

Bây giờ bạn đã biết **how to log warnings** cho phông chữ thiếu, bạn có thể muốn:

- **Detect missing fonts** trong quá trình nhập hàng loạt và tạo báo cáo tổng hợp.  
- **Track missing fonts** trên nhiều tài liệu và gửi cảnh báo email khi một phông chữ nào đó xuất hiện thường xuyên.  
- **Integrate with a monitoring system** (ví dụ, Azure Application Insights) để hiển thị xu hướng thay thế phông chữ theo thời gian.  

Tất cả các mở rộng này đều dựa trên nền tảng `IWarningCallback` mà chúng ta đã tạo.

---

*Happy coding! Nếu bạn gặp bất kỳ vấn đề nào—có thể là thư mục phông chữ tùy chỉnh hoặc chia sẻ mạng—hãy để lại bình luận bên dưới. Cộng đồng (và tôi) luôn sẵn sàng giúp bạn tinh chỉnh chiến lược font‑warning của mình.* 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}