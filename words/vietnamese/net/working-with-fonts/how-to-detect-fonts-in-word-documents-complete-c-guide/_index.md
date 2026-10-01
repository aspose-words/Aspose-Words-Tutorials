---
category: general
date: 2026-02-24
description: Cách phát hiện phông chữ trong tài liệu Word bằng Aspose.Words. Tìm hiểu
  cách thiết lập callback và tải tài liệu Word với ví dụ mã đầy đủ.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: vi
og_description: Cách phát hiện phông chữ trong tài liệu Word bằng callback cảnh báo.
  Hướng dẫn này cho thấy cách thiết lập callback và tải tài liệu Word bằng Aspose.Words.
og_title: Cách phát hiện phông chữ trong tài liệu Word – Hướng dẫn C# chi tiết từng
  bước
tags:
- C#
- Aspose.Words
- Document Processing
title: Cách phát hiện phông chữ trong tài liệu Word – Hướng dẫn C# đầy đủ
url: /vi/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách phát hiện phông chữ trong tài liệu Word – Hướng dẫn C# đầy đủ

Bạn đã bao giờ tự hỏi **cách phát hiện phông chữ** bị thiếu khi tải một tệp Word chưa? Có thể bạn đã gặp một tài liệu trông ổn trong trình soạn thảo, nhưng PDF bạn tạo ra lại thay đổi một vài kiểu chữ phía sau. Đó là dấu hiệu điển hình của việc thay thế phông chữ, và việc phát hiện sớm có thể giúp bạn tránh những bất ngờ về bố cục.

Trong hướng dẫn này, chúng ta sẽ đi qua một giải pháp thực tế: sử dụng **Aspose.Words** để tải một `.docx`, gắn một callback cảnh báo, và **cách thiết lập callback** để báo cáo mọi lần thay thế phông chữ. Khi kết thúc, bạn không chỉ biết **cách phát hiện phông chữ** một cách lập trình, mà còn hiểu **cách thiết lập callback** đúng và **tải tài liệu word** một cách an toàn — tất cả trong một ví dụ C# có thể chạy được.

> **Bạn sẽ nhận được**
> * Một mẫu mã hoàn chỉnh, sẵn sàng sao chép‑dán  
> * Giải thích chi tiết từng dòng một cách từng bước  
> * Mẹo xử lý các trường hợp đặc biệt như nhiều phông chữ thiếu hoặc thư mục phông chữ tùy chỉnh  
> * Đầu ra console dự kiến để bạn có thể xác minh mọi thứ hoạt động

---

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Core)  
- Gói NuGet Aspose.Words cho .NET (`Install-Package Aspose.Words`)  
- Một tệp Word có cố ý tham chiếu tới một phông chữ bạn không cài đặt (ví dụ, `MissingFont.docx`)  
- Visual Studio, Rider, hoặc bất kỳ trình chỉnh sửa nào bạn thích

Không cần thư viện nào khác; mọi thứ còn lại đều là một phần của runtime .NET tiêu chuẩn.

---

## Cách phát hiện phông chữ trong tài liệu Word

### Bước 1: Tạo Load Options và Gắn Callback Cảnh báo

Điều đầu tiên chúng ta làm là thông báo cho Aspose.Words rằng chúng ta muốn nhận thông báo về bất kỳ vấn đề nào phát sinh khi tải tệp. Đây là nơi **cách thiết lập callback** đóng vai trò.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Tại sao điều này quan trọng:**  
`LoadOptions` là cổng vào để tùy chỉnh quá trình tải. Bằng cách gán một thể hiện của `FontWarningCollector` cho `WarningCallback`, Aspose.Words sẽ gọi phương thức `Warning` của chúng ta mỗi khi nó thay thế một phông chữ thiếu bằng phông chữ dự phòng. Đây là cốt lõi của **cách phát hiện phông chữ** không có trên máy.

### Bước 2: Chuẩn bị thể hiện LoadOptions

Bây giờ chúng ta tạo một thể hiện của `LoadOptions` và gắn callback của mình.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Mẹo chuyên nghiệp:** Nếu bạn cần kiểm soát *nơi* Aspose tìm kiếm phông chữ thay thế, bạn cũng có thể đặt `loadOptions.FontSettings` ở đây. Điều này hữu ích khi bạn có một thư mục phông chữ riêng trên máy chủ.

### Bước 3: Tải tài liệu Word

