---
category: general
date: 2026-02-28
description: Tìm hiểu cách xử lý cảnh báo phông chữ và phát hiện phông chữ thiếu trong
  Aspose.Words bằng C#. Hướng dẫn chi tiết từng bước kèm mã nguồn đầy đủ.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: vi
og_description: Xử lý cảnh báo phông chữ trong Aspose.Words và phát hiện phông chữ
  thiếu bằng ví dụ C# đã sẵn sàng chạy. Thực hiện các bước và xem kết quả.
og_title: Xử lý Cảnh báo Phông chữ trong Aspose.Words – Hướng dẫn Toàn diện
tags:
- Aspose.Words
- C#
- Document Loading
title: Xử lý cảnh báo phông chữ trong Aspose.Words – Phát hiện phông chữ thiếu
url: /vi/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xử lý Cảnh báo Phông chữ trong Aspose.Words – Phát hiện Phông chữ Thiếu

Bạn đã bao giờ **xử lý cảnh báo phông chữ** khi tải một tài liệu Word và tự hỏi tại sao một số đoạn văn lại trông lạ không? Bạn không phải là người duy nhất. Các phông chữ thiếu sẽ gây ra cảnh báo thay thế có thể làm hỏng bố cục hiển thị một cách âm thầm, và nếu bạn không **phát hiện phông chữ thiếu** thì sẽ không bao giờ biết điều gì đã sai.

Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn một cách thực tế để **xử lý cảnh báo phông chữ** bằng cách sử dụng `IWarningCallback` của Aspose.Words. Khi kết thúc, bạn sẽ có thể phát hiện mọi sự kiện thay thế phông chữ, ghi lại chúng, và thậm chí quyết định có nên hủy quá trình tải hay không. Không cần tài liệu bên ngoài, chỉ một ví dụ sẵn sàng sao chép‑dán.

## Những gì bạn sẽ học

- Thiết lập một bộ xử lý cảnh báo tùy chỉnh chỉ phản hồi các cảnh báo thay thế phông chữ.  
- Gắn bộ xử lý này vào `LoadOptions` để mọi lần tải tài liệu đều đi qua nó.  
- Kiểm tra kết quả trên console và hiểu ý nghĩa của từng cảnh báo.  

**Yêu cầu trước**

- .NET 6.0 trở lên (mã cũng hoạt động với .NET Framework 4.6+).  
- Aspose.Words for .NET được cài đặt qua NuGet (`Install-Package Aspose.Words`).  
- Một tệp Word tham chiếu tới một phông chữ không được cài đặt trên máy của bạn (ví dụ: phông chữ công ty tùy chỉnh).  

Nếu bạn thiếu bất kỳ mục nào ở trên, hãy cài đặt ngay—nếu không, chúng ta cùng bắt đầu.

## Cách Xử lý Cảnh báo Phông chữ trong Aspose.Words

Dưới đây là chương trình đầy đủ, có thể chạy ngay. Nó bao gồm mọi thứ từ các câu lệnh `using` đến phương thức `Main`, vì vậy bạn chỉ cần đưa nó vào một ứng dụng console và nhấn **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Kết quả console dự kiến** (giả sử tài liệu sử dụng một phông chữ mà bạn không có):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Nếu tài liệu **không có phông chữ nào bị thiếu**, dòng cảnh báo sẽ không xuất hiện—do đó bạn đã **phát hiện phông chữ thiếu** chỉ khi cần thiết.

### Tại sao cách này hoạt động

Aspose.Words ném một đối tượng `WarningInfo` cho mỗi vấn đề không quan trọng mà nó gặp khi phân tích tệp. Bằng cách triển khai `IWarningCallback` bạn có một điểm hook vào quy trình đó. Cờ `WarningType.FontSubstitution` cho bạn biết chính xác khi thư viện phải thay thế phông chữ yêu cầu bằng một phông chữ dự phòng. Đây là cách đáng tin cậy nhất để **xử lý cảnh báo phông chữ** vì nó chạy *trong quá trình* tải, trước khi bạn chạm vào mô hình đối tượng tài liệu.

