---
category: general
date: 2026-02-10
description: Thiết lập callback cảnh báo để giám sát các thay đổi phông chữ khi bạn
  cấu hình phông chữ mặc định và đặt phông chữ nhập mặc định trong Aspose.Words. Tìm
  hiểu giải pháp chi tiết từng bước.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: vi
og_description: Đặt callback cảnh báo để giám sát các thay đổi phông chữ khi cấu hình
  phông chữ mặc định và thiết lập phông chữ nhập mặc định. Tham khảo hướng dẫn đầy
  đủ cho Aspose.Words.
og_title: Thiết lập callback cảnh báo trong C# – Hướng dẫn chi tiết
tags:
- Aspose.Words
- C#
- Document Import
title: Thiết lập callback cảnh báo trong C# – Hướng dẫn toàn diện về xử lý phông chữ
url: /vi/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Thiết lập callback cảnh báo trong C# – Hướng dẫn toàn diện về Xử lý Phông chữ

Bạn đã bao giờ cần **set warning callback** khi tải một tài liệu Word và tự hỏi làm thế nào để *configure default font* cùng lúc không? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế—như các công cụ tạo báo cáo tự động hoặc các pipeline chuyển đổi tài liệu—các phông chữ thiếu có thể làm hỏng bố cục một cách im lặng, và cách duy nhất để phát hiện những vấn đề này là **monitor font changes** thông qua một warning callback.

Trong tutorial này chúng ta sẽ đi qua một ví dụ thực hành cho thấy cách **set warning callback**, **configure default font**, và thậm chí **set default import font** bằng Aspose.Words for .NET. Khi kết thúc, bạn sẽ có một đoạn mã sẵn sàng chạy, hiểu tại sao mỗi phần lại quan trọng, và biết cách điều chỉnh cho các trường hợp đặc biệt như thư mục phông chữ tùy chỉnh hoặc các thay thế im lặng.

---

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng chạy trên .NET Framework 4.6+)  
- Gói NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Một thư mục chứa phông chữ dự phòng bạn muốn sử dụng (ví dụ: `fonts/Arial.ttf`)  
- Kiến thức cơ bản về ứng dụng console C#  

Không cần thư viện bổ sung nào khác.

---

## Bước 1: Tạo LoadOptions và **configure default font**

Điều đầu tiên bạn làm khi muốn kiểm soát việc xử lý phông chữ là tạo một thể hiện `LoadOptions`. Đối tượng này cho Aspose.Words biết cách xử lý các phông chữ thiếu trong quá trình nhập.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Tại sao điều này quan trọng:**  
Nếu tài liệu nguồn tham chiếu một phông chữ không được cài đặt trên máy chủ, Aspose.Words sẽ tìm trong thư mục bạn cung cấp. Đây là cốt lõi của **set default import font**—bạn đang chỉ rõ cho thư viện nơi tìm kiếm thay thế trước khi bất kỳ cảnh báo nào được đưa ra.

---

## Bước 2: **Set warning callback** để **monitor font changes**

Aspose.Words phát ra một `WarningInfoCollection` mỗi khi nó phải thay thế phông chữ, cùng với các thông tin khác. Bằng cách gắn một handler, bạn có thể ghi lại hoặc phản hồi với mỗi lần thay thế.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Tại sao điều này quan trọng:**  
Chỉ **configure default font** không đủ nếu bạn cần kiểm tra những phông chữ nào thực sự đã bị thay thế. Callback cung cấp một bản ghi thời gian thực, đáp ứng yêu cầu **monitor font changes** và giúp bạn phát hiện các thay thế không mong muốn ngay trong pipeline CI.

---

## Bước 3: Tải tài liệu với các tùy chọn đã chuẩn bị

Khi các tùy chọn tải đã được cấu hình đầy đủ, bạn có thể an toàn tải bất kỳ tệp `.docx` nào. Callback sẽ tự động kích hoạt nếu có sự thay thế.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Bạn sẽ thấy:**  
Nếu nguồn sử dụng một phông chữ không có, console sẽ in ra một thông báo giống như:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Kết quả này xác nhận rằng bạn đã **set warning callback** thành công và **default import font** đã có hiệu lực.

---

## Bước 4: (Tùy chọn) Tinh chỉnh hành vi thay thế phông chữ

