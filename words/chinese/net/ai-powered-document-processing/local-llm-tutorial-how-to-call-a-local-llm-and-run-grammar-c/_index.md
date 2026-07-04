---
category: general
date: 2026-06-24
description: 本地 LLM 教程，演示如何调用本地 LLM、加载 Word 文档并在 C# 中使用 AI 语法检查。
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: zh
og_description: 本地 LLM 教程逐步解释如何调用本地 LLM、加载 Word 文档并在 C# 中运行 AI 语法检查。
og_title: 本地 LLM 教程 – 调用本地 LLM 并进行语法检查
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: 本地 LLM 教程 – 如何调用本地 LLM 并进行语法检查
url: /zh/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 本地 LLM 教程 – 调用本地 LLM 并进行语法检查

有没有想过在不把文件发送到云端的情况下 **对 Word 文件进行语法检查**？在本 **本地 llm 教程** 中，我们将连接一个自托管的大语言模型，加载 `.docx` 文件，让 AI 整理文稿。无需 API 密钥，也不产生外部流量——全部在你的机器上完成繁重工作。

我们会逐行讲解代码，说明每一部分为何重要，并展示如何处理常见的陷阱（如文件缺失或端点不可达）。完成后，你将拥有一个可直接运行的 C# 控制台应用，使用本地托管的模型执行 **ai 语法检查**。

> **你将获得：** 完整可运行的程序、每一步的清晰解释，以及将解决方案扩展到更大文档或不同 LLM 提供商的技巧。

![本地 llm 教程示意图](https://example.com/local-llm-tutorial-diagram.png "示意图：本地 llm 教程的工作流程")

## 前置条件

在开始之前，请确保你已经具备：

- .NET 6.0 SDK 或更高版本（可从 Microsoft 官网下载）
- 本地运行的 LLM 服务器，提供兼容 OpenAI 的端点（例如 Ollama、LM Studio，或自定义的 FastAPI 包装器）
- `AiGrammar` NuGet 包（或提供 `LocalLargeLanguageModel`、`Document`、`AiModelType` 类的任意库）
- 一个示例 Word 文档（`input.docx`），放置在稍后会引用的文件夹中

就这些——无需额外的云凭证。

## 第一步：本地 LLM 教程 – 设置端点

我们首先需要一个 **call local llm** 对象，告诉它请求应发送到哪里。把它想象成你拨打电话前需要的电话号码。

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**为什么重要：**  
大多数 LLM SDK 都期望一个遵循 OpenAI API 合约的 HTTP 端点。将 `Endpoint` 指向 `http://localhost:8000/v1`，就告诉库 **call local llm** 而不是去 OpenAI 的服务器。虚拟的 API key 只是占位符——有些客户端不接受 null 值，所以我们提供一个无害的字符串。

> **小贴士：** 如果你在反向代理后面运行 LLM，请将 `Endpoint` 设置为代理的 URL，让代理处理 TLS 终止。这样可以保持控制台应用简洁且安全。

## 第二步：加载 Word 文档进行语法检查

模型可达后，需要 **load word document** 内容到内存。`Document` 类为我们抽象了 `.docx` 的解析。

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**为什么重要：**  
直接把二进制 `.docx` 文件喂给 LLM 会让它困惑。`Document` 辅助类提取纯文本并保留段落换行，为 **ai grammar check** 提供干净的输入。存在性检查可以避免出现 `FileNotFoundException`，防止程序崩溃。

## 第三步：使用 LLM 运行语法检查

下面是教程的核心：让本地模型校对文本。`CheckGrammar` 方法封装了 HTTP 细节，并返回结果对象。

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**为什么重要：**  
`AiModelType.Gpt4` 只是一个标签，告诉远程服务使用哪套提示模板。如果你使用更小的模型（例如 `Llama2`），请相应替换。库会序列化文档文本，发送到 `http://localhost:8000/v1/completions`，并解析纠正后的输出。

> **边缘情况：** 如果 LLM 超时，`CheckGrammar` 会抛出 `TimeoutException`。如果预期文档很大或服务器繁忙，请在调用处使用 `try/catch` 包裹。

## 第四步：输出纠正后的文本

最后，我们将展示清理后的版本。在真实应用中，你可能会把它写回新的 `.docx` 文件，但本教程只需在控制台打印即可。

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**预期输出**（假设原文件中有几处刻意错误）：

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

如果 LLM 没发现任何错误，输出将与输入完全相同，这本身也是一种有价值的信号。

## 完整可运行示例

将所有代码组合在一起，下面是可以直接复制到新控制台项目中的完整程序：

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### 如何运行

1. 在项目文件夹打开终端。  
2. 运行 `dotnet run`。  
3. 观察控制台打印出的纠正文本。

这就是 **local llm tutorial** 的全部内容，代码不足 100 行。

## 常见问题解答 (FAQ)

### 可以使用其他品牌的 LLM 吗？

完全可以。只要服务器遵循 OpenAI v1 API 规范，修改 `Endpoint` 并选择对应的 `AiModelType` 枚举值（例如 `AiModelType.Llama2`），其余代码保持不变。

### 如果我的文档非常大（10 MB 以上）怎么办？

大体积会超出许多服务器的默认请求大小限制。可以将文档拆分为多个章节，分别调用 `CheckGrammar`，再把结果拼接。这也能降低超时的概率。

### 如何把纠正后的内容写回 `.docx` 文件？

`Document` 类通常提供 `Save(string path, string content)` 方法。获取 `result.CorrectedText` 后，调用：

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

具体签名请参考库的文档。

### 虚拟 API key 会带来安全风险吗？

不会。自托管端点会忽略该密钥，但某些 SDK 要求非空字符串。使用 `"dummy"` 之类的占位符即可满足要求，而不会泄露任何机密。

## 后续步骤与相关主题

- **微调本地 LLM** 以适应特定领域的语法（如法律或医学写作）。  
- **批处理作业**：一次处理整个文件夹的 Word 文档，适用于出版流水线。  
- 探索 **流式响应**，在用户输入时实时提供建议。  
- 将其与 **拼写检查库** 结合，实现双层质量把关。

上述思路都基于本 **local llm tutorial** 中的核心概念——**call local llm**、**load word document**、**run grammar check**、**handle results**——在不同场景中反复出现。

---

*祝编码愉快！如果遇到问题，欢迎在下方留言，我们一起排查。*


## 接下来该学习什么？

以下教程与本指南紧密相关，进一步扩展了本教程中展示的技术。每篇资源都提供完整可运行的代码示例，并配有逐步解释，帮助你掌握更多 API 功能并在项目中探索替代实现方式。

- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Load Encrypted In Word Document](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}