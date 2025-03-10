---
title: 使用 AI 模型
linktitle: 使用 AI 模型
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 通过 AI 总结文档。增强文档管理的简单步骤。
weight: 10
url: /zh/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 AI 模型

## 介绍

欢迎来到 Aspose.Words for .NET 的迷人世界！如果您曾经希望将文档管理提升到一个新的水平，那么您来对地方了。想象一下，只需几行代码就能自动汇总大型文档。听起来很棒，对吧？在本指南中，我们将深入探讨如何使用 Aspose.Words 使用强大的 AI 语言模型（如 OpenAI 的 GPT）生成文档摘要。无论您是希望增强应用程序的开发人员，还是渴望学习新知识的技术爱好者，本教程都能满足您的需求。

## 先决条件

在我们撸起袖子开始编码之前，你需要做好以下几点准备：

1. 已安装 Visual Studio：确保您的计算机上已安装 Visual Studio。如果您尚未安装，可以免费下载。
  
2. .NET Framework：确保您使用的是与 Aspose.Words 兼容的 .NET Framework 版本。它支持 .NET Framework 和 .NET Core。

3.  Aspose.Words for .NET：您需要下载并安装 Aspose.Words。您可以获取最新版本[这里](https://releases.aspose.com/words/net/).

4. AI 模型的 API 密钥：要利用 AI 摘要，您需要访问 AI 模型。从 OpenAI 或 Google 等平台获取您的 API 密钥。

5. C# 基础知识：要充分利用本教程，需要对 C# 编程有基本的了解。

一切都搞定了？太棒了！让我们进入最有趣的部分 - 导入所需的包。

## 导入包

为了利用 Aspose.Words 的功能并使用 AI 模型，我们首先要导入必要的软件包。操作方法如下：

### 创建新项目

首先，启动 Visual Studio 并创建一个新的控制台应用程序项目。

1. 打开 Visual Studio。
2. 点击“创建新项目”。
3. 根据您的设置选择“控制台应用程序（.NET Framework）”或“控制台应用程序（.NET Core）”。
4. 命名您的项目并指定位置。

### 安装 Aspose.Words 和 AI 模型包

要使用 Aspose.Words，您需要通过 NuGet 安装该包。

1. 在解决方案资源管理器中右键单击您的项目并选择“管理 NuGet 包”。
2. 搜索“Aspose.Words”然后单击“安装”。
3. 如果您使用任何特定的 AI 模型包（如 OpenAI），请确保也安装了这些包。
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
恭喜！软件包准备就绪后，让我们深入研究一下我们的实现。

## 步骤 1：设置文档目录

在我们的代码中，我们将定义目录来管理文档的存储位置以及输出的位置。 

```csharp
//您的文档目录
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
//你的 ArtifactsDir 目录
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

- 在这里，替换`YOUR_DOCUMENT_DIRECTORY`您的文档存储的位置以及`YOUR_ARTIFACTS_DIRECTORY`您想要保存汇总文件的位置。

## 步骤 2：加载文档

接下来，我们将要汇总的文档加载到程序中。这非常简单！操作方法如下：

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- 将文件名调整为您已保存的内容。本示例假设您有两个文档，分别名为“Big document.docx”和“Document.docx”。

## 步骤3：初始化AI模型

我们的下一步是与 AI 模型建立连接。这就是您之前获得的 API 密钥发挥作用的地方。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- 确保将 API 密钥存储为环境变量。这就像保护你的秘密武器一样！

## 步骤 4：生成第一个文档的摘要

现在，让我们为第一个文档创建摘要。我们还将设置参数来定义摘要长度。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- 此代码片段总结了第一个文档并将输出保存在您指定的工件目录中。您可以随意更改摘要长度以符合您的喜好！

## 步骤 5：生成多个文档的摘要

喜欢冒险吗？您还可以一次汇总多个文档！操作方法如下：

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- 就这样，您就可以同时汇总两个文档！效率真高，对吧？

## 结论

就这样！通过遵循本指南，您已经掌握了使用 Aspose.Words for .NET 和强大的 AI 模型总结文档的技巧。这是一个令人兴奋的功能，可以为您节省大量时间，无论是个人使用还是集成到专业应用程序中。现在继续，释放自动化的力量，并观察您的生产力飙升！

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，使开发人员能够以编程方式创建、修改、转换和呈现 Word 文档。

### 如何获取 AI 模型的 API 密钥？
您可以从 OpenAI 或 Google 等 AI 提供商处获取 API 密钥。请务必创建一个帐户并按照他们的说明生成密钥。

### 我可以将 Aspose.Words 用于其他文件格式吗？
是的！Aspose.Words 支持各种文件格式，包括 DOCX、RTF 和 HTML，除了文本文档之外还提供广泛的功能。

### Aspose.Words 有免费版本吗？
Aspose 提供免费试用，让您可以测试其功能。您可以从他们的网站下载。

### 在哪里可以找到更多有关 Aspose.Words 的资源？
您可以查看文档[这里](https://reference.aspose.com/words/net/)获得全面的指南和见解。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
