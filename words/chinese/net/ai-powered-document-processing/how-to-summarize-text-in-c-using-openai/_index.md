---
category: general
date: 2026-09-11
description: 学习如何在 C# 中读取 API 密钥、调用 OpenAI，并生成 Word 文档的简洁摘要。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to summarize text
- summarize word document
- read api key
- how to create summary
- how to call openai
language: zh
lastmod: 2026-09-11
og_description: 如何在 C# 中摘要文本？本教程展示了如何读取 API 密钥、调用 OpenAI 并创建 Word 文档的摘要。
og_image_alt: Diagram showing C# code flow that reads an API key, calls OpenAI, and
  outputs a document summary
og_title: 使用 OpenAI 在 C# 中进行文本摘要 – 步骤指南
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
title: 如何在 C# 中使用 OpenAI 对文本进行摘要
url: /zh/net/ai-powered-document-processing/how-to-summarize-text-in-c-using-openai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 OpenAI 对文本进行摘要

如果你需要 **how to summarize text** 在 .docx 文件中，本指南提供了一个完整、可直接运行的解决方案。你将学习如何从环境变量读取 API 密钥、如何在 C# 中调用 OpenAI（或 Google），以及如何为 Word 文档生成简洁的摘要。

对 Word 文档进行摘要是报告生成、邮件摘要或知识库抽取的常见需求。完成本教程后，你将拥有一个命令行程序，能够打印任意 `.docx` 文件的五句摘要。

## 前置条件

- .NET 6.0 SDK 或更高版本（从 [dotnet.microsoft.com](https://dotnet.microsoft.com/download) 下载）
- 已在环境变量 `OPENAI_API_KEY` 中存储的有效 OpenAI API 密钥（你将在演示中看到 **read api key** 的实际操作）
- 用于读取 `.docx` 文件的 `DocumentFormat.OpenXml` NuGet 包
- `OpenAI` NuGet 包（如果你更倾向于使用 Google，则使用 `Google.AI`）

## 步骤 1：创建项目并安装依赖

创建一个新的控制台项目并添加所需的包：

```bash
dotnet new console -n SummarizerDemo
cd SummarizerDemo
dotnet add package DocumentFormat.OpenXml
dotnet add package OpenAI
# Optional: dotnet add package Google.AI
```

> **专业提示：** 如果以后添加更多依赖，建议将相关包放在同一个 `<ItemGroup>` 中，以保持 `csproj` 整洁。

## 步骤 2：安全读取 API 密钥

硬编码密钥是不安全的。教程演示了从环境变量 **read api key** 的正确做法。

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

## 步骤 3：加载需要摘要的 Word 文档

下面的代码展示了 **how to summarize word document** 内容的实现方式，即从 OpenXML 结构中提取纯文本。

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

## 步骤 4：构建可复用的摘要类

该类封装了 **how to call openai**（或 Google）的调用，并实现了 **how to create summary** 的逻辑。通过一个枚举值，你可以轻松切换提供者。

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

### 为什么这种结构很重要

- **关注点分离：** 文档加载、API 密钥读取以及 AI 服务调用各自独立为方法，使代码更易于测试和扩展。
- **提供者灵活性：** 使用枚举即可在 OpenAI 与 Google 之间切换，而无需修改调用代码，这直接实现了 **how to call openai** 和 **how to create summary** 的可复用方式。
- **错误处理：** 缺失 API 密钥时会抛出明确异常，避免静默失败。

## 步骤 5：在 `Program.cs` 中整合所有代码

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

### 预期输出

使用示例文档运行程序：

```bash
dotnet run -- "sample/input.docx"
```

可能得到的结果如下：

```
Summary:
The report outlines quarterly sales growth, highlighting a 12% increase in the North American market. 
Key challenges include supply‑chain delays and rising material costs. 
Customer feedback indicates higher satisfaction with the new product line. 
Recommendations focus on expanding the digital sales channel and optimizing inventory levels. 
Overall, the company is positioned for continued growth in the next fiscal year.
```

## 步骤 6：常见变体和边界情况

| 情况 | 推荐调整 |
|-----------|------------------------|
| **大文档**（ > 10 KB） | 将文本拆分为块，分别摘要后再合并结果。 |
| **非英文内容** | 在提示中加入语言提示，例如 “Summarize the following French text …”。 |
| **Google 提供者** | 将 `SummarizeWithOpenAIAsync` 调用替换为相应的 Google API 客户端；保持相同的枚举接口。 |
| **自定义摘要长度** | 在调用 `SummarizeAsync` 时更改 `maxSentences` 参数。 |
| **缺失 API 密钥** | `GetOpenAIApiKey` 方法已经会抛出明确异常；如需更友好的提示，可在 `Main` 中捕获。 |

## 生产环境使用的专业提示

1. **缓存 API 密钥** – 每次读取环境变量的开销可以忽略不计，但如果在同一进程中多次调用摘要器，可将其存入 `static readonly` 字段。
2. **限流请求** – OpenAI 对请求频率有限制；若遇到 `429 Too Many Requests`，请实现指数退避。  
3. **清理输入** – 在将文本发送至外部 AI 服务前，去除个人身份信息。  
4. **单元测试提取逻辑** – 使用 mock 的 `WordprocessingDocument` 验证 `ExtractTextFromDocx` 在不同文档结构下的表现。

## 结论

现在，你已经掌握了 **how to summarize text** 在 C# 中的实现方法：安全读取 API 密钥、调用 OpenAI，并为 Word 文档生成简洁摘要。同样的模式也可以让你 **how to call openai** 使用其他提供者、实现 **how to create summary** 的不同内容类型，并安全地 **read api key** 环境变量。尝试更长的文档、不同的提供者或自定义提示，以便将摘要功能细化到你的特定领域。

---


## 接下来你应该学习什么？

以下教程涵盖了与本指南技术密切相关的主题，帮助你在项目中进一步运用这些技巧。每篇资源都提供了完整的可运行代码示例和逐步解释，帮助你掌握更多 API 功能并探索替代实现方案。

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [how to create pdf from Word – Complete C# Guide](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Word Document - How to Remove Content](/words/english/net/remove-content/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}