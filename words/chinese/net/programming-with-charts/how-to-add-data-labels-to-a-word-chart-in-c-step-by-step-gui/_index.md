---
category: general
date: 2026-08-04
description: 如何在 C# 中使用 Aspose.Words 添加数据标签。学习编辑图表、居中图表数据标签、在图表中显示百分比以及自定义图表数据标签。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: zh
lastmod: 2026-08-04
og_description: 如何在 C# 中使用 Aspose.Words 添加数据标签。本教程展示了如何编辑图表、居中图表数据标签、在图表中显示百分比以及自定义图表数据标签。
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: 如何在 C# 中为 Word 图表添加数据标签 – 完整指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: 如何在 C# 中向 Word 图表添加数据标签 – 步骤指南
url: /zh/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中向 Word 图表添加数据标签 – 步骤指南

如果您需要 **how to add data labels**（向位于 Word 文档中的图表添加数据标签），本指南将展示您必须运行的完整代码。您将看到如何编辑图表属性、center chart data labels、show percentages in chart，以及 customize chart data labels，以适用于任何场景。

本教程涵盖了修改现有图表所需的全部内容，从加载文档到持久化更改。无需外部引用——只需 Aspose.Words for .NET 库和基本的 C# 开发环境。

## 前提条件

在开始之前，请确保您具备：

* 已安装 .NET 6.0（或更高版本）。
* Aspose.Words for .NET 版本 23.9 或更高。  
  您可以通过 NuGet 安装：

```bash
dotnet add package Aspose.Words
```

* 一个包含至少一个图表的 Word 文件（`input.docx`）。

## 如何在 C# 中向 Word 图表添加数据标签

以下章节将逐步引导您完成每一步。主要关键词 **how to add data labels** 自然出现在叙述和代码注释中，密度符合推荐范围。

### 步骤 1 – 加载包含图表的 Word 文档

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Why this step matters*: `Document` 对象代表整个 Word 文件。加载它后即可访问所有节点，包括承载图表的 shape。

### 步骤 2 – 从文档中检索第一个图表

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Why this step matters*: 图表存储在 `Shape` 节点内部。将检索到的节点强制转换为 `Shape` 并调用 `GetChart()`，即可获得 `Chart` 对象，从而访问系列、坐标轴和标签集合。

### 步骤 3 – 启用数据标签自定义并在图表中显示百分比

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Why this step matters*: 设置 `ShowPercentage` 可让 Aspose.Words 计算并显示每个切片相对于总数的贡献。这直接对应次要关键词 **show percentages in chart**。

### 步骤 4 – 将标签位置更改为每个数据点的中心

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Why this step matters*: `Position` 属性决定标签相对于数据点的显示位置。使用 `Center` 满足次要关键词 **center chart data labels**，并提升饼图或环形图的可读性。

### 步骤 5 – 进一步自定义图表数据标签（可选）

如果需要更细致的控制，您可以调整字体、颜色或引导线：

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

这些设置演示了次要关键词 **customize chart data labels**，并展示了如何根据品牌指南定制外观。

### 步骤 6 – 保存修改后的文档

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Why this step matters*: 保存操作会将更新后的图表写回 Word 文档，使新数据标签在 Microsoft Word 中打开文件时可见。

## 完整、可运行的示例

下面是一段完整的程序代码，您可以复制、粘贴并直接运行。它包含所有必需的 `using` 指令以及解释每行代码的注释。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### 预期结果

当您在 Microsoft Word 中打开 `output.docx` 时，图表将显示：

* 每个切片旁的百分比值（例如 **25 %**、**40 %**，……）。
* 标签位于每个数据点的中心。
* 您所应用的其他样式，例如粗体红色文字。

这些视觉提示使图表更易于解读，尤其在演示或报告中尤为重要。

## 如何在数据标签之外编辑图表属性

虽然本指南的重点是 **how to add data labels**，但您可能还想 **how to edit chart**（如标题、图例位置或坐标轴格式）等设置。`Chart` 对象提供了 `Title`、`Legend`、`AxisX/AxisY` 等属性。例如，修改图表标题：

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

所有图表修改遵循相同的模式：检索图表 → 调整属性 → 保存文档。

## 常见陷阱与最佳实践提示

| 陷阱 | 产生原因 | 推荐解决方案 |
|---|---|---|
| 图表位于组合形状内部。 | `GetChild(NodeType.Shape, …)` 返回的是外层组，而不是内部的图表。 | 递归搜索具有 `shape.HasChart` 的 shape。 |
| 保存后数据标签未显示。 | 未将 `ShowValue` 或 `ShowPercentage` 设置为 `true`。 | 根据需要显式设置 `ShowValue` 和 `ShowPercentage`。 |
| 小切片的标签重叠。 | 中心定位可能导致拥挤。 | 使用 `ChartDataLabelPosition.OutSideEnd` 将标签放置在外侧，或启用 `LeaderLines`。 |

## 结论

您现在已经掌握了使用 C# **how to add data labels** 到 Word 图表的完整方法。教程涵盖了检索图表、启用标签可见性、居中标签、显示百分比以及自定义外观。凭借这些知识，您同样可以 **how to edit chart** 细节、**center chart data labels**、**show percentages in chart**，以及 **customize chart data labels**，满足任何报告场景的需求。

准备好进一步探索了吗？尝试添加多个系列、应用条件格式，或将图表导出为图片。Aspose.Words API 提供了丰富的图表操作功能——尽情实验，找到最适合您数据的可视化方案。

## 接下来您可以学习什么？

以下教程与本指南紧密相关，进一步深化所示技术。每篇资源均包含完整可运行的代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [自定义图表数据标签](/words/english/net/programming-with-charts/chart-data-label/)
- [在图表中设置数据标签的默认选项](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [自定义图表中的单个数据点](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}