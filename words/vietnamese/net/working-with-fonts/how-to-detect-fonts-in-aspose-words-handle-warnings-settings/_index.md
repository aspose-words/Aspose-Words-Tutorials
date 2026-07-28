---
category: general
date: 2026-01-03
description: Cách phát hiện phông chữ trong Aspose.Words và xử lý cảnh báo bằng cài
  đặt phông chữ Aspose – hướng dẫn từng bước cho nhà phát triển.
draft: false
keywords:
- how to detect fonts
- how to handle warnings
- aspose font settings
- how to configure warnings
language: vi
og_description: Cách phát hiện phông chữ trong Aspose.Words và cấu hình cảnh báo với
  cài đặt phông chữ Aspose. Học quy trình đầy đủ trong vài phút.
og_title: Cách phát hiện phông chữ trong Aspose.Words – Xử lý cảnh báo
tags:
- Aspose.Words
- C#
- Document Processing
title: Cách phát hiện phông chữ trong Aspose.Words – Xử lý cảnh báo và cài đặt
url: /vi/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách phát hiện phông chữ trong Aspose.Words – Xử lý cảnh báo & Cài đặt

Bạn đã bao giờ tự hỏi **cách phát hiện phông chữ** trong tài liệu Word trước khi đưa vào sản xuất chưa? Bạn không phải là người duy nhất. Các phông chữ thiếu có thể gây ra những rắc rối về bố cục, và nếu không có cảnh báo phù hợp, bạn có thể phát hành một file PDF hoặc DOCX bị hỏng mà không hề biết.  

Trong tutorial này, chúng ta sẽ đi qua **cách phát hiện phông chữ** bằng Aspose.Words, trình bày **cách xử lý cảnh báo**, và tinh chỉnh **cài đặt phông chữ Aspose** để bạn có thể **cấu hình cảnh báo** chính xác theo nhu cầu. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy, in ra mọi lần thay thế phông chữ mà Aspose thực hiện, và bạn sẽ biết cách điều chỉnh nó cho các dự án của mình.

## Các yêu cầu trước

- .NET 6+ (hoặc .NET Framework 4.6+).  
- Aspose.Words for .NET được cài đặt qua NuGet (`Install-Package Aspose.Words`).  
- Một file Word có cố ý tham chiếu tới phông chữ thiếu (ví dụ, *DocumentWithMissingFonts.docx*).  

Nếu bạn đã có những thứ trên, tuyệt vời—hãy bắt đầu.

