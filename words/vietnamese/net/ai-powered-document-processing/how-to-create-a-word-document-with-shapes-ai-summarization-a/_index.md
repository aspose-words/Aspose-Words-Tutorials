---
category: general
date: 2026-11-25
description: Tìm hiểu cách tạo tài liệu Word, thêm hình chữ nhật, tóm tắt tài liệu
  bằng AI, dịch văn bản bằng AI và lưu tài liệu dưới dạng DOCX bằng Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: vi
lastmod: 2026-11-25
og_description: Tạo tài liệu Word, thêm hình chữ nhật, tóm tắt tài liệu bằng AI, dịch
  văn bản bằng AI và lưu tài liệu dưới dạng DOCX—tất cả trong một hướng dẫn C# duy
  nhất.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Tạo tài liệu Word với các hình dạng, tóm tắt AI và dịch trong C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Cách tạo tài liệu Word với các hình dạng, tóm tắt AI và dịch trong C#
url: /vi/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tạo tài liệu Word với các hình dạng, tóm tắt AI và dịch trong C#

Nếu bạn cần **tạo một tài liệu Word** một cách lập trình, hướng dẫn này sẽ chỉ cho bạn cách thực hiện. Sử dụng Aspose.Words cho .NET, bạn sẽ học cách **thêm hình chữ nhật**, gọi một dịch vụ AI để **tóm tắt tài liệu bằng AI**, dịch một đoạn văn với **dịch văn bản bằng AI**, và cuối cùng **lưu tài liệu dưới dạng DOCX**.

Nhiều nhà phát triển gặp khó khăn khi kết hợp tự động hoá tài liệu và các tính năng AI hiện đại. Khi kết thúc hướng dẫn này, bạn sẽ có một dự án C# duy nhất, tự chứa, tạo ra một tệp *.docx* được định dạng đầy đủ, bao gồm một hình dạng trực quan, bản tóm tắt được tạo bởi AI, và nội dung đa ngôn ngữ.

## Yêu cầu trước

