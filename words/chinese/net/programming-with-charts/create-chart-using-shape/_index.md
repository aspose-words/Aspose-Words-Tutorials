---
title: 使用形状创建和自定义图表
linktitle: 使用形状创建和自定义图表
second_title: Aspose.Words 文档处理 API
description: 通过本分步指南学习如何使用 Aspose.Words for .NET 在 Word 文档中创建和自定义图表。非常适合数据可视化。
weight: 10
url: /zh/net/programming-with-charts/create-chart-using-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用形状创建和自定义图表

## 介绍

在当今数据驱动的世界中，在文档中创建和自定义图表是一项关键技能。图表可以帮助可视化数据，使复杂的信息更易于理解。Aspose.Words for .NET 是一个功能强大的库，可让您以编程方式创建和操作 Word 文档。在本教程中，我们将引导您完成使用 Aspose.Words for .NET 创建和自定义折线图的过程。在本指南结束时，您将能够轻松创建具有专业外观的图表。

## 先决条件

在深入研究代码之前，请确保您已具备以下条件：

-  Aspose.Words for .NET 库：您可以下载[这里](https://releases.aspose.com/words/net/).
- Visual Studio：任何支持 .NET 的版本。
- C# 基础知识：了解 C# 的基础知识将帮助您跟随本教程。

## 导入命名空间

首先，您需要导入必要的命名空间。此步骤至关重要，因为它允许您使用 Aspose.Words for .NET 提供的类和方法。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 步骤 1：创建新文档

首先，您需要创建一个新的 Word 文档。此文档将作为图表的画布。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 2：插入图表

接下来，您将在文档中插入一个折线图。`DocumentBuilder.InsertChart`方法就是用于此目的。

```csharp
Shape shape = builder.InsertChart(ChartType.Line, 432, 252);
Chart chart = shape.Chart;
```

## 步骤 3：自定义图表标题

自定义图表标题有助于为所显示的数据提供背景信息。您可以使用以下代码显示标题并设置其文本：

```csharp
chart.Title.Show = true;
chart.Title.Text = "Line Chart Title";
chart.Title.Overlay = false;
//请注意，如果将标题文本指定为空值或空值，则将显示自动生成的标题。
```

## 步骤 4：调整图例位置

图例有助于识别图表中的不同数据系列。您可以自定义其位置和叠加设置，如下所示：

```csharp
chart.Legend.Position = LegendPosition.Left;
chart.Legend.Overlay = true;
```

## 步骤 5：保存文档

最后，您需要保存文档。此步骤可确保您的所有更改都写入文件。

```csharp
doc.Save(dataDir + "WorkingWithCharts.CreateChartUsingShape.docx");
```

## 结论

在本教程中，我们介绍了如何使用 Aspose.Words for .NET 在 Word 文档中创建和自定义折线图。按照分步指南，您现在可以创建具有视觉吸引力的图表，以有效地传达您的数据。Aspose.Words for .NET 提供了广泛的自定义选项，允许您根据特定需求定制图表。

## 常见问题解答

### 我可以使用 Aspose.Words for .NET 创建其他类型的图表吗？

是的，Aspose.Words for .NET 支持各种图表类型，包括条形图、饼图等。您可以浏览文档[这里](https://reference.aspose.com/words/net/)了解更多详情。

### 购买之前如何试用 Aspose.Words for .NET？

您可以从下载免费试用版[这里](https://releases.aspose.com/)。这可让您在购买之前测试该库及其功能。

### 如果我遇到问题，有什么办法可以获得支持吗？

当然可以。您可以通过 Aspose 社区论坛获得支持[这里](https://forum.aspose.com/c/words/8)。社区和 Aspose 员工的响应非常积极。

### 如何购买 Aspose.Words for .NET 的许可证？

您可以直接从 Aspose 网站购买许可证[这里](https://purchase.aspose.com/buy)有多种许可选项可满足不同需求。

### 如果我需要短期项目的临时许可证怎么办？

 Aspose 提供临时许可证，您可以申请[这里](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
