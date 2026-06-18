---
category: general
date: 2026-06-17
description: Xử lý việc thay thế phông chữ trong Aspose.Words và nhanh chóng phát
  hiện các phông chữ thiếu với hướng dẫn chi tiết từng bước dành cho các nhà phát
  triển .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: vi
og_description: Xử lý việc thay thế phông chữ trong Aspose.Words và học cách phát
  hiện phông chữ thiếu trong tài liệu của bạn với các ví dụ mã rõ ràng.
og_title: Xử lý Thay thế Phông chữ trong Aspose.Words – Hướng dẫn đầy đủ
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Xử lý Thay thế Phông chữ trong Aspose.Words – Hướng dẫn Lập trình Toàn diện
url: /vi/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Xử lý Thay thế Phông chữ trong Aspose.Words – Hướng dẫn Lập trình Toàn diện

Bạn đã bao giờ tự hỏi làm thế nào để **xử lý việc thay thế phông chữ** khi một tài liệu Word tham chiếu tới một phông chữ chưa được cài đặt trên máy chủ? Bạn không phải là người duy nhất. Trong nhiều ứng dụng thực tế—như trình tạo hoá đơn hay dịch vụ báo cáo tự động—các phông chữ thiếu gây ra các fallback im lặng làm hỏng bố cục.

Tin tốt là Aspose.Words cung cấp một hệ thống cảnh báo tích hợp cho phép bạn **phát hiện phông chữ thiếu** và phản hồi theo cách bạn muốn. Trong hướng dẫn này, chúng ta sẽ đi qua cách đăng ký một handler cảnh báo, tải tài liệu và lấy ra các sự kiện thay thế phông chữ cần biết. Khi kết thúc, bạn sẽ thấy cách trả lời câu hỏi “**làm sao để phát hiện phông chữ thiếu**?” bằng mã sạch, sẵn sàng cho môi trường production.

## Nội dung Hướng dẫn

* Cấu hình Aspose.Words để phát sinh cảnh báo cho mọi lần thay thế phông chữ.  
* Bắt các cảnh báo này trong một handler tùy chỉnh để bạn có thể ghi log, thay thế, hoặc hủy bỏ.  
* Sử dụng dữ liệu đã bắt để **phát hiện phông chữ thiếu** trước khi tài liệu được lưu hoặc render.  
* Mẹo khắc phục các trường hợp đặc biệt—như khi một phông chữ fallback được chọn một cách im lặng.  
* Một ví dụ hoàn chỉnh, có thể chạy ngay mà bạn có thể chèn vào bất kỳ ứng dụng console .NET nào.

> **Yêu cầu trước** – Bạn cần một .NET SDK mới (phiên bản 6.0+ hoạt động tốt), một giấy phép Aspose.Words for .NET hợp lệ (hoặc khóa đánh giá tạm thời), và một file DOCX mẫu cố tình tham chiếu tới một phông chữ bạn không có trên máy. Không cần thư viện bên thứ ba nào khác.

---

## ## Xử lý Thay thế Phông chữ với Handler Cảnh báo Tùy chỉnh

Aspose.Words tạo ra một đối tượng `WarningInfo` mỗi khi không tìm thấy phông chữ yêu cầu. Mặc định các cảnh báo này bị bỏ qua, vì vậy bạn thường không nhận ra việc thay thế. Để **xử lý thay thế phông chữ**, bạn thay thế handler cảnh báo mặc định bằng một handler thực sự thực hiện hành động nào đó.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Tại sao Cách này Hoạt động

* `FontSettings.DefaultWarningHandler` là một thuộc tính tĩnh toàn cục—khi bạn thiết lập nó, **mọi** hoạt động Aspose.Words trong AppDomain hiện tại sẽ sử dụng delegate của bạn.  
* `WarningInfoCollectionHandler` nhận một đối tượng `WarningInfo` chứa `WarningType` và một `Description` dễ đọc. Lọc theo `WarningType.FontSubstitution` giúp bạn chỉ thấy những sự kiện mình quan tâm.  
* Gọi `doc.Save` buộc thư viện giải quyết tất cả các phông chữ, lúc này các cảnh báo sẽ được kích hoạt. Nếu bạn chỉ muốn kiểm tra tài liệu mà không lưu, có thể gọi `doc.UpdatePageLayout()` thay thế.

