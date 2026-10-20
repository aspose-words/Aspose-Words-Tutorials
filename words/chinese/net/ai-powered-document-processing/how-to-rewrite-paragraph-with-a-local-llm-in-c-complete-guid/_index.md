---
category: general
date: 2026-07-03
description: 如何使用本地大语言模型改写段落、替换文本、生成文本并保存文档——全部使用 C#。请按照本分步教程操作。
draft: false
keywords:
- how to rewrite paragraph
- use local llm
- how to replace text
- how to generate text
- how to save document
language: zh
og_description: 如何使用本地大语言模型改写段落、替换文本、生成文本并在 C# 中保存文档。一步一步学习完整流程。
og_title: 如何在 C# 中使用本地 LLM 重写段落
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: How to rewrite paragraph using a local LLM, replace text, generate
    text and save document—all in C#. Follow this step‑by‑step tutorial.
  headline: How to Rewrite Paragraph with a Local LLM in C# – Complete Guide
  type: TechArticle
- questions:
  - answer: Absolutely. Loop through `document.GetChildNodes(NodeType.Paragraph, true)`
      and apply the same prompt to each paragraph you need to modify.
    question: Can I rewrite multiple paragraphs at once?
  - answer: That usually means the prompt was ambiguous or the model hit a token limit.
      Try simplifying the prompt or increasing the `max_tokens` setting in the endpoint
      configuration.
    question: What if the LLM returns an empty string?
  - answer: Not directly. You’d first need to convert the PDF to a Word document (Aspose.PDF
      → Aspose.Words) or extract the text, rewrite it, then re‑create the PDF.
    question: Does this approach work with PDFs?
  - answer: 'Just change the instruction in the prompt, e.g., `"Rewrite the following
      in a friendly tone:"`. The LLM follows the natural‑language cue you give it.
      ## Next Steps & Related Topics - **How to replace text** in tables, headers,
      or footers (use `NodeType.Table` and similar loops). - **How to generate '
    question: How do I control the tone beyond “formal”?
  type: FAQPage
tags:
- Aspose.Words
- C#
- LLM
title: 如何在 C# 中使用本地 LLM 改写段落 – 完整指南
url: /zh/net/ai-powered-document-processing/how-to-rewrite-paragraph-with-a-local-llm-in-c-complete-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用本地 LLM 重写段落 – 完整指南

是否曾经想过在不将数据发送到云端的情况下自动 **重写段落**？你并不孤单。许多开发者需要一种快速的方式来改写文本，同时保持所有数据在本地，好消息是，你可以使用本地 LLM 和 Aspose.Words 来实现。

在本指南中，我们将连接本地 LLM，加载 .docx 文件，要求模型 **生成文本**，替换原始内容，最后 **保存文档** 回磁盘。完成后，你将拥有一个可复用的代码片段，能够直接嵌入任何 .NET 项目中。

> **专业提示：** 如果你已经在使用 Aspose.Words 处理其他文档任务，那么本示例可以直接使用——除了 LLM 客户端外无需额外的库。

## 前置条件

- 已安装 .NET 6+（或 .NET Framework 4.7.2+）。
- Aspose.Words for .NET ≥ 23.11（AI 扩展已包含在包中）。
- 可访问的本地兼容 OpenAI 的端点（例如 Ollama、LM Studio 或自托管的 vLLM），地址为 `http://localhost:8000/v1/chat/completions`。
- 本地服务的 API 密钥（通常是类似 `"my-local-key"` 的占位字符串）。

> **为什么这些重要：** 使用 **本地 LLM** 的方式可以消除网络延迟并保护敏感文本，而 Aspose.Words 为我们提供了强大的 Word 文档操作能力。

## 第一步：设置 LargeLanguageModel 实例  

首先我们创建一个指向本地端点的 `LargeLanguageModel` 对象。该对象封装了 HTTP 调用，使得后续代码看起来像普通的 C# 方法调用。

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Create a LargeLanguageModel instance for a local LLM.
var llm = new LargeLanguageModel(
    endpoint: "http://localhost:8000/v1/chat/completions",
    apiKey: "my-local-key");   // Replace with your actual key if needed.
```

*为什么？* 只建立一次连接可以让后续的 **生成文本** 调用更快，并避免每次都重新创建 HTTP 客户端。

## 第二步：加载源文档  

接下来我们将 Word 文件加载到内存中。Aspose.Words 会读取整个文档，使我们能够访问段落、表格等内容。

```csharp
// Load the .docx file you want to process.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

如果文件未找到，Aspose 会抛出明确的 `FileNotFoundException`，你可以捕获它并提供友好的错误提示。

## 第三步：获取要重写的段落  

演示中我们使用第一段，但你可以通过索引、样式或文本搜索定位任意段落。

```csharp
// Retrieve the first paragraph – this is the target for rewriting.
Paragraph originalParagraph = document.FirstParagraph;
```

*提示：* 为了后续在特定段落中 **替换文本**，请像示例中那样保留对 `Paragraph` 对象的引用。

## 第四步：请求 LLM 重写段落  

现在是有趣的部分：我们将原始文本发送给 LLM，并要求它以正式语气重写。`GenerateText` 方法会返回模型的响应，形式为普通字符串。

