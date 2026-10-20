---
category: general
date: 2026-07-16
description: 使用 C# 通过 AI 对文本进行摘要。了解如何从 Word 生成摘要并在几步内加载 Word 文档（C#）。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize text with ai
- generate summary from word
- load word document c#
- ai summarizer c#
- word document processing c#
- text summarization api
language: zh
lastmod: 2026-07-16
og_description: 使用 C# 的 AI 对文本进行摘要。遵循本指南从 Word 文件生成摘要，并快速学习如何在 C# 中加载 Word 文档。
og_image_alt: Screenshot of C# code that loads a Word document and produces an AI‑generated
  summary
og_title: 使用 C# AI 对文本进行摘要 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Summarize text with AI using C#. Learn how to generate summary from
    Word and load Word document C# in just a few steps.
  headline: Summarize Text with AI in C# – Complete Programming Guide
  type: TechArticle
tags:
- C#
- AI
- Word
title: 使用 AI 在 C# 中进行文本摘要 – 完整编程指南
url: /zh/net/ai-powered-document-processing/summarize-text-with-ai-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 AI 在 C# 中摘要文本 – 完整编程指南

是否曾想过在不离开 IDE 的情况下 **summarize text with AI**？也许你手头有一堆 *.docx* 报告，需要快速生成执行摘要。好消息是，你可以全部在 C# 中完成——加载 Word 文档，调用 AI 摘要接口，打印整洁的五句概览。

在本教程中，我们将通过一个真实案例演示如何 **generate summary from Word** 文件以及 **load Word document C#** 代码，兼容 OpenAI 与 Google 模型。完成后，你将拥有一个可直接放入任意 .NET 项目的独立控制台应用。

> **你将收获**  
> • 一个可直接运行的 C# 程序，读取 *.docx* 文件。  
> • 一个可复用的 `Summarize` 方法，用于调用 AI 服务。  
> • 处理文件缺失、模型选择和 token 限制的实用技巧。

---

## 前置条件 — 开始之前你需要准备的内容

| 要求 | 为什么重要 |
|------|------------|
| .NET 6 或更高版本 | 支持现代语言特性和 `async`。 |
| NuGet 包：`Aspose.Words`（或 `DocumentFormat.OpenXml`），`System.Net.Http.Json` | `Aspose.Words` 提供本文示例中的 `Document` 类；`HttpClient` 负责 API 调用。 |
| OpenAI 或 Google Vertex AI 的 API 密钥 | 摘要服务需要模型端点，你需要在代码中填入密钥。 |
| 一个示例 Word 文件（`report.docx`），放在可引用的文件夹中 | 本教程使用 `load word document c#` 演示文件 I/O。 |

如果缺少上述任意项，请立即安装——步骤简单，毫无压力。

---

## 第一步 – 在 C# 中加载 Word 文档  

首先要做的就是 **load Word document C#**。使用 Aspose.Words，只需创建指向磁盘文件的 `Document` 实例即可。

```csharp
using Aspose.Words;
using System;
using System.IO;

// Ensure the file exists before we try to open it.
string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
if (!File.Exists(filePath))
{
    Console.Error.WriteLine($"❌ File not found: {filePath}");
    return;
}

// Step 1: Load the source document
Document doc = new Document(filePath);
Console.WriteLine("✅ Document loaded successfully.");
```

**为什么重要：**  
* `Document` 对象抽象了 *.docx* 文件背后的 XML，让我们后续可以把内容当作纯文本处理。  
* 检查文件是否存在可以避免 `FileNotFoundException`，这是在生产脚本中 **load word document c#** 时常见的坑。

---

## 第二步 – 提取纯文本用于摘要  

AI 模型无法理解 Word 的内部标记，需要干净的文本。Aspose 提供 `Document.GetText()`，返回整个文档的字符串。

```csharp
// Extract raw text – this strips out tables, images, and formatting.
string rawText = doc.GetText();
if (string.IsNullOrWhiteSpace(rawText))
{
    Console.Error.WriteLine("⚠️ Document appears empty after extraction.");
    return;
}
Console.WriteLine($"📝 Extracted {rawText.Length:N0} characters of text.");
```

**小技巧：** 如果需要保留标题，可遍历 `doc.GetChildNodes(NodeType.Paragraph, true)`，仅拼接样式为 “Heading” 的段落。这样摘要就能遵循文档结构。

---

## 第三步 – 定义摘要选项  

接下来进入本教程的核心：**summarize text with AI**。我们将选项封装在一个小 POCO 中，便于在不修改 HTTP 调用代码的情况下调节模型、最大句数和 temperature。

```csharp
public enum SummarizationModel
{
    OpenAI,
    Google
}

public class SummarizationOptions
{
    public int MaxSentences { get; set; } = 5;
    public SummarizationModel Model { get; set; } = SummarizationModel.OpenAI;
    public double Temperature { get; set; } = 0.7; // Controls creativity
}
```

现在可以创建一个选项实例，明确告诉 AI 你的需求：

```csharp
// Step 2: Define summarization options (e.g., limit to 5 sentences, choose a model)
SummarizationOptions options = new SummarizationOptions
{
    MaxSentences = 5,
    Model = SummarizationModel.OpenAI   // switch to Google if you prefer
};
```

**为什么要公开这些设置：**  
* 不同项目对简洁度的要求不同——有的需要两句 TL;DR，有的需要五句执行摘要。  
* 只需更改一个 enum 值即可在 `OpenAI` 与 `Google` 模型之间切换，方便进行 A/B 测试。

