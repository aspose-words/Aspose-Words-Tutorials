---
category: general
date: 2026-07-20
description: 使用 Aspose.Words for .NET 添加饼图标签。了解如何更改饼图标签、显示百分比标签以及快速更新图表系列标签。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: zh
lastmod: 2026-07-20
og_description: 使用 Aspose.Words 在 C# 中添加饼图标签。只需几个步骤即可轻松更改饼图标签、显示百分比标签以及更新图表系列标签。
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: 在 C# 中添加饼图标签 – Aspose.Words 完整教程
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: 在 C# 中使用 Aspose.Words 添加饼图标签 – 完整指南
url: /zh/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 C# 中使用 Aspose.Words 为饼图添加标签 – 完整指南

需要在 Word 文档中 **添加饼图标签** 吗？使用 Aspose.Words，您可以轻松 **更改饼图标签** 并 **显示饼图百分比**，无需在 Word 中手动调整。  

在本教程中，我们将逐步演示 **显示百分比标签**、重新定位标签以及 **为动态数据更新图表系列标签** 的完整过程。完成后，您将拥有一个可在任何 .NET 项目中直接使用的代码片段。

> **快速预览：** 按照本指南操作后，打开保存的 `.docx` 文件，您会看到饼图的每个切片都标有百分比，且标签位于切片外部，便于阅读。

---

## 您需要准备的内容

- **Aspose.Words for .NET**（截至 2026 年的最新版本）。可通过 NuGet 获取：`Install-Package Aspose.Words`。
- 一个已经包含饼图或环形图的 **Word 文档**（我们将其命名为 `Chart.docx`）。
- 基本的 **C#** 与 Visual Studio（或您喜欢的 IDE）使用经验。

就这些——无需额外库、无需 COM 互操作，纯托管代码即可。

---

## 添加饼图标签 – 完整实现

下面是一段 **完整、可运行** 的 C# 控制台程序，它加载文档、修改第一个饼图并保存结果。每行代码都有注释，帮助您了解 **为什么** 要这么做，而不仅仅是 **做了什么**。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### 预期结果

在 Microsoft Word 中打开 `ChartWithCustomLabels.docx`。您应该看到饼图 **带有位于每个切片外部的百分比标签**。标签类似于 “35 %”、 “20 %” 等，使图表一目了然。

---

## 更改饼图标签：位置与格式

如果您只想 **更改饼图标签** 而不显示百分比，只需将 `Position` 属性设置为以下任意值：

| 位置枚举 | 可视效果 |
|----------|----------|
| `InsideEnd`   | 标签位于切片内部，紧贴边缘。 |
| `Center`      | 标签出现在切片中间（适用于小饼图）。 |
| `OutsideEnd`  | 标签位于切片外部，并通过指示线连接（默认选项）。 |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**小技巧：** 当图表切片较多时，`OutsideEnd` 效果最佳，可避免文字重叠。

---

## 在饼图上显示百分比标签

属性 `ShowPercentage` 是一个 **布尔标志**。将其设为 `true`，Aspose.Words 将根据底层数据源计算每个切片的占比。

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

如果您同时需要原始数值 **和** 百分比，也可以将 `ShowValue` 开启：

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

同时启用两项时，标签会显示为 “45 % (120)” 的形式。

---

## 为动态数据更新图表系列标签

在实际项目中，图表往往是实时生成的——比如月度销售或调查结果。要 **以编程方式更新图表系列标签**，请在处理数据标签之前先修改 `Series` 集合：

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

此代码片段演示了如何 **为任意系列更新图表系列标签**，而不仅限于第一个系列。对于需要同时展示实际值与预测值的报表非常实用。

---

## 边缘情况与常见陷阱

| 场景 | 需要注意的点 | 解决方案 |
|------|--------------|----------|
| **图表不是饼图/环形图** | `Position` 可能没有视觉效果。 | 确认 `chart.Type` 为 `ChartType.Pie` 或 `ChartType.Doughnut`。 |
| **未找到图表** | `GetChild` 返回 `null`。 | 添加防护代码（参见示例）并记录友好提示信息。 |
| **Word 版本较旧** | 某些标签功能会被忽略。 | 保存为 `.docx`（现代格式）以确保完整支持。 |
| **切片数量过多** | 即使使用 `OutsideEnd`，标签仍可能重叠。 | 考虑减少切片数量或增大图表尺寸。 |

---

## 完整可运行示例（复制‑粘贴）

以下是您可以直接复制到新控制台项目中的 **完整程序**。只需将 `YOUR_DIRECTORY` 替换为存放 `Chart.docx` 的文件夹路径。



## 接下来您可以学习什么？

以下教程与本指南紧密相关，帮助您进一步掌握 API 功能并探索在项目中的其他实现方式。每篇资源均提供完整可运行的代码示例和逐步说明。

- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize Single Chart Series In A Chart](/words/english/net/programming-with-charts/single-chart-series/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}