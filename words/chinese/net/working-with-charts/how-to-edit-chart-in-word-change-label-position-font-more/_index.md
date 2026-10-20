---
category: general
date: 2026-07-29
description: 如何在 Word 文档中编辑图表——学习更改图表标签位置、调整柱形图标签、修改图表数据标签以及更改图表标签字体。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: zh
lastmod: 2026-07-29
og_description: 如何快速编辑 Word 中的图表。掌握更改图表标签位置、调整柱形图标签、修改图表数据标签以及更改图表标签字体。
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: 如何在 Word 中编辑图表 – 更改标签和字体
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 如何在 Word 中编辑图表：更改标签位置、字体及其他
url: /zh/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何在 Word 中编辑图表：更改标签位置、字体等

在 Word 文档中编辑图表是让报告更专业的常见需求。是否曾为 **更改图表标签位置** 或让标签易读而在无尽的菜单中苦苦寻找？你并不孤单——大多数开发者在自动化生成报告时都会遇到这个难题。在本指南中，我们将通过一个完整、可运行的示例，展示如何使用 C# 和 Aspose.Words 库 **调整条形图标签**、**修改图表数据标签**，以及 **更改图表标签字体**。

## 你将学到

- 加载已包含条形图的 .docx 文件。  
- 获取第一个图表形状并访问其数据标签集合。  
- **更改图表标签位置** 使条形图更整洁。  
- **调整条形图标签** 的字体大小，以提升可读性。  
- 将修改后的文档保存回磁盘。  

无需外部工具，无需手动 UI 步骤——只需纯代码即可在任何 .NET 项目中使用。完成后，你将拥有一个可在数十个文档中复用的自包含解决方案。

> **前置条件**  
> - .NET 6.0 或更高（代码同样适用于 .NET Framework 4.7+）。  
> - Aspose.Words for .NET（可通过 NuGet 获取）。  
> - 一个已经包含条形图的 Word 文件（`BarChart.docx`）。  

如果缺少上述任意项，请立即获取最新的 Aspose.Words 包：

```bash
dotnet add package Aspose.Words
```

---

## 如何编辑图表：从 Word 文档中获取图表

在 **如何编辑图表** 对象的第一步是加载文档并定位图表形状。Aspose.Words 将图表视为 `Shape` 节点，因此我们可以使用 `GetChild` 并指定 `NodeType.Shape` 来获取遇到的第一个图表。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **为什么重要：**  
> 直接访问 `Chart` 对象，可避免在 Word 中打开文件并手动调整每个标签的开销。这是任何 **修改图表数据标签** 自动化的基石。

## 调整条形图标签：更改图表标签位置

现在我们已经拥有 `Chart` 实例，接下来遍历其 `DataLabelCollection`。目标是 **更改图表标签位置**，让每个标签整齐地位于条形底部，而不是尴尬地漂浮在上方。

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **小技巧：**  
> `InsideBase` 适用于垂直条形图。如果使用水平条形图，可尝试 `InsideEnd`。尝试不同位置成本低——只需重新运行代码并打开保存后的文档即可。

## 更改图表标签字体：调整字体大小提升可读性

细小的字体是报告可读性的隐形杀手。要 **更改图表标签字体**，只需在每个 `ChartDataLabel` 上设置 `Font.Size` 属性。我们将其调至 9 pt，这在大多数打印报告中是一个理想的大小。

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **为什么要这么做：**  
> 调整字体大小是 **修改图表数据标签** 的最佳实践之一。更大的字体提升可访问性，减少手动后处理的需求。

## 保存更新后的文档

在调整完位置和字体后，**如何编辑图表** 的最后一步是将更改持久化。Aspose.Words 只需一行代码即可完成。

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

打开 `BarChartCustomLabels.docx`，你会看到标签紧贴条形内部，并以清晰的 9 pt 字体呈现。再也不必为微小的数字眯眼。

---

## 完整工作示例（所有步骤合在一个文件中）

下面是一个完整的、可直接运行的控制台程序，演示了从加载文档到保存更新版本的整个流程。复制粘贴到新的 .NET 控制台项目中，按 **F5** 运行即可。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**运行程序时的预期输出：**

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

打开生成的文件，你会看到 **调整条形图标签** 已位于条形内部，且字体大小舒适。

---

## 常见问题与边缘情况

### 文档中包含多个图表怎么办？

上述代码获取的是 *第一个* 图表（`GetChild(NodeType.Shape, 0, true)`）。若要编辑所有图表，可将单次获取替换为循环：

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### 如何仅为特定系列 **更改图表标签字体**？

每个 `ChartSeries` 都有自己的 `DataLabelCollection`。通过索引定位系列：

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### 这能用于饼图或折线图吗？

可以——`ChartDataLabelPosition` 支持 `InsideEnd`、`OutsideEnd`、`BestFit` 等值。对于饼图，通常使用 `OutsideEnd` 以保持标签可读。

### 本地化（例如不同的小数分隔符）怎么办？

Aspose.Words 会遵循文档的区域设置。如果需要强制特定格式，可在保存前调整 `label.NumberFormat`。

---

## 小结与后续步骤

我们已经完整演示了在 Word 文档中 **如何编辑图表**：加载文件、获取图表、**更改图表标签位置**、**调整条形图标签**、**修改图表数据标签**，以及 **更改图表标签字体**，最后保存。完整示例已具备生产级别，可直接嵌入任何自动化流水线。

想进一步提升？可以尝试以下思路：

- **添加数据标签颜色**（`dataLabel.Font.Color = Color.Blue;`）。  
- **将数值显示为百分比**（`dataLabel.NumberFormat = "0%";`）。  
- **编程创建图表**，而不是加载已有图表。  

这些功能都基于我们今天使用的相同 API，轻松上手。

如果遇到问题，欢迎在下方留言或查阅 Aspose.Words 文档，获取更深入的图表自定义选项。祝编码愉快，享受美观的标签图表吧！

## 接下来你可以学习什么？

以下教程与本指南紧密相关，帮助你进一步掌握 API 功能并探索项目中的其他实现方式。

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}