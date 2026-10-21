---
category: general
date: 2026-09-21
description: Học cách xây dựng một công cụ tóm tắt tài liệu AI bằng C# tạo bản tóm
  tắt từ các tệp Word bằng cách sử dụng API của OpenAI hoặc Google.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- ai document summarizer
- ai powered summarization
- create summary from word
- summarize docx with ai
- summarize using google
language: vi
lastmod: 2026-09-21
og_description: Bộ tóm tắt tài liệu AI bằng C# cho phép bạn tạo bản tóm tắt từ các
  tệp Word một cách nhanh chóng. Hãy làm theo hướng dẫn này để sử dụng OpenAI hoặc
  Google cho việc tóm tắt dựa trên AI.
og_image_alt: Diagram showing the workflow of an ai document summarizer processing
  a Word file
og_title: Xây dựng công cụ tóm tắt tài liệu AI bằng C# – hướng dẫn từng bước
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  headline: How to use an ai document summarizer in C#
  type: TechArticle
- description: Learn how to build an ai document summarizer in C# that creates summary
    from Word files using OpenAI or Google APIs.
  name: How to use an ai document summarizer in C#
  steps:
  - name: Provider implementation details
    text: '```csharp static class DocumentSummarizer { public static string Summarize(string
      text, SummarizerProvider provider, int maxSentences = 5) { return provider switch
      { SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences), SummarizerProvider.Google
      => SummarizeWithGoogle(text, maxSenten'
  - name: Handling token limits and large documents
    text: If the source document exceeds the model’s token quota, split it into paragraphs
      and summarize each chunk separately, then combine the chunk summaries. This
      ensures you never hit the 8 k‑token limit for most models.
  - name: Expected output
    text: '``` Summary: The report highlights a 12% revenue increase driven by new
      product launches. Customer churn dropped to 3% after the recent support improvements.
      Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will
      focus on expanding into APAC markets. Overall, the company is on'
  type: HowTo
tags:
- AI
- C#
- Document Processing
title: Cách sử dụng công cụ tóm tắt tài liệu AI trong C#
url: /vi/net/ai-powered-document-processing/how-to-use-an-ai-document-summarizer-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cách sử dụng ai document summarizer trong C#

Nếu bạn cần một **ai document summarizer** cho các tệp .docx, hướng dẫn này sẽ chỉ cho bạn cách tạo bản tóm tắt từ Word bằng C#. Bạn sẽ thấy một ví dụ hoàn chỉnh, có thể chạy được, hoạt động với cả OpenAI hoặc Google, cung cấp cho bạn giải pháp **ai powered summarization** trong vài phút.

Bài hướng dẫn bao gồm mọi thứ từ thiết lập dự án đến xử lý các trường hợp đặc biệt, giúp bạn tự tin **summarize docx with ai** trong các ứng dụng của mình. Không cần script bên ngoài — chỉ cần một vài gói NuGet và một đoạn mã ngắn.

## Những gì bạn cần

- .NET 6.0 hoặc mới hơn (mã cũng hoạt động trên .NET Core 3.1+)
- Khóa API OpenAI **hoặc** khóa Google Cloud Vertex AI
- Gói NuGet `DocX` để đọc các tệp Word
- Gói NuGet `OpenAI` hoặc `Google.Cloud.AIPlatform.V1` cho nhà cung cấp đã chọn
- Môi trường phát triển như Visual Studio 2022 hoặc VS Code

## Bước 1: Thiết lập môi trường ai document summarizer

Đầu tiên, tạo một dự án console mới và thêm các gói cần thiết:

```bash
dotnet new console -n AiSummarizerDemo
cd AiSummarizerDemo
dotnet add package DocX --version 1.0.0
dotnet add package OpenAI --version 2.5.0   # for OpenAI
dotnet add package Google.Cloud.AIPlatform.V1 --version 2.6.0   # for Google
```

> **Mẹo chuyên nghiệp:** Giữ các khóa API của bạn trong biến môi trường (`OPENAI_API_KEY`, `GOOGLE_APPLICATION_CREDENTIALS`) thay vì mã hóa cứng chúng.

## Bước 2: Tải tài liệu Word để **create summary from word**

Dòng chức năng đầu tiên đọc tệp `.docx` nguồn. Sử dụng `DocX` chúng ta trích xuất văn bản thuần, mà mô hình AI sẽ tóm tắt sau.

```csharp
using System;
using System.IO;
using Xceed.Words.NET;   // DocX namespace

// Load the source document you want to summarize
Document document = Document.Load("input.docx");

// Extract raw text for the summarizer
string rawText = document.Text;
```

> **Tại sao bước này quan trọng:** Các mô hình AI hoạt động tốt nhất với văn bản sạch, tuyến tính. Loại bỏ định dạng giúp tránh các bất ngờ về giới hạn token và cải thiện độ liên quan của bản tóm tắt.

## Bước 3: Chọn nhà cung cấp **ai powered summarization**

Bạn có thể chuyển đổi giữa GPT‑4 của OpenAI hoặc mô hình PaLM của Google bằng cách đặt enum `SummarizerProvider`. Enum này trừu tượng hoá logic riêng của từng nhà cung cấp.

```csharp
enum SummarizerProvider
{
    OpenAI,
    Google
}

// Choose the provider (replace with your preference)
SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google
```

### Chi tiết triển khai nhà cung cấp

```csharp
static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
    {
        return provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported summarizer provider.")
        };
    }

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder
        {
            // Google credentials are read from GOOGLE_APPLICATION_CREDENTIALS env var
        }.Build();

        var request = new PredictRequest
        {
            // The model name depends on your Vertex AI deployment
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };

        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}
```

> **Tại sao chúng tôi trừu tượng hoá nhà cung cấp:** Mẫu này cho phép bạn **summarize using google** hoặc OpenAI mà không cần thay đổi mã gọi—rất hữu ích cho việc kiểm thử hoặc chuyển đổi nhà cung cấp sau này.

## Bước 4: Tạo bản tóm tắt ngắn gọn – **summarize docx with ai**

Bây giờ gọi phương thức trợ giúp, giới hạn đầu ra thành năm câu (có thể điều chỉnh qua `maxSentences`).

```csharp
// Generate a concise summary with a maximum of 5 sentences
string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);
```

### Xử lý giới hạn token và tài liệu lớn

Nếu tài liệu nguồn vượt quá hạn mức token của mô hình, hãy chia nó thành các đoạn và tóm tắt từng phần riêng biệt, sau đó kết hợp các bản tóm tắt phần. Điều này đảm bảo bạn không bao giờ vượt quá giới hạn 8 k‑token cho hầu hết các mô hình.

```csharp
static string SummarizeLargeText(string fullText, SummarizerProvider provider, int maxSentences)
{
    const int chunkSize = 2000; // approximate token count
    var chunks = fullText
        .Split(new[] { "\n\n" }, StringSplitOptions.RemoveEmptyEntries)
        .Select(p => p.Trim())
        .Where(p => p.Length > 0)
        .ToList();

    var partialSummaries = new List<string>();
    var sb = new System.Text.StringBuilder();

    foreach (var paragraph in chunks)
    {
        sb.Append(paragraph);
        if (sb.Length > chunkSize)
        {
            partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));
            sb.Clear();
        }
    }

    if (sb.Length > 0)
        partialSummaries.Add(Summarize(sb.ToString(), provider, maxSentences));

    // Final pass to merge chunk summaries
    return Summarize(string.Join(" ", partialSummaries), provider, maxSentences);
}
```

## Bước 5: Hiển thị bản tóm tắt kết quả

Cuối cùng, ghi bản tóm tắt ra console hoặc lưu nó ở bất kỳ nơi nào bạn cần.

```csharp
// Display the resulting summary
Console.WriteLine("Summary:\n" + summary);
```

### Đầu ra dự kiến

```
Summary:
The report highlights a 12% revenue increase driven by new product launches. Customer churn dropped to 3% after the recent support improvements. Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will focus on expanding into APAC markets. Overall, the company is on track to exceed its annual targets.
```

Cách diễn đạt chính xác sẽ khác nhau tùy vào nhà cung cấp AI, nhưng cấu trúc (≤ 5 câu) vẫn nhất quán.

## Chương trình chạy đầy đủ

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Xceed.Words.NET;               // DocX
using OpenAI;                       // OpenAI SDK
using OpenAI.Chat;                  // Chat classes
using Google.Cloud.AIPlatform.V1;   // Google Vertex AI SDK
using Google.Protobuf;              // Value type

enum SummarizerProvider { OpenAI, Google }

static class DocumentSummarizer
{
    public static string Summarize(string text, SummarizerProvider provider, int maxSentences = 5)
        => provider switch
        {
            SummarizerProvider.OpenAI => SummarizeWithOpenAI(text, maxSentences),
            SummarizerProvider.Google => SummarizeWithGoogle(text, maxSentences),
            _ => throw new NotSupportedException("Unsupported provider.")
        };

    private static string SummarizeWithOpenAI(string text, int maxSentences)
    {
        var apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                     ?? throw new InvalidOperationException("OpenAI API key missing.");
        var client = new OpenAIClient(apiKey);
        var request = new ChatRequest
        {
            Model = "gpt-4o-mini",
            Messages =
            {
                new ChatMessage(ChatMessageRole.System,
                    "You are a helpful assistant that creates concise summaries."),
                new ChatMessage(ChatMessageRole.User,
                    $"Summarize the following text in no more than {maxSentences} sentences:\n\n{text}")
            }
        };
        var response = client.ChatEndpoint.GetCompletionAsync(request).Result;
        return response.FirstChoice.Message.Content.Trim();
    }

    private static string SummarizeWithGoogle(string text, int maxSentences)
    {
        var client = new PredictionServiceClientBuilder().Build();
        var request = new PredictRequest
        {
            Endpoint = "projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison",
            Instances = { new Value { StringValue = $"Summarize in {maxSentences} sentences: {text}" } }
        };
        var response = client.Predict(request);
        return response.Predictions[0].StringValue.Trim();
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Load the source document you want to summarize
        var doc = Document.Load("input.docx");
        string rawText = doc.Text;

        // Step 2: Choose the AI provider for summarization (OpenAI or Google)
        SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google

        // Step 3: Generate a concise summary with a maximum of 5 sentences
        string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + summary);
    }
}
```

Lưu tệp dưới tên `Program.cs`, đặt một `

## Bạn nên học gì tiếp theo?

Các hướng dẫn sau đây bao gồm các chủ đề liên quan chặt chẽ, xây dựng trên các kỹ thuật được trình bày trong hướng dẫn này. Mỗi tài nguyên bao gồm các ví dụ mã hoàn chỉnh, hoạt động được kèm theo giải thích từng bước để giúp bạn nắm vững các tính năng API bổ sung và khám phá các cách triển khai thay thế trong dự án của mình.

- [Tóm tắt tài liệu Word trong C# với Aspose.Words API – Hướng dẫn AI‑Powered đầy đủ](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Tạo tài liệu Word mới](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Tạo và định dạng tài liệu Word trong Aspose.Words cho .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}