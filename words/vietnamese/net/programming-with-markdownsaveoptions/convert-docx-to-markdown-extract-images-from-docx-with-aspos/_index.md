---
category: general
date: 2026-04-05
description: Học cách chuyển đổi DOCX sang Markdown và trích xuất hình ảnh từ DOCX
  trong C#. Hướng dẫn từng bước với mã nguồn đầy đủ và các mẹo.
draft: false
keywords:
- convert docx to markdown
- extract images from docx
- Aspose.Words markdown conversion
- C# document processing
- image extraction C#
language: vi
og_description: Chuyển đổi DOCX sang Markdown và trích xuất hình ảnh từ DOCX bằng
  Aspose.Words. Hướng dẫn C# đầy đủ với mã nguồn, giải thích và các mẹo thực hành
  tốt nhất.
og_title: Chuyển DOCX sang Markdown – Trích xuất hình ảnh từ DOCX bằng C#
tags:
- Aspose.Words
- C#
- Markdown
- DOCX
- Image extraction
title: Chuyển DOCX sang Markdown – Trích xuất hình ảnh từ DOCX bằng Aspose.Words
url: /vi/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-extract-images-from-docx-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chuyển DOCX sang Markdown – Trích xuất hình ảnh từ DOCX trong C#

Bạn đã bao giờ cần **chuyển DOCX sang Markdown** nhưng gặp khó khăn vì các hình ảnh biến mất trong kết quả chưa? Bạn không phải là người duy nhất. Trong nhiều dự án, phiên bản markdown là hoàn hảo cho việc kiểm soát phiên bản hoặc các trình tạo trang tĩnh, nhưng các hình ảnh lại bị bỏ lại, biến một tài liệu phong phú thành một tệp văn bản trống rỗng.  

Tin tốt? Chỉ với vài dòng C# và Aspose.Words, bạn có thể **chuyển DOCX sang Markdown** *và* **tự động trích xuất hình ảnh từ DOCX**. Hướng dẫn này sẽ đưa bạn qua toàn bộ quá trình, giải thích lý do mỗi phần quan trọng, và thậm chí chỉ cho bạn cách giữ thư mục hình ảnh gọn gàng.

## Những gì bạn sẽ học

- Cách tải một tệp DOCX có chứa hình ảnh.
- Cách định nghĩa một `IResourceSavingCallback` tùy chỉnh để quyết định nơi lưu mỗi hình ảnh.
- Cách cấu hình `MarkdownSaveOptions` để markdown được tạo tham chiếu đúng các hình ảnh đã trích xuất.
- Mẹo xử lý các trường hợp đặc biệt như tên hình ảnh trùng lặp hoặc định dạng không phải PNG.
- Một mẫu mã hoàn chỉnh, sẵn sàng sao chép‑dán mà bạn có thể chạy ngay hôm nay.

### Yêu cầu trước

- .NET 6.0 trở lên (API hoạt động trên .NET Core, .NET Framework và .NET 5+).
- Giấy phép cho **Aspose.Words for .NET** (bản dùng thử miễn phí đủ cho việc thử nghiệm).
- Kiến thức cơ bản về C# và Visual Studio (hoặc IDE yêu thích của bạn).

Nếu bạn đã có những thứ trên, hãy bắt đầu.

---

## Bước 1: Thiết lập dự án và cài đặt Aspose.Words

Đầu tiên, tạo một ứng dụng console mới (hoặc tích hợp vào một solution hiện có).

```bash
dotnet new console -n DocxToMarkdownDemo
cd DocxToMarkdownDemo
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Sử dụng phiên bản NuGet mới nhất (tính đến tháng 4 2026 là 24.12) để có các cải tiến mới nhất cho việc xuất markdown.

---

## Bước 2: Tạo Callback để lưu hình ảnh ở vị trí bạn muốn

Aspose.Words cho phép bạn chặn mọi tài nguyên (hình ảnh, SVG, v.v.) được ghi trong quá trình xuất markdown. Bằng cách triển khai `IResourceSavingCallback` bạn có thể:

1. Chọn một thư mục nằm cạnh tệp markdown của bạn.
2. Tạo một tên tệp duy nhất (để bạn không bao giờ ghi đè lên hình ảnh đã tồn tại).
3. Quyết định định dạng (ở đây chúng tôi ép PNG để đồng nhất).

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Saves each image extracted from the DOCX into a dedicated folder
/// with a GUID‑based filename. The markdown file will reference the
/// new filename via <c>args.ResourceFileName</c>.
/// </summary>
class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageResourceSaver(string targetFolder)
    {
        _targetFolder = targetFolder;
        // Ensure the folder exists before we start writing files.
        Directory.CreateDirectory(_targetFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Generate a unique name to avoid collisions.
        string newFileName = $"img_{Guid.NewGuid():N}.png";

        // Full physical path where the image will be written.
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // Tell the markdown exporter what name to use in the .md file.
        args.ResourceFileName = newFileName;

        // Provide a stream that writes to the desired location.
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}
```

