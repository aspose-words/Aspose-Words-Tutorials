---
category: general
date: 2026-02-20
description: Học cách lưu hình ảnh từ Word và chuyển đổi Word sang markdown trong
  C#. Hướng dẫn từng bước này cũng chỉ cách trích xuất hình ảnh từ Word và xuất markdown
  kèm hình ảnh.
draft: false
keywords:
- save word images
- convert word to markdown
- extract images from word
- convert docx to md
- export markdown with images
language: vi
og_description: Trong hướng dẫn này, chúng tôi sẽ chỉ cho bạn cách lưu hình ảnh Word
  và chuyển đổi Word sang markdown bằng Aspose.Words. Hãy làm theo các bước để xuất
  markdown kèm hình ảnh.
og_title: Lưu hình ảnh Word khi chuyển đổi Word sang Markdown – Hướng dẫn C# đầy đủ
tags:
- Aspose.Words
- C#
- Markdown
title: Lưu hình ảnh Word khi chuyển đổi Word sang Markdown – Hướng dẫn C# đầy đủ
url: /vi/net/programming-with-markdownsaveoptions/save-word-images-while-converting-word-to-markdown-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# lưu hình ảnh word khi chuyển đổi Word sang Markdown – Hướng dẫn C# đầy đủ

Bạn đã bao giờ cần **save word images** khi chuyển đổi tài liệu Word sang Markdown chưa? Bạn không phải là người duy nhất—các nhà phát triển thường gặp vấn đề hình ảnh biến mất sau một lệnh đơn giản `convert docx to md`. Trong hướng dẫn này, chúng ta sẽ đi qua một cách sạch sẽ, sẵn sàng cho sản xuất để **save word images**, **convert word to markdown**, và có được một tệp Markdown vẫn hiển thị mọi hình ảnh.

Hãy tưởng tượng bạn có một hướng dẫn sử dụng trong `input.docx` và muốn xuất bản nó trên một trang tĩnh. Bạn cần văn bản ở dạng Markdown, nhưng cũng cần các ảnh chụp màn hình, sơ đồ và logo xuất hiện đúng vị trí của chúng. Đó là vấn đề chúng ta sẽ giải quyết—không cần công cụ bên ngoài, không cần sao chép‑dán thủ công, chỉ vài dòng C# và Aspose.Words.

Kết thúc hướng dẫn này, bạn sẽ có thể:

* Tải một tệp `.docx` bằng Aspose.Words.  
* Cấu hình `MarkdownSaveOptions` để quá trình chuyển đổi cũng **extracts images from word**.  
* Triển khai một callback ghi mỗi hình ảnh vào một thư mục riêng với tên duy nhất.  
* Xác minh rằng tệp `.md` được tạo tham chiếu đúng các hình ảnh, tức là bạn đã thành công **exported markdown with images**.

> **Prerequisites** – Bạn sẽ cần .NET 6+ (hoặc .NET Framework 4.6+), một giấy phép Aspose.Words hợp lệ (hoặc dùng bản đánh giá miễn phí), và hiểu biết cơ bản về C#. Nếu bạn chưa từng dùng Aspose trước đây, đừng lo; API rất đơn giản và đoạn mã dưới đây hoàn toàn tự chứa.

---

## Cách lưu hình ảnh word khi chuyển đổi Word sang Markdown

Bước đầu tiên là **save word images** trong quá trình chuyển đổi. Aspose.Words cung cấp một `ResourceSavingCallback` được kích hoạt cho mỗi tài nguyên bên ngoài—hình ảnh, biểu đồ, SVG, bất kỳ gì bạn muốn. Bằng cách gắn triển khai của chúng tôi, chúng ta quyết định chính xác nơi mỗi hình ảnh sẽ được lưu trên đĩa.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Configure Markdown save options and attach a callback that will handle external resources
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image, letting us control the file name and folder
    ResourceSavingCallback = new MyResourceCallback()
};

// Save the document as Markdown; the callback will store images in a custom folder
document.Save("YOUR_DIRECTORY/output.md", markdownOptions);

// -----------------------------------------------------------------
// Callback implementation – stores each image in a dedicated folder with a unique name
class MyResourceCallback : IResourceSavingCallback
{
    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Define the folder where resources will be saved
        string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
        Directory.CreateDirectory(resourceFolder);

