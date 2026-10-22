---
category: general
date: 2026-10-13
description: 在 C# 中自定义饼图后保存修改的文档：分离切片、改变首个切片的角度并显示百分比标签。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: zh
lastmod: 2026-10-13
og_description: 在 C# 中自定义饼图后保存修改的文档。了解如何炸开饼图切片、改变首块角度并显示百分比标签。
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: 保存已修改的文档（带分离饼图切片）– C# 指南
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: 在 C# 中保存带有分离饼图切片的已修改文档
url: /zh/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 使用 C# 保存已修改的文档并拆分饼图切片

如果您需要在调整 Word 饼图后 **保存已修改的文档**，本指南将手把手教您如何操作。您将学习如何拆分饼图切片、修改第一切片的角度以及显示百分比标签——全部只需几行 C# 代码。

在以编程方式生成报告、发票或仪表盘时，自定义图表是常见需求。完成本教程后，您将能够加载 DOCX 文件、修改图表外观，并 **保存已修改的文档** 以供分发。

## 前置条件

- .NET 6.0 或更高版本（代码同样适用于 .NET Framework 4.6+）
- Aspose.Words for .NET 23.10 或更新版本（免费试用版或正式授权版）
- 包含单个饼图的 Word 文件（`input.docx`）
- Visual Studio 2022 或任意 C# IDE

> **提示：** 使用 `dotnet add package Aspose.Words` 可以添加 Aspose.Words NuGet 包。

## 步骤 1：加载包含图表的 Word 文档

第一步是打开源 DOCX 文件。`Document` 类在内存中表示整个 Word 文件。

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

加载文档后，您即可完全访问每个节点，包括承载图表的形状。

## 步骤 2：从文档中获取第一个图表形状

图表存放在 `Shape` 节点内部。您可以使用 `GetChild` 定位第一个图表。

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

如果文档中有多个图表，请调整索引（`0`）或遍历集合。此行代码确保您获得要修改的 `Chart` 对象的引用。

## 步骤 3：拆分饼图切片

拆分切片会将其从整体饼图中分离出来，使图表更易阅读。`Explode` 属性适用于整个系列。

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

将 `Explode` 设置为 `true` **拆分饼图切片**，适用于整个系列，能够让每个切片都突出显示。

## 步骤 4：修改第一切片的角度

有时需要让第一切片从自定义角度开始，例如配合设计规范。

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

`FirstSliceAngle` 属性 **更改第一切片** 的方向，将整个饼图旋转，使第一切片从 30 度开始。

## 步骤 5：在饼图切片上显示百分比标签

在报告中常常需要显示每个切片的数值贡献。`DataLabel.ShowPercentage` 标志可打开百分比显示。

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

此步骤 **在图表上直接显示百分比标签**，同时满足 **display percentages pie** 的需求。

## 步骤 6：保存已修改的文档

完成所有自定义后，将更改持久化到新文件。`Save` 方法会将更新后的 DOCX 写入磁盘。

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

现在您拥有一个 **已保存的修改文档**，其中包含拆分的饼图、旋转的第一切片以及可见的百分比标签。

![保存已修改的文档，显示拆分的饼图切片](/images/pie-chart-exploded.png "保存已修改的文档，展示拆分的饼图切片和百分比标签")

*截图展示了文档保存后最终的输出效果。*

## 完整可运行示例

将上述代码片段组合在一起，下面是可以直接复制到控制台项目中的完整程序：

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### 预期结果

打开 `output.docx` 后，饼图将呈现：

- 每个切片略微分离（**exploded pie chart slices**）
- 第一切片从 30 度偏移开始（**change first slice**）
- 每个切片显示其百分比贡献（**show percentage labels**、**display percentages pie**）
- 文件已 **save modified document**，且未改变原始文件。

## 常见问题与边缘情况

| 问题 | 答案 |
|----------|--------|
| **如果文档中没有图表怎么办？** | 代码在 `GetChild` 后会检查是否为 `null`。若不存在图表，您可以选择编程方式添加一个，或直接给出明确的提示并终止。 |
| **能只拆分单个切片吗？** | 可以。使用 `chart.PieChart.Series[0].DataPoints[i].Explosion = true;`，其中 `i` 为切片索引。 |
| **如何更改标签格式（例如同时显示数值和 %）？** | 设置 `chart.PieChart.DataLabel.ShowValue = true;`，并可选地保留 `chart.PieChart.DataLabel.ShowPercentage = true;`，即可同时显示两者。 |
| **保存后图表样式会被保留吗？** | Aspose.Words 在 **save modified document** 时会保留所有样式，包括颜色和字体。 |
| **能在同一文件中处理多个图表吗？** | 可以遍历所有 `NodeType.Shape` 节点，并通过 `shape.HasChart` 过滤。对每个图表执行相同的步骤即可。 |

## 结论

现在，您已经掌握了在 Word 中通过编程方式自定义饼图后 **save modified document** 的完整流程。本文涵盖了拆分饼图切片、修改第一切片角度以及显示百分比标签，满足 **show percentage labels**、**explode pie chart slices**、**display percentages pie** 与 **change first slice** 等需求。

接下来，您可以进一步探索：

- 动态添加数据系列 (`chart.Series.Add(...)`)  
- 自定义图例位置和图表标题  
- 将 DOCX 转换为 PDF 并保持图表样式  

欢迎尝试不同的角度、拆分设置或标签格式，以匹配您的报表需求。祝编码愉快！

## 接下来您可以学习什么？

以下教程与本指南紧密相关，能够帮助您进一步掌握相关技术。每篇资源都提供完整的可运行代码示例以及逐步解释，帮助您在项目中灵活运用更多 API 功能或探索替代实现方案。

- [How to Save Edited Document in C# with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}