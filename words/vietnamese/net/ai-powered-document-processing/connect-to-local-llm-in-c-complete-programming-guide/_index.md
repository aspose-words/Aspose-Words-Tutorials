---
category: general
date: 2026-04-28
description: Kết nối tới LLM cục bộ từ C# và yêu cầu mô hình ngôn ngữ lớn tải tài
  liệu Word, gọi LLM cục bộ và tự động viết lại văn bản. Bao gồm mã từng bước.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: vi
og_description: Kết nối tới LLM cục bộ từ C# và xem cách đưa ra lời nhắc cho mô hình
  ngôn ngữ lớn, tải tài liệu Word, gọi LLM cục bộ và tự động viết lại văn bản trong
  vài phút.
og_title: Kết nối tới LLM cục bộ trong C# – Hướng dẫn lập trình toàn diện
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Kết nối với LLM cục bộ trong C# – Hướng dẫn lập trình đầy đủ
url: /vi/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Kết nối tới LLM cục bộ trong C# – Hướng dẫn lập trình đầy đủ

Bạn đã bao giờ cần **kết nối tới LLM cục bộ** từ một ứng dụng .NET và tự hỏi làm sao để nó giao tiếp với một tệp Word chưa? Bạn không phải là người duy nhất. Trong hướng dẫn này, chúng ta sẽ đi qua toàn bộ quá trình — kết nối tới LLM cục bộ, **gửi lời nhắc tới mô hình ngôn ngữ lớn**, tải tài liệu Word, **gọi LLM cục bộ**, và cuối cùng **tự động viết lại văn bản**. Khi hoàn thành, bạn sẽ có một mẫu có thể chạy được, chuyển đổi bất kỳ đoạn văn nào thành giọng điệu trang trọng mà không cần khóa API bên ngoài.

## Những gì hướng dẫn này sẽ đề cập

Chúng ta sẽ bắt đầu bằng việc cài đặt các gói NuGet cần thiết, sau đó khởi động một endpoint LLM cục bộ đơn giản (nghĩa là Ollama trên cổng 11434). Tiếp theo, chúng ta sẽ tải một tệp `.docx` bằng Aspose.Words, gửi một đoạn văn tới LLM, nhận phiên bản đã được viết lại, và ghi lại vào cùng tài liệu. Bạn cũng sẽ thấy cách xử lý các vấn đề thường gặp — đoạn văn rỗng, việc giải phóng async, và các vấn đề mã hoá — để mã hoạt động trong môi trường sản xuất, không chỉ là bản demo.

### Các điều kiện tiên quyết

- .NET 6.0 SDK hoặc mới hơn (bạn cũng có thể dùng .NET 8 nếu muốn)
- Visual Studio 2022 hoặc VS Code với extension C#
- **Aspose.Words for .NET** (bản dùng thử miễn phí vẫn ổn)
- Một LLM được lưu trữ cục bộ hỗ trợ hợp đồng `/api/generate` (ví dụ: Ollama, LMStudio)
- Kiến thức cơ bản về async/await trong C#

> **Mẹo chuyên nghiệp:** Nếu bạn chưa cài đặt Ollama, chạy `ollama serve` và tải mô hình bằng `ollama pull llama3`. Endpoint HTTP mặc định sẽ là `http://localhost:11434/api/generate`.

---

## Bước 1: Cài đặt các gói cần thiết

Đầu tiên, thêm các gói NuGet Aspose.Words và Aspose.Words.AI vào dự án của bạn.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Các thư viện này cung cấp khả năng **tải tài liệu Word** và một lớp bao bọc nhẹ để **gọi LLM cục bộ** mà không cần tự viết các yêu cầu HTTP.

---

## Bước 2: Kết nối tới Endpoint LLM cục bộ

Kết nối tới một mô hình được lưu trữ cục bộ đơn giản như việc khởi tạo `LocalLargeLanguageModel`. Constructor yêu cầu URL đầy đủ của endpoint tạo nội dung.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Tại sao chúng ta lại bọc endpoint trong một lớp? `LocalLargeLanguageModel` xử lý việc tuần tự hoá JSON, retry, và streaming response cho bạn — vì vậy bạn có thể tập trung vào logic lời nhắc thay vì phải loay hoay với `HttpClient`.

---

## Bước 3: Tải tài liệu Word nguồn

Tiếp theo, chúng ta đưa tài liệu vào bộ nhớ. Aspose.Words hỗ trợ hầu hết mọi định dạng Word, vì vậy `Document` sẽ phân tích `input.docx` mà không cần cài Office.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Nếu bạn cần làm việc với một stream (ví dụ: tệp được tải lên qua ASP.NET), chỉ cần thay thế đường dẫn tệp bằng một `MemoryStream` và truyền nó vào constructor của `Document`.

---

## Bước 4: Trích xuất văn bản đoạn văn hiện tại

Chúng ta sẽ dùng `DocumentBuilder` để di chuyển trong tài liệu. Trong ví dụ này, chúng ta viết lại **đoạn văn đầu tiên**, nhưng bạn có thể lặp qua `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` để xử lý nhiều đoạn.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

Toán tử `?.` ngăn chặn `NullReferenceException` nếu tài liệu vô tình rỗng. Đây là một trong những **trường hợp góc cạnh** thường làm người mới bối rối.

