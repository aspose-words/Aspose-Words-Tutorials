---
category: general
date: 2026-10-16
description: 创建空白文档并添加 ActiveX 控件，同时使用 AI 在 C# 中对文本进行摘要和翻译。将 Word 文档保存为一个完整的示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add activex control
- summarize document with ai
- translate text to spanish
- save word document
language: zh
lastmod: 2026-10-16
og_description: 创建空白文档并添加 ActiveX 控件，然后使用 AI 对文本进行摘要和翻译。将最终的 Word 文档在一次工作流中保存。
og_image_alt: Screenshot of a create blank document with an ActiveX CommandButton
  inserted
og_title: 创建空白文档，在 C# 中添加带 AI 摘要的 ActiveX 控件
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create blank document and add ActiveX control while using AI to summarize
    and translate text in C#. Save the Word document with one complete example.
  headline: Create blank document, add ActiveX control with AI summary
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI
- ActiveX
title: 创建空白文档，添加带 AI 摘要的 ActiveX 控件
url: /zh/net/working-with-oleobjects-and-activex/create-blank-document-add-activex-control-with-ai-summary/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 创建空白文档，添加带 AI 摘要的 ActiveX 控件

如果您需要 **创建空白文档** 并嵌入交互式元素，本指南将向您展示如何 **添加 ActiveX 控件**、运行 **AI 摘要器**、**将文本翻译为西班牙语**，以及最终 **保存 Word 文档**。您将看到一个完整、可运行的 C# 程序，使用 Aspose.Words、Aspose.Words.AI 以及所需的云密钥。

本教程涵盖从项目设置到结果验证的每一步。无需查阅外部文档——复制代码，替换占位符密钥，然后运行。完成后，您将了解每个 API 调用的意义、如何处理常见陷阱，以及如何将解决方案扩展到其他语言或控件。

## 您需要的环境

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.7+）
- 有效的 Aspose.Words 许可证（可选，用于完整功能）
- 用于摘要的 OpenAI API 密钥
- 用于翻译的 Google Cloud Translation API 密钥
- Visual Studio 2022 或您喜欢的任何 C# IDE

## 创建空白文档并初始化 Aspose.Words

第一步是 **创建空白文档**。Aspose.Words 提供了 `Document` 类，用于表示一个可以进行操作的空 Word 文件。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;
using Aspose.Words.Fields;
using Aspose.Words.AI;
using Aspose.Words.AI.Summarizer;
using Aspose.Words.AI.Translator;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```


## 接下来您可以学习什么？

以下教程涵盖与本指南技术紧密相关的主题，构建在本教程展示的技巧之上。每个资源都包含完整的可运行代码示例以及逐步解释，帮助您掌握更多 API 功能，并在自己的项目中探索替代实现方案。

- [Summarize Word Document in C# with Aspose.Words API – Complete AI‑Powered Guide](/words/english/net/ai-powered-document-processing/summarize-word-document-in-c-complete-ai-powered-guide/)
- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}