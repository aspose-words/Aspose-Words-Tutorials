---
category: general
date: 2026-04-07
description: Lưu Word dưới dạng Markdown và trích xuất hình ảnh từ docx bằng callback.
  Tìm hiểu cách sử dụng callback để lưu trữ thư mục hình ảnh Markdown một cách hiệu
  quả.
draft: false
keywords:
- save word as markdown
- extract images from docx
- how to use callback
- markdown images folder
language: vi
og_description: Lưu Word dưới dạng Markdown và trích xuất hình ảnh từ docx bằng callback.
  Hướng dẫn này cho thấy cách sử dụng callback để tạo thư mục hình ảnh Markdown.
og_title: Lưu Word thành Markdown – Hướng dẫn chi tiết từng bước
tags:
- Aspose.Words
- C#
- Markdown
- Image Extraction
title: Lưu Word dưới dạng Markdown với Thư mục Hình ảnh Tùy chỉnh – Hướng dẫn đầy
  đủ
url: /vi/net/programming-with-markdownsaveoptions/save-word-as-markdown-with-custom-image-folder-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lưu Word dưới dạng Markdown – Hướng dẫn chi tiết từng bước

Bạn đã bao giờ cần **lưu Word dưới dạng Markdown** nhưng không chắc phải làm gì với các hình ảnh nhúng không? Bạn không phải là người duy nhất. Trong nhiều dự án, kết quả markdown trông tuyệt vời—*cho đến* khi bạn nhận ra các liên kết hình ảnh bị hỏng vì các tệp không bao giờ rời khỏi gói Word.  

Tin tốt là Aspose.Words cung cấp cho bạn một cách sạch sẽ để **trích xuất hình ảnh từ docx** và đặt chúng chính xác ở nơi bạn muốn, bằng cách sử dụng một **callback** cho phép bạn kiểm soát thư mục hình ảnh markdown. Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình, từ việc tải một tệp `.docx` đến khi có được một thư mục PNG gọn gàng (hoặc bất kỳ định dạng nào bạn có) và một tệp markdown trỏ tới chúng.

Khi kết thúc hướng dẫn này, bạn sẽ có thể:

* Chuyển đổi bất kỳ tài liệu Word nào sang Markdown chỉ với một dòng mã.  
* Tự động xuất mọi hình ảnh vào một thư mục con `images` riêng biệt.  
* Tùy chỉnh tên tệp sao cho không bao giờ trùng lặp, ngay cả khi nguồn chứa hàng chục hình ảnh.  

Không cần script bên ngoài, không cần sao chép‑dán thủ công—chỉ cần C# thuần và Aspose.Words.

## Yêu cầu trước

Trước khi bắt đầu, hãy chắc chắn rằng bạn có:

* **Aspose.Words for .NET** (phiên bản ổn định mới nhất; thời điểm viết là 24.9).  
* Môi trường phát triển .NET (Visual Studio, Rider, hoặc `dotnet` CLI).  
* Một tài liệu Word (`.docx`) chứa ít nhất một hình ảnh—gọi nó là `DocWithImages.docx`.  

Nếu bạn chưa từng sử dụng Aspose.Words, đừng lo. Thư viện này hoàn toàn được quản lý, không yêu cầu COM interop, và hoạt động trên .NET 6+ cũng như .NET Framework 4.8.

## Bước 1 – Thiết lập dự án và cài đặt gói

Đầu tiên, tạo một ứng dụng console mới (hoặc thêm mã vào dự án hiện có).

```bash
dotnet new console -n WordToMarkdownDemo
cd WordToMarkdownDemo
dotnet add package Aspose.Words
```

> **Mẹo:** Nếu bạn đang nhắm tới .NET 6, `Program.cs` mặc định đã sử dụng câu lệnh cấp cao, giúp mẫu ngắn gọn hơn.

## Bước 2 – Tạo Callback để Kiểm soát Lưu Hình Ảnh

