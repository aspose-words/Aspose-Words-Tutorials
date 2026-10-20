---
category: general
date: 2026-03-30
description: 使用本地 LLM 为您的 Word 文件创建 AI 摘要。学习如何对 Word 文档进行摘要，搭建本地 LLM 服务器，并在几分钟内生成文档摘要。
draft: false
keywords:
- create summary with ai
- summarize word document
- use local llm
- generate document summary
- setup local llm server
language: zh
og_description: 使用 AI 为 Word 文件创建摘要。本指南展示如何使用本地大语言模型对 Word 文档进行摘要，并轻松生成文档摘要。
og_title: 使用 AI 创建摘要 – 完整 C# 指南
tags:
- Aspose.Words
- C#
- AI
- Document Automation
title: 使用 AI 创建摘要 – C# Aspose Words 教程
url: /zh/net/ai-powered-document-processing/create-summary-with-ai-c-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 AI 创建摘要 – C# Aspose Words 教程

是否曾想过在不将机密文件发送到云端的情况下 **使用 AI 创建摘要**？你并不孤单。在许多企业中，数据隐私规则使得依赖外部服务变得风险很大，因此开发者转而使用在自己机器上运行的 **本地 LLM**。

在本教程中，我们将演示一个完整且可运行的示例，使用 Aspose.Words AI 和自托管的语言模型 **对 Word 文档进行摘要**。完成后，你将了解如何 **设置本地 LLM 服务器**、配置连接，并 **生成文档摘要**，可以在任意位置显示或存储。

## 所需条件

- **Aspose.Words for .NET** (v24.10 或更高) – 提供 `Document` 类和 AI 辅助功能的库。  
- 一个 **本地 LLM 服务器**，提供兼容 OpenAI 的 `/v1/chat/completions` 接口（例如 Ollama、LM Studio 或 vLLM）。  
- .NET 6+ SDK 以及你喜欢的任何 IDE（Visual Studio、Rider、VS Code）。  
- 一个你想要摘要的简单 `.docx` 文件 – 将其放在名为 `YOUR_DIRECTORY` 的文件夹中。

> **技巧提示：** 如果你只是进行测试，免费 “tiny‑llama” 模型对短文档表现良好，且延迟保持在一秒以内。

## 第 1 步：加载要摘要的 Word 文档

我们首先需要将源文件加载为 `Aspose.Words.Document` 对象。此步骤至关重要，因为 AI 引擎期望的是 `Document` 实例，而不是原始文件路径。

```csharp
using Aspose.Words;

// Load the source .docx file
Document doc = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of pages
Console.WriteLine($"Document loaded: {doc.PageCount} pages");
```

*为什么重要：* 预先加载文档可以验证文件是否存在且可读。它还让你能够获取元数据（作者、字数），这些信息可能在后续提示中使用。

## 第 2 步：配置本地 LLM 服务器的连接

接下来我们告诉 Aspose Words 将提示发送到哪里。`LlmConfiguration` 对象保存端点 URL 和可选的 API 密钥。对于大多数自托管服务器，密钥可以是虚拟值。

```csharp
using Aspose.Words.AI;

// Define connection settings for the local LLM
var llmConfig = new LlmConfiguration
{
    Endpoint = "http://localhost:8000/v1/chat/completions",
    ApiKey = "dummy" // not required for self‑hosted servers
};

// Verify the connection (optional but handy)
try
{
    var test = llmConfig.TestConnectionAsync().Result;
    Console.WriteLine("LLM server reachable ✅");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to reach LLM: {ex.Message}");
    // Exit early – no point continuing without a working server
    return;
}
```

*为什么重要：* 预先测试端点可以避免后续摘要请求失败时出现难以理解的错误。它还演示了 **如何安全地使用本地 LLM**。

## 第 3 步：使用 Document AI 生成摘要

现在是有趣的部分——我们让 AI 阅读文档并生成简洁的摘要。Aspose.Words.AI 提供了一行代码的 `DocumentAi.Summarize`，它会处理提示构建、令牌限制以及结果解析。

```csharp
// Ask the AI to summarize the document
string summary = DocumentAi.Summarize(doc, llmConfig);

// Show the raw JSON response for debugging (optional)
Console.WriteLine("=== AI Raw Response ===");
Console.WriteLine(summary);
```

*为什么重要：* `Summarize` 方法抽象掉了构建聊天完成请求的样板代码，让你专注于业务逻辑。它还会遵守模型的令牌限制，必要时会截断文档。

## 第 4 步：显示或持久化生成的摘要

最后，我们将摘要输出到控制台。在实际应用中，你可能会将其写入数据库、通过电子邮件发送，或嵌入回原始 Word 文件中。

