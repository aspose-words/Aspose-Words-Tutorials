---
category: general
date: 2026-09-21
description: 如何使用 C# 在 Word 折线图中格式化系列。学习创建 Word 文档、插入折线图并应用自定义数字格式。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: zh
lastmod: 2026-09-21
og_description: 如何使用 C# 在 Word 折线图中格式化系列。本教程展示了如何创建 Word 文档、插入折线图并应用自定义数字格式。
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: 如何使用 C# 在 Word 折线图中格式化系列——一步步指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: 如何使用 C# 在 Word 折线图中格式化系列
url: /zh/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 折线图中格式化系列（使用 C#）

如果您需要 **在 Word 折线图中格式化系列**，本指南为您提供完整、可直接运行的解决方案。您将看到如何 **创建 Word 文档**、**插入折线图**，以及 **对 Y 轴数值应用自定义数字格式**——全部使用 Aspose.Words for .NET。

一旦了解图表对象模型，Word 自动化就变得简单明了。完成本教程后，您将拥有一个包含折线图的 Word 文件，数据系列将以保留两位小数的百分比形式显示。

## 您将实现的目标

* 以编程方式生成一个空的 `.docx` 文件。  
* 添加一个大小为 400 × 300 点的折线图。  
* 访问图表的第一个数据系列。  
* 应用格式代码 `#,##0.00%`，使 Y 轴数值显示为百分比。  

无需任何外部工具，只需 Aspose.Words NuGet 包。

## 前置条件

* .NET 6.0 SDK 或更高版本。  
* Visual Studio 2022（或任意 C# IDE）。  
* Aspose.Words for .NET 23.10 或更新版本 – 通过 `dotnet add package Aspose.Words` 安装。  

该代码可在 Windows、Linux 和 macOS 上运行，因为 Aspose.Words 与平台无关。

## 使用 Aspose.Words 创建 Word 文档

第一步是实例化一个 `Document` 对象。该对象在内存中表示整个 Word 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*为什么这很重要*：`Document` 是所有 Word 处理操作的入口。没有它，您无法添加段落、表格或图表。

## 向文档插入折线图

`DocumentBuilder` 用于向 `Document` 写入内容。调用 `InsertChart` 会在当前页面创建一个图表形状。

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*为什么这很重要*：`InsertChart` 返回一个 `Chart` 对象，您可以完全控制系列、坐标轴和格式。尺寸参数以点为单位（1 点 = 1/72 英寸）。

## 访问第一个数据系列

每个图表包含一个或多个 `ChartSeries`。第一个系列的索引为 0。

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*为什么这很重要*：`ChartSeries` 对象保存单条折线的 Y 值、X 值以及格式选项。修改该对象即可改变数据的可视化表现。

## 对系列应用自定义数字格式

`FormatCode` 属性决定数值的显示方式。将其设为 `#,##0.00%` 即可让 Word 将数值视为保留两位小数的百分比。

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*为什么这很重要*：如果不使用自定义格式，Word 会显示原始小数（例如 `0.15`）。格式代码会将其转换为 `15.00%`，这正是业务报告常见的需求。

## 保存文档并验证结果

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

当您在 Microsoft Word 中打开 `FormattedSeriesLineChart.docx` 时，会看到折线图的 Y 轴标签显示为 `15.00%`、`30.00%`、`45.00%` 和 `60.00%`。图表尺寸与 `InsertChart` 中提供的尺寸相匹配。

### 预期输出截图

> *图片：显示带有百分比格式化 Y 轴数值的折线图的 Word 文档页面。*  
> *(Alt text: 截图显示 Word 文档中的折线图，Y 轴数值已按百分比格式化)*

## 常见变体和边缘情况

| 情形 | 调整 |
|-----------|------------|
| **多个系列** | 遍历 `chart.Series`，为每个系列设置 `FormatCode`。 |
| **不同的图表类型** | 将 `ChartType.Line` 替换为 `ChartType.Column`、`ChartType.Pie` 等。 |
| **区域特定的分隔符** | 使用 `CultureInfo` 感知的格式字符串，例如法语地区的 `"# ##0,00 %"`。 |
| **动态数据源** | 在应用格式之前，从数据库或 CSV 文件填充 `series.YValues`。 |

**专业提示**：始终在添加 Y 值之后再应用格式。先设置格式再添加数值也可行，但后置格式可确保格式作用于最终的数据集。

## 小结

现在您已经掌握了 **如何在 Word 折线图中格式化系列**（使用 C#）。本教程涵盖了：

* 创建 Word 文档（`create word document`）。  
* 插入折线图（`insert line chart`、`add chart to word`）。  
* 访问图表的第一个系列。  
* 对显示为百分比的数值应用自定义数字格式（`apply custom number format`）。

## 后续步骤

* 尝试不同的 `ChartType` 值，观察其他可视化效果。  
* 使用 `chart.Title`、`chart.AxisX.Title` 和 `chart.AxisY.Title` 添加标题、坐标轴标签和图例。  
* 将图表导出为图像（`chart.Save` 与 `SaveFormat.Png`），用于网页报告。

欢迎将此模式用于生成仪表盘、财务报告或任何需要程序化绘图的文档。祝编码愉快！


## 接下来您应该学习什么？

以下教程涵盖与本指南紧密相关的主题，帮助您进一步掌握 API 功能并探索在项目中的其他实现方式。每个资源均包含完整的可运行代码示例和逐步说明。

- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}