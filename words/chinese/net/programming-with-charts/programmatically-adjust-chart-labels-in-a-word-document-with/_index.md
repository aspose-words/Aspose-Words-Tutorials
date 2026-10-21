---
category: general
date: 2026-10-13
description: 学习如何使用 C# 在 Word 文档中以编程方式调整图表标签。本指南涵盖 Aspose.Words 图表操作和标签对齐。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: zh
lastmod: 2026-10-13
og_description: 使用 C# 以编程方式调整 Word 文档中的图表标签。请遵循本完整教程，了解如何更改标签位置、对齐方式等。
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: 使用 C# 编程方式在 Word 中调整图表标签 – 步骤指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: 使用 C# 在 Word 文档中以编程方式调整图表标签
url: /zh/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 在 Word 文档中以编程方式调整图表标签

如果您需要在 Word 文档中**以编程方式调整图表标签**，本指南将向您展示如何使用 C# 完成此操作。无论您是生成报告、自动化仪表板，还是自定义模板，您都将看到一个完整的可运行示例，该示例更改 .docx 文件中图表的标签位置和对齐方式。

您还将学习如何使用**Aspose.Words 图表操作**技术，处理多个系列，并在使用**C# 图表数据标签**对象时避免常见陷阱。

## 前提条件

* 已安装 .NET 6.0（或更高版本）  
* Visual Studio 2022（或任何 C# IDE）  
* **Aspose.Words for .NET** NuGet 包 (`Install-Package Aspose.Words`)  
* 包含至少一个图表的 Word 文档（`input.docx`）  

这些项目是我们将要修改的**Word 文档图表示例**所必需的。

## 步骤 1：设置项目并导入命名空间

创建一个新的控制台项目并添加必要的 `using` 指令。这为**以编程方式调整图表标签**做好环境准备。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*为什么要执行此步骤？*  
加载文档后，您可以访问内部的**Word 文档图表示例**树，图表存储为 shape 节点。

## 步骤 2：定位第一个图表形状

图表存储为 `Shape` 节点。以下代码检索文档中的第一个图表，它是我们标签调整的目标。

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*为什么要执行此步骤？*  
`GetChild` 方法递归搜索（`true`）并返回第一个 `Shape` 类型的节点。将其转换为 `Chart` 使我们能够使用图表专用的 API。

## 步骤 3：访问要修改的数据标签

图表中的每个系列都有一个数据标签集合。对于简单的图表，通常只需第一个标签。下面的代码展示了如何获取它。

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*为什么要执行此步骤？*  
`ChartSeries` 表示一系列点。`DataLabelCollection` 保存该系列的标签，允许对位置和对齐方式进行精确控制。

## 步骤 4：更改标签位置和对齐方式

现在我们通过设置位置、水平对齐和垂直对齐来**以编程方式调整图表标签**。这些属性对应于 Word UI 中看到的选项。

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*为什么要使用这些设置？*  

* `OutsideEnd` 将标签放置在每个条形或列的末端之外，提升可读性。  
* `HorizontalAlignment.Center` 使文本在点上居中，而 `VerticalAlignment.Top` 将标签的顶部边缘与数据点对齐，防止与其他元素重叠。

### 小技巧
如果图表有多个系列，请遍历 `chart.Series` 并对每个 `DataLabelCollection` 应用相同的设置。这可确保整个图表外观一致。

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## 步骤 5：保存修改后的文档

在调整标签后，将更改持久化到新文件中。这完成了**修改图表标签位置**的过程。

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

当您打开 `output.docx` 时，您会看到每个图表标签已移动到其数据点的外部末端，水平居中且垂直顶部对齐。

## 边缘情况和变体

| Situation | What to watch for | Recommended approach |
|-----------|-------------------|----------------------|
| **同一文档中的多个图表** | `GetChild` 只返回第一个图表。 | 使用 `doc.GetChildNodes(NodeType.Shape, true)` 遍历所有图表形状。 |
| **没有数据标签的系列** | `DataLabelCollection` 可能为空。 | 在访问集合之前检查 `series.HasDataLabels`。 |
| **不同的图表类型**（饼图、折线图、散点图） | 并非所有 `DataLabelPosition` 值都有效。 | 对于自动决定最佳位置的图表，使用 `DataLabelPosition.Auto`。 |
| **本地化** | 对齐常量与语言无关，但渲染的文本可能需要从右到左的支持。 | 如果需要 RTL 语言，请设置 `dataLabel.TextDirection`。 |

## 完整、可运行的示例

下面是完整的程序，您可以复制、粘贴并运行。将 `YOUR_DIRECTORY` 替换为实际的文件夹路径。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**预期结果：** 打开 `output.docx` 可看到每个图表标签位于数据点外部，水平居中，垂直顶部对齐——正是您通过**以编程方式调整图表标签**脚本实现的效果。

## 结论

您现在已经了解如何使用 C# 在 Word 文档中**以编程方式调整图表标签**。本教程涵盖了：

* 使用 **Aspose.Words 图表操作** 加载文档  
* 访问 **C# 图表数据标签**  
* 更改 **修改图表标签位置** 和对齐方式  
* 保存文件并处理常见的边缘情况  

从这里您可以探索更高级的场景，例如自定义标签字体、添加条件格式，或在批处理过程中更新多个图表。尝试不同的 `DataLabelPosition` 选项，以找到最适合您报告的样式。

---

*准备好提升您的自动化报告流水线了吗？尝试为标签添加自定义数字格式，或将图表导出为图像以用于 PDF。*

## 接下来您应该学习什么？

以下教程涵盖与本指南演示的技术密切相关的主题。每个资源都包含完整的可运行代码示例和逐步解释，帮助您掌握更多 API 功能并在自己的项目中探索替代实现方法。

- [使用 Aspose.Words for .NET 在柱形图中设置统一数据标签](/words/english/net/programming-with-charts/uniform-data-labels/)
- [在图表中设置数据标签的默认选项](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [使用 Aspose.Words for .NET 更新 Word 文档中的图表系列数据](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}