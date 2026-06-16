---
category: general
date: 2026-04-28
description: Tìm hiểu cách đặt đường dẫn tương đối cho ảnh markdown khi chuyển Word
  sang markdown, trích xuất ảnh từ Word và tạo thư mục resources cho các ảnh đã xuất.
draft: false
keywords:
- markdown image relative path
- convert word to markdown
- extract images from word
- create resources folder
- export images from docx
language: vi
og_description: Đặt đường dẫn tương đối cho ảnh markdown khi bạn chuyển đổi Word sang
  markdown, trích xuất ảnh từ Word và tạo thư mục resources cho các ảnh đã xuất.
og_title: đường dẫn tương đối của hình ảnh markdown – Chuyển Word sang Markdown
tags:
- Aspose.Words
- C#
- Markdown
- Image Export
title: Đường dẫn tương đối cho hình ảnh markdown – Chuyển Word sang Markdown
url: /vi/net/programming-with-markdownsaveoptions/markdown-image-relative-path-convert-word-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Đường dẫn ảnh markdown tương đối – Chuyển Word sang Markdown

Bạn đã bao giờ cần một **markdown image relative path** khi **convert Word to markdown** chưa? Bạn không phải là người duy nhất. Hầu hết các nhà phát triển gặp khó khăn khi Markdown được tạo ra trỏ tới các ảnh trong một thư mục phẳng, làm phá vỡ cấu trúc liên kết tương đối mà bạn mong đợi trong một trang tĩnh hoặc repo GitHub.

Trong tutorial này, chúng ta sẽ đi qua một giải pháp hoàn chỉnh, từ đầu đến cuối mà **extracts images from Word**, **creates a resources folder**, và ghi lại các tham chiếu ảnh sao cho chúng sử dụng một *markdown image relative path* sạch sẽ. Khi kết thúc, bạn sẽ có một tệp `.md` sẵn sàng xuất bản và một thư mục `Resources` được tổ chức gọn gàng chứa mọi hình ảnh được trích xuất từ tệp `.docx` gốc.

> **Bạn sẽ nhận được:** một chương trình C# duy nhất (không có script bên ngoài), một giải thích rõ ràng về *tại sao* mỗi phần quan trọng, và một vài mẹo thực tế mà bạn có thể sao chép‑dán vào dự án của mình.

---

## Yêu cầu trước

- **.NET 6.0** hoặc phiên bản mới hơn đã được cài đặt (bạn cũng có thể nhắm mục tiêu .NET Framework 4.7+, nhưng .NET 6 là lựa chọn tối ưu cho các dự án mới).
- **Aspose.Words for .NET** (gói NuGet mới nhất tại thời điểm viết, phiên bản 23.12). Cài đặt bằng:
  ```bash
  dotnet add package Aspose.Words
  ```
- Một tài liệu Word thực sự chứa ảnh—gọi nó là `WithImages.docx`.
- Một thư mục nơi bạn muốn lưu markdown đầu ra và các ảnh, ví dụ `C:\Projects\MarkdownExport`.
- Không cần thư viện bổ sung; mọi thứ khác được Aspose.Words xử lý.

## Bước 1: Tải tài liệu Word nguồn (điểm khởi đầu để convert word to markdown)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Adjust the path to point at your own .docx file.
        string sourcePath = @"C:\Projects\MarkdownExport\WithImages.docx";

        // Load the document – this is where Aspose.Words parses the Word file.
        Document doc = new Document(sourcePath);
        
        // The rest of the workflow follows…
    }
}
```

*Tại sao điều này quan trọng:* Việc tải tài liệu cho phép chúng ta truy cập vào cây node nội bộ, bao gồm các phần ảnh mà sau này chúng ta cần **export images from docx**. Nếu việc tải thất bại, các bước sau sẽ không chạy, vì vậy hãy kiểm tra lại đường dẫn và quyền truy cập tệp.

## Bước 2: Cấu hình `MarkdownSaveOptions` với callback tùy chỉnh (trái tim của việc tạo thư mục resources)

`ResourceSavingCallback` cho phép chúng ta can thiệp mỗi khi Aspose.Words muốn ghi một tệp ảnh. Trong callback, chúng ta sẽ **create a Resources sub‑folder** và điều chỉnh tham chiếu sao cho markdown được tạo ra sử dụng một *markdown image relative path*.

```csharp
// Inside Main(), after loading the document:
string outputFolder = @"C:\Projects\MarkdownExport";
string resourcesFolder = Path.Combine(outputFolder, "Resources");

// Make sure the folder exists before we start saving anything.
Directory.CreateDirectory(resourcesFolder);

// Set up the Markdown save options.
MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
{
    // Hook that runs for every image resource.
    ResourceSavingCallback = new MyMarkdownResourceCallback(resourcesFolder)
};

// Save the document as Markdown.
string markdownPath = Path.Combine(outputFolder, "Doc.md");
doc.Save(markdownPath, mdOptions);
```

Lưu ý chúng tôi đã truyền `resourcesFolder` vào constructor của callback—điều này giữ cho đường dẫn thư mục linh hoạt và tránh việc hard‑coding chuỗi trong toàn bộ mã.

## Bước 3: Triển khai callback **creates resources folder** và ghi lại đường dẫn

```csharp
/// <summary>
/// Handles image extraction and path rewriting for markdown export.
/// </summary>
class MyMarkdownResourceCallback : IResourceSavingCallback
{
    private readonly string _resourcesFolder;

