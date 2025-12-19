---
category: general
date: 2025-12-19
description: Hướng dẫn markdown với các công thức LaTeX – học cách chuyển đổi DOCX
  sang Markdown, xuất công thức sang LaTeX và lưu hình ảnh vào thư mục với tên duy
  nhất bằng Aspose.Words trong C#.
draft: false
keywords:
- markdown with latex equations
- convert docx to markdown
- save images to folder
- export equations to latex
- generate unique image names
language: vi
og_description: Hướng dẫn markdown với các phương trình LaTeX cho thấy cách chuyển
  đổi DOCX sang markdown, xuất các phương trình sang LaTeX và tạo tên hình ảnh duy
  nhất cho các hình ảnh đã lưu.
og_title: Markdown với các phương trình LaTeX – Hướng dẫn chuyển đổi đầy đủ C#
tags:
- Aspose.Words
- C#
- Markdown
- LaTeX
title: 'markdown với các công thức latex: Chuyển DOCX sang Markdown và Xuất hình ảnh'
url: /vi/net/programming-with-markdownsaveoptions/markdown-with-latex-equations-convert-docx-to-markdown-and-e/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# markdown với các phương trình latex: Chuyển DOCX sang Markdown và Xuất Hình Ảnh

Bạn đã bao giờ cần **markdown with latex equations** nhưng không chắc làm sao để lấy chúng ra từ một tệp Word? Bạn không phải là người duy nhất—nhiều nhà phát triển gặp phải vấn đề này khi chuyển tài liệu từ Office sang các trình tạo trang tĩnh.

Trong tutorial này, chúng ta sẽ đi qua một giải pháp hoàn chỉnh, từ đầu đến cuối, **chuyển docx sang markdown**, **xuất các phương trình ra latex**, và **lưu hình ảnh vào thư mục** với logic **tạo tên hình ảnh duy nhất**, tất cả đều sử dụng Aspose.Words cho .NET.

Khi hoàn thành, bạn sẽ có một chương trình C# sẵn sàng chạy, tạo ra các tệp Markdown sạch sẽ, công thức LaTeX sẵn sàng và một thư mục hình ảnh gọn gàng—không cần sao chép‑dán thủ công.

## Những gì bạn cần

- .NET 6 (hoặc bất kỳ runtime .NET hiện đại nào)  
- Aspose.Words cho .NET 23.10 trở lên (gói NuGet `Aspose.Words`)  
- Một tệp mẫu `input.docx` chứa văn bản thường, đối tượng Office Math và một vài hình ảnh  
- Một IDE mà bạn thích (Visual Studio, Rider, hoặc VS Code)  

Đó là tất cả. Không cần thư viện phụ, không cần công cụ dòng lệnh rắc rối—chỉ cần C# thuần.

## Bước 1: Tải tài liệu một cách an toàn (Recovery Mode)

Khi bạn làm việc với các tệp có thể đã được chỉnh sửa bởi nhiều người, nguy cơ hỏng dữ liệu là thực tế. Aspose.Words cho phép bạn bật *RecoveryMode* để bộ tải cố gắng sửa các phần bị hỏng thay vì ném ra ngoại lệ.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // Load the document with recovery mode – this handles possible corruption.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);
```

**Tại sao điều này quan trọng:**  
Nếu tệp nguồn chứa các nút XML lạc lõng hoặc luồng hình ảnh bị hỏng, chế độ khôi phục vẫn sẽ cung cấp cho bạn một đối tượng `Document` có thể sử dụng. Bỏ qua bước này có thể gây ra lỗi nghiêm trọng, đặc biệt trong các pipeline CI nơi bạn không kiểm soát mọi lần tải lên.

> **Mẹo chuyên nghiệp:** Khi xử lý hàng loạt, hãy bọc việc tải trong một `try/catch` và ghi lại bất kỳ `DocumentCorruptedException` nào để kiểm tra sau.

## Bước 2: Chuyển DOCX sang Markdown với các Phương trình LaTeX

Bây giờ là phần trọng tâm của tutorial: chúng ta muốn **markdown with latex equations**. `MarkdownSaveOptions` của Aspose.Words cho phép bạn chỉ định `OfficeMathExportMode.LaTeX`, chuyển mỗi đối tượng Office Math thành một chuỗi LaTeX được bao quanh bởi `$…$` hoặc `$$…$$`.

```csharp
        // Export Office Math equations to LaTeX while saving as Markdown.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);
```

Kết quả `output_math.md` sẽ trông giống như sau:

```markdown
Here is an inline equation $E = mc^2$ inside a sentence.

