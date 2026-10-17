---
title: 使用 Aspose.Words for .NET 在柱形图中设置统一的数据标签
weight: 110
limit:
description: 学习使用 Aspose.Words for .NET 创建 Word 柱形图，并对所有系列应用统一的数据标签字体大小和颜色。
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 学习使用 Aspose.Words for .NET 创建 Word 柱形图，并对所有系列应用统一的数据标签字体大小和颜色。
  headline: 使用 Aspose.Words for .NET 在柱形图中设置统一的数据标签
  type: TechArticle
- description: 学习使用 Aspose.Words for .NET 创建 Word 柱形图，并对所有系列应用统一的数据标签字体大小和颜色。
  name: 使用 Aspose.Words for .NET 在柱形图中设置统一的数据标签
  steps:
  - name: 创建一个新的空白 Word 文档，并创建一个 DocumentBuilder 用于编辑它。
    text: 创建一个新的空白 Word 文档，并创建一个 DocumentBuilder 用于编辑它。
  - name: 在文档中插入一个 500×300 的柱形图，并获取其 Chart 对象。
    text: 在文档中插入一个 500×300 的柱形图，并获取其 Chart 对象。
  - name: 删除 Aspose.Words 为新图表添加的默认示例系列。
    text: 删除 Aspose.Words 为新图表添加的默认示例系列。
  - name: 定义类别标签，并向图表添加两个数据系列（Item Alpha 和 Item Beta）及其数值。
    text: 定义类别标签，并向图表添加两个数据系列（Item Alpha 和 Item Beta）及其数值。
  - name: 设置将应用于所有数据标签的基准字体大小和颜色。
    text: 设置将应用于所有数据标签的基准字体大小和颜色。
  - name: 为每个系列启用数据标签，显示数值，并应用预定义的字体大小和颜色。
    text: 为每个系列启用数据标签，显示数值，并应用预定义的字体大小和颜色。
  - name: 将文档保存为 .docx 文件。
    text: 将文档保存为 .docx 文件。
  type: HowTo
- questions:
  - answer: '`InsertChart` 会创建一个带有默认示例系列的图表；清除该系列会移除占位符，使图表仅显示您添加的系列（`Item Alpha`
      和 `Item Beta`）。'
    question: 为什么在添加自定义系列之前需要调用 `chart.Series.Clear()`？
  - answer: 将 `Color.White` 替换为任意 `System.Drawing.Color` 值，例如 `Color.Black` 或 `Color.FromArgb(255,
      30, 144, 255)`；新颜色通过循环中的 `series.DataLabels.Font.Color` 应用。
    question: 如何将数据标签的颜色改为除白色之外的其他颜色？
  - answer: 数据标签将被隐藏，您设置的字体样式也随之不可见；必须将 `HasDataLabels` 保持为 `true`，标签及其样式才会显示。
    question: 如果在配置字体大小和颜色后将 `series.HasDataLabels = false` 会怎样？
  - answer: 是的——每个 `ChartSeries` 都有自己的 `DataLabels` 对象，因此在初始循环后添加的任何系列也必须设置 `HasDataLabels`、`ShowValue`
      以及字体属性，可以通过再次遍历或将样式提取到辅助方法中实现。
    question: 如果稍后在代码中再添加一个系列，是否需要再次遍历所有系列？
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: 对 Word 图表应用统一的数据标签
og_description: 使用 Aspose.Words for .NET 快速为每个图表标签设置相同的字体大小和颜色。
og_image_alt: 指南展示使用 Aspose.Words for .NET 创建的 Word 文档，其中的柱形图所有数据标签共享相同的字体大小和颜色。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在柱形图中设置统一的数据标签
本教程展示如何使用 Aspose.Words for .NET 生成 Word 文档、插入柱形图并添加自定义数据系列。随后演示如何定义默认的数据标签字体大小和颜色，使图表中的每个系列显示相同的标签。通过应用统一的样式，可确保整个图表的视觉外观保持一致。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: 为什么在添加自定义系列之前需要调用 `chart.Series.Clear()`？**  
A: `InsertChart` 会创建一个带有默认示例系列的图表；清除该系列会移除占位符，使图表仅显示您添加的系列（`Item Alpha` 和 `Item Beta`）。

**Q: 如何将数据标签的颜色改为除白色之外的其他颜色？**  
A: 将 `Color.White` 替换为任意 `System.Drawing.Color` 值，例如 `Color.Black` 或 `Color.FromArgb(255, 30, 144, 255)`；新颜色通过循环中的 `series.DataLabels.Font.Color` 应用。

**Q: 如果在配置字体大小和颜色后将 `series.HasDataLabels = false` 会怎样？**  
A: 数据标签将被隐藏，您设置的字体样式也随之不可见；必须将 `HasDataLabels` 保持为 `true`，标签及其样式才会显示。

**Q: 如果稍后在代码中再添加一个系列，是否需要再次遍历所有系列？**  
A: 是的——每个 `ChartSeries` 都有自己的 `DataLabels` 对象，因此在初始循环后添加的任何系列也必须设置 `HasDataLabels`、`ShowValue` 以及字体属性，可以通过再次遍历或将样式提取到辅助方法中实现。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}