---

## 第四步 – 实现 `Summarize` 方法  

下面是一段 **完整、可运行** 的实现，能够调用 OpenAI 的 `chat/completions` 接口或 Google Vertex AI 的 `text-bison` 模型。为简洁起见，使用了带 `System.Net.Http.Json` 的 `HttpClient`。

```csharp
using System.Net.Http;
using System.Net.Http.Json;
using System.Threading.Tasks;

public static class AiSummarizer
{
    private static readonly HttpClient http = new HttpClient();

    public static async Task<string> SummarizeAsync(string text, SummarizationOptions opts)
    {
        // Choose endpoint and payload based on the selected model.
        if (opts.Model == SummarizationModel.OpenAI)
        {
            // OpenAI expects a messages array; we use a system prompt to enforce sentence limit.
            var request = new
            {
                model = "gpt-4o-mini",
                temperature = opts.Temperature,
                messages = new[]
                {
                    new { role = "system", content = $"Summarize the following text in no more than {opts.MaxSentences} sentences." },
                    new { role = "user", content = text }
                },
                max_tokens = 500
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("OPENAI_API_KEY"));

            var response = await http.PostAsJsonAsync("https://api.openai.com/v1/chat/completions", request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            return (string)json.choices[0].message.content;
        }
        else // Google Vertex AI
        {
            var request = new
            {
                instances = new[] { new { content = text } },
                parameters = new
                {
                    temperature = opts.Temperature,
                    maxOutputTokens = 500,
                    topK = 40,
                    topP = 0.95,
                    // Vertex AI doesn’t have a built‑in sentence limit, so we post‑process later.
                }
            };

            http.DefaultRequestHeaders.Authorization =
                new System.Net.Http.Headers.AuthenticationHeaderValue("Bearer", Environment.GetEnvironmentVariable("GOOGLE_API_KEY"));

            var response = await http.PostAsJsonAsync(
                "https://us-central1-aiplatform.googleapis.com/v1/projects/YOUR_PROJECT/locations/us-central1/publishers/google/models/text-bison-001:predict",
                request);
            response.EnsureSuccessStatusCode();

            var json = await response.Content.ReadFromJsonAsync<dynamic>();
            string raw = (string)json.predictions[0].content;
            // Simple post‑processing: keep only the first N sentences.
            return string.Join(' ', raw.Split('.').Take(opts.MaxSentences)).Trim() + ".";
        }
    }
}
```

**“为什么”解释**  
* **模型无关设计** – 同一方法兼容 OpenAI 与 Google，保持代码库整洁。  
* **环境变量存放密钥** – 硬编码 API 密钥存在安全风险，使用 `Environment.GetEnvironmentVariable` 符合最佳实践。  
* **句子数限制** – OpenAI 可以直接在系统提示中限定；Google 需要在返回后进行简短的后处理，因为其 API 本身不支持句子上限。

---

## 第五步 – 将所有环节串联并输出摘要  

现在把各部分组合起来：读取文档，将文本传入 `SummarizeAsync`，并打印结果。

```csharp
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // Load the document (Step 1)
        string filePath = Path.Combine(Environment.CurrentDirectory, "report.docx");
        if (!File.Exists(filePath))
        {
            Console.Error.WriteLine($"❌ Cannot find {filePath}");
            return;
        }
        Document doc = new Document(filePath);

        // Extract raw text (Step 2)
        string rawText = doc.GetText();

        // Define options (Step 3)
        SummarizationOptions options = new SummarizationOptions
        {
            MaxSentences = 5,
            Model = SummarizationModel.OpenAI   // Change to Google if you prefer
        };

        // Generate the summary (Step 4)
        string summary = await AiSummarizer.SummarizeAsync(rawText, options);

        // Step 5: Output the generated summary
        Console.WriteLine("\n=== AI‑Generated Summary ===\n");
        Console.WriteLine(summary);
    }
}
```

### 预期输出

假设 `report.docx` 包含一份两页的业务分析，控制台可能显示：

```
=== AI‑Generated Summary ===

The quarterly sales increased by 12% YoY, driven primarily by the new product line. Customer churn fell to 3%, the lowest in five years. Marketing spend rose 8% but delivered a 15% lift in brand awareness. Operational efficiencies saved $1.2M, mainly through supply‑chain automation. The outlook for Q3 remains positive, with projected growth of 10‑15%.
```

如果将 `options.Model` 改为 `SummarizationModel.Google`，你会看到类似的简洁段落——只是表达风格不同。

---

## 处理边缘情况与常见陷阱  

| 场景 | 需要关注的点 | 快速解决方案 |
|------|--------------|--------------|
| **超大文档（>10 k tokens）** | API 可能拒绝请求或截断输出。 | 将文本按逻辑段落（如标题）拆分，分别摘要后再合并。 |
| **缺失或无效的 API 密钥** | 401 Unauthorized 错误。 | 确认 `OPENAI_API_KEY` / `GOOGLE_API_KEY` 已在环境变量中设置，或使用 `appsettings.json` 进行本地开发。 |
| **非英文 Word 文件** | Summar |

## 接下来你可以学习什么？

以下教程与本指南紧密相关，帮助你进一步掌握 API 功能并探索在项目中的其他实现方式。每篇资源均提供完整可运行的代码示例和逐步解释。

- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Ranges Get Text In Word Document](/words/english/net/programming-with-ranges/ranges-get-text/)
- [Copy Bookmarked Text In Word Document](/words/english/net/programming-with-bookmarks/copy-bookmarked-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}