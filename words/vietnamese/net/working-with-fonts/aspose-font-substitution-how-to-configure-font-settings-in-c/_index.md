---
category: general
date: 2026-03-27
description: 'Thay thế phông chữ Aspose trở nên dễ dàng: học cách cấu hình cài đặt
  phông chữ, ghi lại cảnh báo và xử lý các phông chữ thiếu trong ứng dụng .NET của
  bạn.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: vi
og_description: Thành thạo việc thay thế phông chữ Aspose bằng cách cấu hình cài đặt
  phông chữ và xử lý các phông chữ thiếu bằng callback cảnh báo. Hướng dẫn C# đầy
  đủ.
og_title: Thay thế phông chữ Aspose – Cấu hình cài đặt phông chữ trong C#
tags:
- Aspose.Words
- C#
- Font Management
title: Thay thế phông chữ Aspose – Cách cấu hình cài đặt phông chữ trong C#
url: /vi/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thay Thế Phông Chữ Aspose – Hướng Dẫn Toàn Diện Để Cấu Hình Cài Đặt Phông

Bạn đã bao giờ gặp phải một tài liệu đột nhiên thay đổi phông chữ tùy chỉnh của mình thành một phông chữ chung chung chưa? Đó là **aspose font substitution** đang thực hiện công việc của nó — thay thế các phông chữ bị thiếu bằng phông chữ gần nhất mà nó có thể tìm thấy. Điều này tiện lợi, nhưng nếu bạn cần biết *chính xác* phông chữ nào đã được thay thế, bạn phải truy cập vào hệ thống cảnh báo của thư viện và tự cấu hình cài đặt phông chữ.

Trong hướng dẫn này, chúng ta sẽ đi qua một kịch bản thực tế: tải một tệp DOCX tham chiếu đến một phông chữ mà bạn không có, bắt sự kiện thay thế, và in một thông báo thân thiện ra console. Khi kết thúc, bạn sẽ quen thuộc với **configure font settings**, thiết lập một **Aspose.Words warning callback**, và mở rộng mẫu để phù hợp với bất kỳ quy trình làm việc nào.

> **Bạn sẽ cần**  
> • .NET 6+ (hoặc .NET Framework 4.7.2+)  
> • Aspose.Words cho .NET (phiên bản NuGet mới nhất)  
> • Một tệp DOCX tham chiếu đến một phông chữ bị thiếu (chúng tôi sẽ gọi nó là `MissingFont.docx`)  

Hãy bắt đầu.

---

## Bước 1: Cài Đặt Aspose.Words và Chuẩn Bị Dự Án

Trước khi chúng ta viết bất kỳ mã nào, hãy chắc chắn rằng gói Aspose.Words đã được tham chiếu:

