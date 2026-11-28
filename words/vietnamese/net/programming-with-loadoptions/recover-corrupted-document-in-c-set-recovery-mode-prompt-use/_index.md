---
category: general
date: 2026-01-11
description: Khôi phục tài liệu bị hỏng trong C# bằng Aspose.Words. Tìm hiểu cách
  thiết lập chế độ khôi phục, tải file docx với chế độ khôi phục và hiển thị thông
  báo cho người dùng khi có lỗi trong vài bước đơn giản.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: vi
og_description: Khôi phục tài liệu bị hỏng trong C# bằng cách thiết lập chế độ phục
  hồi, tải một tệp DOCX với chế độ phục hồi và thông báo cho người dùng khi có lỗi.
  Hướng dẫn chi tiết từng bước.
og_title: Khôi phục tài liệu bị hỏng trong C# – Hướng dẫn nhanh
tags:
- Aspose.Words
- C#
- Document Recovery
title: Khôi phục tài liệu bị hỏng trong C# – Đặt chế độ khôi phục & Nhắc người dùng
url: /vi/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Khôi phục tài liệu bị hỏng trong C# – Hướng dẫn đầy đủ

Bạn đã bao giờ cố gắng mở một tệp DOCX trông bình thường trong Word nhưng lại ném ra ngoại lệ trong mã của bạn chưa? Bạn có thể đang gặp phải kịch bản **recover corrupted document**. Tin tốt là Aspose.Words cung cấp cho bạn khả năng kiểm soát chi tiết cách xử lý những tệp khó chịu này — dù bạn muốn tự động sửa chúng, ném ngoại lệ, hoặc hỏi người dùng phải làm gì.

Trong tutorial này chúng ta sẽ đi qua mọi thứ bạn cần để **recover corrupted document** files, từ việc cài đặt thư viện đến việc chọn tùy chọn **set recovery mode** phù hợp, **load docx with recovery**, và cuối cùng **prompt user on error** khi có sự cố. Không có phần thừa, chỉ có một ví dụ hoàn chỉnh, có thể chạy được mà bạn có thể đưa vào bất kỳ dự án .NET nào.

> **Xem nhanh:** Khi kết thúc, bạn sẽ có một ứng dụng console tải một tệp `corrupt.docx` có thể bị hỏng, ghi lại mọi cảnh báo, và hỏi người dùng có muốn tiếp tục khi quá trình khôi phục thất bại.

---

## Những gì bạn cần

- **.NET 6.0** trở lên (mã cũng hoạt động trên .NET Framework 4.6+).  
- **Aspose.Words for .NET** – cài đặt qua NuGet (`Install-Package Aspose.Words`).  
- Một tệp **corrupt DOCX** để thử nghiệm (bạn có thể gây hỏng cố ý bằng cách mở tệp trong trình soạn thảo hex hoặc đổi phần mở rộng).  
- Bất kỳ IDE nào bạn thích—Visual Studio, Rider, hoặc thậm chí VS Code đều được.

> *Mẹo chuyên nghiệp:* Giữ một bản sao lưu của tệp gốc. Quá trình khôi phục có thể ghi đè lên các phần của tài liệu, và bạn không muốn mất những phần còn tốt.

## Bước 1 – Cài đặt Aspose.Words và thêm Namespaces

Đầu tiên, lấy thư viện từ NuGet và đưa các namespace cần thiết vào phạm vi.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Đó là tất cả những gì bạn cần cho phần còn lại của hướng dẫn. Namespace `Aspose.Words.Loading` chứa lớp `LoadOptions`, là chìa khóa để **set recovery mode**.

## Bước 2 – Chọn chế độ khôi phục (Primary H2 with Keyword)

### Recover Corrupted Document – Đặt chế độ khôi phục đúng

Aspose.Words cung cấp ba hành vi khôi phục:

| Mode | What Happens | When to Use |
|------|--------------|------------|
| **PromptUser** | Hiển thị một hộp thoại (hoặc bạn có thể tự triển khai lời nhắc) và cố gắng sửa tệp. | Lý tưởng cho các công cụ tương tác nơi người dùng có thể quyết định. |
| **Silent** | Tự động cố gắng sửa, không giao diện người dùng. | Tốt cho các công việc batch hoặc dịch vụ. |
| **ThrowException** | Dừng xử lý và ném ngoại lệ. | Dùng khi bạn muốn kiểm tra nghiêm ngặt. |

Dưới đây là cách **set recovery mode** thành `PromptUser`. Nếu bạn muốn xử lý im lặng, chỉ cần đổi giá trị enum.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Tại sao điều này quan trọng:** Bằng cách **set recovery mode** một cách rõ ràng, bạn cho Aspose.Words biết mức độ “aggressive” cần thiết. Mặc định là `PromptUser`, nhưng việc khai báo rõ ràng giúp ý định của bạn trở nên trong suốt — cả với những người bảo trì trong tương lai và với các công cụ tìm kiếm thu thập mã.

## Bước 3 – Tải DOCX với chế độ khôi phục

