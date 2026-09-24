---
category: general
date: 2026-01-03
description: Chuyển đổi Word sang Markdown và nhúng hình ảnh dưới dạng base64 trong
  một lần. Tìm hiểu cách lưu Word dưới dạng markdown, tạo markdown từ Word và sử dụng
  dữ liệu hình ảnh base64 dạng URI.
draft: false
keywords:
- convert word to markdown
- embed images as base64
- save word as markdown
- base64 image data uri
- generate markdown from word
language: vi
og_description: Chuyển đổi Word sang Markdown và nhúng hình ảnh dưới dạng base64 data
  URI. Hướng dẫn từng bước này cho thấy cách lưu Word dưới dạng markdown và tạo markdown
  từ Word.
og_title: Chuyển đổi Word sang Markdown – Hướng dẫn nhúng hình ảnh Base64
tags:
- Aspose.Words
- C#
- Markdown
title: Chuyển đổi Word sang Markdown – Nhúng hình ảnh dưới dạng Base64
url: /vi/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chuyển Word sang Markdown – Nhúng Hình ảnh dưới dạng Base64

Bạn đã bao giờ cần **chuyển Word sang markdown** nhưng luôn gặp rắc rối với hình ảnh? Bạn không phải là người duy nhất. Word thích lưu ảnh dưới dạng các tệp riêng biệt, trong khi markdown ưa chuộng những chuỗi `data:image/...;base64,` nhỏ gọn giúp mọi thứ gọn gàng trong một tệp duy nhất.  

Trong hướng dẫn này, chúng ta sẽ đi qua một giải pháp hoàn chỉnh, sẵn sàng chạy, giúp **lưu Word dưới dạng markdown**, **nhúng hình ảnh dưới dạng base64**, và thậm chí chỉ cho bạn cách **tạo markdown từ Word** bằng Aspose.Words cho .NET. Khi kết thúc, bạn sẽ có một tệp `.md` duy nhất hiển thị chính xác như tài liệu gốc—không cần thư mục ảnh bên ngoài.

## Những gì bạn cần

- **.NET 6.0 trở lên** (bất kỳ gì có thể tham chiếu tới gói NuGet)
- **Aspose.Words cho .NET** (bản dùng thử miễn phí hoạt động tốt cho việc thử nghiệm)
- Một tệp `.docx` đơn giản có vài hình ảnh (chúng ta sẽ gọi nó là `input.docx`)
- IDE yêu thích của bạn (Visual Studio, Rider, VS Code—chọn bất kỳ cái nào bạn thích)

Nếu bạn đã có những thứ này, tuyệt—hãy bắt đầu. Nếu chưa, cài đặt gói NuGet chỉ cần một dòng:

```bash
dotnet add package Aspose.Words
```

## Bước 1: Tải tài liệu Word — điểm khởi đầu cho **convert word to markdown**

Đầu tiên chúng ta cần đưa tệp `.docx` vào bộ nhớ. Đây là nơi phép màu chuyển đổi bắt đầu.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the Word file that contains the images.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

> **Tại sao điều này quan trọng:**  
> Việc tải tài liệu cho phép Aspose truy cập đầy đủ vào văn bản, kiểu dáng và mọi tài nguyên được nhúng. Nếu bỏ qua bước này, sẽ không có gì để chuyển đổi.

## Bước 2: Cấu hình MarkdownSaveOptions với Callback lưu tài nguyên

Aspose cho phép bạn chặn mọi tài nguyên (như hình ảnh) mà thường sẽ được ghi ra đĩa. Bằng cách cung cấp một `IResourceSavingCallback` tùy chỉnh, chúng ta có thể thay thế việc lưu dựa trên tệp mặc định bằng một **URI dữ liệu hình ảnh base64**.

```csharp
// Configure Markdown save options so that images become Base64 URIs.
MarkdownSaveOptions markdownSaveOptions = new MarkdownSaveOptions
{
    ResourceSavingCallback = new MyResourceHandler()
};
```

### Trình xử lý tùy chỉnh – Chuyển hình ảnh thành Base64

Dưới đây là triển khai đầy đủ. Lưu ý cách chúng ta kiểm tra `args.ResourceType == ResourceType.Image` và sau đó:

