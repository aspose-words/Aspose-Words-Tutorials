---
category: general
date: 2026-06-17
description: 使用 Aspose.Words 的 AI 重写段落，并学习如何配置本地 LLM，以在您的 .NET 应用中实现无缝集成。
draft: false
keywords:
- rewrite paragraph with ai
- how to configure local llm
- Aspose.Words AI integration
- local LLM endpoint setup
- C# document automation
language: zh
og_description: 使用 C# 的 AI 重写段落，并了解如何配置本地 LLM 端点以实现可靠的本地部署处理。
og_title: 使用 AI 重写段落 – 本地 LLM 配置快速指南
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Rewrite paragraph with AI using Aspose.Words and learn how to configure
    local LLM for seamless integration in your .NET app.
  headline: Rewrite Paragraph with AI in C# – How to Configure Local LLM
  type: TechArticle
- description: Rewrite paragraph with AI using Aspose.Words and learn how to configure
    local LLM for seamless integration in your .NET app.
  name: Rewrite Paragraph with AI in C# – How to Configure Local LLM
  steps:
  - name: Aspose.Words extracts the raw text of the target paragraph.
    text: Aspose.Words extracts the raw text of the target paragraph.
  - name: It builds a request payload that includes the user‑provided `prompt`.
    text: It builds a request payload that includes the user‑provided `prompt`.
  - name: The payload is sent to the local LLM via the `BaseUrl`.
    text: The payload is sent to the local LLM via the `BaseUrl`.
  - name: The model returns the revised text, which Aspose.Words returns as a `string`.
    text: The model returns the revised text, which Aspose.Words returns as a `string`.
  type: HowTo
- questions:
  - answer: Yes. Loop over the desired indices and call `RewriteParagraph` for each.
      Remember to respect rate limits of your LLM—local servers are usually generous,
      but large batches can still overload the CPU.
    question: Can I rewrite multiple paragraphs in one go?
  - answer: For very large files (> 500 MB) consider using `LoadOptions` with `LoadFormat`
      set to `Auto` and enable `LoadOptions.LoadFormat` = `LoadFormat.Docx`. The AI
      call still works on a per‑paragraph basis, keeping memory usage modest.
    question: Does Aspose.Words support streaming large documents?
  - answer: 'Try simplifying the instruction or adding examples. For instance, `"Rewrite
      the following sentence in a formal tone: {text}"` can give the model a clearer
      context. ## Next Steps & Related Topics - **Fine‑tune your local model** for
      domain‑specific rewriting (e.g., legal contracts). - **Combine multi'
    question: What if my local LLM doesn’t understand the prompt?
  type: FAQPage
tags:
- Aspose.Words
- C#
- AI
- LLM
title: 使用 C# AI 重写段落 – 如何配置本地 LLM
url: /zh/net/ai-powered-document-processing/rewrite-paragraph-with-ai-in-c-how-to-configure-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# AI 重写段落 – 完整指南

是否曾想过在不将数据发送到云端的情况下 **使用 AI 重写段落**？你并不孤单。许多开发者渴望在本地大型语言模型（LLM）上拥有完全控制，同时仍能享受 Aspose.Words AI 助手的便利。

在本教程中，我们将通过一个动手示例演示如何重写 .docx 文件中的特定段落，并展示 **如何配置本地 LLM** 端点（如 Ollama 或 LM Studio）。完成后，你将拥有一个独立的 C# 控制台应用程序，它与本地托管的模型通信，重写文本并打印结果——全部在本机上完成。

## 前置条件

- .NET 6+ SDK（如果需要，也可以针对 .NET Framework 4.8）
- Aspose.Words for .NET（NuGet 包 `Aspose.Words` ≥ 23.12）
- 一个提供 OpenAI 兼容 API 的本地 LLM 服务器（Ollama、LM Studio 或类似）
- 基础的 C# 知识——只需能够运行控制台应用程序

