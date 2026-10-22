---
category: general
date: 2026-10-13
description: 如何使用 C# 在 Word 中为图表轴应用自定义数字格式（如货币）来格式化图表。包含逐步代码示例。
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: zh
lastmod: 2026-10-13
og_description: 使用 C# 在 Word 中格式化图表，可让您对图表坐标轴应用自定义数字格式，确保数值以货币、百分比或任何您需要的模式显示。请按照分步指南操作。
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: 如何使用 C# 在 Word 中格式化图表 – 自定义数字格式
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: 如何使用 C# 和自定义数字格式在 Word 中格式化图表
url: /zh/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 C# 在 Word 中格式化图表并自定义数字格式

在需要专业呈现数据时，使用 C# 对 Word 中的图表进行格式化是常见需求。本指南展示了如何使用 **Aspose.Words for .NET** 为图表坐标轴应用自定义数字格式，使数值显示符合预期。

您将学习如何加载 DOCX 文件，定位第一个图表，读取当前格式，然后设置诸如带两位小数的货币格式等新模式。教程还涵盖了如何为其他系列更改图表坐标轴格式以及在需要时如何重置格式。

## 前置条件

开始之前，请确保您具备以下条件：

* 已安装 .NET 6.0 或更高版本  
* 一个 Visual Studio 2022（或任何支持 .NET 的 IDE）项目  
* **Aspose.Words for .NET** NuGet 包 (`Aspose.Words`)  
* 一个包含至少一个图表的 Word 文档 (`input.docx`)

您可以使用以下命令添加该包：

```bash
dotnet add package Aspose.Words
```

## 使用 Aspose.Words 在 Word 中格式化图表

下面的完整程序演示了 **格式化图表** 坐标轴数值所需的每一步。将文件保存为 `Program.cs`，然后在命令行或 IDE 中运行它。

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### 各步骤说明

| 步骤 | 为什么重要 | 关键代码 |
|------|------------|----------|
| **加载文档** | 您需要一个 `Document` 对象来操作 Word 文件。 | `new Document("input.docx")` |
| **获取图表** | `Chart` 对象存储为 `Shape` 节点；强制转换后即可使用图表专用 API。 | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **访问 X 值** | 坐标轴格式化应用于数据系列的值集合。 | `chart.ChartData.Series[0].XValues` |
| **读取当前格式** | 知道已有的 `FormatCode` 有助于决定是替换还是追加。 | `xValues.FormatCode` |
| **设置自定义格式** | `FormatCode` 属性接受任何 Excel 兼容的模式，可实现货币、百分比、日期等。 | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **保存文档** | 将更改持久化会把新的坐标轴格式写回 DOCX 文件。 | `doc.Save("output_formatted.docx")` |

运行程序后会生成 `output_formatted.docx`。在 Word 中打开，您会看到图表的 X 轴数值显示为 **$1,234.00**、**$2,345.00** …，而不是普通数字。

## 为图表坐标轴应用自定义数字格式

如果需要 **为 Y 轴或其他系列** 应用自定义数字格式，步骤完全相同——只需定位不同的集合：

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **专业提示：** 在格式字符串内部使用双引号来嵌入文字字符（例如 `"$"` 表示货币符号）。如上所示对引号进行转义。

## 自定义数字格式与 Word 本地化处理

Word 在解释数字格式时会遵循文档的语言区域设置。如果文档使用非美国地区设置，可能需要调整格式字符串：

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

在使用德语语言设置的文档上测试后，数值会显示为 **€ 1.234,00**。

## 如何以编程方式设置图表属性

除了坐标轴格式化，您通常还想 **设置图表** 标题、图例或数据标签。下面的代码片段演示了在完成坐标轴格式化后设置图表标题的方法：

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

将其与自定义数字格式结合使用，即可得到一张完整、精美的图表，适合报表使用。

## 根据用户输入动态更改图表坐标轴格式

在实际应用中，您可能允许用户在运行时选择格式。以下方法封装了格式化逻辑：

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

您可以调用 `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` 来设置货币格式，或 `SetAxisFormat(chart, 0, "0%")` 来设置百分比。此方式保持主代码简洁，并便于后续扩展。

## 边缘情况与常见陷阱

| 情况 | 需要注意的点 | 建议的解决方案 |
|------|--------------|----------------|
| 文档中 **没有图表** | `GetChild` 返回 `null`，会导致强制转换异常。 | 在强制转换前检查 `null`（参见示例）。 |
| 同一文档中有 **多个图表** | 代码始终获取第一个图表（索引 0）。 | 遍历 `doc.GetChildNodes(NodeType.Shape, true)` 并根据 `ShapeType.Chart` 过滤。 |
| 系列 **没有 X 值**（如饼图） | 访问 `XValues` 可能抛出 `ArgumentOutOfRangeException`。 | 在格式化前确认 `Series[i].XValues` 非空。 |
| 区域设置不匹配 | 货币符号可能显示错误。 | 使用适当的本地化符号显式设置 `xValues.FormatCode`。 |

## 预期输出

运行示例程序后，打开 **output_formatted.docx**。图表的 X 轴应以所选自定义格式显示数值。以货币示例为例，坐标轴标签如下所示：

```
$1,000.00
$2,000.00
$3,000.00
```

如果您对 Y 轴数值使用了百分比格式，则 Y 轴标签会显示为：

```
10%
20%
30%
```

## 结论

本教程展示了如何通过 **在 Word 中使用 C# 为图表坐标轴应用自定义数字格式** 来实现图表格式化。您现在掌握了一套可复用的模式，可用于设置货币、百分比或其他任意数字格式，并了解了处理本地化、多系列以及动态用户输入的要点。

接下来，您可以进一步探索 **设置图表** 标题、数据标签，甚至使用 `ChartRenderer` 将图表导出为图片。这些主题直接基于本指南的概念，可帮助您构建全自动化的报表解决方案。

---


## 接下来你应该学习什么？

以下教程涵盖了与本指南技术紧密相关的主题，帮助您在实际项目中进一步运用这些技巧。每篇资源都提供了完整的可运行代码示例以及逐步解释，帮助您掌握更多 API 功能并探索替代实现方式。

- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Format Secondary X‑Axis and Set Display Units to Thousands in Word Line Charts Using Aspose.Words for .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}