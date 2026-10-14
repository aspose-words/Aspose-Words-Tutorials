---
title: Resize Chart Proportionally When Changing Page Size in Word Using Aspose.Words for .NET
weight: 210
limit:
description: Learn to auto‑resize a Word column chart when changing the document to A4 using Aspose.Words for .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn to auto‑resize a Word column chart when changing the document
    to A4 using Aspose.Words for .NET.
  headline: Resize Chart Proportionally When Changing Page Size in Word Using Aspose.Words
    for .NET
  type: TechArticle
- description: Learn to auto‑resize a Word column chart when changing the document
    to A4 using Aspose.Words for .NET.
  name: Resize Chart Proportionally When Changing Page Size in Word Using Aspose.Words
    for .NET
  steps:
  - name: Create a new Document object and a DocumentBuilder to edit it.
    text: Create a new Document object and a DocumentBuilder to edit it.
  - name: Insert a column chart of size 432×252 points and obtain its Chart object.
    text: Insert a column chart of size 432×252 points and obtain its Chart object.
  - name: Set the chart title text to "Quarterly Revenue" and make it visible.
    text: Set the chart title text to "Quarterly Revenue" and make it visible.
  - name: Save the document to a file showing the original chart size.
    text: Save the document to a file showing the original chart size.
  - name: Change the document's paper size to A4 and refresh the layout.
    text: Change the document's paper size to A4 and refresh the layout.
  - name: Calculate a new chart width equal to 80 % of the page width while preserving
      the original aspect ratio.
    text: Calculate a new chart width equal to 80 % of the page width while preserving
      the original aspect ratio.
  - name: If the shape contains a chart, apply the calculated width and height to
      resize it.
    text: If the shape contains a chart, apply the calculated width and height to
      resize it.
  - name: Save the document after the chart has been resized to reflect the new page
      size.
    text: Save the document after the chart has been resized to reflect the new page
      size.
  type: HowTo
- questions:
  - answer: Yes. Changing `docBuilder.PageSetup.PaperSize` does not automatically
      adjust existing shapes, so you must recalculate and assign `chartContainer.Width`
      and `Height` yourself as shown.
    question: Do I need to manually resize the chart after changing the document's
      paper size?
  - answer: It stores `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      and then computes `newChartHeight = newChartWidth * originalAspectRatio` after
      determining the new width.
    question: How does the code keep the chart's original width‑to‑height ratio when
      resizing?
  - answer: '`UpdatePageLayout()` forces the layout engine to re‑evaluate page dimensions,
      ensuring `docBuilder.PageSetup.PageWidth` reflects the new A4 width before the
      chart size is recalculated.'
    question: Why is `myDoc.UpdatePageLayout()` called after setting the paper size
      to A4?
  - answer: The `if (chartContainer.HasChart)` guard prevents the code from assigning
      `Width` and `Height` when no chart is present, avoiding a runtime exception.
    question: What happens if the inserted shape does not actually contain a chart?
  - answer: Absolutely—replace the `0.8` multiplier with any proportion you prefer;
      the rest of the resizing logic will still preserve the original aspect ratio.
    question: Can I change the 80 % scaling factor to a different value?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Resize a Word Chart When Switching to A4
og_description: Keep your chart proportional by auto‑resizing it after changing the document to A4.
og_image_alt: Screenshot showing a column chart automatically resized to fit an A4‑sized Word document using Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Resize Chart Proportionally When Changing Page Size in Word Using Aspose.Words
This tutorial shows how to insert a column chart into a Word document, switch the document's page size to A4, and have the chart automatically resize so it remains proportional to the new page width. By following the steps, you’ll see the chart adjust its dimensions without manual scaling, ensuring a consistent layout across different page formats.

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

**Q: Do I need to manually resize the chart after changing the document's paper size?**  
A: Yes. Changing `docBuilder.PageSetup.PaperSize` does not automatically adjust existing shapes, so you must recalculate and assign `chartContainer.Width` and `Height` yourself as shown.

**Q: How does the code keep the chart's original width‑to‑height ratio when resizing?**  
A: It stores `originalAspectRatio = chartContainer.Height / chartContainer.Width` and then computes `newChartHeight = newChartWidth * originalAspectRatio` after determining the new width.

**Q: Why is `myDoc.UpdatePageLayout()` called after setting the paper size to A4?**  
A: `UpdatePageLayout()` forces the layout engine to re‑evaluate page dimensions, ensuring `docBuilder.PageSetup.PageWidth` reflects the new A4 width before the chart size is recalculated.

**Q: What happens if the inserted shape does not actually contain a chart?**  
A: The `if (chartContainer.HasChart)` guard prevents the code from assigning `Width` and `Height` when no chart is present, avoiding a runtime exception.

**Q: Can I change the 80 % scaling factor to a different value?**  
A: Absolutely—replace the `0.8` multiplier with any proportion you prefer; the rest of the resizing logic will still preserve the original aspect ratio.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}