- .NET 6.0 SDK hoặc phiên bản sau được cài đặt  
- Visual Studio 2022 (hoặc bất kỳ IDE C# nào)  
- Giấy phép Aspose.Words cho .NET (hoặc khóa dùng thử miễn phí)  
- Kết nối Internet để thực hiện các cuộc gọi tóm tắt và dịch AI  

Không cần thêm bất kỳ gói NuGet nào ngoài `Aspose.Words` và `Aspose.Words.AI`.

## Bước 1: Thiết lập dự án và thêm các gói cần thiết

Tạo một dự án console mới và thêm các thư viện Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Mẹo chuyên nghiệp:** Nếu bạn dự định sử dụng chế độ dùng thử, gọi `Aspose.Words.License.SetLicense("Aspose.Words.lic");` sớm trong `Main` để tránh watermark.

## Bước 2: Khởi tạo tài liệu – cốt lõi của **create word document**

Dòng mã đầu tiên thực hiện tạo một đối tượng **Word document** mới. Đối tượng này là nền cho tất cả các thao tác tiếp theo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` đơn giản hoá việc chèn văn bản, hình dạng và điều khiển mà không cần xử lý thủ công cây node cấp thấp.

## Bước 3: **Add rectangle shape** vào tài liệu

Một hình chữ nhật có thể được dùng làm chỗ giữ chỗ trực quan, nền nhãn, hoặc một đồ họa đơn giản. Đầu tiên chúng ta tạo một `GroupShape`, sau đó chèn một `Rectangle` vào bên trong.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Hình chữ nhật có chiều rộng 100 điểm và chiều cao 50 điểm. Vì nó nằm trong một `GroupShape`, bạn có thể sau này thêm nhiều phần tử khác (ví dụ: hộp văn bản) mà không lo va chạm bố cục.

## Bước 4: Chèn StructuredDocumentTag (SDT) dạng văn bản thuần

Các đối tượng StructuredDocumentTag hữu ích cho các điều khiển nội dung có thể được liên kết với nguồn dữ liệu sau này.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

Cờ `true` đánh dấu thẻ là một điều khiển **repeating**, rất tiện cho các mẫu.

## Bước 5: Thêm điều khiển ActiveX CommandButton (giao diện tùy chọn)

Nếu tài liệu được tạo sẽ được sử dụng trong môi trường hỗ trợ ActiveX, bạn có thể nhúng một nút.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Bước này là tùy chọn; bạn có thể bỏ qua nếu người dùng mục tiêu của bạn không bao giờ tương tác với tài liệu trong môi trường Windows.

## Bước 6: **Summarize document with AI**

Aspose.Words.AI cung cấp một lớp bao bọc tiện lợi cho các dịch vụ mô hình ngôn ngữ lớn. Ở đây chúng ta gọi `DocumentSummarizer.Summarize` với backend OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Phương thức này phân tích cây node hiện tại, trích xuất các câu liên quan nhất và trả về một đoạn văn ngắn gọn. Đây là cốt lõi của chức năng **summarize document with AI**.

## Bước 7: **Translate text using AI**

Tiếp theo chúng ta sẽ minh họa cách dịch một chuỗi mẫu từ tiếng Anh sang tiếng Pháp. Phương thức `Translator.Translate` bên trong gọi một mô hình AI của Google.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Bạn có thể thay `Language.French` bằng bất kỳ giá trị enum ngôn ngữ nào được hỗ trợ, cho phép tạo tài liệu đa ngôn ngữ ngay lập tức.

## Bước 8: **Save document as DOCX**

Cuối cùng, lưu tài liệu đã chỉnh sửa vào đĩa. Phương thức `Save` tự động ghi một tệp *.docx* khi bạn chỉ định phần mở rộng `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

Tệp `Result.docx` hiện chứa:

- Một hình chữ nhật bên trong một group shape  
- Một điều khiển nội dung dạng văn bản thuần (SDT)  
- Một ActiveX CommandButton (nếu bạn giữ Bước 5)  
- Một đoạn tóm tắt được tạo bởi AI  
- Bản dịch tiếng Pháp của “Hello world”

Bạn có thể mở tệp trong Microsoft Word để kiểm tra từng yếu tố.

## Mã nguồn hoàn chỉnh

Dưới đây là chương trình đầy đủ, sẵn sàng chạy. Sao chép nó vào `Program.cs` và thực thi `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Kết quả mong đợi

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Khi bạn mở `Result.docx`, bạn sẽ thấy hình chữ nhật ở gần đầu trang, placeholder SDT, nút, đoạn tóm tắt và bản dịch tiếng Pháp được chèn dưới dạng văn bản thuần.

## Kết luận

Bây giờ bạn đã biết cách **tạo một tài liệu Word** từ đầu, **thêm hình chữ nhật**, **tóm tắt tài liệu bằng AI**, **dịch văn bản bằng AI**, và **lưu tài liệu dưới dạng DOCX**—tất cả chỉ với vài dòng C# ngắn gọn. Mô hình này có thể mở rộng: bạn có thể thay thế các chuỗi cứng bằng dữ liệu động, thêm nhiều hình dạng hoặc biểu đồ, và chuyển nhà cung cấp AI bằng cách điều chỉnh các tham số `SummarizerOptions` hoặc `Translator`.

### Tiếp theo là gì?

- Khám phá các biến thể của **add rectangle shape**: thay đổi màu nền, kiểu đường viền, hoặc thêm văn bản bên trong hình.  
- Sử dụng **summarize document with AI** trên các tài liệu lớn hơn để tự động tạo bản tóm tắt cho lãnh đạo.  
- Mở rộng **translate text using AI** để xử lý hàng loạt toàn bộ đoạn văn hoặc bảng cho các báo cáo đa ngôn ngữ.  
- Kết hợp các API vẽ biểu đồ của Aspose.Words để nhúng trực quan dữ liệu cùng với những hiểu biết được tạo bởi AI.  

Hãy thoải mái thử nghiệm, và chia sẻ kết quả của bạn trong phần bình luận hoặc trên GitHub. Chúc lập trình vui vẻ!

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh với giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tạo tài liệu Word trống và thêm hình chữ nhật](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Tạo Group Shape trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Thêm Watermark văn bản trong tài liệu Word bằng Aspose.Words cho .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}