    public MyMarkdownResourceCallback(string resourcesFolder)
    {
        _resourcesFolder = resourcesFolder;
    }

    public void ResourceSaving(ResourceSavingArgs args)
    {
        // 1️⃣ Build the full file system path where the image will be stored.
        string targetPath = Path.Combine(_resourcesFolder, args.ResourceFileName);
        
        // 2️⃣ Ensure the directory exists (in case Aspose creates sub‑folders).
        Directory.CreateDirectory(Path.GetDirectoryName(targetPath));

        // 3️⃣ Write the image stream to disk.
        using (FileStream fileStream = File.Create(targetPath))
        {
            args.Stream.CopyTo(fileStream);
        }

        // 4️⃣ Update the markdown reference to use a relative path.
        // This is the crucial line that gives us the markdown image relative path.
        args.ResourceFileName = Path.Combine("Resources", args.ResourceFileName);
    }
}
```

*Tại sao cách này hoạt động:* `args.Stream` chứa dữ liệu ảnh thô. Bằng cách sao chép nó vào một tệp trong thư mục `Resources` của chúng ta, chúng ta **export images from docx** một cách an toàn. Sau đó chúng ta thay thế `args.ResourceFileName` bằng một URL tương đối (`Resources/image.png`). Khi Aspose.Words sau này ghi markdown, nó sẽ chèn chính chuỗi đó, mang lại cho chúng ta *markdown image relative path* mong muốn.

## Bước 4: Xác minh Markdown đã tạo (kết quả cuối cùng trông như thế nào)

Mở `Doc.md` trong bất kỳ trình soạn thảo văn bản nào. Bạn sẽ thấy một nội dung tương tự như:

```markdown
# Sample Heading

Here is an inline picture:

![Image 0](Resources/Image_0.png)

And a picture inside a table:

![Image 1](Resources/Image_1.jpg)
```

Phần quan trọng là mỗi tham chiếu ảnh đều trỏ tới `Resources/...` – đó là **markdown image relative path** mà chúng ta đang tìm kiếm.

![markdown image relative path example](example.png "markdown image relative path example")

*Mẹo:* Nếu bạn mở markdown trong một trình xem hỗ trợ liên kết tương đối (xem trước VS Code, GitHub, hoặc một trình tạo site tĩnh), các hình ảnh sẽ hiển thị đúng mà không cần cấu hình thêm.

## Bước 5: Những lỗi thường gặp và mẹo chuyên nghiệp

| Vấn đề | Tại sao xảy ra | Cách khắc phục |
|-------|----------------|---------------|
| Ảnh bị lưu vào thư mục gốc thay vì `Resources` | Callback chưa được gắn hoặc `args.ResourceFileName` chưa được ghi đè. | Kiểm tra lại rằng `ResourceSavingCallback` được thiết lập **trước** khi gọi `doc.Save`. |
| Tên tệp chứa ký tự không hợp lệ | Word đôi khi đặt tên ảnh có dấu cách hoặc ký tự Unicode. | Sử dụng `Path.GetInvalidFileNameChars()` để làm sạch `args.ResourceFileName` trong callback. |
| Tài liệu lớn mất thời gian xử lý lâu | Mỗi ảnh được ghi đồng bộ. | Chuyển sang I/O bất đồng bộ (`await args.Stream.CopyToAsync(fileStream)`) nếu bạn đang dùng .NET 6+ và cần hiệu năng. |
| Đường dẫn tương đối bị hỏng khi markdown được di chuyển | Đường dẫn tương đối với vị trí tệp markdown. | Giữ `Doc.md` và thư mục `Resources` cùng nhau, hoặc điều chỉnh callback để sử dụng tiền tố tương đối khác (ví dụ, `../assets`). |

## Bước 6: Mở rộng giải pháp (nếu bạn cần kiểm soát nhiều hơn?)

- **Multiple output formats:** Thay thế `MarkdownSaveOptions` bằng `HtmlSaveOptions` hoặc `PdfSaveOptions` trong khi vẫn giữ callback giống nhau—Aspose.Words sẽ gọi nó cho mọi ảnh bất kể định dạng.
- **Custom image naming:** Nếu bạn muốn đổi tên ảnh (ví dụ, `figure-01.png`), sửa `args.ResourceFileName` trong callback trước khi ghi tệp.
- **Embedding images as Base64:** Đặt `args.ResourceFileName` thành một data URI (`data:image/png;base64,...`) và bỏ qua việc ghi tệp. Điều này hữu ích cho việc xuất markdown thành một tệp duy nhất.

## Kết luận

Bây giờ bạn đã có một chương trình C# hoàn chỉnh có khả năng **converts Word to markdown**, **extracts images from word**, **creates a resources folder**, và đảm bảo một **markdown image relative path** sạch sẽ cho mọi hình ảnh. Mã nguồn tự chứa, hoạt động với phiên bản Aspose.Words mới nhất, và có thể được đưa vào bất kỳ dự án .NET nào với ít nỗ lực.

Bước tiếp theo? Hãy thử đưa markdown đã tạo vào một trình tạo site tĩnh như Hugo hoặc Jekyll, hoặc thử nghiệm callback để nhúng ảnh trực tiếp dưới dạng chuỗi Base64. Nếu gặp các trường hợp đặc biệt—ví dụ, ảnh SVG hoặc tệp rất lớn—hãy quay lại bảng “Common pitfalls”; một chỉnh sửa nhỏ thường giải quyết được vấn đề.

Chúc lập trình vui vẻ, và mong markdown của bạn luôn trỏ tới đúng thư mục!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}