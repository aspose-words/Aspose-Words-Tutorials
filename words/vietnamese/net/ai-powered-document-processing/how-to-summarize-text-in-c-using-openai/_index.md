---
category: general
date: 2026-09-11
description: Học cách tóm tắt văn bản trong C# bằng cách đọc khóa API, gọi OpenAI
  và tạo một bản tóm tắt ngắn gọn của tài liệu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: vi
lastmod: 2026-09-11
og_description: Cách tóm tắt văn bản trong C#? Hướng dẫn này chỉ cho bạn cách đọc
  khóa API, gọi OpenAI và tạo bản tóm tắt cho tài liệu Word.
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: Cách tóm tắt văn bản trong C# với OpenAI – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  headline: How to summarize text in C# using OpenAI
  type: TechArticle
- description: Learn how to summarize text in C# by reading the API key, calling OpenAI,
    and generating a concise summary of a Word document.
  name: How to summarize text in C# using OpenAI
  steps:
  - name: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
    text: '**Cache the API key** – reading from the environment each call adds negligible
      overhead, but you can store it in a static readonly field if you call the summarizer
      many times in one process.'
  - name: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
    text: '**Rate‑limit requests** – OpenAI enforces request limits; implement exponential
      back‑off if you hit `429 Too Many Requests`.'
  - name: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
    text: '**Sanitize input** – remove personally identifiable information before
      sending text to an external AI service.'
  - name: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
    text: '**Unit test the extraction logic** – mock `WordprocessingDocument` to verify
      `ExtractTextFromDocx` works with different document structures.'
  type: HowTo
tags:
- C#
- OpenAI
- Document processing
- AI summarization
title: Cách tóm tắt văn bản trong C# bằng OpenAI
url: /vi/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách tóm tắt văn bản trong C# bằng OpenAI

Nếu bạn cần **how to summarize text** trong một tệp .docx, hướng dẫn này sẽ cho bạn một giải pháp hoàn chỉnh, sẵn sàng chạy. Bạn sẽ học cách đọc khóa API từ môi trường của mình, cách gọi OpenAI (hoặc Google) từ C#, và cách tạo một bản tóm tắt ngắn gọn của tài liệu Word.

Việc tóm tắt một tài liệu Word là một yêu cầu phổ biến cho việc tạo báo cáo, bản tóm tắt email, hoặc trích xuất cơ sở kiến thức. Khi kết thúc hướng dẫn này, bạn sẽ có một chương trình dòng lệnh in ra bản tóm tắt năm câu của bất kỳ tệp `.docx` nào bạn cung cấp.

## Yêu cầu trước

