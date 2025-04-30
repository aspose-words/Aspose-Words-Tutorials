---
"description": "使用 Aspose.Words for .NET 和 Google AI 提升您的文档处理能力，轻松创建简洁的摘要。"
"linktitle": "使用 Google AI 模型"
"second_title": "Aspose.Words文档处理API"
"title": "使用 Google AI 模型"
"url": "/zh/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Google AI 模型

## 介绍

在本文中，我们将逐步探索如何使用 Aspose.Words 和 Google 的 AI 模型来汇总文档。无论您是想精简冗长的报告，还是想从多个来源提取洞见，我们都能满足您的需求。

## 先决条件

在深入实践部分之前，我们先确保你已经做好了成功的准备。以下是你需要准备的：

1. C# 和 .NET 的基础知识：熟悉编程概念将帮助您更好地掌握示例。
   
2. Aspose.Words for .NET Library：这个强大的库允许您无缝地创建和操作 Word 文档。您可以 [点击此处下载](https://releases。aspose.com/words/net/).

3. Google AI 模型的 API 密钥：要使用 AI 模型，您需要一个 API 密钥进行身份验证。请将其安全地存储在您的环境变量中。

4. 开发环境：确保您已设置好可用的 .NET 环境（Visual Studio 或任何其他 IDE）。

5. 示例文档：您需要示例 Word 文档（例如“Big document.docx”、“Document.docx”）来测试摘要。

现在我们已经介绍了基础知识，让我们深入研究代码！

## 导入包

要使用 Aspose.Words 并集成 Google AI 模型，您需要导入必要的命名空间。操作方法如下：

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

现在您已经导入了必要的包，让我们逐步分解汇总文档的过程。

## 步骤 1：设置文档目录

在处理文档之前，我们需要指定文件所在的位置。此步骤对于确保 Aspose.Words 能够访问文档至关重要。

```csharp
// 您的文档目录
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// 您的 ArtifactsDir 目录
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

代替 `"YOUR_DOCUMENT_DIRECTORY"` 和 `"YOUR_ARTIFACTS_DIRECTORY"` 与您系统中存储文档的实际路径一致。这将作为阅读和保存文档的基准。

## 步骤2：加载文档

接下来，我们需要加载需要汇总的文档。在本例中，我们将加载我们之前指定的两个文档。

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

这 `Document` Aspose.Words 中的类允许您将 Word 文件加载到内存中。请确保文件名与目录中的实际文档匹配，否则您将遇到文件未找到的错误！

## 步骤 3：检索 API 密钥

要使用 AI 模型，您需要获取 API 密钥。该密钥是您访问 Google AI 服务的凭证。

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

这行代码会获取您存储在环境变量中的 API 密钥。出于安全考虑，最好将 API 密钥等敏感信息保留在代码之外。

## 步骤4：创建AI模型实例

现在，是时候创建 AI 模型的实例了。在这里，您可以选择要使用的模型——在本例中，我们选择 GPT-4 Mini 模型。

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

这行代码设置了用于文档摘要的 AI 模型。请务必咨询 [文档](https://reference.aspose.com/words/net/) 了解不同型号及其功能的详细信息。

## 步骤5：总结单个文档

让我们重点总结一下第一份文档。我们可以选择在这里获取一个简短的摘要。

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

在此步骤中，我们使用 `Summarize` 方法从 AI 模型实例中获取第一个文档的精简版本。摘要长度设置为短，但您可以根据需要自定义。最后，摘要文档将保存到您的 artifacts 目录中。

## 步骤 6：汇总多个文档

想要一次性汇总多个文档吗？Aspose.Words 也能轻松实现！

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

在这里，我们称之为 `Summarize` 再次使用该方法，但这次使用的是文档数组。这将为您提供一个较长的摘要，其中概括了两个文件的精髓。与之前一样，结果将保存在指定的 artifacts 目录中。

## 结论

就这样！您已成功搭建了一个使用 Aspose.Words for .NET 和 Google AI 模型进行文档摘要的环境。从加载文档到创建简洁的摘要，这些步骤提供了一种高效管理大量文本的简化方法。

## 常见问题解答

### 什么是 Aspose.Words？
Aspose.Words 是一个功能强大的库，可以使用 .NET 创建、修改和转换 Word 文档。

### 如何获取 Google AI 的 API 密钥？
您通常可以通过注册 Google Cloud 并启用必要的 API 服务来获取 API 密钥。

### 我可以一次汇总多个文档吗？
是的！正如演示所示，您可以将文档数组传递给摘要方法。

### 我可以创建哪些类型的摘要？
您可以根据需要选择短摘要、中摘要和长摘要。

### 在哪里可以找到更多 Aspose.Words 资源？
查看 [文档](https://reference.aspose.com/words/net/) 以获取更多示例和指导。



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}