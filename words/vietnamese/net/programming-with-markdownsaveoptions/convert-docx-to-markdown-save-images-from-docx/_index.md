---
category: general
date: 2026-06-27
description: Chuyển đổi docx sang markdown và lưu ảnh từ docx bằng Aspose.Words. Tìm
  hiểu cách trích xuất ảnh từ tệp Word và xuất tài liệu Word dưới dạng markdown.
draft: false
keywords:
- convert docx to markdown
- save images from docx
- extract images from word file
- export word document as markdown
language: vi
og_description: Chuyển đổi docx sang markdown và lưu ảnh từ docx. Hướng dẫn này chỉ
  cách trích xuất ảnh từ tệp Word và xuất tài liệu Word dưới dạng markdown.
og_title: Chuyển đổi docx sang markdown & lưu ảnh từ docx
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  headline: Convert docx to markdown & save images from docx
  type: TechArticle
- description: Convert docx to markdown and save images from docx using Aspose.Words.
    Learn how to extract images from Word file and export Word document as markdown.
  name: Convert docx to markdown & save images from docx
  steps:
  - name: How the code works
    text: '- **Loading the document** (`new Document(inputPath)`) gives us an in‑memory
      representation of the Word file, complete with all its parts—paragraphs, tables,
      and **images**. - **`MarkdownSaveOptions`** is where the magic happens. By attaching
      a `ResourceSavingCallback`, we gain full control over eve'
  - name: Quick sanity check
    text: '- Does the Markdown file open without errors in VS Code’s preview pane?
      ✅ - Are all pictures displayed when you view the file on GitHub? ✅ - Did the
      `Images` directory contain one file per picture from the original `.docx`? ✅'
  - name: What’s next?
    text: '- **Style the Markdown** – add a front‑matter block for Jekyll or Hugo.
      - **Automate the pipeline** – embed this code in an Azure DevOps or GitHub Action
      step. - **Handle tables and footnotes** – explore other `MarkdownSaveOptions`
      flags like `ExportTableBorderStyles`.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Markdown
- Word
title: Chuyển đổi docx sang markdown & lưu ảnh từ docx
url: /vi/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-save-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Chuyển đổi docx sang markdown & lưu ảnh từ docx

Bạn đã bao giờ tự hỏi làm thế nào **chuyển đổi docx sang markdown** mà không mất các hình ảnh nhúng trong tệp Word của mình chưa? Bạn không đơn độc—các nhà phát triển thường cần một phiên bản Markdown sạch của báo cáo đồng thời vẫn giữ nguyên mọi sơ đồ, logo hoặc ảnh chụp màn hình.

Trong hướng dẫn này, chúng ta sẽ đi qua một ví dụ hoàn chỉnh, sẵn sàng chạy mà **chuyển đổi .docx sang Markdown**, **lưu ảnh từ docx** vào một thư mục bạn chọn, và cho bạn thấy cách **trích xuất ảnh từ tệp Word** bằng thư viện mạnh mẽ Aspose.Words. Khi kết thúc, bạn cũng sẽ biết cách **xuất tài liệu Word dưới dạng markdown** chỉ với một dòng lệnh.

## Những gì bạn cần

- .NET 6+ (hoặc .NET Framework 4.7.2+) đã được cài đặt trên máy  
- Tham chiếu NuGet tới `Aspose.Words` (bản dùng thử miễn phí vẫn hoạt động)  
- Một tệp mẫu `input.docx` chứa ít nhất một hình ảnh  
- Một IDE mà bạn thích—Visual Studio, Rider, hoặc thậm chí VS Code cũng được  

Không cần công cụ bên thứ ba nào khác, không cần các thao tác phức tạp trên dòng lệnh. Chỉ cần mã C# thuần.

## Chuyển đổi docx sang markdown – Tổng quan

Ý tưởng cốt lõi rất đơn giản:

1. Tải tài liệu Word nguồn.  
2. Cho Aspose.Words biết bạn muốn xử lý các tài nguyên bên ngoài (như ảnh) như thế nào.  
3. Lưu tài liệu dưới dạng Markdown, để thư viện thực hiện phần còn lại.