### Tại sao lại dùng tên dựa trên GUID?

Nếu DOCX nguồn chứa hai hình ảnh có cùng tên gốc, việc sao chép‑dán đơn giản sẽ ghi đè lên một trong số chúng. Sử dụng `Guid.NewGuid()` đảm bảo tính duy nhất, điều này đặc biệt hữu ích khi bạn chạy chuyển đổi nhiều lần trong một pipeline tự động.

---

## Bước 3: Tải DOCX và cấu hình các tùy chọn Markdown

Bây giờ chúng ta đưa tài liệu vào bộ nhớ và gắn callback mà chúng ta vừa tạo.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------------
        // 1️⃣  Define paths – adjust these to match your environment.
        // --------------------------------------------------------------------
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMarkdown = @"C:\Docs\DocWithImages.md";
        string imagesFolder = @"C:\Docs\MarkdownResources";

        // --------------------------------------------------------------------
        // 2️⃣  Load the Word document.
        // --------------------------------------------------------------------
        Document doc = new Document(sourceDocx);

        // --------------------------------------------------------------------
        // 3️⃣  Configure MarkdownSaveOptions with our custom saver.
        // --------------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This tells Aspose.Words to call ImageResourceSaver for each image.
            ResourceSavingCallback = new ImageResourceSaver(imagesFolder)
        };

        // --------------------------------------------------------------------
        // 4️⃣  Perform the conversion.
        // --------------------------------------------------------------------
        doc.Save(outputMarkdown, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown saved to: {outputMarkdown}");
        Console.WriteLine($"Images saved to:   {imagesFolder}");
    }
}
```

### Những gì mã thực hiện, từng bước

| Bước | Mục đích |
|------|----------|
| **Xác định đường dẫn** | Giữ cho dự án của bạn linh hoạt; bạn có thể chỉ tới bất kỳ thư mục nào mà không cần biên dịch lại. |
| **Tải DOCX** | `Document` phân tích tệp Word, cho phép truy cập tất cả các thành phần (đoạn văn, bảng, hình ảnh). |
| **Cấu hình `MarkdownSaveOptions`** | `ResourceSavingCallback` là hook để trích xuất hình ảnh. Nếu không có nó, Aspose.Words sẽ nhúng hình ảnh dưới dạng chuỗi base64 hoặc bỏ chúng hoàn toàn, tùy thuộc vào cài đặt. |
| **Lưu** | `doc.Save` ghi tệp markdown và kích hoạt callback cho mỗi hình ảnh. |

---

## Bước 4: Xác minh đầu ra – Bạn sẽ thấy gì?

Sau khi chạy chương trình, mở `DocWithImages.md`. Bạn sẽ thấy các liên kết hình ảnh markdown trông như sau:

```markdown
![img_1a2b3c4d5e6f7g8h9i0j.png](MarkdownResources/img_1a2b3c4d5e6f7g8h9i0j.png)
```

Và trong `C:\Docs\MarkdownResources` bạn sẽ tìm thấy một loạt các tệp PNG có tên GUID. Mở bất kỳ tệp nào – chúng sẽ giống hệt các hình ảnh đã được nhúng trong DOCX gốc.

Nếu bạn mở tệp markdown trong một trình xem hỗ trợ đường dẫn tương đối (ví dụ: xem trước VS Code, GitHub, hoặc một trình tạo trang tĩnh), các hình ảnh sẽ hiển thị giống như trong Word.

### Những lỗi thường gặp & Cách tránh

| Triệu chứng | Nguyên nhân có thể | Cách khắc phục |
|------------|--------------------|----------------|
| Hình ảnh xuất hiện dưới dạng liên kết hỏng | `ResourceFileName` chưa được đặt, vì vậy markdown trỏ tới tệp không tồn tại. | Đảm bảo `args.ResourceFileName = newFileName;` trong callback. |
| Các tệp PNG quá lớn | Hình ảnh gốc là JPEG hoặc BMP; chuyển sang PNG có thể làm tăng kích thước. | Phát hiện định dạng gốc qua `args.ResourceContentType` và giữ nguyên: `args.ResourceFileName = $"{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}";` |
| Các hình ảnh trùng lặp vẫn xuất hiện | Bạn đã sử dụng tên tệp tĩnh thay vì GUID. | Quay lại logic GUID hoặc thêm bộ đếm cho mỗi loại hình ảnh. |
| Quá trình chuyển đổi ném `FileNotFoundException` | Đường dẫn DOCX nguồn sai hoặc thư mục không có quyền đọc. | Kiểm tra lại đường dẫn và cấp quyền hệ thống tập tin phù hợp. |

---

## Bước 5: Tinh chỉnh nâng cao (Tùy chọn)

### 5.1 Giữ nguyên định dạng hình ảnh gốc

Nếu bạn muốn các hình ảnh đầu ra giữ nguyên phần mở rộng gốc, hãy sửa đổi callback:

```csharp
public void ResourceSaving(ResourceSavingArgs args)
{
    string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
    // Default to .png if Aspose couldn't determine an extension.
    if (string.IsNullOrEmpty(ext)) ext = ".png";

    string newFileName = $"img_{Guid.NewGuid():N}{ext}";
    string fullPath = Path.Combine(_targetFolder, newFileName);
    args.ResourceFileName = newFileName;
    args.Stream = new FileStream(fullPath, FileMode.Create);
}
```

### 5.2 Nhúng hình ảnh dưới dạng Base64 (Khi bạn *không* muốn tách riêng các tệp)

Đôi khi một markdown duy nhất là ưu tiên (ví dụ: để gửi qua email). Thay đổi tùy chọn:

```csharp
mdOptions.ImagesFolder = string.Empty; // disables external folder
mdOptions.ExportImagesAsBase64 = true;
```

Nhưng hãy nhớ: **trích xuất hình ảnh từ DOCX** là mục tiêu chính cho hầu hết các quy trình làm việc với trang tĩnh, vì vậy cách sử dụng thư mục thường là lựa chọn tốt hơn.

---

## Ví dụ Hoạt động đầy đủ (Sẵn sàng sao chép‑dán)

Dưới đây là toàn bộ chương trình trong một tệp. Chỉ cần thay đổi các đường dẫn thành của bạn và chạy.

```csharp
// ---------------------------------------------------------------
// Convert DOCX to Markdown – Extract Images from DOCX
// ---------------------------------------------------------------
// NuGet: Aspose.Words (>= 24.12)
// ---------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class ImageResourceSaver : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageResourceSaver(string targetFolder) => Directory.CreateDirectory(_targetFolder = targetFolder);

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string ext = Path.GetExtension(args.ResourceFileName).ToLowerInvariant();
        if (string.IsNullOrEmpty(ext)) ext = ".png";
        string newFileName = $"img_{Guid.NewGuid():N}{ext}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        args.ResourceFileName = newFileName;
        args.Stream = new FileStream(fullPath, FileMode.Create);
    }
}