1. Ghi hình ảnh vào một `MemoryStream`.
2. Chuyển mảng byte thành chuỗi Base64.
3. Tạo một URI `data:image/jpeg;base64,` và gán nó cho `args.Uri`.

```csharp
// Custom handler that converts each image resource to a Base64 data URI.
class MyResourceHandler : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Only process images – leave other resources untouched.
        if (args.ResourceType == ResourceType.Image)
        {
            // Prepare an in‑memory stream for the image.
            using (MemoryStream ms = new MemoryStream())
            {
                // Save the image using default JPEG options.
                args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                // Build the Base64 data URI.
                string base64 = Convert.ToBase64String(ms.ToArray());
                args.Uri = $"data:image/jpeg;base64,{base64}";
                // No need to keep the stream open after we set the URI.
                args.KeepResourceStreamOpen = false;
            }
        }
    }
}
```

> **Mẹo chuyên nghiệp:** Nếu tài liệu Word nguồn của bạn sử dụng PNG, hãy thay `ImageSaveOptions.DefaultJpeg` bằng `ImageSaveOptions.DefaultPng` và thay đổi loại MIME cho phù hợp (`image/png`).

## Bước 3: Lưu tài liệu dưới dạng Markdown – bước **save word as markdown** cuối cùng

Bây giờ callback đã sẵn sàng, việc lưu thực tế chỉ cần một dòng lệnh.

```csharp
// Save the document to a Markdown file. Images are already embedded.
document.Save("YOUR_DIRECTORY/output.md", markdownSaveOptions);
```

Khi bạn mở `output.md` trong bất kỳ trình xem markdown nào (xem trước VS Code, GitHub, v.v.), bạn sẽ thấy văn bản giống hệt như trong tệp Word gốc, và các hình ảnh sẽ xuất hiện nội tuyến mà không cần tệp ảnh riêng.

## Kết quả mong đợi

```markdown
# Sample Title

Here’s a paragraph that originally lived in Word.

![Embedded Image](data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhU...
```

Dòng `![Embedded Image]` là một **URI dữ liệu hình ảnh base64**—toàn bộ hình ảnh được mã hoá ngay tại đó. Không có thư mục phụ, không có liên kết hỏng.

## Các trường hợp đặc biệt & Cách xử lý

| Tình huống | Cách xử lý |
|-----------|------------|
| **Hình ảnh lớn** – Base64 làm tăng kích thước khoảng ~33% | Xem xét thay đổi kích thước trước khi chuyển đổi: `args.ResourceData.Save(ms, new ImageSaveOptions { ImageResolution = 72 })`. |
| **Hình ảnh không phải JPEG** (PNG, GIF) | Phát hiện định dạng gốc qua `args.ResourceData.ImageType` và đặt MIME type đúng (`image/png`, `image/gif`). |
| **Tài liệu rất dài** (hàng trăm hình ảnh) | Giám sát việc sử dụng bộ nhớ; bạn có thể stream mỗi hình ảnh ra đĩa tạm thời nếu quá trình hết RAM. |
| **Cần tách riêng các tệp ảnh** (ví dụ, cho site tĩnh) | Trả về `false` từ callback đối với các ảnh muốn giữ dưới dạng tệp, và để Aspose ghi chúng vào thư mục. |

## Câu hỏi thường gặp (Được trả lời ngay từ đầu)

- **Liệu điều này có hoạt động với tệp .doc không?** Có—Aspose.Words có thể tải các tệp `.doc` cũ theo cùng cách bạn tải `.docx`. Chỉ cần trỏ `new Document("myfile.doc")` tới nó.
- **Còn các bảng và chú thích thì sao?** Chúng được hỗ trợ đầy đủ bởi bộ xuất Markdown. Bảng sẽ trở thành bảng markdown; chú thích sẽ trở thành tham chiếu nội tuyến.
- **Tôi có thể thay đổi kiểu markdown không?** `MarkdownSaveOptions` có thuộc tính `MarkdownVersion` (CommonMark, GitHub, v.v.). Đặt nó trước khi lưu nếu bạn cần một cú pháp cụ thể.

