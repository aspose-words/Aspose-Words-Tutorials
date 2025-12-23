---
category: general
date: 2025-12-23
description: Học cách khôi phục các tệp docx bị hỏng, sử dụng chế độ khôi phục, xuất
  các phương trình sang LaTeX và tạo tên ảnh duy nhất trong C#. Mã từng bước kèm giải
  thích.
draft: false
keywords:
- recover corrupted docx
- how to use recovery mode
- export equations to latex
- generate unique image names
language: vi
og_description: Khôi phục các tệp docx bị hỏng, sử dụng chế độ khôi phục, xuất các
  phương trình sang LaTeX và tạo tên hình ảnh duy nhất với Aspose.Words trong C#.
og_title: Khôi phục docx bị hỏng – Hướng dẫn C# toàn diện
tags:
- Aspose.Words
- C#
- Document Recovery
title: khôi phục docx bị hỏng – Hướng dẫn đầy đủ để sửa chữa, xuất công thức sang
  LaTeX & tạo tên ảnh duy nhất
url: /vi/net/programming-with-officemath/recover-corrupted-docx-full-guide-to-repair-export-math-to-l/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# khôi phục docx bị hỏng – Hướng dẫn đầy đủ để sửa, xuất công thức sang LaTeX & tạo tên ảnh duy nhất

Bạn đã bao giờ mở một **.docx** mà không tải được vì nó bị hỏng chưa? Bạn không phải là người duy nhất. Trong nhiều dự án thực tế, một tệp Word bị hỏng có thể làm dừng toàn bộ quy trình làm việc, nhưng tin tốt là bạn có thể **khôi phục các tệp docx bị hỏng** một cách lập trình.  

Trong tutorial này chúng tôi sẽ hướng dẫn chi tiết các bước **khôi phục docx bị hỏng**, chỉ ra **cách sử dụng chế độ recovery**, trình diễn **xuất công thức sang LaTeX**, và cuối cùng **tạo tên ảnh duy nhất** khi lưu dưới dạng Markdown. Khi hoàn thành, bạn sẽ có một chương trình C# duy nhất, có thể chạy được, thực hiện tất cả các nhiệm vụ này mà không gặp trục trặc.

## Yêu cầu

- .NET 6 hoặc mới hơn (mã cũng hoạt động với .NET Framework 4.6+).  
- Aspose.Words for .NET (bản dùng thử miễn phí hoặc bản có giấy phép). Cài đặt qua NuGet:

```bash
dotnet add package Aspose.Words
```

- Kiến thức cơ bản về C# và I/O file.  
- Một tệp `corrupt.docx` bị hỏng để thử nghiệm (bạn có thể mô phỏng hỏng bằng cách cắt ngắn một tệp hợp lệ).

> **Mẹo chuyên nghiệp:** Giữ một bản sao lưu của tệp gốc trước khi bắt đầu — quá trình khôi phục sẽ gây hủy dữ liệu chỉ khi bạn ghi đè lên nguồn.

## Bước  Khôi phục DOCX bị hỏng bằng Recovery Mode

