---
title: 水平合并
linktitle: 水平合并
second_title: Aspose.Words 文档处理 API
description: 通过这个详细的分步教程学习如何使用 Aspose.Words for .NET 在 Word 文档中水平合并单元格。
weight: 10
url: /zh/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 水平合并

## 介绍

大家好！准备好进入 Aspose.Words for .NET 的世界了吗？今天，我们将介绍一个超级有用的功能：表格中的水平合并。这听起来可能有点技术性，但别担心，我会支持你的。在本教程结束时，您将成为以编程方式合并 Word 文档中单元格的专家。所以，让我们撸起袖子开始吧！

## 先决条件

在我们讨论细节之前，您需要做好以下几件事：

1. Aspose.Words for .NET 库：如果您还没有下载 Aspose.Words for .NET 库，请下载。您可以下载它[这里](https://releases.aspose.com/words/net/).
2. 开发环境：确保您已经设置了合适的开发环境，例如 Visual Studio。
3. C# 基础知识：对 C# 编程的基本了解将会很有帮助。

一旦将这些整理好，您就可以开始了！

## 导入命名空间

在深入研究代码之前，让我们确保已导入必要的命名空间。在您的 C# 项目中，请确保包含：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

好吧，让我们分解使用 Aspose.Words for .NET 在 Word 文档中水平合并表格单元格的过程。

## 步骤 1：设置文档

首先，我们需要创建一个新的 Word 文档并初始化`DocumentBuilder`：

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

此代码片段设置了一个新文档并准备`DocumentBuilder`采取行动。

## 步骤 2：插入第一个单元格

接下来，我们开始插入第一个单元格并将其标记为水平合并：

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

在这里，我们插入一个新单元格并设置其`HorizontalMerge`财产`CellMerge.First`，表示该单元格是合并单元格序列的开头。

## 步骤3：插入合并单元格

现在，我们插入将与前一个单元格合并的单元格：

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

此单元格设置为使用以下方式与前一个单元格合并`CellMerge.Previous`。注意我们如何用`builder.EndRow()`.

## 步骤 4：插入未合并的单元格

为了说明差异，让我们插入几个未合并的单元格：

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

这里我们插入两个没有水平合并的单元格。这显示了单元格不属于合并序列时的行为。

## 第五步：完成表格

最后，我们结束表格并保存文档：

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

此代码片段完成表格并将文档保存到指定目录。

## 结论

就这样！您已经掌握了使用 Aspose.Words for .NET 在 Word 文档中水平合并单元格的技巧。按照以下步骤操作，您可以轻松创建复杂的表格结构。继续尝试和探索 Aspose.Words 的功能，让您的文档尽可能动态和灵活。祝您编码愉快！

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个功能强大的库，允许开发人员在 .NET 应用程序中以编程方式创建、编辑和操作 Word 文档。

### 我可以使用 Aspose.Words for .NET 垂直合并单元格吗？
是的，您也可以使用`CellFormat.VerticalMerge`财产。

### Aspose.Words for .NET 可以免费使用吗？
Aspose.Words for .NET 提供免费试用，但要获得完整功能，您需要购买许可证。您可以获取临时许可证[这里](https://purchase.aspose.com/temporary-license/).

### 如何了解有关 Aspose.Words for .NET 的更多信息？
您可以探索详细文档[这里](https://reference.aspose.com/words/net/).

### 在哪里可以获得 Aspose.Words for .NET 的支持？
如有任何疑问或问题，您可以访问 Aspose 支持论坛[这里](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
