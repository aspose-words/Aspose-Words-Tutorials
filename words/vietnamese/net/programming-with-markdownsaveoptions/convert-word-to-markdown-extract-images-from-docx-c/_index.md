---
category: general
date: 2026-03-17
description: Chuyển đổi Word sang Markdown trong C# đồng thời trích xuất hình ảnh
  từ DOCX. Tìm hiểu cách trích xuất hình ảnh, thiết lập callbacks và lưu markdown
  với thư mục assets.
draft: false
keywords:
- convert word to markdown
- extract images from docx
- how to extract images
- how to convert docx
language: vi
og_description: Chuyển đổi Word sang Markdown bằng C# và học cách trích xuất hình
  ảnh từ DOCX. Mã nguồn, giải thích chi tiết và mẹo từng bước để quá trình chuyển
  đổi diễn ra suôn sẻ.
og_title: Chuyển đổi Word sang Markdown & Trích xuất hình ảnh từ DOCX (C#) – Hướng
  dẫn đầy đủ
tags:
- Aspose.Words
- C#
- Markdown
- Document Conversion
title: Chuyển Word sang Markdown & Trích xuất hình ảnh từ DOCX (C#)
url: /vi/net/programming-with-markdownsaveoptions/convert-word-to-markdown-extract-images-from-docx-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chuyển đổi Word sang Markdown & Trích xuất Hình ảnh từ DOCX (C#)

Bạn đã bao giờ **chuyển đổi Word sang Markdown** nhưng lại gặp rắc rối với những hình ảnh biến mất một cách bí ảo? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế — như các trình tạo site tĩnh, quy trình tài liệu, hay các CMS headless — bạn cần cả văn bản markdown **và** các hình ảnh gốc, được lưu gọn trong một thư mục *assets*.  

Trong hướng dẫn này, bạn sẽ thấy **cách chuyển đổi docx** sang markdown **kèm trích xuất hình ảnh** bằng Aspose.Words cho .NET. Chúng ta sẽ thiết lập một callback lưu tài nguyên, xử lý các trường hợp đặc biệt như tên file trùng lặp, và cuối cùng có được cấu trúc thư mục sạch sẽ, sẵn sàng cho trình tạo site tĩnh của bạn.  

## Những gì bạn sẽ học

- Tải một file `.docx` và chuẩn bị cho việc chuyển đổi.  
- Triển khai `IResourceSavingCallback` để **trích xuất hình ảnh từ DOCX**.  
- Cấu hình `MarkdownSaveOptions` để markdown tham chiếu đúng tới các tài nguyên.  
- Chạy mã và xác minh rằng cả file `.md` và thư mục hình ảnh đều được tạo ra như mong đợi.  

**Yêu cầu trước** – bạn cần .NET 6+ (hoặc .NET Framework 4.7.2+) và một giấy phép Aspose.Words (bản dùng thử miễn phí đủ cho demo này). Kiến thức cơ bản về C# và I/O file sẽ giúp quá trình suôn sẻ hơn, nhưng hướng dẫn này đã tự chứa đầy đủ.

![Bố cục thư mục chuyển Word sang Markdown](https://example.com/convert-word-to-markdown.png "Bố cục thư mục chuyển Word sang Markdown")

*Bố cục thư mục sau khi chuyển đổi – file markdown nằm cạnh một thư mục `assets` chứa mọi hình ảnh đã được trích xuất.*

---

## Bước 1: Tải Tài liệu Nguồn (convert word to markdown)

Điều đầu tiên chúng ta làm là đọc file `.docx` mà bạn muốn chuyển thành markdown. Aspose.Words ẩn đi chi tiết OPC cấp thấp, vì vậy chỉ một dòng lệnh là đủ.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

// Adjust these paths to match your environment.
string inputPath  = Path.Combine("YOUR_DIRECTORY", "input.docx");
string outputDir  = Path.Combine("YOUR_DIRECTORY", "output");

// Ensure the output folder exists.
Directory.CreateDirectory(outputDir);

// Load the DOCX file.
Document document = new Document(inputPath);
```

*Tại sao điều này quan trọng:* Việc tải tài liệu sớm cho chúng ta một đối tượng `Document` chứa cả nội dung văn bản **và** các tài nguyên nhúng (hình ảnh, biểu đồ, v.v.). Nếu bỏ qua bước này, bạn sẽ không thể **cách trích xuất hình ảnh** sau này.

---

## Bước 2: Tạo Callback để **cách trích xuất hình ảnh** từ DOCX

Aspose.Words sẽ gọi `IResourceSavingCallback` của bạn mỗi khi cần ghi một tài nguyên (như hình ảnh). Bằng cách cung cấp triển khai riêng, chúng ta quyết định **nơi** file sẽ được lưu và **cách** markdown sẽ tham chiếu tới nó.

```csharp
/// <summary>
/// Saves each extracted resource (image, video, etc.) into an "assets" sub‑folder
/// and rewrites the markdown reference to point at that relative path.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _outputDirectory;

    public MyMarkdownResourceCallback(string outputDirectory)
    {
        _outputDirectory = outputDirectory;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the assets folder path.
        string assetsFolder = Path.Combine(_outputDirectory, "assets");
        Directory.CreateDirectory(assetsFolder);

        // 2️⃣ Resolve potential filename collisions.
        string safeFileName = GetUniqueFileName(assetsFolder, args.ResourceFileName);

        // 3️⃣ Write the resource stream to disk.
        string assetPath = Path.Combine(assetsFolder, safeFileName);
        using (FileStream fs = new FileStream(assetPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // 4️⃣ Tell the markdown writer the *relative* path it should embed.
        args.ResourceFileName = Path.Combine("assets", safeFileName);
        args.KeepResourceStreamOpen = false; // we already closed it
    }

    // Helper: ensure we don't overwrite an existing file.
    private string GetUniqueFileName(string folder, string originalName)
    {
        string filePath = Path.Combine(folder, originalName);
        if (!File.Exists(filePath))
            return originalName;

        string nameWithoutExt = Path.GetFileNameWithoutExtension(originalName);
        string ext = Path.GetExtension(originalName);
        int counter = 1;

        while (File.Exists(filePath))
        {
            string candidate = $"{nameWithoutExt}_{counter}{ext}";
            filePath = Path.Combine(folder, candidate);
            counter++;
        }

        return Path.GetFileName(filePath);
    }
}
```

**Các điểm chính**  

- **Tại sao lại dùng thư mục con assets?** Giữ hình ảnh riêng biệt khỏi file `.md` phản ánh cấu trúc mà hầu hết các trình tạo site tĩnh mong đợi.  
- **Xử lý va chạm** ngăn ngừa lỗi “file already exists” khi cùng một hình ảnh xuất hiện nhiều lần.  
- Đặt `args.KeepResourceStreamOpen = false` thông báo cho Aspose rằng chúng ta đã xử lý stream, tránh rò rỉ bộ nhớ.

---

## Bước 3: Gắn Callback vào **MarkdownSaveOptions**

Bây giờ chúng ta chỉ định cho Aspose.Words sử dụng callback của mình mỗi khi ghi một tài nguyên. Đây là phần cốt lõi của **cách chuyển đổi docx** trong khi bảo toàn các phương tiện truyền thông.

```csharp
// Instantiate the callback with the output directory.
var resourceCallback = new MyMarkdownResourceCallback(outputDir);

// Configure markdown options.
MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions
{
    // The callback does the heavy lifting for image extraction.
    ResourceSavingCallback = resourceCallback,

    // Optional: make the markdown more GitHub‑friendly.
    ExportImagesAsBase64 = false, // we want separate files, not embedded data URIs.
    ExportHeadersFooters = true,
    ExportDocumentProperties = false
};
```

*Tại sao chúng ta đặt `ExportImagesAsBase64 = false`*: Hình ảnh được mã hoá Base64 làm tăng kích thước file markdown và phá vỡ mục đích có một thư mục `assets` sạch sẽ. Khi tắt tùy chọn này, markdown sẽ chứa một tham chiếu đơn giản `![](assets/image.png)`.

---

## Bước 4: Lưu Tài liệu dưới dạng Markdown

Với mọi thứ đã sẵn sàng, bước cuối cùng chỉ cần một dòng lệnh để tạo cả file `.md` và các hình ảnh.

```csharp
string markdownPath = Path.Combine(outputDir, "output.md");

// Save the document.
document.Save(markdownPath, markdownOptions);
Console.WriteLine($"✅ Conversion complete! Markdown saved to: {markdownPath}");
Console.WriteLine($"📁 Extracted images are in: {Path.Combine(outputDir, "assets")}");
```

**Bạn sẽ thấy**  

- `output.md` chứa văn bản markdown, trong đó mỗi thẻ hình ảnh trỏ tới `assets/<image_name>`.  
- Một thư mục `assets` được lấp đầy bằng các file PNG, JPEG hoặc GIF đã được nhúng trong `input.docx`.  

Mở `output.md` bằng bất kỳ trình xem markdown nào (VS Code, GitHub, MkDocs) và bạn sẽ thấy các hình ảnh được hiển thị chính xác như trong tài liệu Word.

---

## Xử lý Các Trường Hợp Thường Gặp (FAQ)

### Nếu DOCX chứa các tên hình ảnh trùng lặp thì sao?
Trợ giúp `GetUniqueFileName` của chúng tôi sẽ thêm hậu tố tăng dần (`image_1.png`, `image_2.png`, …) để không có file nào bị ghi đè.

### Tôi có cần giấy phép cho Aspose.Words không?
Bản dùng thử đủ cho việc thử nghiệm, nhưng trong môi trường sản xuất bạn nên mua giấy phép để loại bỏ watermark đánh giá và đạt hiệu năng tối đa.

### Tôi có thể chuyển đổi nhiều file Word cùng lúc không?
Chắc chắn. Đặt đoạn tải và lưu trong một vòng lặp `foreach (var file in Directory.GetFiles(sourceFolder, "*.docx"))`, tái sử dụng cùng một thể hiện `MyMarkdownResourceCallback` (hoặc tạo mới cho mỗi file nếu muốn thư mục assets riêng biệt).

### Còn các tài nguyên không phải hình ảnh (ví dụ PDF nhúng) thì sao?
Callback nhận **bất kỳ** loại tài nguyên nào. Bạn có thể kiểm tra `args.ResourceType` và quyết định giữ, bỏ qua hoặc đổi tên chúng.

### Phương pháp này có tương thích với .NET Core không?
Có. Mã trên nhắm tới .NET 6, nhưng bạn có thể hạ cấp xuống .NET Framework 4.7.2 bằng cách điều chỉnh file dự án. Aspose.Words hỗ trợ cả hai runtime.

---

## Mẹo Chuyên Gia & Thực Hành Tốt Nhất

- **Giữ thư mục assets gọn gàng** – sau khi chuyển đổi hàng loạt, chạy một script nhanh để xóa các file có kích thước 0 byte có thể được tạo ra bởi các placeholder rỗng.  
- **Sử dụng tên file có ý nghĩa** – nếu bạn muốn tên hình ảnh dễ đọc, hãy trích xuất `AltText` gốc (nếu có) từ `args.ResourceFileName` và đưa vào tên file.  
- **Kiểm soát phiên bản** – chỉ lưu markdown trong repo; thư mục assets có thể được tạo tự động trong pipeline CI, giúp repository nhẹ hơn.  
- **Hiệu năng** – với tài liệu lớn, cân nhắc stream đầu ra bằng cách đặt `markdownOptions.SaveFormat = SaveFormat.Markdown;` và ghi vào một `MemoryStream` trước.

---

## Ví dụ Hoàn chỉnh (Sẵn sàng Sao Chép)

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

/// <summary>
/// Demonstrates converting a DOCX to Markdown while extracting images into an assets folder.
/// </summary>
class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1️⃣ Paths – adjust these to your environment.
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        string outputDir = Path.Combine("YOUR_DIRECTORY", "output");
        Directory.CreateDirectory(outputDir);

        // -----------------------------------------------------------------
        // 2️⃣ Load the source document.
        // -----------------------------------------------------------------
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // 3️⃣ Set up the resource‑saving callback.
        // -----------------------------------------------------------------
        var callback = new MyMarkdownResourceCallback(outputDir);

        // -----------------------------------------------------------------
        // 4️⃣ Configure Markdown options.
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = callback,
            ExportImagesAsBase64 = false,
            ExportHeadersFooters = true,
            ExportDocumentProperties = false
        };

        // -----------------------------------------------------------------
        // 5️⃣ Save as Markdown.
        // -----------------------------------------------------------------
        string markdownFile = Path

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}