---
category: general
date: 2026-04-28
description: 从 C# 连接本地 LLM，并提示大型语言模型加载 Word 文档，调用本地 LLM 自动重写文本。包括逐步代码示例。
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: zh
og_description: 使用 C# 连接本地 LLM，了解如何提示大型语言模型，加载 Word 文档，调用本地 LLM 并在几分钟内自动重写文本。
og_title: 在 C# 中连接本地 LLM – 完整编程指南
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: 在 C# 中连接本地 LLM – 完整编程指南
url: /zh/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中连接本地 LLM – 完整编程指南

是否曾经需要在 .NET 应用中 **connect to local llm**，并想知道如何让它与 Word 文件交互？你并不孤单。在本指南中，我们将完整演示整个过程——connect to local llm、**prompt large language model**、加载 Word 文档、**call local llm**，以及最终 **rewrite text automatically**。完成后，你将拥有一个可运行的示例，能够将任意段落转换为正式语气，且无需任何外部 API 密钥。

## 本教程涵盖内容

我们将首先安装必要的 NuGet 包，然后启动一个简单的本地 LLM 端点（例如运行在 11434 端口的 Ollama）。随后我们会使用 Aspose.Words 加载 `.docx` 文件，将段落发送给 LLM，获取改写后的版本，并写回同一文档。你还将看到如何处理常见的陷阱——空段落、异步释放以及编码问题——确保代码在生产环境而非仅演示中也能正常工作。

### 先决条件

- .NET 6.0 SDK 或更高（如果愿意也可以使用 .NET 8）
- Visual Studio 2022 或带 C# 扩展的 VS Code
- **Aspose.Words for .NET**（免费试用即可）
- 本地托管的 LLM，遵循 `/api/generate` 合约（例如 Ollama、LMStudio）
- 对 C# 中的 async/await 有基本了解

> **专业提示：** 如果尚未安装 Ollama，请运行 `ollama serve` 并使用 `ollama pull llama3` 拉取模型。默认的 HTTP 端点为 `http://localhost:11434/api/generate`。

---

## 步骤 1：安装必需的包

First, add the Aspose.Words and Aspose.Words.AI NuGet packages to your project.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

这些库为我们提供了 **load word document** 功能，以及一个轻量包装器，可 **call local llm** 而无需手动编写 HTTP 请求。

---

## 步骤 2：连接本地 LLM 端点

Connecting to a locally hosted model is as simple as instantiating `LocalLargeLanguageModel`. The constructor expects the full URL of the generation endpoint.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

为什么要把端点包装成一个类？`LocalLargeLanguageModel` 为你处理 JSON 序列化、重试以及流式响应——这样你可以专注于提示逻辑，而无需摆弄 `HttpClient`。

---

## 步骤 3：加载源 Word 文档

Next, we bring the document into memory. Aspose.Words supports virtually every Word format, so `Document` will parse `input.docx` without needing Office installed.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

如果需要使用流（例如通过 ASP.NET 上传的文件），只需将文件路径替换为 `MemoryStream` 并传入 `Document` 构造函数即可。

---

## 步骤 4：提取当前段落文本

We’ll use `DocumentBuilder` to navigate the document. In this example we rewrite **the first paragraph**, but you can iterate over `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` to process many.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

`?.` 运算符可以防止在文档为空时抛出 `NullReferenceException`。这就是会让初学者踩坑的 **edge cases** 之一。

---

## 步骤 5：提示 LLM 改写段落

Now we actually **prompt large language model**. The prompt is plain English; the wrapper will send it as JSON to the local endpoint.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

为什么要这样表述请求？LLM 对清晰、单一任务的指令响应最佳。在冒号后添加换行可以将指令与内容分离，降低模型回显提示的可能性。

**预期输出** – 如果 `originalParagraph` 为 `"Hey, what's up?"`，LLM 可能返回：

> “Good day, how may I assist you?”

你可以通过打印来验证结果：

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## 步骤 6：将改写后的文本写回文档

With the new text in hand, we replace the old paragraph. `DocumentBuilder.Writeln` writes a new line and moves the cursor forward, which is perfect for appending. If you need to *replace* the exact same paragraph, you can use `docBuilder.CurrentParagraph.RemoveAllChildren()` before writing.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

这里展示了两种方法，你可以根据工作流选择合适的方式。

---

## 步骤 7：保存更新后的文档

Finally, we persist the changes to a new file. Aspose.Words automatically chooses the format based on the file extension.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

在 Word 中打开 `output.docx`，你会看到段落已以正式语气呈现。

---

## 完整工作示例

Below is the **complete, self‑contained program**. Copy‑paste it into a console project, restore NuGet packages, and run it—no extra configuration required beyond a running local LLM.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### 运行时的预期结果

1. 控制台会打印原始段落和改写后的段落。  
2. `output.docx` 会出现在 `input.docx` 旁边。  
3. 打开文件后会看到新的正式段落插入在原始段落之后（如果使用了替代代码，则会替换原段落）。

---

## 处理常见的边缘情况

| 情况 | 解决方案 |
|-----------|----------|
| **仅为空或仅包含空白的段落** | 在提示前检查 `string.IsNullOrWhiteSpace`（见步骤 3）。 |
| **LLM 返回错误或空字符串** | 将 `PromptAsync` 包裹在 `try/catch` 中，并回退使用原始文本。 |
| **需要改写多个段落** | 遍历 `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` 并应用相同的提示逻辑。 |
| **大型文档导致延迟** | 将段落批量处理，在一次请求中发送（每次提示最多约 4 KB）。 |
| **非 ASCII 字符出现乱码** | 确保 LLM 端点使用 UTF‑8（大多数现代模型都是如此）。 |

---

## 后续步骤与相关主题

- 使用更丰富的指令对 **Prompt large language model**（例如风格指南、长度限制）。  
- 在 Web API 中使用 **call local llm**，将文档自动化作为服务暴露。  
- 探索在并行流中 **load word document** 以实现高吞吐场景。  
- 将此方法与 **rewrite text automatically** 结合，用于批量邮件生成或报告标准化。  

如果想深入了解，请查阅 Aspose 关于 **document merging** 的文档以及 Ollama API 参考以获取自定义采样参数。

---

## 结论

我们刚刚演示了如何在 C# 中 **connect to local llm**、**prompt large language model**、**load word document**、**call local llm**，以及 **rewrite text automatically**——全部在一个可运行的控制台应用中完成。该模式具有可扩展性：可以更换提示、遍历段落，或通过 ASP.NET 端点公开逻辑。关键点在于，本地 AI 模型可以与传统文档处理库紧密结合，为你提供强大的自动化能力，而无需离开可信的本地环境。  

如有关于线程的问题，

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}