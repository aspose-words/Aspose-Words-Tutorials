---
title: Remove a Chart Series from a Word Document Using Aspose.Words for .NET
weight: 510
limit:
description: Learn how to delete a specific data series from a column chart in a Word document with Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to delete a specific data series from a column chart in a
    Word document with Aspose.Words for .NET.
  headline: Remove a Chart Series from a Word Document Using Aspose.Words for .NET
  type: TechArticle
- description: Learn how to delete a specific data series from a column chart in a
    Word document with Aspose.Words for .NET.
  name: Remove a Chart Series from a Word Document Using Aspose.Words for .NET
  steps:
  - name: Create a new Word Document and a DocumentBuilder linked to it.
    text: Create a new Word Document and a DocumentBuilder linked to it.
  - name: Insert a column chart of size 432×252 points and obtain the Chart object
      for further manipulation.
    text: Insert a column chart of size 432×252 points and obtain the Chart object
      for further manipulation.
  - name: Define the zero‑based index of the series that should be removed (the second
      series).
    text: Define the zero‑based index of the series that should be removed (the second
      series).
  - name: If the index is valid, call RemoveAt on the chart's Series collection to
      delete that series.
    text: If the index is valid, call RemoveAt on the chart's Series collection to
      delete that series.
  - name: Save the updated document to a .docx file.
    text: Save the updated document to a .docx file.
  type: HowTo
- questions:
  - answer: The `if` check (`targetSeriesIdx < columnChart.Series.Count`) will fail,
      so `RemoveAt` is never called and the chart remains unchanged.
    question: What happens if I pass an index that is equal to the number of series
      in the chart?
  - answer: Yes, after `columnChart.Series.RemoveAt` the legend is regenerated to
      reflect the remaining series, so the removed entry disappears from the legend.
    question: Does removing a series automatically update the chart legend?
  - answer: The code works for any chart type that supports a `Series` collection;
      just change `ChartType.Column` to the desired type when inserting the chart.
    question: Can I use the same code to delete a series from a line or pie chart?
  - answer: A chart with zero series is still a valid `Shape` and will be saved, but
      it will appear empty in the resulting document.
    question: If I remove the only series in a chart, will the chart still be saved
      correctly?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Delete a Chart Series in a Word Document
og_description: Step‑by‑step guide to strip a data series from a Word chart using Aspose.Words for .NET.
og_image_alt: Guide showing how to delete a specific data series from a column chart in a Word document using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Remove a Chart Series from a Word Document Using Aspose.Words
This tutorial shows how to create a Word document, add a column chart with DocumentBuilder, and then delete a specific data series from that chart using the ChartSeriesCollection.RemoveAt method. By the end, you’ll have a saved document with the unwanted series removed, giving you precise control over chart content directly from .NET code.

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

**Q: What happens if I pass an index that is equal to the number of series in the chart?**  
A: The `if` check (`targetSeriesIdx < columnChart.Series.Count`) will fail, so `RemoveAt` is never called and the chart remains unchanged.

**Q: Does removing a series automatically update the chart legend?**  
A: Yes, after `columnChart.Series.RemoveAt` the legend is regenerated to reflect the remaining series, so the removed entry disappears from the legend.

**Q: Can I use the same code to delete a series from a line or pie chart?**  
A: The code works for any chart type that supports a `Series` collection; just change `ChartType.Column` to the desired type when inserting the chart.

**Q: If I remove the only series in a chart, will the chart still be saved correctly?**  
A: A chart with zero series is still a valid `Shape` and will be saved, but it will appear empty in the resulting document.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}