```bash
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Sử dụng phiên bản ổn định mới nhất; tính đến tháng 3 2026, phiên bản là 23.11.0. Các bản phát hành mới hơn cải thiện thuật toán khớp phông và thêm các loại cảnh báo bổ sung.

Tạo một ứng dụng console mới (hoặc chèn mã vào dự án hiện có) và thêm các chỉ thị `using` thông thường:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Các không gian tên này cho phép chúng ta truy cập vào `Document`, `LoadOptions`, và các lớp liên quan đến phông chữ mà chúng ta sẽ cần.

## Bước 2: Cấu Hình Cài Đặt Phông Chữ với LoadOptions

Trung tâm của việc kiểm soát **aspose font substitution** nằm trong `LoadOptions.FontSettings`. Bằng cách cung cấp một đối tượng `FontSettings` rỗng, chúng ta nói với Aspose sử dụng các đường dẫn tìm kiếm mặc định *và* báo cáo bất kỳ sự thay thế nào thông qua một callback cảnh báo.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Tại sao không chỉ dựa vào mặc định? Bởi vì việc gắn một callback cảnh báo (bước tiếp theo) chỉ hoạt động khi thuộc tính `FontSettings` không phải là null. Dòng mã nhỏ này cung cấp cho chúng ta một điểm nối vào quá trình thay thế mà không thay đổi hành vi tìm kiếm phông chữ thực tế.

## Bước 3: Gắn Callback Cảnh Báo để Bắt Lại Các Sự Thay Thế

Aspose.Words triển khai giao diện `IWarningCallback`. Bất cứ khi nào có điều gì đáng chú ý xảy ra — chẳng hạn như một phông chữ bị thiếu — nó sẽ gọi phương thức `Warning` của chúng ta. Chúng ta sẽ triển khai một trình xử lý nhỏ để lọc `WarningType.FontSubstitution` và in mô tả.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Và đây là phần xử lý thực tế:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Tại sao điều này quan trọng** – Nếu không có callback, Aspose sẽ thay thế phông chữ một cách im lặng, và bạn sẽ không bao giờ biết phông chữ nào đã được sử dụng. Callback làm cho quá trình này trở nên trong suốt, điều này rất cần thiết cho việc báo cáo tuân thủ hoặc gỡ lỗi các vấn đề bố cục.

## Bước 4: Tải Tài Liệu Sử Dụng Các Tùy Chọn Đã Cấu Hình

Bây giờ chúng ta cuối cùng tải tài liệu, truyền `loadOptions` mà chúng ta vừa chuẩn bị. Nếu tệp nguồn tham chiếu đến một phông chữ chưa được cài đặt, trình xử lý của chúng ta sẽ được kích hoạt.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Thay thế `YOUR_DIRECTORY` bằng đường dẫn thực tế nơi chứa `MissingFont.docx`. Khi bạn chạy chương trình, bạn sẽ thấy đầu ra tương tự như:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Dòng này cho bạn biết chính xác phông chữ nào bị thiếu và phông chữ thay thế nào mà Aspose đã chọn.

## Bước 5: (Tùy Chọn) Tinh Chỉnh Đường Dẫn Tìm Kiếm Phông Chữ

Nếu bạn có một thư mục riêng chứa các phông chữ công ty, bạn có thể chỉ định cho Aspose nơi tìm kiếm trước khi nó quay lại các phông chữ hệ thống. Đây là một cách sử dụng nâng cao của **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Cài đặt `recursive: true` khiến Aspose quét cả các thư mục con. Bây giờ thư viện sẽ thử các phông chữ riêng của bạn trước, giảm khả năng xảy ra sự thay thế không mong muốn.

## Ví Dụ Hoàn Chỉnh Hoạt Động

Kết hợp mọi thứ lại, dưới đây là chương trình hoàn chỉnh, sẵn sàng để chạy:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Kết quả mong đợi** (khi gặp phông chữ bị thiếu):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Nếu tất cả các phông chữ đều có, chương trình sẽ chạy im lặng (không có cảnh báo) và vẫn tạo ra file PDF.

## Các Câu Hỏi Thường Gặp & Trường Hợp Đặc Biệt

### Nếu tôi muốn *ngăn* việc thay thế hoàn toàn thì sao?

Đặt `FontSettings.SubstitutionSettings` thành `null` hoặc sử dụng `FontSettings.FontSubstitutionSettings` để kiểm soát hành vi. Ví dụ:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Bây giờ Aspose sẽ ném ra một ngoại lệ thay vì thay thế im lặng, ngoại lệ này có thể được bắt và xử lý.

### Điều này có hoạt động với các định dạng tệp khác (ví dụ: .doc, .rtf) không?

Chắc chắn rồi. Đối tượng `LoadOptions` giống nhau có thể được truyền vào bất kỳ hàm khởi tạo `Document` nào chấp nhận đường dẫn tệp. Callback cảnh báo sẽ được kích hoạt cho tất cả các định dạng dựa vào phông chữ.

### Tôi có thể bắt được tên phông chữ thay thế *chính xác* không?

Có. Chuỗi `info.Description` chứa cả phông chữ bị thiếu và phông chữ thay thế. Nếu bạn cần tên này trong mã, bạn có thể phân tích chuỗi hoặc sử dụng đối tượng `FontInfo` (có sẵn trong các phiên bản mới hơn).

### Điều này hoạt động như thế nào trong môi trường đa luồng?

`FontSettings` **không** an toàn với đa luồng. Tạo một `LoadOptions` riêng (với `FontSettings` riêng) cho mỗi luồng, hoặc bảo vệ truy cập bằng một lock.

## Kết Luận

Chúng tôi đã bao phủ mọi thứ bạn cần để thành thạo **aspose font substitution** và **configure font settings** trong một ứng dụng C#:

1. Cài đặt Aspose.Words và thêm các chỉ thị `using` cần thiết.  
2. Tạo một đối tượng `LoadOptions` với một `FontSettings` mới.  
3. Gắn một `IWarningCallback` tùy chỉnh để hiển thị các sự kiện thay thế.  
4. Tải tài liệu, cho phép callback báo cáo bất kỳ phông chữ nào bị thiếu.  
5. (Tùy chọn) Mở rộng đường dẫn tìm kiếm hoặc vô hiệu hoá hoàn toàn việc thay thế.

Với mẫu này, bạn có thể ghi lại các phông chữ bị thiếu để tuân thủ, cảnh báo người dùng trong giao diện UI, hoặc tự động nhúng các phông chữ thay thế trước khi xuất bản. Tiếp theo, bạn có thể khám phá **chính sách thay thế phông chữ Aspose.Words** hoặc tích hợp quy trình này vào một pipeline xử lý tài liệu lớn hơn.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng phông chữ!  

---  

![Sơ đồ cho thấy Aspose.Words tải một tài liệu, gọi FontSettings, kích hoạt một callback cảnh báo, và xuất thông tin thay thế](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}