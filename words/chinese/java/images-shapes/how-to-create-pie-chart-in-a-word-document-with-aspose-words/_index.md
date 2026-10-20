---
category: general
date: 2026-10-20
description: 使用 Aspose.Words 在 Word 文档中创建饼图 – 步骤指南，展示如何设置颜色、突出切片以及保存 Word 文档。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: zh
lastmod: 2026-10-20
og_description: 使用 Aspose.Words 在 Word 文档中创建饼图。学习如何设置颜色、突出切片，并在一个可运行的示例中保存 Word 文档。
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: 在 Word 文档中创建饼图 – 完整 C# 指南
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: 如何使用 Aspose.Words 在 Word 文档中创建饼图
url: /zh/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中使用 Aspose.Words 创建饼图

如果您需要在 Word 文件中 **创建饼图**，本指南将准确展示如何操作。您将看到如何设置自定义颜色、为突出显示而 **炸开切片**，以及最终 **保存 Word 文档** 并嵌入图表。

以编程方式生成图表可以省去手动打开 Word、插入图表以及微调外观的步骤。完成本教程后，您将拥有一个完整的、可运行的 C# 控制台应用程序，能够创建饼图、定制它并将结果写入磁盘。

## 前置条件

在开始之前，请确保您拥有：

* .NET 6.0 SDK 或更高版本已安装  
* 有效的 Aspose.Words for .NET 许可证（或免费评估密钥）  
* 如 Visual Studio 2022 或 VS Code 等 IDE  

除 `Aspose.Words` 外，无需其他 NuGet 包。

## 如何在 Word 文档中创建饼图

第一步是实例化一个 `Document` 和一个 `DocumentBuilder`。Builder 为您提供对高级 Word 功能的访问，包括图表插入。

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

此时文档已经包含一个基本的饼图。接下来的章节将解释 **如何炸开切片**、**如何设置颜色**，以及 **如何保存 Word 文档**。

## 如何为突出显示炸开切片

炸开切片会将其从饼图的其余部分分离出来，吸引读者的注意。Aspose.Words API 允许您以点为单位指定炸开距离。

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

为什么要炸开切片？在突出显示特定类别的报告中——例如 “畅销产品”——视觉上的分离可以让数据点瞬间被识别。

## 如何为图表切片设置颜色

自定义颜色可以提升品牌一致性和可读性。您可以为特定数据点分配任意 `System.Drawing.Color`。

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

您并不局限于预定义颜色；也可以使用 `Color.FromArgb` 创建精确色调的值。

## 如何保存带有图表的 Word 文档

当图表达到您想要的效果后，持久化文件非常简单。`Document.Save` 方法会按照您指定的格式写入文档——这里我们使用默认的 `.docx`。

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

运行程序后会生成 `PieChart.docx`。在 Microsoft Word 中打开该文件，可看到一个饼图，其中第一块已炸开并填充为红色，完全符合代码的指定。

### 预期结果

* 在 `C:\Temp` 中生成一个名为 **PieChart.docx** 的 Word 文件。  
* 文档包含一个单一的饼图，尺寸为 400 × 300 点。  
* 切片 0 偏移 20 点并填充为红色，其他切片保持默认颜色。  

您可以通过在 Word 中选中图表并检查切片属性来验证炸开效果和颜色设置。

## 专业技巧与常见陷阱

* **专业技巧：** 如果需要更改图表标题或图例，请在保存前使用 `pieChart.Title.Text` 和 `pieChart.Legend` 属性。  
* **注意：** 忘记清除默认数据点会导致额外的、无用的切片。始终在添加自定义数据前调用 `Series[0].DataPoints.Clear()`。  
* **性能技巧：** 对于大型文档，重复使用单个 `DocumentBuilder` 实例而不是创建多个构建器，可降低内存开销。

## 如何使用 Aspose.Words 创建图表（附加说明）

`InsertChart` 方法支持除饼图之外的多种图表类型，如柱形图、折线图和面积图。要切换到其他类型，只需将 `ChartType.Pie` 替换为所需的枚举值，例如 `ChartType.Column`。其余的定制步骤（炸开切片、设置颜色）遵循相同的模式，尽管并非所有图表类型都公开 “炸开” 属性。

## 如何在其他图表类型中炸开切片

仅饼图类型公开 `SetExplosion` 方法。如果在条形图上调用它，API 会抛出 `ArgumentException`。在这种情况下，考虑使用数据标签或标注来突出显示特定的条形。

## 如何为整个系列而非单个切片设置颜色

如果希望系列中的每个切片共享相同的颜色，可遍历数据点：

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

当需要在多个图表之间保持统一配色方案时，这种做法非常方便。

## 如何以其他格式保存 Word 文档

Aspose.Words 可以导出为 PDF、HTML 以及许多其他格式。只需在 `Save` 中更改文件扩展名，并可选地传入 `SaveOptions` 对象：

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

图表渲染引擎会自动将图表转换为目标格式，保留颜色和炸开设置。

## 结论

您现在已经掌握了在 Word 文档中 **创建饼图**、通过 **炸开切片** 与 **设置颜色** 定制外观，并最终 **保存 Word 文档** 并嵌入图表的完整流程。此端到端示例为您自动化报告生成、仪表板构建或任何需要以编程方式插入可视化数据的场景奠定了坚实基础。

### 后续步骤

* 探索其他图表类型（`ChartType.Column`、`ChartType.Line`），以扩展您的报告工具箱。  
* 在单个文档中组合多个图表，构建综合仪表板。  
* 尝试使用 `ChartDataLabel` 在切片上直接显示百分比或数值。  

随意将代码适配到您自己的数据源——无论是从数据库、API 还是 CSV 文件获取值，相同的 Aspose.Words 工作流都适用。祝您绘图愉快！

## 接下来应该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在已有技巧的基础上进一步深入。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [在 C# 中使用 Aspose.Words 炸开饼图切片 – 完整指南](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [使用 Aspose.Words for .NET 在 Word 文档中插入自定义柱状图](/words/english/net/programming-with-charts/insert-custom-chart/)
- [使用 Aspose.Words for .NET 更新 Word 文档中的图表系列数据](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}