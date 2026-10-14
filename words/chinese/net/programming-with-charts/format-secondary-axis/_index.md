---
title: 使用 Aspose.Words for .NET 在 Word 折线图中格式化次要 X 轴并将显示单位设置为千。
weight: 710
limit:
description: 使用 Aspose.Words for .NET 创建 Word 折线图，添加次要 X 轴，将其显示单位设置为千，并应用自定义数字格式。
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 使用 Aspose.Words for .NET 创建 Word 折线图，添加次要 X 轴，将其显示单位设置为千，并应用自定义数字格式。
  headline: 使用 Aspose.Words for .NET 在 Word 折线图中格式化次要 X 轴并将显示单位设置为千。
  type: TechArticle
- description: 使用 Aspose.Words for .NET 创建 Word 折线图，添加次要 X 轴，将其显示单位设置为千，并应用自定义数字格式。
  name: 使用 Aspose.Words for .NET 在 Word 折线图中格式化次要 X 轴并将显示单位设置为千。
  steps:
  - name: 创建一个新的 Document 和一个 DocumentBuilder，以开始构建 Word 文件。
    text: 创建一个新的 Document 和一个 DocumentBuilder，以开始构建 Word 文件。
  - name: 在文档中插入大小为 500×300 的折线图，并获取 Chart 对象。
    text: 在文档中插入大小为 500×300 的折线图，并获取 Chart 对象。
  - name: 移除 Aspose.Words 自动添加的默认演示系列。
    text: 移除 Aspose.Words 自动添加的默认演示系列。
  - name: 定义一个用于 X 轴的类别标签数组。
    text: 定义一个用于 X 轴的类别标签数组。
  - name: 使用标签和值添加名为 "Main Data" 的主数据系列。
    text: 使用标签和值添加名为 "Main Data" 的主数据系列。
  - name: 创建一个类型为 Line 的次要系列组，并将其分配给次要坐标轴组。
    text: 创建一个类型为 Line 的次要系列组，并将其分配给次要坐标轴组。
  - name: 将次要 X 轴的显示单位设置为千，以便数值以 K 显示。
    text: 将次要 X 轴的显示单位设置为千，以便数值以 K 显示。
  - name: 对次要 X 轴的刻度标签应用自定义数字格式 "#,##0.0"。
    text: 对次要 X 轴的刻度标签应用自定义数字格式 "#,##0.0"。
  - name: 可选地向次要组添加辅助数据系列。
    text: 可选地向次要组添加辅助数据系列。
  - name: 将文档保存为 .docx 文件。
    text: 将文档保存为 .docx 文件。
  type: HowTo
- questions:
  - answer: 不——`AxisX` 设置属于 `ChartSeriesGroup`，因此您可以在添加系列之前或之后设置 `secondaryGroup.AxisX.DisplayUnit.Unit`
      和 `secondaryGroup.AxisX.NumberFormat.FormatCode`；无论何时设置，配置都会应用到该组的轴上。
    question: 我是否必须在设置次要 X 轴的显示单位和数字格式之前添加次要系列？
  - answer: 可以——为 `AxisBuiltInUnit` 分配任意值，例如 `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;`，即可将轴值显示为百万而非千。
    question: 我可以为次要 X 轴使用其他内置单位，例如百万吗？
  - answer: 不会——格式代码仅应用于您修改的轴 (`secondaryGroup.AxisX.NumberFormat.FormatCode`)，因此主
      X 轴保持默认格式。
    question: 自定义格式 "#,##0.0" 会影响主 X 轴标签吗？
  - answer: 图表除了您添加的系列外，还会包含默认的演示系列，这可能导致多余的线条和类别不匹配；清除集合可确保仅显示您预期的数据。
    question: 如果忘记使用 `lineChart.Series.Clear();` 清除演示系列，会发生什么？
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: 格式化次要 X 轴并将单位设置为千。
og_description: 向 Word 折线图添加次要 X 轴，并使用自定义模式将其标签格式化为千。
og_image_alt: 指南展示如何使用 Aspose.Words for .NET 向 Word 折线图添加次要 X 轴，并将标签格式化为千单位显示。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 折线图中格式化次要 X 轴并将显示单位设置为千。
本教程将指导您创建包含折线图的 Word 文档，添加次要 X 轴，并将该轴配置为以千为单位显示数值。您还将学习如何对次要轴标签应用自定义数字格式，从而精确控制数据的呈现方式。按照步骤操作，可提升 Word 报告中多轴图表的可读性。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: 我是否必须在设置次要 X 轴的显示单位和数字格式之前添加次要系列？**  
A: 不——`AxisX` 设置属于 `ChartSeriesGroup`，因此您可以在添加系列之前或之后设置 `secondaryGroup.AxisX.DisplayUnit.Unit` 和 `secondaryGroup.AxisX.NumberFormat.FormatCode`；无论何时设置，配置都会应用到该组的轴上。

**Q: 我可以为次要 X 轴使用其他内置单位，例如百万吗？**  
A: 可以——为 `AxisBuiltInUnit` 分配任意值，例如 `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;`，即可将轴值显示为百万而非千。

**Q: 自定义格式 "#,##0.0" 会影响主 X 轴标签吗？**  
A: 不会——格式代码仅应用于您修改的轴 (`secondaryGroup.AxisX.NumberFormat.FormatCode`)，因此主 X 轴保持默认格式。

**Q: 如果忘记使用 `lineChart.Series.Clear();` 清除演示系列，会发生什么？**  
A: 图表除了您添加的系列外，还会包含默认的演示系列，这可能导致多余的线条和类别不匹配；清除集合可确保仅显示您预期的数据。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}