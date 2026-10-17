---
title: Update Chart Series Data in a Word Document Using Aspose.Words for .NET
weight: 610
limit:
description: Learn to modify chart series data points in a Word document and refresh the chart using Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn to modify chart series data points in a Word document and refresh
    the chart using Aspose.Words for .NET.
  headline: Update Chart Series Data in a Word Document Using Aspose.Words for .NET
  type: TechArticle
- description: Learn to modify chart series data points in a Word document and refresh
    the chart using Aspose.Words for .NET.
  name: Update Chart Series Data in a Word Document Using Aspose.Words for .NET
  steps:
  - name: Create a new Document, insert a column chart with a DocumentBuilder, and
      save it as the initial file.
    text: Create a new Document, insert a column chart with a DocumentBuilder, and
      save it as the initial file.
  - name: Open the saved file and locate the chart shape to obtain the existing Chart
      object.
    text: Open the saved file and locate the chart shape to obtain the existing Chart
      object.
  - name: Clear the first series' values and add new points, then adjust the second
      series by removing its first point and adding a new one.
    text: Clear the first series' values and add new points, then adjust the second
      series by removing its first point and adding a new one.
  - name: Save the modified document to a new file containing the updated chart.
    text: Save the modified document to a new file containing the updated chart.
  type: HowTo
- questions:
  - answer: Use `document.GetChildNodes(NodeType.Shape, true)` to get all shapes,
      then filter with `s.HasChart` and pick the first (or the one you need) – this
      avoids picking unrelated pictures or text boxes.
    question: How can I reliably locate the chart shape in a document that may contain
      other shapes?
  - answer: '`ClearValues()` removes the existing data points; without it the new
      points are appended to the old ones, which can produce duplicate categories
      or incorrect totals.'
    question: Why do I need to call `ClearValues()` before adding new points to a
      series?
  - answer: Use `FromString` when the chart’s X‑axis categories are textual (e.g.,
      "Group A"), and `FromDouble` when the axis expects numeric values such as dates
      or measurements.
    question: When should I use `ChartXValue.FromString` versus `ChartXValue.FromDouble`
      for the X‑axis values?
  - answer: Attempting to access a non‑existent series throws an `ArgumentOutOfRangeException`;
      always check `existingChart.Series.Count` before referencing a specific index.
    question: What happens if the chart has only one series and I try to access `existingChart.Series[1]`?
  - answer: Saving `openedDoc` is enough because it is the document instance that
      contains the modified chart; the original `document` was only used to create
      the initial file.
    question: Do I need to re‑save the original `document` after modifying the chart,
      or is saving `openedDoc` sufficient?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Edit Chart Series Data in Word
og_description: Step‑by‑step guide to changing a chart’s series values in a Word file with Aspose.Words for .NET.
og_image_alt: Guide showing a Word document with a column chart before and after updating its series data using Aspose.Words for .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Update Chart Series Data in a Word Document Using Aspose.Words
This tutorial shows how to create a Word document containing a column chart, then reopen the file, retrieve the existing chart series, modify their data points, and save the document so the chart displays the new values. Follow the step‑by‑step code to see how simple it is to programmatically adjust chart data with Aspose.Words for .NET.

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

**Q: How can I reliably locate the chart shape in a document that may contain other shapes?**  
A: Use `document.GetChildNodes(NodeType.Shape, true)` to get all shapes, then filter with `s.HasChart` and pick the first (or the one you need) – this avoids picking unrelated pictures or text boxes.

**Q: Why do I need to call `ClearValues()` before adding new points to a series?**  
A: `ClearValues()` removes the existing data points; without it the new points are appended to the old ones, which can produce duplicate categories or incorrect totals.

**Q: When should I use `ChartXValue.FromString` versus `ChartXValue.FromDouble` for the X‑axis values?**  
A: Use `FromString` when the chart’s X‑axis categories are textual (e.g., "Group A"), and `FromDouble` when the axis expects numeric values such as dates or measurements.

**Q: What happens if the chart has only one series and I try to access `existingChart.Series[1]`?**  
A: Attempting to access a non‑existent series throws an `ArgumentOutOfRangeException`; always check `existingChart.Series.Count` before referencing a specific index.

**Q: Do I need to re‑save the original `document` after modifying the chart, or is saving `openedDoc` sufficient?**  
A: Saving `openedDoc` is enough because it is the document instance that contains the modified chart; the original `document` was only used to create the initial file.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}