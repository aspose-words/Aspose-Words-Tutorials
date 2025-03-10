---
title: 导出到 Markdown 并对齐表格内容
linktitle: 导出到 Markdown 并对齐表格内容
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 将 Word 文档导出为带有对齐表格的 Markdown。按照我们的分步指南制作完美的 Markdown 表格。
weight: 10
url: /zh/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 导出到 Markdown 并对齐表格内容

## 介绍

嗨！有没有想过如何将 Word 文档导出为 Markdown 格式，并带有完美对齐的表格？无论您是从事文档工作的开发人员，还是只是喜欢 Markdown 的人，本指南都适合您。我们将深入研究使用 Aspose.Words for .NET 实现此目的的细节。准备好将您的 Word 表格转换为整齐对齐的 Markdown 表格了吗？让我们开始吧！

## 先决条件

在深入研究代码之前，您需要做好以下几件事：

1.  Aspose.Words for .NET 库：确保您拥有 Aspose.Words for .NET 库。您可以从[Aspose 发布页面](https://releases.aspose.com/words/net/).
2. 开发环境：设置您的开发环境。Visual Studio 是 .NET 开发的热门选择。
3. C# 基础知识：了解 C# 至关重要，因为我们将用这种语言编写代码。
4. 示例 Word 文档：有一个可用于测试的 Word 文档。

## 导入命名空间

在开始编码之前，让我们导入必要的命名空间。这将使我们能够访问我们将要使用的 Aspose.Words 类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## 步骤 1：初始化 Document 和 DocumentBuilder

首先，我们需要创建一个新的 Word 文档并初始化一个`DocumentBuilder`对象开始构建我们的文档。

```csharp
//文档目录的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";

//创建新文档。
Document doc = new Document();

//初始化 DocumentBuilder。
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 2：插入单元格并对齐内容

接下来，我们将在文档中插入一些单元格并设置它们的对齐方式。这对于确保 Markdown 导出保留正确的对齐方式至关重要。

```csharp
//插入一个单元格并设置右对齐。
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

//插入另一个单元格并将对齐设置为中心。
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## 步骤 3：设置 Markdown 导出的表格内容对齐方式

现在，是时候配置`MarkdownSaveOptions`控制导出的 Markdown 文件中表格内容的对齐方式。我们将使用不同的对齐设置保存文档，以查看其效果。

```csharp
//创建 MarkdownSaveOptions 对象。
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

//以左对齐保存文档。
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

//将对齐方式改为右对齐并保存。
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

//将对齐方式改为居中并保存。
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## 步骤 4：使用自动表格内容对齐

这`Auto`对齐选项从相应表格列中的第一个段落开始对齐。当单个表格中有混合对齐时，这会很方便。

```csharp
//将对齐设置为自动。
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

//使用自动对齐功能保存文档。
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## 结论

就这样！一旦您知道如何操作，使用 Aspose.Words for .NET 将 Word 文档导出到带有对齐表格的 Markdown 中就轻而易举了。这个功能强大的库可以轻松控制表格的格式和对齐方式，确保您的 Markdown 文档看起来正是您想要的样子。祝您编码愉快！

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，使开发人员能够以编程方式创建、修改、转换和导出 Word 文档。

### 我可以为同一张表中的不同列设置不同的对齐方式吗？
是的，通过使用`Auto`对齐选项，您可以根据每列的第一个段落进行不同的对齐。

### 我需要许可证才能使用 Aspose.Words for .NET 吗？
是的，Aspose.Words for .NET 需要许可证才能使用全部功能。您可以获得[临时执照](https://purchase.aspose.com/temporary-license/)进行评估。

### 是否可以使用 Aspose.Words 将其他文档元素导出到 Markdown？
是的，Aspose.Words 支持将标题、列表和图像等各种元素导出为 Markdown 格式。

### 如果我遇到问题，可以在哪里获得支持？
您可以从[Aspose.Words 支持论坛](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
