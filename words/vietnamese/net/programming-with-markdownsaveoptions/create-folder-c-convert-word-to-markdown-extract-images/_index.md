---
category: general
date: 2026-02-26
description: Tạo thư mục hướng dẫn C# về cách chuyển đổi Word sang markdown, trích
  xuất hình ảnh từ docx và sao chép luồng vào tệp—tất cả trong một bước.
draft: false
keywords:
- create folder c#
- convert word to markdown
- extract images from docx
- copy stream to file
language: vi
og_description: Hướng dẫn C# tạo thư mục sẽ hướng dẫn bạn cách chuyển đổi Word sang
  markdown, trích xuất hình ảnh từ docx và sao chép luồng vào tệp với các ví dụ mã
  rõ ràng.
og_title: Tạo thư mục C# – Chuyển đổi Word sang Markdown & Trích xuất hình ảnh
tags:
- C#
- Aspose.Words
- Markdown
- Image Extraction
title: Tạo thư mục C# – Chuyển đổi Word sang Markdown & Trích xuất hình ảnh
url: /vi/net/programming-with-markdownsaveoptions/create-folder-c-convert-word-to-markdown-extract-images/
---

delete

But we need to keep the word "delete" maybe as is. Keep as original.

Now after that the content ends with the closing shortcodes.

We must ensure we keep all shortcodes exactly.

Let's assemble final output.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo thư mục C# – Chuyển Word sang Markdown & Trích xuất Hình ảnh

Bạn đã bao giờ cần **tạo thư mục C#** đồng thời chuyển một tài liệu Word sang markdown và trích xuất mọi hình ảnh ra không? Bạn không phải là người duy nhất bối rối về việc này. Trong nhiều quy trình tự động, bạn sẽ phải xử lý các công việc hệ thống tệp, chuyển đổi định dạng và xử lý dữ liệu nhị phân—tất cả trong một lần.  

Trong hướng dẫn này, chúng ta sẽ đi qua một giải pháp hoàn chỉnh, có thể chạy được, thực hiện đúng những gì mô tả: nó tạo một thư mục đích, chuyển `.docx` sang markdown, trích xuất từng hình ảnh nhúng, và sử dụng logic **copy stream to file** để các hình ảnh được lưu ở nơi bạn muốn. Không có script bên ngoài, không có bước thủ công. Chỉ cần C# thuần và thư viện Aspose.Words.

> **Bạn sẽ nhận được**  
> * Một cấu trúc thư mục rõ ràng, sẵn sàng cho markdown và tài nguyên  
> * Một tệp markdown tham chiếu đúng các hình ảnh đã trích xuất  
> * Mã nguồn đầy đủ mà bạn có thể đưa vào bất kỳ dự án .NET nào  

Trước khi bắt đầu, hãy chắc chắn rằng bạn đã có:

* .NET 6.0 (hoặc mới hơn) SDK được cài đặt – mã sử dụng các tính năng ngôn ngữ hiện đại.  
* Giấy phép cho **Aspose.Words for .NET** (bản dùng thử miễn phí đủ cho việc thử nghiệm).  
* Visual Studio 2022 hoặc trình soạn thảo yêu thích của bạn.  

Nếu bạn tự hỏi *tại sao* muốn trích xuất hình ảnh thay vì nhúng chúng, hãy nghĩ đến các trình tạo site tĩnh: chúng ưa thích markdown với các đường dẫn hình ảnh tương đối, và việc giữ tài nguyên trong một thư mục riêng giúp mọi thứ gọn gàng và thân thiện với bộ nhớ đệm.

---

## Tạo thư mục C# và chuẩn bị cấu trúc đầu ra

Điều đầu tiên chúng ta cần là một vị trí trên đĩa để mọi thứ tồn tại. Bước này là nơi hành động **create folder C#** diễn ra, và nó bất ngờ đơn giản nhờ `Directory.CreateDirectory`. Phương thức này là idempotent—nó sẽ không ném lỗi nếu thư mục đã tồn tại, giúp chúng ta tránh các kiểm tra bổ sung.

