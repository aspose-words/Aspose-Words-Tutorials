---
category: general
date: 2026-08-07
description: 快速在 C# 中创建饼图。了解如何插入饼图、添加数据标签、显示百分比图表以及自定义图表数据标签。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: zh
lastmod: 2026-08-07
og_description: 使用 Aspose.Words 在 C# 中创建饼图 Word 文档。本教程展示了如何插入饼图、添加数据标签，并在自定义图表数据标签的同时显示百分比。
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: 在 C# 中创建 Word 饼图 – 完整教程
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: 在 C# 中创建饼图 Word – 分步指南
url: /zh/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中创建饼图 Word 文档 – 步骤指南

如果您需要在 C# 中 **create pie chart word** 文档，本指南提供完整的、可直接运行的解决方案。您将看到如何 **insert pie chart**、**add data labels pie**，以及 **show percentage chart**，同时 **customize chart data labels** 以获得精致的外观。

以编程方式生成图表可以避免手动编辑，尤其是在报告或仪表盘需要自动生成时。下面的章节将教您如何使用 Aspose.Words for .NET 将完整标注的饼图嵌入 Word 文件。

## 前置条件和设置

在开始之前，请确保您拥有：

* 已安装 .NET 6.0 SDK 或更高版本。  
* 有效的 Aspose.Words for .NET 许可证（或临时评估密钥）。  
* Visual Studio 2022（或任何支持 C# 的 IDE）。  

将 Aspose.Words NuGet 包添加到项目中：

```bash
dotnet add package Aspose.Words
```

> **小贴士:** 如果您计划生成大量图表，请启用 **Free‑Form Drawing** 模式 (`DocumentBuilder.UseFreeFormDrawing = true`) 以获得更好的性能。

## 使用 Aspose.Words 创建饼图 Word 文档

第一步是创建一个空白的 Word 文档并实例化 `DocumentBuilder`。该对象负责后续的所有插入操作。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

**为什么这很重要**：`Document` 代表整个 `.docx` 文件，而 `DocumentBuilder` 提供流式 API 用于添加段落、表格和图表。使用全新文档可以确保没有隐藏的格式干扰图表布局。

## 将饼图插入文档

现在我们放置一个指定尺寸的饼图。`InsertChart` 方法返回一个 `Chart` 对象，后续可以进一步配置。

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

**为什么这很重要**：`ChartType.Pie` 标志告诉 Aspose.Words 生成圆形图表。宽度 (`400`) 和高度 (`300`) 使用点（points）表示，便于精确控制视觉占位。

## 为图表填充数据

饼图至少需要一组数值系列。这里我们添加三个类别：“Apples”、 “Bananas” 和 “Cherries”。

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

**为什么这很重要**：每次调用 `AddCategory` 都会创建一个切片。数值决定切片大小，标签则成为打开数据标签时显示的类别名称。

## 添加数据标签并显示百分比图表

为了让图表信息更完整，我们启用数据标签，将其放置在切片外部，并让 Aspose.Words 同时显示类别名称和百分比。

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

**为什么这很重要**：将 `Position` 设置为 `OutsideEnd` 可提升可读性，尤其是切片较小时。启用 `ShowCategoryName` 和 `ShowPercentage` 满足 **show percentage chart** 的需求，也实现了 **add data labels pie** 的目标。

## 进一步自定义图表数据标签（可选）

您可能想更改字体、添加引导线或隐藏图例。下面的代码片段演示了常见的自定义方式：

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

**为什么这很重要**：自定义标签外观可确保图表符合文档的风格指南。当数据标签已经传达全部信息时，移除图例可以减少视觉杂乱。

## 保存带有自定义图表的文档

最后，将文档写入磁盘。请选择您拥有写入权限的路径。

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

打开 `ChartWithCustomLabels.docx`（Microsoft Word）时，您将看到一个饼图：每个切片都标有类别名称和百分比，标签位于切片外部，并使用自定义字体样式。

### 预期输出

| 切片   | 数值 | 百分比 | Word 中显示的标签 |
|--------|------|--------|-------------------|
| 苹果   | 40   | 40 %   | 苹果 – 40 %       |
| 香蕉   | 35   | 35 %   | 香蕉 – 35 %       |
| 樱桃   | 25   | 25 %   | 樱桃 – 25 %       |

图表应类似下图所示：

![显示每个切片外部百分比标签的饼图 Word 文档](pie-chart-word.png "创建饼图 Word 示例")

*图片 alt 文本包含主要关键词，以提升 SEO 效果。*

## 处理多系列及边缘情况

基本示例使用单一系列，这在饼图中很常见。如果需要展示多系列（例如比较两年数据），必须：

1. 为每个附加系列调用 `chart.Series.Add()`。  
2. 确保每个系列使用相同的类别；否则 Aspose.Words 会抛出 `ArgumentException`。  
3. 可选地设置 `labels.ShowSeriesName = true` 以区分切片。

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

当存在多系列时，图表会自动呈现为 **clustered pie**（亦称 “pie of pies”）。请检查输出，确保标签仍然清晰可读。

## 常见陷阱及规避方法

| 问题                     | 原因                         | 解决方案                                                                 |
|--------------------------|------------------------------|--------------------------------------------------------------------------|
| 标签重叠切片             | 图表区域太小或类别太多       | 增大图表尺寸 (`InsertChart(width, height)`) 或将 `Position` 改为 `InsideEnd`。 |
| 百分比总和不等于 100 %   | 数据四舍五入误差             | 使用 `labels.ShowPercentage = true`（Aspose.Words 会自动规范化）。        |
| 图表在 Word 中显示为空   | 缺少许可证或评估超时         | 在创建文档之前确保已加载有效的 Aspose.Words 许可证。                     |
| 字体颜色与 Word 主题不一致 | 代码中设置了自定义字体       | 移除自定义字体设置或匹配 Word 的主题颜色 (`System.Drawing.Color.Black`)。 |

## 完整源代码（可运行）

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

运行程序后会生成 `ChartWithCustomLabels.docx`，其中包含一个满足本教程所有要求的 **create pie chart word** 示例。

## 结论

现在，您已经掌握了使用 Aspose.Words 在 C# 中 **create pie chart word** 文档的全部步骤。指南涵盖了插入饼图、**add data labels pie**、**show percentage chart**，以及**customize chart data labels**，帮助您生成专业、数据驱动的 Word 文件。

接下来，您可以进一步探索以下相关主题，例如 **insert pie chart** 到现有段落、生成 **bar** 或 **line** 图表，或自动批量创建包含不同数据集的报告。尝试不同的标签位置、字体样式和多系列配置，以满足特定的报表需求。

祝绘图愉快！

## 接下来应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您进一步掌握 API 功能并在项目中尝试替代实现方式。

- [自定义图表数据标签](/words/english/net/programming-with-charts/chart-data-label/)
- [设置图表数据标签的默认选项](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [在 Word 文档中插入柱形图](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}