Với các tùy chọn đã sẵn sàng, cuối cùng chúng ta **tải tài liệu word**. Đây là thời điểm Aspose phân tích DOCX và, nếu có phông chữ nào thiếu, callback của chúng ta sẽ được kích hoạt.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Điều gì xảy ra bên trong?**  
Aspose.Words đọc các phần XML của DOCX, giải quyết mỗi tham chiếu `<w:font>`, và kiểm tra bộ sưu tập phông chữ của hệ thống. Mỗi khi một tham chiếu không thể đáp ứng, nó sẽ thay thế bằng phông chữ dự phòng đầu tiên phù hợp và phát sinh cảnh báo `FontSubstitution`.

### Bước 4: Xác minh đầu ra

Chạy chương trình và quan sát console. Đối với mỗi phông chữ thiếu, bạn sẽ thấy một dòng như:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Nếu tài liệu không chứa phông chữ nào thiếu, console sẽ im lặng — có nghĩa là **cách phát hiện phông chữ** không trả về kết quả nào.

### Bước 5: Ví dụ Hoạt động Đầy đủ (Ứng dụng Console)

Dưới đây là một tệp `Program.cs` tự chứa mà bạn có thể đưa vào một dự án console mới. Nó bao gồm tất cả các phần chúng ta đã thảo luận cùng một trợ giúp nhỏ để giữ cửa sổ console mở khi gỡ lỗi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Đầu ra console dự kiến** (ví dụ):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Nếu bạn thay thế `MissingFont.docx` bằng một tệp chỉ sử dụng các phông chữ đã cài đặt, bạn sẽ chỉ thấy dòng “Press any key…” — xác nhận rằng logic phát hiện hoạt động như mong đợi.

---

## Câu hỏi Thường gặp & Trường hợp Đặc biệt

### Nếu tôi cần ghi lại *tất cả* cảnh báo, không chỉ thay thế phông chữ thì sao?

Chỉ cần loại bỏ điều kiện `if (info.Type == WarningType.FontSubstitution)`. Đối tượng `WarningInfo` chứa một enum `Type` mà bạn có thể chuyển đổi cho các kịch bản khác (ví dụ, `DocumentStructure`, `ImageLoading`).

### Tôi có thể ghi cảnh báo vào tệp thay vì console không?

Chắc chắn. Thay thế `Console.WriteLine` bằng bất kỳ lời gọi khung ghi log nào (`Serilog`, `NLog`, v.v.). Callback chạy trên cùng một luồng tải tài liệu, vì vậy hãy đảm bảo logger của bạn an toàn với đa luồng.

### Điều này hoạt động như thế nào trong ứng dụng web?

Trong ASP.NET Core, bạn thường sẽ tiêm một triển khai `IWarningCallback` singleton và truyền nó qua `LoadOptions`. Hãy nhớ tránh ghi trực tiếp vào luồng phản hồi — ghi log vào cơ sở dữ liệu hoặc một bộ sưu tập trong bộ nhớ mà sau này bạn có thể cung cấp qua một endpoint API.

### Còn phông chữ tùy chỉnh lưu trong thư mục không phải hệ thống thì sao?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Bây giờ Aspose.Words sẽ tìm kiếm `C:\MyCustomFonts` trước khi quay lại các phông chữ của hệ điều hành, giảm số lượng cảnh báo thay thế mà bạn thấy.

## Tóm tắt Trực quan

![Phát hiện cảnh báo callback phông chữ trong Aspose.Words](/images/font-warning-callback.png "Cách phát hiện phông chữ bằng callback cảnh báo")

*Ảnh chụp màn hình hiển thị đầu ra console khi một phông chữ bị thiếu được thay thế. Văn bản thay thế (alt text) chứa từ khóa chính cho SEO.*

## Kết luận

Bây giờ bạn đã có một mẫu mẫu vững chắc, sẵn sàng cho môi trường sản xuất để **cách phát hiện phông chữ** trong bất kỳ tệp Word nào bạn tải bằng Aspose.Words. Bằng **cách thiết lập callback**, bạn có được cái nhìn thời gian thực về các phông chữ bị thiếu hoặc được thay thế, và bạn đã học cách **tải tài liệu word** đúng cách trong khi giữ mã nguồn sạch sẽ và dễ bảo trì.

Bước tiếp theo? Hãy thử mở rộng callback để thu thập các cảnh báo vào một danh sách, sau đó hiển thị chúng trong giao diện người dùng hoặc báo cáo tự động. Bạn cũng có thể khám phá `FontSettings.SubstitutionSettings` để kiểm soát *phông chữ nào* sẽ được chọn làm dự phòng.

Hãy thoải mái thử nghiệm — thay đổi tài liệu, thêm nhiều phông chữ thiếu, hoặc tích hợp logic vào một pipeline xử lý tài liệu lớn hơn. Nếu bạn gặp bất kỳ vấn đề nào, hãy để lại bình luận bên dưới hoặc nhắn tin cho tôi trên GitHub.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn hiển thị đúng phông chữ mà bạn mong muốn!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}