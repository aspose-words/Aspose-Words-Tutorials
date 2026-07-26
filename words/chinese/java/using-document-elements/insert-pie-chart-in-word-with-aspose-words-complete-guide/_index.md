---
category: general
date: 2026-07-26
description: 使用 Aspose.Words 将饼图插入 Word 文档。只需几步，即可学习如何添加图表、突出切片并显示百分比。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: zh
lastmod: 2026-07-26
og_description: 使用 Aspose.Words 将饼图插入 Word 文档。请按照本指南快速学习如何添加图表、突出切片以及显示百分比。
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: 在 Word 中插入饼图 – Aspose.Words 分步教程
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: 使用 Aspose.Words 在 Word 中插入饼图 – 完整指南
url: /zh/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 Aspose.Words 插入饼图 – 完整指南

是否曾经需要在 Word 报告中 **插入饼图**，但不知从何入手？你并不孤单。在许多业务应用中，饼图的视觉冲击力能让数据瞬间易于理解，而 Aspose.Words 只需几行代码即可实现这一点。

在本教程中，我们将逐步演示 **向 Word 添加图表** 的具体步骤，包括为突出显示而“炸开”切片，以及在数据标签上显示百分比。完成后，你将拥有一个可直接运行的示例，能够放入任何 .NET 项目中使用。

---

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Core 和 .NET Framework）
- 已安装 Aspose.Words for .NET NuGet 包  
  ```bash
  dotnet add package Aspose.Words
  ```
- 对 C# 语法有基本了解——无需高级技巧
- 任意 IDE（Visual Studio、Rider 或 VS Code）

就这些。让我们动手实践吧。

---

## 在 Word 文档中插入饼图

我们首先需要一个全新的 `Document` 对象和一个 `DocumentBuilder`。可以把 builder 想象成直接在 Word 画布上书写的笔。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **为什么这很重要：** `Document` 代表整个 .docx 文件，而 `DocumentBuilder` 为我们提供了便捷的 API 来插入图表、表格和文本等元素。这是每一次 **如何添加图表** 操作的基础。

---

## 如何向 Word 添加图表

现在我们已有 builder，便可以实际 **插入饼图**。`insertChart` 方法接受图表类型以及以点为单位的尺寸（1 点 = 1/72 英寸）。

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **提示：** 如果需要不同的尺寸，只需调整宽度和高度的数值。图表会自动缩放以适应页面边距。

---

## 如何炸开切片以突出显示

一种常见的视觉调整是“炸开”某个切片，使其从圆形中弹出，从而吸引读者的目光到最重要的部分。

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **为什么要炸开切片？** 当你想突出显示特定类别——例如财务报告中的 “Q1 收入”——炸开切片可以让它立即显眼，无需额外文字说明。

---

## 如何在数据标签上显示百分比

大多数饼图在每个切片显示其百分比时更具可读性。Aspose.Words 只需一个属性即可开启此功能。

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **快速提示：** `ShowPercentage` 标志适用于系列中的所有点，无需对每个切片单独设置。

---

## 保存包含图表的文档

最后，我们将文档写入磁盘。选择任意文件夹即可，只需确保路径已存在。

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

当你在 Microsoft Word 中打开 `PieChart.docx` 时，你会看到一个渲染完美的饼图，第一块已炸开并显示百分比——正是精致商务报告应有的效果。

---

## 完整可运行示例

下面是完整的、可直接复制粘贴的程序。将其作为控制台应用运行并验证输出文件。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**预期结果：** 打开生成的 `PieChart.docx`。你会看到一个标题为 “Sales Q1” 的三块饼图，第一块已被拉出，每块切片分别标注为 “30 %”、 “45 %” 和 “25 %”。视觉效果与我们提供的数据相匹配。

---

## 常见问题与边缘情况

- **如果需要多个系列怎么办？**  
  只需向 `chart.Series` 添加额外的 `ChartSeries` 对象。每个系列可以拥有自己的数据集、颜色和炸开设置。

- **我可以更改图表颜色吗？**  
  可以。每个 `ChartPoint` 都有 `Format.Fill.ForeColor` 属性，可设置为任意 `System.Drawing.Color`。

- **其他图表类型呢？**  
  `ChartType` 枚举包含柱形、折线、环形等多种类型。将 `ChartType.Pie` 替换为你需要的图表类型即可。

- **插入后图表在 Word 中可编辑吗？**  
  完全可以。Word 将图表视为原生 Office 图表，用户可以双击它打开内置的图表编辑器。

---

## 结论

现在，你已经完全掌握了使用 Aspose.Words **插入饼图** 到 Word 文档的方式，了解了 **如何向 Word 添加图表**、**如何炸开切片** 以及 **如何在数据标签上显示百分比**。上面的完整示例已可直接运行，你可以在此基础上添加自定义数据、样式或额外的系列。

准备好下一步了吗？尝试将饼图替换为环形图，或自动生成一批包含不同数据集的报告。如果你对其他可视化感兴趣，请查看我们关于 **如何添加图表** 的柱形图和折线图指南，或深入浏览 **向 Word 添加图表** 的 API 参考文档，以获得更深度的自定义。

祝编码愉快，愿你的文档始终如完美切开的饼一样清晰！

## 接下来应该学习什么？

以下教程涵盖与本指南紧密相关的主题，基于本教程展示的技术进行扩展。每个资源都包含完整的可运行代码示例和逐步说明，帮助你掌握更多 API 功能，并在自己的项目中探索替代实现方式。

- [在 Word 中使用 Aspose.Words for .NET 插入柱形图](/words/english/net/working-with-charts/insert-column-chart/)
- [在 Word 文档中插入面积图 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [使用 Aspose.Words for .NET 创建 Word 散点图](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}