---
title: 使用开放的人工智能模型
linktitle: 使用开放的人工智能模型
second_title: Aspose.Words 文档处理 API
description: 使用 Aspose.Words for .NET 和 OpenAI 的强大模型实现高效的文档摘要。立即深入了解这份全面的指南。
weight: 10
url: /zh/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用开放的人工智能模型

## 介绍

在当今的数字世界中，内容为王。无论您是学生、商务人士还是狂热的作家，高效地处理、总结和生成文档的能力都是无价的。这就是 Aspose.Words for .NET 库发挥作用的地方，它允许您像专业人士一样管理文档。在本综合教程中，我们将深入探讨如何利用 Aspose.Words 结合 OpenAI 模型来有效地总结文档。准备好释放您的文档管理潜力了吗？让我们开始吧！

## 先决条件

在我们卷起袖子深入研究代码之前，你需要做好一些基本准备：

### .NET 框架
确保您运行的 .NET 框架版本与 Aspose.Words 兼容。通常，.NET 5.0 及以上版本应该可以完美运行。

### Aspose.Words for .NET 库
您需要下载并安装 Aspose.Words 库。您可以从[此链接](https://releases.aspose.com/words/net/).

### OpenAI API 密钥
要集成 OpenAI 的语言模型进行文档摘要，您需要一个 API 密钥。您可以在 OpenAI 平台上注册并从您的帐户设置中检索密钥来获取它。

### 开发用 IDE
拥有像 Visual Studio 这样的集成开发环境 (IDE) 是开发 .NET 应用程序的理想选择。

### 基本编程知识
对 C# 和面向对象编程的基础了解将帮助您更轻松地掌握概念。

## 导入包

现在我们已经准备好了一切，让我们导入我们的包。打开您的 Visual Studio 项目并添加必要的库。您可以按照以下步骤操作：

### 添加 Aspose.Words 包

您可以通过 NuGet 包管理器添加 Aspose.Words 包。操作方法如下：
- 转到工具->NuGet 包管理器->管理解决方案的 NuGet 包。
- 搜索“Aspose.Words”然后单击“安装”。

### 添加系统环境

确保包括`System`处理环境变量的命名空间：
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### 添加 Aspose.Words

然后，在您的 C# 文件中包括 Aspose.Words 命名空间：
```csharp
using Aspose.Words;
```

### 添加 OpenAI 库

如果您使用库与 OpenAI 交互（如 REST 客户端），请确保也将其包括在内。您可能需要通过 NuGet 添加它，就像我们添加 Aspose.Words 一样。

现在我们已经准备好环境并导入了必要的包，让我们逐步分解文档摘要过程。

## 步骤 1：定义文档目录

在开始处理文档之前，您需要设置文档和工件所在的目录：

```csharp
//您的文档目录
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
//您的文物目录
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
这使得你的代码更易于管理，因为你可以根据需要轻松更改路径。`MyDir`是存储输入文档的地方，而`ArtifactsDir`是您保存生成的摘要的地方。

## 第 2 步：加载文档

接下来，您将加载要汇总的文档。使用 Aspose.Words 非常简单：

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
确保您的文档名称与您想要使用的名称相匹配，否则您将遇到错误！

## 步骤 3：获取 API 密钥

现在您的文档已加载，是时候提取您的 OpenAI API 密钥了。您将从环境变量中获取它以确保其安全：
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
安全地管理您的 API 密钥对于阻止未经授权的用户至关重要。

## 步骤 4：创建 OpenAI 模型实例

准备好 API 密钥后，您现在可以创建 OpenAI 模型的实例。对于文档摘要，我们将使用 Gpt4OMini 模型：

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
此步骤实质上设置了总结文档所需的智力，使您可以访问人工智能驱动的总结。

## 步骤 5：总结单个文档

让我们首先总结一下第一个文档。这就是奇迹发生的地方：

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
在这里，我们使用`Summarize`模型的方法。`SummaryLength.Short`参数指定我们想要一个简短的摘要——非常适合快速概览！

## 步骤 6：汇总多个文档

雄心勃勃？您可以一次汇总多个文档。看看它有多简单：

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
此功能对于比较多个文件特别有用。也许您正在准备会议，需要从几份冗长的报告中获取简明的笔记。这是您的新好朋友！

## 结论

使用 Aspose.Words for .NET 和 OpenAI 总结文档不仅是一项有益的技能，而且非常强大。通过遵循本指南，您可以将冗长复杂的文本转换为简洁的摘要，从而节省时间和精力。无论您是确保客户的清晰度还是准备重要的演示，您现在都有工具来有效地完成它。

那么，您还在等什么？放心地深入研究您的文档，让技术来做繁重的工作！

## 常见问题解答

### 什么是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一个功能强大的库，使开发人员能够以编程方式创建、操作和转换文档。

### 我需要 OpenAI 的 API 密钥吗？  
是的，您必须拥有有效的 OpenAI API 密钥才能使用其模型访问摘要功能。

### 我可以一次汇总多个文件吗？  
当然可以！您可以在一次通话中汇总多个文档，这对于大量报告来说是理想的选择。

### 如何安装 Aspose.Words？  
您可以通过 Visual Studio 中的 NuGet 包管理器搜索“Aspose.Words”来安装它。

### Aspose.Words 有免费试用版吗？  
是的，您可以通过他们的[网站](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
