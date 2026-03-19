---
category: general
date: 2026-03-19
description: 学习如何在 Word 中使用本地大语言模型检查语法、注册模型并保存已纠正的文档——全部在一个 C# 教程中完成。
draft: false
keywords:
- how to check grammar
- set up local llm
- check grammar in word
- how to register llm
- how to save corrected
language: zh
og_description: 如何在 Word 中使用本地大语言模型检查语法、注册模型并保存已纠正的文档——一步步指南。
og_title: 如何在 C# 中使用本地 LLM 检查语法
tags:
- Aspose.Words
- AI
- C#
title: 如何在 C# 中使用本地 LLM 检查语法
url: /zh/net/ai-powered-document-processing/how-to-check-grammar-with-a-local-llm-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用本地 LLM 检查语法

有没有想过 **如何检查语法**，在 Word 文档中而不把你的文本发送到云端？你并不孤单。许多开发者希望在拥有自托管模型的隐私的同时，仍能获得 AI 驱动的建议。在本指南中，我们将逐步演示如何注册自定义 LLM、配置 Aspose.Words 使用它，以及最终 **如何保存已纠正** 的文件——全部使用纯 C#。

我们还会介绍 **set up local llm** 的细节，向您展示 **how to register llm** 端点，并演示 **check grammar in word** 文档的具体步骤。完成后，您将拥有一个可直接放入任何 .NET 项目的可运行示例。

## 前置条件

- .NET 6+ SDK（代码可在 .NET Core 和 .NET Framework 上运行）
- Visual Studio 2022 或带有 C# 扩展的 VS Code
- Aspose.Words for .NET（v24.12 或更高）– 可从 NuGet 获取
- 本地运行的 LLM，支持 OpenAI 兼容的 API（例如 Ollama，端口 11434）

> **专业提示：** 如果您使用 Ollama，命令 `ollama serve` 将自动启动端点 `http://localhost:11434/api/generate`。

## 第一步 – How to register llm：将自定义模型添加到 Aspose.Words

我们首先需要告诉 Aspose.Words 我们的 **local llm**。此操作在每次应用启动时只需执行一次。

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Register a custom LLM endpoint – no API key required for local servers
AiEngine.RegisterModel(
    modelName: "local-llm",                         // identifier we’ll reference later
    endpoint: new Uri("http://localhost:11434/api/generate"),
    apiKey: null,                                   // local server doesn’t need a key
    provider: AiProvider.Custom);
```

**为什么重要：** 通过注册模型，您为 Aspose.Words 提供了一个命名句柄（`"local-llm"`）。随后，当我们调用 `CheckGrammar` 时，库能够准确知道要访问哪个端点。如果跳过此步骤，库将回退到内置的云服务，这就违背了使用私有 LLM 的初衷。

## 第二步 – 加载要分析的 Word 文档

现在我们将文件加载到内存中。您可以指向任意 `.docx`、`.doc`，甚至 `.rtf` 文件。

```csharp
// Replace YOUR_DIRECTORY with the actual folder path on your machine
Document sourceDocument = new Document("YOUR_DIRECTORY/input.docx");

