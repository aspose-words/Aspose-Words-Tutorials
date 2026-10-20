---
title: 使用 Aspose.Words for .NET 在 Word 中更改页面尺寸时按比例调整图表大小
weight: 210
limit:
description: 学习使用 Aspose.Words for .NET 在将文档更改为 A4 时自动调整 Word 柱形图的大小。
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 学习使用 Aspose.Words for .NET 在将文档更改为 A4 时自动调整 Word 柱形图的大小。
  headline: 使用 Aspose.Words for .NET 在 Word 中更改页面尺寸时按比例调整图表大小
  type: TechArticle
- description: 学习使用 Aspose.Words for .NET 在将文档更改为 A4 时自动调整 Word 柱形图的大小。
  name: 使用 Aspose.Words for .NET 在 Word 中更改页面尺寸时按比例调整图表大小
  steps:
  - name: 创建一个新的 Document 对象并使用 DocumentBuilder 对其进行编辑。
    text: 创建一个新的 Document 对象并使用 DocumentBuilder 对其进行编辑。
  - name: 插入一个尺寸为 432×252 点的柱形图，并获取其 Chart 对象。
    text: 插入一个尺寸为 432×252 点的柱形图，并获取其 Chart 对象。
  - name: 将图表标题文本设置为 "Quarterly Revenue" 并使其可见。
    text: 将图表标题文本设置为 "Quarterly Revenue" 并使其可见。
  - name: 将文档保存为文件，显示原始图表尺寸。
    text: 将文档保存为文件，显示原始图表尺寸。
  - name: 将文档的纸张尺寸更改为 A4 并刷新布局。
    text: 将文档的纸张尺寸更改为 A4 并刷新布局。
  - name: 计算一个新的图表宽度，使其等于页面宽度的 80%，同时保持原始宽高比。
    text: 计算一个新的图表宽度，使其等于页面宽度的 80%，同时保持原始宽高比。
  - name: 如果该形状包含图表，则使用计算得到的宽度和高度对其进行重新尺寸调整。
    text: 如果该形状包含图表，则使用计算得到的宽度和高度对其进行重新尺寸调整。
  - name: 在图表已重新调整大小以适应新页面尺寸后，保存文档。
    text: 在图表已重新调整大小以适应新页面尺寸后，保存文档。
  type: HowTo
- questions:
  - answer: 是的。更改 `docBuilder.PageSetup.PaperSize` 并不会自动调整已有的形状，因此必须像示例中那样自行重新计算并赋值
      `chartContainer.Width` 和 `Height`。
    question: 更改文档纸张尺寸后，我是否需要手动调整图表大小？
  - answer: 它先保存 `originalAspectRatio = chartContainer.Height / chartContainer.Width`，在确定新宽度后再计算
      `newChartHeight = newChartWidth * originalAspectRatio`。
    question: 代码在调整大小时如何保持图表原始的宽高比？
  - answer: '`UpdatePageLayout()` 强制布局引擎重新评估页面尺寸，确保在重新计算图表大小之前，`docBuilder.PageSetup.PageWidth`
      已反映新的 A4 宽度。'
    question: 在将纸张尺寸设置为 A4 后，为什么要调用 `myDoc.UpdatePageLayout()`？
  - answer: '`if (chartContainer.HasChart)` 检查可防止在没有图表时对 `Width` 和 `Height` 进行赋值，从而避免运行时异常。'
    question: 如果插入的形状实际上不包含图表会怎样？
  - answer: 当然可以——将 `0.8` 乘数替换为您想要的任意比例，其他的缩放逻辑仍会保持原始宽高比。
    question: 我可以将 80% 的缩放比例改为其他数值吗？
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: 切换至 A4 时调整 Word 图表大小
og_description: 在将文档更改为 A4 后自动调整图表大小，以保持其比例。
og_image_alt: 截图显示使用 Aspose.Words for .NET 将柱形图自动调整大小以适配 A4 大小的 Word 文档
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 在 Word 中更改页面尺寸时按比例调整图表大小
本教程展示如何在 Word 文档中插入柱形图、将文档的页面尺寸切换为 A4，并让图表自动调整大小，使其在新页面宽度下保持比例。按照步骤操作后，您将看到图表在无需手动缩放的情况下自行调整尺寸，确保在不同页面格式下布局一致。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: 更改文档纸张尺寸后，我是否需要手动调整图表大小？**  
A: 是的。更改 `docBuilder.PageSetup.PaperSize` 并不会自动调整已有的形状，因此必须像示例中那样自行重新计算并赋值 `chartContainer.Width` 和 `Height`。

**Q: 代码在调整大小时如何保持图表原始的宽高比？**  
A: 它先保存 `originalAspectRatio = chartContainer.Height / chartContainer.Width`，在确定新宽度后再计算 `newChartHeight = newChartWidth * originalAspectRatio`。

**Q: 在将纸张尺寸设置为 A4 后，为什么要调用 `myDoc.UpdatePageLayout()`？**  
A: `UpdatePageLayout()` 强制布局引擎重新评估页面尺寸，确保在重新计算图表大小之前，`docBuilder.PageSetup.PageWidth` 已反映新的 A4 宽度。

**Q: 如果插入的形状实际上不包含图表会怎样？**  
A: `if (chartContainer.HasChart)` 检查可防止在没有图表时对 `Width` 和 `Height` 进行赋值，从而避免运行时异常。

**Q: 我可以将 80% 的缩放比例改为其他数值吗？**  
A: 当然可以——将 `0.8` 乘数替换为您想要的任意比例，其他的缩放逻辑仍会保持原始宽高比。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}