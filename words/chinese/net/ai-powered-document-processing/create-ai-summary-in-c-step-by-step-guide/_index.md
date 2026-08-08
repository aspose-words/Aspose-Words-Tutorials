---
category: general
date: 2026-08-07
description: 使用 OpenAI 在 C# 中创建 AI 摘要，快速对 Word 文档进行概括。了解如何设置 OpenAI API 密钥并实现文档摘要自动化。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create AI summary
- summarize Word document
- set OpenAI API key
- generate summary OpenAI
- automate document summarization
language: zh
lastmod: 2026-08-07
og_description: 使用 C# 创建 AI 摘要，瞬间概括 Word 文档。按照本教程设置 OpenAI API 密钥，生成 OpenAI 摘要，并实现文档摘要自动化。
og_image_alt: Console window displaying the generated AI summary of a Word document
og_title: 在 C# 中创建 AI 摘要 – 开发者完整指南
schemas:
- author: GroupDocs
  dateModified: '2026-08-07'
  description: Create AI summary in C# to quickly summarize a Word document using
    OpenAI. Learn how to set OpenAI API key and automate document summarization.
  headline: Create AI summary in C# – step‑by‑step guide
  type: TechArticle
tags:
- AI
- C#
- Document processing
- OpenAI
- Automation
title: 使用 C# 创建 AI 摘要——一步一步指南
url: /zh/net/ai-powered-document-processing/create-ai-summary-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 创建 AI 摘要 – 步骤指南

如果您需要对大型 Word 文件 **创建 AI 摘要**，本教程将向您展示如何使用 C# 和 GroupDocs AI SDK 完成此操作。您将学习如何 **summarize Word document** 内容、**set OpenAI API key**，以及 **automate document summarization** 以实现可重复的工作流。

我们将逐步演示每个必需的步骤，解释每个环节的重要性，并提供一个完整、可运行的控制台应用程序。完成后，您将拥有一个可自行包含的解决方案，可直接嵌入任何 .NET 项目中。

## 前置条件

在开始之前，请确保您具备以下条件：

* .NET 6.0 SDK 或更高版本已安装  
* 有效的 OpenAI API 密钥（如果您更喜欢，也可以使用 Google Gemini 密钥）  
* 获取 GroupDocs AI for .NET NuGet 包的访问权限  

您可以使用以下命令安装该包：

```bash
dotnet add package GroupDocs.AI.Summarizer
```

> **专业提示：** 使用 *user‑secret* 或环境变量来存储 API 密钥，而不是硬编码。

## 使用 GroupDocs AI SDK 创建 AI 摘要

解决方案的核心是 `DocumentSummarizer` 类，它接受一个 `Document` 对象和一个 `AiSummarizerOptions` 实例。该选项告诉 SDK 使用哪个提供商以及在哪里获取凭证。

```csharp
using System;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Step 1: Load the source Word document
        Document doc = new Document("YOUR_DIRECTORY/LongReport.docx");

        // Step 2: Configure the summarizer (choose provider and supply API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,          // or AiProvider.Google
            ApiKey   = "YOUR_OPENAI_API_KEY"
        };

        // Step 3: Generate the summary using the configured options
        string reportSummary = DocumentSummarizer.Summarize(doc, summarizerOptions);

        // Step 4: Display the resulting summary
        Console.WriteLine("Summary:\n" + reportSummary);
    }
}
```

### 为什么这样可行

* **Loading the document** 将 `.docx` 文件转换为 AI 引擎可读取的格式。  
* **AiSummarizerOptions** 告诉 SDK 调用哪个 LLM 提供商并提供身份验证令牌——这就是您 **set OpenAI API key** 的位置。  
* **DocumentSummarizer.Summarize** 将文档文本发送给所选提供商并返回简洁的摘要。  
* **Console.WriteLine** 打印结果，您随后可以将其导入文件、电子邮件或数据库。

## 为摘要设置 OpenAI API 密钥

硬编码密钥可用于快速演示，但生产代码应将机密信息从源代码控制中剔除。SDK 读取 `ApiKey` 属性，因此您可以从环境变量中获取该值：

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
};
```

将变量添加到系统中：

```bash
# Windows PowerShell
$Env:OPENAI_API_KEY = "sk-xxxxxxxxxxxxxxxxxxxx"