```csharp
using System;
using System.IO;

// Define the base output directory (adjust as needed)
string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");

// Subfolders for markdown and images
string markdownFolder = Path.Combine(baseOutput, "markdown");
string imagesFolder   = Path.Combine(baseOutput, "MyImages");

// Ensure the folders exist
Directory.CreateDirectory(markdownFolder);
Directory.CreateDirectory(imagesFolder);

Console.WriteLine($"Created folders:\n • {markdownFolder}\n • {imagesFolder}");
```

**Tại sao điều này quan trọng:**  
Tạo các thư mục trước đảm bảo các bước lưu sau này sẽ không gặp lỗi `DirectoryNotFoundException`. Nó cũng cung cấp cho bạn một bố cục dự đoán được: `output/markdown` cho tệp `.md` và `output/MyImages` cho mọi hình ảnh chúng ta trích xuất.

> **Mẹo chuyên nghiệp:** Nếu bạn chạy chương trình nhiều lần, bạn có thể muốn làm sạch thư mục hình ảnh trước (`Directory.GetFiles(imagesFolder).ToList().ForEach(File.Delete);`) để tránh các tệp cũ.

## Chuyển Word sang Markdown bằng Aspose.Words

Bây giờ cây thư mục đã sẵn sàng, chúng ta hãy chuyển tài liệu Word sang markdown. Aspose.Words thực hiện phần công việc nặng—không cần thao tác với OpenXML hay các bộ chuyển đổi bên thứ ba.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source DOCX (replace with your actual path)
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
var doc = new Document(inputPath);

// Configure markdown options and attach the image callback (we’ll define it later)
var mdOptions = new MarkdownSaveOptions
{
    // The callback will redirect each extracted image to our custom folder
    ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
};

// Save the markdown file into the previously created folder
string markdownPath = Path.Combine(markdownFolder, "output.md");
doc.Save(markdownPath, mdOptions);

Console.WriteLine($"Word document converted to markdown at: {markdownPath}");
```

**Điều gì đang diễn ra bên trong?**  
`MarkdownSaveOptions` chỉ định cho Aspose xuất ra cú pháp markdown. Mặc định, thư viện sẽ lưu hình ảnh vào cùng thư mục với tệp markdown với tên tự động tạo. Bằng cách cung cấp một `ResourceSavingCallback`, chúng ta can thiệp hành vi này và **copy stream to file** vào vị trí mà chúng ta chọn.

## Trích xuất hình ảnh từ DOCX và lưu chúng

Lớp callback triển khai `IResourceSavingCallback`. Bên trong chúng ta nhận được một đối tượng `ResourceSavingArgs` chứa luồng hình ảnh gốc và tên tệp được đề xuất. Sau đó chúng ta ghi luồng đó ra đĩa, đổi tên tệp nếu muốn, và thông báo cho Aspose rằng chúng ta đã xử lý.

```csharp
using Aspose.Words.Saving;
using System.IO;

