---
category: general
date: 2026-06-02
description: Cách lưu PDF từ DOCX bằng Aspose.Words, xuất các hình dạng dưới dạng
  thẻ span nội tuyến, và chuyển đổi Word sang PDF chỉ trong vài bước.
draft: false
keywords:
- how to save pdf
- save docx as pdf
- convert word to pdf
- how to export shapes
- inline span tags
language: vi
og_description: Cách lưu PDF từ tài liệu Word bằng Aspose.Words, xuất các hình dạng
  nổi dưới dạng thẻ span nội tuyến để có kết quả chuyển đổi Word sang PDF sạch sẽ.
og_title: Cách Lưu PDF từ Word – Hướng Dẫn Xuất Hình Inline
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  headline: How to Save PDF from Word with Inline Shape Export – Complete Guide
  type: TechArticle
- description: How to save PDF from a DOCX using Aspose.Words, export shapes as inline
    span tags, and convert Word to PDF in just a few steps.
  name: How to Save PDF from Word with Inline Shape Export – Complete Guide
  steps:
  - name: What if my document contains **SmartArt** or **Charts**?
    text: SmartArt and charts are treated as drawing objects. The `ExportFloatingShapesAsInlineTag`
      flag will still wrap them in `<span>` tags, but complex graphics may lose some
      fidelity. In those cases, consider exporting the chart as an image first (`Chart.ToImage()`)
      and then inserting it inline.
  - name: Can I **preserve hyperlinks** and **bookmarks**?
    text: Absolutely. Those elements are not affected by the `ExportFloatingShapesAsInlineTag`
      setting. Aspose.Words retains all hyperlink and bookmark information automatically.
  - name: How do I **change PDF compression** or **embed fonts**?
    text: '`PdfSaveOptions` offers many additional properties:'
  type: HowTo
tags:
- Aspose.Words
- C#
- PDF conversion
title: Cách Lưu PDF Từ Word Với Xuất Hình Dạng Nội Dòng – Hướng Dẫn Chi Tiết
url: /vi/net/programming-with-pdfsaveoptions/how-to-save-pdf-from-word-with-inline-shape-export-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách Lưu PDF từ Word với Xuất Hình Dạng Inline – Hướng Dẫn Toàn Diện

Bạn đã bao giờ tự hỏi **cách lưu PDF** từ một tệp Word trong khi giữ mọi hình dạng nổi được gọn gàng trong luồng chưa? Bạn không phải là người duy nhất. Trong nhiều ứng dụng doanh nghiệp, chúng ta cần *chuyển đổi Word sang PDF* mà không gặp phải hình ảnh bị lệch vị trí hoặc các đối tượng vẽ lơ lửng. Tin tốt là gì? Aspose.Words làm cho việc này trở nên dễ dàng, và bạn thậm chí có thể chỉ cho thư viện **xuất các hình dạng dưới dạng thẻ `<span>` inline** để PDF trông giống hệt DOCX gốc.

Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quy trình — tải một DOCX, điều chỉnh `PdfSaveOptions`, và cuối cùng lưu một PDF sạch sẽ. Khi kết thúc, bạn sẽ biết **cách lưu PDF**, **lưu docx thành pdf**, và thậm chí **cách xuất các hình dạng** bằng cách sử dụng *thẻ span inline*.

## Những Gì Bạn Cần

