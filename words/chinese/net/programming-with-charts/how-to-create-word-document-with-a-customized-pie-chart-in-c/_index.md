---
category: general
date: 2026-10-07
description: 学习如何使用 Aspose.Words 在 C# 中创建 Word 文档并插入饼图。本指南还展示了如何生成带有自定义图表标签的 Word
  文件。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: zh
lastmod: 2026-10-07
og_description: 在 C# 中创建 Word 文档并插入饼图。请按照本分步指南生成带有完全自定义图表标签的 Word 文件。
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: 使用 C# 创建带自定义饼图的 Word 文档
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: 如何在 C# 中创建带有自定义饼图的 Word 文档
url: /zh/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 C# 中创建带有自定义饼图的 Word 文档

如果您需要 **以编程方式创建 Word 文档**，本教程将向您展示如何使用 Aspose.Words for .NET **插入饼图** 并自定义其数据标签。您还将学习如何 **生成包含完整样式图表的 Word 文件**，涵盖从项目设置到保存最终文档的全部过程。

本指南逐步演示了添加图表、调整标签位置、启用引导线以及最终将结果保存为 `.docx` 文件所需的每一步。除了 Aspose.Words 库外，无需任何外部工具，完整源码已提供，您可以直接复制、粘贴并运行。

## 前置条件

在开始之前，请确保您已具备：

* 已安装 .NET 6.0 SDK 或更高版本  
* 有效的 Aspose.Words for .NET 许可证（或免费评估密钥）  
* 如 Visual Studio 2022 或 Visual Studio Code 等 IDE  

您还需要向项目中添加以下 NuGet 包：

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

这些包提供了示例中使用的 `Document`、`DocumentBuilder` 以及图表相关类。

## 创建 Word 文档并添加图表

第一步是 **创建 Word 文档** 并获取一个 `DocumentBuilder`，该对象允许您插入内容。构建器的工作方式类似于位于文档内部的光标。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` 对象代表整个 Word 文件，而 `DocumentBuilder` 提供了诸如 `InsertChart` 的方法，可直接将对象放入文档流中。

## 向文档插入饼图

构建器准备就绪后，您可以 **插入饼图** 并指定特定尺寸。图表会在构建器当前所在位置添加。

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` 返回一个 `Chart` 对象，您可以进一步操作。示例数据创建了四个切片，代表季度销售额。

## 自定义饼图数据标签

为了让图表更易读，通常需要 **自定义饼图** 标签——将它们放置在切片外部并显示引导线。这时 `ChartDataLabelCollection` 就派上用场了。

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

将 `Position` 设置为 `OutsideEnd` 可将每个标签移动到切片边缘之外，而 `ShowLeaderLines` 会绘制一条连接标签与切片的线。可选的 `ShowValue` 和 `ShowPercentage` 标志则为读者提供原始数值和相对百分比。

**小贴士：** 如需设置标签字体，可使用 `dataLabels.Font` 来指定大小、颜色和样式，从而确保图表符合企业品牌形象。

## 保存并生成 Word 文件

在图表全部配置完成后，您可以通过将 `Document` 实例保存到磁盘来 **生成 Word 文件**。请选择 `.docx` 格式，以获得对现代 Word 版本的最大兼容性。

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

打开 `CustomPieChart.docx` 时，您将看到一个包含四个切片的饼图，每个标签都位于切片外部，并通过引导线连接，同时显示数值和百分比。

![Screenshot of a Word document that contains a customized pie chart created with C#](image-placeholder.png)

*该图片展示了 **创建 Word 文档** 教程的最终效果。*

## 常见变体和边缘情况

| 场景 | 代码适配方式 |
|----------|----------------------|
| **多系列** | 向 `pieChart.Series` 添加额外的 `ChartSeries` 对象。每个系列可以拥有独立的 `DataLabels` 集合以实现单独样式。 |
| **不同图表尺寸** | 在 `InsertChart(width, height)` 中更改宽度和高度参数。数值单位为点（1 pt ≈ 1/72 in）。 |
| **图表标题** | 使用 `pieChart.Title.Text = "Quarterly Sales"` 添加描述性标题。 |
| **导出为 PDF** | 在构建完图表后调用 `document.Save("Report.pdf", SaveFormat.Pdf);`。 |
| **许可证处理** | 将许可证文件 (`Aspose.Words.lic`) 放置在应用程序文件夹中，并在创建文档前使用 `new License().SetLicense("Aspose.Words.lic");` 加载。 |

这些变体帮助您在各种实际场景中回答 **如何添加饼图** 的问题，从简单报告到复杂仪表盘皆可应对。

## 结论

现在，您已经掌握了使用 Aspose.Words for .NET **创建 Word 文档**、**插入饼图** 并 **自定义饼图** 标签的完整流程。完整示例展示了一个清晰的工作流：初始化文档、添加图表、调整数据标签位置、启用引导线，最后 **生成 Word 文件**，可与任何人共享。

尝试通过实验不同的图表类型（`ChartType.Column`、`ChartType.Line`）或应用自定义配色方案来扩展本教程，以匹配您的品牌。如果遇到问题，请查阅 Aspose.Words 文档或探索诸如 “how to add pie chart” 的相关主题，了解多系列和动态数据源的实现方式。

祝编码愉快，欢迎在评论区分享您的成果或提出后续问题！

## 接下来您应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步提升。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}