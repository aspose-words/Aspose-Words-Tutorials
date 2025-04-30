---
"description": "使用 Aspose.Words for .NET 和 OpenAI 强大的模型，解锁高效的文档摘要功能。立即深入了解这份全面的指南。"
"linktitle": "使用开放的人工智能模型"
"second_title": "Aspose.Words文档处理API"
"title": "使用开放的人工智能模型"
"url": "/zh/net/ai-powered-document-processing/working-with-open-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用开放的人工智能模型

## 介绍

在当今的数字世界，内容为王。无论您是学生、商务人士还是写作爱好者，高效地处理、汇总和生成文档的能力都至关重要。Aspose.Words for .NET 库正是为此而生，它能让您像专业人士一样管理文档。在本教程中，我们将深入探讨如何结合使用 Aspose.Words 和 OpenAI 模型来有效地汇总文档。准备好释放您的文档管理潜力了吗？让我们开始吧！

## 先决条件

在我们卷起袖子并深入研究代码之前，您需要准备好一些必需品：

### .NET 框架
确保您运行的 .NET Framework 版本与 Aspose.Words 兼容。通常，.NET 5.0 及以上版本应该可以完美运行。

### Aspose.Words for .NET 库
您需要下载并安装 Aspose.Words 库。您可以从 [此链接](https://releases。aspose.com/words/net/).

### OpenAI API 密钥
要集成 OpenAI 的语言模型进行文档摘要，您需要一个 API 密钥。您可以在 OpenAI 平台上注册，然后在您的账户设置中获取密钥。

### 开发IDE
拥有像 Visual Studio 这样的集成开发环境 (IDE) 对于开发 .NET 应用程序来说是理想的。

### 基本编程知识
对 C# 和面向对象编程的基本了解将帮助您更轻松地掌握概念。

## 导入包

现在我们已经准备好了所有东西，让我们导入我们的包。打开你的 Visual Studio 项目并添加必要的库。操作方法如下：

### 添加 Aspose.Words 包

您可以通过 NuGet 包管理器添加 Aspose.Words 包。操作方法如下：
- 转到工具->NuGet 包管理器->管理解决方案的 NuGet 包。
- 搜索“Aspose.Words”并单击安装。

### 添加系统环境

确保包含 `System` 命名空间来处理环境变量：
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### 添加 Aspose.Words

然后，在 C# 文件中包含 Aspose.Words 命名空间：
```csharp
using Aspose.Words;
```

### 添加 OpenAI 库

如果您使用库与 OpenAI 交互（例如 REST 客户端），请确保也将其包含在内。您可能需要通过 NuGet 添加它，就像我们添加 Aspose.Words 一样。

现在我们已经准备好环境并导入了必要的包，让我们逐步分解文档摘要过程。

## 步骤 1：定义文档目录

在开始处理文档之前，您需要设置文档和工件所在的目录：

```csharp
// 您的文档目录
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// 您的 Artifacts 目录
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
这使得您的代码更易于管理，因为您可以根据需要轻松更改路径。 `MyDir` 是存储输入文档的地方，而 `ArtifactsDir` 是您保存生成的摘要的地方。

## 第 2 步：加载文档

接下来，您将加载要汇总的文档。使用 Aspose.Words 非常简单：

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
确保您的文档名称与您想要使用的名称相匹配，否则您将遇到错误！

## 步骤 3：获取您的 API 密钥

现在你的文档已加载，是时候提取你的 OpenAI API 密钥了。你需要从环境变量中获取它以确保其安全：
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
安全地管理您的 API 密钥对于阻止未经授权的用户至关重要。

## 步骤 4：创建 OpenAI 模型实例

准备好 API 密钥后，您现在可以创建 OpenAI 模型的实例了。对于文档摘要，我们将使用 Gpt4OMini 模型：

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
此步骤实质上设置了总结文档所需的脑力，让您可以进行人工智能驱动的总结。

## 步骤5：总结单个文档

我们先来总结一下第一份文件。奇迹就在这里发生：

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
这里我们使用 `Summarize` 模型的方法。 `SummaryLength.Short` 参数指定我们想要一个简短的摘要——非常适合快速概览！

## 步骤 6：汇总多个文档

雄心勃勃？您可以一次汇总多个文档。看看它有多简单：

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
此功能在比较多个文件时特别方便。也许您正在准备会议，需要从几份冗长的报告中提取简洁的笔记。这就是您的新朋友！

## 结论

使用 Aspose.Words for .NET 和 OpenAI 来总结文档不仅是一项有益的技能，还能带来强大的力量。遵循本指南，您可以将冗长复杂的文本转化为简洁的摘要，从而节省时间和精力。无论您是要确保客户理解清晰，还是要准备重要的演示文稿，现在您都拥有了高效完成这些工作的工具。

那么，您还在等什么？放心地深入研究您的文档，让科技来帮您完成繁重的工作！

## 常见问题解答

### 什么是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一个强大的库，使开发人员能够以编程方式创建、操作和转换文档。

### 我需要 OpenAI 的 API 密钥吗？  
是的，您必须拥有有效的 OpenAI API 密钥才能使用其模型访问摘要功能。

### 我可以一次汇总多个文档吗？  
当然！一次通话即可汇总多个文档，非常适合大型报告。

### 如何安装 Aspose.Words？  
您可以通过 Visual Studio 中的 NuGet 包管理器搜索“Aspose.Words”来安装它。

### Aspose.Words 有免费试用版吗？  
是的，您可以通过他们的 [网站](https://releases。aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}