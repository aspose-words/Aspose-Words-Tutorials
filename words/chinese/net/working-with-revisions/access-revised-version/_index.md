---
"description": "了解如何使用 Aspose.Words for .NET 访问和显示文档的修订版本。按照我们的分步指南，实现无缝文档管理。"
"linktitle": "访问修订版本"
"second_title": "Aspose.Words文档处理API"
"title": "访问修订版本"
"url": "/zh/net/working-with-revisions/access-revised-version/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 访问修订版本

## 介绍

您是否曾经需要以编程方式访问文档的修订版本？无论您是在进行协作项目，还是仅仅需要管理文档修订，Aspose.Words for .NET 都是您的首选工具。本教程将引导您完成整个过程，从设置环境到在 Word 文档中访问和显示修订版本。那么，让我们开始吧！

## 先决条件

在我们开始之前，您需要准备一些东西：

1. Aspose.Words for .NET Library：您可以下载 [这里](https://releases。aspose.com/words/net/).
2. 开发环境：Visual Studio 或任何其他支持 .NET 的 IDE。
3. C# 基础知识：这将帮助您跟进编码部分。

在继续执行下一步之前，请确保已解决这些先决条件。

## 导入命名空间

首先，您需要导入必要的命名空间。这是确保您的代码能够识别 Aspose.Words for .NET 库的关键步骤。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

让我们将这个过程分解为简单、易于遵循的步骤。

## 步骤1：设置文档路径

在处理文档之前，您需要指定文档所在的路径。这对于代码查找和操作文件至关重要。

```csharp
// 文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 步骤2：加载文档

接下来，你需要将文档加载到应用程序中。此步骤涉及创建一个新的 `Document` 对象并使用文档的路径对其进行初始化。

```csharp
Document doc = new Document(dataDir + "Revisions.docx");
```

## 步骤3：更新列表标签

如果您的文档包含列表，请务必更新列表标签。这可以确保所有列表项都正确编号和格式。

```csharp
doc.UpdateListLabels();
```

## 步骤4：切换到修订版本

现在，让我们切换到文档的修订版本。如果您想访问并显示修订版本，此步骤至关重要。

```csharp
doc.RevisionsView = RevisionsView.Final;
```

## 步骤 5：迭代修订

要访问修订版本，您需要遍历 `Revisions` 文档的收集。此步骤涉及使用 `foreach` 循环进行每次修订。

```csharp
foreach (Revision revision in doc.Revisions)
{
    // 附加代码将放在此处
}
```

## 步骤6：检查父节点类型

对于每个修订版本，检查父节点是否属于类型 `Paragraph`。这很重要，因为我们想要访问包含修订的段落。

```csharp
if (revision.ParentNode.NodeType == NodeType.Paragraph)
{
    // 附加代码将放在此处
}
```

## 步骤 7：访问段落

一旦确认父节点是一个段落，就将其转换为 `Paragraph` 对象。此步骤允许您处理段落及其属性。

```csharp
Paragraph paragraph = (Paragraph)revision.ParentNode;
```

## 步骤 8：检查该段落是否为列表项

接下来，检查该段落是否为列表项。这很重要，因为列表项具有我们需要访问的特定属性。

```csharp
if (paragraph.IsListItem)
{
    // 附加代码将放在此处
}
```

## 步骤9：显示列表标签和级别

最后，显示段落的列表标签和列表级别。此步骤提供有关列表项的有用信息，例如其编号和缩进级别。

```csharp
Console.WriteLine(paragraph.ListLabel.LabelString);
Console.WriteLine(paragraph.ListFormat.ListLevel);
```

## 结论

就这样！您已成功使用 Aspose.Words for .NET 访问文档的修订版本。按照以下步骤操作，您可以轻松管理和显示文档修订版本。无论您是处理协作项目，还是仅仅需要跟踪更改，Aspose.Words for .NET 都能满足您的需求。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，允许您以编程方式创建、编辑和操作 Word 文档。

### 我可以访问任何 Word 文档中的修订版本吗？
是的，只要文档包含修订，您就可以使用 Aspose.Words for .NET 访问它们。

### 我需要许可证才能使用 Aspose.Words for .NET 吗？
是的，你可以从 [这里](https://purchase.aspose.com/buy)。他们还提供 [免费试用](https://releases.aspose.com/) 和一个 [临时执照](https://purchase。aspose.com/temporary-license/).

### Aspose.Words for .NET 是否与所有 .NET 版本兼容？
Aspose.Words for .NET 与多种 .NET 版本兼容。更多详细信息，请参阅 [文档](https://reference。aspose.com/words/net/).

### 在哪里可以获得 Aspose.Words for .NET 的支持？
您可以从 Aspose 社区获得支持 [论坛](https://forum。aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}