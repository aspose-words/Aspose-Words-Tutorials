---
title: Format Secondary Y‑Axis as Currency in a Word Chart Using Aspose.Words for .NET
weight: 710
limit:
description: Learn to add and format a secondary Y‑axis as currency in a Word line chart with Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn to add and format a secondary Y‑axis as currency in a Word line
    chart with Aspose.Words for .NET.
  headline: Format Secondary Y‑Axis as Currency in a Word Chart Using Aspose.Words
    for .NET
  type: TechArticle
- description: Learn to add and format a secondary Y‑axis as currency in a Word line
    chart with Aspose.Words for .NET.
  name: Format Secondary Y‑Axis as Currency in a Word Chart Using Aspose.Words for
    .NET
  steps:
  - name: Create a new empty Word document and a DocumentBuilder to edit it.
    text: Create a new empty Word document and a DocumentBuilder to edit it.
  - name: Insert a line chart of size 450×250 points into the document and obtain
      its Chart object.
    text: Insert a line chart of size 450×250 points into the document and obtain
      its Chart object.
  - name: Remove the default placeholder series that Aspose adds to a new chart.
    text: Remove the default placeholder series that Aspose adds to a new chart.
  - name: Define quarter labels and add a primary data series with sample values to
      the chart.
    text: Define quarter labels and add a primary data series with sample values to
      the chart.
  - name: Create a secondary series group of type Line and assign it to the secondary
      axis group.
    text: Create a secondary series group of type Line and assign it to the secondary
      axis group.
  - name: Hide the secondary X‑axis so only the secondary Y‑axis is visible.
    text: Hide the secondary X‑axis so only the secondary Y‑axis is visible.
  - name: Show the secondary Y‑axis title and set its text to "Sales (USD)".
    text: Show the secondary Y‑axis title and set its text to "Sales (USD)".
  - name: Set the secondary Y‑axis number format to a currency pattern with two decimal
      places and unlink it from the source formatting.
    text: Set the secondary Y‑axis number format to a currency pattern with two decimal
      places and unlink it from the source formatting.
  - name: Add an auxiliary series to the secondary group, providing data that will
      be plotted against the secondary Y‑axis.
    text: Add an auxiliary series to the secondary group, providing data that will
      be plotted against the secondary Y‑axis.
  - name: Save the finished document to a file named ProfitChart.docx in the current
      directory.
    text: Save the finished document to a file named ProfitChart.docx in the current
      directory.
  type: HowTo
- questions:
  - answer: The chart will retain the default placeholder series that Aspose.Words
      inserts, so your custom "Main Series" will appear alongside unwanted data points.
    question: What happens if I omit the `lineChart.Series.Clear()` call?
  - answer: Set `secondarySeriesGroup.AxisX.Hidden = false;` (or simply omit the line
      that sets it to `true`).
    question: How can I display the secondary X‑axis instead of hiding it?
  - answer: Yes – change the format string, e.g. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = "\"€\"#,##0.00";` for euros or adjust the pattern to suit your locale.
    question: Can I use a different currency symbol or format for the secondary Y‑axis?
  - answer: When `IsLinkedToSource` is true the axis inherits the number format from
      the underlying data source, overriding any custom `FormatCode`; setting it to
      false forces the chart to use the format you specify.
    question: Why do I need to set `IsLinkedToSource = false` when applying a custom
      number format?
  - answer: Yes, assign `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (or `Right` for the default) to control which side the axis is drawn on.
    question: Is it possible to move the secondary Y‑axis to the left side of the
      chart?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Format a Chart’s Secondary Axis as Currency
og_description: Learn to add a secondary Y‑axis to a Word line chart and style it as currency with two decimals.
og_image_alt: Screenshot showing a Word line chart with a secondary Y‑axis formatted as currency using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format Secondary Y‑Axis as Currency in a Word Chart Using Aspose.Words
In this tutorial you’ll see how to build a Word document, insert a line chart, add a secondary Y‑axis, format that axis as currency with two decimal places, and bind a secondary data series to it using Aspose.Words for .NET. Formatting the secondary axis as currency lets you clearly present financial data alongside the primary series. Follow the step‑by‑step code to see the chart rendered directly in the generated document.

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

**Q: What happens if I omit the `lineChart.Series.Clear()` call?**  
A: The chart will retain the default placeholder series that Aspose.Words inserts, so your custom "Main Series" will appear alongside unwanted data points.

**Q: How can I display the secondary X‑axis instead of hiding it?**  
A: Set `secondarySeriesGroup.AxisX.Hidden = false;` (or simply omit the line that sets it to `true`).

**Q: Can I use a different currency symbol or format for the secondary Y‑axis?**  
A: Yes – change the format string, e.g. `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = "\"€\"#,##0.00";` for euros or adjust the pattern to suit your locale.

**Q: Why do I need to set `IsLinkedToSource = false` when applying a custom number format?**  
A: When `IsLinkedToSource` is true the axis inherits the number format from the underlying data source, overriding any custom `FormatCode`; setting it to false forces the chart to use the format you specify.

**Q: Is it possible to move the secondary Y‑axis to the left side of the chart?**  
A: Yes, assign `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (or `Right` for the default) to control which side the axis is drawn on.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}