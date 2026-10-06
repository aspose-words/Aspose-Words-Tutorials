---
category: general
date: 2026-01-13
description: 学习如何使用本地 LLM 接口从 C# 调用 LLM，编辑 Word 文件，删除所有内容，并保存为 docx——一次性教程。
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: zh
og_description: 如何在 C# 中使用本地模型调用 LLM，编辑 Word 文档，删除所有内容，并高效保存 docx。
og_title: 如何在 C# 中调用 LLM – 步骤教程
tags:
- Aspose.Words
- C#
- LLM Integration
title: 如何在 C# 中调用 LLM – 本地模型完整指南
url: /zh/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中调用 LLM – 本地模型完整指南

是否曾想过 **如何在 .NET 应用程序中调用 LLM** 而不将数据发送到云端？你并不孤单。许多开发者希望将提示词和文档保存在本地，尤其是处理敏感文本时。在本教程中，我们将通过一个真实场景演示：使用自托管的 LLM 接口重写 Word 文档、删除所有内容、编辑文件，最终 **如何将 docx 保存** 回磁盘。

我们还会介绍 **使用本地 LLM**，展示从 Aspose.Words `Document` 中 **删除所有内容** 的完整代码，并解释以编程方式编辑 Word 文件的细微差别。完成后，你将拥有一个可直接复制粘贴的解决方案，适用于 Aspose.Words 7+ 以及任何兼容 OpenAI 的本地模型。

## 前置条件 – 开始之前需要准备的内容

- **.NET 6+**（如果你更喜欢经典方式，也可以使用 .NET Framework 4.7.2）
- **Aspose.Words for .NET** NuGet 包（`Aspose.Words` 和 `Aspose.Words.AI`）
- 一个 **本地 LLM**，提供兼容 OpenAI 的 `/v1` 接口（例如运行在 `http://localhost:8000/v1` 的 GPT‑Neo 服务器）
- 一个放在你可控文件夹中的示例 `input.docx`
- Visual Studio、Rider 或任意你喜欢的编辑器 —— 本文截图使用 VS Code

> **专业提示：** 如果你还没有本地模型，可以尝试免费 Docker 镜像的 GPT‑Neo 2.7B —— 启动不到一分钟，并遵循我们这里使用的相同 API 合约。

## 第一步 – 配置本地 LLM 接口（如何调用 LLM）

当你想要 **如何调用 llm** 时，首先需要创建一个指向自托管服务的客户端对象。Aspose.Words.AI 提供了 `LocalLargeLanguageModel` 辅助类，用于封装 HTTP 调用。

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **为什么重要：** 通过自行配置端点，你可以完全控制请求负载、身份验证以及延迟。这是 **如何调用 llm** 而不依赖外部服务的核心。

## 第二步 – 加载源 Word 文档（如何编辑 Word）

接下来，我们将原始的 `.docx` 加载到 Aspose `Document` 中。这是经典的 “**如何编辑 word**” 步骤：文件进入内存后，你可以查询、修改或彻底替换其内容。

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

如果文件不存在，会抛出 `FileNotFoundException`，请确保路径正确。若处理上传流，也可以从 `Stream` 加载。

## 第三步 – 使用本地 LLM 生成修订文本（如何调用 LLM）

现在进入关键环节：让 LLM 以正式语气重写整段文字。提示词通过将简短指令与 `document.GetText()` 提取的原始文本拼接而成。

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **边缘情况：** 如果源文档非常大（超过 10 k token），可能会触及模型的上下文限制。此时请将文本拆分为段落，对每个块分别调用 `GenerateText`。

## 第四步 – 删除所有现有内容（Remove All Content）

在插入新文本之前，需要先清空文档。Aspose 提供的 `RemoveAllChildren()` 会删除章节、段落、表格——所有内容。这是 **从 Word 文件中删除所有内容** 的标准做法。

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **如果只想删除正文而保留页眉怎么办？** 使用 `document.Sections.Clear()`，然后重新构建需要的章节。

## 第五步 – 插入修订后的文本（如何编辑 Word）

