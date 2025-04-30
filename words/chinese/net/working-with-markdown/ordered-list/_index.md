---
"description": "通过我们的分步指南，学习如何使用 Aspose.Words for .NET 在 Word 文档中创建有序列表。非常适合自动化文档创建。"
"linktitle": "有序列表"
"second_title": "Aspose.Words文档处理API"
"title": "有序列表"
"url": "/zh/net/working-with-markdown/ordered-list/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 有序列表

## 介绍

既然您决定深入研究 Aspose.Words for .NET，以编程方式创建精彩的 Word 文档，这真是个绝佳的选择！今天，我们将详细讲解如何在 Word 文档中创建有序列表。我们将一步步讲解，无论您是编程新手还是经验丰富的专业人士，本指南都将对您大有裨益。让我们开始吧！

## 先决条件

在深入研究代码之前，您需要做以下几件事：

1. Aspose.Words for .NET：请确保您已安装 Aspose.Words for .NET。如果没有，您可以下载 [这里](https://releases。aspose.com/words/net/).
2. 开发环境：Visual Studio 或任何其他 .NET 兼容 IDE。
3. C# 基础知识：您应该熟悉 C# 基础知识，以便轻松跟进。

## 导入命名空间

要在项目中使用 Aspose.Words，您需要导入必要的命名空间。这就像在开始工作之前设置工具箱一样。

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

让我们把代码分解成几个小步骤，并解释每个部分。准备好了吗？开始吧！

## 步骤 1：初始化文档

首先，你需要创建一个新文档。就像在电脑上打开一个空白的Word文档一样。

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

这里，我们初始化一个新文档和一个 DocumentBuilder 对象。DocumentBuilder 就像你的笔，允许你将内容写入文档。

## 步骤 2：应用编号列表格式

现在，让我们应用默认的编号列表格式。这就像设置你的Word文档使用编号项目符号一样。

```csharp
builder.ListFormat.ApplyNumberDefault();
```

这行代码设置了列表的编号。很简单，对吧？

## 步骤 3：添加列表项

接下来，让我们在列表中添加一些物品。想象一下你正在记下一份购物清单。

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

通过这些行，您将前两个项目添加到列表中。

## 步骤 4：缩进列表

如果你想在某个项目下添加子项目怎么办？那就来吧！

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

这 `ListIndent` 方法缩进列表，并创建一个子列表。现在，您正在创建一个分层列表，就像嵌套的待办事项列表一样。

## 结论

乍一看，在 Word 文档中以编程方式创建有序列表似乎令人望而生畏，但有了 Aspose.Words for .NET，一切就变得轻而易举。只需遵循以下简单步骤，您便可轻松在文档中添加和管理列表。无论您是生成报告、创建结构化文档，还是仅仅自动化工作流程，Aspose.Words for .NET 都能满足您的需求。还在犹豫什么？立即开始编码，见证奇迹的发生！

## 常见问题解答

### 我可以自定义列表的编号样式吗？  
是的，您可以使用 `ListFormat` 属性。您可以设置不同的编号样式，如罗马数字、字母等。

### 如何添加更多级别的缩进？  
您可以使用 `ListIndent` 方法多次创建更深层次的子列表。每次调用 `ListIndent` 添加一级缩进。

### 我可以混合使用项目符号和编号列表吗？  
当然！您可以使用 `ListFormat` 财产。

### 是否可以从之前的列表继续编号？  
是的，您可以继续使用相同的列表格式进行编号。Aspose.Words 允许您控制不同段落的列表编号。

### 我怎样才能删除列表格式？  
您可以通过调用删除列表格式 `ListFormat.RemoveNumbers()`。这会将列表项变回常规段落。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}