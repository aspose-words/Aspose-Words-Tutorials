---
category: general
date: 2026-05-23
description: Đặt callback cảnh báo Aspose để bắt các cảnh báo thay thế phông chữ trong
  Aspose.Words. Tìm hiểu LoadOptions, FontSettings và cách triển khai IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: vi
og_description: đặt callback cảnh báo của aspose để giám sát việc thay thế phông chữ
  trong Aspose.Words. Hướng dẫn này trình bày cách sử dụng LoadOptions, FontSettings
  và triển khai trình xử lý cảnh báo.
og_title: Đặt callback cảnh báo Aspose – Hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Đặt callback cảnh báo Aspose – Hướng dẫn đầy đủ về tải tài liệu Word
url: /vi/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Hướng Dẫn Toàn Diện cho Việc Tải Tài Liệu Word

Bạn có bao giờ tự hỏi làm thế nào để **set warning callback aspose** để không bao giờ bỏ lỡ cảnh báo thay thế phông chữ nữa không? Bạn không phải là người duy nhất. Khi một tệp DOCX tham chiếu tới một phông chữ chưa được cài đặt, Aspose.Words sẽ im lặng thay thế nó, và nếu không có callback thích hợp, bạn có thể không bao giờ biết có gì đã thay đổi.

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ đầy đủ, có thể chạy được, cho thấy cách bắt các cảnh báo đó. Khi kết thúc, bạn sẽ hiểu **Aspose.Words LoadOptions**, cách cấu hình **FontSettings**, và lý do tại sao việc triển khai **IWarningCallback** là cách sạch nhất để luôn được thông báo. Không có phần thừa—chỉ có mã bạn có thể đưa vào dự án .NET ngay hôm nay.

## Những Điều Bạn Sẽ Học

- Cách **set warning callback aspose** trên một thể hiện `LoadOptions`.
- Vai trò của **Aspose.Words LoadOptions** khi mở tài liệu.
- Cấu hình việc xử lý **Aspose fonts substitution** bằng `FontSettings`.
- Viết một **IWarningCallback implementation** tùy chỉnh để ghi lại các vấn đề về phông chữ.
- Tải tài liệu một cách an toàn với các thực hành tốt nhất của **Aspose document loading**.

### Yêu Cầu Trước

- .NET 6.0 trở lên (mã cũng hoạt động trên .NET Framework 4.5+).
- Giấy phép Aspose.Words for .NET hợp lệ hoặc khóa dùng thử.
- Visual Studio, Rider, hoặc bất kỳ trình chỉnh sửa C# nào bạn thích.
- Một tệp DOCX mẫu (`fontTest.docx`) tham chiếu tới một phông chữ thiếu (tùy chọn nhưng hữu ích).

> **Mẹo chuyên nghiệp:** Nếu bạn không có tệp DOCX thiếu phông chữ, chỉ cần đổi tên một phông chữ trong kiểu của tài liệu và quan sát cảnh báo được kích hoạt.

## Cách set warning callback aspose cho việc tải tài liệu

Dưới đây là chương trình đầy đủ, tự chứa. Lưu nó dưới tên `Program.cs`, khôi phục các gói NuGet, và chạy. Console sẽ in ra mọi cảnh báo thay thế phông chữ mà Aspose.Words tạo ra trong quá trình tải tệp.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Đầu ra console dự kiến

Nếu `fontTest.docx` tham chiếu tới một phông chữ chưa được cài đặt, bạn sẽ thấy một cái gì đó như sau:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Nếu mọi phông chữ đều có, dòng duy nhất được in ra sẽ là *Document loaded successfully*—không có cảnh báo, không có tiếng ồn.

![set warning callback aspose example](image.png "set warning callback aspose example")

## Hiểu LoadOptions trong Aspose.Words

`LoadOptions` là cổng vào cho mọi tùy chỉnh bạn có thể thực hiện trong **aspose document loading**. Nó cho phép bạn:

1. **Chỉ định một `FontSettings` tùy chỉnh** – hữu ích khi ứng dụng của bạn cung cấp các phông chữ riêng.  
2. **Gắn một warning callback** – chính xác như chúng ta đã làm để bắt các thay thế phông chữ.  
3. Kiểm soát việc phát hiện định dạng tài liệu, xử lý mật khẩu, và hơn thế nữa.

Vì `LoadOptions` được truyền vào hàm khởi tạo `Document`, các cài đặt được áp dụng **một lần**, ngay tại thời điểm tệp được phân tích. Đó là lý do chúng ta có thể đảm bảo handler cảnh báo của mình sẽ thấy mọi sự thay thế trước khi tài liệu được tạo trong bộ nhớ.

### Khi nào nên sử dụng LoadOptions tùy chỉnh

