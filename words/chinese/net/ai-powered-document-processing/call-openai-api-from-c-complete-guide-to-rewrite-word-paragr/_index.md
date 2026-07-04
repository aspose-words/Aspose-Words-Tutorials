---
category: general
date: 2026-05-23
description: 在 C# 中调用 OpenAI API 将句子改写为正式风格。学习如何加载 Word 文档、调用本地 LLM，并使用 Aspose.Words
  将段落改写为正式语言。
draft: false
keywords:
- call openai api
- call local llm
- rewrite sentence formal
- rewrite paragraph formal
- load word document
language: zh
og_description: 在 C# 中调用 OpenAI API 将句子改写为正式风格。完整的逐步教程，包含代码、解释和技巧。
og_title: 从 C# 调用 OpenAI API – 重写 Word 段落
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  headline: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  type: TechArticle
- description: Call OpenAI API in C# to rewrite sentence formal style. Learn how to
    load word document, call local LLM, and rewrite paragraph formal with Aspose.Words.
  name: Call OpenAI API from C# – Complete Guide to Rewrite Word Paragraphs
  steps:
  - name: Why This Works
    text: '- **LocalLargeLanguageModel** abstracts the HTTP details, letting you **call
      local llm** exactly the same way you would a cloud OpenAI endpoint. - The prompt
      we send (`Rewrite the following sentence in formal tone:`) is concise, which
      helps the model focus on a **rewrite sentence formal** transforma'
  - name: Expected Output Example
    text: '| Original (informal) | Rewritten (formal) | |---------------------|--------------------|
      | *Hey team, can we get the results ASAP?* | *Dear team, could you please provide
      the results at your earliest convenience?* |'
  - name: Empty Paragraphs
    text: 'Sometimes a Word file contains empty paragraphs that throw off the LLM.
      Guard against this:'
  - name: Large Documents
    text: 'Processing a 100‑page report paragraph‑by‑paragraph can be slow. Batch
      the calls:'
  type: HowTo
tags:
- Aspose.Words
- C#
- LLM
- OpenAI
- Word Automation
title: 从 C# 调用 OpenAI API – 完整的 Word 段落改写指南
url: /zh/net/ai-powered-document-processing/call-openai-api-from-c-complete-guide-to-rewrite-word-paragr/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 从 C# 调用 OpenAI API – 完整指南：改写 Word 段落

是否曾想过 **call OpenAI API** 从 .NET 应用中直接润色文本？也许你有一个 Word 文件，需要以更正式的语气呈现给客户报告，而不想手动重新输入所有内容。在本教程中，我们将一步步演示：加载 Word 文档，将段落发送到本地托管的 LLM（模拟 OpenAI 兼容 API），并获取 **rewrite paragraph formal** 版本的改写。完成后，你将拥有一个可运行的 C# 控制台应用，只需几行代码即可完成全部工作。

我们会覆盖所有必需内容：所需的 NuGet 包、如何使用 Aspose.Words **load word document**、**call local llm** 的细节，以及为何提示 “Rewrite the following sentence in formal tone” 能可靠地产生 **rewrite sentence formal** 的结果。无需外部文档，只需复制粘贴本指南即可运行。

## 你将实现的目标

- 使用 Aspose.Words 加载 *.docx* 文件。  
- 创建一个能够 **call OpenAI API**‑兼容端点的客户端，即使它们运行在本地。  
- 将段落发送给 LLM 并收到 **rewrite paragraph formal** 响应。  
- 替换 Word 文件中的原始文本并保存更新后的文档。  

前置条件非常少：.NET 6+ SDK、Visual Studio 或 VS Code，以及一个暴露 OpenAI 兼容 HTTP 端点的本地 LLM 实例（如 Ollama、LM Studio）。如果你已有云端密钥，只需切换端点和 API 密钥——代码保持不变。

---

## 第 1 步：设置项目并安装包

首先，创建一个新的控制台项目：

```bash
dotnet new console -n WordLlmRewrite
cd WordLlmRewrite
```

现在添加我们需要的两个 NuGet 包：

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **专业提示：** Aspose.Words.AI 附带一个轻量包装器，能够识别 **call OpenAI API**‑风格的服务，省去手动编写 HTTP 请求的麻烦。

## 第 2 步：编写 **Call OpenAI API**（或本地 LLM）代码

打开 `Program.cs`，将内容替换为以下代码。每行代码下面都有解释，帮助你快速上手。