> **专业提示：** 如果尚未安装本地 LLM，先使用 `ollama serve` 启动 Ollama 并拉取模型（`ollama pull llama2`）。服务器默认监听 `http://localhost:11434/v1`，这正好匹配下面的代码。

## 步骤 1：加载源文档  

首先我们需要一个 Word 文档作为操作对象。Aspose.Words 只需一行代码即可完成。

```csharp
using Aspose.Words;

// Load the DOCX file from the file system
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*为什么重要：* `Document` 对象在内存中表示整个文件，提供对任意段落、表格或图片的随机访问。提前加载文件可确保 AI 引擎在后续需要重写多个段落时能够引用上下文。

## 步骤 2：设置本地 LLM 配置  

下面展示 **如何配置本地 llm** 以供 Aspose.Words AI 使用。库期望一个 `AiModelConfig` 对象，其结构与 OpenAI API 合约相匹配。

```csharp
using Aspose.Words.AI;

var aiConfig = new AiModelConfig
{
    BaseUrl = "http://localhost:11434/v1", // Ollama or LM Studio endpoint
    ModelName = "my-llm",                  // The model identifier you pulled
    // Optional settings you might tweak:
    // ApiKey = "YOUR_API_KEY",           // Not needed for local servers
    // Temperature = 0.7,                // Controls randomness
    // MaxTokens = 512                   // Limits response length
};
```

**说明：**  
- `BaseUrl` 指向你的 LLM 所监听的 HTTP 地址。  
- `ModelName` 告诉服务器使用哪个模型。  
- 可选字段允许在不修改服务器默认设置的情况下微调生成行为。

如果使用 **LM Studio**，默认 URL 为 `http://localhost:1234/v1`。只需替换为该地址——代码其余部分无需更改。

## 步骤 3：重写指定段落  

现在进入有趣的部分——让模型重写第 2 段（零基索引），并使用自定义提示。

```csharp
// Ask the AI to rewrite paragraph #2 with a formal, concise tone
string rewrittenParagraph = document.AI.RewriteParagraph(
    paragraphIndex: 2,
    config: aiConfig,
    prompt: "Make the tone more formal and concise."
);

// Output the result to the console
Console.WriteLine(rewrittenParagraph);
```

**底层发生了什么？**  
1. Aspose.Words 提取目标段落的原始文本。  
2. 构建包含用户提供的 `prompt` 的请求负载。  
3. 通过 `BaseUrl` 将负载发送到本地 LLM。  
4. 模型返回修改后的文本，Aspose.Words 将其作为 `string` 返回。

### 边缘情况与技巧

- **索引无效：** 若 `paragraphIndex` 超出文档段落数，会抛出 `ArgumentOutOfRangeException`。可使用 `if (paragraphIndex < document.GetChildNodes(NodeType.Paragraph, true).Count)` 进行检查。  
- **提示为空：** 空的 `prompt` 会回退到模型的默认行为，可能仅仅是回显输入。请始终提供明确指令。  
- **网络问题：** 由于调用的是本地 HTTP 端点，`BaseUrl` 拼写错误会导致 `WebException`。请将调用包装在 `try/catch` 中，并记录 URL 以便快速调试。

## 步骤 4：持久化更改（可选）  

如果希望将重写后的段落替换文档中的原始文本，可直接更新段落节点。

```csharp
// Retrieve the paragraph node
Paragraph target = (Paragraph)document.GetChildNodes(NodeType.Paragraph, true)[2];

// Replace its text with the AI‑generated version
target.Range.Text = rewrittenParagraph;

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");
```

此时磁盘上的文件已包含正式、简洁的版本，便于后续处理或分发。

## 完整工作示例

下面是一段可直接复制粘贴的控制台程序，完整实现上述功能，并包含错误处理和注释，便于阅读。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;