# macOS / Linux
export OPENAI_API_KEY="sk-xxxxxxxxxxxxxxxxxxxx"
```

> **为什么重要：** 安全存储密钥可防止意外泄露，并符合大多数企业安全策略。

## 使用 Generate summary OpenAI 摘要 Word 文档

`DocumentSummarizer` 在内部调用 **Generate summary OpenAI** 端点。如果您希望微调请求，可以通过 `AiSummarizerOptions` 传递额外参数：

```csharp
AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
{
    Provider = AiProvider.OpenAi,
    ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
    Temperature = 0.3,          // Lower temperature for more deterministic output
    MaxTokens   = 250           // Limit the length of the summary
};
```

这些设置帮助您控制返回文本的冗长程度和创造性，在对大量文件 **automate document summarization** 时非常有用。

## 在控制台应用中自动化文档摘要

要在无需人工干预的情况下处理多个文件，可将逻辑包装在循环中，并从文件夹读取路径：

```csharp
string inputFolder = @"YOUR_DIRECTORY";
foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
{
    Document doc = new Document(filePath);
    string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

    string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
    File.WriteAllText(outputPath, summary);
    Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
}
```

### 这带来了什么

* **Batch processing** – 您可以将任意数量的 Word 文件放入文件夹，系统会为每个文件生成 `.summary.txt`。  
* **Error handling** – 您可以使用 `try/catch` 包裹循环，以跳过损坏的文件并记录问题。  
* **Scalability** – 由于 SDK 对每个文档都会发起 HTTP 请求，若您的 OpenAI 配额允许，可使用 `Parallel.ForEach` 并行循环。

## 预期输出

当您使用示例 `LongReport.docx` 运行程序时，控制台会打印类似以下内容：

```
Summary:
The report outlines the quarterly performance of the sales department, highlighting a 12% increase in revenue driven by new product launches. Key challenges include supply‑chain constraints and rising operational costs. Recommendations focus on expanding the digital sales channel and optimizing inventory management.
```

生成的 `.summary.txt` 文件包含相同的文本，可用于后续使用（例如电子邮件通知、知识库导入或 UI 显示）。

## 常见陷阱及避免方法

| 症状 | 原因 | 解决方案 |
|---------|-------|-----|
| *Empty summary* | 文档仅包含图像或表格，且没有可提取的文本。 | 在摘要之前使用 `doc.ExtractText()`，或将图像转换为支持 OCR 的文本。 |
| *Authentication error* | API 密钥错误或缺失。 | 检查 `OPENAI_API_KEY` 环境变量，并确保该密钥具备所需权限。 |
| *Rate‑limit response* | 超过 OpenAI 请求配额。 | 在请求之间添加延迟（`Task.Delay(1000)`），或向 OpenAI 申请更高配额。 |
| *Unexpected language* | 提供商默认使用英语，但源文档为其他语言。 | 设置 `summarizerOptions.Language = "es"`（或相应的 ISO 代码）以强制使用目标语言。 |

## 完整源码供复制粘贴

```csharp
using System;
using System.IO;
using GroupDocs.AI.Summarizer;
using GroupDocs.AI.Summarizer.Options;
using GroupDocs.AI.Summarizer.Providers;

class Program
{
    static void Main()
    {
        // Configure summarizer options (set OpenAI API key)
        AiSummarizerOptions summarizerOptions = new AiSummarizerOptions
        {
            Provider = AiProvider.OpenAi,
            ApiKey   = Environment.GetEnvironmentVariable("OPENAI_API_KEY"),
            Temperature = 0.3,
            MaxTokens   = 250
        };

        // Folder containing Word documents to summarize
        string inputFolder = @"YOUR_DIRECTORY";

        foreach (var filePath in Directory.GetFiles(inputFolder, "*.docx"))
        {
            try
            {
                Document doc = new Document(filePath);
                string summary = DocumentSummarizer.Summarize(doc, summarizerOptions);

                string outputPath = Path.ChangeExtension(filePath, ".summary.txt");
                File.WriteAllText(outputPath, summary);

                Console.WriteLine($"Summarized {Path.GetFileName(filePath)} → {Path.GetFileName(outputPath)}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Failed to process {Path.GetFileName(filePath)}: {ex.Message}");
            }
        }
    }
}
```

> **注意：** 将 `YOUR_DIRECTORY` 替换为保存 `.docx` 文件的文件夹的绝对路径。

![显示 Word 文档生成的 AI 摘要的控制台输出](console-output.png)

## 结论

您现在已经了解如何使用 GroupDocs AI SDK 在 C# 中 **create AI summary** Word 文件，如何 **set OpenAI API key**，以及如何为任意数量的文件 **automate document summarization**。该方法兼容 OpenAI 与 Google 提供商，支持调节生成参数，并能干净地集成到现有 .NET 解决方案中。

**下一步**

* 探索 **summarize Word document** 功能，使用自定义提示控制语气或长度。  
* 将摘要与 **Azure Functions** 或 **AWS Lambda** 结合，构建无服务器摘要服务。  
* 用 ASP.NET Core 实现 REST API 替代控制台输出，实现按需摘要。

祝编码愉快，享受 AI 驱动的摘要为文档工作流带来的生产力提升！

## 您接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中探索替代实现方式。每个资源都提供完整的可运行代码示例和逐步解释。

- [创建新 Word 文档](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [使用 Aspose.Words for .NET 创建 Word 文档](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [在 .NET 中创建带目录的 Word 文档](/words/english/net/add-content-using-document-builder/insert-table-contents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}