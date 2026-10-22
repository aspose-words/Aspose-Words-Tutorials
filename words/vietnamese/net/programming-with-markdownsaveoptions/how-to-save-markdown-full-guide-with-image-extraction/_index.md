---
category: general
date: 2026-03-30
description: Cách lưu tệp markdown trong C# đồng thời trích xuất hình ảnh từ markdown
  và lưu tài liệu dưới dạng markdown bằng Aspose.Words.
draft: false
keywords:
- how to save markdown
- extract images from markdown
- save document as markdown
- markdown resource handling
- C# markdown export
language: vi
og_description: Cách lưu markdown nhanh chóng. Tìm hiểu cách trích xuất hình ảnh từ
  markdown và lưu tài liệu dưới dạng markdown với ví dụ mã đầy đủ.
og_title: Cách Lưu Markdown – Hướng Dẫn Toàn Diện C#
tags:
- C#
- Markdown
- Aspose.Words
title: Cách Lưu Markdown – Hướng Dẫn Toàn Diện Kèm Trích Xuất Hình Ảnh
url: /vi/net/programming-with-markdownsaveoptions/how-to-save-markdown-full-guide-with-image-extraction/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Lưu Markdown – Hướng Dẫn Đầy Đủ C#

Bạn đã bao giờ tự hỏi **cách lưu markdown** mà vẫn giữ nguyên tất cả các hình ảnh được nhúng chưa? Bạn không phải là người duy nhất. Nhiều nhà phát triển gặp khó khăn khi thư viện của họ lưu hình ảnh vào một thư mục ngẫu nhiên hoặc, tệ hơn, không lưu chúng cả. Tin tốt là gì? Chỉ với vài dòng C# và Aspose.Words, bạn có thể xuất tài liệu thành markdown, trích xuất mọi hình ảnh và kiểm soát chính xác nơi mỗi tệp được lưu.

Trong hướng dẫn này, chúng ta sẽ đi qua một kịch bản thực tế: lấy một đối tượng `Document`, cấu hình `MarkdownSaveOptions`, và chỉ định cho bộ lưu nơi sẽ đặt mỗi hình ảnh. Khi hoàn thành, bạn sẽ có thể **lưu tài liệu dưới dạng markdown**, **trích xuất hình ảnh từ markdown**, và có một cấu trúc thư mục gọn gàng sẵn sàng cho việc xuất bản. Không có những tham chiếu mơ hồ—chỉ có một ví dụ hoàn chỉnh, có thể chạy ngay.

## Những Gì Bạn Cần Chuẩn Bị

- **.NET 6+** (bất kỳ SDK mới nào cũng được)
- **Aspose.Words for .NET** (gói NuGet `Aspose.Words`)
- Kiến thức cơ bản về cú pháp C# (chúng tôi sẽ giữ cho nó đơn giản)
- Một thể hiện `Document` hiện có (chúng tôi sẽ tạo một cái cho mục đích demo)

Nếu bạn đã có những thứ trên, hãy bắt đầu.

## Bước 1: Thiết Lập Dự Án và Nhập Các Namespace

Đầu tiên, tạo một ứng dụng console mới (hoặc tích hợp vào giải pháp hiện có). Sau đó thêm gói Aspose.Words:

```bash
dotnet add package Aspose.Words
```

Bây giờ nhập các namespace cần thiết:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

> **Mẹo chuyên nghiệp:** Giữ các câu lệnh `using` ở đầu file; điều này giúp mã dễ đọc hơn cho cả con người và các trình phân tích AI.

## Bước 2: Tạo Tài Liệu Mẫu (hoặc tải tài liệu của bạn)

Để minh họa, chúng ta sẽ tạo một tài liệu nhỏ chứa một đoạn văn và một hình ảnh được nhúng. Thay đoạn này bằng `Document.Load("YourFile.docx")` nếu bạn đã có file nguồn.

```csharp
// Step 2: Build a simple document with an image
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Add some text
builder.Writeln("Hello, Markdown world!");

// Insert an image from disk (make sure the path exists)
string imagePath = @"YOUR_DIRECTORY/sample-image.png";
builder.InsertImage(imagePath);
```