**Kết quả console mong đợi** (giả sử phông chữ thiếu là “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Dòng này là bằng chứng rằng thư viện **đã phát hiện phông chữ thiếu** và đã chọn một phông chữ thay thế.

---

## ## Phát hiện Phông chữ Thiếu Trước Khi Render

Đôi khi bạn muốn dừng toàn bộ quá trình nếu một phông chữ bắt buộc bị thiếu—có thể vì tiêu chuẩn thương hiệu yêu cầu kiểu chữ chính xác. Handler cảnh báo có thể mở rộng để thu thập tất cả các thông báo phông chữ thiếu vào một danh sách, sau đó bạn quyết định hành động.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Cách Thức Giải đáp “làm sao để phát hiện phông chữ thiếu”

* Danh sách `missingFonts` hoạt động như một sổ ghi chép mọi sự kiện thay thế.  
* Sau `UpdatePageLayout`, bạn có thể kiểm tra danh sách và quyết định tiếp tục, ghi log, hoặc ném ngoại lệ.  
* Mẫu này hoạt động với bất kỳ định dạng đầu ra nào (PDF, HTML, hình ảnh) vì hệ thống cảnh báo không phụ thuộc vào định dạng.

---

## ## Mẹo Nâng cao: Thay thế Phông chữ Thiếu Bằng Một Phông chữ Cụ thể

Nếu bạn có một phông chữ doanh nghiệp phải được sử dụng, bạn có thể chỉ định cho Aspose.Words tự động thay thế bất kỳ phông chữ nào thiếu bằng phông chữ fallback của bạn. Điều này hữu ích khi bạn muốn tài liệu *vẫn* trông chấp nhận được mà không cần xử lý thủ công.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Đặt đoạn mã trên **trước** khi tải tài liệu. Bây giờ bất kỳ phông chữ nào thiếu—bất kể tên gốc—sẽ được thay bằng “Calibri” (hoặc “Arial” nếu Calibri không có). Bạn vẫn sẽ nhận được cảnh báo, nhưng tài liệu sẽ render bằng phông chữ bạn kiểm soát.

---

## ## Những Sai Lầm Thường Gặp & Cách Tránh

| Sai lầm | Nguyên nhân | Cách khắc phục |
|---------|-------------|----------------|
| **Cảnh báo biến mất sau lần gọi đầu tiên** | Thuộc tính tĩnh `DefaultWarningHandler` bị ghi đè sau này trong ứng dụng. | Thiết lập handler **một lần** khi khởi động ứng dụng, hoặc lưu tham chiếu và gán lại nếu cần thay đổi. |
| **Chỉ báo cáo phông chữ thiếu đầu tiên** | Một số API gom nhóm cảnh báo; bạn cần gọi `UpdatePageLayout` hoặc `Save` để đẩy hàng đợi. | Buộc cập nhật layout hoặc lưu ở định dạng bạn dự định tạo. |
| **Thay thế vẫn diễn ra ngay cả khi đã hủy** | Handler cảnh báo chạy *sau* khi thay thế đã xảy ra. | Dùng handler để **ghi log** rồi ném ngoại lệ để dừng quá trình xử lý tiếp theo. |
| **Phông chữ thiếu trên container Linux** | Linux thường thiếu danh mục phông chữ Windows, gây nhiều lần thay thế. | Gắn các phông chữ cần thiết vào container hoặc dùng `FontSettings.SetFontsFolder` để chỉ tới thư mục phông chữ tùy chỉnh. |

---

## ## Phát hiện Thay thế Phông chữ trong Kịch bản Web API

Nếu bạn phục vụ tài liệu qua ASP.NET Core, có lẽ bạn không muốn ghi ra console. Thay vào đó, hãy thu thập các cảnh báo và trả về chúng như một phần của phản hồi HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Bây giờ API **phát hiện phông chữ thiếu** và trả về payload JSON rõ ràng trước khi bất kỳ PDF nào được tạo. Đây là minh họa thực tế cho “làm sao để phát hiện phông chữ thiếu” trong một dịch vụ production‑grade.

---

## ## Kiểm thử Cài đặt của Bạn

1. **Tạo một file DOCX thử nghiệm** tham chiếu tới một phông chữ bạn biết không có trên máy (ví dụ “Comic Sans MS” trên một Docker image tối giản).  
2. Chạy ứng dụng console hoặc endpoint API.  
3. Xác nhận rằng console (hoặc phản hồi HTTP) liệt kê cảnh báo thay thế.  
4. Tùy chọn, mở PDF kết quả và kiểm tra thuộc tính phông chữ—Aspose.Words nên hiển thị phông chữ fallback bạn đã cấu hình.

Nếu bạn thấy cảnh báo nhưng PDF vẫn dùng phông chữ không mong muốn, hãy kiểm tra lại thứ tự `SubstitutionSettings`; khớp đầu tiên sẽ thắng.

---

## ## Kết luận

Chúng ta đã bao quát mọi thứ cần thiết để **xử lý thay thế phông chữ** trong Aspose.Words, từ việc đăng ký handler cảnh báo đến việc lập trình **phát hiện phông chữ thiếu** và thậm chí thay thế chúng bằng một kiểu chữ doanh nghiệp. Khi khai thác hệ thống cảnh báo tích hợp, bạn có được khả năng quan sát đầy đủ mọi sự kiện “không tìm thấy phông chữ”, trả lời trực tiếp câu hỏi “**làm sao để phát hiện phông chữ thiếu**?” mà mọi nhà phát triển gặp khi tự động hoá việc tạo tài liệu.

Tiếp theo bạn có thể thử kết hợp logic này với **tải phông chữ động** (`FontSettings.SetFontsFolder`) để hỗ trợ người dùng tải lên phông chữ theo yêu cầu, hoặc mở rộng handler cảnh báo để ghi các mục vào dịch vụ logging trung tâm như Serilog. Càng nhiều công cụ giám sát việc xử lý phông chữ, quy trình tài liệu của bạn càng đáng tin cậy.

Bạn có tình huống thay thế phông chữ khó khăn đang gặp phải? Hãy để lại bình luận bên dưới, chúng ta cùng nhau khắc phục. Chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây đề cập đến các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật đã trình bày trong bài viết này. Mỗi tài nguyên bao gồm mã mẫu đầy đủ, kèm giải thích từng bước để giúp bạn làm chủ các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}