Aspose.Words gọi `IResourceSavingCallback.ResourceSaving` cho mỗi tài nguyên bên ngoài mà nó cần ghi (hình ảnh, CSS, v.v.). Bằng cách triển khai giao diện này, chúng ta có toàn quyền kiểm soát **cách thư mục hình ảnh markdown** được tạo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

/// <summary>
/// Handles the saving of resources (e.g., images) when a document is converted to Markdown.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    // Folder where we want to dump the images.
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        // Ensure the folder exists before the first write.
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Build a unique filename: img_<guid>.<originalExtension>
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";

        // Full path where the image will be saved.
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        // Copy the incoming stream to our file.
        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        // Tell Aspose we’ve handled the write; skip its default behavior.
        args.Cancel = true;
    }
}
```

### Tại sao lại dùng callback?

* **Kiểm soát chi tiết** – bạn quyết định cấu trúc thư mục và quy tắc đặt tên.  
* **Hiệu năng** – bạn ghi luồng một lần, tránh việc thư viện ghi lại lần thứ hai.  
* **Linh hoạt** – bạn có thể thêm logging, tối ưu hình ảnh, hoặc thậm chí tải lên lưu trữ đám mây tại đây.

## Bước 3 – Tải tài liệu Word

Bây giờ callback đã sẵn sàng, chúng ta chỉ cần chỉ định Aspose.Words tới tệp nguồn.

```csharp
// Path to the source .docx (adjust as needed).
string sourcePath = Path.Combine("YOUR_DIRECTORY", "DocWithImages.docx");

// Load the document into memory.
Document doc = new Document(sourcePath);
```

> **Nếu tệp không được tìm thấy thì sao?**  
> `Document` sẽ ném ra `FileNotFoundException`. Bao bọc việc tải trong `try/catch` nếu bạn dự đoán đường dẫn động.

## Bước 4 – Kết nối MarkdownSaveOptions

Lớp `MarkdownSaveOptions` cho phép chúng ta gắn callback vừa tạo. Chúng ta cũng thiết lập thư mục nơi các hình ảnh sẽ được lưu tương đối với tệp markdown.

```csharp
// Define where we want the images folder to sit.
string markdownFolder = Path.Combine("YOUR_DIRECTORY", "markdown-output");
string imagesSubFolder = Path.Combine(markdownFolder, "images");

// Ensure the markdown output directory exists.
Directory.CreateDirectory(markdownFolder);

// Create the save options and attach the callback.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // This callback will be invoked for every image.
    ResourceSavingCallback = new MyMarkdownResourceCallback(imagesSubFolder),

    // Optional: keep image references relative to the markdown file.
    ImagesFolder = "images"
};
```

Thuộc tính `ImagesFolder` chỉ cho Aspose tạo các liên kết markdown như `![Alt text](images/img_123.png)`. Vì chúng ta cũng đặt `ResourceFileName` trong callback, tệp thực tế sẽ được lưu đúng ở đó.

## Bước 5 – Lưu dưới dạng Markdown và Kiểm tra Kết quả

Cuối cùng, chúng ta ghi tệp markdown. Callback sẽ đã điền sẵn thư mục con `images`.

```csharp
// Destination markdown file.
string markdownPath = Path.Combine(markdownFolder, "Doc.md");

// Save the document.
doc.Save(markdownPath, mdOptions);

// Quick sanity check – list the generated files.
Console.WriteLine("Markdown saved to: " + markdownPath);
Console.WriteLine("Extracted images:");
foreach (var img in Directory.GetFiles(imagesSubFolder))
{
    Console.WriteLine("  • " + Path.GetFileName(img));
}
```

### Kết quả mong đợi

Chạy chương trình sẽ in ra một cái gì đó như sau:

```
Markdown saved to: C:\Project\markdown-output\Doc.md
Extracted images:
  • img_5c2a1f8b-3e7b-4d9a-9c1f-2b6e5f9d9a3c.png
  • img_a7d4c9e2-1f55-4c2b-8f6a-9e1b2c3d4e5f.jpg
