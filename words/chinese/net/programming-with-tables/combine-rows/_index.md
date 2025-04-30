---
"description": "通过我们的分步指南了解如何使用 Aspose.Words for .NET 将多个表中的行合并为一个。"
"linktitle": "合并行"
"second_title": "Aspose.Words文档处理API"
"title": "合并行"
"url": "/zh/net/programming-with-tables/combine-rows/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 合并行

## 介绍

将多个表中的行合并成一个统一的表可能是一项艰巨的任务。但有了 Aspose.Words for .NET，这一切都变得轻而易举！本指南将引导您完成整个过程，让您轻松无缝地合并表。无论您是经验丰富的开发人员还是刚刚入门，本教程都将为您提供宝贵的帮助。那么，让我们深入研究，将这些分散的行合并成一个统一的表。

## 先决条件

在进入编码部分之前，让我们确保您拥有所需的一切：

1. Aspose.Words for .NET：您可以下载 [这里](https://releases。aspose.com/words/net/).
2. 开发环境：Visual Studio 或任何其他 .NET 兼容 IDE。
3. C# 基础知识：了解 C# 将会很有帮助。

如果您还没有 Aspose.Words for .NET，您可以获取 [免费试用](https://releases.aspose.com/) 或者购买 [这里](https://purchase.aspose.com/buy)。如有任何疑问， [支持论坛](https://forum.aspose.com/c/words/8) 是一个很好的起点。

## 导入命名空间

首先，您需要导入必要的命名空间。这将允许您访问 Aspose.Words 类和方法。操作方法如下：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;
```

现在我们已经设置好了一切，让我们将过程分解为易于遵循的步骤。

## 步骤 1：加载文档

第一步是加载你的 Word 文档。该文档应该包含你想要合并的表格。以下是加载文档的代码：

```csharp
// 文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Tables.docx");
```

在此示例中，替换 `"YOUR DOCUMENT DIRECTORY"` 以及您的文档的路径。

## 第 2 步：识别表

接下来，您需要确定要合并的表格。Aspose.Words 允许您使用 `GetChild` 方法。操作方法如下：

```csharp
Table firstTable = (Table) doc.GetChild(NodeType.Table, 0, true);
Table secondTable = (Table) doc.GetChild(NodeType.Table, 1, true);
```

在这段代码中，我们从文档中获取第一个和第二个表。

## 步骤 3：将第二个表中的行附加到第一个表中

现在，是时候合并这些行了。我们将把第二个表中的所有行附加到第一个表中。这可以通过一个简单的 while 循环来完成：

```csharp
// 将第二个表中的所有行附加到第一个表
while (secondTable.HasChildNodes)
    firstTable.Rows.Add(secondTable.FirstRow);
```

该循环一直持续，直到第二个表中的所有行都添加到第一个表中。

## 步骤 4：删除第二张表

添加行后，第二个表不再需要。您可以使用 `Remove` 方法：

```csharp
secondTable.Remove();
```

## 步骤5：保存文档

最后，保存修改后的文档。此步骤可确保您的更改写入文件：

```csharp
doc.Save(dataDir + "WorkingWithTables.CombineRows.docx");
```

就这样！您已成功使用 Aspose.Words for .NET 将两个表中的行合并为一个。

## 结论

将多个表中的行合并为一个表可以显著简化您的文档处理任务。使用 Aspose.Words for .NET，这项任务变得简单高效。按照本分步指南操作，您可以轻松合并表格并简化工作流程。

如果您需要更多信息或有任何疑问， [Aspose.Words 文档](https://reference.aspose.com/words/net/) 是一个很好的资源。您还可以探索购买选项 [这里](https://purchase.aspose.com/buy) 或者得到 [临时执照](https://purchase.aspose.com/temporary-license/) 用于测试。

## 常见问题解答

### 我可以合并具有不同列数的表格吗？

是的，Aspose.Words 允许您合并表格，即使它们具有不同的列数和宽度。

### 合并后行的格式会发生什么变化？

当行附加到第一个表时，行的格式将被保留。

### 可以合并两个以上的表吗？

是的，您可以通过对每个附加表重复这些步骤来合并多个表。

### 我可以针对多个文档自动执行此过程吗？

当然！您可以创建一个脚本来自动执行多个文档的此过程。

### 如果我遇到问题，我可以在哪里获得帮助？

这 [Aspose.Words 支持论坛](https://forum.aspose.com/c/words/8) 是获得帮助和寻找常见问题解决方案的好地方。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}