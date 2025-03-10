---
title: 在 Word 文档中附加书签文本
linktitle: 在 Word 文档中附加书签文本
second_title: Aspose.Words 文档处理 API
description: 通过本分步指南了解如何使用 Aspose.Words for .NET 在 Word 文档中附加书签文本。非常适合开发人员。
weight: 10
url: /zh/net/programming-with-bookmarks/append-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 文档中附加书签文本

## 介绍

嗨！您是否曾尝试过从 Word 文档中的书签部分附加文本，但发现这很棘手？您很幸运！本教程将引导您完成使用 Aspose.Words for .NET 的过程。我们将把它分解为简单的步骤，以便您轻松跟进。让我们深入研究并像专业人士一样附加书签文本！

## 先决条件

在开始之前，请确保您已准备好所需的一切：

-  Aspose.Words for .NET：确保已安装。如果没有，您可以[点击下载](https://releases.aspose.com/words/net/).
- 开发环境：任何 .NET 开发环境，如 Visual Studio。
- C# 基础知识：了解基本的 C# 编程概念将会有所帮助。
- 带有书签的 Word 文档：设置了书签的 Word 文档，我们将使用它来附加文本。

## 导入命名空间

首先，让我们导入必要的命名空间。这将确保我们拥有所需的所有工具。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

我们将该示例分解为详细步骤。

## 步骤 1：加载文档并初始化变量

好的，让我们首先加载 Word 文档并初始化我们需要的变量。

```csharp
//加载源文档和目标文档。
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

//初始化文档导入器。
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

//在源文档中查找书签。
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## 第 2 步：确定开始和结束段落

现在，让我们找到书签开始和结束的段落。这很关键，因为我们需要处理这些范围内的文本。

```csharp
//这是包含书签开头的段落。
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;

//这是包含书签结尾的段落。
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

if (startPara == null || endPara == null)
    throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");
```

## 步骤 3：验证段落父级

我们需要确保开始和结束段落有相同的父级。这是一个简单的场景，以使事情变得简单。

```csharp
//将我们自己限制在一个相当简单的场景中。
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");
```

## 步骤 4：确定要停止的节点

接下来，我们需要确定停止复制文本的节点。这将是紧接在结束段落之后的节点。

```csharp
//我们希望复制从起始段落到结束段落（包括结束段落）的所有段落，
//因此我们停止的节点是最后一段之后的一个节点。
Node endNode = endPara.NextSibling;
```

## 步骤 5：将书签文本附加到目标文档

最后，让我们循环遍历从开始段落到结束段落之后的节点，并将它们附加到目标文档。

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    //这将创建当前节点的副本并将其导入上下文中（使其有效）
    //目标文档。导入意味着正确调整样式和列表标识符。
    Node newNode = importer.ImportNode(curNode, true);

    //将导入的节点附加到目标文档。
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

//将附加的文本与目标文档一起保存。
dstDoc.Save("appended_document.docx");
```

## 结论

就这样！您已成功使用 Aspose.Words for .NET 从 Word 文档的书签部分附加文本。这款功能强大的工具让文档操作变得轻而易举，现在您又多了一个绝招。祝您编码愉快！

## 常见问题解答

### 我可以一次添加多个书签中的文本吗？
是的，您可以对每个书签重复此过程并相应地附加文本。

### 如果开始和结束段落有不同的父级怎么办？
当前示例假设它们有相同的父级。对于不同的父级，需要更复杂的处理。

### 我可以保留附加文本的原始格式吗？
当然！`ImportFormatMode.KeepSourceFormatting`确保原始格式得以保留。

### 是否可以将文本附加到目标文档中的特定位置？
是的，您可以通过导航到目标文档中的所需节点将文本附加到任何位置。

### 如果我需要将书签中的文本附加到新的部分该怎么办？
您可以在目标文档中创建一个新的部分并将文本附加到那里。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