## Mẫu đầy đủ, sẵn sàng chạy

Dưới đây là chương trình hoàn chỉnh bạn có thể sao chép‑dán vào một ứng dụng console. Nó bao gồm tất cả các câu lệnh using, lớp handler và xử lý lỗi.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToMarkdownDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                // 1️⃣ Load the source Word document.
                Document doc = new Document("YOUR_DIRECTORY/input.docx");

                // 2️⃣ Prepare Markdown options with our custom image handler.
                MarkdownSaveOptions options = new MarkdownSaveOptions
                {
                    ResourceSavingCallback = new MyResourceHandler()
                };

                // 3️⃣ Save as Markdown – images become Base64 URIs.
                string outputPath = "YOUR_DIRECTORY/output.md";
                doc.Save(outputPath, options);

                Console.WriteLine($"✅ Success! Markdown saved to {outputPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Conversion failed: {ex.Message}");
            }
        }
    }

    // Custom callback that embeds images as Base64 data URIs.
    class MyResourceHandler : IResourceSavingCallback
    {
        public void ResourceSaving(ResourceSavingArgs args)
        {
            if (args.ResourceType == ResourceType.Image)
            {
                using (MemoryStream ms = new MemoryStream())
                {
                    // Preserve original format if you prefer PNG/GIF.
                    args.ResourceData.Save(ms, ImageSaveOptions.DefaultJpeg);
                    string base64 = Convert.ToBase64String(ms.ToArray());
                    args.Uri = $"data:image/jpeg;base64,{base64}";
                    args.KeepResourceStreamOpen = false;
                }
            }
        }
    }
}
```

Chạy chương trình, mở `output.md` đã tạo, và bạn sẽ thấy một bản sao markdown hoàn hảo của tệp Word—**convert word to markdown** chưa bao giờ dễ dàng hơn.

## Tóm tắt

Chúng ta bắt đầu với vấn đề **convert word to markdown** đồng thời giữ hình ảnh nội tuyến. Bằng cách tải tài liệu, cấu hình callback `MarkdownSaveOptions`, và lưu tệp, chúng ta đã đạt được giải pháp **save word as markdown** sạch sẽ, tạo ra các chuỗi **base64 image data uri**. Bây giờ bạn cũng đã biết cách **nhúng hình ảnh dưới dạng base64**, xử lý các trường hợp đặc biệt, và tinh chỉnh quy trình cho các loại hình ảnh khác nhau.

## Bước tiếp theo?

- **Tạo HTML thay vì markdown** – thay `MarkdownSaveOptions` bằng `HtmlSaveOptions` và tái sử dụng cùng callback.
- **Chuyển đổi hàng loạt nhiều tệp** – bao bọc logic trong một vòng lặp `foreach` qua một thư mục.
- **Tích hợp vào pipeline CI** – tự động tạo tài liệu cho các site tĩnh.

Bạn có thể thoải mái thử nghiệm, điều chỉnh chất lượng hình ảnh, hoặc thậm chí thêm xử lý tài nguyên tùy chỉnh của riêng mình (ví dụ, tải ảnh lên CDN và chèn URL). Không gì là không thể khi bạn kết hợp Aspose.Words với một chút sáng tạo C#.

Chúc lập trình vui vẻ, và hy vọng markdown của bạn luôn hiển thị hoàn hảo! 

![Sơ đồ mô tả luồng chuyển Word sang markdown – nhúng hình ảnh dưới dạng base64](data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iNjAwIiBoZWlnaHQ9IjQwMCIgdmlld0JveD0iMCAwIDYwMCA0MDAiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyI+PHJlY3Qgd2lkdGg9IjYwMCIgaGVpZ2h0PSI0MDAiIGZpbGw9IiNmZmYiIHN0cm9rZT0iI2NjYyIgLz48dGV4dCB4PSI1MCIgeT0iMjAwIiBmb250LXNpemU9IjM2IiBmaWxsPSIjMDAwIj5JbWFnZSBJbWFnZSBJbWFnZSBJbWFnZTwvdGV4dD48L3N2Zz4= "convert word to markdown flow diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}