---

## Bước 5: Gửi lời nhắc tới LLM để viết lại đoạn văn

Bây giờ chúng ta thực sự **gửi lời nhắc tới mô hình ngôn ngữ lớn**. Lời nhắc bằng tiếng Anh thuần túy; lớp bao bọc sẽ gửi nó dưới dạng JSON tới endpoint cục bộ.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Tại sao lại diễn đạt yêu cầu theo cách này? Các LLM phản hồi tốt nhất khi nhận được chỉ dẫn rõ ràng, đơn nhiệm. Thêm một dòng mới sau dấu hai chấm giúp tách biệt chỉ dẫn khỏi nội dung, giảm khả năng mô hình lặp lại lời nhắc.

**Kết quả mong đợi** – Nếu `originalParagraph` là `"Hey, what's up?"`, LLM có thể trả về:

> “Good day, how may I assist you?”

Bạn có thể xác minh kết quả bằng cách in ra:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Bước 6: Chèn văn bản đã viết lại trở lại tài liệu

Với văn bản mới trong tay, chúng ta thay thế đoạn văn cũ. `DocumentBuilder.Writeln` ghi một dòng mới và di chuyển con trỏ về phía trước, rất phù hợp cho việc thêm vào. Nếu bạn muốn *thay thế* đúng đoạn văn hiện tại, có thể dùng `docBuilder.CurrentParagraph.RemoveAllChildren()` trước khi ghi.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Cả hai cách đều được trình bày để bạn có thể chọn phương pháp phù hợp với quy trình của mình.

---

## Bước 7: Lưu tài liệu đã cập nhật

Cuối cùng, chúng ta ghi lại các thay đổi vào một tệp mới. Aspose.Words tự động chọn định dạng dựa trên phần mở rộng tệp.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Mở `output.docx` trong Word, và bạn sẽ thấy đoạn văn bây giờ được viết bằng giọng điệu trang trọng.

---

## Ví dụ hoàn chỉnh hoạt động

Dưới đây là **chương trình đầy đủ, tự chứa**. Sao chép‑dán vào một dự án console, khôi phục các gói NuGet, và chạy — không cần cấu hình thêm nào ngoài việc có một LLM cục bộ đang chạy.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Những gì sẽ xảy ra khi bạn chạy

1. Console in ra đoạn văn gốc và đoạn văn đã được viết lại.  
2. `output.docx` xuất hiện cạnh `input.docx`.  
3. Mở tệp, bạn sẽ thấy đoạn văn trang trọng mới được chèn sau đoạn gốc (hoặc được thay thế, nếu bạn dùng đoạn mã thay thế).

---

## Xử lý các trường hợp góc cạnh thường gặp

| Tình huống | Giải pháp |
|-----------|----------|
| **Đoạn văn rỗng hoặc chỉ chứa khoảng trắng** | Kiểm tra `string.IsNullOrWhiteSpace` trước khi gửi lời nhắc (xem Bước 3). |
| **LLM trả về lỗi hoặc chuỗi rỗng** | Bao `PromptAsync` trong `try/catch` và dùng lại văn bản gốc nếu cần. |
| **Nhiều đoạn văn cần viết lại** | Lặp qua `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` và áp dụng cùng logic lời nhắc. |
| **Tài liệu lớn gây độ trễ** | Gộp các đoạn văn và gửi chúng trong một yêu cầu duy nhất (lời nhắc tối đa ~4 KB mỗi lần). |
| **Ký tự không phải ASCII bị lỗi** | Đảm bảo endpoint LLM sử dụng UTF‑8 (hầu hết các mô hình hiện đại đều vậy). |

---

## Các bước tiếp theo & Chủ đề liên quan

- **Gửi lời nhắc tới mô hình ngôn ngữ lớn** với chỉ dẫn chi tiết hơn (ví dụ: hướng dẫn phong cách, giới hạn độ dài).  
- Sử dụng **gọi LLM cục bộ** trong một Web API để cung cấp dịch vụ tự động hoá tài liệu.  
- Khám phá **tải tài liệu Word** trong các stream song song để đạt hiệu suất cao.  
- Kết hợp cách tiếp cận này với **viết lại văn bản tự động** để tạo email hàng loạt hoặc chuẩn hoá báo cáo.  

Nếu muốn đào sâu hơn, hãy tham khảo tài liệu của Aspose về **document merging** và tham chiếu API của Ollama để tùy chỉnh các tham số sampling.

---

## Kết luận

Chúng ta vừa minh họa cách **kết nối tới LLM cục bộ** từ C#, **gửi lời nhắc tới mô hình ngôn ngữ lớn**, **tải tài liệu Word**, **gọi LLM cục bộ**, và **viết lại văn bản tự động** — tất cả trong một ứng dụng console có thể chạy ngay. Mô hình này có thể mở rộng: thay đổi lời nhắc, lặp qua các đoạn văn, hoặc đưa logic ra một endpoint ASP.NET. Điều quan trọng là các mô hình AI cục bộ có thể được tích hợp chặt chẽ với các thư viện xử lý tài liệu truyền thống, mang lại khả năng tự động hoá mạnh mẽ mà không cần rời khỏi môi trường on‑prem đáng tin cậy của bạn.

Có câu hỏi nào về threading không,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}