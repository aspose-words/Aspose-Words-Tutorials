---
category: general
date: 2026-09-14
description: 使用 C# 的 AI 对 Word 文档进行摘要——学习如何使用 OpenAI 或 Google 提供商生成简洁的摘要，并了解如何仅用几行代码使用
  AI 对文本进行摘要。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize word document
- summarize text with ai
- document summarization google
language: zh
lastmod: 2026-09-14
og_description: 使用 C# 的 AI 对 Word 文档进行摘要。本教程展示了如何调用 OpenAI 或 Google 的摘要服务并获得简洁的结果。
og_image_alt: Console window displaying a short AI‑generated summary of a Word document
og_title: 使用 AI 摘要 Word 文档 – 快速 C# 指南
schemas:
- author: GroupDocs
  dateModified: '2026-09-14'
  description: Summarize Word document using AI in C# – learn to generate concise
    summaries with OpenAI or Google providers and see how to summarize text with AI
    in just a few lines.
  headline: Summarize Word document with AI in C#
  type: TechArticle
- description: Summarize Word document using AI in C# – learn to generate concise
    summaries with OpenAI or Google providers and see how to summarize text with AI
    in just a few lines.
  name: Summarize Word document with AI in C#
  steps:
  - name: Load the source `.docx` file.
    text: Load the source `.docx` file.
  - name: Define summarization options (provider and sentence limit).
    text: Define summarization options (provider and sentence limit).
  - name: Call the summarizer to produce a short text.
    text: Call the summarizer to produce a short text.
  - name: Write the result to the console.
    text: Write the result to the console.
  type: HowTo
tags:
- AI summarization
- C#
- Word processing
title: 在 C# 中使用 AI 摘要 Word 文档
url: /zh/net/ai-powered-document-processing/summarize-word-document-with-ai-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 和 AI 摘要 Word 文档

如果您需要 **自动摘要 Word 文档** 内容，本指南提供了一个完整、可直接运行的解决方案。您将看到如何加载 `.docx` 文件、配置摘要请求，并使用 OpenAI 或 Google 作为 AI 提供商获取简洁的摘要。

示例基于流行的 `GroupDocs.Summarization` 库，但相同的模式同样适用于任何提供 `DocumentSummarizer` API 的库。完成本教程后，您只需几行 C# 代码即可 **使用 AI 摘要文本**。

## 您将学到的内容

- 安装所需的 NuGet 包。
- 将 Word 文档（`.docx`）加载到内存中。
- 选择摘要提供商（OpenAI 或 Google）并设置句子上限。
- 生成摘要并在控制台显示。
- 处理常见错误，如文件缺失或不受支持的提供商。

> **先决条件：** .NET 6 或更高版本、基本的 C# 知识，以及所选提供商（OpenAI 或 Google）的 API 密钥。

## 安装摘要库

首先，将 `GroupDocs.Summarization` 包添加到您的项目中：

```bash
dotnet add package GroupDocs.Summarization
```

该包包含后续代码中使用的 `Document`、`SummarizerOptions` 和 `DocumentSummarizer` 类型。

## 摘要 Word 文档 – 概览

核心工作流包括四个步骤：

1. 加载源 `.docx` 文件。
2. 定义摘要选项（提供商和句子上限）。
3. 调用摘要器生成简短文本。
4. 将结果写入控制台。

下面将详细说明每一步。

## 步骤 1：加载源文档

```csharp
using System;
using GroupDocs.Summarization;
using GroupDocs.Summarization.Options;

class Program
{
    static void Main()
    {
        // Replace with the actual path to your .docx file
        const string inputPath = @"C:\Docs\input.docx";

        // Verify that the file exists before attempting to load it
        if (!System.IO.File.Exists(inputPath))
        {
            Console.Error.WriteLine($"Error: The file \"{inputPath}\" was not found.");
            return;
        }

        // Load the Word document into a Document object
        Document doc = new Document(inputPath);
        Console.WriteLine("Document loaded successfully.");
```

**为什么重要：** 将文件加载为 `Document` 对象可以抽象底层的 Word 格式，使摘要器能够在不考虑表格、图像或脚注的情况下处理纯文本。

## 步骤 2：定义摘要选项（选择提供商并限制句子数）

```csharp
        // Configure summarization settings
        SummarizerOptions options = new SummarizerOptions
        {
            // Switch between OpenAI and Google providers as needed
            Provider = SummarizerProvider.OpenAI,   // or SummarizerProvider.Google
            MaxSentences = 5                        // Desired number of sentences in the summary
        };

        Console.WriteLine($"Summarization will use {options.Provider} and return up to {options.MaxSentences} sentences.");
```

**为什么重要：**  
- **提供商选择** 决定了哪个 AI 服务处理文本。OpenAI 和 Google 模型接受相同的输入，但在价格、延迟和语言覆盖范围上有所不同。  
- **`MaxSentences`** 让您控制输出长度，这在只需要快速预览而非完整摘要时尤为关键。

## 步骤 3：使用选定的 AI 提供商生成摘要

```csharp
        try
        {
            // The static Summarize method contacts the chosen AI service and returns a concise summary
            string summary = DocumentSummarizer.Summarize(doc, options);
            Console.WriteLine("\nSummary:");
            Console.WriteLine(summary);
        }
        catch (Exception ex)
        {
            // Provide a clear error message for common failure points
            Console.Error.WriteLine($"Summarization failed: {ex.Message}");
        }
    }
}
```

