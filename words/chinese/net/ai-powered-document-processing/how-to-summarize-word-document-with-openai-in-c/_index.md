---
category: general
date: 2026-10-26
description: 使用 OpenAI 在 C# 中对 Word 文档进行摘要。学习如何加载大型文档、生成摘要，并自动写入摘要文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- summarize word document
- generate summary openai
- write summary file
- load large document
- automate document summarization
language: zh
lastmod: 2026-10-26
og_description: 使用 OpenAI 在 C# 中摘要 Word 文档。本教程将指导您加载大型文档、生成摘要，并自动写入摘要文件。
og_image_alt: Flow diagram of loading a Word file, generating an OpenAI summary, and
  writing the result to a text file
og_title: 使用 OpenAI 在 C# 中摘要 Word 文档 – 完整分步指南
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: summarize Word document using OpenAI in C#. Learn to load a large document,
    generate a summary, and write the summary file automatically.
  headline: How to summarize Word document with OpenAI in C#
  type: TechArticle
tags:
- C#
- OpenAI
- Word automation
title: 如何在 C# 中使用 OpenAI 摘要 Word 文档
url: /zh/net/ai-powered-document-processing/how-to-summarize-word-document-with-openai-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用 OpenAI 摘要 Word 文档

如果你需要 **快速且准确地摘要 Word 文档**，本指南将展示如何在 C# 中使用 OpenAI 完成此任务。我们将演示如何加载大型文档、使用内置摘要器 **生成 OpenAI 摘要**，以及 **将摘要写入文件**，实现全自动化流程。

完成本教程后，你将拥有一个完整、可直接运行的程序，可嵌入任意 .NET 项目。无需除 OpenAI API 之外的外部服务，代码同时支持 .docx 和 .doc 文件。

## 你将学到

* 如何安全地 **加载大型文档** 对象。  
* 使用单次 API 调用的最佳方式 **生成 OpenAI 摘要**。  
* 如何可靠地 **写入摘要文件** 并处理常见的边缘情况。  
* 在后台任务或 CI 流水线中 **自动化文档摘要** 的技巧。

## 前置条件

* 已安装 .NET 6.0 SDK 或更高版本。  
* 拥有可访问 `gpt‑4o-mini`（或类似）模型的 OpenAI API 密钥。  
* `Aspose.Words` NuGet 包（或任何提供 `Document` 类的库）。  
* 对 C# 控制台应用有基本了解。

> **专业提示：** 将 OpenAI 密钥存放在名为 `OPENAI_API_KEY` 的环境变量中，以避免将凭证写入源码。

## 在 C# 中加载大型文档

第一步是将源 Word 文件读取到内存中。使用 `Aspose.Words` 能确保库能够处理数十兆字节的文档，而无需将整个文件加载为字符串。

```csharp
using System;
using System.IO;
using Aspose.Words;

class DocumentLoader
{
    /// <summary>
    /// Loads a Word document from the specified path.
    /// </summary>
    /// <param name="path">Full file path to the .docx or .doc file.</param>
    /// <returns>A fully parsed Document instance.</returns>
    public static Document Load(string path)
    {
        if (!File.Exists(path))
            throw new FileNotFoundException($"Document not found: {path}");

        // Aspose.Words automatically detects the format.
        return new Document(path);
    }
}
```

*原因说明*：使用可靠的库 **加载大型文档** 可防止内存泄漏，并让你获取原始文本、标题和元数据，供后续摘要器使用。

## 使用 OpenAI 生成摘要

文档已在内存中后，提取其纯文本并发送给 OpenAI 模型。辅助类 `DocumentSummarizer` 抽象了 HTTP 请求和 token 限制的处理。