/// <summary>
/// Handles image extraction during markdown conversion.
/// </summary>
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;

    public ImageSavingCallback(string targetFolder)
    {
        _targetFolder = targetFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // Ensure the target folder exists (defensive, though we created it earlier)
        Directory.CreateDirectory(_targetFolder);

        // Build a new, friendly file name – you can customize the pattern
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);

        // **Copy stream to file** – the core of the image extraction
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }

        // Tell Aspose to use our new path in the markdown reference
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true; // Prevent default saving logic
    }
}
```

### Cấu trúc markdown sẽ như thế nào

Sau quá trình chuyển đổi, tệp `output.md` được tạo sẽ chứa các dòng như:

```markdown
![Image 1](MyImages/img_picture1.png)
```

Vì chúng ta đã thay đổi `args.ResourceFileName` thành một đường dẫn tương đối, markdown sẽ trỏ trực tiếp tới thư mục chúng ta đã tạo. Đây chính là những gì các trình tạo site tĩnh mong đợi.

**Xử lý trường hợp đặc biệt:**  
*Nếu tài liệu chứa các tên hình ảnh trùng lặp*, tiền tố `img_` cộng với tên gốc thường tránh được xung đột, nhưng bạn cũng có thể thêm GUID (`Guid.NewGuid()`) để đảm bảo duy nhất tuyệt đối.

## Copy stream to file – xử lý dữ liệu hình ảnh

Bạn có thể tự hỏi tại sao chúng ta không chỉ gọi `File.WriteAllBytes`. Câu trả lời nằm ở **tính linh hoạt của stream**. `args.Stream` có thể là một memory stream, một network stream, hoặc bất kỳ triển khai nào khác. Bằng cách sử dụng `CopyTo`, chúng ta giữ tính trung lập và để .NET tự quản lý kích thước bộ đệm một cách hiệu quả.

Dưới đây là một phương thức tiện ích ngắn gọn nếu bạn cần sao chép một stream chung tới nơi khác:

```csharp
/// <summary>
/// Copies any readable stream to a file on disk.
/// </summary>
public static void CopyStreamToFile(Stream source, string destinationPath)
{
    using (var file = new FileStream(destinationPath, FileMode.Create, FileAccess.Write))
    {
        source.CopyTo(file);
    }
}
```

Bạn có thể thay thế việc sao chép nội tuyến trong `ImageSavingCallback` bằng một lời gọi tới `CopyStreamToFile` nếu muốn áp dụng nguyên tắc trách nhiệm đơn.

## Ví dụ đầy đủ có thể chạy được

Kết hợp tất cả các phần lại với nhau sẽ cho bạn một chương trình tự chứa mà bạn có thể chạy từ dòng lệnh:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the folder structure
        string baseOutput = Path.Combine(Environment.CurrentDirectory, "output");
        string markdownFolder = Path.Combine(baseOutput, "markdown");
        string imagesFolder   = Path.Combine(baseOutput, "MyImages");
        Directory.CreateDirectory(markdownFolder);
        Directory.CreateDirectory(imagesFolder);

        // 2️⃣ Load the DOCX
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(inputPath);

        // 3️⃣ Set up markdown options with our image callback
        var mdOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = new ImageSavingCallback(imagesFolder)
        };

        // 4️⃣ Save as markdown
        string markdownPath = Path.Combine(markdownFolder, "output.md");
        doc.Save(markdownPath, mdOptions);

        Console.WriteLine("✅ Conversion complete!");
        Console.WriteLine($"Markdown: {markdownPath}");
        Console.WriteLine($"Images folder: {imagesFolder}");
    }
}

// ---------- ImageSavingCallback (same as earlier) ----------
public class ImageSavingCallback : IResourceSavingCallback
{
    private readonly string _targetFolder;
    public ImageSavingCallback(string targetFolder) => _targetFolder = targetFolder;

    public void ResourceSaving(ResourceSavingArgs args)
    {
        Directory.CreateDirectory(_targetFolder);
        string newFileName = $"img_{Path.GetFileName(args.ResourceFileName)}";
        string fullPath = Path.Combine(_targetFolder, newFileName);
        using (FileStream fs = new FileStream(fullPath, FileMode.Create, FileAccess.Write))
        {
            args.Stream.CopyTo(fs);
        }
        args.ResourceFileName = Path.Combine("MyImages", newFileName);
        args.Handled = true;
    }
}
```

**Kết quả mong đợi**

* `output/markdown/output.md` – một tệp markdown mà các tham chiếu hình ảnh trông như `![Alt text](MyImages/img_picture1.png)`.  
* `output/MyImages/` – một tệp PNG/JPEG cho mỗi hình ảnh ban đầu nằm trong `input.docx`.  

Mở markdown bằng bất kỳ trình xem nào (VS Code, GitHub, hoặc một trình tạo site tĩnh) và bạn sẽ thấy các hình ảnh được hiển thị chính xác nơi chúng xuất hiện trong tệp Word gốc.

## Câu hỏi thường gặp & khắc phục sự cố

| Câu hỏi | Câu trả lời |
|----------|--------|
| **Nếu thư mục đích đã có tệp?** | `Directory.CreateDirectory` sẽ không ghi đè. Nếu bạn cần một lần chạy sạch, delete

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}