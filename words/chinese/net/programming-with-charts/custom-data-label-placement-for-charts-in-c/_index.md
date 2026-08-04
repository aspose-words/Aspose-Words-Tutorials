---
category: general
date: 2026-08-04
description: C# 中的自定义数据标签位置可让您在图表切片上居中标签。请按照使用 Aspose.Words 图表 API 的分步指南操作。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: zh
lastmod: 2026-08-04
og_description: 在 C# 中的自定义图表数据标签放置演示如何将 Word 图表每个切片上的所有数据标签居中。使用 Aspose.Words 掌握图表数据标签定位。
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: C# 图表自定义数据标签放置 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: C# 图表的自定义数据标签放置
url: /zh/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# C# 中的自定义数据标签位置

**Custom Data‑Label Placement for Charts** 让您能够精确控制 Word 文档中图表上每个标签的显示位置。在本教程中，您将学习如何使用 C# 和 Aspose.Words 图表 API 将每个切片的所有数据标签居中。

您将获得一个完整的可运行示例，加载 `.docx` 文件，访问第一个图表形状，将每个标签的 `Position` 更改为 `Center`，并保存更新后的文档。无需外部引用——只需 Aspose.Words for .NET 库和基本的 C# 开发环境。

**您将学习**

* 如何加载包含图表的 Word 文档。  
* 如何使用 Aspose.Words 图表 API 定位图表形状。  
* 如何对图表中的每个系列应用 **chart data label positioning**。  
* 如何保存文档，使居中的标签在 Word 中显示。  

**先决条件**

* 已安装 .NET 6.0（或更高）。  
* Visual Studio 2022（或任何 C# IDE）。  
* 对 `Aspose.Words` NuGet 包的引用。  
* 一个包含至少一个图表的 Word 文件（`Chart.docx`）。

---

## 自定义数据标签位置 – 步骤 1：加载文档

第一步是打开包含图表的 Word 文件。`Document` 是使用 Aspose.Words 进行任何操作的入口点。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*为什么此步骤重要*：如果不加载文档，就无法访问图表对象。此验证确保在文件缺少图表时返回明确的错误，防止后续出现空引用。

---

## 使用 Aspose.Words 图表 API 访问图表形状

Aspose.Words 将图表视为嵌套在 `Shape` 中的 `Chart` 对象。您可以通过将相应的子节点强制转换来获取它。

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*为什么此步骤重要*：直接访问 `Chart` 可让您完全控制系列、数据点和标签属性。如果该形状不是图表，代码会提前中止并显示信息性消息。

---

## 在 C# 中设置图表数据标签位置

现在遍历每个系列和每个数据标签，将 `Position` 设置为 `Center`。这就是 **Custom Data‑Label Placement for Charts** 的核心。

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**技巧**：如果需要不同的放置方式（例如柱形图的 `InsideEnd`），请相应地更改枚举值。`ChartDataLabelPosition` 枚举涵盖了 Word 支持的所有标准位置。

*为什么此步骤重要*：更改 `label.Position` 会更新底层 OOXML 表示，因此在 Microsoft Word 中打开文档时，标签会居中显示。

---

## 保存带有更新标签的 Word 文档

修改图表后，将更改持久化回文件。您可以覆盖原文件或创建新副本。

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*为什么此步骤重要*：保存会将更新后的 OOXML 写入磁盘。用 Word 打开 `ChartLabelsCentered.docx` 将显示每个切片的标签居中，从而确认 **Custom Data‑Label Placement for Charts** 已成功。

---

## 边缘情况和变体

| 情况 | 处理方法 |
|-----------|---------------|
| **同一文档中的多个图表** | 对 `doc.GetChildNodes(NodeType.Shape, true)` 进行循环，并检查每个 `shape.HasChart`。 |
| **不同的图表类型**（饼图、环形图、条形图） | 对于饼图类型，`ChartDataLabelPosition.Center` 同样适用。对于条形/柱形图，您可能更倾向于使用 `InsideEnd` 或 `OutsideEnd`。 |
| **标签文本需要格式化** | 访问 `label.TextProperties` 以设置字体大小、颜色或加粗。 |
| **在 .NET Core 上运行** | 确保引用 Aspose.Words 的 .NET Standard 版本；API 完全相同。 |

---

## 完整工作示例

下面是完整的程序，您可以复制粘贴到控制台应用程序中。它包含所有必要的 `using` 指令和错误处理。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**预期结果**：在 Microsoft Word 中打开 `ChartLabelsCentered.docx`。图表的每个切片现在都在切片中心直接显示其数据标签，呈现更清晰的视觉效果。

---

## 结论

现在，您已经拥有完整的 C# **Custom Data‑Label Placement for Charts** 解决方案。通过加载文档、使用 Aspose.Words 图表 API 访问图表、为每个标签设置 `ChartDataLabelPosition.Center` 并保存文件，您可以自动化任何基于 Word 的图表的标签位置。

接下来，探索其他 **chart data label positioning** 选项，如 `InsideEnd` 或 `OutsideEnd`，或尝试 **C# chart manipulation** 来更改颜色、添加图例或从头生成图表。这些扩展直接基于本教程的技术，能够拓宽您在 Word 文档图表自动化方面的技能。祝编码愉快！

## 接下来您应该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步说明，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [自定义图表数据标签](/words/english/net/programming-with-charts/chart-data-label/)
- [格式化图表中数据标签的数字](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [图表数据标签](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}