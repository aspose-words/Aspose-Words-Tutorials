---
"description": "通过本分步指南了解如何在 Aspose.Words for .NET 中创建具有绝对、相对和自动宽度设置的表格。"
"linktitle": "首选宽度设置"
"second_title": "Aspose.Words文档处理API"
"title": "首选宽度设置"
"url": "/zh/net/programming-with-tables/preferred-width-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 首选宽度设置

## 介绍

表格是组织和呈现 Word 文档信息的有效方式。在 Aspose.Words for .NET 中使用表格时，您可以使用多种选项设置表格单元格的宽度，以确保它们完美契合文档的布局。本指南将引导您使用 Aspose.Words for .NET 创建具有首选宽度设置的表格，重点介绍绝对、相对和自动调整大小选项。 

## 先决条件

在深入学习本教程之前，请确保您已具备以下条件：

1. Aspose.Words for .NET：确保您的开发环境中已安装 Aspose.Words for .NET。您可以下载 [这里](https://releases。aspose.com/words/net/).

2. .NET 开发环境：设置 .NET 开发环境，例如 Visual Studio。

3. C# 基础知识：熟悉 C# 编程将帮助您更好地理解代码片段和示例。

4. Aspose.Words 文档：请参阅 [Aspose.Words 文档](https://reference.aspose.com/words/net/) 了解详细的 API 信息和进一步阅读内容。

## 导入命名空间

在开始编码之前，您需要将必要的命名空间导入到您的 C# 项目中：

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

这些命名空间提供对 Aspose.Words 和 Table 对象的核心功能的访问，允许您操作文档表。

让我们将创建具有不同首选宽度设置的表格的过程分解为清晰、易于管理的步骤。

## 步骤 1：初始化 Document 和 DocumentBuilder

标题：创建新文档和 DocumentBuilder

说明：首先创建一个新的 Word 文档和一个 `DocumentBuilder` 实例。该 `DocumentBuilder` 类提供了一种向文档添加内容的简单方法。

```csharp
// 定义保存文档的路径。
string dataDir = "YOUR DOCUMENT DIRECTORY";

// 创建一个新文档。
Document doc = new Document();

// 为该文档创建一个 DocumentBuilder。
DocumentBuilder builder = new DocumentBuilder(doc);
```

在这里，您可以指定文档的保存目录并初始化 `Document` 和 `DocumentBuilder` 对象。

## 步骤 2：插入具有绝对宽度的第一个表格单元格

将第一个单元格插入表格，固定宽度为 40 点。这样可以确保无论表格大小如何，该单元格的宽度始终保持为 40 点。

```csharp
// 插入绝对大小的单元格。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

在此步骤中，您将开始创建表格并插入具有绝对宽度的单元格。 `PreferredWidth.FromPoints(40)` 方法将单元格的宽度设置为 40 点，并且 `Shading.BackgroundPatternColor` 应用浅黄色背景颜色。

## 步骤 3：插入相对大小的单元格

插入另一个宽度为表格总宽度 20% 的单元格。此相对大小设置可确保单元格根据表格宽度按比例调整。

```csharp
// 插入相对（百分比）大小的单元格。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

该单元格的宽度将占表格总宽度的 20%，使其能够适应不同的屏幕尺寸或文档布局。

### 步骤 4：插入自动调整大小的单元格

最后，插入一个根据表格中剩余可用空间自动调整大小的单元格。

```csharp
// 插入自动调整大小的单元格。
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. 这 size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

The `PreferredWidth.Auto` 此设置允许此单元格根据其他单元格被占用后的剩余空间进行扩展或收缩。这可确保表格布局看起来平衡且专业。

## 步骤5：完成并保存文档

插入所有单元格后，完成表格并将文档保存到指定路径。

```csharp
// 保存文档。
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

此步骤完成表格并将文档以文件名“WorkingWithTables.PreferredWidthSettings.docx”保存在指定的目录中。

## 结论

了解了不同的尺寸选项后，在 Aspose.Words for .NET 中创建具有首选宽度设置的表格就变得非常简单。无论您需要固定、相对还是自动单元格宽度，Aspose.Words 都能灵活高效地处理各种表格布局场景。按照本指南中概述的步骤操作，您可以确保 Word 文档中的表格结构合理且外观美观。

## 常见问题解答

### 绝对单元格宽度和相对单元格宽度有什么区别？
绝对单元格宽度是固定的，不会改变，而相对宽度会根据表格的总宽度进行调整。

### 我可以使用负百分比来表示相对宽度吗？
不可以，负百分比对于单元格宽度无效。只允许使用正百分比。

### 自动调整尺寸功能如何工作？
自动调整大小功能会在调整其他单元格大小后调整单元格的宽度以填充表格中剩余的空间。

### 我可以对具有不同宽度设置的单元格应用不同的样式吗？
是的，您可以对单元格应用各种样式和格式，而不管其宽度设置如何。

### 如果表格的总宽度小于所有单元格宽度的总和会发生什么？
表格将自动调整单元格的宽度以适应可用空间，这可能会导致某些单元格缩小。


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}