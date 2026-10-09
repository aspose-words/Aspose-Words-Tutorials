---
category: general
date: 2026-02-26
description: Xử lý phông chữ thiếu trong C# bằng Aspose.Words. Tìm hiểu cách bắt các
  cảnh báo thay thế phông chữ, triển khai IWarningCallback và giữ cho tài liệu của
  bạn luôn hiển thị đúng.
draft: false
keywords:
- handle missing fonts
- Aspose.Words font warning
- C# LoadOptions
- IWarningCallback implementation
- document loading with missing fonts
- font substitution handling
language: vi
og_description: Xử lý nhanh các phông chữ thiếu trong C#. Hướng dẫn này cho thấy cách
  bắt các cảnh báo thay thế phông chữ bằng Aspose.Words, triển khai IWarningCallback
  và kiểm tra kết quả.
og_title: Xử lý phông chữ thiếu trong C# – Hướng dẫn Aspose.Words từng bước
tags:
- Aspose.Words
- C#
- Document Processing
title: Xử lý phông chữ thiếu trong C# với Aspose.Words – Hướng dẫn toàn diện
url: /vi/net/working-with-fonts/handle-missing-fonts-in-c-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xử lý phông chữ thiếu trong C# với Aspose.Words – Hướng dẫn đầy đủ

Bạn đã bao giờ cần **xử lý phông chữ thiếu** khi tải một tài liệu Word trong C# và tự hỏi tại sao kết quả lại trông lạ không? Bạn không phải là người duy nhất. Khi một tệp nguồn tham chiếu đến một phông chữ không được cài đặt trên máy, Aspose.Words sẽ âm thầm thay thế bằng một phông chữ khác, điều này có thể làm hỏng bố cục hoặc thương hiệu của bạn.  

Tin tốt? Bằng cách kết nối một **warning callback**, bạn có thể bắt mọi sự kiện thay thế phông chữ, ghi lại và quyết định có cung cấp phông chữ thay thế hay không. Trong hướng dẫn này, chúng tôi sẽ đi qua toàn bộ quy trình—từ việc thiết lập dự án đến kiểm tra đầu ra console—để bạn không bao giờ bị bất ngờ bởi một phông chữ ẩn nữa.

> **Bạn sẽ nhận được**: Một ứng dụng console C# sẵn sàng chạy, báo cáo mỗi phông chữ thiếu, giải thích lý do cảnh báo xảy ra, và cho bạn thấy cách mở rộng handler cho logic tùy chỉnh.

---

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã hoạt động trên .NET Core và .NET Framework đều được)
- Visual Studio 2022 (hoặc bất kỳ IDE C# nào bạn thích)
- Một **giấy phép** cho Aspose.Words for .NET (bản dùng thử miễn phí hoạt động để thử nghiệm)
- Một tài liệu Word tham chiếu đến một phông chữ bạn không có sẵn (ví dụ, *Comic Sans MS* trên máy Linux)

Nếu bạn đã có những thứ này, hãy bắt đầu.

---

## Bước 1: Tạo dự án Console mới và Thêm Aspose.Words

Để giữ mọi thứ gọn gàng, hãy bắt đầu với một dự án console mới.

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp**: Sử dụng cờ `--framework net6.0` nếu bạn muốn nhắm mục tiêu vào một runtime cụ thể.

Điều này sẽ tải gói NuGet Aspose.Words mới nhất, chứa các kiểu `LoadOptions` và `IWarningCallback` mà chúng ta sẽ cần.

---

## Bước 2: Triển khai Warning Handler (IWarningCallback)

Aspose.Words tạo ra một đối tượng `WarningInfo` cho mỗi vấn đề không quan trọng mà nó gặp khi tải tài liệu. Bằng cách triển khai `IWarningCallback`, bạn quyết định cách xử lý các cảnh báo đó.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

public class FontWarningHandler : IWarningCallback
{
    // This method is called automatically by Aspose.Words whenever a warning occurs.
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property contains the name of the missing font and the substitute used.
            Console.WriteLine($"⚠️ Missing font detected: {info.Description}");
        }
        // You could also log other warning types here if you wish.
    }
}
```

**Tại sao điều này quan trọng**: Nếu không có handler, các cảnh báo thay thế phông chữ sẽ bị bỏ qua một cách âm thầm. Khi in chúng ra, bạn sẽ ngay lập tức biết được phông chữ nào bị thiếu và Aspose.Words đã dùng phông chữ nào thay thế.

---

## Bước 3: Cấu hình LoadOptions với Warning Callback

Bây giờ chúng ta gắn handler vào quá trình tải tài liệu. `LoadOptions` cho phép bạn gắn callback trước khi tệp được phân tích.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // 1️⃣ Tell Aspose.Words to use our FontWarningHandler.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // 2️⃣ Path to the Word file that contains missing fonts.
        string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

        // 3️⃣ Load the document with the custom options.
        Document doc = new Document(docPath, loadOptions);

        // At this point, any font‑substitution warning has already been printed.
        Console.WriteLine("✅ Document loaded successfully.");
    }
}
```

