---
title: 使用 Aspose.Words for .NET 从 Word 文档中删除图表系列
weight: 510
limit:
description: 了解如何使用 Aspose.Words for .NET 从 Word 文档中的柱形图删除特定数据系列。
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 了解如何使用 Aspose.Words for .NET 从 Word 文档中的柱形图删除特定数据系列。
  headline: 使用 Aspose.Words for .NET 从 Word 文档中删除图表系列
  type: TechArticle
- description: 了解如何使用 Aspose.Words for .NET 从 Word 文档中的柱形图删除特定数据系列。
  name: 使用 Aspose.Words for .NET 从 Word 文档中删除图表系列
  steps:
  - name: 创建一个新的 Word Document 并关联一个 DocumentBuilder。
    text: 创建一个新的 Word Document 并关联一个 DocumentBuilder。
  - name: 插入一个尺寸为 432×252 点的柱形图，并获取 Chart 对象以便进一步操作。
    text: 插入一个尺寸为 432×252 点的柱形图，并获取 Chart 对象以便进一步操作。
  - name: 定义要删除的系列的零基索引（第二个系列）。
    text: 定义要删除的系列的零基索引（第二个系列）。
  - name: 如果索引有效，调用图表 Series 集合的 RemoveAt 方法删除该系列。
    text: 如果索引有效，调用图表 Series 集合的 RemoveAt 方法删除该系列。
  - name: 将更新后的文档保存为 .docx 文件。
    text: 将更新后的文档保存为 .docx 文件。
  type: HowTo
- questions:
  - answer: '`if` 检查 (`targetSeriesIdx < columnChart.Series.Count`) 将失败，因此不会调用 `RemoveAt`，图表保持不变。'
    question: 如果传入的索引等于图表中系列的数量，会发生什么？
  - answer: 是的，在调用 `columnChart.Series.RemoveAt` 后，图例会重新生成以反映剩余的系列，因此被删除的条目会从图例中消失。
    question: 删除系列后会自动更新图例吗？
  - answer: 该代码适用于任何支持 `Series` 集合的图表类型；只需在插入图表时将 `ChartType.Column` 更改为所需的类型即可。
    question: 我可以使用相同的代码删除折线图或饼图中的系列吗？
  - answer: 即使没有任何系列的图表仍然是有效的 `Shape`，会被保存，但在生成的文档中会显示为空。
    question: 如果我删除图表中唯一的系列，图表还能正确保存吗？
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: 在 Word 文档中删除图表系列
og_description: 使用 Aspose.Words for .NET 的逐步指南，剥离 Word 图表中的数据系列。
og_image_alt: 指南展示了如何使用 Aspose.Words for .NET 从 Word 文档中的柱形图删除特定数据系列
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 从 Word 文档中删除图表系列
本教程展示了如何创建 Word 文档，使用 DocumentBuilder 添加柱形图，然后通过 ChartSeriesCollection.RemoveAt 方法删除该图表中的特定数据系列。完成后，您将得到一个已保存的文档，其中不需要的系列已被移除，从而可以直接在 .NET 代码中精确控制图表内容。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: 如果传入的索引等于图表中系列的数量，会发生什么？**  
A: `if` 检查 (`targetSeriesIdx < columnChart.Series.Count`) 将失败，因此不会调用 `RemoveAt`，图表保持不变。

**Q: 删除系列后会自动更新图例吗？**  
A: 是的，在调用 `columnChart.Series.RemoveAt` 后，图例会重新生成以反映剩余的系列，因此被删除的条目会从图例中消失。

**Q: 我可以使用相同的代码删除折线图或饼图中的系列吗？**  
A: 该代码适用于任何支持 `Series` 集合的图表类型；只需在插入图表时将 `ChartType.Column` 更改为所需的类型即可。

**Q: 如果我删除图表中唯一的系列，图表还能正确保存吗？**  
A: 即使没有任何系列的图表仍然是有效的 `Shape`，会被保存，但在生成的文档中会显示为空。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}