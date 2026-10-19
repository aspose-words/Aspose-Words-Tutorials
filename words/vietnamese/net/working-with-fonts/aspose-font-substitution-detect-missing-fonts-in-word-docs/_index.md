---
category: general
date: 2026-05-04
description: Học cách sử dụng tính năng thay thế phông chữ của Aspose để phát hiện
  các phông chữ bị thiếu khi tải tài liệu Word và truy xuất chi tiết về phông chữ
  thiếu—hướng dẫn chi tiết từng bước.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: vi
og_description: Thành thạo việc thay thế phông chữ Aspose để phát hiện các phông chữ
  thiếu khi tải tài liệu Word và lấy thông tin phông chữ thiếu bằng mã C# đầy đủ.
og_title: Thay thế phông chữ Aspose – Phát hiện phông chữ thiếu trong tài liệu Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Thay thế phông chữ Aspose: Phát hiện phông chữ thiếu trong tài liệu Word'
url: /vi/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thay Thế Phông Chữ Aspose – Phát Hiện Phông Chữ Thiếu Trong Tài Liệu Word

Bạn đã bao giờ tự hỏi tại sao một tài liệu Word lại hiển thị sai trên máy khác chưa? Thường thì nguyên nhân là phông chữ thiếu, và **Aspose font substitution** là công cụ giúp bạn phát hiện những khoảng trống này trước khi chúng trở thành thảm họa về mặt hình ảnh. Trong hướng dẫn này, chúng ta sẽ đi qua cách **phát hiện phông chữ thiếu** ngay khi bạn **tải một tài liệu Word**, và sau đó **lấy thông tin phông chữ thiếu** để bạn có thể sửa hoặc thay thế chúng.

Chúng tôi sẽ bao phủ mọi thứ từ việc thiết lập callback cảnh báo đến việc lấy danh sách sạch các phông chữ thiếu. Khi kết thúc, bạn sẽ có một đoạn mã C# sẵn sàng chạy, cho bạn biết chính xác những phông chữ nào không được tìm thấy, và bạn sẽ hiểu tại sao điều này quan trọng đối với độ trung thực của tài liệu.

---

## Yêu Cầu Trước – Những Gì Bạn Cần Trước Khi Bắt Đầu

- **Aspose.Words for .NET** (v23.12 hoặc phiên bản mới hơn được khuyến nghị).  
- Môi trường phát triển .NET (Visual Studio, Rider, hoặc `dotnet` CLI).  
- Một tệp DOCX mẫu có cố ý sử dụng phông chữ mà bạn chưa cài đặt—gọi nó là `DocumentWithMissingFont.docx`.  
- Kiến thức cơ bản về C#—không cần phức tạp, chỉ cần khả năng chạy một ứng dụng console.

Nếu bất kỳ mục nào trên nghe lạ, hãy tạm dừng và cài đặt gói NuGet:

```bash
dotnet add package Aspose.Words
```

Xong rồi. Không cần phông chữ bổ sung, không có dịch vụ bên ngoài.

---

## Bước 1: Tải Tài Liệu Word (và Kích Hoạt Kiểm Tra Phông Chữ)

Điều đầu tiên bạn làm là **tải một tài liệu Word**. Aspose.Words phân tích tệp và, nếu không thể tìm thấy phông chữ được tham chiếu, nó sẽ đưa vào một cảnh báo *FontSubstitution*. Dưới đây là đoạn mã thực hiện việc tải:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Tại sao điều này quan trọng:** Việc tải tài liệu sớm cho phép Aspose quét mọi đoạn văn bản, kiểu dáng và đối tượng nhúng. Nếu một phông chữ không được tìm thấy trên hệ thống hoặc trong thư mục phông chữ tùy chỉnh, bạn sẽ nhận được cảnh báo sau này.

---

## Bước 2: Gắn Callback Cảnh Báo Để Bắt Sự Kiện Thay Thế

Aspose.Words sử dụng cơ chế callback để thông báo cho bạn về các vấn đề như phông chữ thiếu. Bằng cách gán một triển khai của `IWarningCallback` vào `doc.WarningCallback`, bạn có thể chặn mỗi cảnh báo khi nó xảy ra.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Mẹo chuyên nghiệp:** Bạn có thể gắn nhiều callback (ví dụ: ghi log, cập nhật UI) bằng cách bọc chúng trong một mẫu composite, nhưng trong hướng dẫn này một callback duy nhất giúp mọi thứ rõ ràng.

---

## Bước 3: Triển Khai Callback Cảnh Báo Thay Thế Phông Chữ

Bây giờ chúng ta định nghĩa lớp thực hiện công việc. Callback nhận một đối tượng `WarningInfo`; chúng ta lọc cho `WarningType.FontSubstitution` và lưu mô tả để sử dụng sau.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Điều gì đang xảy ra:** Khi Aspose gặp phông chữ thiếu, nó tạo ra một cảnh báo như “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Callback của chúng ta in ra dòng này và lưu lại.

---

## Bước 4: Xử Lý Tài Liệu (Tùy Chọn) và Thu Thập Phông Chữ Thiếu