> **Lưu ý**: Thay thế `YOUR_DIRECTORY` bằng thư mục thực tế chứa file `.docx` thử nghiệm của bạn. Đối tượng `LoadOptions` phải được truyền vào hàm khởi tạo `Document`; nếu không, hành vi mặc định là im lặng sẽ được áp dụng.

---

## Bước 4: Chạy ứng dụng và Kiểm tra đầu ra

Biên dịch và chạy:

```bash
dotnet run
```

Nếu tài liệu tham chiếu đến một phông chữ không có trên máy của bạn (ví dụ, *Papyrus*), bạn sẽ thấy một cái gì đó như sau:

```
⚠️ Missing font detected: The font 'Papyrus' was not found. Using 'Times New Roman' as a substitute.
✅ Document loaded successfully.
```

Dòng duy nhất đó cho bạn biết chính xác phông chữ nào bị thiếu và phông chữ thay thế nào mà Aspose.Words đã chọn. Bây giờ bạn có thể quyết định nhúng phông chữ thiếu, thay đổi tài liệu nguồn, hoặc chấp nhận việc thay thế.

---

## Bước 5: Nâng cao – Thu thập Cảnh báo để Sử dụng sau

Đôi khi bạn muốn lưu trữ các cảnh báo thay vì in chúng ngay lập tức. Dưới đây là một chỉnh sửa nhanh cho handler để gom các tin nhắn vào một danh sách.

```csharp
using System.Collections.Generic;

public class FontWarningCollector : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string msg = $"Missing font: {info.Description}";
            Messages.Add(msg);
        }
    }
}
```

Và cập nhật `Main` cho phù hợp:

```csharp
static void Main()
{
    var collector = new FontWarningCollector();

    LoadOptions lo = new LoadOptions { WarningCallback = collector };
    Document doc = new Document(@"YOUR_DIRECTORY\DocumentWithMissingFont.docx", lo);

    Console.WriteLine("✅ Document loaded.");
    if (collector.Messages.Count > 0)
    {
        Console.WriteLine("\n--- Font Substitution Report ---");
        foreach (var m in collector.Messages)
            Console.WriteLine(m);
    }
}
```

Bây giờ bạn có một danh sách có thể tái sử dụng, có thể ghi vào file log, gửi tới dịch vụ giám sát, hoặc hiển thị trong UI.

---

## Bước 6: Những Cạm Bẫy Thông Thường & Cách Tránh

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **Không có cảnh báo nào xuất hiện** | Callback không được gắn, hoặc tài liệu được tải mà không có `LoadOptions`. | Đảm bảo `LoadOptions.WarningCallback` được đặt **trước** khi gọi hàm khởi tạo `Document`. |
| **Tên phông chữ sai trong thông báo** | Một số phông chữ được nhúng trong tài liệu; Aspose.Words báo cáo tên *gốc*, không phải tên đã nhúng. | Kiểm tra các tham chiếu phông chữ trong tệp nguồn; nhúng phông chữ sẽ loại bỏ hoàn toàn cảnh báo. |
| **Ảnh hưởng tới hiệu năng** | Việc thu thập cảnh báo cho hàng ngàn tài liệu có thể gây thêm chi phí. | Sử dụng `Console.WriteLine` đơn giản để gỡ lỗi nhanh; chuyển sang bộ thu thập chỉ khi bạn cần dữ liệu. |

---

## Tóm tắt trực quan

![Minh hoạ xử lý phông chữ thiếu hiển thị luồng warning callback](/images/handle-missing-fonts.png "Sơ đồ xử lý phông chữ thiếu với Aspose.Words")

*Sơ đồ (văn bản thay thế bao gồm từ khóa chính) minh họa cách warning callback chặn các sự kiện thay thế phông chữ trong quá trình tải tài liệu.*

---

## Kết luận

Bây giờ bạn đã biết **cách xử lý phông chữ thiếu** trong C# bằng cách sử dụng Aspose.Words. Bằng cách kết nối một `IWarningCallback` vào `LoadOptions`, bạn sẽ có đầy đủ khả năng nhìn thấy mọi sự kiện thay thế phông chữ, có thể ghi lại hoặc hành động dựa trên chúng, và cuối cùng đảm bảo các tài liệu được tạo ra giữ nguyên giao diện và cảm giác mong muốn.

> **Tóm tắt nhanh**:  
> 1. Thêm Aspose.Words vào ứng dụng console.  
> 2. Triển khai `FontWarningHandler` (hoặc một bộ thu thập).  
> 3. Truyền nó qua `LoadOptions` khi tải tài liệu.  
> 4. Kiểm tra đầu ra console hoặc các cảnh báo đã lưu.  

Từ đây bạn có thể khám phá **việc nhúng phông chữ thiếu** (`FontSettings.SubstitutionSettings`) hoặc **tự động tải chúng từ máy chủ phông chữ của công ty**—cả hai đều là mở rộng tự nhiên của mẫu chúng ta vừa xây dựng.

Có thêm câu hỏi về **cảnh báo phông chữ Aspose.Words**, **C# LoadOptions**, hoặc **tải tài liệu với phông chữ thiếu**? Để lại bình luận, và chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}