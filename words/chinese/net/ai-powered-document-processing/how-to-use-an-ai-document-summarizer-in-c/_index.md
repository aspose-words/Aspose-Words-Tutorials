---
category: general
date: 2026-09-21
description: 学习如何使用 C# 构建一个 AI 文档摘要器，利用 OpenAI 或 Google API 从 Word 文件生成摘要。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- ai document summarizer
- ai powered summarization
- create summary from word
- summarize docx with ai
- summarize using google
language: zh
lastmod: 2026-09-21
og_description: C# 的 AI 文档摘要工具让您快速从 Word 文件生成摘要。请按照本指南使用 OpenAI 或 Google 进行 AI 驱动的摘要。
og_image_alt: Diagram showing the workflow of an ai document summarizer processing
  a Word file
og_title: 在 C# 中构建 AI 文档摘要器 – 步骤指南
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
title: 如何在 C# 中使用 AI 文档摘要器
url: /zh/net/ai-powered-document-processing/how-to-use-an-ai-document-summarizer-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 ai document summarizer

如果您需要用于 .docx 文件的 **ai document summarizer**，本指南将向您展示如何使用 C# 从 Word 创建摘要。您将看到一个完整、可运行的示例，支持 OpenAI 或 Google，几分钟内即可获得 **ai powered summarization** 解决方案。

本教程涵盖从项目设置到处理边缘情况的全部内容，让您能够自信地在自己的应用中 **summarize docx with ai**。无需外部脚本——只需几个 NuGet 包和一小段代码片段。

## 您需要的条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Core 3.1+）
- OpenAI API 密钥 **或** Google Cloud Vertex AI 密钥
- `DocX` NuGet 包用于读取 Word 文件
- `OpenAI` 或 `Google.Cloud.AIPlatform.V1` NuGet 包用于所选提供商
- 开发环境，例如 Visual Studio 2022 或 VS Code

## 步骤 1：设置 ai document summarizer 环境

首先，创建一个新的控制台项目并添加所需的包：

```bash
dotnet new console -n AiSummarizerDemo
cd AiSummarizerDemo
dotnet add package DocX --version 1.0.0
dotnet add package OpenAI --version 2.5.0   # for OpenAI
dotnet add package Google.Cloud.AIPlatform.V1 --version 2.6.0   # for Google
```

> **技巧提示：** 将 API 密钥保存在环境变量 (`OPENAI_API_KEY`, `GOOGLE_APPLICATION_CREDENTIALS`) 中，而不是硬编码。

## 步骤 2：加载 Word 文档以 **create summary from word**

第一行功能代码读取源 `.docx` 文件。使用 `DocX` 提取纯文本，随后 AI 模型将对其进行摘要。

```csharp
using System;
using System.IO;
using Xceed.Words.NET;   // DocX namespace

// Load the source document you want to summarize
Document document = Document.Load("input.docx");

// Extract raw text for the summarizer
string rawText = document.Text;
```

> **此步骤重要原因：** AI 模型在干净、线性的文本上表现最佳。去除格式可避免 token 限额的意外，并提升摘要的相关性。

## 步骤 3：选择 **ai powered summarization** 提供商

通过设置 `SummarizerProvider` 枚举，您可以在 OpenAI 的 GPT‑4 与 Google 的 PaLM 模型之间切换。该枚举抽象了特定提供商的实现逻辑。

```csharp
enum SummarizerProvider
{
    OpenAI,
    Google
}

// Choose the provider (replace with your preference)
SummarizerProvider provider = SummarizerProvider.OpenAI; // or SummarizerProvider.Google
```

### 提供商实现细节

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

> **我们抽象提供商的原因：** 该模式使您能够 **summarize using google** 或 OpenAI，而无需更改调用代码——便于后期测试或切换提供商。

## 步骤 4：生成简洁摘要 – **summarize docx with ai**

现在调用辅助方法，将输出限制为五句话（可通过 `maxSentences` 调整）。

```csharp
// Generate a concise summary with a maximum of 5 sentences
string summary = DocumentSummarizer.Summarize(rawText, provider, maxSentences: 5);
```

### 处理 token 限额和大文档

如果源文档超过模型的 token 配额，可将其拆分为段落，分别对每个块进行摘要，然后合并块摘要。这样可确保在大多数模型中永不超过 8 k‑token 限额。

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

## 步骤 5：显示生成的摘要

最后，将摘要写入控制台或存储到您需要的位置。

```csharp
// Display the resulting summary
Console.WriteLine("Summary:\n" + summary);
```

### 预期输出

```
Summary:
The report highlights a 12% revenue increase driven by new product launches. Customer churn dropped to 3% after the recent support improvements. Marketing spend rose by 8% but delivered a 15% ROI. The upcoming quarter will focus on expanding into APAC markets. Overall, the company is on track to exceed its annual targets.
```

具体措辞会因 AI 提供商而异，但结构（≤ 5 句）保持一致。

## 完整可运行程序

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

将文件保存为 `Program.cs`，放置一个 `

## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步学习。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方案。

- [使用 Aspose.Words API 在 C# 中摘要 Word 文档 – 完整 AI 驱动指南](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [创建新 Word 文档](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [在 Aspose.Words for .NET 中创建并设置 Word 文档样式](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}