Bây giờ chúng ta sẽ **load docx with recovery** bằng `LoadOptions` vừa cấu hình. Nếu tệp bị hỏng, Aspose.Words sẽ hoặc sửa chữa nó hoặc đưa ra cảnh báo, tùy thuộc vào chế độ.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

Constructor `Document` thực hiện phần lớn công việc. Trong chế độ **PromptUser**, bạn sẽ thấy lời nhắc trên console (hoặc UI tùy chỉnh nếu bạn gắn vào các sự kiện `LoadOptions`) hỏi có nên tiếp tục không. Trong chế độ **Silent**, phương thức chỉ cố gắng hết sức và tiếp tục.

## Bước 4 – Kiểm tra cảnh báo và hỏi người dùng

Aspose.Words ghi lại mọi vấn đề gặp phải trong bộ sưu tập `Warnings`. Hãy lặp qua chúng và cho người dùng cơ hội quyết định bước tiếp theo.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Đoạn mã trên **prompt user on error** theo cách thân thiện với console. Nếu bạn đang xây dựng ứng dụng Windows Forms hoặc WPF, hãy thay `Console.ReadLine` bằng `MessageBox` hoặc hộp thoại tùy chỉnh.

## Bước 5 – Làm việc với tài liệu đã khôi phục

Ở thời điểm này, tài liệu đã nằm trong bộ nhớ, được sửa chữa tốt nhất có thể bởi Aspose.Words. Bạn có thể đọc nội dung, lưu bản sao sạch, hoặc thực hiện bất kỳ thao tác nào cần thiết.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Chạy chương trình đầy đủ trên tệp bị hỏng sẽ tạo ra đầu ra console tương tự như sau:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Nếu tệp thực sự ổn, bạn sẽ thấy “Document loaded without any warnings.” và bản sao sạch sẽ giống hệt nguồn.

## Ví dụ hoàn chỉnh

Dưới đây là toàn bộ chương trình trong một file. Sao chép‑dán vào dự án console mới và nhấn **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Chạy nó, làm hỏng một tệp thử nghiệm, và quan sát quá trình khôi phục hoạt động. 🎉

## Các trường hợp đặc biệt & Biến thể

| Scenario | What to Change | Why |
|----------|----------------|-----|
| **Batch processing** (không có tương tác người dùng) | Đặt `RecoveryMode = RecoveryMode.Silent` và loại bỏ lời nhắc console. | Giữ cho pipeline chạy tự động. |
| **Strict validation** (fail fast) | Sử dụng `RecoveryMode.ThrowException`. Bao quanh lời gọi load trong try/catch và ghi lại ngoại lệ. | Đảm bảo bạn không bao giờ làm việc với tệp chỉ được sửa một phần. |
| **Custom UI** (WinForms/WPF) | Đăng ký vào `LoadOptions.LoadingProgress` hoặc sử dụng các sự kiện `Document.LoadOptions` để hiển thị hộp thoại. | Cung cấp trải nghiệm phong phú hơn so với console. |
| **Large documents** (giới hạn bộ nhớ) | Tải với `LoadOptions.LoadFormat = LoadFormat.Docx` và cân nhắc `Document.SaveOptions` để stream đầu ra. | Ngăn ngừa ngoại lệ OutOfMemory. |

## Mẹo thực tiễn (E‑E‑A‑T Signals)

- **Luôn giữ bản sao lưu** trước khi thực hiện khôi phục; quá trình có thể ghi đè lên các phần của tệp.  
- **Ghi log cảnh báo** vào file để phân tích sau; chúng thường gợi ý nguyên nhân gốc (ví dụ: thiếu phần, XML bị hỏng).  
- **Kiểm tra với nhiều loại hỏng** – cắt ngắn tệp, làm hỏng thẻ XML, hoặc thay đổi cấu trúc zip để xem mỗi chế độ phản hồi như thế nào.  
- **Nâng cấp Aspose.Words thường xuyên**; các phiên bản mới cải thiện thuật toán khôi phục và thêm các loại cảnh báo mới.  
- **Kết hợp với validation** – sau khi khôi phục, chạy nhanh `document.UpdateFields()` và `document.Save()` để đảm bảo tài liệu hoạt động đầy đủ.

## Kết luận

Bạn giờ đã biết cách **recover corrupted document** trong C# bằng cách **set recovery mode**, **load docx with recovery**, và **prompt user on error** khi có sự cố. Ví dụ đầy đủ minh họa một quy trình sạch sẽ, từ đầu tới cuối, hoạt động trong các ứng dụng console, dịch vụ, hoặc dự án UI.

Bước tiếp theo? Hãy thử thay lời nhắc console bằng hộp thoại modal trong ứng dụng WinForms, thử nghiệm chế độ **Silent** cho các công việc nền, hoặc tích hợp logic khôi phục vào endpoint tải lên file ASP.NET để người dùng có thể tải lên DOCX bị hỏng và nhận ngay phiên bản đã sửa.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn nguyên vẹn!  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}