---
category: general
date: 2025-12-29
description: Các tùy chọn tải Aspose cho phép bạn tải các tệp DOCX trong khi tùy chỉnh
  cài đặt phông chữ và phát hiện các phông chữ thiếu. Tìm hiểu cách tải docx với kiểm
  soát hoàn toàn.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: vi
og_description: Tùy chọn tải Aspose cho phép bạn tải các tệp DOCX đồng thời tùy chỉnh
  cài đặt phông chữ và phát hiện các phông chữ thiếu. Tìm hiểu cách tải docx với kiểm
  soát đầy đủ.
og_title: Tùy chọn tải Aspose – Tải DOCX với cài đặt phông chữ tùy chỉnh
tags:
- Aspose.Words
- C#
- Document Processing
title: Tùy chọn tải Aspose – Tải DOCX với cài đặt phông chữ tùy chỉnh
url: /vi/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Load Options – Tải DOCX với Cài Đặt Phông Tùy Chỉnh

Bạn đã bao giờ thắc mắc làm sao để tải một tệp DOCX trong C# mà không gặp phải vấn đề phông chữ thiếu chưa? Bạn không phải là người duy nhất. **Aspose Load Options** cho phép bạn kiểm soát chính xác cách một tài liệu Word được mở, giúp bạn thiết lập **cài đặt phông tùy chỉnh** và thậm chí phát hiện phông chữ thiếu trước khi chúng trở thành vấn đề.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình tải một DOCX bằng Aspose.Words, cấu hình **cài đặt phông tùy chỉnh**, và gắn một callback cảnh báo để thông báo những phông chữ nào đang thiếu. Khi kết thúc, bạn sẽ có thể **tải tài liệu Word** một cách tự tin, bất kể tác giả gốc đã sử dụng phông chữ nào.

> **Prerequisite** – Bạn cần có Aspose.Words for .NET (phiên bản mới nhất) được tham chiếu trong dự án và có kiến thức cơ bản về C#. Không cần thư viện nào khác.

## Những Điều Bạn Sẽ Học

- Cách tạo đối tượng `LoadOptions` và gắn một callback cảnh báo.  
- Cách thiết lập `FontSettings` cho **cài đặt phông tùy chỉnh**.  
- Cách thực sự **tải docx** và xác minh rằng các phông chữ thiếu được báo cáo.  
- Mẹo xử lý các trường hợp đặc biệt như phông chữ nhúng hoặc thư mục phông chữ trên mạng.

## Bước 1: Cài Đặt Aspose.Words và Chuẩn Bị Dự Án

Đầu tiên, hãy chắc chắn rằng Aspose.Words đã được cài đặt. Cách dễ nhất là qua NuGet:

```bash
dotnet add package Aspose.Words
```

Sau khi thêm gói, tạo một dự án console C# mới (hoặc chèn mã vào bất kỳ ứng dụng nào hiện có). Mã chúng ta sẽ viết hoạt động với .NET 6+ và .NET Framework 4.7.2+, vì vậy bạn sẽ được hỗ trợ ở cả hai môi trường.

> **Mẹo:** Nếu bạn đang nhắm tới .NET Core, thêm `using System;` ở đầu tệp; IDE thường sẽ tự động chèn nó.

## Bước 2: Cấu Hình Aspose Load Options với Callback Cảnh Báo

Bây giờ chúng ta đến phần cốt lõi—**aspose load options**. Lớp `LoadOptions` cho phép bạn tinh chỉnh cách tài liệu được phân tích. Chúng ta sẽ dùng nó để:

1. Gắn một callback sẽ được kích hoạt mỗi khi trình tải không tìm thấy phông chữ được yêu cầu.  
2. Gán một thể hiện `FontSettings` mà sau này có thể được điều chỉnh cho **cài đặt phông tùy chỉnh**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Tại sao điều này quan trọng:** Nếu không có callback cảnh báo, Aspose sẽ im lặng thay thế các phông chữ thiếu, điều này có thể gây ra những bất ngờ về bố cục sau này. Bằng cách hook vào callback, bạn **phát hiện phông chữ thiếu** sớm và có thể quyết định nhúng phông thay thế hoặc yêu cầu người dùng cài đặt phông chữ còn thiếu.

## Bước 3: Tải DOCX Bằng Các Tùy Chọn Đã Cấu Hình

