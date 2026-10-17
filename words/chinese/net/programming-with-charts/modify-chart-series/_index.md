---
title: 使用 Aspose.Words for .NET 更新 Word 文档中的图表系列数据
weight: 610
limit:
description: 学习如何在 Word 文档中修改图表系列的数据点，并使用 Aspose.Words for .NET 刷新图表。
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 学习如何在 Word 文档中修改图表系列的数据点，并使用 Aspose.Words for .NET 刷新图表。
  headline: 使用 Aspose.Words for .NET 更新 Word 文档中的图表系列数据
  type: TechArticle
- description: 学习如何在 Word 文档中修改图表系列的数据点，并使用 Aspose.Words for .NET 刷新图表。
  name: 使用 Aspose.Words for .NET 更新 Word 文档中的图表系列数据
  steps:
  - name: 创建一个新的 Document，使用 DocumentBuilder 插入柱形图，并将其保存为初始文件。
    text: 创建一个新的 Document，使用 DocumentBuilder 插入柱形图，并将其保存为初始文件。
  - name: 打开已保存的文件，定位图表形状以获取现有的 Chart 对象。
    text: 打开已保存的文件，定位图表形状以获取现有的 Chart 对象。
  - name: 清除第一系列的值并添加新点，然后通过删除第二系列的第一个点并添加新点来调整该系列。
    text: 清除第一系列的值并添加新点，然后通过删除第二系列的第一个点并添加新点来调整该系列。
  - name: 将修改后的文档保存为包含更新后图表的新文件。
    text: 将修改后的文档保存为包含更新后图表的新文件。
  type: HowTo
- questions:
  - answer: 使用 `document.GetChildNodes(NodeType.Shape, true)` 获取所有形状，然后通过 `s.HasChart`
      进行过滤，挑选第一个（或所需的）形状——这样可以避免选中无关的图片或文本框。
    question: 如何在可能包含其他形状的文档中可靠地定位图表形状？
  - answer: '`ClearValues()` 会删除已有的数据点；如果不调用，它会将新点追加到旧点后，可能导致类别重复或总计不正确。'
    question: 为什么在向系列添加新点之前需要调用 `ClearValues()`？
  - answer: 当图表的 X 轴类别为文本（例如 “Group A”）时使用 `FromString`，而当轴需要数值（如日期或测量值）时使用 `FromDouble`。
    question: 在 X 轴数值上，何时应使用 `ChartXValue.FromString` 而不是 `ChartXValue.FromDouble`？
  - answer: 尝试访问不存在的系列会抛出 `ArgumentOutOfRangeException`；在引用特定索引前请务必检查 `existingChart.Series.Count`。
    question: 如果图表只有一个系列，我尝试访问 `existingChart.Series[1]` 会怎样？
  - answer: 保存 `openedDoc` 已足够，因为它是包含已修改图表的文档实例；原始的 `document` 仅用于创建初始文件。
    question: 在修改图表后，我是否需要重新保存原始的 `document`，还是保存 `openedDoc` 已足够？
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: 在 Word 中编辑图表系列数据
og_description: 使用 Aspose.Words for .NET 在 Word 文件中更改图表系列值的分步指南。
og_image_alt: 本指南展示使用 Aspose.Words for .NET 更新系列数据前后，Word 文档中柱形图的对比。
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 使用 Aspose.Words for .NET 更新 Word 文档中的图表系列数据
本教程展示如何创建包含柱形图的 Word 文档，然后重新打开文件，获取已有的图表系列，修改其数据点，并保存文档，使图表显示新的数值。按照一步一步的代码示例，您可以看到使用 Aspose.Words for .NET 以编程方式调整图表数据是多么简单。

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: 如何在可能包含其他形状的文档中可靠地定位图表形状？**  
A: 使用 `document.GetChildNodes(NodeType.Shape, true)` 获取所有形状，然后通过 `s.HasChart` 进行过滤，挑选第一个（或所需的）形状——这样可以避免选中无关的图片或文本框。

**Q: 为什么在向系列添加新点之前需要调用 `ClearValues()`？**  
A: `ClearValues()` 会删除已有的数据点；如果不调用，它会将新点追加到旧点后，可能导致类别重复或总计不正确。

**Q: 在 X 轴数值上，何时应使用 `ChartXValue.FromString` 而不是 `ChartXValue.FromDouble`？**  
A: 当图表的 X 轴类别为文本（例如 “Group A”）时使用 `FromString`，而当轴需要数值（如日期或测量值）时使用 `FromDouble`。

**Q: 如果图表只有一个系列，我尝试访问 `existingChart.Series[1]` 会怎样？**  
A: 尝试访问不存在的系列会抛出 `ArgumentOutOfRangeException`；在引用特定索引前请务必检查 `existingChart.Series.Count`。

**Q: 在修改图表后，我是否需要重新保存原始的 `document`，还是保存 `openedDoc` 已足够？**  
A: 保存 `openedDoc` 已足够，因为它是包含已修改图表的文档实例；原始的 `document` 仅用于创建初始文件。

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}