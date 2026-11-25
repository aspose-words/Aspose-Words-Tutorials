---
category: general
date: 2026-11-25
description: 学习如何创建 Word 文档、添加矩形形状、使用 AI 对文档进行摘要、使用 AI 翻译文本，并使用 Aspose.Words 将文档保存为
  DOCX。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: zh
lastmod: 2026-11-25
og_description: 创建 Word 文档，添加矩形形状，使用 AI 对文档进行摘要，使用 AI 翻译文本，并将文档保存为 DOCX——全部在一个 C#
  教程中完成。
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: 使用 C# 创建包含形状、AI 摘要和翻译的 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: 如何使用 C# 创建包含形状、AI 摘要和翻译的 Word 文档
url: /zh/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中创建带有形状、AI 摘要和翻译的 Word 文档

如果您需要以编程方式 **创建 Word 文档**，本指南将一步步演示。使用 Aspose.Words for .NET，您将学习如何 **添加矩形形状**、调用 AI 服务 **使用 AI 摘要文档**、使用 **使用 AI 翻译文本** 翻译段落，最后 **将文档保存为 DOCX**。

许多开发者在将文档自动化与现代 AI 功能结合时会遇到困难。完成本教程后，您将拥有一个完整的、独立的 C# 项目，能够生成格式完整的 *.docx* 文件，包含可视化形状、AI 生成的摘要以及多语言内容。

## 前置条件

在开始之前，请确保您具备以下条件：

- .NET 6.0 SDK 或更高版本已安装  
- Visual Studio 2022（或任何 C# IDE）  
- Aspose.Words for .NET 许可证（或免费评估密钥）  
- 用于 AI 摘要和翻译调用的互联网访问  

无需除 `Aspose.Words` 和 `Aspose.Words.AI` 之外的其他 NuGet 包。

## 第 1 步：设置项目并添加所需的包

创建一个新的控制台项目并引入 Aspose.Words 库。

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **专业提示：** 如果您计划使用评估模式，请在 `Main` 方法开头调用 `Aspose.Words.License.SetLicense("Aspose.Words.lic");` 以避免水印。

## 第 2 步：初始化文档 – **创建 Word 文档** 的核心

第一行可执行代码会创建一个全新的 **Word 文档** 对象。该对象是后续所有操作的画布。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`DocumentBuilder` 简化了插入文本、形状和控件的过程，无需手动处理低层节点树。

## 第 3 步：向文档 **添加矩形形状**

矩形形状可用作可视占位符、标签背景或简单图形。我们首先创建一个 `GroupShape`，然后在其中插入一个 `Rectangle`。

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

该矩形宽 100 点，高 50 点。由于它位于 `GroupShape` 中，您以后可以添加更多元素（例如文本框），而无需担心布局冲突。

## 第 4 步：插入纯文本 StructuredDocumentTag (SDT)

StructuredDocumentTag 对象对于以后可以绑定到数据源的内容控件非常有用。

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

`true` 标志将该标签标记为 **可重复** 控件，适用于模板场景。

## 第 5 步：添加 ActiveX CommandButton 控件（可选 UI）

如果生成的文档将在支持 ActiveX 的环境中使用，您可以嵌入一个按钮。

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

此步骤为可选项；如果目标受众从不在 Windows 环境中与文档交互，可将其移除。

## 第 6 步：**使用 AI 摘要文档**

Aspose.Words.AI 为大型语言模型服务提供了便利的封装。这里我们使用 OpenAI 后端调用 `DocumentSummarizer.Summarize`。

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

该方法分析当前节点树，提取最相关的句子，并返回一个简洁的段落。这就是 **使用 AI 摘要文档** 功能的核心。

## 第 7 步：**使用 AI 翻译文本**

接下来演示如何将示例字符串从英文翻译为法文。`Translator.Translate` 方法内部调用了 Google AI 模型。

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

您可以将 `Language.French` 替换为任何受支持的语言枚举值，从而实现即时的多语言文档生成。

## 第 8 步：**将文档保存为 DOCX**

最后，将编辑后的文档持久化到磁盘。当您指定 `.docx` 扩展名时，`Save` 方法会自动写入 *.docx* 文件。

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

文件 `Result.docx` 现在包含：

- 位于组形状中的矩形形状  
- 纯文本内容控件 (SDT)  
- ActiveX CommandButton（如果保留了第 5 步）  
- AI 生成的摘要段落  
- “Hello world”的法语翻译  

您可以在 Microsoft Word 中打开该文件，以验证每个元素。

## 完整源代码

以下是完整的、可直接运行的程序。将其复制到 `Program.cs` 并执行 `dotnet run`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### 预期输出

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

打开 `Result.docx` 时，您会看到顶部的矩形形状、SDT 占位符、按钮、摘要段落以及作为纯文本插入的法语翻译。

## 结论

现在，您已经掌握了如何 **从头创建 Word 文档**、**添加矩形形状**、**使用 AI 摘要文档**、**使用 AI 翻译文本**，以及 **将文档保存为 DOCX**——只需几行简洁的 C# 代码。此模式具备可扩展性：您可以将硬编码字符串替换为动态数据，添加更多形状或图表，并通过调整 `SummarizerOptions` 或 `Translator` 参数来切换 AI 提供商。

### 接下来可以做什么？

- 探索 **添加矩形形状** 的各种变体：更改填充颜色、线条样式，或在形状内部添加文本。  
- 在更大的文档上使用 **使用 AI 摘要文档**，自动生成执行摘要。  
- 将 **使用 AI 翻译文本** 扩展为批量处理整段或表格，实现多语言报告。  
- 结合 Aspose.Words 图表 API，在 AI 生成的洞察旁嵌入数据可视化。  

欢迎实验并在评论或 GitHub 上分享您的成果。祝编码愉快！


## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并探索在项目中的替代实现方式。

- [创建空白 Word 文档并添加矩形形状](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [在 Word 文档中使用 Aspose.Words for .NET 创建组形状](/words/english/net/working-with-shapes/add-group-shape/)
- [使用 Aspose.Words for .NET 在 Word 文档中添加文本水印](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}