```csharp
// Build the prompt – you can tweak the tone or style as needed.
string prompt = $"Rewrite the following for a formal tone:\n{originalParagraph.GetText()}";

// Generate the revised text using the local LLM.
string revisedText = llm.GenerateText(prompt);
```

*为什么有效：* LLM 能看到完整的段落和明确的指令，因此输出会遵循所请求的风格。由于我们调用的是 **本地 LLM** 端点，请求永远不会离开你的机器。

## 第五步：替换原始段落文本  

拿到新内容后，我们替换旧文本。Aspose.Words 提供了强大的 `FindReplaceOptions` 类，可对操作进行细粒度调节，但默认设置已足以完成简单的替换。

```csharp
// Perform the replacement – this updates the document in memory.
originalParagraph.Range.Replace(
    originalParagraph.GetText(),
    revisedText,
    new FindReplaceOptions());
```

*边缘情况：* 如果原始段落包含隐藏字符（如换行），`GetText()` 会将其包含在内，从而确保精确匹配。如果发现不匹配，可在替换前考虑去除空白字符。

## 第六步：保存更新后的文档  

最后，我们将修改后的文档写回磁盘。你可以覆盖原文件或写入新位置——下面都给出示例。

```csharp
// Overwrite the original file (use with caution).
document.Save("YOUR_DIRECTORY/input.docx");

// Or save to a new file to keep the original intact.
document.Save("YOUR_DIRECTORY/rewritten.docx");
```

这就是完整的 **保存文档** 流程。`Save` 方法会自动根据文件扩展名检测格式，因此只需一行代码即可导出为 PDF、HTML 或 ODT。

## 完整工作示例  

将所有代码组合在一起即可得到一个独立的程序，你可以在命令行运行或嵌入更大的服务中。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize the local LLM client.
        var llm = new LargeLanguageModel(
            endpoint: "http://localhost:8000/v1/chat/completions",
            apiKey: "my-local-key");

        // 2️⃣ Load the document you want to edit.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 3️⃣ Pick the paragraph to rewrite (first paragraph in this case).
        Paragraph para = doc.FirstParagraph;

        // 4️⃣ Ask the LLM to rewrite it in a formal tone.
        string prompt = $"Rewrite the following for a formal tone:\n{para.GetText()}";
        string newText = llm.GenerateText(prompt);

        // 5️⃣ Replace the old text with the new, formal version.
        para.Range.Replace(para.GetText(), newText, new FindReplaceOptions());

        // 6️⃣ Save the updated document.
        doc.Save("YOUR_DIRECTORY/rewritten.docx");

        Console.WriteLine("Paragraph rewritten and document saved successfully.");
    }
}
```

### 预期输出

运行程序后，控制台会输出：

```
Paragraph rewritten and document saved successfully.
```

文件 `rewritten.docx` 现在包含与原始文件相同的内容，只是第一段已被以正式语气重写——正是我们所要求的。

## 常见问题 (FAQs)

**问：我可以一次重写多个段落吗？**  
**答：** 当然可以。遍历 `document.GetChildNodes(NodeType.Paragraph, true)`，对每个需要修改的段落使用相同的提示即可。

**问：如果 LLM 返回空字符串怎么办？**  
**答：** 通常表示提示不够明确或模型达到了 token 限制。尝试简化提示或在端点配置中增大 `max_tokens` 参数。

**问：这种方法能用于 PDF 吗？**  
**答：** 不能直接使用。需要先将 PDF 转换为 Word 文档（Aspose.PDF → Aspose.Words）或提取文本，进行重写后再重新生成 PDF。

**问：如何控制除“正式”之外的语气？**  
**答：** 只需在提示中更改指令，例如 `"Rewrite the following in a friendly tone:"`。LLM 会遵循你提供的自然语言指示。

## 后续步骤与相关主题

- **如何在表格、页眉或页脚中替换文本**（使用 `NodeType.Table` 等循环）。
- **如何使用更丰富的提示生成文本**，包括项目符号或 markdown。
- **如何有条件地重写段落**，根据长度或关键词密度（在调用 LLM 前添加预检查）。
- 探索 **本地 LLM** 的性能调优：调整 temperature、top‑p 或 max‑tokens，以获得更确定的输出。
- 学习 **如何将文档保存为其他格式**，如 PDF (`doc.Save("out.pdf")`) 或 HTML (`doc.Save("out.html")`)。

---

### 总结

现在你已经掌握了使用本地 LLM **重写段落**、**替换文本**、**生成文本**以及 **保存文档** 的方法——全部在一个简洁、可用于生产的 C# 代码片段中。欢迎尝试不同的提示、批量处理多个文件，或将此逻辑集成到 Web API 中，实现即时文档编辑。

如果遇到任何问题，欢迎在下方留言——祝编码愉快！

## 接下来该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助你掌握更多 API 功能并在项目中探索替代实现方案。

- [Word 文档 - 查找并替换文本](/words/english/net/find-and-replace-text/)
- [将文档保存为 TXT – 完整 C# 指南，将 DOCX 转换为纯文本](/words/english/net/programming-with-txtsaveoptions/save-document-as-txt-complete-c-guide-to-convert-docx-to-pla/)
- [使用 Aspose.Words for .NET 在 Word 文档中添加文字水印](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}