        // Generate a unique file name while preserving the original extension
        string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";

        // Tell Aspose.Words where to write the resource
        args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
    }
}
```

Đó là toàn bộ giải pháp—chạy nó và bạn sẽ có `output.md` cùng một thư mục `MarkdownResources` đầy các tệp hình ảnh. Markdown sẽ chứa các liên kết như `![](MarkdownResources/7f3c2a1e-...png)`, nghĩa là bạn đã thành công **save word images** và **export markdown with images** trong một lần.

---

## Cấu hình tùy chọn Markdown để chuyển đổi docx sang md

Tại sao phải dùng callback? Mặc định Aspose.Words sẽ nhúng hình ảnh dưới dạng chuỗi base‑64 trong Markdown, làm tăng kích thước tệp và làm rối việc kiểm soát phiên bản. Thiết lập `ResourceSavingCallback` cho thư viện **convert docx to md** *và* ghi mỗi hình ảnh ra đĩa thay vì nhúng trực tiếp.

### Các thuộc tính chính bạn có thể điều chỉnh

| Property | Giá trị điển hình | Khi nào cần thay đổi |
|----------|-------------------|----------------------|
| `ExportImagesAsBase64` | `false` (default) | Giữ hình ảnh dưới dạng các tệp riêng biệt. |
| `ImagesFolder` | `null` (ignored when callback is used) | Bạn có thể đặt một thư mục tĩnh nếu không cần đặt tên động. |
| `ExportHeadersFooters` | `true` | Bảo tồn nội dung header/footer có thể chứa hình ảnh. |
| `EncodeUrls` | `true` | Cần thiết nếu đường dẫn của bạn chứa dấu cách hoặc ký tự không phải ASCII. |

> **Pro tip:** Nếu bạn đang tạo tài liệu cho nhiều ngôn ngữ, hãy cân nhắc thêm mã ngôn ngữ vào `resourceFolder` (ví dụ, `MarkdownResources/en`) để các đường dẫn hình ảnh gọn gàng.

---

## Triển khai callback tài nguyên để extract images from word

Callback trong khối mã trước thực hiện phần việc nặng, nhưng hãy cùng phân tích một chút. `IResourceSavingCallback` nhận một đối tượng `ResourceSavingArgs` cho mỗi tài nguyên bên ngoài. Các trường quan trọng nhất là:

* `ResourceFileName` – đường dẫn nơi tệp sẽ được ghi.  
* `ResourceFileExtension` – phần mở rộng gốc (`.png`, `.jpg`, v.v.).  
* `ResourceType` – cho biết đó là hình ảnh, biểu đồ, hay loại khác.

Bạn có thể lọc các tài nguyên không phải hình ảnh nếu chỉ quan tâm đến ảnh:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    // Skip non‑image resources – we only want to save pictures
    if (args.ResourceType != ResourceType.Image)
        return;

    string resourceFolder = "YOUR_DIRECTORY/MarkdownResources";
    Directory.CreateDirectory(resourceFolder);

    string uniqueFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";
    args.ResourceFileName = Path.Combine(resourceFolder, uniqueFileName);
}
```

### Xử lý các trường hợp đặc biệt

1. **Duplicate images** – Nếu cùng một hình ảnh xuất hiện nhiều lần, callback vẫn sẽ ghi một tệp mới cho mỗi lần. Nếu bạn muốn loại bỏ trùng lặp, giữ một `Dictionary<string, string>` ánh xạ hàm băm của byte hình ảnh tới tên tệp đã tồn tại.  
2. **Unsupported formats** – Aspose.Words có thể xuất PNG, JPEG, GIF, BMP và TIFF. Nếu gặp định dạng lạ, bạn sẽ cần tự chuyển đổi (ví dụ, dùng `System.Drawing`).  
3. **Large documents** – Đối với các PDF hoặc DOCX khổng lồ, hãy cân nhắc stream đầu ra để tránh hết bộ nhớ. `MarkdownSaveOptions` hỗ trợ `SaveOptions.UseMemoryCache = false`.

---

## Lưu tài liệu và xác minh markdown đã xuất với hình ảnh

Sau khi chạy mã, mở `output.md` trong bất kỳ trình soạn thảo văn bản nào. Bạn sẽ thấy gì đó như:

```markdown
# Chapter 1

Here is a diagram:

![](MarkdownResources/2c7f9a3e-9b4d-4f6a-8d12-5e9f2c7a1b3c.png)

And another screenshot:

![](MarkdownResources/7a1d4e2f-3c9b-4a5d-9e8f-6b2c3d4e5f6a.jpg)
```

Nếu các liên kết hình ảnh đúng, mở tệp Markdown trong một trình xem (xem trước VS Code, GitHub, hoặc trình tạo site tĩnh). Các hình ảnh sẽ tự động hiển thị, xác nhận rằng bạn đã thành công **save word images** và **export markdown with images**.

### Kịch bản kiểm tra nhanh

Nếu bạn muốn tự động kiểm tra, đoạn mã dưới đây sẽ quét Markdown đã tạo để tìm các tệp bị thiếu:

```csharp
using System;
using System.IO;
using System.Text.RegularExpressions;

string mdPath = "YOUR_DIRECTORY/output.md";
string mdFolder = Path.GetDirectoryName(mdPath)!;
string[] lines = File.ReadAllLines(mdPath);

foreach (var line in lines)
{
    var match = Regex.Match(line, @"!\[.*?\]\((.+?)\)");
    if (match.Success)
    {
        string imgPath = Path.Combine(mdFolder, match.Groups[1].Value);
        if (!File.Exists(imgPath))
            Console.WriteLine($"Missing image: {imgPath}");
    }
}
Console.WriteLine("Verification complete.");
```

Chạy nó sau khi chuyển đổi; bất kỳ hình ảnh nào bị thiếu sẽ được in ra console.

---

## Những khó khăn thường gặp và thực hành tốt nhất khi chuyển đổi word sang markdown

| Rủi ro | Tại sao gây hại | Cách khắc phục |
|--------|----------------|----------------|
| **Images end up with long GUID names** | Khó đọc trong kiểm soát phiên bản. | Tiền xử lý thư mục để đổi tên các tệp thành tiêu đề có ý nghĩa (ví dụ, dựa trên `args.ResourceFileName` gốc). |
| **Relative paths break after moving the Markdown file** | Các liên kết `![]()` là tương đối so với vị trí của `.md`. | Giữ thư mục hình ảnh bên cạnh tệp Markdown hoặc sử dụng đường dẫn cơ sở nhất quán trong cấu hình site tĩnh. |
| **Missing images when `ExportImagesAsBase64` is `true`** | Callback không bao giờ được kích hoạt vì hình ảnh được nhúng. | Đảm bảo `ExportImagesAsBase64 = false` (mặc định). |
| **Large documents cause `OutOfMemoryException`** | Aspose tải toàn bộ tài liệu vào RAM. | Sử dụng `LoadOptions` với `LoadFormat.Docx` và đặt cờ `MemoryOptimization` nếu có. |
| **Non‑ASCII file names break on some platforms** | Mã hoá URL có thể thất bại. | Giữ ký tự ASCII hoặc đặt `EncodeUrls = true`. |

---

## Tổng kết

Chúng tôi đã bao quát mọi thứ bạn cần để **save word images** trong khi **convert word to markdown** bằng Aspose.Words. Ý tưởng cốt lõi rất đơn giản: gắn một `ResourceSavingCallback`, chỉ tới một thư mục bạn kiểm soát, và để thư viện thực hiện phần còn lại. Sau khi chạy, bạn sẽ có một tệp `.md` sạch sẽ và một bộ tài sản hình ảnh gọn gàng—hoàn hảo cho việc xuất bản hoặc kiểm soát phiên bản.

Nếu bạn muốn **extract images from word** cho các mục đích khác (ví dụ, tạo gallery), chỉ cần tái sử dụng mã callback mà không cần bước lưu Markdown. Tương tự, mẫu này cũng hoạt động cho **convert docx to md** trong các công việc batch—chỉ cần lặp qua một thư mục các tệp `.docx` và gọi cùng một logic.

**Các bước tiếp theo** bạn có thể khám phá:

* Tích hợp quá trình chuyển đổi vào một API ASP.NET Core để người dùng có thể tải lên DOCX và nhận gói Markdown có thể tải xuống.  
* Thêm hỗ trợ cho bảng và

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}