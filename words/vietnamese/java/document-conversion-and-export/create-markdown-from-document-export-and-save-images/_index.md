---
category: general
date: 2026-02-18
description: Tạo markdown từ tài liệu với các bước dễ dàng để xuất tài liệu sang markdown
  và lưu hình ảnh vào thư mục con. Tìm hiểu cách lưu tài liệu dưới dạng markdown trong
  C#.
draft: false
keywords:
- create markdown from document
- export document to markdown
- save document as markdown
- save images to subfolder
language: vi
og_description: Tạo markdown từ tài liệu trong C# và học cách xuất tài liệu sang markdown
  đồng thời lưu hình ảnh vào thư mục con. Thực hiện theo hướng dẫn từng bước.
og_title: Tạo markdown từ tài liệu – Xuất và lưu hình ảnh
tags:
- C#
- Aspose.Words
- Markdown export
title: Tạo markdown từ tài liệu – Xuất và lưu hình ảnh
url: /vi/java/document-conversion-and-export/create-markdown-from-document-export-and-save-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tạo markdown từ tài liệu – Xuất và lưu ảnh

Bạn đã bao giờ **tạo markdown từ tài liệu** nhưng không biết làm sao để giữ các hình ảnh nhúng gọn gàng? Bạn không cô đơn. Trong nhiều dự án, chúng ta tạo báo cáo, hướng dẫn, hoặc bản nháp blog một cách tự động, và điều cuối cùng chúng ta muốn là một đống các tệp ảnh rải rác khắp thư mục đầu ra.  

Trong hướng dẫn này, chúng ta sẽ đi qua một giải pháp hoàn chỉnh, sẵn sàng chạy để **xuất tài liệu ra markdown**, lưu mọi ảnh vào một thư mục con *md‑resources*, và cuối cùng **lưu tài liệu dưới dạng markdown** bằng API Aspose.Words for .NET. Khi kết thúc, bạn sẽ có một phương thức duy nhất có thể chèn vào bất kỳ dự án C# nào, cùng với một vài mẹo xử lý các trường hợp đặc biệt.

> **Nhìn nhanh:**  
> • Cấu hình `MarkdownSaveOptions`  
> • Cung cấp một `IResourceSavingCallback` để chuyển hướng ảnh vào thư mục con  
> • Gọi `Document.Save` với các tùy chọn đã cấu hình  

Nếu bạn tò mò vì sao chúng tôi chọn callback thay vì xử lý sau, hãy tiếp tục đọc – lý do sẽ được giải thích từng bước.

---

## Yêu cầu trước

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.7+)  
- Aspose.Words for .NET (gói NuGet `Aspose.Words`)  
- Một đối tượng `Document` nguồn (có thể là .docx, .pdf, .rtf, v.v.)  

Không cần thư viện bổ sung nào; API callback đã được tích hợp trong Aspose.Words.

---

## Bước 1: Tạo markdown từ tài liệu – cấu hình tùy chọn lưu

Điều đầu tiên chúng ta làm là khởi tạo `MarkdownSaveOptions`. Đối tượng này chỉ cho Aspose.Words cách thực hiện chuyển đổi, chẳng hạn như flavor Markdown nào sẽ dùng, có nhúng ảnh dưới dạng Base64 không, và nơi sẽ lưu các tệp được tạo.

```csharp
// Step 1: Initialize Markdown save options
var markdownSaveOptions = new Aspose.Words.Saving.MarkdownSaveOptions();
```

> **Tại sao điều này quan trọng:**  
> Nếu không tạo rõ ràng `MarkdownSaveOptions`, thư viện sẽ quay lại cài đặt mặc định và nhúng ảnh trực tiếp vào tệp Markdown dưới dạng chuỗi Base64. Điều đó làm tệp trở nên khổng lồ và mất đi mục đích có một thư mục *images* sạch sẽ.

---

## Bước 2: Xuất tài liệu ra markdown và định nghĩa cách xử lý tài nguyên

Bây giờ chúng ta chỉ cho bộ lưu **điểm nào** sẽ đặt mỗi ảnh. Giao diện `IResourceSavingCallback` cung cấp một hook được kích hoạt cho mỗi tài nguyên (ảnh, SVG, v.v.) được phát hiện trong quá trình xuất. Trong callback, chúng ta:

1. Đảm bảo thư mục đích tồn tại (`md-resources/`).  
2. Đặt `OutputFileName` thành thư mục cộng với tên tài nguyên gốc.  

```csharp
// Step 2: Hook into the resource‑saving pipeline
markdownSaveOptions.ResourceSavingCallback = new Aspose.Words.Saving.IResourceSavingCallback(
    (args) =>
    {
        // All images will be placed in "md-resources" relative to the output .md file
        const string folder = "md-resources/";
        Directory.CreateDirectory(folder);          // Create folder if it doesn’t exist

        // Preserve the original file name (e.g., image001.png) but prepend the folder path
        args.OutputFileName = Path.Combine(folder, args.ResourceFileName);

        // Optional: you could also change the format here (e.g., convert BMP to PNG)
        // args.ResourceFileName = Path.ChangeExtension(args.ResourceFileName, ".png");
    });
```

> **Câu hỏi thường gặp:** *Nếu tôi muốn nhúng ảnh thay vì lưu chúng thì sao?*  
> Chỉ cần bỏ qua callback hoặc đặt `args.OutputFileName = null;` – bộ lưu sẽ tự động nhúng ảnh dưới dạng chuỗi Base64.

> **Trường hợp đặc biệt:** Một số tài liệu cũ có tên ảnh trùng lặp. Callback ở trên sẽ ghi đè tệp trước. Để tránh, bạn có thể thêm GUID:

```csharp
args.OutputFileName = Path.Combine(folder,
    $"{Path.GetFileNameWithoutExtension(args.ResourceFileName)}_{Guid.NewGuid()}{Path.GetExtension(args.ResourceFileName)}");
```

---

## Bước 3: Lưu tài liệu dưới dạng markdown và kiểm tra ảnh đã lưu

Với các tùy chọn đã được cấu hình đầy đủ, lời gọi cuối cùng chỉ là một dòng mã ghi tệp Markdown và các ảnh liên quan ra đĩa.

```csharp
// Step 3: Perform the actual export
string outputPath = @"C:\Exports\MyReport.md";
doc.Save(outputPath, markdownSaveOptions);
```

Nếu mọi thứ diễn ra suôn sẻ, bạn sẽ thấy:

- `MyReport.md` – bản đại diện Markdown của tài liệu nguồn.  
- `md-resources/` – một thư mục nằm cạnh tệp .md chứa mọi ảnh đã trích xuất (ví dụ: `image001.png`, `image002.jpg`).  

**Đoạn mã Markdown mẫu** (tự động tạo bởi Aspose.Words):

```markdown
# Sample Report

Here is an introductory paragraph.

![Sample image](md-resources/image001.png)

More text follows...
```

> **Mẹo chuyên nghiệp:** Mở tệp `.md` đã tạo trong VS Code hoặc bất kỳ trình xem Markdown nào; các ảnh sẽ hiển thị ngay lập tức vì đường dẫn tương đối khớp với cấu trúc thư mục.

---

## Ví dụ đầy đủ, có thể chạy

Dưới đây là một chương trình console tự chứa, bạn có thể dán vào một dự án .NET mới và chạy. Nó tạo một tài liệu Word đơn giản, chèn một ảnh, và sau đó **tạo markdown từ tài liệu** đồng thời lưu ảnh vào thư mục con.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a sample Word document with an image
        var doc = new Document();
        var builder = new DocumentBuilder(doc);
        builder.Writeln("Hello, this is a test document.");
        builder.InsertImage("sample-image.png"); // Ensure this file exists next to exe

        // 2️⃣ Configure markdown export options (see Step 1 & 2 above)
        var markdownOptions = new MarkdownSaveOptions();
        markdownOptions.ResourceSavingCallback = new IResourceSavingCallback(
            (args) =>
            {
                const string folder = "md-resources/";
                Directory.CreateDirectory(folder);
                args.OutputFileName = Path.Combine(folder, args.ResourceFileName);
            });

        // 3️⃣ Save as markdown (Step 3)
        string outputFolder = Path.Combine(Environment.CurrentDirectory, "output");
        Directory.CreateDirectory(outputFolder);
        string markdownPath = Path.Combine(outputFolder, "ExportedDoc.md");
        doc.Save(markdownPath, markdownOptions);

        Console.WriteLine($"✅ Markdown saved to: {markdownPath}");
        Console.WriteLine("📂 Images saved in: md-resources/");
    }
}
```

**Kết quả bạn sẽ thấy** sau khi chạy:

```
✅ Markdown saved to: C:\MyProject\output\ExportedDoc.md
📂 Images saved in: md-resources/
```

Mở `ExportedDoc.md` – tham chiếu ảnh sẽ chỉ tới `md-resources/sample-image.png`, và hình sẽ hiển thị đúng trong bất kỳ trình xem Markdown nào.

---

## Các biến thể thường gặp

| Kịch bản | Cách điều chỉnh mã |
|----------|----------------------|
| **Bỏ qua xuất ảnh** (nhúng dưới dạng Base64) | Loại bỏ hoàn toàn `ResourceSavingCallback`, hoặc đặt `args.OutputFileName = null;` trong callback. |
| **Thay đổi định dạng ảnh** (ví dụ, tất cả PNG) | Trong callback, sửa `args.ResourceFileName` và tùy chọn chuyển đổi luồng trước khi ghi. |
| **Tên thư mục tùy chỉnh** | Thay `"md-resources/"` bằng bất kỳ đường dẫn tương đối hoặc tuyệt đối nào bạn muốn. |
| **Nhiều tài liệu trong một lô** | Lặp qua một tập hợp các đối tượng `Document`, tái sử dụng cùng một thể hiện `MarkdownSaveOptions` (chỉ cần chắc chắn thư mục được xóa hoặc đặt tên duy nhất cho mỗi lần chạy). |

---

## Kết luận

Chúng ta vừa chỉ cho bạn **cách tạo markdown từ tài liệu**, **xuất tài liệu ra markdown**, và **lưu ảnh vào thư mục con** bằng một cách tiếp cận sạch sẽ, dựa trên callback. Những điểm quan trọng cần nhớ:

- Sử dụng `MarkdownSaveOptions` để kiểm soát chi tiết quá trình xuất.  
- Triển khai `IResourceSavingCallback` để đưa ảnh vào một thư mục riêng, giữ cho Markdown của bạn gọn gàng.  
- Mẫu tương tự cũng áp dụng cho các loại tài nguyên khác (SVG, âm thanh) – chỉ cần kiểm tra `args.ResourceType`.  

Tiếp theo, bạn có thể khám phá **lưu tài liệu dưới dạng markdown** với các kiểu tiêu đề tùy chỉnh, hoặc tích hợp quy trình này vào một ASP.NET Web API trả về file ZIP chứa tệp `.md` và các tài nguyên của nó. Dù chọn cách nào, các khối xây dựng đã có trong tay bạn.

Có câu hỏi, hoặc phát hiện trường hợp đặc biệt mà chúng tôi chưa đề cập? Hãy để lại bình luận bên dưới, và chúc bạn lập trình vui vẻ!

---

![tạo markdown từ tài liệu ví dụ](placeholder.png "tạo markdown từ tài liệu ví dụ")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}