清空后，我们可以将 LLM 生成的文本写回文档。`DocumentBuilder` 是一个友好的包装器，允许你添加段落、表格、图片等。这里我们直接将整段字符串作为单个段落写入。

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

如果需要更丰富的格式（粗体、标题），可以解析 LLM 输出中的 markdown 标记，并相应地设置 `builder.Font`。

## 第六步 – 保存更新后的文档（如何保存 Docx）

最后，将更改持久化到新文件中。这展示了 **如何在程序化编辑后保存 docx**。

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

`Save` 方法会自动根据文件扩展名检测格式，因此你也可以只改一行代码导出为 PDF、HTML 或 ODT。

### 预期结果

打开 `output.docx` 时，你应该看到原始内容已全部以精炼、正式的风格重新编写。没有残留的表格、页眉或页脚——只有 LLM 生成的全新文本。

---

![Screenshot of output.docx opened in Word, showing formal rewritten text – how to call llm](/images/output-docx.png "如何调用 llm 示例：重写后的 Word 文档")

*图片替代文字：* **如何调用 llm 示例，展示已重写的 Word 文档**

## 常见问题与故障排除

### 1. “如果我的 LLM 返回错误怎么办？”

`GenerateText` 方法会在非 2xx 响应时抛出 `HttpRequestException`。请使用 `try/catch` 包裹调用并检查 `ex.Message`。常见问题包括缺少 API Key 头或超出模型的 token 限制。

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. “我可以只编辑文档的特定部分，而不是全部清空吗？”

完全可以。使用 `document.GetChildNodes(NodeType.Paragraph, true)` 枚举段落，然后仅在需要的地方替换 `Paragraph.Text` 属性。这种方式让你 **如何编辑 word** 时保持粒度，且不破坏样式。

### 3. “有没有办法保留原始格式？”

如果想保留样式，可先将 LLM 输出作为纯文本，然后根据模板对每个段落使用 `builder.Font.StyleIdentifier`。或者，如果 LLM 能输出 HTML，使用 `DocumentBuilder.InsertHtml()`。

### 4. “如何处理超大文档？”

将文档拆分为章节（`document.Sections`），分别处理。这样既能规避 token 限制，又能降低内存压力。

## 性能优化建议

- **在多次调用之间复用 `LocalLargeLanguageModel` 实例**；底层的 `HttpClient` 会保持连接存活。
- **缓存修订后的文本**，如果同一提示会被重复使用——即使在本地硬件上，LLM 调用也可能成本不菲。
- **并行处理章节**，使用 `Parallel.ForEach`，在多核 CPU 和线程安全的 LLM 客户端下可提升吞吐。

## 后续步骤 – 扩展工作流

既然你已经掌握了 **如何调用 llm**、**使用本地 llm**、**删除所有内容**、**如何编辑 word** 以及 **如何保存 docx**，可以进一步探索：

- **批量处理**：遍历文件夹中的 `.docx`，对每个文件执行相同的重写逻辑。
- **自定义提示**：针对生成摘要、要点列表或翻译等需求调整指令。
- **与 ASP.NET Core 集成**：暴露一个 HTTP 接口，接受文件上传、调用 LLM 并返回编辑后的文档。
- **高级样式**：解析 LLM 输出的 markdown，并使用 `DocumentBuilder` 将其映射为 Word 样式。

这些扩展都基于我们已经讲解的核心模式，几乎无需额外工作即可实现。

---

## 结论

本指南详细阐述了 **如何在 C# 中调用 llm**（使用自托管端点），演示了 **使用本地 llm**，展示了从 Word 文件中 **删除所有内容** 的正确方法，解释了 **如何编辑 word** 的编程技巧，并通过示例说明了 **如何保存 docx**。完整、可运行的示例可直接嵌入任意 .NET 项目，配套的原理说明帮助你理解每一步的 “为什么”，从而自如地进行调优、扩展或调试。

快动手尝试吧，实验不同的提示，让本地 LLM 为你的文档自动化流水线提供强大动力。若遇到任何问题，故障排除章节会为你指明方向。祝编码愉快，尽情享受本地 LLM 的强大威力！

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}