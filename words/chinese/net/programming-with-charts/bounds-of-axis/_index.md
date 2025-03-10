---
title: 图表中的轴边界
linktitle: 图表中的轴边界
second_title: Aspose.Words 文档处理 API
description: 了解如何使用 Aspose.Words for .NET 设置图表中轴的边界，从而控制轴上显示的值的范围。
weight: 10
url: /zh/net/programming-with-charts/bounds-of-axis/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 图表中的轴边界

## 介绍

您是否希望使用 .NET 中的图表创建专业文档？您来对地方了！本指南将引导您完成使用 Aspose.Words for .NET 设置图表中轴的边界的过程。我们将分解每个步骤，以确保您可以轻松地跟进，即使您是库的新手。那么，让我们开始吧！

## 先决条件

在开始之前，请确保您已准备好以下内容：

-  Aspose.Words for .NET：您可以[下载](https://releases.aspose.com/words/net/)最新版本或使用[免费试用](https://releases.aspose.com/).
- .NET Framework：确保您的系统上安装了.NET。
- IDE：像 Visual Studio 这样的开发环境。

一旦一切准备就绪，我们就可以继续下一步。

## 导入命名空间

首先，您需要导入必要的命名空间。这将允许您访问 Aspose.Words 库及其图表功能。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;
```

## 步骤 1：设置文档目录

首先，您需要设置文档的保存目录。这是一个简单的步骤，但对于组织文件至关重要。

```csharp
//文档目录的路径
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## 第 2 步：创建新文档

接下来，创建一个新的文档对象。此文档将作为图表的容器。

```csharp
Document doc = new Document();
```

## 步骤 3：初始化文档生成器

DocumentBuilder 类提供了一种快速简便的方法来创建文档。使用您的文档对其进行初始化。

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 步骤 4：插入图表

现在，是时候将图表插入到文档中了。在此示例中，我们将使用柱形图。

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

## 步骤 5：清除现有系列

为了确保您从头开始，请清除图表中的所有现有系列。

```csharp
chart.Series.Clear();
```

## 步骤 6：向图表添加数据

在这里，我们向图表添加数据。这包括指定系列名称和数据点。

```csharp
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1.2, 0.3, 2.1, 2.9, 4.2 });
```

## 步骤 7：设置轴边界

设置 Y 轴的边界可确保您的图表正确缩放。

```csharp
chart.AxisY.Scaling.Minimum = new AxisBound(0);
chart.AxisY.Scaling.Maximum = new AxisBound(6);
```

## 步骤 8：保存文档

最后，将您的文档保存到指定目录。

```csharp
doc.Save(dataDir + "WorkingWithCharts.BoundsOfAxis.docx");
```

就这样！您已成功使用 Aspose.Words for .NET 创建了带有图表的文档。 

## 结论

使用 Aspose.Words for .NET，您可以轻松创建和操作文档中的图表。本分步指南向您展示了如何设置图表中轴的边界，使您的数据呈现更加精确和专业。无论您是生成报告、演示文稿还是任何其他文档，Aspose.Words 都能提供您所需的工具。

## 常见问题解答

### 什么是 Aspose.Words for .NET？
Aspose.Words for .NET 是一个库，允许您使用 .NET 框架以编程方式创建、修改和转换 Word 文档。

### 如何设置 Aspose.Words for .NET？
您可以从以下位置下载[这里](https://releases.aspose.com/words/net/)并按照提供的安装说明进行操作。

### 我可以免费使用 Aspose.Words 吗？
是的，你可以使用[免费试用](https://releases.aspose.com/)或者得到[临时执照](https://purchase.aspose.com/temporary-license/).

### 在哪里可以找到 Aspose.Words for .NET 的文档？
有详细文档可供查阅[这里](https://reference.aspose.com/words/net/).

### 如何获得 Aspose.Words 的支持？
您可以访问[支持论坛](https://forum.aspose.com/c/words/8)寻求帮助。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