class Program
{
    static void Main()
    {
        // 👉 Adjust these paths:
        string sourceDocx = @"C:\Docs\WithImages.docx";
        string outputMd  = @"C:\Docs\DocWithImages.md";
        string imgFolder = @"C:\Docs\MarkdownResources";

        // Load the DOCX.
        Document doc = new Document(sourceDocx);

        // Set up markdown options with our image saver.
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageResourceSaver(imgFolder)
        };

        // Perform conversion.
        doc.Save(outputMd, mdOptions);

        Console.WriteLine("✅ DOCX successfully converted to Markdown.");
        Console.WriteLine($"📄 Markdown: {outputMd}");
        Console.WriteLine($"🖼️ Images folder: {imgFolder}");
    }
}
```

Chạy nó bằng `dotnet run`. Khi console in ra dòng ✅, mở tệp markdown và bạn sẽ thấy các hình ảnh được hiển thị đúng.

---

## Kết luận

Bây giờ bạn đã có một **giải pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để chuyển DOCX sang Markdown và trích xuất hình ảnh từ DOCX** bằng Aspose.Words trong C#. Từ khóa chính xuất hiện xuyên suốt hướng dẫn, tăng cường tính liên quan cho cả công cụ tìm kiếm và trợ lý AI.  

Trong một lần chạy duy nhất, mã thực hiện:

1. Tải tài liệu Word.
2. Chặn mỗi hình ảnh qua `IResourceSavingCallback`.
3. Lưu mỗi hình ảnh vào một thư mục dự đoán được với tên duy nhất.
4. Tạo markdown tham chiếu tới các hình ảnh đó.

Từ đây bạn có thể:

- Plug

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}