```csharp
using Aspose.Words;
using Aspose.Words.AI;
using System;

// ------------------------------------------------------------
// 1️⃣ Create a client for the local LLM that follows the
//    OpenAI‑compatible API. This is the heart of the
//    “call openai api” step.
// ------------------------------------------------------------
var localLlm = new LocalLargeLanguageModel(
    endpoint: "http://localhost:8000/v1", // change if your server runs elsewhere
    apiKey: "dummy",                      // dummy because the local server usually skips auth
    model: "my-llm");                     // name of the model you want to use

// ------------------------------------------------------------
// 2️⃣ Load the source Word document.
// ------------------------------------------------------------
Document doc = new Document("YOUR_DIRECTORY/source.docx");

// ------------------------------------------------------------
// 3️⃣ Grab the first paragraph that we want to rewrite.
// ------------------------------------------------------------
Paragraph paragraph = doc.FirstSection.Body.FirstParagraph;

// ------------------------------------------------------------
// 4️⃣ Ask the LLM to rewrite the paragraph in a formal tone.
//    This is where we “rewrite paragraph formal”.
// ------------------------------------------------------------
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in formal tone:\n{paragraph.GetText()}");

// ------------------------------------------------------------
// 5️⃣ Replace the original paragraph text with the revised version.
// ------------------------------------------------------------
paragraph.Runs.Clear();                     // remove old runs
paragraph.AppendChild(new Run(doc, revisedText));

// ------------------------------------------------------------
// 6️⃣ Save the updated document.
// ------------------------------------------------------------
doc.Save("YOUR_DIRECTORY/rewritten.docx");

// ------------------------------------------------------------
// 7️⃣ Confirmation output.
// ------------------------------------------------------------
Console.WriteLine("✅ Document rewritten and saved as rewritten.docx");
```

### 为什么这样可行

- **LocalLargeLanguageModel** 抽象了 HTTP 细节，让你可以 **call local llm** 的方式与调用云端 OpenAI 端点完全相同。  
- 我们发送的提示 (`Rewrite the following sentence in formal tone:`) 简洁明了，帮助模型专注于 **rewrite sentence formal** 转换，而不会添加无关内容。  
- 通过清空 `paragraph.Runs` 并追加新的 `Run`，确保 Word 文件只保留全新的正式文本。

## 第 3 步：运行应用

确保本地 LLM 服务器已启动并监听 `http://localhost:8000/v1`。然后执行：

```bash
dotnet run
```

如果一切配置正确，你将看到：

```
✅ Document rewritten and saved as rewritten.docx
```

打开 `rewritten.docx` —— 第一个段落现在应该以润色后的正式风格呈现。

### 预期输出示例

| 原始（非正式） | 改写后（正式） |
|----------------|----------------|
| *Hey team, can we get the results ASAP?* | *Dear team, could you please provide the results at your earliest convenience?* |

该转换展示了 **rewrite sentence formal** 的干净改写，非常适合商务沟通。

## 第 4 步：为不同语气微调提示

如果需要更随意的改写，只需更改提示：

```csharp
string revisedText = localLlm.GenerateText(
    $"Rewrite the following sentence in a casual tone:\n{paragraph.GetText()}");
```

同理，你可以让模型 **rewrite paragraph formal** 处理更长的章节，甚至对整篇文档进行摘要。相同的 **call openai api** 模式依然适用——只需替换提示，保持客户端代码不变。

## 第 5 步：处理边缘情况

### 空段落

Word 文件中有时会出现空段落，导致 LLM 出错。可以这样防护：

```csharp
if (string.IsNullOrWhiteSpace(paragraph.GetText()))
{
    Console.WriteLine("Skipped empty paragraph.");
}
else
{
    // generate and replace as before
}
```

### 大文档

逐段处理 100 页报告可能较慢。可以批量调用：

```csharp
foreach (Paragraph p in doc.GetChildNodes(NodeType.Paragraph, true))
{
    // same rewrite logic for each paragraph
}
```

注意本地服务器的速率限制；必要时在调用之间加入 `Thread.Sleep(200)`。

## 第 6 步：部署到生产环境

当你从开发机器迁移到 CI/CD 流水线时：

1. 若切换到 Azure OpenAI 或 OpenAI SaaS，需将占位 API 密钥替换为真实密钥。  
2. 将端点和密钥存放在环境变量 (`OPENAI_ENDPOINT`, `OPENAI_KEY`) 中，并通过 `Environment.GetEnvironmentVariable` 读取。  
3. 在 **call openai api** 代码块周围添加日志（如 Serilog），以追踪请求/响应负载。

## 第 7 步：进阶 – 添加简易 UI

如果希望提供 Windows Forms 前端：

```csharp
// inside a button click handler
var filePath = openFileDialog1.FileName;
Document doc = new Document(filePath);
// reuse the same rewriting logic...
```

这样非技术同事即可拖拽文件，获取正式改写，无需触碰代码。

---

## 结论

我们刚刚构建了一个小巧却强大的 C# 实用工具，能够 **call openai api**（或任何兼容的本地 LLM）对 Word 文件中的 **rewrite paragraph formal** 进行改写。通过 **load word document**、发送简洁提示并替换段落文本，你可以在几秒钟内得到润色后的文档。

接下来你可以：

- 扩展工具以处理表格和图片。  
- 与 SharePoint 集成，实现文档自动润色。  
- 尝试其他语气——**rewrite sentence formal**、**rewrite sentence casual**，甚至 **rewrite sentence persuasive**。

动手试一试，调优提示，让 LLM 为你完成繁重的文字工作。祝编码愉快！

## 相关教程

- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)
- [Apply Paragraph Style In Word Document](/words/english/net/document-formatting/apply-paragraph-style/)
- [Move To Paragraph In Word Document](/words/english/net/add-content-using-documentbuilder/move-to-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}