```

Mở `Doc.md` trong bất kỳ trình xem markdown nào; bạn sẽ thấy các liên kết hình ảnh trỏ đúng tới thư mục `images`.

---

## Câu hỏi thường gặp (FAQ)

### Làm thế nào để **trích xuất hình ảnh từ docx** mà không chuyển đổi sang markdown?

Bạn có thể tái sử dụng `MyMarkdownResourceCallback` nhưng truyền nó vào `doc.Save("images.zip", SaveFormat.Zip)`. Callback vẫn sẽ được gọi cho mỗi hình ảnh, cho phép bạn đặt chúng ở bất kỳ nơi nào bạn muốn.

### Nếu tôi cần **định dạng hình ảnh khác nhau** thì sao?

`args.FileName` đã chứa phần mở rộng gốc (`.png`, `.jpg`, v.v.). Nếu bạn phải chuyển đổi tất cả hình ảnh sang một định dạng duy nhất, hãy thêm bước chuyển đổi trong `ResourceSaving` trước khi ghi luồng.

### Tôi có thể **tùy chỉnh thư mục hình ảnh markdown** cho mỗi tài liệu không?

Chắc chắn. Callback nhận đường dẫn thư mục qua constructor, vì vậy bạn có thể tạo một callback mới với thư mục khác cho mỗi tài liệu trong quá trình batch.

### Điều này có hoạt động với **tài liệu lớn** (hàng trăm hình ảnh) không?

Có. Callback truyền luồng hình ảnh trực tiếp tới đĩa, giữ mức sử dụng bộ nhớ thấp. Chỉ cần đảm bảo ổ đích có đủ không gian và bạn không vượt quá giới hạn file‑handle của hệ điều hành.

---

## Ví dụ Hoạt động Đầy đủ

Dưới đây là chương trình hoàn chỉnh, sẵn sàng sao chép‑dán. Thay thế `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối phù hợp với môi trường của bạn.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _imageFolder;

    public MyMarkdownResourceCallback(string imageFolder)
    {
        _imageFolder = imageFolder;
        Directory.CreateDirectory(_imageFolder);
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        string uniqueName = $"img_{Guid.NewGuid()}{Path.GetExtension(args.FileName)}";
        string fullPath = Path.Combine(_imageFolder, uniqueName);
        args.ResourceFileName = fullPath;

        using (FileStream outStream = File.OpenWrite(fullPath))
            args.Stream.CopyTo(outStream);

        args.Cancel = true;
    }
}

class Program
{
    static void Main()
    {
        // Adjust these paths.
        string baseDir = Path.Combine(Environment.CurrentDirectory, "demo");
        string sourceDoc = Path.Combine(baseDir, "DocWithImages.docx");
        string markdownDir = Path.Combine(baseDir, "markdown-output");
        string imagesDir = Path.Combine(markdownDir, "images");
        string markdownFile = Path.Combine(markdownDir, "Doc.md");

        // Load the document.
        Document doc;
        try
        {
            doc = new Document(sourceDoc);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // Configure save options with our callback.
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new MyMarkdownResourceCallback(imagesDir),
            ImagesFolder = "images"
        };

        // Ensure output folder exists.
        Directory.CreateDirectory(markdownDir);

        // Save as markdown.
        doc.Save(markdownFile, mdOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownFile}");
        Console.WriteLine("🖼️ Extracted images:");
        foreach (var file in Directory.GetFiles(imagesDir))
            Console.WriteLine($"   - {Path.GetFileName(file)}");
    }
}
```

Chạy chương trình (`dotnet run`) và bạn sẽ thấy một tệp `Doc.md` mới tạo bên cạnh thư mục con `images` chứa

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}