Với `LoadOptions` đã sẵn sàng, việc tải một DOCX chỉ cần một dòng lệnh. Hàm khởi tạo `Document` nhận đường dẫn tới tệp và các tùy chọn chúng ta vừa xây dựng.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Nếu tệp nguồn tham chiếu một phông chữ không có trên hệ thống hoặc trong thư mục tùy chỉnh, bạn sẽ thấy đầu ra như:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Phản hồi ngay lập tức này vô cùng quý giá khi bạn xây dựng một pipeline xử lý hàng loạt cần đảm bảo độ chính xác về hình ảnh.

## Bước 4: Xác Minh Tài Liệu Đã Tải (Tùy Chọn nhưng Hữu Ích)

Sau khi tải, bạn có thể muốn xác nhận rằng nội dung tài liệu có thể truy cập được. Để kiểm tra nhanh, hãy xuất ra văn bản của đoạn văn đầu tiên.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Chạy chương trình ngay bây giờ sẽ cho bạn:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Bước 5: Các Trường Hợp Đặc Biệt & Mẹo Nâng Cao

### 5.1 Xử Lý Phông Chữ Nhúng

Một số tệp DOCX nhúng sẵn các phông chữ cần thiết. Aspose.Words sẽ tự động sử dụng chúng, vì vậy bạn sẽ không thấy cảnh báo cho những phông này. Tuy nhiên, nếu bạn cố ý **tải tài liệu Word** mà đã loại bỏ các phông chữ nhúng (ví dụ, sau một quá trình chuyển đổi), bạn có thể cần cung cấp các phông chữ còn thiếu qua `SetFontsFolder` như đã minh họa ở trên.

### 5.2 Sử Dụng Memory Stream Thay Vì Đường Dẫn Tệp

Nếu DOCX của bạn nằm trong cơ sở dữ liệu hoặc đến từ một yêu cầu HTTP, bạn có thể tải nó từ một `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Các **aspose load options** vẫn được áp dụng, và callback cảnh báo vẫn hoạt động.

### 5.3 Ghi Đè Thay Thế Phông Chữ Toàn Cục

Nếu bạn muốn thay thế các phông chữ thiếu bằng một phông dự phòng cụ thể (ví dụ, Arial), bạn có thể thêm một quy tắc thay thế:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Kết hợp điều này với callback cảnh báo để ghi lại sự kiện thay thế và giữ cho đầu ra của bạn nhất quán.

## Bước 6: Ví Dụ Hoàn Chỉnh

Dưới đây là chương trình đầy đủ, sẵn sàng sao chép‑dán, bao gồm tất cả các bước ở trên. Lưu lại dưới tên `Program.cs`, khôi phục các gói NuGet, và chạy.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Đầu Ra Dự Kiến

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Nếu không có phông chữ nào bị thiếu, các dòng cảnh báo sẽ không xuất hiện.

## Tổng Quan Trực Quan

![ví dụ tùy chọn tải aspose](/images/aspose-load-options.png "Sơ đồ hiển thị quy trình làm việc của Aspose Load Options")

*Biểu đồ minh họa cách **Aspose Load Options** nằm giữa nguồn tệp của bạn và đối tượng `Document`, xử lý việc giải quyết phông chữ và phát hiện phông chữ thiếu.*

## Kết Luận

Chúng ta đã đi qua một giải pháp hoàn chỉnh cho **aspose load options**, cho bạn thấy chính xác **cách tải docx** đồng thời áp dụng **cài đặt phông tùy chỉnh** và **phát hiện phông chữ thiếu**. Bằng cách cấu hình một callback cảnh báo và tùy chọn chỉ định thư mục phông chữ tùy chỉnh cho Aspose, bạn sẽ có toàn bộ khả năng quan sát các vấn đề về phông trước khi chúng ảnh hưởng đến việc render.

Từ đây, bạn có thể khám phá các chủ đề liên quan như **chuyển đổi tài liệu Word** sang PDF, thêm watermark, hoặc xử lý hàng chục tệp trong một thư mục. Mẫu tương tự—tạo `LoadOptions`, gắn callback, và gọi `new Document(...)`—hoạt động trên toàn bộ API của Aspose.Words.

Có câu hỏi về một trường hợp đặc biệt, chẳng hạn xử lý ngôn ngữ phải‑từ‑trái hoặc tệp DOCX được mã hoá? Hãy để lại bình luận hoặc tham khảo tài liệu Aspose.Words để tìm hiểu sâu hơn. Chúc bạn lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng như mong muốn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}