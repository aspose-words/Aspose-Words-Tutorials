---
category: general
date: 2026-05-04
description: 如何使用 LLM 与 Aspose 编辑文档——学习替换段落文本、连接本地 LLM，并使用 AI 重写文本。
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: zh
og_description: 如何使用 LLM 与 Aspose 编辑文档。本指南展示了如何连接本地 LLM、替换段落文本以及使用 AI 重写文本。
og_title: 如何使用 LLM 与 Aspose.Words – 在 C# 中重写段落
tags:
- Aspose.Words
- C#
- AI
- LLM
title: 如何在 Aspose.Words 中使用 LLM – 用 C# 重写段落
url: /zh/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Aspose.Words 中使用 LLM – 用 C# 重写段落

有没有想过 **如何使用 LLM** 在不手动打开的情况下润色 Word 文档？你并不是唯一有此困惑的人。许多开发者在需要以编程方式 *替换段落文本* 时会遇到瓶颈，因为缺乏干净的 AI 驱动工作流。

在本教程中，我们将连接本地大型语言模型，向其提供来自 `.docx` 文件的片段，要求它 **使用 AI 重写文本**，最后保存更新后的文档——全部使用 Aspose.Words。完成后，你将拥有一个可直接运行的 C# 控制台应用程序，演示完整的流程。

> **你将获得：** 完整可运行的示例、每一步的解释、针对边缘情况的技巧以及扩展方案的思路。

## 你需要的环境

- **.NET 6+**（或 .NET Framework 4.7.2 —— 代码在两者上均可运行）
- **Aspose.Words for .NET**（NuGet 包 `Aspose.Words`）
- 一个 **本地 LLM 服务器**，提供简单的 HTTP `/generate` 接口（例如 Ollama、LMStudio，或自定义 Flask 服务）
- 对 C# 和 HTTP 客户端代码有基本了解  

无需额外的 SDK；其余全部在我们即将编写的代码中。

## 步骤 1：如何使用 LLM 替换段落文本

我们首先需要做的事是确定要修改的段落。Aspose.Words 通过提供丰富的对象模型，使这一步变得轻而易举。

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**为什么这很重要：**  
选择正确的节点可以防止意外覆盖标题或表格。通过使用 **replace paragraph text** 方法，我们在保持文档结构完整的同时，仅修改我们关心的内容。

> **专业提示：** 如果文档中有可变长度的章节，可使用 `document.GetChildNodes(NodeType.Paragraph, true)` 并结合 LINQ 根据文本或样式定位段落。

## 步骤 2：连接本地 LLM 接口

现在我们已经拿到文本，需要将其发送给 LLM。示例使用了一个简易的包装类 `LocalLargeLanguageModel` 来隐藏 HTTP 细节。如果你愿意，也可以直接使用 `HttpClient` 调用来替代它。

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**为什么这样连接：**  
**connect to local llm** 的设置可以消除延迟，保持数据本地化，并避免 API 成本。包装类还能让后续代码更简洁，使我们能够专注于 **rewrite text using ai** 逻辑。

## 步骤 3：使用 Aspose.Words 通过 AI 重写文本

手握段落文本且 LLM 已就绪后，我们构造一个提示词，明确告诉模型我们的需求——以正式语气重写。你可以根据需要调整提示词，以实现其他风格（友好、技术等）。

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**为什么有效：**  
LLM 依赖提示词驱动；提供明确指令（“Rewrite … in a formal tone”）可获得一致的结果。**rewrite text using ai** 步骤是本教程的核心——它展示了如何将 AI 直接嵌入文档工作流。

## 步骤 4：编辑文档并保存更改

现在我们用新内容替换原始的 run。Aspose.Words 将文本存储在 `Run` 对象中，先清空它们可以避免残留的格式化痕迹。

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**边缘情况说明：**  
如果原始段落包含混合格式（粗体、斜体），你可能需要保留样式。此时，可创建新的 `Run`，复制原始 `Font` 设置，然后将其 `Text` 设置为 `revisedText`。

## 完整工作示例

下面是完整的程序代码，可直接复制粘贴到控制台项目中。请先安装 Aspose.Words NuGet 包（`dotnet add package Aspose.Words`）。

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### 预期输出

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

打开 `output.docx` —— 你会看到第三段已变为润色后的版本。

## 常见问题与注意事项

| 问题 | 回答 |
|----------|--------|
| **如果我的 LLM 返回带有额外字段的 JSON？** | 调整 `GenerateText` 以反序列化正确的属性，或手动解析响应。 |
| **我能一次处理多个段落吗？** | 可以——遍历 `document.FirstSection.Body.Paragraphs` 并应用相同的提示逻辑，必要时在提示中加入段落索引以提供上下文。 |
| **我的 LLM 服务器需要身份验证？** | 在 POST 前向 `HttpClient` 添加头部：`_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`。 |
| **替换后格式丢失。** | 保留原始 `Run.Font` 设置：创建新的 `Run`，复制 `originalRun.Font.Clone()`，然后设置其 `Text`。 |
| **LLM 有时返回空字符串。** | 实现回退机制——如果 `revisedText.Trim().Length == 0`，保留原始文本或使用更简单的提示重新尝试。 |

## 扩展方案

既然你已经掌握了 **how to use llm** 对单段落的使用，接下来可以考虑以下步骤：

- **批量处理：** 遍历每个段落并以选定的风格重写（例如 “使所有文本简洁”）。  
- **样式感知重写：** 在提示中传入原始段落的样式名称，使 LLM 能区分标题和正文。  
- **与 CI 流水线集成：** 将文档润色自动化，作为文档构建过程的一部分。  
- **替代提示词：** 尝试 “summarize this paragraph” 或 “translate this paragraph to Spanish”，以探索 **rewrite text using ai** 的全部潜能。

## 结论

我们已经完整演示了在 Aspose.Words 中使用 **how to use llm** 的整个流程：加载文档、**connect to local llm**、提取段落、**rewrite text using ai**、**replace paragraph text**，最后保存结果。代码自包含、开箱即用，展示了将 AI 与传统文档自动化相结合的实用方法。

试一试，调整提示词，然后让

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}