![ảnh chụp màn hình cách phát hiện phông chữ](https://example.com/detect-fonts.png "kết quả ví dụ cách phát hiện phông chữ")

## Cách phát hiện phông chữ với Aspose.Words

Bước đầu tiên là thông báo cho Aspose.Words rằng bạn quan tâm tới các sự kiện thay thế phông chữ. Điều này được thực hiện bằng cách cung cấp một callback cảnh báo tùy chỉnh thông qua **cài đặt phông chữ Aspose**. Callback sẽ nhận một đối tượng `WarningInfo` cho mỗi lần thay thế, cho phép bạn **phát hiện phông chữ** trong thời gian chạy.

### Bước 1: Tạo lớp Callback Cảnh báo

Triển khai giao diện `IWarningCallback`. Trong phương thức `Warning`, lọc các cảnh báo có `WarningType.FontSubstitution` và ghi lại chi tiết.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Receives warnings from Aspose.Words during document loading.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only act on font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **detect fonts** that were missing.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

> **Mẹo chuyên nghiệp:** Chuỗi `info.Description` chứa cả tên phông chữ thiếu và phông chữ thay thế mà Aspose đã chọn. Bạn có thể phân tích nó nếu cần báo cáo có cấu trúc.

### Bước 2: Cấu hình LoadOptions với Cài đặt Phông chữ Aspose

Tạo một thể hiện `LoadOptions`, gắn một đối tượng `FontSettings` mới, và chỉ định `WarningCallback` tới handler vừa tạo. Điều này cho Aspose biết **cách cấu hình cảnh báo**.

```csharp
// Prepare load options – this is where we **configure warnings**.
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings can be further customized (e.g., add a custom folder).
    FontSettings = new FontSettings(),
    WarningCallback = new FontSubstitutionWarningHandler()
};
```

Nếu bạn có một thư mục phông chữ riêng, bạn có thể thêm nó như sau:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

Dòng này cho thấy một khía cạnh khác của **cài đặt phông chữ Aspose**—bạn kiểm soát chính xác nơi Aspose tìm kiếm phông chữ trước khi quyết định thay thế.

### Bước 3: Tải tài liệu và kích hoạt Callback

Bây giờ tải tài liệu mục tiêu bằng `loadOptions`. Khi Aspose phân tích file, bất kỳ phông chữ nào thiếu sẽ kích hoạt handler cảnh báo, thực tế **phát hiện phông chữ** ngay lập tức.

```csharp
// The document contains missing fonts, which will fire our warning handler.
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);
```

Khi chạy chương trình, bạn sẽ thấy đầu ra tương tự như:

```
Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font substituted: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

### Bước 4: (Tùy chọn) Thu thập Cảnh báo để Sử dụng Sau

Nếu bạn cần lưu trữ dữ liệu thay thế cho một báo cáo, chỉnh sửa handler để tích lũy các thông điệp vào một danh sách.

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public List<string> Substitutions { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Substitutions.Add(info.Description);
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Sau này bạn có thể ghi `handler.Substitutions` ra file JSON, gửi tới dịch vụ logging, hoặc hiển thị trong UI.

### Bước 5: Xác minh Kết quả Theo Chương trình

Đôi khi bạn muốn khẳng định rằng *không* có sự thay thế nào xảy ra (ví dụ, trong một build CI). Đây là một kiểm tra nhanh:

```csharp
var handler = new FontSubstitutionWarningHandler();
loadOptions.WarningCallback = handler;

Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFonts.docx", loadOptions);

if (handler.Substitutions.Count == 0)
{
    Console.WriteLine("All fonts were found – no substitutions.");
}
else
{
    Console.WriteLine($"Detected {handler.Substitutions.Count} missing fonts.");
}
```

Đoạn mã này minh họa **cách xử lý cảnh báo** một cách quyết đoán, cho bạn toàn quyền kiểm soát quy trình build.

## Các câu hỏi thường gặp (và các trường hợp đặc biệt)

**Nếu tôi muốn bỏ qua một số lần thay thế nhất định thì sao?**  
Bạn có thể thêm logic điều kiện trong `Warning` và chỉ đơn giản `return` mà không ghi log cho những phông chữ bạn cho là chấp nhận được.

**Có thể tắt toàn bộ cảnh báo và chỉ nhận kết quả boolean không?**  
Có—đặt `loadOptions.WarningCallback = null` và sau đó kiểm tra `doc.FontInfo` sau khi tải (mặc dù bạn sẽ mất chi tiết log).

**Điều này có hoạt động khi chuyển đổi sang PDF không?**  
Chắc chắn. Cơ chế cảnh báo giống nhau sẽ được kích hoạt khi bạn gọi `doc.Save("out.pdf")`. Callback sẽ bắt mọi lần hoán đổi phông chữ diễn ra trong bước chuyển đổi.

**Có ảnh hưởng tới hiệu năng không?**  
Chi phí chỉ là vài lời gọi phương thức bổ sung cho mỗi phông chữ thiếu. Đối với các batch lớn, bạn có thể muốn cache kết quả.

## Tổng kết: Những gì chúng ta đã đề cập

- **Cách phát hiện phông chữ** bằng cách triển khai một `IWarningCallback` tùy chỉnh.  
- **Cách xử lý cảnh báo** thông qua `LoadOptions.WarningCallback`.  
- Tinh chỉnh **cài đặt phông chữ Aspose** (thêm thư mục phông chữ tùy chỉnh, bật/tắt cảnh báo).  
- **Cách cấu hình cảnh báo** cho cả đầu ra console ngay lập tức và phân tích sau này.  

Với những phần này, bạn có thể tự tin xử lý tài liệu Word, đảm bảo rằng các phông chữ thiếu được đánh dấu, và duy trì kết quả nhất quán trên mọi môi trường.

## Các bước tiếp theo

- Khám phá `FontSettings.SubstitutionSettings` để kiểm soát chi tiết hơn (ví dụ, ánh xạ các phông chữ thiếu cụ thể tới các phông chữ thay thế đã chọn).  
- Kết hợp cách tiếp cận này với Aspose.PDF để tạo PDF giữ nguyên kiểu chữ chính xác.  
- Tự động hoá kiểm tra cảnh báo trong pipeline CI/CD để chặn các bản phát hành có vấn đề về phông chữ—hoàn hảo cho các đội nhóm **xử lý cảnh báo** như một phần của cổng chất lượng.

Có thêm câu hỏi về **cài đặt phông chữ Aspose** hoặc cần hỗ trợ tích hợp vào dịch vụ lớn hơn? Hãy để lại bình luận bên dưới, chúc bạn lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}