Dưới đây là **chương trình đầy đủ, có thể chạy**. Bạn có thể sao chép‑dán vào một dự án console mới và nhấn `Ctrl+F5`.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.IO;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load the source document that contains images
        // -----------------------------------------------------------------
        string inputPath = Path.Combine("YOUR_DIRECTORY", "input.docx");
        Document doc = new Document(inputPath);

        // -----------------------------------------------------------------
        // Step 2: Configure Markdown save options with a custom callback
        // -----------------------------------------------------------------
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions
        {
            // This callback runs for each external resource (images, CSS, etc.)
            ResourceSavingCallback = (sender, args) =>
            {
                // ---------------------------------------------------------
                // Step 3a: Save images to a custom folder using a unique name
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.Image)
                {
                    string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
                    Directory.CreateDirectory(imageFolder); // ensures folder exists

                    // Use a GUID so we never clash with existing files
                    string uniqueName = Guid.NewGuid().ToString() + args.Extension;
                    args.SavePath = Path.Combine(imageFolder, uniqueName);
                }

                // ---------------------------------------------------------
                // Step 3b: Skip CSS files – they aren't needed for plain Markdown
                // ---------------------------------------------------------
                if (args.ResourceType == ResourceType.CssStyleSheet)
                    args.Cancel = true;
            }
        };

        // -----------------------------------------------------------------
        // Step 4: Export the document to Markdown, applying the options
        // -----------------------------------------------------------------
        string outputPath = Path.Combine("YOUR_DIRECTORY", "output.md");
        doc.Save(outputPath, mdOptions);

        Console.WriteLine("Conversion complete! Markdown saved to " + outputPath);
        Console.WriteLine("Images extracted to " + Path.Combine("YOUR_DIRECTORY", "Images"));
    }
}
```

### Cách mã hoạt động

- **Tải tài liệu** (`new Document(inputPath)`) cung cấp cho chúng ta một biểu diễn trong bộ nhớ của tệp Word, bao gồm tất cả các phần—đoạn văn, bảng và **hình ảnh**.  
- **`MarkdownSaveOptions`** là nơi phép thuật diễn ra. Bằng cách gắn một `ResourceSavingCallback`, chúng ta có toàn quyền kiểm soát mọi tài nguyên bên ngoài mà Aspose.Words cố gắng ghi ra.  
- Trong callback, chúng ta **trích xuất ảnh từ tệp Word** bằng cách kiểm tra `args.ResourceType == ResourceType.Image`. Callback nhận được byte ảnh, phần mở rộng gốc và thuộc tính `SavePath` mà chúng ta đặt thành một thư mục tạo ngay tại thời điểm chạy. Sử dụng `Guid.NewGuid()` đảm bảo tên tệp duy nhất, vì vậy bạn sẽ không vô tình ghi đè các lần chạy trước.  
- Chúng ta **bỏ qua CSS** (`ResourceType.CssStyleSheet`) vì Markdown thuần không cần stylesheet. Điều này giúp đầu ra gọn gàng.  
- Cuối cùng, `doc.Save(outputPath, mdOptions)` ghi tệp Markdown, thay thế các cấu trúc Word bằng các tương đương Markdown (đầu đề trở thành `#`, bảng trở thành các hàng ngăn bằng dấu gạch đứng, v.v.).

## Lưu ảnh từ docx – Chiến lược thư mục tùy chỉnh

Tại sao lại cần một thư mục tùy chỉnh? Hãy tưởng tượng bạn đang tạo tài liệu cho một pipeline CI. Bạn muốn tệp Markdown và các tài sản của nó nằm cạnh nhau trong một bố cục sạch sẽ, có thể tái tạo.

```csharp
string imageFolder = Path.Combine("YOUR_DIRECTORY", "Images");
Directory.CreateDirectory(imageFolder);
```

Một vài **mẹo chuyên nghiệp**:

- **Giữ đường dẫn thư mục tương đối** so với gốc dự án. Như vậy tệp Markdown có thể tham chiếu ảnh bằng liên kết tương đối (`![Alt text](Images/abc123.png)`), hoạt động trên GitHub, GitLab hoặc bất kỳ trình tạo site tĩnh nào.  
- **Nếu bạn cần tên xác định** (ví dụ, cùng một ảnh luôn nhận cùng một tên tệp), thay GUID bằng hàm băm của byte ảnh: `MD5.Create().ComputeHash(args.Data)`. Đó là một thay đổi nhỏ nhưng hữu ích cho việc cache.

## Trích xuất ảnh từ tệp Word – Các trường hợp đặc biệt

1. **Nhiều định dạng ảnh** – Aspose.Words hỗ trợ PNG, JPEG, GIF, BMP và thậm chí SVG. Thuộc tính `args.Extension` đã chứa phần mở rộng đúng, vì vậy bạn không cần đoán.  
2. **Ảnh rất lớn** – Nếu tài liệu nguồn chứa các ảnh độ phân giải cao, các tệp tạo ra có thể khá nặng. Hãy cân nhắc thêm bước nén sau callback, sử dụng `System.Drawing` hoặc `ImageSharp`.  
3. **Ảnh ẩn** – Word có thể lưu ảnh trong header/footer hoặc thậm chí trong textbox. Callback sẽ thấy chúng tất cả, vì vậy bạn sẽ **trích xuất mọi** ảnh, không chỉ những ảnh hiển thị. Nếu bạn chỉ muốn ảnh trong phần thân, hãy thêm bộ lọc dựa trên `args.ImageIndex` hoặc kiểm tra `args.ImageType`.