## Phát hiện Phông chữ Thiếu mà Không Gây Đổ Vỡ Ứng Dụng

Đôi khi bạn muốn coi một phông chữ thiếu là lỗi nghiêm trọng—có thể các quy tắc thương hiệu của bạn cấm mọi sự thay thế. Bạn có thể sửa đổi bộ xử lý để ném ngoại lệ thay vì chỉ ghi log:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Bây giờ khối `try…catch` quanh `new Document(...)` sẽ bắt được vấn đề, cho phép bạn quyết định có nên hủy, chuyển sang phương án dự phòng, hay hiển thị thông báo cho người dùng.

## Bonus: Hiển thị Cảnh báo trong Ứng dụng UI

Nếu bạn đang xây dựng ứng dụng WinForms hoặc WPF, thay `Console.WriteLine` bằng một lời gọi thân thiện với UI:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

Như vậy, người dùng cuối sẽ thấy cảnh báo ngay lập tức, và bạn vẫn **xử lý cảnh báo phông chữ** một cách nhất quán trên mọi nền tảng.

## Những Sai Lầm Thường Gặp & Mẹo Chuyên Nghiệp

- **Sai lầm:** Quên thiết lập `WarningCallback`. Hành vi mặc định là bỏ qua các cảnh báo phông chữ, vì vậy bạn sẽ không bao giờ thấy chúng.  
  **Mẹo:** Luôn tạo một thể hiện `LoadOptions` ngay cả khi bạn chỉ cần bộ xử lý cảnh báo. Nó nhẹ và rõ ràng.  

- **Sai lầm:** Sử dụng ký tự phân tách đường dẫn sai trên hệ điều hành không phải Windows.  
  **Mẹo:** Dùng `Path.Combine` hoặc chuỗi thô (`@"C:\Docs\MissingFont.docx"` hoạt động trên Windows; trên Linux dùng `"/home/user/docs/MissingFont.docx"`).  

- **Sai lầm:** Giả định rằng cảnh báo sẽ xuất hiện cho các phông chữ được nhúng.  
  **Mẹo:** Các phông chữ nhúng được coi là đã có, vì vậy sẽ không có cảnh báo thay thế. Hãy thử với các phông chữ thực sự *thiếu* để thấy bộ xử lý hoạt động.  

- **Sai lầm:** Ghi log quá nhiều loại cảnh báo.  
  **Mẹo:** Lọc theo `WarningType.FontSubstitution` như trong ví dụ—giúp console sạch sẽ và tập trung vào kịch bản **phát hiện phông chữ thiếu**.

## Tổng Kết Ví dụ Hoàn chỉnh

Dưới đây là toàn bộ chương trình một lần nữa, lần này không có chú thích cho những ai muốn xem bản sạch:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Sao chép, dán, chạy—console của bạn sẽ ngay lập tức **xử lý cảnh báo phông chữ** và **phát hiện phông chữ thiếu** một cách tự động.

## Các Bước Tiếp Theo

- **Ghi log vào file:** Thay `Console.WriteLine` bằng một logger (ví dụ: NLog) để theo dõi ở mức sản xuất.  
- **Xử lý hàng loạt:** Duyệt qua một thư mục các tài liệu, thu thập tất cả các sự kiện thay thế phông chữ vào báo cáo CSV.  
- **Cài đặt phông chữ tự động:** Kết nối vào bộ xử lý cảnh báo để tải xuống các phông chữ thiếu từ kho lưu trữ nội bộ trước khi tiếp tục tải.  

Mỗi phần mở rộng này đều dựa trên ý tưởng cốt lõi của việc **xử lý cảnh báo phông chữ** một cách sạch sẽ và tái sử dụng.

---

*Chúc bạn lập trình vui! Nếu gặp bất kỳ vấn đề nào khi cố gắng **phát hiện phông chữ thiếu**, hãy để lại bình luận bên dưới. Tôi sẽ sẵn sàng hỗ trợ bạn giải quyết.* 

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}