---
category: general
date: 2026-08-10
description: 使用 Aspose.Words 创建饼图 Word 文档。学习如何插入图表、定制饼图颜色以及在 C# 中更改饼块颜色。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: zh
lastmod: 2026-08-10
og_description: 使用 Aspose.Words 创建饼图 Word 文档。本指南解释了如何在 C# 应用程序中插入图表、定制饼图颜色以及更改饼块颜色。
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: 创建饼图 Word 文档 – Aspose.Words 指南
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: 使用 Aspose.Words 创建饼图 Word 文档
url: /zh/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words 创建饼图 Word 文档

如果您需要以编程方式 **创建饼图 Word 文档**，本教程将一步步演示如何实现。我们将通过 Aspose.Words for .NET 讲解插入图表、**自定义饼图颜色**以及**更改饼块颜色**的完整过程。

您将看到一个完整、可运行的示例，复制到 Visual Studio 后直接运行，即可打开生成的 *.docx* 文件，验证已样式化的饼图。无需查阅外部文档——本指南已囊括所有必要信息。

## 前置条件

开始之前，请确保您具备：

* 已安装 .NET 6.0 SDK 或更高版本  
* 有效的 Aspose.Words for .NET 许可证（或临时评估密钥）  
* Visual Studio 2022（或任意 C# IDE）  

代码仅使用 `Aspose.Words` 和 `Aspose.Words.Drawing.Charts` 命名空间，无需除 Aspose.Words 库之外的其他 NuGet 包。

## 创建饼图 Word 文档 – 完整示例

下面的 C# 程序会创建一个新的 Word 文档，插入饼图，设置前两个切片的样式，并保存文件。每一步都作了详细说明。

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### 各步骤说明

| 步骤 | 功能说明 | 重要原因 |
|------|----------|----------|
| **1** | 创建新的 `Document` 和 `DocumentBuilder`。 | `DocumentBuilder` 提供流式方法，可将图表等内容插入 Word 文件。 |
| **2** | 使用 `ChartType.Pie` 并指定固定尺寸调用 `InsertChart`。 | `InsertChart` 是 **插入图表** 的方法；指定宽高可确保图表在页面上布局合理。 |
| **3** | 添加包含三个类别和数值的数据系列。 | 没有数据的饼图是不可见的，填充数据后才能演示样式设置步骤。 |
| **4** | 为第一个点设置 `Explosion`。 | 将切片突出显示，可用于强调关键数据。 |
| **5** | 为前两个点设置 `ForeColor`。 | 这正是 **自定义饼图颜色** 的核心；您可以使用任意 `System.Drawing.Color`。 |
| **6** | 演示如何为其他切片 **更改饼块颜色**。 | 表明样式化不仅限于前两个切片，所有切片均可单独着色。 |
| **7** | 将文档保存为 `PieChartStyled.docx`。 | 最终输出可在 Microsoft Word、Google Docs 或任何兼容查看器中打开。 |

#### 预期输出

打开 `PieChartStyled.docx`，您会看到单页上呈现一个 400 × 300 pt 的饼图：

* 切片 1（橙色）向外突出。  
* 切片 2（绿色）紧邻突出切片。  
* 切片 3（钢蓝色）填充剩余部分。

图表依据数据值（30、45、25）以及您定义的自定义颜色进行绘制。

## 如何样式化饼图 – 其他技巧

* **使用主题颜色** – 与其硬编码 `Color.Orange`，不如从文档主题中获取颜色：  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **添加数据标签** – 若需在图表上显示百分比：  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **动态调整大小** – 根据页面边距计算图表尺寸：  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

这些变体展示了 **如何样式化饼图** 超出基础示例的灵活性。

## 常见问题解答

**问：这在 .NET Core 上能工作吗？**  
答：可以。Aspose.Words for .NET 与 .NET Core、.NET 5、.NET 6 以及更高版本兼容，只需引用同一 NuGet 包。

**问：如果我需要的是环形图而不是饼图怎么办？**  
答：将 `ChartType.Pie` 替换为 `ChartType.Doughnut` 即可。相同的样式 API（`Explosion`、`ForeColor`）仍然适用。

**问：能否将图表插入到已有的文档中？**  
答：使用 `new Document("Existing.docx")` 打开已有文件，为该文档创建 `DocumentBuilder`，然后在所需光标位置调用 `InsertChart`。

**问：如何处理大型数据集？**  
答：饼图适合类别数量有限的场景（通常 < 10）。若类别较多，建议改用条形图或柱形图。

## 完整源代码回顾

以下是一整块可直接复制粘贴的完整程序：

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

运行此代码即可生成前文描述的已样式化饼图 Word 文档。

## 结论

现在，您已经掌握了使用 Aspose.Words **创建饼图 Word** 文档、**自定义饼图颜色**以及**更改饼块颜色**的编程方法。指南涵盖了插入图表、填充数据、突出切片、应用自定义颜色以及保存结果的全过程。

接下来，您可以进一步探索 **如何插入其他类型图表**、添加图例，或生成包含多个图表的多页报告。尝试不同的配色方案和数据集，以满足您的报表需求。

祝编码愉快！

## 接下来你应该学习什么？

以下教程与本指南紧密相关，帮助您在已有技术基础上进一步深入。每篇资源均提供完整可运行的代码示例，并配有逐步解释，助您掌握更多 API 功能或在项目中尝试替代实现方案。

- [使用 Aspose.Words for .NET 在 Word 中插入柱形图](/words/english/net/working-with-charts/insert-column-chart/)
- [在 Word 文档中插入面积图 | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [使用 Aspose.Words for .NET 创建 Word 散点图](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}