Đôi khi bạn muốn thay thế *tất cả* các phông chữ thiếu bằng một họ duy nhất, bất kể yêu cầu gốc. Aspose.Words cho phép bạn đặt một *fallback font* toàn cục.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Khi nào nên sử dụng:**  
Nếu bạn đang tạo PDF cho một thương hiệu chỉ cho phép một bộ phông chữ hạn chế, cách này sẽ đảm bảo tính nhất quán trên mọi tài liệu, ngay cả khi nguồn cố gắng sử dụng phông chữ lạ.

---

## Bước 5: Lưu hoặc tiếp tục xử lý tài liệu

Sau khi tải, bạn có thể tiếp tục với bất kỳ xử lý nào cần—chỉnh sửa, chuyển đổi sang PDF, trích xuất văn bản, v.v. Dưới đây là một ví dụ nhanh về việc lưu tài liệu dưới dạng PDF trong khi giữ nguyên các phông chữ đã được thay thế.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

PDF kết quả sẽ hiển thị phông chữ dự phòng ở mọi vị trí đã có sự thay thế, cung cấp bằng chứng trực quan rằng **set warning callback** đã hoạt động như mong đợi.

---

## Các lỗi thường gặp & Mẹo chuyên nghiệp

| Vấn đề | Nguyên nhân | Cách khắc phục |
|--------|-------------|----------------|
| **Callback never fires** | `LoadOptions.WarningCallback` chưa được gán *trước* khi tải tài liệu. | Luôn gắn callback **trước** khi gọi `new Document(...)`. |
| **Wrong font folder** | Đường dẫn sai hoặc thiếu quyền đọc. | Kiểm tra thư mục tồn tại và ứng dụng có quyền `Read`. Sử dụng đường dẫn tuyệt đối để đảm bảo độ tin cậy. |
| **Multiple substitutions, noisy output** | Tài liệu lớn với nhiều phông chữ thiếu. | Lọc cảnh báo bằng `WarningType.FontSubstitution` (như trong ví dụ) hoặc ghi chúng vào file log thay vì console. |
| **Fallback font not applied** | Phông chữ dự phòng không được cài đặt trên máy. | Đặt file `.ttf`/`.otf` vào thư mục bạn truyền cho `SetFontsFolder`. Aspose.Words sẽ tải trực tiếp, không cần cài đặt trên hệ điều hành. |

**Mẹo chuyên nghiệp:** Khi chạy trong pipeline CI/CD, chuyển hướng đầu ra console tới một artifact build. Như vậy bạn sẽ có một bản ghi audit cho mọi lần thay thế phông chữ xảy ra trong quá trình build.

---

## Ví dụ hoàn chỉnh (Sẵn sàng sao chép)

Dưới đây là chương trình đầy đủ bạn có thể đưa vào một dự án Console App mới. Nó bao gồm tất cả các bước, các câu lệnh `using`, và chú thích cần thiết.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Kết quả đầu ra console dự kiến** (giả sử `Times New Roman` bị thiếu):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Chạy chương trình, mở `output.pdf`, và bạn sẽ thấy tài liệu được hiển thị với phông chữ dự phòng ở mọi nơi cần thiết.

---

## Kết luận

Bạn đã có một mẫu mẫu production‑ready để **set warning callback** trong C#, **configure default font**, **monitor font changes**, và **set default import font** khi làm việc với Aspose.Words. Bằng cách gắn một bộ thu thập cảnh báo trước khi tải, chỉ định `FontSettings` tới một thư mục phông chữ tin cậy, và tùy chọn buộc một fallback toàn cục, bạn sẽ có toàn quyền kiểm soát và quan sát việc thay thế phông chữ—điều mà bất kỳ pipeline xử lý tài liệu mạnh mẽ nào cũng cần.

Sẵn sàng cho cấp độ tiếp theo? Hãy thử kết hợp cách này với:

- **Dynamic font loading** từ cơ sở dữ liệu (sử dụng `FontSettings.SetFontsFolder` tại thời gian chạy).  
- **Custom warning handlers** ghi vào log có cấu trúc (JSON hoặc CSV) để phân tích.  
- **Parallel document processing** nơi mỗi luồng có `LoadOptions` riêng để tránh xung đột.

Hãy thoải mái thử nghiệm, điều chỉnh mã cho kiến trúc của bạn, và chia sẻ bất kỳ khám phá nào trong phần bình luận. Chúc lập trình vui vẻ!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}