- **Aspose.Words for .NET** (phiên bản mới nhất, 24.x tại thời điểm viết).  
- **.NET 6.0** hoặc mới hơn – mã cũng hoạt động trên .NET Framework 4.7.2, nhưng .NET 6 là lựa chọn tối ưu.  
- Một tài liệu Word đơn giản chứa ít nhất một hình dạng nổi (hình ảnh, hộp văn bản, hoặc bản vẽ).  
- Bất kỳ IDE nào bạn thích (Visual Studio, Rider, VS Code + C# extension).  

Chỉ vậy thôi — không cần gói NuGet bổ sung, không cần COM interop phức tạp. Sẵn sàng? Hãy bắt đầu.

## Bước 1: Thiết Lập Dự Án và Thêm Aspose.Words

Đầu tiên, tạo một ứng dụng console (hoặc tích hợp mã vào dịch vụ hiện có của bạn).

```bash
dotnet new console -n WordToPdfDemo
cd WordToPdfDemo
dotnet add package Aspose.Words
```

> **Mẹo chuyên nghiệp:** Nếu bạn đang sử dụng Visual Studio, bạn có thể thêm gói qua giao diện NuGet Package Manager — chỉ cần tìm kiếm *Aspose.Words*.

## Bước 2: Tải Tài Liệu Nguồn

Bây giờ thư viện đã được tham chiếu, chúng ta có thể tải DOCX. Đây là hành động cụ thể đầu tiên của phần **cách lưu pdf** — đưa nguồn vào bộ nhớ.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Step 2: Load the source document
        // Replace YOUR_DIRECTORY with the actual path on your machine.
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded successfully.");
```

**Tại sao điều này quan trọng:** Việc tải tệp xác nhận đường dẫn đúng và Aspose có thể phân tích cấu trúc Word. Nếu tệp chứa các hình dạng nổi, chúng sẽ là một phần của cây node của đối tượng `Document`.

## Bước 3: Cấu Hình Tùy Chọn Lưu PDF – Xuất Hình Dạng dưới Dạng Thẻ Inline

Đây là phần cốt lõi của **cách xuất hình dạng**. Mặc định, Aspose.Words render các hình dạng nổi như các đối tượng riêng trong PDF, có thể làm lệch bố cục. Đặt `ExportFloatingShapesAsInlineTag` thành `true` sẽ yêu cầu engine bọc mỗi hình dạng trong một phần tử `<span>` inline, giữ nguyên luồng.

```csharp
        // Step 3: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            // Optional: keep the original page size
            PageMode = PdfPageMode.UseTrimBox
        };
        Console.WriteLine("PDF save options configured – shapes will be inline.");
