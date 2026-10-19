---
category: general
date: 2026-06-02
description: 使用 C# 在 Word 文档中显示图表图例。了解如何添加图例、应用预设图表样式，并在几分钟内自定义 Word 图表的视觉效果。
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: zh
og_description: 在 Word 文档中即时显示图表图例。本指南将带您逐步添加图例、应用预设图表样式，并处理边缘情况。
og_title: 在 Word 中显示图表图例 – 完整 C# 教程
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: 使用 C# 在 Word 中显示图表图例 – 完整分步指南
url: /zh/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Word 中使用 C# 显示图表图例 – 完整分步指南

是否曾想过 **如何向嵌入 Word 文档的图表添加图例**？你并非唯一有此需求的人。在许多报告中，缺少图例会让数据显得晦涩，而解决这个问题本不该是个难题。  

在本教程中，我们将使用 Aspose.Words for .NET 在 Word 文件中 **显示图表图例**，应用预设图表样式，并确保图例出现在您需要的位置。完成后，您将拥有一个可直接运行的示例，可放入任何 C# 项目中。

## 本指南涵盖内容

我们将完整演示整个工作流：

1. 加载已有的包含图表的 *.docx* 文件。  
2. 获取第一个图表（或您指定的任意图表）。  
3. **应用预设图表样式**，使视觉效果更专业。  
4. **显示图表图例**，将其定位在右侧，并处理诸如瀑布图等特殊情况。  
5. 保存修改后的文档。

无需外部工具，也不必手动操作 UI——只需纯代码。唯一的前提是引用 Aspose.Words NuGet 包（版本 23.10 或更高）并具备基本的 C# 知识。

---

## 前提条件

- .NET 6.0 或更高（示例同样适用于 .NET Framework 4.7.2）。  
- 已安装 Aspose.Words for .NET 库（`Install-Package Aspose.Words`）。  
- 一个已包含至少一个图表的 Word 文件（`input.docx`）。  
- Visual Studio、Rider 或您喜欢的任何 IDE。

---

## 步骤 1：设置项目并加载文档

首先，创建一个控制台应用程序（或将代码集成到现有项目中）。添加 `using` 指令并加载 `.docx` 文件。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **为什么重要：** 加载文档是基础。没有 `Document` 实例，您无法访问 Aspose.Words 提供的图表对象。

---

## 步骤 2：获取目标图表

图表作为节点存储在文档树中。`GetChild` 方法执行深度搜索，使我们能够获取第一个图表，无论它位于页眉、正文、页脚等位置。

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **提示：** 如果有多个图表，将索引 `0` 改为 `1`、`2` …，或遍历 `doc.GetChildNodes(NodeType.Chart, true)`。

---

## 步骤 3：应用预设视觉样式

一个好看的图表通常从样式开始。Aspose.Words 附带数十种内置样式；`ChartStyle.Style12` 是一种简洁、现代的选项。

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **工作原理：** `Style` 属性映射到 UI 中看到的内置 Word 图表样式。选择预设可免去手动设置颜色、字体和标记的步骤。

---

## 步骤 4：启用图例并定位

现在进入重点——**显示图表图例**。我们打开图例，然后将其停靠在图表的右侧。

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **为什么放右侧？** 将图例放在右侧可以保持数据区域宽敞，这对条形图或柱形图尤为有用。

---

## 步骤 5：处理瀑布图（特殊情况）

瀑布图的行为略有不同；默认情况下图例可能被隐藏。以下防护代码确保在图表类型为 Waterfall 时图例可见。

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **边缘情况说明：** 某些旧版 Word 会忽略瀑布图的 `HasLegend`，因此显式设置 `Legend.Show` 可确保可见性。

---

## 步骤 6：保存修改后的文档

最后，将更改写回磁盘。您可以覆盖原文件或创建新文件。

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

运行程序后会生成带有右侧可见图例、使用 `Style12` 样式的 `output.docx`。在 Word 中打开文件即可验证结果。

---

## 完整工作示例（所有步骤合并）

下面是完整的可直接运行的代码。将其复制粘贴到 `Program.cs`（或任意 C# 文件）并根据需要调整文件路径。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**预期输出：** 打开 `output.docx` 可看到原始图表带有右对齐的图例，使用现代的 `Style12` 样式。所有数据系列均清晰标注，使图表一目了然。

---

## 常见问题解答 (FAQ)

### 如何向特定图表（而非第一个）添加图例？

将 `GetChild(NodeType.Chart, 0, true)` 中的 `0` 索引替换为目标图表的零基位置，或遍历所有图表节点：

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### 能否将图例放在底部而不是右侧？

完全可以。只需更改 `LegendPosition` 枚举即可：

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### 如果图表已经有图例，但我想隐藏它怎么办？

将 `HasLegend` 设置为 `false`：

```csharp
chart.HasLegend = false;
```

### 这是否适用于 Word 2010、2016 及更高版本？

是的。Aspose.Words 抽象了底层的 Word 版本，因此相同代码可在所有现代 .docx 文件中运行。

---

## 专业技巧与常见陷阱

- **专业提示：** 应用样式后，仍可通过 `Chart.Series` 集合微调各个元素（颜色、数据标签）。样式为您提供了坚实的基础。  
- **注意：** 如果图表位于表格单元格内，图例可能显得拥挤。考虑在定位图例前增大图表尺寸（`chart.Width`、`chart.Height`）。  
- **性能提示：** 加载大型文档（数百 MB）可能占用大量内存。如果仅需操作图表，可使用带 `LoadFormat.Docx` 的 `LoadOptions` 来降低开销。

---

## 后续步骤

既然您已经了解了在 Word 中 **如何添加图例** 和 **应用预设图表样式**，接下来可以探索：

- **自定义图表颜色**（`chart.Series[i].Format.Fill.ForeColor`）。  
- **数据标签格式化**（`chart.Series[i].HasDataLabel = true`）。  
- **将图表导出为图像**（`chart.ToImage()`），便于在其他位置嵌入。  

这些主题都基于相同的对象模型，学习曲线相对平缓。

---

## 结论

我们刚刚演示了使用 C# 在 Word 文档中 **显示图表图例** 的完整端到端解决方案。通过加载文档、获取图表、应用预设样式、启用图例并处理瀑布图的特殊情况，您即可获得一张可用于任何业务报告的精美图表。  

欢迎尝试其他 `ChartStyle` 值或图例位置——您的数据可视化值得最佳呈现。如果遇到任何问题，请在下方留言；祝编码愉快！

## 接下来该学习什么？

以下教程涵盖与本指南技术密切相关的主题。每个资源都包含完整的可运行代码示例和分步说明，帮助您掌握更多 API 功能并在项目中探索替代实现方案。

- [在 Word 文档中插入柱形图](/words/english/net/programming-with-charts/insert-column-chart/)
- [在 Word 文档中隐藏图表坐标轴](/words/english/net/programming-with-charts/hide-chart-axis/)
- [使用 Word 图表 API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}