```csharp
// Print the clean summary to the console
Console.WriteLine("\n--- Document Summary ---");
Console.WriteLine(summary);

// Optional: Save the summary to a text file
File.WriteAllText("YOUR_DIRECTORY/summary.txt", summary);
Console.WriteLine("\nSummary saved to summary.txt");
```

*为什么重要：* 存储结果意味着你可以在以后进行审计，或将其输入后续工作流（例如用于搜索的索引）。

## 完整工作示例

下面是完整的程序代码，你可以直接放入控制台项目并立即运行。确保已安装 NuGet 包 `Aspose.Words` 和 `Aspose.Words.AI`。

```csharp
// ----------------------------------------------------------
// Complete C# console app – Create summary with AI
// ----------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.AI;

namespace DocumentSummaryDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            var docPath = "YOUR_DIRECTORY/input.docx";
            if (!File.Exists(docPath))
            {
                Console.WriteLine($"File not found: {docPath}");
                return;
            }

            Document doc = new Document(docPath);
            Console.WriteLine($"Loaded document ({doc.PageCount} pages).");

            // 2️⃣ Set up local LLM configuration
            var llmConfig = new LlmConfiguration
            {
                Endpoint = "http://localhost:8000/v1/chat/completions",
                ApiKey = "dummy"
            };

            // Quick connectivity test
            try
            {
                llmConfig.TestConnectionAsync().Wait();
                Console.WriteLine("✅ Connected to local LLM.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"❌ Unable to reach LLM: {ex.Message}");
                return;
            }

            // 3️⃣ Generate the summary
            Console.WriteLine("\nGenerating summary…");
            string summary = DocumentAi.Summarize(doc, llmConfig);

            // 4️⃣ Show and save the result
            Console.WriteLine("\n--- Document Summary ---");
            Console.WriteLine(summary);

            var outPath = "YOUR_DIRECTORY/summary.txt";
            File.WriteAllText(outPath, summary);
            Console.WriteLine($"\n✅ Summary written to {outPath}");
        }
    }
}
```

### 预期输出

```
Loaded document (3 pages).
✅ Connected to local LLM.

Generating summary…

--- Document Summary ---
This report outlines the quarterly sales performance, highlighting a 12% increase in revenue driven by the new product line. Key challenges include supply‑chain delays, which are mitigated by renegotiated contracts. Recommendations focus on expanding into emerging markets and investing in automation.

✅ Summary written to YOUR_DIRECTORY/summary.txt
```

具体的措辞会根据你的文档内容和所使用的模型而有所不同，但结构（短段落、要点式列举）是典型的。

## 常见陷阱及避免方法

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| **模型超出上下文长度** | 大型 Word 文件超出 LLM 的令牌窗口。 | 使用接受 `maxTokens` 参数的 `DocumentAi.Summarize` 重载，或手动将文档拆分为多个章节并分别摘要。 |
| **CORS 或 SSL 错误** | 你的本地 LLM 服务器可能使用自签名证书绑定在 `https` 上。 | 在开发时禁用 SSL 验证（`HttpClientHandler.ServerCertificateCustomValidationCallback = HttpClientHandler.DangerousAcceptAnyServerCertificateValidator`）。 |
| **摘要为空** | 提示过于模糊或模型未被指示进行摘要。 | 通过 `DocumentAi.Summarize(doc, llmConfig, new SummarizeOptions { Prompt = "Give a 3‑sentence executive summary." })` 提供自定义提示。 |
| **性能下降** | LLM 仅在 CPU 上运行。 | 切换到支持 GPU 的实例，或使用更小的模型进行快速原型。 |

## 边缘情况与变体

- **PDF 摘要** – 首先将 PDF 转换为 `Document`（`Document pdfDoc = new Document("file.pdf");`），然后执行相同的步骤。  
- **多语言文档** – 在 `SummarizeOptions` 中传入 `CultureInfo`，以指导特定语言的分词。  
- **批量处理** – 遍历包含 `.docx` 文件的文件夹，复用同一个 `llmConfig` 以避免重新连接的开销。  

## 后续步骤

现在你已经掌握了使用 **本地 LLM** **对 Word 文档进行摘要** 的方法，你可能想要：

1. **集成 Web API** – 暴露一个接受文件上传并返回摘要 JSON 的端点。  
2. **将摘要存入搜索索引** – 使用 Azure Cognitive Search 或 Elasticsearch，使文档可通过 AI 生成的摘要进行搜索。  
3. **尝试其他 AI 功能** – Aspose.Words.AI 还提供 `Translate`、`ExtractKeyPhrases` 和 `ClassifyDocument`。  

上述每项都基于相同的基础：**使用本地 LLM** 和 **生成文档摘要**。

*祝编码愉快！如果在 **设置本地 LLM 服务器** 或运行示例时遇到任何问题，请在下方留言——我会帮助你排查。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}