```

**Tại sao bật cờ này?** Hãy tưởng tượng một hợp đồng có hộp chữ ký nổi trên văn bản. Khi bạn chuyển đổi sang PDF mà không bật cài đặt này, hộp có thể xuất hiện trên trang khác. Các thẻ `<span>` inline giữ hình dạng gắn vào đoạn văn xung quanh, tạo ra bản sao hình ảnh trung thực.

## Bước 4: Lưu Tài Liệu dưới Dạng PDF

Cuối cùng, chúng ta gọi `doc.Save` với các tùy chọn vừa tạo. Đây là thời điểm bạn thực sự **lưu docx thành pdf**.

```csharp
        // Step 4: Save the document as a PDF using the configured options
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved successfully to: {outputPath}");
    }
}
```

Chạy chương trình (`dotnet run`) và kiểm tra `output.pdf`. Bạn sẽ thấy các hình dạng nổi được render inline, giống như trong Word.

## Bước 5: Xác Minh Kết Quả – Danh Sách Kiểm Tra Nhanh

1. **Tất cả văn bản đều có** – không thiếu đoạn nào.  
2. **Các hình dạng nổi xuất hiện đúng vị trí** – chúng hiện là một phần của luồng văn bản.  
3. **Kích thước PDF hợp lý** – xuất dưới dạng thẻ inline thường giảm bớt kích thước tệp so với các luồng ảnh riêng biệt.  

Nếu có gì không ổn, hãy kiểm tra lại DOCX nguồn thực sự sử dụng các hình dạng *nổi* (click chuột phải → Layout → “In line with text” vs “Square/Behind text”). Chuyển một hình dạng sang “In line” trước khi chuyển đổi cũng hoạt động, nhưng tùy chọn thẻ inline cho bạn kiểm soát mà không cần chỉnh sửa tệp gốc.

## Trường Hợp Cạnh & Câu Hỏi Thường Gặp

### Nếu tài liệu của tôi chứa **SmartArt** hoặc **Charts**?

SmartArt và biểu đồ được xem như các đối tượng vẽ. Cờ `ExportFloatingShapesAsInlineTag` vẫn sẽ bọc chúng trong thẻ `<span>`, nhưng đồ họa phức tạp có thể mất một phần độ chính xác. Trong những trường hợp đó, hãy cân nhắc xuất biểu đồ thành hình ảnh trước (`Chart.ToImage()`) rồi chèn inline.

### Tôi có thể **giữ lại siêu liên kết** và **đánh dấu** không?

Chắc chắn. Các yếu tố này không bị ảnh hưởng bởi cài đặt `ExportFloatingShapesAsInlineTag`. Aspose.Words tự động giữ lại tất cả thông tin siêu liên kết và đánh dấu.

### Làm sao để **thay đổi nén PDF** hoặc **nhúng phông chữ**?

`PdfSaveOptions` cung cấp nhiều thuộc tính bổ sung:

```csharp
pdfOpts.JpegQuality = 90;               // Adjust image compression
pdfOpts.FontEmbeddingMode = FontEmbeddingMode.EmbedAll; // Embed all used fonts
```

Bạn có thể tự do điều chỉnh các cài đặt này dựa trên yêu cầu downstream (ví dụ, tuân thủ PDF/A).

## Ví Dụ Hoàn Chỉnh (Sẵn Sàng Sao Chép‑Dán)

Dưới đây là chương trình đầy đủ mà bạn có thể sao chép vào `Program.cs`. Thay `YOUR_DIRECTORY` bằng đường dẫn thư mục thực tế.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // Load the source DOCX (contains floating shapes)
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        Console.WriteLine("Document loaded.");

        // Configure PDF save options – export shapes as inline <span> tags
        PdfSaveOptions pdfOpts = new PdfSaveOptions
        {
            ExportFloatingShapesAsInlineTag = true,
            PageMode = PdfPageMode.UseTrimBox,
            // Optional tweaks
            JpegQuality = 90,
            FontEmbeddingMode = FontEmbeddingMode.EmbedAll
        };
        Console.WriteLine("PDF options set – shapes will be inline.");

        // Save as PDF
        string outputPath = @"YOUR_DIRECTORY\output.pdf";
        doc.Save(outputPath, pdfOpts);
        Console.WriteLine($"PDF saved to {outputPath}");
    }
}
```

**Kết quả mong đợi trong console:**

```
Document loaded.
PDF options set – shapes will be inline.
PDF saved to C:\MyDocs\output.pdf
```

Mở `output.pdf` — bạn sẽ thấy bố cục gốc, với mọi hình dạng nổi được đặt gọn trong luồng văn bản.

## Kết Luận

Chúng tôi đã trình bày **cách lưu PDF** từ tài liệu Word đồng thời đảm bảo các hình dạng nổi trở thành thẻ `<span>` inline. Bằng cách tải DOCX, cấu hình `PdfSaveOptions`, và gọi `doc.Save`, bạn có thể tin cậy **lưu docx thành pdf** và **chuyển đổi word sang pdf** mà không gặp bất ngờ về bố cục.

Bước tiếp theo? Hãy thử kết hợp cách này với tuân thủ **PDF/A** để lưu trữ, hoặc xử lý hàng loạt một thư mục các tệp DOCX bằng vòng lặp `foreach` đơn giản. Bạn cũng có thể khám phá **render tùy chỉnh** (ví dụ, thêm watermark) bằng cách sử dụng API `DocumentVisitor` của Aspose.Words.

Có thêm câu hỏi về xử lý hình dạng, nhúng phông chữ, hoặc tối ưu hiệu năng? Để lại bình luận bên dưới, và chúc bạn lập trình vui vẻ!

## Bạn Nên Học Gì Tiếp Theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Cách lưu tài liệu dưới dạng pdf với Aspose.Words cho Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Chuyển đổi Word sang PDF với Aspose.Words cho Java](/words/english/java/document-converting/exporting-documents-to-pdf/)
- [aspose word to pdf – Chuyển DOCX sang PDF trong Java](/words/english/java/document-conversion-and-export/aspose-word-to-pdf-convert-docx-to-pdf-in-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}