And a displayed equation:

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$
```

**Lý do bạn muốn làm như vậy:**  
Hầu hết các trình tạo trang tĩnh (Hugo, Jekyll, MkDocs) đã hiểu các dấu phân cách LaTeX khi bạn bật plugin MathJax hoặc KaTeX. Bằng cách xuất trực tiếp sang LaTeX, bạn tránh được bước xử lý hậu kỳ mà thường đòi hỏi các hack regex.

### Các trường hợp đặc biệt

- **Phương trình phức tạp:** Các cấu trúc lồng nhau sâu vẫn được hiển thị đúng, nhưng bạn có thể cần tăng giới hạn bộ nhớ của `MathRenderer` nếu gặp `OutOfMemoryException`.  
- **Nội dung hỗn hợp:** Nếu một đoạn văn chứa cả văn bản thường và một phương trình, Aspose.Words sẽ tự động tách chúng, giữ nguyên markdown xung quanh.

## Bước 3: Lưu Hình ảnh vào Thư mục với Tên Độc Nhất

Nếu tài liệu Word của bạn chứa hình ảnh, bạn có thể muốn chúng dưới dạng các tệp hình ảnh riêng mà markdown có thể tham chiếu. `ResourceSavingCallback` trên `MarkdownSaveOptions` cho phép bạn kiểm soát hoàn toàn cách mỗi hình ảnh được ghi.

```csharp
        // Customize image handling during Markdown export.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                // Generate a unique file name for each image.
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);

                // Ensure the Images folder exists.
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);

                // Save the image to the file system.
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);
```

**Markdown hiện tại sẽ trông như thế nào:**

```markdown
![Image description](Images/img_3f9c2a1e-7b5d-4c8f-9d6e-2b5c7a9e1f0a.png)
```

**Tại sao phải tạo tên duy nhất?**  
Nếu cùng một hình ảnh xuất hiện nhiều lần, việc dùng tên gốc sẽ gây ghi đè. Tên dựa trên GUID đảm bảo mỗi tệp là duy nhất, rất hữu ích khi bạn chạy chuyển đổi trong các công việc song song.

### Mẹo & Lưu ý

- **Hiệu năng:** Tạo GUID cho mỗi hình ảnh chỉ thêm một chút overhead, nhưng nếu bạn xử lý hàng ngàn hình ảnh, bạn có thể chuyển sang một hàm băm xác định (ví dụ, SHA‑256 của byte hình ảnh).  
- **Định dạng tệp:** `resource.Save` ghi hình ảnh ở định dạng gốc. Nếu bạn muốn tất cả đều là PNG, thay `resource.Save(imageFile);` bằng `resource.Save(imageFile, ImageSaveOptions.CreateSaveOptions(SaveFormat.Png));`.

## Bước 4: Xuất PDF với Các Đối tượng Inline (Tùy chọn)

Đôi khi bạn vẫn cần một phiên bản PDF của cùng tài liệu, có thể cho mục đích pháp lý. Thiết lập `ExportFloatingShapesAsInlineTag` giữ các đối tượng nổi (như text box) trong PDF dưới dạng thẻ inline, bảo toàn độ chính xác bố cục.

```csharp
        // Save the document as PDF, exporting floating shapes as inline tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

Bạn có thể bỏ qua bước này nếu không cần xuất PDF—không có gì bị hỏng nếu bạn không thực hiện.

## Ví dụ Hoàn chỉnh (Tất cả các Bước Kết hợp)

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào một ứng dụng console. Nhớ thay `YOUR_DIRECTORY` bằng đường dẫn tuyệt đối hoặc tương đối thực tế.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class DocxToMarkdown
{
    static void Main()
    {
        // 1️⃣ Load with recovery mode.
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc = new Document(@"YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ Export markdown with LaTeX equations.
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        doc.Save(@"YOUR_DIRECTORY/output_math.md", markdownMathOptions);

        // 3️⃣ Save images to a folder, using unique GUID names.
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = (resource, stream) =>
            {
                string imageFileName = $"img_{Guid.NewGuid()}.png";
                string imagePath = Path.Combine(@"YOUR_DIRECTORY/Images", imageFileName);
                Directory.CreateDirectory(Path.GetDirectoryName(imagePath)!);
                using var imageFile = File.Create(imagePath);
                resource.Save(imageFile);
            }
        };
        doc.Save(@"YOUR_DIRECTORY/output_images.md", markdownImageOptions);

        // 4️⃣ (Optional) Export PDF with inline shape tags.
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        doc.Save(@"YOUR_DIRECTORY/output_shapes.pdf", pdfOptions);
    }
}
```

Chạy chương trình này sẽ tạo ra ba tệp:

| Tệp | Mục đích |
|------|---------|
| `output_math.md` | Markdown chứa các phương trình đã sẵn sàng cho LaTeX |
| `output_images.md` | Markdown với các liên kết hình ảnh trỏ tới PNG có tên duy nhất |
| `output_shapes.pdf` | Phiên bản PDF bảo toàn các hình dạng nổi dưới dạng thẻ inline (tùy chọn) |

## Kết luận

Bạn đã có một pipeline **markdown with latex equations** có khả năng **chuyển docx sang markdown**, **xuất phương trình ra latex**, và **lưu hình ảnh vào thư mục** đồng thời **tạo tên hình ảnh duy nhất** cho mỗi ảnh. Cách tiếp cận này hoàn toàn tự chứa, hoạt động với bất kỳ dự án .NET hiện đại nào, và chỉ yêu cầu gói NuGet Aspose.Words.

Tiếp theo gì? Hãy thử đưa markdown đã tạo vào một trình tạo trang tĩnh như Hugo, bật MathJax, và xem tài liệu của bạn biến đổi từ định dạng Office kín đáo sang một trang web đẹp mắt, sẵn sàng. Cần bảng? Aspose.Words cũng hỗ trợ `MarkdownSaveOptions.ExportTableAsHtml`, vì vậy bạn có thể giữ nguyên các bố cục phức tạp.

If

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}