```csharp
using System;
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

public enum SummarizerModel
{
    OpenAI   // currently maps to gpt‑4o-mini
}

public static class DocumentSummarizer
{
    private static readonly HttpClient _http = new HttpClient();

    /// <summary>
    /// Summarizes the given Word document using the selected model.
    /// </summary>
    /// <param name="doc">The loaded Aspose.Words Document.</param>
    /// <param name="model">Which summarization model to use.</param>
    /// <returns>A concise summary string.</returns>
    public static string Summarize(Document doc, SummarizerModel model)
    {
        // Extract raw text; you could also pass headings only for a more focused summary.
        string fullText = doc.GetText();

        // Build the OpenAI request payload.
        var payload = new
        {
            model = model == SummarizerModel.OpenAI ? "gpt-4o-mini" : "unknown",
            messages = new[]
            {
                new { role = "system", content = "You are a concise summarizer." },
                new { role = "user",   content = $"Summarize the following document in no more than 150 words:\n\n{fullText}" }
            },
            temperature = 0.3
        };

        var request = new HttpRequestMessage(HttpMethod.Post,
            "https://api.openai.com/v1/chat/completions")
        {
            Content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json")
        };

        // Retrieve the API key from the environment.
        string apiKey = Environment.GetEnvironmentVariable("OPENAI_API_KEY")
                        ?? throw new InvalidOperationException("OPENAI_API_KEY not set.");

        request.Headers.Add("Authorization", $"Bearer {apiKey}");

        // Synchronous call for simplicity; replace with async in production.
        HttpResponseMessage response = _http.Send(request);
        response.EnsureSuccessStatusCode();

        using var stream = response.Content.ReadAsStream();
        using var docJson = JsonDocument.Parse(stream);
        string summary = docJson.RootElement
            .GetProperty("choices")[0]
            .GetProperty("message")
            .GetProperty("content")
            .GetString();

        return summary?.Trim() ?? string.Empty;
    }
}
```

**工作原理**：该方法通过一次提示 **生成 OpenAI 摘要**，并遵守模型的 token 限制。`temperature` 设置较低，以保持输出确定性，适合自动化流水线。

## 安全写入摘要文件

获得摘要文本后，将其持久化为 `.txt` 文件。下面的辅助代码会在目标目录不存在时自动创建，并覆盖已有文件。

```csharp
using System;
using System.IO;

public static class SummaryWriter
{
    /// <summary>
    /// Writes the supplied summary to a text file.
    /// </summary>
    /// <param name="summary">The summary string to save.</param>
    /// <param name="outputPath">Full path of the output .txt file.</param>
    public static void Write(string summary, string outputPath)
    {
        if (string.IsNullOrWhiteSpace(summary))
            throw new ArgumentException("Summary cannot be empty.", nameof(summary));

        string directory = Path.GetDirectoryName(outputPath);
        if (!Directory.Exists(directory))
            Directory.CreateDirectory(directory);

        File.WriteAllText(outputPath, summary, Encoding.UTF8);
    }
}
```

*为什么需要这样做*：使用带显式 UTF‑8 编码的 `WriteAllText` 可确保原始 Word 文档中的特殊字符在 **写入摘要文件** 步骤中得到保留。

## 自动化文档摘要工作流

将上述各部分组合即可得到一个简洁的控制台应用，可用于调度、容器化或在 CI 流水线中调用。

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        try
        {
            // 1️⃣ Load the large document you want to summarize
            string docPath = Path.Combine(Environment.CurrentDirectory, "largeReport.docx");
            Document doc = DocumentLoader.Load(docPath);
            Console.WriteLine($"Loaded document: {docPath}");

            // 2️⃣ Generate a summary using the OpenAI model
            string summary = DocumentSummarizer.Summarize(doc, SummarizerModel.OpenAI);
            Console.WriteLine("Summary generated successfully.");

            // 3️⃣ Write the summary to a text file
            string summaryPath = Path.Combine(Environment.CurrentDirectory, "summary.txt");
            SummaryWriter.Write(summary, summaryPath);
            Console.WriteLine($"Summary written to: {summaryPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
            Environment.Exit(1);
        }
    }
}
```

### 预期输出

运行程序（例如 `dotnet run`）后，你应该看到类似如下的输出：



## 接下来你应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助你在项目中进一步掌握 API 功能并探索替代实现方案，每篇资源均提供完整可运行的代码示例和逐步解释。

- [使用 AI 的 C# Word 文档摘要 – 步骤指南](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-step-by-step-guide-using-ai/)
- [使用自定义 GPT 模型在 C# 中摘要 Word 文档 – 完整指南](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-using-a-custom-gpt-model-full-g/)
- [使用 Aspose.Words AI 为 Word 文档添加摘要](/words/english/net/ai-powered-document-processing/add-summary-to-word-document-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}