- **Xử lý hàng loạt** nhiều tệp mà bạn muốn một chiến lược ghi log đồng nhất.  
- **Dịch vụ đám mây** cần báo cáo các phông chữ thiếu cho người gọi.  
- **Pipeline kiểm thử** xác minh tài liệu tuân thủ chính sách phông chữ của công ty.

## Cấu hình FontSettings cho Aspose fonts substitution

The `FontSettings` object kiểm soát cách Aspose.Words giải quyết phông chữ. Mặc định nó tìm kiếm trong các thư mục phông chữ của hệ thống, sau đó dựa vào các thay thế tích hợp. Bạn có thể tinh chỉnh hành vi này:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Các dòng này là tùy chọn cho kịch bản “set warning callback aspose” cơ bản, nhưng chúng minh họa cách bạn có thể **giảm** số lượng cảnh báo thay thế bằng cách cung cấp các phông chữ phù hợp ngay từ đầu.

## Triển khai IWarningCallback cho các cảnh báo thay thế phông chữ

Giao diện `IWarningCallback` rất nhỏ—chỉ có một phương thức `Warning`. Tuy nhiên nó cung cấp cho bạn **toàn quyền** trong việc xử lý cảnh báo:

- **Ghi log vào tệp** thay vì console.  
- **Thu thập các cảnh báo** vào một danh sách để phân tích sau.  
- **Ném ngoại lệ** cho các cảnh báo quan trọng (ví dụ, khi một phông chữ bắt buộc bị thiếu).

Dưới đây là một ví dụ nhanh lưu các cảnh báo vào một `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Bạn có thể kiểm tra `handler.Messages` sau khi tải tài liệu để quyết định có nên hủy quá trình xử lý hay không.

## Tải tài liệu với xử lý cảnh báo tùy chỉnh (quy trình đầy đủ)

Kết hợp mọi thứ lại, mẫu cuối cùng mà bạn có thể tái sử dụng trông như sau:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Đoạn mã này minh họa luồng **aspose document loading** mà bạn sẽ dùng trong môi trường sản xuất: cấu hình, tải, rồi phản hồi. Mẫu này mở rộng tốt dù bạn đang xử lý một tệp đơn lẻ hay lặp qua hàng ngàn tệp.

## Các Câu Hỏi Thường Gặp & Trường Hợp Cạnh

**Nếu tài liệu được bảo vệ bằng mật khẩu thì sao?**  
Thêm `Password = "secret"` vào khởi tạo `LoadOptions`. Callback cảnh báo vẫn hoạt động sau khi tệp được giải mã.

**Callback có được kích hoạt cho các loại cảnh báo khác không?**  
Có—`WarningInfo.Type` có thể là `DocumentStructure`, `UnsupportedFileFormat`, v.v. Trong ví dụ của chúng ta, chúng ta lọc cho `FontSubstitution`, nhưng bạn có thể ghi lại mọi thứ bằng cách loại bỏ kiểm tra `if`.

**Điều này có ảnh hưởng tới hiệu năng không?**  
Rất ít. Callback chỉ được gọi khi có cảnh báo, điều này xảy ra ít hơn nhiều so với các bước phân tích thông thường.

**Tôi có thể tắt hoàn toàn việc thay thế phông chữ không?**  
Bạn có thể đặt `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` nhưng sau đó Aspose.Words sẽ ném ngoại lệ cho các phông chữ thiếu thay vì tự động thay thế.

## Kết Luận

Bây giờ bạn đã biết chính xác cách **set warning callback aspose** để giám sát các sự kiện thay thế phông chữ trong quá trình xử lý **Aspose.Words LoadOptions**. Bằng cách cấu hình `FontSettings`, triển khai một `IWarningCallback` nhẹ, và tải tài liệu với các tùy chọn đó, bạn sẽ có toàn bộ khả năng quan sát mọi thay đổi phông chữ mà Aspose thực hiện phía sau.

Từ đây bạn có thể:

- Mở rộng handler cảnh báo để ghi vào dịch vụ log trung tâm.  
- Kết hợp callback với chiến lược fallback phông chữ tùy chỉnh.  
- Sử dụng mẫu này khi xây dựng API đám mây xác thực tài liệu do khách hàng tải lên.

Hãy thử với các tệp DOCX của bạn, điều chỉnh `FontSettings`, và quan sát console thông báo chính xác những phông chữ nào đã được thay thế. Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng như mong muốn!

## Các Hướng Dẫn Liên Quan

- [Ghi lại Cảnh báo Thay thế Phông chữ trong Java với Aspose.Words – Hướng Dẫn Toàn Diện](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Bật Cảnh báo Thay thế Phông chữ trong Aspose.Words – Hướng Dẫn Toàn Diện](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Cách Đặt LoadOptions trong Aspose.Words cho Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}