// Quick sanity check – print the number of paragraphs we just loaded
Console.WriteLine($"Loaded document with {sourceDocument.GetChildNodes(NodeType.Paragraph, true).Count} paragraphs.");
```

**正在发生的事情：** `Document` 是 Aspose.Words 的核心对象模型。它解析文件并构建节点树（段落、表格、图像等），从而让 AI 引擎能够针对特定文本范围进行语法分析。

## 第三步 – 配置 grammar‑check 选项（set up local llm）

在这里我们将之前注册的模型绑定到语法检查操作上。

```csharp
AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
{
    Model = "local-llm",               // references the name we used in RegisterModel
    // Optional: you can tweak temperature, maxTokens, etc. if your LLM supports them
    // Temperature = 0.7,
    // MaxTokens = 512
};
```

**为什么要公开这些选项：** 不同的 LLM 行为各异。通过公开 `Model`，Aspose.Words 允许您在本地模型和云模型之间切换，而无需更改其他代码。当 **set up local llm** 环境用于合规或离线场景时，这种灵活性至关重要。

## 第四步 – 运行 AI 驱动的语法检查（check grammar in word）

所有配置就绪后，实际的语法检查只需一行代码。

```csharp
// This mutates sourceDocument in place, inserting suggestions and corrections
sourceDocument.CheckGrammar(grammarOptions);
Console.WriteLine("Grammar check completed.");
```

**内部工作原理：** Aspose.Words 提取每个句子，发送到 LLM 端点，接收包含建议编辑的 JSON 负载，然后将这些编辑应用回文档树。此过程为简化起见同步执行；如果您偏好非阻塞 I/O，也可以调用异步重载 `CheckGrammarAsync`。

## 第五步 – 如何保存已纠正的文档

AI 完成处理后，您需要将更改持久化。

```csharp
// Save the corrected file – you can change the format to PDF, HTML, etc.
sourceDocument.Save("YOUR_DIRECTORY/checked.docx");
Console.WriteLine("Corrected document saved as checked.docx");
```

**预期结果：** 在 Word 中打开 `checked.docx`，您会看到语法问题被标记（或根据您的 `AiGrammarCheckOptions` 自动纠正）。如果启用了修订跟踪，还会看到修订标记。

## 完整可运行示例

将所有内容整合在一起，以下是一个可直接运行的控制台应用示例：

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Register the local LLM
        AiEngine.RegisterModel(
            modelName: "local-llm",
            endpoint: new Uri("http://localhost:11434/api/generate"),
            apiKey: null,
            provider: AiProvider.Custom);

        // 2️⃣ Load the source document
        string inputPath = "YOUR_DIRECTORY/input.docx";
        Document sourceDocument = new Document(inputPath);
        Console.WriteLine($"Loaded: {inputPath}");

        // 3️⃣ Set up grammar‑check options (using the local model)
        AiGrammarCheckOptions grammarOptions = new AiGrammarCheckOptions
        {
            Model = "local-llm"
        };

        // 4️⃣ Perform the AI‑driven grammar check
        sourceDocument.CheckGrammar(grammarOptions);
        Console.WriteLine("Grammar analysis finished.");

        // 5️⃣ Save the corrected document
        string outputPath = "YOUR_DIRECTORY/checked.docx";
        sourceDocument.Save(outputPath);
        Console.WriteLine($"Corrected file saved to: {outputPath}");
    }
}
```

**控制台预期输出：**

```
Loaded: YOUR_DIRECTORY/input.docx
Grammar analysis finished.
Corrected file saved to: YOUR_DIRECTORY/checked.docx
```

打开 `checked.docx`，您应该会看到语法改进已自动应用。

## 常见问题与边缘情况

| Question | Answer |
|----------|--------|
| *如果我的 LLM 需要 API 密钥怎么办？* | 在 `RegisterModel` 中将密钥传递给 `apiKey`。相同的代码可同时适用于需要密钥和不需要密钥的服务。 |
| *我可以使用其他文件格式吗？* | 当然可以。`Document.Save` 支持 `.pdf`、`.html`、`.txt` 等格式，只需更改扩展名即可。 |
| *如果 LLM 返回错误怎么办？* | 将 `CheckGrammar` 包裹在 try/catch 中；检查 `AiException` 以获取详细信息。通常是超时——可以考虑增大 `grammarOptions.Timeout`。 |
| *该操作是线程安全的吗？* | 注册步骤是全局的，应该在启动时执行一次。随后对 `CheckGrammar` 的调用只要每个都使用各自的 `Document` 实例，就可以安全并行运行。 |

## 后续步骤

既然您已经了解了使用 **local llm** **如何检查语法**，可以进一步探索：

- **批量处理**：遍历文件夹中的文档并运行相同的流水线。
- **自定义提示**：通过设置 `grammarOptions.PromptTemplate` 调整请求负载，以进行特定风格的检查。
- **与 ASP.NET Core 集成**：公开一个 API 端点，接受上传的 `.docx` 文件，执行语法检查，并返回已纠正的文件。

这些扩展使您能够构建完整的 “grammar‑as‑a‑service” 平台，而无需离开本地环境。

---

*祝编码愉快！如果遇到任何问题，欢迎在下方留言——我很乐意帮助您微调设置。*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}