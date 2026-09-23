---
category: general
date: 2026-02-21
description: 如何在 C# 中通过加载 DOCX、将其文本发送到本地 LLM 并写回纠正后的版本来检查语法。包括如何使用 LLM 和读取 Word 文档文本。
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: zh
og_description: 如何在 C# 中加载 DOCX，将其文本发送到本地 LLM 检查语法，并将纠正后的版本写回。学习如何使用 LLM 读取 Word 文档文本。
og_title: 如何使用本地大语言模型在 C# 中检查语法
tags:
- C#
- LLM
- Aspose.Words
title: 如何在 C# 中使用本地 LLM 检查语法
url: /zh/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中使用本地 LLM 检查语法

是否曾经想过 **如何检查语法** 在 Word 文档中而不离开你的 C# 项目？你并不是唯一的——开发者们经常问，‘我能用驱动聊天机器人的同样代码来自动校对吗？’ 简短的答案是可以。通过加载 DOCX，提取其文本，并将其发送到本地托管的大型语言模型（LLM），你可以获得即时的语法修正，并将润色后的结果直接写回文件。

在本教程中，我们将完整演示整个过程：使用 **load docx in c#** 读取 `.docx`，调用 **how to use llm** 进行语法纠正，最后保存清理后的文档。完成后，你将拥有一个可直接运行的控制台应用程序，完全满足你的需求——无需手动复制粘贴，无需外部 API，仅使用纯 C# 和本地 LLM 接口。

> **你需要的条件**
> - .NET 6.0 或更高（代码在 .NET Framework 上也能运行，但 .NET 6 是最佳选择）
> - [Aspose.Words for .NET](https://products.aspose.com/words/net/) 库（免费试用可用于测试）
> - 一个运行中的 LLM 服务器，提供简单的 `CheckGrammar(string)` 接口（例如 Ollama、LM Studio，或自定义的 FastAPI 包装器）
> - 对 async/await 有基本了解（可选但推荐）

如果你在想 **为什么这很重要**，请想想你在生成报告时手动修正拼写错误所花的时间。自动化此步骤不仅能加快流水线速度，还能保证数十份文档的一致性。让我们开始吧。

## 检查语法 – 概览

在动手之前，这里有一个快速路线图：

1. **创建一个客户端**，与本地 LLM 端点通信。  
2. 使用 Aspose.Words **读取 Word 文档**——这是在 C# 中 **read word document text** 的经典方式。  
3. **将原始文本** 发送给 LLM 并接收修正后的版本。  
4. **用修正后的文本** 替换文档中的原始内容。  
5. **保存** 更新后的文件（可选，但通常需要）。

每一步都封装在各自的方法中，便于后续复用或替换。完整源码位于文章末尾。

## 步骤 1：设置 LLM 客户端（How to Use LLM）

为了保持整洁，我们将在一个小型包装类中封装 HTTP 调用。该类假设 LLM 服务接受包含 JSON 负载 `{ "prompt": "..."}` 的 POST 请求，并返回 `{ "response": "..." }`。如果你的服务不同，请相应调整序列化方式。

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**为什么这很重要：**  
- **解耦** —— 如果以后从 Ollama 切换到 LM Studio，只需更改 URL 或负载格式。  
- **异步友好** —— 网络 I/O 不会阻塞你的 UI 或后台工作者。  
- **错误处理** —— `EnsureSuccessStatusCode` 在 LLM 不可用时抛出明确异常，我们稍后会捕获它。

> **专业提示：** 如果你的 LLM 在 GPU 上运行，请将请求大小保持在约 4 KB 以下，以避免延迟峰值。

## 步骤 2：加载 DOCX 并提取文本（Read Word Document Text）

Aspose.Words 让读取 Word 文件变得轻而易举。`Document.GetText()` 方法返回全部可见文本，并保留换行。如果需要更丰富的格式（表格、脚注），则必须遍历节点树，但对于纯语法检查来说，纯文本已足够。

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**边缘情况说明：**  
如果文档包含非英文字符或特殊符号，请确保所使用的 LLM 模型支持 Unicode。大多数现代模型都支持，但旧模型可能会截断或误解这些字符。

## 步骤 3：用修正后的文本替换内容

Aspose.Words 没有“一行代码替换整个正文”的方法，但清空节点树并插入单个段落效果很好。这也能确保任何隐藏的标记（如修订痕迹）被去除。

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**为什么要移除所有子节点：**  
- 确保全新起点，防止残留的格式干扰新内容。  
- 简化代码——无需寻找特定节点进行替换。

如果你想保留原始标题，可以解析原始节点树，仅替换 `Run` 节点，但这会增加复杂度，超出本教程范围。

## 步骤 4：将所有部分连接起来 — 完整工作示例

下面是完整的控制台程序。它演示了从头到尾的 **how to check grammar**，包括基本的错误处理和可选的命令行参数。

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### 预期输出

运行程序（`dotnet run`）时，控制台会显示类似如下内容：

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

在 Word 中打开 `output.docx`——你会看到相同的内容，但标点、主谓一致以及任何明显的拼写错误都已由 LLM 修正。

## 常见问题与边缘情况

### 如果 LLM 返回 `null` 或空字符串怎么办？

`CheckGrammarAsync` 方法在响应负载缺少 `response` 字段时会回退到原始输入。这可以防止意外清空文档。

### 文档多大时请求会超时？

大多数本地 LLM 服务器能够轻松处理几千字符。对于更大的文件（例如 100 KB 以上），可以将文本按段落分块，分别发送每个块，然后重新组装修正后的片段。约 2 KB 的块大小是一个不错的起点。

### 这会保留图像、表格或脚注吗？

不会。通过清除所有子节点会丢失所有非文本元素。如果需要保留这些内容，你必须遍历节点树，仅替换 `Run` 节点（文本片段），其余节点保持不变。这是更高级的场景——欢迎探索 Aspose.Words 的 `NodeCollection` 操作 API。

### 我可以使用云端 LLM 而不是本地的吗？

完全可以。只需在 `LocalLargeLanguageModel` 中更换端点 URL 和负载格式。请注意，云服务通常有速率限制和费用，而本地模型在初始 GPU/CPU 配置后即可离线免费使用。

## 专业提示与最佳实践

- **缓存客户端**：复用同一个 `HttpClient` 实例可以避免

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}