namespace RewriteParagraphDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source DOCX
            string inputPath = "YOUR_DIRECTORY/input.docx";
            Document document;
            try
            {
                document = new Document(inputPath);
                Console.WriteLine($"Loaded document: {inputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // 2️⃣ Configure the local LLM (adjust URL/model as needed)
            var aiConfig = new AiModelConfig
            {
                BaseUrl = "http://localhost:11434/v1", // Ollama default
                ModelName = "my-llm",
                Temperature = 0.6
            };

            // 3️⃣ Choose which paragraph to rewrite (zero‑based)
            int paragraphIndex = 2;
            var paragraphs = document.GetChildNodes(NodeType.Paragraph, true);
            if (paragraphIndex < 0 || paragraphIndex >= paragraphs.Count)
            {
                Console.WriteLine("Paragraph index out of range.");
                return;
            }

            // 4️⃣ Ask the AI to rewrite it
            string prompt = "Make the tone more formal and concise.";
            string rewrittenParagraph;
            try
            {
                rewrittenParagraph = document.AI.RewriteParagraph(
                    paragraphIndex: paragraphIndex,
                    config: aiConfig,
                    prompt: prompt);
                Console.WriteLine("\n--- Rewritten Paragraph ---");
                Console.WriteLine(rewrittenParagraph);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"AI request failed: {ex.Message}");
                return;
            }

            // 5️⃣ (Optional) Replace the original paragraph and save
            Paragraph target = (Paragraph)paragraphs[paragraphIndex];
            target.Range.Text = rewrittenParagraph;
            string outputPath = "YOUR_DIRECTORY/output.docx";
            document.Save(outputPath);
            Console.WriteLine($"\nDocument saved with changes: {outputPath}");
        }
    }
}
```

**预期输出**（假设原段落为 “We need to finish the report soon.”）：

```
--- Rewritten Paragraph ---
The report should be completed promptly.
```

保存后的 `output.docx` 现在已将该句子替换为更精炼的版本。

## 常见问题

**问：能一次性重写多个段落吗？**  
答：可以。遍历所需的索引并对每个索引调用 `RewriteParagraph`。请注意遵守本地 LLM 的速率限制——本地服务器通常较宽松，但大批量请求仍可能导致 CPU 过载。

**问：Aspose.Words 支持流式处理大型文档吗？**  
答：对于非常大的文件（> 500 MB），建议使用 `LoadOptions`，将 `LoadFormat` 设置为 `Auto`，并启用 `LoadOptions.LoadFormat = LoadFormat.Docx`。AI 调用仍然是按段落进行，保持内存占用在可接受范围。

**问：如果本地 LLM 不理解我的提示怎么办？**  
答：尝试简化指令或添加示例。例如，`"Rewrite the following sentence in a formal tone: {text}"` 能为模型提供更清晰的上下文。

## 后续步骤与相关主题

- **微调本地模型** 以实现领域特定的重写（如法律合同）。  
- **组合多种 AI 功能**，如 Aspose.Words AI 的 `SummarizeDocument` 或 `GenerateCoverPage`。  
- **为端点加固安全**，在将 LLM 暴露到 localhost 之外时使用 API Key 或 TLS。  
- 探索使用 `Parallel.ForEach` 进行 **批量处理**，加速大规模文档转换。

---

就这些！现在你已经掌握了使用 Aspose.Words 以及 **如何配置本地 llm**，在本地环境中 **使用 AI 重写段落** 的完整流程。动手尝试，调整提示，让你的文档瞬间焕然一新。

如果遇到任何问题，欢迎在下方留言或查阅 Aspose.Words 文档获取更深入的 API 细节。祝编码愉快！


## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助你在项目中进一步扩展 API 功能并探索替代实现方式。每篇资源均提供完整可运行的代码示例和逐步解释。

- [在 Aspose.Words for .NET 中为段落应用边框和底纹](/words/english/net/document-styling/apply-border-and-shading/)
- [使用 Aspose.Words 为表格添加标题和描述](/words/english/net/working-with-table-styles-and-formatting/table-tittle-and-description/)
- [在 Aspose.Words for Java 中使用 DocumentBuilder 创建表单字段并添加内容](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}