**为什么重要：** `Summarize` 调用完成所有繁重工作——分词、模型推理和后处理——您无需自行编写提示或管理 HTTP 请求。`try/catch` 代码块确保网络错误、认证问题或不受支持的文档特性能够清晰报告。

## 步骤 4：将生成的摘要输出到控制台

前一步中的 `Console.WriteLine` 已经显示了结果，您也可以将摘要写入文件以便后续分析：

```csharp
        // Optional: save the summary to a .txt file
        const string outputPath = @"C:\Docs\summary.txt";
        System.IO.File.WriteAllText(outputPath, summary);
        Console.WriteLine($"\nSummary saved to \"{outputPath}\".");
```

**为什么重要：** 持久化摘要可用于批处理流水线，例如为数十个文档生成摘要并将其与原始文件一起存储。

## 使用 OpenAI 摘要文本的方式

如果您倾向于使用 OpenAI 的 GPT‑4 模型，请显式设置提供商：

```csharp
options.Provider = SummarizerProvider.OpenAI;
```

确保已定义环境变量 `OPENAI_API_KEY`，或以编程方式配置密钥：

```csharp
SummarizerOptions.ApiKey = "sk-YourOpenAIKey";
```

OpenAI 通常生成更流畅的 prose，适用于营销文案或高管简报。

## 文档摘要 Google – 使用 Google 提供商

对于已经在 Google Cloud 上投入的组织，可切换到 Google 提供商：

```csharp
options.Provider = SummarizerProvider.Google;
```

设置 Google API 密钥：

```csharp
SummarizerOptions.ApiKey = "AIzaYourGoogleKey";
```

Google 的 PaLM 模型在多语言摘要方面表现出色，并且在大批量工作负载下可能更具成本效益。

## 边缘情况和最佳实践提示

| 情况 | 推荐处理方式 |
|-----------|----------------------|
| **大文档 (>10 MB)** | 增加 `MaxSentences` 或将文档拆分为多个章节分别摘要，以避免令牌限制。 |
| **缺少 API 密钥** | 库会抛出 `AuthenticationException`。在调用 `Summarize` 前验证密钥。 |
| **不受支持的文件格式** | `Document` 仅支持 `.docx`、`.pdf` 和纯文本。请先使用转换库将其他格式（如 `.doc`）转换为 `.docx`。 |
| **网络延迟** | 若应用必须保持响应，可将调用包装为异步版本 (`SummarizeAsync`)。 |

**专业提示：** 为不常更改的文档缓存摘要。存储文件内容的哈希并复用缓存结果，以避免不必要的 API 调用。

## 完整、可运行的示例

下面是完整程序，您可以复制粘贴到新建的控制台项目（`dotnet new console`）中，在安装 NuGet 包并设置 API 密钥后运行：

```csharp
using System;
using GroupDocs.Summarization;
using GroupDocs.Summarization.Options;

namespace WordSummarizer
{
    class Program
    {
        static void Main()
        {
            const string inputPath = @"C:\Docs\input.docx";
            const string outputPath = @"C:\Docs\summary.txt";

            if (!System.IO.File.Exists(inputPath))
            {
                Console.Error.WriteLine($"Error: The file \"{inputPath}\" was not found.");
                return;
            }

            Document doc = new Document(inputPath);
            Console.WriteLine("Document loaded successfully.");

            SummarizerOptions options = new SummarizerOptions
            {
                Provider = SummarizerProvider.OpenAI, // change to Google if preferred
                MaxSentences = 5
            };

            // Set your API key (environment variable or direct assignment)
            // SummarizerOptions.ApiKey = "YOUR_API_KEY";

            try
            {
                string summary = DocumentSummarizer.Summarize(doc, options);
                Console.WriteLine("\nSummary:");
                Console.WriteLine(summary);

                System.IO.File.WriteAllText(outputPath, summary);
                Console.WriteLine($"\nSummary saved to \"{outputPath}\".");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Summarization failed: {ex.Message}");
            }
        }
    }
}
```

**预期输出（示例）：**

```
Document loaded successfully.
Summarization will use OpenAI and return up to 5 sentences.

Summary:
The report outlines Q3 revenue growth of 12% driven by new product launches. Customer churn decreased to 3%, the lowest in two years. Marketing spend rose by 8% to support brand awareness. The executive team recommends expanding into the APAC market. Risks include supply‑chain delays and regulatory changes.
```

## 结论

现在，您拥有了一套完整、可投入生产的 **使用 AI 摘要 Word 文档** 方法。只需将 `SummarizerProvider.OpenAI` 替换为 `SummarizerProvider.Google`，即可实现 **Google 文档摘要** 风格，而无需更改其他代码。尝试不同的 `MaxSentences` 值、批量处理，或将摘要集成到更大的工作流中，例如邮件通知或知识库更新。

**后续步骤**  
- 探索异步 API (`SummarizeAsync`) 以应对高吞吐场景。  
- 将摘要与关键词提取结合，构建可搜索的索引。  
- 使用相同模式 **使用 AI 摘要文本**，处理纯 `.txt` 文件或网页。

祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在项目中进一步掌握 API 功能并探索替代实现方式。每个资源都提供完整的可运行代码示例和逐步解释。

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Word Document - Find And Replace Text](/words/english/net/find-and-replace-text/)
- [Ranges Get Text In Word Document](/words/english/net/programming-with-ranges/ranges-get-text/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}