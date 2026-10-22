---
category: general
date: 2026-09-21
description: 学习如何使用 Aspose.Words 创建饼图并将图表插入 Word，向饼图添加数据标签，并在饼图上显示百分比，只需几个步骤。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: zh
lastmod: 2026-09-21
og_description: 使用 Aspose.Words 在 Word 中创建饼图，将图表插入 Word，为饼图添加数据标签，并在饼图上显示百分比——全部提供清晰的代码示例。
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: 使用 Aspose.Words 在 Word 中创建饼图 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: 如何使用 Aspose.Words 在 Word 文档中创建饼图
url: /zh/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 文档中使用 Aspose.Words 创建饼图

如果您需要**以编程方式创建饼图**，Aspose.Words 让这件事变得简单直观。在本教程中，您将看到如何**将图表插入 Word**、配置系列、**向饼图添加数据标签**，以及最终**在饼图上显示百分比**，使可视化能够传达精确的数值。完成后，您将拥有一个完整的、可直接运行的示例，能够放入任何 .NET 项目中。

本指南涵盖您需要了解的全部内容：必需的 NuGet 包、完整的 C# 源码、每个 API 调用意义的解释，以及自定义图表的技巧。无需查阅外部文档——只需复制、运行并根据需要调整。

## 前置条件

在开始之前，请确保您已具备：

* 已安装 .NET 6.0 SDK 或更高版本。  
* Visual Studio 2022（或任何支持 .NET 的 IDE）。  
* Aspose.Words for .NET 许可证（免费试用版可用于测试）。  
* 对 C# 和 Word 文档结构的基本了解。

如果这些条件都已满足，您可以直接进入代码部分。

## 第 1 步：创建项目并导入 Aspose.Words

新建一个控制台项目并添加 Aspose.Words NuGet 包：

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

该包包含 `Aspose.Words.Drawing.Charts` 命名空间，其中的 `Chart` 和 `ChartSeries` 类将在后文中使用。

> **专业提示：** 将许可证文件（`Aspose.Words.lic`）放在项目根目录，并在启动时加载，以避免出现评估水印。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## 第 2 步：创建空白文档并实例化 DocumentBuilder

`Document` 表示 Word 文件，而 `DocumentBuilder` 提供了一个流式 API 用于插入内容。

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么重要：** `DocumentBuilder` 维护当前的插入点，确保图表正好出现在文档流中的预期位置。

## 第 3 步：在 Word 文档中插入饼图

现在我们**将图表插入 Word**。`InsertChart` 方法接受图表类型、宽度和高度（单位为点）。

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

此时图表包含一个默认的数据系列，占位值为 (25, 25, 25, 25)。您可以稍后根据需要替换这些值。

## 第 4 步：访问第一个系列并自定义数据标签

饼图通常只有一个系列。要**向饼图添加数据标签**，我们需要获取该系列并启用百分比显示。

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**为何要设置 `ShowPercentage`：** 该标志指示 Aspose.Words 计算每个扇区的占比并以百分比形式呈现。`Position` 属性确保标签不会与扇区重叠，从而提升可读性——尤其在扇区较小时尤为重要。

## 第 5 步：（可选）替换占位数据

如果您想使用特定数值，只需替换默认的点：

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

显示的百分比会自动根据新数值进行调整。

## 第 6 步：保存文档

最后，将文档写入磁盘。文件扩展名决定了输出格式；`.docx` 会生成现代 Word 文件。

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

运行程序后，会在输出文件夹生成名为 **PieChart.docx** 的文件。使用 Microsoft Word 打开后，您将看到每个扇区都标有百分比，且标签位于扇区外侧。

### 预期输出

打开生成的文档时，您应看到：

* 一个大小为 400 × 300 pt 的饼图。  
* 四个扇区（或您添加的任意数量的点）。  
* 如 “40 %”、 “30 %” 等百分比标签，显示在每个扇区外侧。

如果标签出现在扇区内部，请再次确认已正确设置 `ChartDataLabelPosition.OutsideEnd`。

## 第 7 步：常见变体与边界情况

### 为图表添加标题

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### 更改扇区颜色

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### 处理空系列

如果数据源可能为空，请防止 `IndexOutOfRangeException`：

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### 导出为 PDF 而非 Word

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

图表渲染逻辑保持不变，Aspose.Words 会自动将 Word 布局转换为 PDF。

## 完整源码列表

下面是完整的、可直接运行的程序代码。将其复制到 `Program.cs` 并执行 `dotnet run`。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## 结论

现在，您已经掌握了如何使用 Aspose.Words 在 Word 文件中**创建饼图**、**将图表插入 Word**、**向饼图添加数据标签**以及**在饼图上显示百分比**。示例展示了从项目设置到最终文档的完整工作流，您可以将其用于仪表盘、报告或自动化发票生成等场景。

接下来，您可以进一步探索以下主题，例如**在图例中显示百分比**、自定义图表颜色，或将 Word 文档转换为 PDF 以便分发。尝试使用相同的 `InsertChart` 方法创建其他图表类型（柱形图、折线图），以扩展您的自动化能力。

祝您绘图愉快！


## 接下来该学习什么？

以下教程涵盖与本指南技术紧密相关的主题，帮助您在实际项目中进一步运用这些技巧。每篇资源都提供完整的可运行代码示例和逐步解释，助您掌握更多 API 功能并探索替代实现方案。

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}