Điều đầu tiên chúng ta cần làm là thông báo cho Aspose.Words rằng tệp đầu vào có thể bị hỏng. Đây là lúc **cách sử dụng chế độ recovery** trở nên quan trọng.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // Step 1: Load a possibly corrupted document using recovery mode
        // -----------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded successfully – recovery mode applied.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
            return;
        }

        // ---------------------------------------------------------------
        // Subsequent steps go here...
        // ---------------------------------------------------------------
    }
}
```

**Tại sao điều này quan trọng:**  
Khi `RecoveryMode.Recover` được bật, Aspose.Words sẽ cố gắng xây dựng lại cây tài liệu nội bộ, bỏ qua các phần không đọc được trong khi giữ lại càng nhiều nội dung càng tốt. Nếu không bật, hàm khởi tạo `Document` sẽ ném ra ngoại lệ và bạn sẽ mất cơ hội cứu dữ liệu.

> **Nếu tệp không thể sửa được?**  
> Thư viện vẫn sẽ trả về một đối tượng `Document`, nhưng một số nút có thể bị thiếu. Bạn có thể kiểm tra `doc.GetChildNodes(NodeType.Any, true).Count` để xem có bao nhiêu phần tử còn lại.

## Bước 2 – Xuất công thức Office Math sang LaTeX khi lưu dưới dạng Markdown

Nhiều tài liệu kỹ thuật chứa các công thức được viết bằng Office Math. Nếu bạn cần các công thức này ở dạng LaTeX — ví dụ để đăng trên blog khoa học — bạn có thể yêu cầu Aspose.Words thực hiện chuyển đổi.

```csharp
        // -----------------------------------------------------------------
        // Step 2: Export Office Math equations to LaTeX in a Markdown file
        // -----------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };

        string markdownPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(markdownPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown with LaTeX equations saved to: {markdownPath}");
```

**Cách hoạt động:**  
`OfficeMathExportMode.LaTeX` chỉ cho bộ lưu thay thế mỗi nút `OfficeMath` bằng biểu diễn LaTeX của nó, được bao bọc trong `$…$` (inline) hoặc `$$…$$` (display). Tệp Markdown kết quả có thể được đưa thẳng vào các công cụ tạo site tĩnh như Hugo hoặc Jekyll.

> **Trường hợp đặc biệt:** Nếu tài liệu gốc chứa các đối tượng phương trình phức tạp (ví dụ ma trận), việc chuyển đổi sang LaTeX có thể tạo ra đầu ra đa dòng. Hãy kiểm tra tệp `.md` được tạo để đảm bảo đáp ứng yêu cầu định dạng của bạn.

## Bước 3 – Lưu tài liệu dưới dạng PDF đồng thời kiểm soát thẻ cho các hình dạng nổi

Đôi khi bạn cần một phiên bản PDF của cùng một tài liệu, nhưng cũng quan tâm đến cách các hình dạng nổi (hình ảnh, textbox) được gắn thẻ để hỗ trợ truy cập. Cờ `ExportFloatingShapesAsInlineTag` cho phép bạn kiểm soát điều này.

```csharp
        // -----------------------------------------------------------------
        // Step 3: Save as PDF with custom floating‑shape tagging
        // -----------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true // true → <Figure>, false → <Div>
        };

        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved with inline tags to: {pdfPath}");