Nếu bạn chỉ cần **phát hiện phông chữ thiếu**, bước tải đã đủ—các cảnh báo sẽ tự động phát sinh. Tuy nhiên, nhiều nhà phát triển cũng cần **lấy thông tin phông chữ thiếu** sau khi thực hiện một số thao tác (ví dụ: lưu, chuyển đổi). Dưới đây chúng tôi buộc một thao tác nhỏ—lưu thành PDF—để đảm bảo tất cả cảnh báo được phát ra, sau đó chúng tôi lấy các tin nhắn đã thu thập.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Kết quả dự kiến trên console** (ví dụ):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Chú ý cách mỗi dòng rõ ràng chỉ ra phông chữ gốc và phông chữ dự phòng mà Aspose đã chọn. Đó là cốt lõi của báo cáo **aspose font substitution**.

---

## Bước 5: Nâng Cao – Sử Dụng Nguồn Phông Chữ Tùy Chỉnh Để Giảm Thay Thế

Đôi khi bạn *có* các phông chữ thiếu, chỉ là chúng không nằm trong thư mục hệ thống mặc định. Aspose.Words cho phép bạn chỉ đến một thư mục tùy chỉnh thông qua `FontSettings`. Thêm bước này có thể giảm đáng kể số lượng cảnh báo thay thế.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Tại sao thêm bước này?** Nếu bạn phân phối tài liệu trên nhiều máy, việc đóng gói các phông chữ cần thiết trong một thư mục đã biết đảm bảo cùng một giao diện hình ảnh ở mọi nơi. Nó cũng làm cho quy trình **detect missing fonts** của bạn chính xác hơn vì Aspose sẽ kiểm tra thư mục đó trước khi dùng phông dự phòng.

---

## Ví Dụ Hoàn Chỉnh Hoạt Động

Kết hợp tất cả lại, đây là một chương trình console sẵn sàng sao chép‑dán. Lưu nó dưới tên `Program.cs` và chạy bằng `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Bạn sẽ thấy gì:** Nếu DOCX nguồn tham chiếu các phông chữ bạn không có, console sẽ in mỗi dòng thay thế kèm theo một bản tóm tắt ngắn gọn. Nếu tất cả phông chữ đều có, bạn sẽ nhận được thông báo “No missing fonts were detected.”

---

## Các Rủi Ro Thường Gặp & Cách Tránh

| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|----------------|-----|
| **Không có cảnh báo nào xuất hiện** | Tài liệu chỉ sử dụng phông chữ hệ thống, hoặc bạn đã thêm một thư mục tùy chỉnh chứa các phông chữ thiếu. | Xác minh DOCX thực sự tham chiếu một phông chữ không có. Bạn có thể mở nó trong Word và thay đổi một đoạn văn thành phông chữ hiếm (ví dụ: “Papyrus”). |
| **Tin nhắn trùng lặp** | Cùng một phông chữ được sử dụng trong nhiều đoạn, gây ra nhiều cảnh báo. | Loại bỏ trùng lặp danh sách bằng `Distinct()` nếu bạn chỉ cần một tập duy nhất. |
| **Giảm hiệu năng trên tài liệu lớn** | Mỗi cảnh báo được xử lý trên luồng UI. | Chạy việc tải trong một tác vụ nền hoặc sử dụng `Parallel.ForEach` cho xử lý sau. |
| **Phông chữ dự phòng sai** | Phông chữ dự phòng mặc định của Aspose có thể không phù hợp với thương hiệu của bạn. | Đặt `FontSettings.SubstitutionSettings.DefaultFontName` thành phông chữ dự phòng ưa thích (ví dụ: “Calibri”). |

---

## Mở Rộng Giải Pháp – Xuất Phông Chữ Thiếu Ra JSON

Nếu bạn đang xây dựng một dịch vụ web cần báo cáo phông chữ thiếu cho client, việc tuần tự hoá danh sách là rất đơn giản:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Bây giờ API của bạn có thể trả về một payload JSON sạch sẽ mà hệ thống khác có thể tiêu thụ.

---

## Kết Luận

Trong hướng dẫn này, chúng tôi đã trình bày **Aspose font substitution** từ đầu đến cuối: tải tài liệu Word, gắn callback cảnh báo, bắt mỗi sự kiện *detect missing fonts*, và cuối cùng **lấy thông tin phông chữ thiếu** để báo cáo hoặc khắc phục. Bằng cách thêm các thư mục phông chữ tùy chỉnh tùy chọn, bạn có thể giảm danh sách các lần thay thế, và chỉ với vài dòng thêm, bạn thậm chí có thể xuất kết quả ra JSON.

Hãy nhớ, tính toàn vẹn hình ảnh của tài liệu phụ thuộc vào các phông chữ được sử dụng. Với kỹ thuật được trình bày ở đây, bạn sẽ không bao giờ bị bất ngờ bởi một phông chữ dự phòng không mong muốn nữa.

Sẵn sàng bước tiếp theo? Hãy thử tích hợp logic này vào một pipeline xử lý tài liệu lớn hơn, hoặc khám phá các tính năng khác của Aspose.Words như nhúng phông chữ (`doc.FontSettings.EmbeddedFonts`). Các khả năng là vô hạn, và người dùng của bạn sẽ cảm ơn bạn vì đầu ra được tinh chỉnh.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}