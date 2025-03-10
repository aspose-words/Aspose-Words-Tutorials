---
title: 使用生成器插入文档
linktitle: 使用生成器插入文档
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 合并两个 Word 文档。使用 DocumentBuilder 插入文档并保留格式的分步指南。
weight: 10
url: /zh/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用生成器插入文档

## 介绍

因此，您有两个 Word 文档，并且希望将它们合并为一个。您可能会想，“有没有一种简单的方法可以通过编程来完成此操作？”当然！今天，我将引导您完成使用 Aspose.Words for .NET 库将一个文档插入另一个文档的过程。这种方法非常方便，尤其是在处理大型文档或需要自动化该过程时。让我们开始吧！

## 先决条件

在开始之前，请确保您已获得所需的一切：

1.  Aspose.Words for .NET：如果你还没有，你可以从[这里](https://releases.aspose.com/words/net/).
2. 开发环境：确保您已安装 Visual Studio 或任何其他合适的 IDE。
3. C# 基础知识：对 C# 有一点熟悉将会大有帮助。

## 导入命名空间

首先，您需要导入必要的命名空间以访问 Aspose.Words 库功能。操作方法如下：

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

现在我们已经满足了先决条件，让我们逐步分解该过程。

## 步骤 1：设置文档目录

在开始编码之前，您需要设置文档目录的路径。这是存储源文档和目标文档的地方。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

代替`"YOUR DOCUMENT DIRECTORY"`替换为文档所在的实际路径。这将有助于程序轻松找到您的文件。

## 步骤 2：加载源文档和目标文档

接下来，我们需要加载要处理的文档。在此示例中，我们有一个源文档和一个目标文档。

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

在这里，我们使用`Document` Aspose.Words 库中的类来加载我们的文档。确保文件名与目录中的文件名匹配。

## 步骤3：创建 DocumentBuilder 对象

这`DocumentBuilder`类是 Aspose.Words 库中的一个强大工具。它允许我们导航和操作文档。

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

在此步骤中，我们创建了一个`DocumentBuilder`目标文档的对象。这将帮助我们将内容插入文档。

## 步骤 4：移至文档末尾

在插入源文档之前，我们需要将构建器光标移动到目标文档的末尾。

```csharp
builder.MoveToDocumentEnd();
```

这可确保源文档插入到目标文档的末尾。

## 步骤 5：插入分页符

为了保持整洁，我们在插入源文档之前添加分页符。这将在新页面上开始源文档的内容。

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

分页符可确保源文档内容从新页面开始，使合并的文档看起来更专业。

## 步骤 6：插入源文档

现在到了令人兴奋的部分——将源文档实际插入目标文档。

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

使用`InsertDocument`方法，我们可以将整个源文档插入到目标文档中。`ImportFormatMode.KeepSourceFormatting`确保源文档的格式得以保留。

## 步骤 7：保存合并文档

最后，让我们保存合并的文档。这会将源文档和目标文档合并为一个文件。

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

通过保存文档，我们完成了两个文档的合并过程。您的新文档现已准备好并保存在指定的目录中。

## 结论

就这样！您已成功使用 Aspose.Words for .NET 将一个文档插入另一个文档。此方法不仅高效，而且保留了两个文档的格式，确保无缝合并。无论您是在处理一次性项目还是需要自动化文档处理，Aspose.Words for .NET 都能满足您的需求。

## 常见问题解答

### 什么是 Aspose.Words for .NET？  
Aspose.Words for .NET 是一个功能强大的库，允许开发人员以编程方式创建、编辑、转换和操作 Word 文档。

### 我可以保留源文档的格式吗？  
是的，通过使用`ImportFormatMode.KeepSourceFormatting`，将源文档插入目标文档时，其格式将被保留。

### 我需要许可证才能使用 Aspose.Words for .NET 吗？  
是的，Aspose.Words for .NET 需要许可证才能使用全部功能。您可以获得[临时执照](https://purchase.aspose.com/temporary-license/)进行评估。

### 我可以自动完成这个过程吗？  
绝对可以！所描述的方法可以合并到更大的应用程序中，以自动执行文档处理任务。

### 我可以在哪里找到更多资源和支持？  
欲了解更多信息，您可以查看[文档](https://reference.aspose.com/words/net/)或访问[支持论坛](https://forum.aspose.com/c/words/8)寻求帮助。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