```

**Tại sao cần bật/tắt cờ này?**  
- `true` → Các hình dạng nổi sẽ trở thành thẻ `<Figure>`, mà nhiều trình đọc màn hình coi là hình ảnh riêng biệt có chú thích.  
- `false` → Các hình dạng sẽ được bao bọc trong thẻ `<Div>` chung, có thể bị các công nghệ hỗ trợ bỏ qua. Hãy chọn dựa trên yêu cầu khả năng truy cập của bạn.

## Bước 4 – Xuất sang Markdown với xử lý ảnh tùy chỉnh (tạo tên ảnh duy nhất)

Khi bạn lưu tài liệu Word sang Markdown, tất cả các ảnh nhúng sẽ được ghi ra đĩa. Mặc định chúng nhận tên tệp gốc, điều này có thể gây xung đột nếu bạn xử lý nhiều tài liệu trong cùng một thư mục. Hãy can thiệp vào quá trình lưu và **tự động tạo tên ảnh duy nhất**.

```csharp
        // -----------------------------------------------------------------
        // Step 4: Export to Markdown with custom image naming
        // -----------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                // Create a sub‑folder for markdown images if it doesn't exist
                string imageFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imageFolder);

                // Build a GUID‑based filename preserving the original extension
                string uniqueName = Guid.NewGuid().ToString() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imageFolder, uniqueName);
            }
        };

        string markdownPath2 = @"YOUR_DIRECTORY\out2.md";
        doc.Save(markdownPath2, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with uniquely named images saved to: {markdownPath2}");
```

**Điều gì đang diễn ra phía sau?**  
`ResourceSavingCallback` được gọi cho mỗi tài nguyên bên ngoài (ảnh, SVG, v.v.) trong quá trình lưu. Bằng cách trả về một đường dẫn đầy đủ, bạn quyết định nơi tệp sẽ được lưu và tên của nó. GUID đảm bảo **tạo tên ảnh duy nhất** mà không cần quản lý thủ công.

> **Mẹo:** Nếu bạn muốn một quy tắc đặt tên có thể dự đoán được (ví dụ dựa trên thuộc tính alt của ảnh), thay `Guid.NewGuid()` bằng hàm băm của `resourceInfo.Name`.

## Ví dụ hoàn chỉnh hoạt động

Kết hợp tất cả lại, đây là chương trình đầy đủ mà bạn có thể sao chép‑dán vào một ứng dụng console:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // -------------------------------------------------------------
        // Load the possibly corrupted document (Recovery Mode)
        // -------------------------------------------------------------
        var loadOptions = new LoadOptions { RecoveryMode = RecoveryMode.Recover };
        Document doc;

        try
        {
            doc = new Document(@"YOUR_DIRECTORY\corrupt.docx", loadOptions);
            Console.WriteLine("✅ Document loaded with recovery mode.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Unable to load document: {ex.Message}");
            return;
        }

        // -------------------------------------------------------------
        // Export equations to LaTeX in Markdown
        // -------------------------------------------------------------
        var markdownMathOptions = new MarkdownSaveOptions
        {
            OfficeMathExportMode = OfficeMathExportMode.LaTeX
        };
        string mdMathPath = @"YOUR_DIRECTORY\out.md";
        doc.Save(mdMathPath, markdownMathOptions);
        Console.WriteLine($"✅ Markdown (LaTeX) saved: {mdMathPath}");

        // -------------------------------------------------------------
        // Save as PDF with inline floating‑shape tags
        // -------------------------------------------------------------
        var pdfOptions = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true
        };
        string pdfPath = @"YOUR_DIRECTORY\out.pdf";
        doc.Save(pdfPath, pdfOptions);
        Console.WriteLine($"✅ PDF saved: {pdfPath}");

        // -------------------------------------------------------------
        // Export Markdown with unique image names
        // -------------------------------------------------------------
        var markdownImageOptions = new MarkdownSaveOptions
        {
            ResourceSavingCallback = resourceInfo =>
            {
                string imgFolder = @"YOUR_DIRECTORY\md_images";
                Directory.CreateDirectory(imgFolder);
                string uniqueFile = Guid.NewGuid() + Path.GetExtension(resourceInfo.Name);
                return Path.Combine(imgFolder, uniqueFile);
            }
        };
        string mdImgPath = @"YOUR_DIRECTORY\out2.md";
        doc.Save(mdImgPath, markdownImageOptions);
        Console.WriteLine($"✅ Markdown with unique images saved: {mdImgPath}");
    }
}
```

### Kết quả mong đợi

Chạy chương trình sẽ in ra các thông báo console tương tự:

```
✅ Document loaded with recovery mode.
✅ Markdown (LaTeX) saved: YOUR_DIRECTORY\out.md
✅ PDF saved: YOUR_DIRECTORY\out.pdf
✅ Markdown with unique images saved: YOUR_DIRECTORY\out2.md
```

Bạn sẽ thấy ba tệp:

| Tệp | Mục đích |
|------|---------|
| `out.md` | Markdown trong đó mọi công thức Office Math xuất hiện dưới dạng LaTeX (`$…$` hoặc `$$…$$`). |
| `out.pdf` | Phiên bản PDF với các hình dạng nổi được gắn thẻ `<Figure>` để tăng khả năng truy cập. |
| `out2.md` + `md_images\*` | Markdown cộng với một thư mục chứa các tệp ảnh có tên duy nhất (dựa trên GUID). |

## Câu hỏi thường gặp & Trường hợp đặc biệt

| Câu hỏi | Trả lời |
|----------|--------|
| **Nếu tệp bị hỏng không có nội dung có thể khôi phục?** | Aspose.Words vẫn sẽ trả về một đối tượng `Document`, nhưng có thể rỗng. Hãy kiểm tra `doc.GetChildNodes(NodeType.Paragraph, true).Count` trước khi tiếp tục. |
| **Tôi có thể thay đổi ký tự phân cách LaTeX không?** | Có — đặt `markdownMathOptions.MathDelimiter = "$$"` để buộc sử dụng ký tự phân cách dạng hiển thị. |
| **Có cần giải phóng đối tượng `Document` không?** | Lớp `Document` triển khai `IDisposable`. Đặt nó trong khối `using` nếu bạn xử lý nhiều tệp để giải phóng tài nguyên gốc kịp thời. |
| **Làm sao giữ nguyên tên ảnh gốc?** | Trả về `Path.Combine(imageFolder, resourceInfo.Name)` trong callback. Chỉ cần nhớ rủi ro xung đột tên. |
| **Phương pháp GUID có an toàn cho kho lưu trữ có phiên bản không?** | GUID ổn định qua các lần chạy, nhưng không dễ đọc cho con người. Nếu cần tên có thể tái tạo, hãy băm tên gốc cộng với một “salt” chung cho dự án. |

## Kết luận

Chúng tôi đã chỉ cho bạn cách **khôi phục các tệp docx bị hỏng**, trình bày **cách sử dụng

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}