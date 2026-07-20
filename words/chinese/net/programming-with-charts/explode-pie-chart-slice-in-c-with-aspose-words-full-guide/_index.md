---
category: general
date: 2026-07-19
description: 使用 Aspose.Words for C# 突出显示饼图切片。学习如何突出显示饼图切片、调整环形图孔径大小以及快速更改图表数据点。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: zh
lastmod: 2026-07-19
og_description: 使用 Aspose.Words for C# 将饼图切片分离。本指南向您展示如何分离饼图切片、调整环形图孔径大小以及高效更改图表数据点。
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: 在 C# 中拆分饼图切片 – Aspose.Words 教程
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: 在 C# 中使用 Aspose.Words 将饼图切片拆分 – 完整指南
url: /zh/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 爆炸饼图切片 – 完整指南

有没有想过如何在 Word 文档中使用 C# **爆炸饼图切片**？你并不是唯一有此需求的人。无论是准备销售演示还是可视化调查结果，爆炸的切片都能把注意力精准地吸引到你想要的位置。在本教程中，我们将完整演示整个过程——加载文档、获取图表、爆炸第一块切片、调整环形图的孔径，甚至修改图表数据点。

我们还会顺带介绍你可能在寻找的次要概念：**如何爆炸饼图切片**、**调整环形图孔径大小**以及**更改图表数据点**。不啰嗦，直接给出完整的可复制粘贴的解决方案。

---

## 您需要的条件

- **Aspose.Words for .NET**（截至 2026‑07‑19 的最新版本）。您可以通过 NuGet 使用 `Install-Package Aspose.Words` 获取它。
- 一个 **.NET 6+** 项目（如果仍在使用旧版，则为 .NET Framework 4.7.2+）。
- 一个 Word 文件（`Chart.docx`），其中已经包含饼图或环形图。如果没有，可在 Word 中快速创建一个图表并保存。

就这些——无需额外库、无需 COM 互操作，纯托管代码即可。

## 爆炸饼图切片 – 步骤实现

下面我们将任务拆分为若干小步骤。每个部分都有明确的标题、代码片段以及对我们为何这样做的简短说明。

### 步骤 1：安装并引用 Aspose.Words

首先，将 Aspose.Words 包添加到项目中。在 Package Manager Console 中输入：

```powershell
Install-Package Aspose.Words
```

> **小技巧：** 如果您使用 Visual Studio 内置的 NuGet UI，搜索 “Aspose.Words” 并点击 Install。这样可确保获得最新的 bug 修复，并且开箱即用支持图表。

### 步骤 2：加载包含图表的 Word 文档

我们需要一个指向包含目标图表的 `.docx` 文件的 `Document` 对象。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **原因说明：** `Document` 是 Aspose.Words 所有操作的入口。提前检查图表可以避免后续在爆炸切片时出现空引用。

### 步骤 3：获取第一个图表节点

大多数示例假设只有一个图表，所以我们获取第一个。如果有多个图表，请相应调整索引。

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **注意：** 在确认图表存在后，将其强制转换为 `Chart` 是安全的。该对象让我们可以访问系列、数据点以及特定图表类型的设置。

### 步骤 4：爆炸饼图的第一块切片

现在进入重点——**如何爆炸饼图切片**。我们将设置第一数据点的 `Exploded` 属性。

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **原理说明：** `Exploded` 告诉 Word 将该切片从中心拉出，形成经典的“爆炸饼图”效果。该属性为布尔值，设为 `true` 即可实现。

### 步骤 5：调整环形图孔径大小（如果是环形图）

如果图表恰好是环形图，您可能想要 **调整环形图孔径大小**。孔径大小是相对于图表半径的百分比。

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **数值含义：** `30` 表示内部圆占总半径的 30 %，从而使外环更厚。

### 步骤 6：更改图表数据点（可选）

有时您需要 **更改图表数据点**——可能已经更新了底层数值，想让可视化同步。

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **这样做的原因：** 更改数据点的值会自动重新计算切片比例，使图表保持准确，无需在 Word 中手动编辑。

### 步骤 7：保存修改后的文档

最后，将更改写回磁盘。您可以覆盖原文件，也可以创建新文件——自行决定。

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **提示：** 如需明确指定，可使用 `SaveFormat.Docx`，但 `Save(string)` 会自动根据文件扩展名检测格式。

## 预期结果

在 Microsoft Word 中打开 `FormattedChart.docx` 时，您应看到：

- 饼图的第一块切片 **向外爆炸**。
- 如果是环形图，中心孔径现在占半径的 **30 %**。
- 所有修改过的数据点均显示您设置的新数值。

![使用 Aspose.Words 在 C# 中创建的爆炸饼图切片](exploded-pie-slice.png)

*Alt text:* **爆炸饼图切片**，显示在 Word 文档中被拉开的片段。

## 常见问题与边缘情况

**如果图表不是饼图或环形图怎么办？**  
代码在应用 `Exploded` 或 `HoleSize` 前会检查 `ChartType`。对于柱形图、折线图或面积图，这些属性根本不存在，逻辑会安全地跳过它们。

**我可以爆炸多个切片吗？**  
完全可以。遍历 `chart.PieChartData.Series[0].DataPoints`，对任意索引设置 `Exploded = true` 即可。

**我需要担心特定地区的数字格式吗？**  
Aspose.Words 将数值存为 double，独立于地区设置，因此不会出现逗号与句点的格式问题。

**嵌入页眉/页脚的图表怎么办？**  
使用 `doc.GetChildNodes(NodeType.Chart, true)` 获取所有图表，然后检查每个节点的 `ParentNode` 以确定其所在位置。相同的爆炸逻辑同样适用。

## 结论

现在您已经拥有一个完整、可复制粘贴的解决方案，使用 Aspose.Words 在 C# 中 **爆炸饼图切片**。我们覆盖了整个工作流——从加载文档、获取图表、爆炸切片、**调整环形图孔径大小**、**更改图表数据点**，直至保存文件。

欢迎自行尝试：爆炸其他切片、将孔径调至 45 %，或一次更新多个数据点。Aspose.Words API 让这些调整轻而易举，打开 Word 文件即可立即看到效果。

### 接下来可以做什么？

- **为爆炸的切片设置样式**（更改填充颜色、边框或添加数据标签）。搜索 “Aspose.Words chart formatting”。
- **批量处理自动化** 多个文档——遍历文件夹，爆炸切片并保存新版本。
- **结合 Aspose.Slides**，如果需要在 PowerPoint 演示文稿中使用相同的图表。

对图表操作还有其他疑问，或想深入了解其他图表类型？在下方留言吧，祝编码愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，构建在本教程演示的技巧之上。每篇资源均提供完整可运行的代码示例和逐步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [在 Word 中使用 Aspose.Words for .NET 插入柱形图](/words/english/net/working-with-charts/insert-column-chart/)
- [在 Word 中使用 Aspose.Words for .NET 插入简易柱形图](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [在 Word 文档中插入面积图 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}