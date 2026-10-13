---
title: 使用 Aspose.Words for .NET 在 Word 图表中将次要 Y 轴格式化为货币
weight: 710
limit:
description: 学习如何在 Word 折线图中使用 Aspose.Words for .NET 添加并将次要 Y 轴格式化为货币。
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 学习如何在 Word 折线图中使用 Aspose.Words for .NET 添加并将次要 Y 轴格式化为货币。
  headline: 使用 Aspose.Words for .NET 在 Word 图表中将次要 Y 轴格式化为货币
  type: TechArticle
- description: 学习如何在 Word 折线图中使用 Aspose.Words for .NET 添加并将次要 Y 轴格式化为货币。
  name: 使用 Aspose.Words for .NET 在 Word 图表中将次要 Y 轴格式化为货币
  steps:
  - name: 创建一个新的空 Word 文档，并创建一个 DocumentBuilder 来编辑它。
    text: 创建一个新的空 Word 文档，并创建一个 DocumentBuilder 来编辑它。
  - name: 在文档中插入大小为 450×250 点的折线图，并获取其 Chart 对象。
    text: 在文档中插入大小为 450×250 点的折线图，并获取其 Chart 对象。
  - name: 移除 Aspose 为新图表添加的默认占位系列。
    text: 移除 Aspose 为新图表添加的默认占位系列。
  - name: 定义季度标签，并向图表添加带示例值的主数据系列。
    text: 定义季度标签，并向图表添加带示例值的主数据系列。
  - name: 创建一个类型为 Line 的次要系列组，并将其分配给次要坐标轴组。
    text: 创建一个类型为 Line 的次要系列组，并将其分配给次要坐标轴组。
  - name: 隐藏次要 X 轴，使仅次要 Y 轴可见。
    text: 隐藏次要 X 轴，使仅次要 Y 轴可见。
  - name: 显示次要 Y 轴标题，并将其文本设置为 \"Sales (USD)\"。
    text: 显示次要 Y 轴标题，并将其文本设置为 \"Sales (USD)\"。
  - name: 将次要 Y 轴的数字格式设置为带两位小数的货币模式，并取消其与源格式的链接。
    text: 将次要 Y 轴的数字格式设置为带两位小数的货币模式，并取消其与源格式的链接。
  - name: 向次要组添加辅助系列，提供将在次要 Y 轴上绘制的数据。
    text: 向次要组添加辅助系列，提供将在次要 Y 轴上绘制的数据。
  - name: 将完成的文档保存为当前目录下名为 ProfitChart.docx 的文件。
    text: 将完成的文档保存为当前目录下名为 ProfitChart.docx 的文件。
  type: HowTo
- questions:
  - answer: 图表将保留 Aspose.Words 插入的默认占位系列，因此您的自定义 \"Main Series\" 将与不需要的数据点一起出现。
    question: 如果省略 `lineChart.Series.Clear()` 调用会怎样？
  - answer: 设置 `secondarySeriesGroup.AxisX.Hidden = false;`（或直接省略将其设为 `true` 的那行代码）。
    question: 如何显示次要 X 轴而不是隐藏它？
  - answer: 可以——更改格式字符串，例如使用欧元可写 `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";`，或根据所在地区调整模式。
    question: 我可以为次要 Y 轴使用不同的货币符号或格式吗？
  - answer: 当 `IsLinkedToSource` 为 true 时，坐标轴会继承底层数据源的数字格式，覆盖任何自定义的 `FormatCode`；将其设为
      false 则强制图表使用您指定的格式。
    question: 在应用自定义数字格式时，为什么需要将 `IsLinkedToSource = false`？
  - answer: 可以，将 `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`（默认为 `Right`）赋值即可控制坐标轴绘制在左侧还是右侧。
    question: 是否可以将次要 Y 轴移动到图表的左侧？
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: 将图表的次要坐标轴格式化为货币
og_description: 学习在 Word 折线图中添加次要 Y 轴，并将其样式设为带两位小数的货币。
og_image_alt: 截图显示使用 Aspose.Words for .NET 将次要 Y 轴格式化为货币的 Word 折线图
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 图表中将次要 Y 轴格式化为货币
在本教程中，您将看到如何使用 Aspose.Words for .NET 构建 Word 文档、插入折线图、添加次要 Y 轴、将该轴格式化为带两位小数的货币，并将次要数据系列绑定到该轴。将次要轴格式化为货币可让您在主系列旁清晰展示财务数据。按照逐步代码操作，即可在生成的文档中直接看到渲染的图表。

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

**Q: 如果省略 `lineChart.Series.Clear()` 调用会怎样？**  
A: 图表将保留 Aspose.Words 插入的默认占位系列，因此您的自定义 \"Main Series\" 将与不需要的数据点一起出现。

**Q: 如何显示次要 X 轴而不是隐藏它？**  
A: 设置 `secondarySeriesGroup.AxisX.Hidden = false;`（或直接省略将其设为 `true` 的那行代码）。

**Q: 我可以为次要 Y 轴使用不同的货币符号或格式吗？**  
A: 可以——更改格式字符串，例如使用欧元可写 `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";`，或根据所在地区调整模式。

**Q: 在应用自定义数字格式时，为什么需要将 `IsLinkedToSource = false`？**  
A: 当 `IsLinkedToSource` 为 true 时，坐标轴会继承底层数据源的数字格式，覆盖任何自定义的 `FormatCode`；将其设为 false 则强制图表使用您指定的格式。

**Q: 是否可以将次要 Y 轴移动到图表的左侧？**  
A: 可以，将 `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`（默认为 `Right`）赋值即可控制坐标轴绘制在左侧还是右侧。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}