- .NET 6.0 SDK hoặc phiên bản mới hơn (tải về từ [dotnet.microsoft.com](https://dotnet.microsoft.com/download))
- Một khóa API OpenAI hợp lệ được lưu trong biến môi trường có tên `OPENAI_API_KEY` (bạn sẽ thấy **read api key** trong hành động)
- Gói NuGet `DocumentFormat.OpenXml` để đọc các tệp `.docx`
- Gói NuGet `OpenAI` (hoặc `Google.AI` nếu bạn thích nhà cung cấp Google)

## Bước 1: Thiết lập dự án và cài đặt các phụ thuộc

Tạo một dự án console mới và thêm các gói cần thiết:

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **Mẹo chuyên nghiệp:** Giữ file `csproj` của bạn gọn gàng bằng cách nhóm các gói liên quan dưới một `<ItemGroup>` nếu bạn thêm nhiều phụ thuộc sau này.

## Bước 2: Đọc khóa API một cách an toàn

Việc mã hóa cứng các bí mật là không an toàn. Hướng dẫn này trình bày cách đúng để **read api key** từ các biến môi trường.

```csharp
using System;

/// <summary>
/// Retrieves the OpenAI API key from the environment.
/// Throws an exception if the variable is missing.
/// </summary>
static string GetOpenAIApiKey()
{
    var key = Environment.GetEnvironmentVariable("OPENAI_API_KEY");
    if (string.IsNullOrWhiteSpace(key))
    {
        throw new InvalidOperationException(
            "OPENAI_API_KEY environment variable not set. " +
            "Set it before running the program.");
    }
    return key;
}
```

## Bước 3: Tải tài liệu Word mà bạn muốn tóm tắt

Mã dưới đây cho thấy **how to summarize word document** nội dung bằng cách trích xuất văn bản thuần từ cấu trúc OpenXML.

```csharp
using DocumentFormat.OpenXml.Packaging;
using DocumentFormat.OpenXml.Wordprocessing;

/// <summary>
/// Extracts raw text from a .docx file.
/// </summary>
static string ExtractTextFromDocx(string path)
{
    using var wordDoc = WordprocessingDocument.Open(path, false);
    var body = wordDoc.MainDocumentPart.Document.Body;
    return body.InnerText;
}
```

## Bước 4: Xây dựng lớp tóm tắt có thể tái sử dụng

Lớp này bao hàm **how to call openai** (hoặc Google) và triển khai logic **how to create summary**. Nó cũng cho phép bạn chuyển đổi nhà cung cấp bằng một giá trị enum duy nhất.

```csharp
using System.Threading.Tasks;
using OpenAI;
using OpenAI.Chat;

/// <summary>
/// Supported AI providers for summarization.
/// </summary>
enum SummarizerProvider { OpenAI, Google }

/// <summary>
/// Provides a method to summarize a document using the selected provider.
/// </summary>
static class DocumentSummarizer
{
    public static async Task<string> SummarizeAsync(
        string text,
        SummarizerProvider provider,
        int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => await SummarizeWithOpenAIAsync(text, maxSentences),
            SummarizerProvider.Google => await SummarizeWithGoogleAsync(text, maxSentences),
            _ => throw new NotSupportedException($"Provider {provider} is not supported.")
        };
    }

    // ---------- OpenAI implementation ----------
    private static async Task<string> SummarizeWithOpenAIAsync(string text, int maxSentences)
    {
        var apiKey = GetOpenAIApiKey(); // re‑use the method from Step 2
        var client = new OpenAIClient(new OpenAIAuthentication(apiKey));

        var prompt = $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}";
        var chatRequest = new ChatRequest(new[] { new ChatMessage(ChatMessageRole.System, prompt) });

        var response = await client.ChatEndpoint.GetCompletionAsync(chatRequest);
        return response.FirstChoice.Message.Content.Trim();
    }

    // ---------- Google implementation (optional) ----------
    private static async Task<string> SummarizeWithGoogleAsync(string text, int maxSentences)
    {
        // Placeholder for Google AI call.
        // Replace with actual Google client code if you have the package.
        await Task.Yield();
        return "Google summarization not implemented in this demo.";
    }
}
```

### Tại sao cấu trúc này lại quan trọng

- **Separation of concerns:** Tải tài liệu, đọc khóa API, và gọi dịch vụ AI được tách riêng thành các phương thức riêng. Điều này làm cho mã dễ kiểm thử và mở rộng hơn.
- **Provider flexibility:** Bằng cách sử dụng enum, bạn có thể chuyển đổi giữa OpenAI và Google mà không cần chỉnh sửa mã gọi, điều này trực tiếp trả lời **how to call openai** và **how to create summary** theo cách có thể tái sử dụng.
- **Error handling:** Thiếu khóa API sẽ ném ra một ngoại lệ rõ ràng, ngăn ngừa các lỗi im lặng.

## Bước 5: Kết hợp mọi thứ lại trong `Program.cs`

```csharp
using System;
using System.Threading.Tasks;

class Program
{
    static async Task Main(string[] args)
    {
        if (args.Length != 1)
        {
            Console.WriteLine("Usage: SummarizerDemo <path-to-docx>");
            return;
        }

        string docPath = args[0];

        // 1️⃣ Load the source document
        string rawText = ExtractTextFromDocx(docPath);

        // 2️⃣ Summarize the document using OpenAI (you can switch to Google)
        string summary = await DocumentSummarizer.SummarizeAsync(
            rawText,
            SummarizerProvider.OpenAI, // change to SummarizerProvider.Google if needed
            maxSentences: 5);

        // 3️⃣ Output the generated summary
        Console.WriteLine("Summary:");
        Console.WriteLine(summary);
    }

    // Include the helper methods from Steps 2‑4 here
    // (GetOpenAIApiKey, ExtractTextFromDocx, DocumentSummarizer, etc.)
}
```

### Kết quả mong đợi

Chạy chương trình với một tài liệu mẫu:

```bash
dotnet run -- "sample/input.docx"
```

có thể tạo ra:

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## Bước 6: Các biến thể phổ biến và trường hợp góc cạnh

| Tình huống | Điều chỉnh đề xuất |
|-----------|------------------------|
| **Large documents** ( > 10 KB ) | Chia văn bản thành các đoạn và tóm tắt từng đoạn, sau đó kết hợp các kết quả. |
| **Non‑English content** | Cung cấp gợi ý ngôn ngữ trong prompt, ví dụ: “Summarize the following French text …”. |
| **Google provider** | Thay thế lời gọi `SummarizeWithOpenAIAsync` bằng client API Google thích hợp; giữ giao diện enum giống nhau. |
| **Custom summary length** | Thay đổi đối số `maxSentences` khi gọi `SummarizeAsync`. |
| **Missing API key** | Phương thức `GetOpenAIApiKey` đã ném ra một ngoại lệ rõ ràng; bắt nó trong `Main` nếu bạn muốn thông báo thân thiện hơn. |

## Mẹo chuyên nghiệp cho việc sử dụng trong môi trường sản xuất

1. **Cache the API key** – đọc từ môi trường mỗi lần gọi thêm chi phí không đáng kể, nhưng bạn có thể lưu nó trong một trường static readonly nếu bạn gọi summarizer nhiều lần trong một tiến trình.
2. **Rate‑limit requests** – OpenAI áp dụng giới hạn yêu cầu; triển khai back‑off exponential nếu gặp lỗi `429 Too Many Requests`.
3. **Sanitize input** – loại bỏ thông tin nhận dạng cá nhân trước khi gửi văn bản tới dịch vụ AI bên ngoài.
4. **Unit test the extraction logic** – mock `WordprocessingDocument` để xác minh `ExtractTextFromDocx` hoạt động với các cấu trúc tài liệu khác nhau.

## Kết luận

Bây giờ bạn đã biết **how to summarize text** trong C# bằng cách đọc khóa API một cách an toàn, gọi OpenAI, và tạo ra một bản tóm tắt ngắn gọn của tài liệu Word. Mẫu tương tự cho phép bạn **how to call openai** với các nhà cung cấp khác, logic **how to create summary** cho các loại nội dung khác nhau, và an toàn **read api key** giá trị từ môi trường. Hãy thử nghiệm với các tài liệu dài hơn, nhà cung cấp khác, hoặc prompt tùy chỉnh để điều chỉnh việc tóm tắt cho lĩnh vực cụ thể của bạn.

---

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng dựa trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên đều có các ví dụ mã hoàn chỉnh, hoạt động cùng các giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tóm tắt tài liệu Word trong C# với Aspose.Words API – Hướng dẫn AI‑Powered hoàn chỉnh](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [cách tạo pdf từ Word – Hướng dẫn C# hoàn chỉnh](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Tài liệu Word - Cách xóa nội dung](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}