## Xuất tài liệu Word dưới dạng markdown – Kiểm tra kết quả

Sau khi chạy chương trình, mở `output.md` bằng bất kỳ trình xem Markdown nào. Bạn sẽ thấy một thứ gì đó như:

```markdown
# My Report

Here is an introductory paragraph.

![Image1](Images/3f9c2d1e-7a5b-4c9e-9f6a-2b4e5d6f7a8b.png)

More text follows...
```

Chú ý liên kết ảnh trỏ tới thư mục **Images** mà chúng ta đã tạo. Đó là dấu hiệu của một **xuất tài liệu Word dưới dạng markdown** thành công.

### Kiểm tra nhanh

- Tệp Markdown có mở mà không lỗi trong khung preview của VS Code không? ✅  
- Tất cả các ảnh có hiển thị khi bạn xem tệp trên GitHub không? ✅  
- Thư mục `Images` có chứa một tệp cho mỗi ảnh từ tệp `.docx` gốc không? ✅  

Nếu bất kỳ kiểm tra nào không đạt, hãy kiểm tra lại logic `ResourceSavingCallback` và đảm bảo placeholder `YOUR_DIRECTORY` trỏ tới một vị trí có quyền ghi.

## Những lỗi thường gặp và cách tránh

| Lỗi | Nguyên nhân | Cách khắc phục |
|-----|-------------|----------------|
| **Ảnh không hiển thị** | Callback không bao giờ được gọi vì `ResourceSavingCallback` chưa được gán. | Gán callback **trước** khi gọi `doc.Save`. |
| **Thư mục Images rỗng** | `args.Cancel = true` đã được đặt cho mọi tài nguyên một cách vô tình. | Chỉ hủy CSS (`ResourceType.CssStyleSheet`), để ảnh không bị hủy. |
| **Đường dẫn file quá dài trên Windows** | Sử dụng thư mục lồng sâu cộng với GUID có thể vượt quá 260 ký tự. | Giữ thư mục nông, hoặc bật hỗ trợ đường dẫn dài trong Windows 10+. |
| **Tên ảnh trùng lặp** | Dùng `DateTime.Now.Ticks` thay cho GUID có thể gây trùng khi vòng lặp nhanh. | Tiếp tục dùng `Guid.NewGuid()` để đảm bảo tính duy nhất. |

## Kết luận

Chúng ta vừa **chuyển đổi docx sang markdown**, **lưu ảnh từ docx**, và minh họa cách **trích xuất ảnh từ tệp Word** đồng thời **xuất tài liệu Word dưới dạng markdown** một cách sạch sẽ, có thể lặp lại. Toàn bộ quá trình dựa vào `ResourceSavingCallback` của Aspose.Words, cho phép bạn kiểm soát chi tiết mọi tài nguyên bên ngoài.

### Bước tiếp theo?

- **Trang trí Markdown** – thêm block front‑matter cho Jekyll hoặc Hugo.  
- **Tự động hoá pipeline** – nhúng đoạn mã này vào bước Azure DevOps hoặc GitHub Action.  
- **Xử lý bảng và chú thích** – khám phá các flag khác của `MarkdownSaveOptions` như `ExportTableBorderStyles`.  

Bạn có thể tùy chỉnh cấu trúc thư mục, thêm nén ảnh, hoặc thậm chí chuyển đổi sang định dạng HTML bằng cách thay `MarkdownSaveOptions` bằng `HtmlSaveOptions`. Khi đã có nền tảng vững chắc cho **convert docx to markdown**, khả năng chỉ còn là giới hạn của bạn.

Chúc lập trình vui vẻ, và mong tài liệu của bạn luôn đẹp **và** máy‑đọc được!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây liên quan chặt chẽ và mở rộng các kỹ thuật đã trình bày trong bài này. Mỗi tài nguyên đều bao gồm mã mẫu đầy đủ và giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Save Word Images – Convert Word to Markdown with Aspose](/words/english/net/programming-with-markdownsaveoptions/save-word-images-convert-word-to-markdown-with-aspose/)
- [Convert Word to Markdown – Embed Images as Base64](/words/english/net/programming-with-markdownsaveoptions/convert-word-to-markdown-embed-images-as-base64/)
- [How to Rename Images When Converting DOCX to Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}