> **Tại sao điều này quan trọng:** Nếu bạn bỏ qua hình ảnh, sẽ không có gì để *trích xuất* sau này, và bạn sẽ không thấy callback hoạt động.

## Bước 3: Cấu Hình MarkdownSaveOptions với Callback Lưu Tài Nguyên

Đây là phần cốt lõi của giải pháp. `ResourceSavingCallback` sẽ được kích hoạt cho **mọi** tài nguyên bên ngoài—hình ảnh, phông chữ, CSS, v.v. Chúng ta sẽ dùng nó để tạo một thư mục con `Resources` riêng và đặt tên duy nhất cho mỗi tệp.

```csharp
// Step 3: Define markdown save options and attach a callback
var markdownSaveOptions = new MarkdownSaveOptions
{
    // This delegate runs for each resource the saver wants to write out
    ResourceSavingCallback = (sender, args) =>
    {
        // Ensure the Resources folder exists (creates it only once)
        string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
        Directory.CreateDirectory(resourcesFolder);

        // Build a unique filename: img_0.png, img_1.jpg, etc.
        string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";

        // Tell the saver where to place the file
        args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
    }
};
```

**Điều gì đang xảy ra?**  
- `args.Index` là bộ đếm bắt đầu từ 0, đảm bảo tính duy nhất.  
- `Path.GetExtension(args.FileName)` giữ nguyên loại tệp gốc (PNG, JPG, v.v.).  
- Bằng cách đặt `args.SavePath`, chúng ta ghi đè vị trí mặc định và giữ mọi thứ gọn gàng.

## Bước 4: Lưu Tài Liệu Dưới Dạng Markdown

Với các tùy chọn đã được thiết lập, việc xuất chỉ cần một dòng:

```csharp
// Step 4: Export to markdown using the configured options
string outputMarkdown = @"YOUR_DIRECTORY/Doc.md";
doc.Save(outputMarkdown, markdownSaveOptions);
```

Sau khi chạy, bạn sẽ thấy:

- `Doc.md` chứa văn bản markdown có tham chiếu đến các hình ảnh.  
- Một thư mục `Resources` bên cạnh nó chứa `img_0.png`, `img_1.jpg`, …  

Đó là quy trình **cách lưu markdown**, hoàn chỉnh với việc trích xuất tài nguyên.

## Bước 5: Kiểm Tra Kết Quả (Tùy Chọn nhưng Được Khuyến Khích)

Mở `Doc.md` bằng bất kỳ trình soạn thảo văn bản nào. Bạn sẽ thấy nội dung tương tự:

```markdown
Hello, Markdown world!

![image](Resources/img_0.png)
```

Và thư mục `Resources` sẽ chứa hình ảnh gốc mà bạn đã chèn. Nếu bạn mở file markdown trong một trình xem (ví dụ: VS Code, GitHub), hình ảnh sẽ hiển thị đúng.

> **Câu hỏi thường gặp:** *Nếu tôi muốn các hình ảnh nằm trong cùng thư mục với file markdown thì sao?*  
> Chỉ cần thay đổi `resourcesFolder` thành `Path.GetDirectoryName(outputMarkdown)` và điều chỉnh đường dẫn hình ảnh trong markdown cho phù hợp.

## Trích Xuất Hình Ảnh Từ Markdown – Các Điều Chỉnh Nâng Cao

Đôi khi bạn cần kiểm soát nhiều hơn về quy tắc đặt tên hoặc muốn bỏ qua một số loại tài nguyên nhất định. Dưới đây là một vài biến thể hữu ích.

### 5.1 Bỏ Qua Các Tài Nguyên Không Phải Hình Ảnh

```csharp
ResourceSavingCallback = (sender, args) =>
{
    // Only process images; ignore CSS, fonts, etc.
    if (!args.ContentType.StartsWith("image/", StringComparison.OrdinalIgnoreCase))
        return; // Let the default handling continue

    // ...same folder creation logic as before...
};
```

### 5.2 Giữ Nguyên Tên Tệp Gốc

Nếu bạn muốn giữ tên tệp gốc thay vì `img_0`, chỉ cần bỏ phần `args.Index`:

```csharp
string resourceFileName = args.FileName; // uses the name from the source document
```

### 5.3 Sử Dụng Thư Mục Con Tùy Chỉnh Cho Mỗi Tài Liệu

```csharp
string docName = Path.GetFileNameWithoutExtension(outputMarkdown);
string resourcesFolder = $@"YOUR_DIRECTORY/{docName}_Resources/";
Directory.CreateDirectory(resourcesFolder);
```

Các đoạn mã này minh họa **trích xuất hình ảnh từ markdown** một cách linh hoạt, phù hợp với các quy ước dự án khác nhau.

## Câu Hỏi Thường Gặp (FAQ)

| Câu hỏi | Trả lời |
|----------|--------|
| **Có hoạt động với .NET Core không?** | Hoàn toàn có—Aspose.Words đa nền tảng, vì vậy cùng một đoạn mã chạy trên Windows, Linux hoặc macOS. |
| **Còn các hình ảnh SVG thì sao?** | SVG được coi là hình ảnh; callback sẽ nhận phần mở rộng `.svg`. Hãy chắc chắn trình xem markdown của bạn hỗ trợ SVG. |
| **Có thể thay đổi cú pháp markdown (ví dụ: dùng thẻ HTML `<img>`)?** | Đặt `markdownSaveOptions.ExportImagesAsBase64 = false` và điều chỉnh `ExportImagesAsHtml` nếu bạn cần thẻ HTML thuần. |
| **Có cách để xử lý hàng loạt nhiều tài liệu không?** | Đặt logic trên trong một vòng `foreach` duyệt qua tập hợp file—chỉ cần nhớ tạo thư mục tài nguyên riêng cho mỗi tài liệu. |

## Ví Dụ Hoàn Chỉnh (Sẵn Sàng Sao Chép‑Dán)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a document and add an image
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, Markdown world!");
        string imagePath = @"YOUR_DIRECTORY/sample-image.png"; // <-- change this
        builder.InsertImage(imagePath);

        // 2️⃣ Configure save options with a callback to extract images
        var markdownSaveOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (sender, args) =>
            {
                string resourcesFolder = @"YOUR_DIRECTORY/Resources/";
                Directory.CreateDirectory(resourcesFolder);

                string resourceFileName = $"img_{args.Index}{Path.GetExtension(args.FileName)}";
                args.SavePath = Path.Combine(resourcesFolder, resourceFileName);
            }
        };

        // 3️⃣ Save as markdown
        string outputPath = @"YOUR_DIRECTORY/Doc.md";
        doc.Save(outputPath, markdownSaveOptions);

        Console.WriteLine("Markdown saved successfully!");
        Console.WriteLine($"Check {outputPath} and the Resources folder for images.");
    }
}
```

Chạy chương trình (`dotnet run`) và bạn sẽ thấy các thông báo console xác nhận thành công. Tất cả hình ảnh giờ đã được lưu gọn gàng, và file markdown trỏ đúng tới chúng.

## Kết Luận

Bạn vừa học được **cách lưu markdown** đồng thời **trích xuất hình ảnh từ markdown** và đảm bảo tài liệu có thể **được lưu dưới dạng markdown** với kiểm soát hoàn toàn vị trí tài nguyên. Điểm mấu chốt là `ResourceSavingCallback`—nó cho phép bạn quản lý chi tiết từng tệp ngoại vi mà bộ xuất tạo ra.

Từ đây, bạn có thể:

- Tích hợp quy trình này vào một dịch vụ web chuyển đổi file DOCX do người dùng tải lên thành markdown ngay lập tức.  
- Mở rộng callback để đổi tên tệp dựa trên quy tắc đặt tên phù hợp với CMS của bạn.  
- Kết hợp với các tính năng khác của Aspose.Words như `ExportImagesAsBase64` để có markdown nhúng hình ảnh dưới dạng base64.

Hãy thử nghiệm, điều chỉnh logic thư mục cho dự án của bạn, và để kết quả markdown tỏa sáng trong quy trình tài liệu của bạn.

--- 

![cách lưu markdown ví dụ](/assets/how-to-save-markdown.png "cách lưu markdown ví dụ")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}